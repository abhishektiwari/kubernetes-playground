eval $(minikube docker-env)

docker build -t hello-python:v1 .

kubectl run hello-python --image=hello-python:v1 --port=8000

kubectl expose deployment hello-python --type=NodePort

kubectl get services

minikube service hello-python

minikube service --url hello-python

telepresence --swap-deployment hello-python --run-shell python3 server.py