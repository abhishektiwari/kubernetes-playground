Build docker image `hello-python` against the minikube

~~~
eval $(minikube docker-env)
docker build -t hello-python:v1 .
~~~

Create a deployment `hello-python`

~~~
kubectl run hello-python --image=hello-python:v1 --port=8000
~~~

Expose deployment `hello-python` as service

~~~
kubectl expose deployment hello-python --type=NodePort
kubectl get services
~~~

Open or get URL for service `hello-python`

~~~
minikube service hello-python
minikube service --url hello-python
~~~

Start telepresence for `hello-python`

~~~
telepresence --swap-deployment hello-python --run-shell python3 server.py
~~~