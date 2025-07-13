# Promethus
Prometheus is a monitoring tool used to analyze the various metrics of servers.
It is simple and powerful. It can store historical data through a timestamp database. This helps in analysis such as:
- Resource utilization
- Uptime
- Cost estimation
- And other metrics easily
---
## How to setup Prometheus
### Step 1: Installing Prometheus for Linux using `wget` command on the server
It will download a tar file.

```bash
cd /opt
wget https://github.com/prometheus/prometheus/releases/download/vX.Y.Z/prometheus-X.Y.Z.linux-amd64.tar.gz
tar -xf prometheus-X.Y.Z.linux-amd64.tar.gz
```

### step 2: setup of system service configuration.

```bash
# renaming the untar file.
mv prometheus-X.Y.Z.linux-amd64.tar.gz prometheus

# it contains to a script file and confirguration file.
 - promethus   
 - promethus.yaml

# creating a systemservice file.

vim /etc/systemd/system/prometheus.service  # cat /etc/systemd/system/prometheus.service

[Unit]
Description=prometheus

[Service]
ExecStart=/opt/prometheus/prometheus --config.file=/opt/prometheus/prometheus.yml

[Install]
WantedBy=multi-user.target

```
### step3: start and enable the prometheus services.
 ```bash
sudo systemctl daemon-reload
sudo systemctl start prometheus
sudo systemctl enable prometheus
```

### open in browser
 <publicip>:9090
