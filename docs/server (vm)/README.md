# Environment
## Ipv6
- ```sudo nano /etc/network/interfaces```
- ```iface enp0s3 inet6 auto```
- ```sudo nano /etc/gai.conf```
- ```lösche Kommentare für <precedence ::ffff:0:0/96 100>```
## zusätzliche Tools
- Docker https://docs.docker.com/engine/install/ubuntu/#set-up-the-repository
- Docker Compose https://docs.docker.com/compose/install/other/
- Composer https://getcomposer.org/download/
## Docker
### Group Für Docker erstellen
- sudo groupadd docker
- sudo usermod -aG docker aria
- newgrp docker
## PHP extensions
- sudo add-apt-repository ppa:ondrej/php
- sudo apt-get install php8.2 php8.2-cli php8.2-xml php8.2-mysql php8.2-curl
## Apache
- deinstalliere Apache (falls nötig)
- ```sudo apt-get remove apache2```