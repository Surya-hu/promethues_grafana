### Install Prometheus and Grafana on a Linux EC2 machine, connect Prometheus to Grafana, and create a dashboard to view metrics.

Instlled prometheus using below command  
wget https://github.com/prometheus/prometheus/releases/download/v2.30.0/prometheus-2.30.0.linux-amd64.tar.gz  
Then extracted the tar.gz file  
cd prometheus-2.30.0.linux-amd64  
from the main prom folder did vi prometheus.yml and edited the config file as whoen below  

global:  
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

Logged in with the ec2 mchine IP :9090 and prometheus was working fine like shown in the below.

Prometheus
![image](https://github.com/Surya-hu/promethues_grafana/assets/119995742/89c7fb4d-dae7-441e-8151-7428d9ae5ba3)


Prometheus
![image](https://github.com/Surya-hu/promethues_grafana/assets/119995742/e131b9a7-93b6-4a1e-9eb6-e441ff7a27a4)

To install grafana,

used below commands:  
sudo apt-get install -y software-properties-common  
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"  
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -  
sudo apt-get install -y grafana  
sudo systemctl start grafana-server  
sudo systemctl enable grafana-server  
Logged in to grafana using default credentials  
Then added data source prometheus using URL http://13.201.45.88:9090/

Grafana
![image](https://github.com/Surya-hu/promethues_grafana/assets/119995742/9c614924-c60c-45ee-88b8-730524d28060)

Created a Dashboard in Grafana
And Configured the panel by selecting Prometheus as the data source and specifying the query to fetch metrics as shown below    

Grafana dashbord with metrics  
![image](https://github.com/Surya-hu/promethues_grafana/assets/119995742/b760e1db-88ac-4476-8bd7-6dde12794dec)



![image](https://github.com/Surya-hu/promethues_grafana/assets/119995742/bb0c3c64-ef41-40b9-ac87-0fe7d194c59a)

