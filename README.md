# Dharmpal Local Dependencies
#### Pre-requisites
- Docker [Manual](https://docs.docker.com/install/)
- Post Docker Installation [Link](https://docs.docker.com/install/linux/linux-postinstall/)
- Reatart PC, and login docker.
- Docker-compose [Manual](https://docs.docker.com/compose/install/)
----
#### Install DB / Queue Servers
```
$ sudo docker-compose up -d
```
Following Services Will Be Installed
| Name      | Default Port      | Password      |
|---        |---                |---            |
| Mongo  	| 27017  	        | -             |
| MySQL  	| 3307  	        | root:root     |
| Redis  	| 3379  	        | -             |
| Postgres  | 5432  	        | postgres:postgres  	|
| Elasticsearch | 9200  	    | -             |
| Logstash  | 9300  	        | -  	        |
| Kibana  	| 5601  	        | -  	        |
| RabbitMQ  | 5672  	        | -  	        |
---
#### Install Dockerized Development Environment
Install make
```
$ sudo apt install make
```
A common development environment for all devices, any OS that can run docker.
```
$ cd DevEnv
$ make update
$ make install MOUNTDIR=<ABSOLUTE-PATH-DEV-DIRECTORY> SHELLRC=<PATH-TO-SHELL-RC>
```
***Notes:***
1. ABSOLUTE-PATH-DEV-DIRECTORY = Directory where your projects will be stored on your host / hard drive   
Eg. MOUNTDIR=/home/User/Projects
2. PATH-TO-SHELL-RC = Path to shell script that runs whenever it is started interactively.  
Eg. For 'bash' shell, SHELLRC=~/.bashrc   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For 'zsh' shell, SHELLRC=~/.zshrc   
> make install MOUNTDIR=/home/hx SHELLRC=~/.zshrc
#### Adding Virtual Hosts (VHOST) to RabbitMQ
1. Replace <user> with username (eg. admin)
2. Replace <password> with password (eg. admin)
3. Replace <vhost_name> with name for virtual host (eg. MailAPIService)
```
# Add User
rabbitmqctl add_user <user> <password>
# Create VHOST
rabbitmqctl add_vhost <vhost_name>
# Give <user> permission to <vhost_name>
rabbitmqctl set_permissions -p <vhost_name> <user> ".*" ".*" ".*"
# Give <user> management rights
rabbitmqctl set_user_tags <user> management
```