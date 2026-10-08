# Ajout d’une pile AMP au serveur Linux

*Document converti depuis [ve2cuy.com/420-3c3](https://ve2cuy.com/420-3c3/?page_id=871) — dernière modification : 2024-09-26*

---

# Contenu

<img src="images/Ajout-d-une-pile-AMP/mamp.png" alt="" width="128" />

- Connexion au serveur (ssh)
- sudo apt-get update
- sudo apt-get upgrade
- sudo apt-get install apache2
- sudo apache2ctl configtest
- sudo nano /etc/apache2/apache2.conf
- sudo systemctl restart apache2
- http://localhost
- sudo apt-get install mysql-server
- mysql_secure_installation
- sudo apt-get install php libapache2-mod-php php-mcrypt php-mysql
- sudo nano /var/www/html/info.php

# 

# 

---

# Objectif général

À la suite de cet atelier le participant sera en mesure, sur **L**inux, d’installer, d’utiliser et d’effectuer des tests de fonctionnalités des services **A**(pache), **M**(MySQL) et **P**(PHP).

# Prérequis

- Avoir complété l’atelier ‘[Installation d’Ubuntu-Desktop](Virtualisation-d-Ubuntu.md)‘

---

# Voici les étapes d’une installations LAMP

**Mise en contexte**

Une fois le serveur Linux installé, les opérations de mise à jour, d’installation de services et de configuration sont habituellement effectuées à distance, c-a-d, pas directement sur l’ordinateur physique sur lequel roule le système mais plutôt à partir d’une session (ssh) qui peut être à des kilomètres du serveur.

Le serveur Ubuntu que nous avons installé à l’[atelier précédent](Virtualisation-d-Ubuntu.md) ne permet pas, pour l’instant, de connexion à partir d’une autre station réseau.

Si c’était le cas, il serait alors possible de s’y connecter de la façon suivante:

**Action 1a** – À partir de MacOS, connexion ssh au serveur Linux

```
$ ssh utilisateur@SERVER_IP
```

**Action 1b** – À partir de Windows

Utilisation de l’application [putty](http://www.putty.org).

**Note**: Dans notre cas, nous allons utiliser une fenêtre ‘**terminal**‘ à partir du bureau d’Ubuntu.  Un peu plus tard, nous installerons un service de connexion à distance (ssh) sur notre station Ubuntu.

---

## Début de l’installation

**Action 2** – Avant de commencer, il est préférable de vérifier la présence de mises à jour générales du système:

```
$ sudo apt-get update
```

Si c’est le cas, de les installer:

**Action 3** – Installer les mises à jour:

```
$ sudo apt-get upgrade
```

### 

---

### Installation  du serveur Web

**Action 4** – Installer le serveur Apache, à partir des dépôts Ubuntu:

```
$ sudo apt-get install apache2
```

**Action 5** – Démarrer le test de configuration d’Apache:

```
$ sudo apache2ctl configtest
```

```
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using fe80::5054:ff:fe69:a3e0. 
Set the 'ServerName' directive globally to suppress this message

Syntax ok
```

Il n’y a pas d’erreurs de syntaxe dans le fichier de configuration du serveur Apache.

Par contre, il n’est pas en mesure de déterminer le nom de domaine – par exemple, tim.cstj.qc.ca –  du serveur.

Nous allons corriger cette situation.

**Action 5** – Editer la configuration principle du serveur ‘Apache’:

```
$ sudo nano /etc/apache2/apache2.conf
```

**Action 6** – À la fin du fichier, ajouter une référence à `ServerName` pointant sur l’adresse IP:

```
ServerName localhost
```

Note: Cette configuration est temporaire, il faudrait plutôt pointer sur l’adresse du réseau privé que nous avons installé entre l’hôte et l’invité.  Pour afficher cette adresse il suffit de tapper:

```
ip addr
```

Et localiser l’adresse IP qui commence par ‘192.168.56’.

**Action 7** – Enregister le fichier et vérifier si tout est conforme:

```
$ sudo apache2ctl configtest
```

Nous devrions obtenir:

```
Syntax OK
```

**Action 8** – Redémarrer Apache:

```
$ sudo systemctl restart apache2
```

**Action 9** – Ouvrir un fureteur et tester le serveur web:

**Note**: À partir de la session GUI, il suffit d’inscrire l’adresse: **http://localhost** dans le fureteur.

**Note**:  Il est aussi possible de tester le serveur apache à partir de l’hôte en utilisant l’adresse IP de l’invité débutant par 192.168.56.

À vous de tester…

### Dossier racine du serveur Apache

La localisation dossier racine du serveur Apache dépend de la distribution Linux ou de l’application xAMP utilisée.

Sur Ubuntu, ce dossier est:

> /var/www/html

Par défaut, les fichiers et dossiers copiés à cet endroit seront disponibles à partir d’un fureteur web.

---

### Laboratoire

1. Créer, dans le bon dossier, une nouvelle page web – **hello.html** – qui affiche « Bonjour TIM » en `<h1>` et tester dans le fureteur.
2. Retirer à ‘**other**‘ le droit de lecture au fichier **hello.html** et tester dans le fureteur
3. Changer le groupe du fichier **hello.html** pour **www-data** et tester dans le fureteur.

---

### Installer MySQL

À cette étape, nous avons un serveur web en fonction.

Nous allons maintenant installer le gestionnaire de base de données  – SGBD – [MySQL](https://dev.mysql.com/downloads/).

MySQL est disponible dans le dépot Ubuntu , nous allons dons utiliser la commande`apt`

**Action 10** – Installer Mysql

```
$ sudo apt-get install mysql-server
```

Selon la version, durant l’installation, il est possible que nous devrions fournir le mot de passe de l’administrateur de la base de données:

Note: Si c’est le cas, il faut entrer ‘**password**‘ comme mot de passe.

À la fin de l’installation, il est possible de rouler un ‘script’ de configuration du SGBD et ce, dans le but d’en sécuriser l’accès.

**Note**:  Selon la version de la distribution Linux, il est possible qu’il ne soit pas possible de renseigner le mot de passe de l’utilisateur ‘root’ de la BD lors de l’installation.

---

Action 11 – Modifier directement la DB pour renseigner le mot de passe du compte root.

```
$ sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password99';
FLUSH PRIVILEGES;
exit

# Tester le service
sudo mysql -u root -p
```

---

```
Il est aussi possible de sécuriser MySQL avec:
```

```
$ mysql_secure_installation

NOTE: ATTENTION NE PAS UTILISER CETTE COMMANDE SUR VOTRE SERVEUR DE TESTS
```

```
Securing the MySQL server deployment.

Enter password for user root: 

VALIDATE PASSWORD PLUGIN can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD plugin?

Press y|Y for Yes, any other key for No: N
Using existing password for root.
Change the password for root ? ((Press y|Y for Yes, any other key for No) : 

 ... skipping.
By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them. This is intended only for
testing, and to make the installation go a bit smoother.
You should remove them before moving into a production
environment.

Remove anonymous users? (Press y|Y for Yes, any other key for No) : y
Success.

Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network.

Disallow root login remotely? (Press y|Y for Yes, any other key for No) : y
Success.

By default, MySQL comes with a database named 'test' that
anyone can access. This is also intended only for testing,
and should be removed before moving into a production
environment.

Remove test database and access to it? (Press y|Y for Yes, any other key for No) : y
 - Dropping test database...
Success.

 - Removing privileges on test database...
Success.

Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.

Reload privilege tables now? (Press y|Y for Yes, any other key for No) : y
Success.

All done!
```

Nous avons maintenant un SGBD!

### Laboratoire

1. Utiliser la commande mysql -u root -p pour démarrer le client terminal de mySQL
2. Afficher les BD disponibles:  SHOW DATABASES;
3. Sélectionner la BD ‘mysql’: USE mysql;
4. Afficher les tables de la BD courante: SHOW TABLES;
5. Afficher les champs d’une table:  SHOW COLUMNS FROM user;
6. Afficher la liste des utilisateurs: SELECT User, Create_priv FROM user;
7. Créer une nouvelle BD: CREATE DATABASE maBD; SHOW DATABASES;
8. Effacer une BD: DROP DATABASE maBD; SHOW DATABASES;
9. Quitter le client mysql: exit

Références: [Syntaxe SQL](https://dev.mysql.com/doc/refman/5.7/en/sql-syntax.html)

---

### Installer PHP

La prochaine partie de l’installation de notre pile LAMP est php:

**Mise en contexte**

Dans la mesure où l’on nous demande de mettre en place un site Web utilisant WordPress il faudra alors s’assurer que le module du language PHP est installé sur le serveur web.  Wordpress est essentiellement programmé en PHP.

**Action 12** – Installer php:

```
$ sudo apt-get install php libapache2-mod-php php-mysql

# Note: il peut-être aussi nécessaire d'installer le module: php-mcrypt
```

PHP propose une multitude de modules permettant d’enrichir ses fonctionnalités .

Voici comment en obtenir la liste:

```
$ apt-cache search php- | less
```

```
libnet-libidn-perl - Perl bindings for GNU Libidn
php-all-dev - package depending on all supported PHP development packages
php-cgi - server-side, HTML-embedded scripting language (CGI binary) (default)
php-cli - command-line interpreter for the PHP scripting language (default)
php-common - Common files for PHP packages
php-curl - CURL module for PHP [default]
php-dev - Files for PHP module development (default)
php-gd - GD module for PHP [default]
php-gmp - GMP module for PHP [default]
php-ldap - LDAP module for PHP [default]
php-mysql - MySQL module for PHP [default]
php-odbc - ODBC module for PHP [default]
php-pear - PEAR Base System
php-pgsql - PostgreSQL module for PHP [default]
php-pspell - pspell module for PHP [default]
php-recode - recode module for PHP [default]
php-snmp - SNMP module for PHP [default]
php-sqlite3 - SQLite3 module for PHP [default]
php-tidy - tidy module for PHP [default]
php-xmlrpc - XMLRPC-EPI module for PHP [default]
php7.0-cgi - server-side, HTML-embedded scripting language (CGI binary)
php7.0-cli - command-line interpreter for the PHP scripting language
php7.0-common - documentation, examples and common module for PHP

...
```

**Note**:  Pour quitter la liste il faut appuyer sur ‘q’

## EN CAS DE PROBLEME

```
sudo apt remove apache2 libapache2-mod-php libapache2-mod-php8.3 --purge
sudo apt install php8.3 libapache2-mod-php8.3
sudo a2dismod mpm_event
sudo a2enmod mpm_prefork
sudo a2enmod php8.3
```

---

#### Tester PHP

Nous allons maintenant vérifier si le module PHP fonctionne correctement

**Action 13** – Créer le fichier `info.php` dans le dossier racine d’Apache web root – pour Ubuntu il est dans `/var/www/html`:

```
$ sudo nano /var/www/html/info.php
```

**Action 14** – Ajouter le code suivant dans le fichier:

```
<?php
   phpinfo();
?>
```

**Action 15** – Enregistrer le fichier et fermer l’éditeur.

**Action 16** – Tester le script dans un fureteur:

```
http://localhost/info.php
```

---

## Voila, nous avons installé une pile Apache, Php, MySQL sur notre serveur Linux.

Nous allons en tirer profit en installant l’application ‘phpmyadmin’

**Action 17** – Installer ‘phpmyadmin’

PHPMyAdmin est disponible dans le dépôt Ubuntu. Pour l’installer il suffit de tapper:

```
sudo apt install phpmyadmin
```

**Action 18** – Suivre les directives du programme d’installation. Au mot de passe, fournir ‘password’

**Action 19** – Tester phpmyadmin à l’aide d’un fureteur Web:

```
http://localhost/phpmyadmin

ou 

http://127.0.0.1/phpmyadmin

ou à partir de votre poste de travail:

http://192.168.56.102/phpmyadmin  (utiliser l'adresse privée de l'invité)
```

**Note**: En cas de problème:

```
sudo apt remove --purge phpmyadmin
```

et réinstaller!

**Erreur possible** sur mot de passe: [solution](http://Erreur possible: https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-20-04-fr)

**Erreur Possible**:  Page not found, solution:

```
1 - Éditer le fichier: /etc/apache2/apache2.conf

    $ sudo nano /etc/apache2/apache2.conf

2 - Ajouter la ligne suivante à la fin du fichier:

    Include /etc/phpmyadmin/apache.conf

3 - Redémarrer le service apache:

    $ sudo systemctl restart apache2
```

**Note**:  Depuis la version 18 d’ubuntu, l’utilisateur ‘root’ de phpMyAdmin ne peut pas se connecter à distance.

Pour corriger cette situation:

```
$ sudo mysql
mysql> SELECT user,plugin,host FROM mysql.user WHERE user = 'root';
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password99';
mysql> FLUSH PRIVILEGES;
exit
```

---

## Résumé des commandes pour installer la pile LAMP

```
sudo apt-get update && sudo apt-get upgrade
​sudo apt-get install lamp-server^
sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
FLUSH PRIVILEGES;
exit
wget -c https://wordpress.org/wordpress-4.9.16.tar.gz
tar -xzvf wordpress-4.9.16.tar.gz 
sudo mv wordpress/* wordpress/.* /var/www/html
sudo chown www-data:www-data /var/www/html -R
sudo rm /var/www/html/index.html
sudo apt install phpmyadmin
Avec phpmyadmin: Créer un user et une BD pour WP
Lancer l'installation de WP: http://adr-ip
```

**Astuce:**

Certaines distributions Linux proposent une installation LAMP en quelques commandes.  Par exemple, sur Ubuntu il suffit de suivre les étapes suivantes:

```
sudo apt-get update && apt-get upgrade
​sudo apt-get install lamp-server^
```

Prochain atelier – [Installation de WordPress](Installer-WordPress.md)

FIN du document

---

##### Document rédigé par Alain Boudreault – version 2024.09.11

---

[⬅️ Retour à la liste des documents](../README.md)
