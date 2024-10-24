# Install Grafana

## Install the prerequisite packages:

sudo apt-get install -y apt-transport-https software-properties-common wget

## Import the GPG key:

sudo mkdir -p /etc/apt/keyrings/
wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null

## To add a repository for stable releases:

echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list

## To add a repository for beta releases:

echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com beta main" | sudo tee -a /etc/apt/sources.list.d/grafana.list

## Updates the list of available packages

sudo apt-get update

## Installs the latest OSS release:

sudo apt-get install grafana

### NOT starting on installation, please execute the following statements to configure grafana to start automatically using systemd

sudo systemctl daemon-reload
sudo systemctl enable --now grafana-server

### You can start grafana-server by executing

sudo systemctl start grafana-server

## Setting Firewall

sudo ufw allow 3000
