# uvdesk-unraid

## What is UVDesk?

[**UVDesk**](https://www.uvdesk.com/en/) is a open source helpdesk software solution. It has support for a multitude of features including the following: 

* A multi-customer & multi-agent ticket system.
* A full mailer system to send mail to agents and customers.
* A fully featured knowledge base for self-service.
* CMS Platform Support
* Plugin Support
* Custom branding

## Self-Hosting

### Docker Run / Docker Compose

This is a container template for hosting uvdesk on [unRAID](https://unraid.net/). If you are not using unRAID, there are better `docker-compose` and `docker-run` templates out there, such as the base for this unRAID image, [dietermartens/uvdesk](https://hub.docker.com/r/dietermartens/uvdesk/).

### Non-Docker Setup

If you're looking to install this on a non-containerized system, look to UVDesk's [Official Install Guide](https://github.com/uvdesk/community-skeleton#installation).


### unRAID

Alright, the main event and what this template is made for. If you're running unRAID you should be able to find this template underneath the **Productivity** or **Tools** sections in Community Applications, or by searching for `uvdesk`. 

#### unRAID Requirements

* You will need to have a **local** mySQL or MariaDB instance running on the same docker network as uvdesk. 
    * You will need to create a `uvdesk` database and `uvdesk` user with full privileges on that database *prior* to downloading uvdesk from Community Applications. Please refer to [Setting up the Database](#setting-up-the-database) for instructions.
* You will need a reverse proxy setup. 

#### Setting up the Database

If you don't know how to setup a database in mySQL, it sounds scarier than it is. First, download a mariaDB or mySQL image from Community Applications. After you've done that, click on the container image and hit console: 

![console link on container click](accessing-console.png "Console link")

You should be presented with a terminal pop-up browser window. If not, make sure to allow popups from your server's domain name. 

##### Logging In

You'll first need to login to mysql as root, using the password you made when you generated the mySQL template, as so: 

```
mysql -u root -p
Enter password:
```
Once you paste/type in your password, you should see this: 

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 8.0.32 MySQL Community Server - GPL

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

##### Creating the User

Now we can create the user (uvdesk by default):   

`CREATE USER 'uvdesk'@'localhost' IDENTIFIED BY 'SUPERSECUREPASSWORDHERE';`

You should see this output:
`Query OK, 0 rows affected (0.01 sec)`

##### Creating the Database

Now we create the database (uvdesk by default):
`CREATE DATABASE 'uvdesk'`;

Once again, you should see this output:
`Query OK, 1 rows affected (0.01 sec)`

##### Granting User Privileges on Database

Lastly, we need to give our `uvdesk` user all privileges on the uvdesk database: 

`GRANT ALL PRIVILEGES ON uvdesk.* TO 'uvdesk'@'localhost' IDENTIFIED BY 'SUPERSECUREPASSWORDHERE';`

Once last time, you should see this output:
`Query OK, 1 rows affected (0.01 sec)`

You've now done all the work you'll need to do in mySQL, you can exit the pop-up window or leave by typing `exit`. 