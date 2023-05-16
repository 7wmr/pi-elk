# Prometheus / Mosquitto / Grafana / Loki

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

## Mosquitto

<!-- https://pimylifeup.com/raspberry-pi-mosquitto-mqtt-server/ -->

```bash
sudo apt install mosquitto mosquitto-clients
```


## Grafana

<!-- https://pimylifeup.com/raspberry-pi-grafana/ -->

```bash
curl https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /usr/share/keyrings/grafana-archive-keyrings.gpg >/dev/null
echo "deb [signed-by=/usr/share/keyrings/grafana-archive-keyrings.gpg] https://apt.grafana.com stable main" | sudo tee /etc/apt/sources.list.d/grafana.list
```

```bash
sudo apt update
```

```bash
sudo apt install grafana
```

```bash
sudo systemctl enable grafana-server
sudo systemctl start grafana-server
```


## Loki
