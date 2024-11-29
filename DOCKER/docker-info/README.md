## Docker services :-

1. container
2. docker
3. install
4. docker architectures
5. docker compose
6. docker swarm


### container


Containerization refers to a technology that allows applications and their dependencies to be packaged together into containers.

Containers are lightweight, portable, and isolated environments that can run consistently across different computing environments, whether it's a developer's laptop, a test server, or a production system. 

Containers helps address the common issue of "it works on my machine" by ensuring that an application behaves the same way regardless of where it is run.

Containers are isolated environments that encapsulate an application and everything it needs to run: libraries, dependencies, binaries, configuration files, etc.

Unlike traditional virtual machines (VMs), containers do not require an entire operating system. Instead, they share the host OS's kernel, making them more lightweight and efficient.

A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another and required to run your application with the minimum system dependencies.





### Docker



Docker is an open-source containerization platform used for automating the process of building, shipping, and running applications inside containers.

Docker, Inc. was founded in 2010 by Solomon Hykes as a company originally known as dotCloud, a Platform-as-a-Service (PaaS) provider. However, Docker itself, the technology, was released to the public in March 2013.

Docker simplifies the development process by allowing developers to easily package and deploy applications with all their dependencies.

Docker is integrated into major cloud providers like AWS, Google Cloud, and Microsoft Azure, which support running Docker containers in scalable cloud environments.

Docker remains at the core of the cloud-native ecosystem, with widespread use in continuous integration and continuous delivery (CI/CD) pipelines, microservices architectures, and cloud computing environments.

In simple words, you can understand as `containerization is a concept or technology` and `Docker Implements Containerization`.


### Docker Architecture


![image](https://user-images.githubusercontent.com/43399466/217507877-212d3a60-143a-4a1d-ab79-4bb615cb4622.png)

The above picture, clearly indicates that Docker Deamon is brain of Docker. If Docker Deamon is killed, stops working.


Docker Architecture is based on a client-server model that includes several key components working together to create, run, and manage containers.

#### Key Components of Docker Architecture :-

1. Docker Client (CLI)
2. Docker Daemon (Server)
3. Docker Images
4. Docker Containers
5. Docker Registry
6. Docker Network
7. Docker Volumes




`1. Docker Client (CLI)`


The Docker client is the primary interface for interacting with Docker. It allows users to issue commands to Docker to create, manage, and run containers.

The client can be run from a terminal or command line and communicates with the Docker daemon (server) to carry out actions.

The client communicates with the Docker daemon using a REST API, typically over a Unix socket (on Linux) or via a network connection (on remote servers).


`2. Docker Daemon (Server)`


The Docker daemon (dockerd) is a background process that manages Docker containers, images, networks, and volumes. It is the heart of Docker’s operation.

It listens for requests from the Docker client and responds by performing actions such as starting/stopping containers, building images, and managing containers' lifecycle.

The Docker daemon can be run on a local machine or on a remote server. The Docker client communicates with the daemon using a REST API, either locally or over a network connection.



`3. Docker Images`


A Docker image is a lightweight, read-only template used to create containers. It includes everything needed to run an application: code, libraries, environment variables, configurations, and dependencies.

Docker images are built from Dockerfiles, which define a series of steps to assemble an image.

Images are usually versioned and stored in a Docker registry (like Docker Hub or a private registry). They are referenced by a unique image ID and tag (e.g., nginx:latest).



`4. Docker Containers`


A container is a running instance of a Docker image. It is an isolated, lightweight environment where applications run.

Containers share the host operating system’s kernel. 

When a container is started, it is allocated a unique ID and its own networking environment.



`5. Docker Registry`


A Docker registry is a storage and distribution system for Docker images. 

It allows you to upload and download images, share them with others, or store them for your own use.

Docker Hub is the default, public registry, but you can also set up private registries or use others like Amazon ECR (Elastic Container Registry) or Google Container Registry.

The Docker client pulls images from the registry and pushes local images to it.

Docker’s registry system has the following components:



`6. Docker Networking`


Docker provides different networking options to allow containers to communicate with each other and with the external world.

Network types in Docker :-

Bridge Network :- The default network driver used when no other driver is specified. Containers on a bridge network can communicate with each other using their internal IP addresses.

Host Network :- Containers use the host’s network stack. This is useful when containers need to have direct access to the host network.

Overlay Network :- Used when containers are deployed across multiple Docker hosts. It is commonly used in Docker Swarm and Kubernetes environments.

Macvlan Network :- Allows containers to have their own MAC address, making them appear as physical devices on the network.

None Network :- Containers are not connected to any network.



`7. Docker Volumes`


Docker volumes are used to persist data generated or used by containers. 

By default, when a container is removed, any data stored within the container is lost, but volumes are external to containers and can be reused across container restarts or removals.


Types of volumes :-


Named Volumes :- Explicitly created volumes with names that can be shared across containers.

Anonymous Volumes :- Volumes created automatically by Docker when no volume name is provided.



### Install

Follow installation guide

### Docker LifeCycle 

We can use the above Image as reference to understand the lifecycle of Docker.

There are three important things,

1. docker build -> builds docker images from Dockerfile
2. docker run   -> runs container from docker images
3. docker push  -> push the container image to public/private regestries to share the docker images.

![Screenshot 2023-02-08 at 4 32 13 PM](https://user-images.githubusercontent.com/43399466/217511949-81f897b2-70ee-41d1-b229-38d0572c54c7.png)



### Understanding the terminology (Inspired from Docker Docs)


#### Docker daemon

The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.


#### Docker client

The Docker client (docker) is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon.


#### Docker Desktop

Docker Desktop is an easy-to-install application for your Mac, Windows or Linux environment that enables you to build and share containerized applications and microservices. Docker Desktop includes the Docker daemon (dockerd), the Docker client (docker), Docker Compose, Docker Content Trust, Kubernetes, and Credential Helper. For more information, see Docker Desktop.


#### Docker registries

A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. You can even run your own private registry.

When you use the docker pull or docker run commands, the required images are pulled from your configured registry. When you use the docker push command, your image is pushed to your configured registry.
Docker objects

When you use Docker, you are creating and using images, containers, networks, volumes, plugins, and other objects. This section is a brief overview of some of those objects.


#### Dockerfile

Dockerfile is a file where you provide the steps to build your Docker Image. 


#### Images

An image is a read-only template with instructions for creating a Docker container. Often, an image is based on another image, with some additional customization. For example, you may build an image which is based on the ubuntu image, but installs the Apache web server and your application, as well as the configuration details needed to make your application run.

You might create your own images or you might only use those created by others and published in a registry. To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. Each instruction in a Dockerfile creates a layer in the image. When you change the Dockerfile and rebuild the image, only those layers which have changed are rebuilt. This is part of what makes images so lightweight, small, and fast, when compared to other virtualization technologies.



### Start Docker and Grant Access

A very common mistake that many beginners do is, After they install docker using the sudo access, they miss the step to Start the Docker daemon and grant acess to the user they want to use to interact with docker and run docker commands.

Always ensure the docker daemon is up and running.

A easy way to verify your Docker installation is by running the below command

```
docker run hello-world
```

If the output says:

```
docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/create": dial unix /var/run/docker.sock: connect: permission denied.
See 'docker run --help'.
```

This can mean two things, 
1. Docker deamon is not running.
2. Your user does not have access to run docker commands.


### Start Docker daemon

You use the below command to verify if the docker daemon is actually started and Active

```
sudo systemctl status docker
```

If you notice that the docker daemon is not running, you can start the daemon using the below command

```
sudo systemctl start docker
```


### Grant Access to your user to run docker commands

To grant access to your user to run the docker command, you should add the user to the Docker Linux group. Docker group is create by default when docker is installed.

```
sudo usermod -aG docker ubuntu
```

In the above command `ubuntu` is the name of the user, you can change the username appropriately.

**NOTE:** : You need to logout and login back for the changes to be reflected.


### Docker is Installed, up and running 🥳🥳

Use the same command again, to verify that docker is up and running.

```
docker run hello-world
```

Output should look like:

```
....
....
Hello from Docker!
This message shows that your installation appears to be working correctly.
...
...
```


## Great Job, Now start with the examples folder to write your first Dockerfile and move to the next examples. Happy Learning :)

### Clone this repository and move to example folder

```
git clone <github-url>
cd  examples
```

### Login to Docker [Create an account with https://hub.docker.com/]

```
docker login
```

```
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: abhishekf5
Password:
WARNING! Your password will be stored unencrypted in /home/ubuntu/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
```

### Build your first Docker Image

You need to change the username accoringly in the below command

```
docker build -t abhishekf5/my-first-docker-image:latest .
```

Output of the above command

```
    Sending build context to Docker daemon  992.8kB
    Step 1/6 : FROM ubuntu:latest
    latest: Pulling from library/ubuntu
    677076032cca: Pull complete
    Digest: sha256:9a0bdde4188b896a372804be2384015e90e3f84906b750c1a53539b585fbbe7f
    Status: Downloaded newer image for ubuntu:latest
     ---> 58db3edaf2be
    Step 2/6 : WORKDIR /app
     ---> Running in 630f5e4db7d3
    Removing intermediate container 630f5e4db7d3
     ---> 6b1d9f654263
    Step 3/6 : COPY . /app
     ---> 984edffabc23
    Step 4/6 : RUN apt-get update && apt-get install -y python3 python3-pip
     ---> Running in a558acdc9b03
    Step 5/6 : ENV NAME World
     ---> Running in 733207001f2e
    Removing intermediate container 733207001f2e
     ---> 94128cf6be21
    Step 6/6 : CMD ["python3", "app.py"]
     ---> Running in 5d60ad3a59ff
    Removing intermediate container 5d60ad3a59ff
     ---> 960d37536dcd
    Successfully built 960d37536dcd
    Successfully tagged abhishekf5/my-first-docker-image:latest
```

### Verify Docker Image is created

```
docker images
```

Output 

```
REPOSITORY                         TAG       IMAGE ID       CREATED          SIZE
abhishekf5/my-first-docker-image   latest    960d37536dcd   26 seconds ago   467MB
ubuntu                             latest    58db3edaf2be   13 days ago      77.8MB
hello-world                        latest    feb5d9fea6a5   16 months ago    13.3kB
```

### Run your First Docker Container

```
docker run -it abhishekf5/my-first-docker-image
```

Output

```
Hello World
```

### Push the Image to DockerHub and share it with the world

```
docker push abhishekf5/my-first-docker-image
```

Output

```
Using default tag: latest
The push refers to repository [docker.io/abhishekf5/my-first-docker-image]
896818320e80: Pushed
b8088c305a52: Pushed
69dd4ccec1a0: Pushed
c5ff2d88f679: Mounted from library/ubuntu
latest: digest: sha256:6e49841ad9e720a7baedcd41f9b666fcd7b583151d0763fe78101bb8221b1d88 size: 1157
```

### You must be feeling like a champ already 















# 1. How to create container :- FROM IMAGE (USING DOCKER PULL)

#### ex-1 :-

Suppose if you want to create debian based container , then go to docker-hub & search `debian`

```sh
sudo docker pull debian
```

To check images


```sh
sudo docker images
```


To create container from `debian image`


```sh
sudo docker run -d -it --name container-1 debian /bin/bash
```

To check only Running container status


```sh
sudo docker ps
```


To stop container


```sh
sudo docker stop container-1
```

To check all container ( both stop and running ) status


```sh
sudo docker ps -a
```


To start a stopped container


```sh
sudo docker start container-1
```

To Remove container from your system

```sh
sudo docker stop container-1
sudo docker rm container-1
```

# 2. How to create container :- FROM IMAGE (USING DOCKER FILE)

#### ex-1 :-

To create a dockerfile

`vi Dockerfile`

( press-i )


```sh
FROM debian
RUN echo "hi all" > myfile
```

( Press - esc , :wq )


Now Create image from dockerfile


```sh
sudo docker build -t myownimg1 .
```


To check image (dockerfile)


```sh
sudo docker images
```


To create container from `myownimg1`


```sh
sudo docker run -d -it --name container-2 myownimg1 /bin/bash
```

To check container status


```sh
sudo docker ps -a
```

Go inside Container

```sh
sudo docker exec -it <container-id-no> /bin/bash
```

To verify `myfile` & its Data present inside container or not

```sh
ls
```

```sh
cat myfile
```

To Go outside from container

```sh
exit
```




## TO HOST A WEBSITE USING DOCKERFILE

#### 1. Create a html file

`vi index.html`

( press-i )

```sh
<html>
<head>
<body>
<title> India-visit </title>
<h1> WELCOME TO INDIA </h1>
<p1> MY INDIA ! MY COUNTRY </p1>
</body>
</head>
</html>
```

( Press - esc , :wq )


#### 2. To create a dockerfile

`vi Dockerfile`

( press-i )


```sh
# Use an existing Nginx image from Docker Hub as the base image
FROM nginx:alpine

# Copy the HTML file into the Nginx default document root directory
COPY index.html /usr/share/nginx/html/

# Expose port 80 to allow communication to/from the container
EXPOSE 80
```

( Press - esc , :wq )


Now Create image from dockerfile


```sh
sudo docker build -t mywebsiteimg1 .
```


To check image (dockerfile)


```sh
sudo docker images
```


To create container from `mywebsiteimg1`


```sh
sudo docker run -d -it -p 8080:80 --name container-3 mywebsiteimg1 /bin/bash
```

To check container status


```sh
sudo docker ps -a
```




# 3. How to create container image


`docker commit container-name newimagename`

`docker images`

