# Prometheus / Grafana / Loki

## Prometheus

<!-- https://pimylifeup.com/raspberry-pi-prometheus/ -->

```bash
wget https://github.com/prometheus/prometheus/releases/download/v2.44.0/prometheus-2.44.0.linux-armv7.tar.gz
tar xfz prometheus-2.44.0.linux-armv7.tar.gz
```

```bash
sudo mv prometheus-2.44.0.linux-armv7/ /prometheus/
```

```bash
rm prometheus-2.44.0.linux-armv7.tar.gz
```

```bash
sudo useradd prometheus
sudo chown prometheus:prometheus -R /prometheus 
```

```bash
sudo vim /etc/systemd/system/prometheus.service
```

```
[Unit]
Description=Prometheus Server
Documentation=https://prometheus.io/docs/introduction/overview/
After=network-online.target

[Service]
User=prometheus
Restart=on-failure

ExecStart=/prometheus/prometheus \
  --config.file=/prometheus/prometheus.yml \
  --storage.tsdb.path=/prometheus/data

[Install]
WantedBy=multi-user.target
```

```bash
sudo systemctl enable prometheus
sudo systemctl start prometheus
```

## Grafana

## Loki
