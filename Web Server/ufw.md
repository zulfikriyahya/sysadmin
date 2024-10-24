# Instalasi

```
sudo apt install ufw
```

# Membongkar

```
sudo apt purge ufw
```

```
sudo apt autoremove
```

```
sudo apt autoclean
```

# Mengelola

## Blokir seluruh port akses masuk

```
sudo ufw default deny incoming
```

## Buka seluruh port akses keluar

```
sudo ufw default allow outgoing
```

## Membuka port akses default

```
sudo ufw allow 9090
```

```
sudo ufw allow 9100
```

```
sudo ufw allow 22
```

```
sudo ufw allow 21
```

```
sudo ufw allow 80
```

```
sudo ufw allow 8080
```

```
sudo ufw allow 8000
```

```
sudo ufw allow 443
```

## Menutup port akses default

```
sudo ufw deny 9090
```

```
sudo ufw deny 9100
```

```
sudo ufw deny 22
```

```
sudo ufw deny 21
```

```
sudo ufw deny 80
```

```
sudo ufw deny 8080
```

```
sudo ufw deny 8000
```

```
sudo ufw deny 443
```

## Menolak atau mengizinkan akses dari IP tertentu

### Mengizinkan akses dari IP 36.125.176.24

```
sudo ufw allow from 36.125.176.24
```

### Menolak akses dari IP 36.125.176.24

```
sudo ufw deny from 36.125.176.24
```

## Menjalankan Autostart

```
sudo ufw enable
```

## Menghentikan Autostart

```
sudo ufw disable
```

## Melihat Status

```
sudo ufw status
```
