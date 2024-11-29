## Setup Grafana in Ubuntu And Check the Visualization for Node Js Project.
===========================================================================================


### 1. Go to EC2, create ubuntu-instance and connect it ( terminal )


ami = ubuntu

instance types = t2.medium

keypair = any-key.pem

security group = all traffic ( anywhere )


#### 1.1 Updates the list of available packages ( ubuntu )

```sh
sudo apt-get update
```

#### 1.2 install docker

```sh
sudo apt-get install docker.io -y
sudo usermod -aG docker $USER
sudo reboot
```

#### 1.3 need to install docker compose

```sh
sudo apt-get install \
  apt-transport-https \
  ca-certificates \
  curl \
  software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
sudo curl -L "https://github.com/docker/compose/releases/download/v2.6.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
sudo chmod +x /usr/local/bin/docker-compose

docker --version
docker-compose --version
sudo reboot
```

#### 1.4 check docker images if any

```sh
docker images
```

#### 1.5 check docker containers if any

```sh
docker ps -a
```

#### 1.6 Now we need to create a one directory that is prometheus

```sh
mkdir prometheus
cd prometheus/
```

#### 1.7 need to Download Prometheus Configration File

```sh
wget https://raw.githubusercontent.com/prometheus/prometheus/main/documentation/examples/prometheus.yml
```

#### 1.8 check Prometheus Configration File

```sh
ls
```

#### 1.9 need to create a docker-compse file for the Prometheus


`vi docker-compose.yml`


```sh
version: '3.2'
services:
  prometheus:
    image: prom/prometheus:latest
    container_name: prometheus
    ports:
      - 9090:9090
    command:
      - --config.file=/etc/prometheus/prometheus.yml
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml:ro
    depends_on:
      - cadvisor
  cadvisor:
    image: gcr.io/cadvisor/cadvisor:latest
    container_name: cadvisor
    ports:
      - 8080:8080
    volumes:
      - /:/rootfs:ro
      - /var/run:/var/run:rw
      - /sys:/sys:ro
      - /var/lib/docker/:/var/lib/docker:ro
    depends_on:
      - redis
  redis:
    image: redis:latest
    container_name: redis
    ports:
      - 6379:6379
```

what is present inside this docker-compose file

```sh
This docker-compose file we have service , cadvisor and redis.
So let me explain cadvisor, we use cadvisor because Prometheus working for metrics and alerting but it is also working for time series data base,
so if we need to send container metrics to Prometheus , so there has been some tool that is cadivsor send the metrics.
So cadivsor work for containers API call and send the Prometheus.
```
![image](https://github.com/user-attachments/assets/dc36cf3c-5e42-4d44-9e81-b8855f5aea85)


#### 1.10 After that run this docker-compose.yml file

```sh
docker-compose up -d
```

```sh
docker ps
```

`you can see we have cadvisor and Prometheus. Cadvisor running to port number 8080 and Prometheus running to port number 9090.`


#### 1.11 check Cadvisor running and Prometheus running status

pub-ip:8080

pub-ip:9090


### 2. Now we will go to check the metrics for the project, go to the docker hub and pull image


```sh
cd prometheus/
```

```sh
docker pull ishusharmaece/node-app-batch-6:latest
```

#### 2.1 check docker images if any

```sh
docker images
```


#### 2.1 Now create container for project is running

```sh
docker run -d -p 8000:8000 --name myNodeApp ishusharmaece/node-app-batch-6:latest
```

#### 2.2 check docker containers status

```sh
docker ps -a
```

Now application is running


#### 2.3 Now go the cadvisor and check our App container is here or not


go to cadvisor ---->  click on Docker Containers

Now we have Node App here in Cadvisor.



#### 2.4 Now we have application in Cadvisor need to go to Prometheus so change the Prometheus config file


vi prometheus.yml


```sh
# my global config
global:
  scrape_interval: 15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

# Alertmanager configuration
alerting:
  alertmanagers:
    - static_configs:
        - targets:
          # - alertmanager:9093

# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: "prometheus"

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
      - targets: ["localhost:9090"]
  - job_name: "docker"
    static_configs:
      - targets: ["cadvisor:8080"]
```


#### 2.5 Now need to restart your prometheus container

`docker ps -a`

`docker restart prometheus-container-id`

Now go the prometheus server and refresh it   ---->  click on Target health


`Now we have docker logs in Prometheus .Now we check matrics for Node App Aplication.`


#### 2.6 Setup Grafana in AWS EC2 Ubuntu


```sh
sudo apt-get update
sudo apt-get install -y software-properties-common
sudo apt-get install -y gnupg2 curl
curl -fsSL https://packages.grafana.com/gpg.key | sudo gpg --dearmor -o /usr/share/keyrings/grafana-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/grafana-archive-keyring.gpg] https://packages.grafana.com/oss/deb stable main" | sudo tee /etc/apt/sources.list.d/grafana.list > /dev/null

sudo apt-get update
sudo apt-get install -y grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server

sudo systemctl status grafana-server

```

`Grafana Login`

pub-ip:3000


when you login first time that is admin and admin.


#### 2.6 Now in Grafana, go to connection

In connection, add to Prometheus data sources

Now add data sources. And fill the form

   --->  Prometheus server URL = `http://localhost:9090`
   
   --->  Now no need to change anything click to `save and test`

Now Successfully queried the Prometheus API, Now you can visualize data by building dashboard


#### 2.7 Now add to visualization


click on dashboard

Start your new dashboard by adding a visualization

select Prometheus(default)


##### Now we need to install tool that is node-exporter for run the app to Grafana for visualization. so we need to change docker-compose file.


`vi docker-compose.yml`


```sh
version: '3.2'
services:
  prometheus:
    image: prom/prometheus:latest
    container_name: prometheus
    ports:
      - 9090:9090
    command:
      - --config.file=/etc/prometheus/prometheus.yml
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml:ro
    depends_on:
      - cadvisor

  cadvisor:
    image: gcr.io/cadvisor/cadvisor:latest
    container_name: cadvisor
    ports:
      - 8080:8080
    volumes:
      - /:/rootfs:ro
      - /var/run:/var/run:rw
      - /sys:/sys:ro
      - /var/lib/docker/:/var/lib/docker:ro
    depends_on:
      - redis

  redis:
    image: redis:latest
    container_name: redis
    ports:
      - 6379:6379

  node-exporter:
    image: prom/node-exporter:latest
    container_name: node-exporter
    restart: unless-stopped
    volumes:
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /:/rootfs:ro
    command:
      - '--path.procfs=/host/proc'
      - '--path.rootfs=/rootfs'
      - '--path.sysfs=/host/sys'
      - '--collector.filesystem.mount-points-exclude=^/(sys|proc|dev|host|etc)($$|/)'
    expose:
      - 9100
```


`After that run this docker-compose.yml file`

```sh
docker-compose up -d
```



##### Now need to change Prometheus file, so target for node-exporter


`vi prometheus.yml`


```sh
# my global config
global:
  scrape_interval: 15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

# Alertmanager configuration
alerting:
  alertmanagers:
    - static_configs:
        - targets:
          # - alertmanager:9093

# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: "prometheus"

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
      - targets: ["localhost:9090"]
  - job_name: "docker"
    static_configs:
      - targets: ["cadvisor:8080"]

  - job_name: "Nodeexporter"
    static_configs:
      - targets: ["node-exporter:9100"]
```


##### Now need to restart Prometheus container


`docker ps -a`

`docker restart prometheus-container-id`

Now go the prometheus server and refresh it   ---->  we have a node-exporter.



##### Now Need to send the Prometheus data to Grafana


![image](https://github.com/user-attachments/assets/5ac58143-d732-42f6-af76-49161fcaa317)

Now need to create a visualization go to the the browser and `search Grafana dashboard library`

Click to first link. After that click `Node-Exporter Full`

After that click  `copy id to clipboard`

After that go the the Grafana and go the the Dashboard   ---->  New  --->  Import  --->  paste copy-id  and click Load

select Prometheus , After that click to `import`



## Now you see we have visualization our app Node JS Project


=======================END===============================================================
