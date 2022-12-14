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

El primer ha fer és instal·lar moodle des de la pàgina oficial. Això ho hem de fer des de el nostre ordinador amfitrió ja que el servidor ubuntu no té interficie gràfica.
Farem la següent comanda per descargar moodle al servidor:

```
wget <link de l'arxiu que hem descarregat a la màquina amfirtriona>
```
![image](https://user-images.githubusercontent.com/114423111/204319129-b9aa370d-5e77-410f-a299-8efc9ef59ea0.png)

I el descomprimim i el movem al director /var/www/html/

![image](https://user-images.githubusercontent.com/114423111/204319441-314c187c-8edc-4c1d-99b6-aa113ac23b0f.png)

Ara hem de canviar el propietari del lloc web:

![image](https://user-images.githubusercontent.com/114423111/204320103-d62dba4c-0d29-4efb-91ca-4060da1eb955.png)

Ara hem de crear el directori de fitxers:
(Les següents comandes jo vaig fer-les anteriorment, per això no les he introduït)

![image](https://user-images.githubusercontent.com/114423111/204320979-5855e451-76d5-4f86-96eb-e052e11c3164.png)


#### Configuració de la base de dades:

Per accedir a la base de dades MariaBD hem d'introduïr la següent comanda:

![image](https://user-images.githubusercontent.com/114423111/204321583-0eead15b-16be-43b8-ab8c-4f592986e076.png)

Creem un usuari per a moodle, per exemple moodlemanager:

```
CREATE USER 'moodlemanager'@'localhost' IDENTIFIED BY 'managermoodle';
```

I creem la base de dades per a moodle:

```
CREATE DATABASE moodle;
```

I ara li hem de donar accés a la base de dades a l'usuari moodlemanager:

```
GRANT ALL PRIVILEGES ON moodle.* TO 'moodlemanager'@'localhost';
FLUSH PRIVILEGES;
```

I si introdiïm al buscador de la màquina amfitriona la IP del servidor i moodle ens ha de d'apareixer la següent pantalla:

![image](https://user-images.githubusercontent.com/114423111/204323058-dc5b1a42-7680-41cc-8ba5-3ad2409adda9.png)

Ara si sel·leccionem un idioma i li donem a "next" ens sortira aquests errors:

![image](https://user-images.githubusercontent.com/114423111/204330870-c4f7f53e-6796-4982-a505-fe717f37c8aa.png)

Que els solucinarem instal·lant les extensions que ens demana de la següent forma:

Instal·lar PHP CURL:
![image](https://user-images.githubusercontent.com/114423111/204331311-3a110acf-aa37-4eac-96c2-42045273d70b.png)

Parent directory (/var/www) is not writeable. Data directory (/var/www/moodledata) cannot be created by the installer.
Instal·lar PHP Zip:

![image](https://user-images.githubusercontent.com/114423111/204331499-4d909891-4b20-40f8-a081-33d8789cf208.png)

A la següent finestra hem de ficar la carpeta que nosaltres hem creat anteriorment, si no la posem, no funcionarà.

![image](https://user-images.githubusercontent.com/114423111/204349005-80ddb08e-fa5f-49fc-a29d-87110a082fa5.png)

Si passem a la següent finestra ens sortirà per configurar les credencials del usuari administrador i la informació sobre l'ubicaió.

![Selecció_388](https://user-images.githubusercontent.com/114423111/208475365-1e9fe3f9-a647-42af-88b1-5967729a41ad.png)


I a la mateixa finestra ens sortirà el nom que volem ficar-li al nostre moodle:

![Selecció_389](https://user-images.githubusercontent.com/114423111/205711578-d94957b2-790e-4a05-aa7b-34bd01732e63.png)

I també ens sortirà per configurar els correus de suport i el correu de "correo saliente".

![Selecció_390](https://user-images.githubusercontent.com/114423111/205712576-1feaa28f-985b-46f5-b101-874cb4117361.png)

Un cop amb tot això fet la instal·lació ja estarà completada.

