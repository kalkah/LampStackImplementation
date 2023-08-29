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
