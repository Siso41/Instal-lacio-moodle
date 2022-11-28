# INSTAL·LACIÓ MOODLE

### Instal·lar apache2

El primer que hem de fer és instal·lar apache2 

```
sudo apt-get install apache2
```

![image](https://user-images.githubusercontent.com/114423111/204312545-8a6a0e20-8948-426c-a305-a6dd0dad2920.png)

### Instal·lar MariaDB

Ara hem d'instal·lar MariaDB, que serà la nostra base de dades amb aquesta comanda:

```
sudo apt-get install mariadb-server mariadb-client -y
```
![image](https://user-images.githubusercontent.com/114423111/204313159-e2ce8545-8b05-42b6-87de-3da7b7f54a3b.png)

I reiniciarem el servidor MariaDB amb la següent comanda:

```
sudo service mariadb.service restart
```

### Instal·lar PHP

Per instal·lar moodle també necessitem el PHP.
Farem les següents comandes per actualitzar les paquests i instal·lar algunes dependències:

```
sudo apt update; sudo apt upgrade
```

```
sudo apt install ca-certificates apt-transport-https programari-properties-common
```
![image](https://user-images.githubusercontent.com/114423111/204314711-ea9ddd0e-9a14-4889-9fb7-287dd1cefb8b.png)

Ara hem d'instal·lar el PPA d'Ondrej. Ho farem amb la següent comanda:

```
sudo add-apt-repository ppa:ondrej/php
```
I ara instal·lem PHP.8:

```
sudo apt install php8.0 libapache2-mod-php8.0
```
I reiniciem el servidor web Apache:

```
sudo systemctl restart apache2
```
## Instal·lació moodle





