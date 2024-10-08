# Hvordan-sette-opp-en-Ubuntu-Server-p-Raspberry-Pi
Hvordan sette opp en Ubuntu Server på Raspberry Pi

## Installasjon av SD kort.
Start med å laste ned en Raspberry Pi imager (https://downloads.raspberrypi.org/imager/imager_latest.exe). Plugg inn SD kortet ditt inn i datamaskinen din.
Her velger du hvilken modell av raspberry pi du har, hvilket operativt system du vil bruke (i dette tilfelle ubuntu) og så velger du fil plaseringen til SD kortet ditt. (se Referanse_Bilde_1.png for extra detalje)
Når denne installasjonen er ferdig, plugger du SD kortet ditt in i raspberry pien din og starter å kjøre den.

## Ubuntu setup
Start med å velge valgfritt språk til Ubuntu maskinen. (se Referanse_Bilde_2.png for extra detalje)

Deretter velg et valgfri Keyboard layout. (se Referanse_Bilde_3.png for extra detalje)

Også velger du en valgfri tidssone. (se Referanse_Bilde_4.png for extra detalje)

Deretter skriver du in navnet ditt, velger et valgfritt brukernavn og velger et valgfritt passord. (se Referanse_Bilde_5.png for extra detalje)

## MariaDB Installasjon og setup
Vi begynner med å oppdatere og opgradere systemet i tilfelle det er noen filer datamaskinen mangler:
```system
sudo apt update
```
```system
sudo apt upgrade
```

Så laster vi ned mariadb serveren:
```system
sudo apt install mariadb-server
```
Denne kommandoen vil sikre MariaDB:
```system
sudo mysql_secure_installation
```
```Enter current password for root (enter for none):```
Skriv in ```Y```

```Switch to unix_socket authentication [Y/N]```
Skrv in ```Y```

```Change the root password? [Y/N]```
skriv in ```N```

```Remove anonymous users? [Y/N]```
skriv in ```Y```

```Disallow root login remotely? [Y/N]```
Skrv in ```Y```

```Remove test database and access to it? [Y/N]```
Skriv in ```Y```

```Reload priviliege tables now? [Y/N]```
Skriv in ```Y```



Deretter kjører vi MariaDB:
```system
sudo mariadb -u server
```
Videre så lager vi en bruker til MariaDB. Brukernavnet og passordet er valgfritt:
```system
CREATE USER 'brukernavn'@'localhost' IDENTIFIED BY 'passord';
```
Deretter gir vi denne brukeren full makt:
```system
GRANT ALL PRIVILEGES ON *.* TO 'brukernavn'@'localhost';
```
Etter at du har tildelt privilegier til bruken, kjører du denne kommandoen for å sikre at MariaDB oppdaterer rettighetene umiddelbart:
```system
FLUSH PRIVILEGES;
```
Deretter kjører vi denne kommandoen for å avslutte MariaDB-sesjonen og tar deg tilbake til terminalen:
```system
EXIT;
```

## SSH setup

Vi må starte med å åpne brannmuren.
Instaler ufw for å åpne brannmuren:
```system
sudo apt install ufw
```
Så aktiverer vi ufw:
```system
sudo ufw enable
```
tilater SSH:
```system
sudo ufw allow ssh
```
Også laster vi ned SSH serveren:
```system
sudo apt install openssh-server
```
Deretter forsikrer vi oss at SSH serveren kjører ved oppstart:
```system
sudo systemctl enable ssh
```
Også starter vi SSH serveren.
```system
sudo systemctl start ssh
```



## Andre anbefale programmer å instalere:

Instalering av Python3 med pip:
```system
sudo apt install python3-pip
```
Instalering av Git:
```system
sudo apt install git
```

## Hvordan koble til SSH serveren fra en ekstern PC

start med å kjøre denne kommandoen på Ubuntu serveren:
```system
hostname -I | awk '{print $1}'
```
deretter skriver du in dette på den eksterne PCen:
```system
SSH brukernavn@din_ip
```


