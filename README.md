# Docker and Kubernetes with minikube

```
cd minikube

# build our test hello-node image
docker build -t calvinx/hello-node .

# make it available on dockerhub
docker login
docker push calvinx/hello-node
```

```
minikube start
kubectl create deployment hello-node --image=docker.io/calvinx/hello-node
```

## View the Deployment

```
kubectl get deployments
```

## View the Pod

```
kubectl get pods
```

## View cluster events

```
kubectl get events
```

## View the kubectl configuration

```
kubectl config view
```

## Create a Service

```
# --type=LoadBalancer flag indicates that we want to expose our Service outside of the cluster
kubectl expose deployment hello-node --type=LoadBalancer --port=8080
```

## View the service we created

```
kubectl get services
```

On cloud providers that support load balancers, an external IP address would be provisioned to access the Service. On Minikube, the LoadBalancer type makes the Service accessible through the minikube service command.

```
minikube service hello-node
```

## Clean up

```
kubectl delete service hello-node
kubectl delete deployment hello-node

minikube stop
minikube delete
```

