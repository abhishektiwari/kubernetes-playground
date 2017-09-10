eval $(minikube docker-env)

docker build -t hello-node:v1 .

kubectl run hello-node --image=hello-node:v1 --port=8080

kubectl expose deployment hello-node --type=NodePort

kubectl get services

minikube service hello-node

minikube service --url hello-node

telepresence --swap-deployment hello-node --run-shell node server.js