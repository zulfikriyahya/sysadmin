# Install Promatheus Node_Exporter

## Download

```
wget https://github.com/prometheus/node_exporter/releases/download/v1.8.2/node_exporter-1.8.2.linux-amd64.tar.gz
```

## Ekstrak

```
tar xvf node_exporter-1.8.2.linux-amd64
```

## Pindah Direktori

```
cd node_exporter-1.8.2.linux-amd64
```

## Pindahkan File node_exporter ke /usr/local/bin/

```
sudo mv node_exporter /usr/local/bin/
```

## Buatkan Service Daemon

```
sudo nano /etc/systemd/system/node-exporter.service
```

## Isi konfigurasi

```
[Unit]
Description=Prometheus exporter for machine metrics

[Service]
Restart=always
User=prometheus
ExecStart=/usr/local/bin/node_exporter
ExecReload=/bin/kill -HUP $MAINPID
TimeoutStopSec=20s
SendSIGKILL=no

[Install]
WantedBy=multi-user.target
```

## Reload Daemon

```
sudo systemctl daemon-reload
```

## Menjalankan Service dan autostart Node_Exporter

```
sudo systemctl enable --now node-exporter
```

## Setting Firewall

```
sudo ufw allow 9100
```
