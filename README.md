# Packaging Applications with Helm for Kubernetes
Ressources for "Packaging Applications with Helm for Kubernetes" @ Pluralsight (Helm version 3)
choco install kubernetes-cli
kubectl version --client
kubectl config get-contexts
kubectl config use-context cluster-name

Install minikube: https://minikube.sigs.k8s.io/docs/start/
choco install minikube
minikube version
minikube start
minikube status
kubectl get po -A
minikube addons enable ingress
minikube ip

Install helm: https://helm.sh/
helm version --short
helm env
kubectl config view
helm repo add stable https://charts.helm.sh/stable
helm install demo-mysql stable/mysql
kubectl get all
kubectl get secret

Uninstall Helm
helm uninstall demo-mysql

lab1
kubectl apply -f ./yaml
kubectl get all
minikube ip
Edit the hosts file and add the ip from previous step to the host name http://frontend.minikube.local/
Check pod is running
kubectl get pods
Navigate to the hostname - for me not working!!!

lab2
cd to lab2
kubectl apply -f ./yaml
kubectl delete -f ./yaml   