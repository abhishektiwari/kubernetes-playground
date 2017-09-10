Build docker image `hello-node` against the minikube

~~~
eval $(minikube docker-env)
docker build -t hello-node:v1 .
~~~

Create a deployment `hello-node`

~~~
kubectl run hello-node --image=hello-node:v1 --port=8080
~~~

Expose deployment `hello-node` as service

~~~
kubectl expose deployment hello-node --type=NodePort
kubectl get services
~~~

Open or get URL for service `hello-node`

~~~
minikube service hello-node
minikube service --url hello-node
~~~

Start telepresence for `hello-node`

~~~
telepresence --swap-deployment hello-node --run-shell node server.js
~~~