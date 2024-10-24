# Instalasi Prometheus

## Download

```
wget https://github.com/prometheus/prometheus/releases/download/v2.55.0/prometheus-2.55.0.linux-amd64.tar.gz
```

## Ekstrak

```
tar xvf prometheus-2.55.0.linux-amd64.tar.gz
```

## Pindah ke Direktori File

```
cd prometheus-2.55.0.linux-amd64
```

## Menambahkan Group

```
sudo groupadd --system prometheus
```

## Menambahkan User dan Memasukkannya ke Group

```
sudo useradd --system -s /sbin/nologin -g prometheus prometheus
```

## Pindahkan File ke /usr/local/bin/

```
sudo mv prometheus promtool /usr/local/bin/
```

## Membuat Direktori untuk menyimpan file konfigurasi

```
sudo mkdir /etc/prometheus
```

## Membuat Direktori untuk menyimpan data prometheus

```
sudo mkdir /var/lib/prometheus
```

## Ubah Permission data prometheus

```
sudo chown -R prometheus:prometheus /var/lib/prometheus
```

## Pindahkan direktori dan file consoles/ console_libraries/ prometheus.yml ke /etc/prometheus/

```
sudo mv consoles/ console_libraries/ prometheus.yml /etc/prometheus/
```

## Pindah direktori

```
cd /etc/prometheus
```

## Ubah konfigurasi file prometheus.yml

```
sudo nano prometheus.yml
```

## Isi konfigurasi

```
global:
scrape_interval: 15s
evaluation_interval: 15s

scrape_configs:

- job_name: "prometheus"
  static_configs:
  - targets: ["localhost:9090"]
- job_name: "node-exporter"
  static_configs:
  - targets: ["localhost:9100"]
```

## Membuat dan menjalankan service daemon

```
sudo nano /etc/systemd/system/prometheus.service
```

## Isi konfigurasi

```
[Unit]
Description=Prometheus
Documentation=https://prometheus.io/docs/introduction/overview/
Wants=network-online.target
After=network-online.target

[Service]
User=prometheus
Group=prometheus
Type=Simple
ExecStart=/usr/local/bin/prometheus \
--config.file /etc/prometheus/prometheus.yml \
--storage.tsdb.path /var/lib/prometheus/ \
--web.console.templates=/etc/prometheus/consoles \
--web.console.libraries=/etc/prometheus/console_libraries

[Install]
WantedBy=multi-user.target
```

## Reload Daemon

```
sudo systemctl daemon-reload
```

## Menjalankan Service dan autostart Prometheus

```
sudo systemctl enable --now prometheus
```

## Mengatur Firewall

```
sudo ufw allow 9090
```
