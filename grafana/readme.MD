# Grafana
As promethus is not good with grpahs presentation. so using grafana for better graphs presentation.
# Installing grafana
```bash
curl -o gpg.key https://rpm.grafana.com/gpg.key
sudo rpm --import gpg.key

# setting up service config
vim /etc/yum.repos.d/grafana.repo
cat /etc/yum.repos.d/grafana.repo

[grafana]
name=grafana
baseurl=https://rpm.grafana.com
repo_gpgcheck=1
enabled=1
gpgcheck=1
gpgkey=https://rpm.grafana.com/gpg.key
sslverify=1
sslcacert=/etc/pki/tls/certs/ca-bundle.crt

# install grafana
sudo dnf install grafana -y 

# starting services.
systemctl start grafana-server
systemctl enable grafana-server

# checking for port grafana starts on port :3000
netstat -lntp
tcp6       0      0 :::9090                 :::*                    LISTEN      1661/prometheus
tcp6       0      0 :::3000                 :::*                    LISTEN      2069/grafana
```

### setup of adding garfana into prometheus.

1. after successfull login into grafana interface.
2. go to connections > add new connection > add new data source > name : <provide your name> > connection:  http://localhost:9090  (if prometheus and garfana hosted on same server.) > save & test.
3. this will successfully add promethus into garafana
4. now go to dashboards 
5. click on add visualization and select the connection name saved earlier.
6. in quries you can find your metrics eg: up and run your qurey 
7. this is display the metrics you can save this dashboard.
8. other multiple representations avaiable,choose based on your needs and comfort.