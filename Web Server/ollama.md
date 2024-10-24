# Linux

## Instalasi

Untuk menginstal Ollama, jalankan perintah berikut:

```shell
curl -fsSL https://ollama.com/install.sh | sh
```

## Instalasi Manual

Unduh dan ekstrak paket:

```shell
curl -L https://ollama.com/download/ollama-linux-amd64.tgz -o ollama-linux-amd64.tgz
sudo tar -C /usr -xzf ollama-linux-amd64.tgz
```

Mulai Ollama:

```shell
ollama serve
```

Di terminal lain, verifikasi bahwa Ollama berjalan:

```shell
ollama -v
```

### Instalasi GPU AMD

Jika kamu memiliki GPU AMD, juga unduh dan ekstrak paket ROCm tambahan:

```shell
curl -L https://ollama.com/download/ollama-linux-amd64-rocm.tgz -o ollama-linux-amd64-rocm.tgz
sudo tar -C /usr -xzf ollama-linux-amd64-rocm.tgz
```

### Instalasi ARM64

Unduh dan ekstrak paket khusus ARM64:

```shell
curl -L https://ollama.com/download/ollama-linux-arm64.tgz -o ollama-linux-arm64.tgz
sudo tar -C /usr -xzf ollama-linux-arm64.tgz
```

### Menambahkan Ollama sebagai layanan startup (direkomendasikan)

Buat pengguna dan grup untuk Ollama:

```shell
sudo useradd -r -s /bin/false -U -m -d /usr/share/ollama ollama
sudo usermod -a -G ollama $(whoami)
```

Buat file layanan di `/etc/systemd/system/ollama.service`:

```ini
[Unit]
Description=Ollama Service
After=network-online.target

[Service]
ExecStart=/usr/bin/ollama serve
User=ollama
Group=ollama
Restart=always
RestartSec=3
Environment="PATH=$PATH"

[Install]
WantedBy=default.target
```

Kemudian mulai layanan:

```shell
sudo systemctl daemon-reload
sudo systemctl enable ollama
```

### Instalasi driver CUDA (opsional)

[Unduh and instal](https://developer.nvidia.com/cuda-downloads) CUDA.

Verifikasi bahwa driver sudah terinstal dengan menjalankan perintah berikut, yang akan mencetak detail tentang GPU-mu:

```shell
nvidia-smi
```

### Instalasi driver AMD ROCm (opsional)

[Unduh and Instal](https://rocm.docs.amd.com/projects/install-on-linux/en/latest/tutorial/quick-start.html) ROCm v6.

### Mulai Ollama

Mulai Ollama dan verifikasi bahwa ia berjalan:

```shell
sudo systemctl start ollama
sudo systemctl status ollama
```

> [!Catatan] Meskipun AMD telah menyumbangkan driver `amdgpu` ke kernel linux resmi, versi tersebut lebih lama dan mungkin tidak mendukung semua fitur ROCm. Kami merekomendasikan untuk menginstal driver terbaru dari AMD untuk dukungan terbaik dari GPU Radeon-mu.

## Memperbarui

Perbarui Ollama dengan menjalankan skrip instalasi lagi:

```shell
curl -fsSL https://ollama.com/install.sh | sh
```

Atau dengan mengunduh ulang Ollama:

```shell
curl -L https://ollama.com/download/ollama-linux-amd64.tgz -o ollama-linux-amd64.tgz
sudo tar -C /usr -xzf ollama-linux-amd64.tgz
```

## Menginstal versi tertentu

Gunakan variabel lingkungan `OLLAMA_VERSION` dengan skrip instalasi untuk menginstal versi tertentu dari Ollama, termasuk pra-rilis. Kamu bisa menemukan nomor versi di [halaman rilis](https://github.com/ollama/ollama/releases).

Misalnya:

```shell
curl -fsSL https://ollama.com/install.sh | OLLAMA_VERSION=0.3.9 sh
```

## Melihat log

Untuk melihat log Ollama yang berjalan sebagai layanan startup, jalankan:

```shell
journalctl -e -u ollama
```

## Uninstall

Hapus layanan ollama:

```shell
sudo systemctl stop ollama
sudo systemctl disable ollama
sudo rm /etc/systemd/system/ollama.service
```

Hapus binary ollama dari direktori bin (baik `/usr/local/bin`, `/usr/bin`, atau `/bin`):

```shell
sudo rm $(which ollama)
```

Hapus model yang diunduh dan pengguna serta grup layanan Ollama:

```shell
sudo rm -r /usr/share/ollama
sudo userdel ollama
sudo groupdel ollama
```
