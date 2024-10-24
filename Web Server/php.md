# Instalasi PHP

## Add the Ondrej PHP Repository

```
sudo apt install apt-transport-https
```

```
sudo curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
```

```
sudo sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
```

```
sudo apt update
```

## Instalasi

### Install PHP and Extensions and extensions

```
sudo apt install php8.3 php8.3-{cli,bz2,curl,mbstring,intl,zip,gd,mysqli,mcrypt} -y
```

### Install FPM or Apache Module

#### Install FPM

```
sudo apt install php8.3-fpm -y
```

#### Install Apache Module

```
sudo apt install libapache2-mod-php -y
```

sudo systemctl restart apache2

sudo systemctl status apache2
