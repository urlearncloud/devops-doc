## minikube 

1. create a ubuntu sys ( instance )
2. connect ubuntu sys ( instance )
3. run below commands
   
#### Update Ubuntu sys 

`sudo apt update -y`

#### Install Docker

`sudo apt install docker.io -y`

#### Install Minikube

[go to minikube & paste below curl command]----visit

`curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64`

#### To check minikube version

`minikube version`

#### Allow permission for Docker

sudo usermod -aG docker $USER && newgrp docker

#### Start Minikube Service

`minikube start --driver=docker`

#### Install Kubectl ( k8s-CLI )

`sudo snap install kubectl --classic`

#### To check all cluster info

`kubectl get nodes`

`kubectl cluster-info`

`kubectl get po -A`

======END=======

