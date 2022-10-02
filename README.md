# Privater Portal - Allgemein
## Docker Setup
1. Docker starten
````shell
docker-compose up -d
````
2. Portal Anwendung vorbereiten
````shell
docker exec -it portal-service bash
composer install
````
3. Hosts Eintrag erstellen

Pfad auf Linux: `/etc/hosts`, Pfad auf Windows: `%windir%\system32\drivers\etc`

Folgenden Eintrag einfügen:
````
192.168.xxx.xxx www.aria-portal.local
192.168.xxx.xxx aria-portal.local
````
4. SSL für Verschlüsselung verwenden
````
öffne openssl shell
openssl req -new -newkey rsa:4096 -days 3650 -nodes -x509 -subj "/C=US/ST=NC/L=Local/O=Dev/CN=aria-portal.local" -keyout ./aria-portal.local.key -out ./aria-portal.local.crt
chmod 644 aria-portal.local.crt
chmod 600 aria-portal.local.key
````
## Docker Probleme
Bei Problemen bitte Docker Container leeren
````shell 
docker-compose down -v --rmi all --remove-orphans
docker system prune -a --volumes
````