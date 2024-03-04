# Zimbra
In this Repository you will find how to install Zimbra on Docker

# Docker
## How to install Docker

sudo apt install  apt-transport-https  ca-certificates  curl  software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add --

sudo cp /etc/apt/trusted.gpg /etc/apt/trusted.gpg.d
sudo  add-apt-repository  "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"

sudo apt update
sudo apt install docker-ce

# Creating Zimbra Containers

git clone https://github.com/amirouchef/docker-zimbra.git
cd docker-zimbra/docker

sudo docker build -t monzimbra .

docker run -p 25:25 -p 80:80 -p 465:465 -p 587:587 -p 110:110 -p 143:143 -p 993:993 -p 995:995 -p 443:443 -p 8443:8443 -p 7071:7071 -p 9071:9071 -h <YOUR_FQDN> --dns 127.0.0.1 --dns 8.8.8.8 -i -t -e PASSWORD=<YOUR_ADMIN_PASSWORD> monzimbra

Example : 
docker run -p 25:25 -p 80:80 -p 465:465 -p 587:587 -p 110:110 -p 143:143 -p 993:993 -p 995:995 -p 443:443 -p 8443:8443 -p 7071:7071 -p 9071:9071 -h mail.stadiumcompany.com --dns 127.0.0.1 --dns 8.8.8.8 -i -t -e PASSWORD=Zimbra2024 monzimbra
