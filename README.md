# 32º Encontro Online DevOpsGo 

**Palestra : Grafana Loki: adicione logs aos dashboards do Grafana facilmente**


Install Docker

```
curl -fsSL https://get.docker.com | bash
```

# Grafana

```
docker run -d -u 0 -v /media/grafana:/var/lib/grafana -p 3000:3000 --name grafana --restart always grafana/grafana:8.0.3
```

# Loki

```
docker run -d -u 0 -v /media/loki/data:/loki -v /media/loki/config:/mnt/config -p 3100:3100 --name loki --restart always grafana/loki:2.2.1 -config.file=/mnt/config/loki-config.yaml
```

# Promtail

```
docker run -d -v /media/promtail:/mnt/config -v /var/log:/var/log -v /media/apache:/media/apache --name promtail --restart always grafana/promtail:2.2.1 -config.file=/mnt/config/promtail-config.yaml
```

# Gerando fake log

Projeto que peguei como base:
https://github.com/tuanpembual/Fake-Apache-Log-Generator

SrvApp1:
```
python3 apache-fake-log-gen.py -n 20000 -o LOG -p apache1 -s 1
```
SrvApp2:
```
python3 apache-fake-log-gen.py -n 20000 -o LOG -p apache2 -s 1
```