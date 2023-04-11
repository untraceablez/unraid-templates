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

![console link](accessing-container.png)