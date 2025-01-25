## minikube 

1. create a ubuntu sys ( instance )
2. connect ubuntu sys ( instance )
3. run below commands
   
#### 1. Update Ubuntu sys 

`sudo apt update -y`

#### 2. Install Docker

`sudo apt install docker.io -y`

#### 3. Install Minikube

[go to minikube & paste below curl command]----visit

`curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64`

#### 4. To check minikube version

`minikube version`

#### 5. Allow permission for Docker

sudo usermod -aG docker $USER && newgrp docker

#### 6. Start Minikube Service

`minikube start --driver=docker`

#### 7. Install Kubectl ( k8s-CLI )

`sudo snap install kubectl --classic`

#### 8. To check all cluster info

`kubectl get nodes`

`kubectl cluster-info`

`kubectl get po -A`

======END=======

