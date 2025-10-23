### V-Server sicher verbinden

## Lokalen SSH‑Schlüssel erstellen
```bash
ssh-keygen -t ed25519 
```

## Mit V-Server Verbinden
```bash
ssh root@82.165.219.147
```

## Neuen Benutzer erstellen
```bash
adduser name
usermod -aG sudo name
mkdir -p /home/name/.ssh
chmod 700 /home/name/.ssh
chown -R name:name /home/name/.ssh
```

## Localen SSH Key auf den V-Server kopieren unter Windows 
```bash
type C:\Users\name\.ssh\developerAkademie\id_ed25519.pub | ssh name@168.119.232.167 "cat >> .ssh/authorized_keys"
```

## Mit SSH Key auf den Server Verbinden
```bash
ssh -i C:\Users\name\.ssh\developerAkademie\id_ed25519 name@168.119.232.167
```

## Datei berechtigung nur auf Benutzer setzen
```bash
sudo chown name:name /home/name/.ssh/authorized_keys
sudo chmod 600 /home/name/.ssh/authorized_keys
sudo chmod 700 /home/name/.ssh
```

## V-Server Passwort Verbunding deaktivieren nur noch per Shh
```bash
sudo nano /etc/ssh/sshd_config
```
# PasswordAuthentication yes zu no und entkommentieren

```bash
sudo systemctl restart ssh.service
```
# Shh System neu Starten

### Webserver im Webrowser öffnen Nginx

## Server einaml Updaten
```bash
sudo apt update
```

## Nginx installieren
```bash
sudo apt install nginx -y
```

## Überprüfen ob alles funktioniet
```bash
systemctl status nginx
```

## Ip aufrufen und in Suchleiste eingeben
```bash
ifconfig
```
> eth0 inte 168.119.232.16 ist die Ip Adresse

## Eigene Html seite anzeigen
```bash
sudo mkdir /var/www/alternatives/
sudo touch /var/www/alternatives/alternate-index.html
sudo nano /etc/nginx/sites-enabled/alternatives
```
> Nginx konfigurieren für neue Html seite

```js
    server {
        listen 8081;
        listen [::]:8081;

        root /var/www/alternatives;
        index alternate-index.html;

        location / {
            try_files $uri $uri/ =404;
        }
    }
```

## Nginx nach änderung neu Starten
```bash
sudo service nginx restart
```

### Alias abkürzungen erstellen unter Linux/Ubunto

## Neuen Alias erstellen 
> cd //home/name
```bash
sudo nano .bashrc
```
> unten neuen alias definieren

```bash
alias dal_connect='ssh -i ~/.ssh/id_ed25519 name@168.119.232.167'
```
> dal_connect steht hier für den abkürzenden Namen

## .bashrc Datei neu laden
```bash
. ~/.bashrc
```

## Alias benutzen
```bash
dal_connetc
```