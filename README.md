# Hvordan-sette-opp-en-Ubuntu-Server-p-Raspberry-Pi
Hvordan sette opp en Ubuntu Server på Raspberry Pi

## Installasjon av SD kort.
Start med å laste ned en Raspberry Pi imager (https://downloads.raspberrypi.org/imager/imager_latest.exe). Plugg inn SD kortet ditt inn i datamaskinen din.
Her velger du hvilken modell av raspberry pi du har, hvilket operativt system du vil bruke (i dette tilfelle ubuntu) og så velger du fil plaseringen til SD kortet ditt.
Når denne installasjonen er ferdig, plugger du SD kortet ditt in i raspberry pien din og starter å kjøre den.

## Ubuntu setup
Start med å velge valgfritt språk til Ubuntu maskinen.
Deretter velg et valgfri Keyboard layout.
Også velger du en valgfri tidssone.
Deretter skriver du in navnet ditt, velger et valgfritt brukernavn og velger et valgfritt passord.

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
## Kjør MariaDB automatisk ved oppstart
Denne kommandoen vil forsikre seg at MariaDB kjører automatisk ved oppstart:
```system
sudo systemctl enable mariadb
```


