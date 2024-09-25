# Hvordan-sette-opp-en-Ubuntu-Server-p-Raspberry-Pi
Hvordan sette opp en Ubuntu Server på Raspberry Pi

## Instalasjon av SD kort.
Start med å laste ned en Raspberry Pi imager. Plugg inn SD kortet ditt inn i datamaskinen din.
Her velger du hvilken modell av raspberry pi du har, hvilket operativt system du vil bruke (i dette tilfelle ubuntu) og så velger du fil plaseringen til SD kortet ditt.
Når denne installasjonen er ferdig, plugger du SD kortet ditt in i raspberry pien din og starter å kjøre den.

## Ubuntu setup
Start med å velge valgfritt språk til Ubuntu maskinen.
Deretter velg et valgfri Keyboard layout.
Også velger du en valgfri tidssone.
Deretter skriver du in navnet ditt, velger et valgfritt brukernavn og velger et valgfritt passord.

## MariaDB Instalasjon og setup
Vi begynner med å oppdatere og opgradere systemet i tilfelle det er noen filer datamaskinen mangler.
```system
sudo apt update
```
```system
sudo apt update
```

Så laster vi ned mariadb serveren
```system
sudo apt install mariadb-server
```

Deretter kjører vi MariaDB
```system
sudo mariadb -u server
```
