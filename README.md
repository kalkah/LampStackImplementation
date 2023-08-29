# Documentation for AWS LAMP STACK IMPLEMENTATION

## WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS

### This project shows how to implement LAMP Stack on AWS. LAMP stack comprises of four technologies - Linux, Apache, Mysql and PhP

After launching the Ubuntu virtual server on AWS, the server was updated using the command below

**`Sudo apt update`**

### The Apache2 webserver was installed using the command below

**`Sudo apt install apache2`**

The status of apache2 webserver is confirmed using the command below

**`Sudo systemctl status apache2`**

The image show the status of the apache2 webserver

<img width="551" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/2744430c-7451-4d24-9427-53ab25b6ff5d">

The command below was used to confirm if the server is accessible locally

**`curl http://localhost:80`**  using the DNS name  

<img width="662" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/5c70b3bd-a726-4b95-ae86-a8c436e1a79b">

**`curl http://127.0.0.1:80`** command also does the same thing as the command above  using the IP address that corresponds to the DNS name 'localhost'

<img width="660" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/63bdd848-a144-41a9-9eda-8723d4387c8a">

I also conirmed that the Apache webserver can be access from the internet using the EC2 public address.

**`http://13.53.89.180`**

<img width="895" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/b4383283-cb52-4da7-bf83-62f1cfa47598">

### Mysql was used as the database management system, mysql was installed using the command below

**`sudo apt install mysql-server`**

The following command was used to log in to the MySQL console

**`sudo mysql`**

<img width="486" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/a0b7fae8-3d83-4af1-8dda-6f6b8fa6ab41">

A root user password was set using mysql_native_password as default authentication method.

**`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Password.1';`**

I exit the MySQL console to start MYSQL interactive script using the command below. This remove some insecure default settings and lock down access to the database system. This script also prompt me to configure the validate password plugin.

**`sudo mysql_secure_installation`**
The command below was used to test login access to the MYSQL console

**`sudo mysql -p`** -p flag prompt me for password.

<img width="559" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/33687bb9-8087-4b61-afcd-1d0ea4c710ec">

### The fourth technology in the stack is PHP. PHP process code to display dynamic content to the end user.  PHP was installed with the command below

**`sudo apt install php libaapache2-mod-php php-mysql`** php-mysql is a php module that allow php to communicate with MySQL-based databases. libapache2-mod-php module enable Apache to handle PHP files.

This command **`php -v`** was run to confirm the version of my PHP

<img width="434" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/874794b2-ec97-46d4-8e6b-8da9be01842b">

The LAMP stack is completely installed and operational. Apache Virtual Host that hold website files and folder is needed to test the stack with a PHP script.

### CREATING A VIRTUAL HOST FOR THE WEBSITE USINF APACHE

Directory was created for projectlamp

**`sudo mkdir /var/www/projectlamp`**

The ownership of the directory was assigned with the current user

**`sudo chown -R &USER:$USER /var/www/projectlamp`**

A new configuration file was created and opened in Apache's sites-available directory

**`sudo vi /etc/apache2/sites-available/projectlamp.conf`**

The created file is blank and the following command is pasted in the file.

**<VirtualHost *:80>***
    **ServerName projectlamp**
    **ServerAlias www.projectlamp** 
    **ServerAdmin webmaster@localhost**
    **DocumentRoot /var/www/projectlamp**
    **ErrorLog ${APACHE_LOG_DIR}/error.log**
    **CustomLog ${APACHE_LOG_DIR}/access.log combined**
**</VirtualHost>**

The ls command below was used to list the files in the directory

**`sudo ls /etc/apache2/sites-available`**

<img width="527" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/e061ee1b-de19-45f3-a88c-224bfa780b4d">

The new virual host is enable with a2ensite command

**`sudo a2ensite projectlamp`**

<img width="342" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/64f5eaef-4939-4b04-8b87-3c49baa32cba">

The default site was disable with a a2dissite command

**`sudo a2dissite projectlamp`**

<img width="352" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/cb20c63e-abf1-4c3d-a0f1-21a88aff93ed">

The command below was ran to check for syntax errors in the configuration file

**`sudo apache2ctl configtest`**

<img width="306" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/2512ccc1-5eaf-4bee-890f-98931abca14f">

The Apache service was reloaded for changes to take effect

creating an index file in the projectlamp folder using the command below

**`sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`**

The website was accessed on the browser using the public IP Address: **`http://13.53.89.180:80`** though it works without the port number. DNS name can also be use to access the website.

<img width="604" alt="image" src="https://github.com/kalkah/project-1/assets/95209274/9856de95-43e6-4aef-bb95-f86b6aada8ce">



