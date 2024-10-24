# Instalasi Grafana

## Instal paket prasyarat:

```
sudo apt-get install -y apt-transport-https software-properties-common wget
```

## Impor kunci GPG:

```
sudo mkdir -p /etc/apt/keyrings/
```

```
wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null
```

## Untuk menambahkan repositori untuk rilis stabil:

```
echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```

## Untuk menambahkan repositori untuk rilis beta:

```
echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com beta main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```

## Memperbarui daftar paket yang tersedia

```
sudo apt-get update
```

## Menginstal rilis OSS terbaru:

```
sudo apt-get install grafana
```

### TIDAK dimulai saat instalasi, silakan jalankan pernyataan berikut untuk mengkonfigurasi grafana untuk memulai secara otomatis menggunakan systemd

```
sudo systemctl daemon-reload
```

```
sudo systemctl enable --now grafana-server
```

### Anda dapat memulai grafana-server dengan menjalankan

```
sudo systemctl start grafana-server
```

## Mengatur Firewall

```
sudo ufw allow 3000
```
