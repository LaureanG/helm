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

minikube dashboard

Helm Commands
Install a Release:              helm install [release][chart]       helm install --generate-name [chart]
Upgrade a Release revision:     helm upgrade [release][chart] 
Rollback to a Release revision  helm rollback [release][revision]
Print Release history           helm history [release]
Display Release status          helm status [release]
Show details of a release       helm get all [release]
Uninstall a Release             helm uninstall [release]             helm --keep-history [release]
List Releases                   helm list

lab5
cd to lab5 version 1 final (equivalent to lab1)
cd to chart
helm install [name-of-release] [name-of-chart]
helm install demo-guestbook guestbook
helm list --short
helm get manifest demo-guestbook

lab6
version 2 final
cd to chart
helm upgrade demo-guestbook guestbook
now at revision 3
helm rollback demo-guestbook 2
helm history demo-guestbook
helm uninstall demo-guestbook

Multiple charts structure = Umbrella Chart
-all strings are Base64 encoded
In folder chart\
guestbook
    Chart.yaml (parent of other charts)
    charts\
        Frontent
            Chart.yaml
            Templates (yaml files, including config map)
        Backend
            Chart.yaml
            Templates (yaml files, including secret)
        Database
            Chart.yaml
            Templates (yaml files, including pv and pvc)
From folder chart, call: helm install demo-guestbook guestbook.
Or helm upgrade demo-guestbook guestbook if app already installed.
Check with kubectl get pods