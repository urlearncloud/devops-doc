## JENKINS INSTALLATION ON AMAZON-EC2
=======================================

### Pre-Requisites:-
 - AWS Account
 - Java (JDK)

## 1. Launch AWS EC2 Instance

- Go to AWS Console
- Instances(running) :- ubuntu-22 or other
- t2.micro
- security group :- ssh, http, https, all traffic (anywhere)
- key pair :- jenkins-key.pem
- Launch instances


### Run the below commands to install Java and Jenkins

Install Java

```
sudo apt update
sudo apt install fontconfig openjdk-17-jre -y
```

Verify Java is Installed

```
java -version
```

Now, you can proceed with installing Jenkins
## YOU CAN FOLLOW : https://www.jenkins.io/doc/book/installing/linux/#debianubuntu

```
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins -y
```



```
sudo systemctl start jenkins
sudo systemctl enable jenkins
```



By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. 

Open port 8080 in the inbound traffic rules as show below.


### Login to Jenkins using the below URL


http://(ec2-instance-public-ip-address):8080 

 
Run the command to copy the Jenkins Admin Password

```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Install suggested plugins



==============SUUCESSFULLY INSTALLED================




