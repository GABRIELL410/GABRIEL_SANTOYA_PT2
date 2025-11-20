# GABRIEL_SANTOYA_PT2
Primero te registras en IsardVDI una vez entres, arriba a la derecha le das donde pone "Escritorio Nuevo", luego le pones el nombre que quieres y seleccionas la plantilla que quieras tambien.
# Instal·lació del gestor d’arxius Nextcloud:
Instal·lació de LAMP stack a Ubuntu 24.04
Per instal·lar una pila LAMP (Linux, Apache, MySQL, PHP) a Ubuntu 24.04, segueix aquests passos detallats. Aquesta guia assumeix que comences amb un sistema net d’Ubuntu 24.04 i tens privilegis sudo.

1. Actualitza el sistema
sudo apt update && sudo apt upgrade -y
2. Instal·la Apache
sudo apt install apache2 -y
Activa i inicia el servei:

sudo systemctl enable apache2
sudo systemctl start apache2
Verifica l’estat:

sudo systemctl status apache2
Visita http://localhost per veure la pàgina per defecte d’Apache.

3. Instal·la MySQL
Ubuntu 24.04 ja inclou el paquet mysql-server als repositoris oficials (versió 8.0 o superior):

sudo apt install mysql-server mysql-client -y
Inicia i habilita el servei:

sudo systemctl enable mysql
sudo systemctl start mysql
Configura de MySQL:

Accés a la consola de MySQL
sudo mysql
Creació de la base de dades
CREATE DATABASE bbdd;
Creació de l’usuari local
CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
GRANT ALL PRIVILEGES ON bbdd.* TO 'usuario'@'localhost';
FLUSH PRIVILEGES;
EXIT;


