**Install and run an GLPI instance with docker**  

**Tâche n°1 : Installer les paquets nécessaires permettant à apt d'utiliser les paquets sur HTTPS**  
sudo apt install  apt-transport-https  ca-certificates  curl  software-properties-common  

**Tâche n°2 : Ajouter la clé GPG du dépôt officiel de Docker au système**  
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add --  
sudo cp /etc/apt/trusted.gpg /etc/apt/trusted.gpg.d  

**Tâche n°3 : Ajouter le référentiel Docker aux sources APT**  
sudo  add-apt-repository  "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"  

**Tâche n°4 : Mettre à jour la base de données des paquets avec les paquets du référentiel Docker qui vient d'être ajouté**  
sudo apt update  

**Tâche n°5 : Vérifier le dépôt afin de s’assurer que l’installation est réalisée à partir du dépôt Docker (et non du dépôt Ubuntu par défaut)**  
apt-cache policy docker-ce  

**Tâche n°6 : Installer Docker**  
sudo apt install docker-ce  

# Creating Zimbra Containers

**Tâche n°6 : git clone https://github.com/amirouchef/docker-zimbra.git**  
cd docker-zimbra/docker  
sudo docker build -t monzimbra .  

docker run -p 25:25 -p 80:80 -p 465:465 -p 587:587 -p 110:110 -p 143:143 -p 993:993 -p 995:995 -p 443:443 -p 8443:8443 -p 7071:7071 -p 9071:9071 -h <YOUR_FQDN> --dns 127.0.0.1 --dns 8.8.8.8 -i -t -e PASSWORD=<YOUR_ADMIN_PASSWORD> monzimbra  

**Example :** 
docker run -p 25:25 -p 80:80 -p 465:465 -p 587:587 -p 110:110 -p 143:143 -p 993:993 -p 995:995 -p 443:443 -p 8443:8443 -p 7071:7071 -p 9071:9071 -h mail.stadiumcompany.com --dns 127.0.0.1 --dns 8.8.8.8 -i -t -e PASSWORD=Zimbra2024 monzimbra  
