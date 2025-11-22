# Configuració del sistema de virtualització (IsardVDI):
![](https://github.com/GABRIELL410/GABRIEL_SANTOYA_PT2/blob/main/Captura%20de%20pantalla%20de%202025-11-21%2014-28-59.png)
# 1. en aquest apartat hem de registrar-nos en IsardVDI
una vegada estiguem dintre, li donarem al boto blau que esta en la esquena dreta, que posa 'escriptori nou'. 
# 2. posar el nom que volem a la nostra maquina virtual
jo he posat el meu nom propi, pero es pot posar qualsevol nom.

# 3. Escollir alguna de les versions que hi ha
la que hem escollit ha sigut 	ubuntu-24.04-desktop, que ens pemet instalar el nextcloud.





























# Ara tenim que instalar el Nextcloud




# 1. Actualitza el sistema

- sudo apt update && sudo apt upgrade -y

# 2. Instal·la Apache
- sudo apt install apache2 -y
# Activa i inicia el servei:
para activar y iniciar el servei posa aquest comand
- sudo systemctl enable apache2
- sudo systemctl start apache2

# Verifica l’estat:

sudo systemctl status apache2
Visita http://localhost per veure la pàgina per defecte d’Apache.

# 3. Instal·la MySQL
Ubuntu 24.04 ja inclou el paquet mysql-server als repositoris oficials (versió 8.0 o superior):

sudo apt install mysql-server mysql-client -y

# Inicia i habilita el servei:

sudo systemctl enable mysql

sudo systemctl start mysql

# Configura de MySQL:

Accés a la consola de MySQL
sudo mysql
Creació de la base de dades
CREATE DATABASE bbdd;
Creació de l’usuari local
CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
GRANT ALL PRIVILEGES ON bbdd.* TO 'usuario'@'localhost';
FLUSH PRIVILEGES;
EXIT;
Nota: Aquest usuari només pot connectar-se des del servidor local (localhost), cosa que és suficient si l’aplicació web i la base de dades estan al mateix servidor.

# 4. Instal·la PHP i extensions comunes

Ubuntu 24.04 inclou PHP 8.3 als repositoris estàndard:

sudo apt install php libapache2-mod-php php-mysql php-curl php-gd php-mbstring php-xml php-zip php-json php-cli -y

# Reinicia Apache per carregar PHP:

sudo systemctl restart apache2
Verifica la versió de PHP:

php -v
# Crea un fitxer de prova:

echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php
Visita http://localhost/info.php per veure la informació de PHP.

Mesura de seguretat: Un cop hagis verificat que funciona, elimina el fitxer:

sudo rm /var/www/html/info.php
Verificació final
La pila LAMP ara hauria d’estar operativa amb:

Apache servint pàgines web.
MySQL preparat per emmagatzemar dades.
PHP processant scripts.
