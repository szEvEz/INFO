# Kubernetes 101

## Setup the Kubernetes-Cluster

* Using Docker for Windows (edge version)
* Installing minikube & kubectl

## Useful commands

`kubectl get nodes`
`kubectl config get-contexts`
`kubectl config use-context CONTEXT-NAME`

`kubectl run hello-kubernetes --image=k8s.gcr.io/echoserver:1.4 --port=8080`
`kubectl expose deployment hello-kubernetes --type=NodePort`
`kubectl get service hello-kubernetes`

`kubectl delete service hello-kubernetes`
`kubectl delete deployment hello-kubernetes`


Create a pod via yml file

`kubectl create -f myYamlFile.yml`

`kubectl port-forward nodehelloworld.example.com 8081:3000`

`kubectl expose pod nodehelloworld.example.com --type=NodePort --name nodehelloworld-service`
