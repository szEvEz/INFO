[Install Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

Enable Kubernetes

![docker-desktop-kubernetes-wsl](/images/docker-desktop-kubernetes.JPG)

[Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)

```sh
sudo apt-get update && sudo apt-get install -y apt-transport-https
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
```
Copy kube config that was created for Windows environment to WSL environment

```sh
cp /mnt/c/Users/{username}/.kube/config ~/.kube/config
```

Verify functionality

```sh
kubectl get nodes
```

Example deployment

```sh
kubectl apply -f https://k8s.io/examples/application/deployment.yaml
kubectl expose deployment nginx-deployment --type=LoadBalancer --name=nginx
```

Access browser at `localhost`
