#### THIS SETUP WILL CONTINUALLY BE UPDATED
#### BASIC ASSUMPTION: Operating System is Ubuntu 20.04 LTS

## System Admin Setup
1) Install git -   sudo apt install git
2) Install Emacs - sudo apt install emacs
3) Install ShellCheck - sudo apt install shellcheck
4) Install network tools: sudo apt install net-tools
5) Install unzip:  sudo apt install unzip
6) Tools: sudo apt install curl wget
7) Install OpenSSH Server:  sudo apt-get install openssh-server
8) Install Haproxy: https://haproxy.debian.net/
9) Install Nginx:  sudo apt install nginx
10) Install htop: sudo apt-get install htop -y
11) Install inxi: sudo apt install inxi
    

Resource
ssh-keygen guide: https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-20-04


## C Setup
1) Install basic setup -   sudo apt install build-essential
2) Install Betty:
   	- Clone the repo to your local machine - git clone https://github.com/holbertonschool/Betty.git
   	- cd into the Betty directory
   	- Install the linter -   sudo ./install.sh
   	- emacs or vim a new file called betty, and copy the script below:
   	  	```
		#!/bin/bash
		# Simply a wrapper script to keep you from having to use betty-style
		# and betty-doc separately on every item.
		# Originally by Tim Britton (@wintermanc3r), multiargument added by
		# Larry Madeo (@hillmonkey)

		BIN_PATH="/usr/local/bin"
		BETTY_STYLE="betty-style"
		BETTY_DOC="betty-doc"

		if [ "$#" = "0" ]; then
		    echo "No arguments passed."
		    exit 1
		fi

		for argument in "$@" ; do
		    echo -e "\n========== $argument =========="
		    ${BIN_PATH}/${BETTY_STYLE} "$argument"
		    ${BIN_PATH}/${BETTY_DOC} "$argument"
		done
	e) Once saved, exit file and change permissions to apply to all users -   chmod a+x betty
	f) Move the betty file into /bin/ directory or somewhere else in your $PATH with sudo mv betty /bin/


4) Setup emacs to use Betty Linter for C - https://sage.hashnode.dev/using-holbertons-betty-linter-for-c-on-emacs


## Python Setup
1) Install Python -	 sudo apt install python3 (this installs Python3. This is the choice)  
2) Install Pycodestyle - sudo apt install pycodestyle
3) Install pip -         sudo apt install pip
4) Install pipx -        sudo apt install pipx  (used for local installs into a project's root directory)
5) Install venv  -       sudo apt install python3.8-venv  (according to your python version)
6) Install virtualenv -  sudo python3 -m pip install virtualenv
7) sudo apt-get install python3-distutils
8) sudo apt-get install python3-dev
9) sudo apt install python3-dev build-essential
10) sudo apt-get install libmysqlclient-dev
11) sudo apt-get install zlib1g-dev
12) sudo pip3 install mysqlclient
13) sudo pip3 install SQLAlchemy
14) pip3 install redis
15) pip3 install pymongo



## JavaScript/TypeScript Setup
1) Install node version manager
	- curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
	- source ~/.bashrc
2) Install a version of node:
	- nvm install v16.17.0  (Node version manager can do a lot more things. Google its uses.)
3) package.json inside every main project directory:
   	- npm init (step by step, press enter to skip. OR
	- npm init -y (everything default)
4) for npm:
   	- local dependency - npm i <packageName>  (inside every main project directory, after npm init)
	- global dependency - npm install -g <packageName>  (Using <sudo> command with npm is not recommended. Try not to use global dependency)
	- dev dependencies - npm install <packageName> --save-dev
5) create a .gitignore file inside every main project directory that contains </node_modules> to not push the node_modules folder
6) Packages to install:
   	- local dependency:
		- express:    npm install express --save
		- ionic:      npm install -g @ionic/cli
		- sequelize:  npm install sequelize
		- AWS SDK:    npm install aws-sdk
		- Dotenv:     npm install dotenv --save
		- bcrypt:     npm install bcrypt
		- serverless: npm install -g serverless
	- dev dependency:
		- nodemon:  npm install nodemon --save-dev
		- bcrypt:   npm install @types/bcrypt --save-dev  **
		- mocha:    npm install mocha --save-dev
		- chai:     npm install chai --save-dev
		- typescript:
			- npm install typescript --save-dev
			- npm install ts-node --save-dev
			- npm install @types/node --save-dev
			       
			      
learning resource: John Smilga's repo ( git clone https://github.com/john-smilga/node-express-course.git )


## Deno
Installation: `curl -fsSL https://deno.land/install.sh | sh`

learning resource: https://docs.deno.com/runtime/manual/


## MySQL
1) sudo apt update
2) sudo apt install mysql-server
3) sudo systemctl start mysql.service
4) sudo mysql
5) mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_password';
6) mysql> exit
7) sudo mysql_secure_installation
NB:
==
This will take you through a series of prompts where you can make some changes to your MySQL installation’s security options. The first prompt will ask whether you’d like to set up the Validate Password Plugin, which can be used to test the password strength of new MySQL users before deeming them valid. If you elect to set up the Validate Password Plugin, any MySQL user you create that authenticates with a password will be required to have a password that satisfies the policy you select.
After selecting your password, From there, you can press Y and then ENTER to accept the defaults for all the subsequent questions. This will remove some anonymous users and the test database, disable remote root logins, and load these new rules so that MySQL immediately respects the changes you have made.

8) mysql -u root -p
9) mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH auth_socket;
10) mysql> exit
11) sudo mysql
12) mysql> CREATE USER 'codart'@'localhost' IDENTIFIED BY 'whatever_password_you_want';
13) mysql> GRANT ALL PRIVILEGES ON *.* TO 'codart'@'localhost';
16) mysql> FLUSH PRIVILEGES;
17) mysql> exit

### Test
Login-  mysql -u <username> -p
It will prompt you for your password.
Then exit-  mysql> exit

### Check- sudo mysqladmin -p -u <username> version

Reference -   https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04
Install workbench:   sudo snap install mysql-workbench-community

To uninstall mysql comletely, refer -  https://askubuntu.com/questions/640899/how-do-i-uninstall-mysql-completely
Again, READ ALL THIS GUIDE AND THE REFERENCES CAREFULLY BEFORE DOING ANYTHING



## PostgreSQL
ND: version 14 is now outdated
1) sudo apt install postgresql-common
2) sudo sh /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh
3) sudo apt install postgresql-14

### Setup
	- Switch to default superuser "postgres",
	- run utility "createuser" to create a superuser same name as current login.
	- "$USER" is an environment variable denoting the current login user.
		- sudo -u postgres createuser --superuser $USER

	- Create the default database which shall be the same as the username.
		- sudo -u postgres createdb $USER

	- Login in to server via "psql" with user "postgres"
		- sudo -u postgres psql

	- Change password for current logged in OS user
		postgres=# \password "user"
		Enter new password: xxxx
		Enter it again: xxxx

Reference: https://www3.ntu.edu.sg/home/ehchua/programming/sql/PostgreSQL_GetStarted.html


## Redis SETUP
1) curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg
2) echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list
3) sudo apt update
4) sudo apt install redis
5) sudo vim /etc/redis/redis.conf (supervised is set to `no` by default. Change it to `systemd`.
6) sudo systemctl restart redis.service
Reference: https://redis.io/docs/getting-started/installation/install-redis-on-linux/


## MongoDB SETUP
1) curl -fsSL https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
2) echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
3) sudo apt update
4) sudo apt install mongodb-org
5) sudo systemctl start mongod.service
Reference: https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-20-04


## Docker Setup
Install Reference:
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04
https://docs.docker.com/desktop/install/ubuntu/
NB: resolve the dependencies like "qemu-system-x86" and set up "pass"

Important Docker Commands
- docker context list [use] (to see which docker system you are using)
- docker ps {-a}     (to see all docker processes)
- docker build -t <image_name> .  (build an image)
- docker images   (to see your images)
- docker login --username=<dockerhub_username>  (optional: to login to dockerhub if you have not already done so)
- docker tag <image_name>:<image_tag> <dockerhub_username>/<dockerhub_repo_name>:<image_name>    (to tag an image to be pushed)
- docker push <dockerhub_username>/<dockerhub_repo_name>:<image_name>     (to push docker image)
(Google "docker login" for how to login to dockerhub from the cli and refer to



## Minikube Setup
Prerequisite: Fully functional Docker installation
Installation:
	- curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
	- sudo dpkg -i minikube_latest_amd64.deb

Reference: https://minikube.sigs.k8s.io/docs/start/



## Amazon Web Services
### INSTALL AWS CLI TOOL
1) curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
2) unzip awscliv2.zip
3) sudo ./aws/install

#### Configuration and setup
1) setup:  aws configure
NOTE:
	a) prefered output format is json
	b) default profile name is default
	c) if you already have a default profile (an existing profile) setting up new profiles is done as: aws configure --profile <profile-name>
2) confirm setup:
	aws configure list 
	aws configure list-profiles
3) protect sensitive information
	export AWS_CONFIG_FILE=~/.aws/config
	export AWS_SHARED_CREDENTIALS_FILE=~/.aws/credentials
4) Testing setup
	##### If you've just one profile set locally
	aws iam list-users
	##### If you've multiple profiles set locally
	aws iam list-users --profile <profile-name>

NB: Updating specific variable configuration is done via the following syntax
Syntax
aws configure set <varname> <value> [--profile profile-name]
For example
aws configure set default.region us-east-2
aws configure set default.aws_session_token "Your-value"

### INSTALL AWS EB CLI TOOL
Ensure you have the following installed - git, python3 and virtualenv (instructions to get these were described)
1) Clone the repo - git clone https://github.com/aws/aws-elastic-beanstalk-cli-setup.git
2) Install/Upgrade - python3 ./aws-elastic-beanstalk-cli-setup/scripts/ebcli_installer.py
3) Move to path  - sudo echo 'export PATH="~/.ebcli-virtual-env/executables:$PATH"' >> ~/.bash_profile && source ~/.bash_profile     (the prompt will give more direction on this final step)
4) Use pip to get the EB CLI - pip install awsebcli --upgrade
			       pip install awsebcli --upgrade --user
5) Verify the install - eb --version
6) Usage:
	- eb init      (in project root directory to setup the eb configuration)
	- eb create    ( when you're ready to deploy)

Reference - https://github.com/aws/aws-elastic-beanstalk-cli-setup
	    https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-linux.html

#### Installation for AWS SDK for JavaScript is referenced in the JavaScript/TypeScript section
Reference - https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/installing-jssdk.html


## Kafka
### Installation
1) sudo adduser kafka
2) sudo adduser kafka sudo
3) su -l kafka
4) mkdir ~/Downloads
5) curl "https://downloads.apache.org/kafka/3.5.0/kafka_2.12-3.5.0.tgz" -o ~/Downloads/kafka.tgz
6) mkdir ~/kafka && cd ~/kafka
7) tar -xvzf ~/Downloads/kafka.tgz --strip 1

### Configuration
1) vim ~/kafka/config/server.properties
   	- Change the value of `log.dirs` to `/home/kafka/logs`
   	- Append the following to the file `delete.topic.enable = true`
2) sudo vim /etc/systemd/system/zookeeper.service
   	- Enter the following unit definition into the file:
   		```
   	  	[Unit]
		Requires=network.target remote-fs.target
		After=network.target remote-fs.target

		[Service]
		Type=simple
		User=kafka
		ExecStart=/home/kafka/kafka/bin/zookeeper-server-start.sh /home/kafka/kafka/config/zookeeper.properties
		ExecStop=/home/kafka/kafka/bin/zookeeper-server-stop.sh
		Restart=on-abnormal

		[Install]
		WantedBy=multi-user.target

3) sudo vim /etc/systemd/system/kafka.service
   	- Enter the following unit definition into the file:
   	  	```
   	  	[Unit]
		Requires=zookeeper.service
		After=zookeeper.service

		[Service]
		Type=simple
		User=kafka
		ExecStart=/bin/sh -c '/home/kafka/kafka/bin/kafka-server-start.sh /home/kafka/kafka/config/server.properties > /home/kafka/kafka/kafka.log 2>&1'
		ExecStop=/home/kafka/kafka/bin/kafka-server-stop.sh
		Restart=on-abnormal

		[Install]
		WantedBy=multi-user.target

4) sudo systemctl start kafka
5) sudo systemctl status kafka
6) sudo systemctl enable zookeeper
7) sudo systemctl enable kafka

### Hardening
1) sudo deluser kafka sudo
2) sudo passwd kafka -l

Reference - https://www.digitalocean.com/community/tutorials/how-to-install-apache-kafka-on-ubuntu-20-04



## Puppet Setup
### Install Pupppet:
- sudo apt-get install -y ruby
- sudo apt-get install -y ruby-augeas
- sudo apt-get install -y ruby-shadow
- sudo apt-get install -y puppet
- sudo apt -y install puppet-module-puppetlabs-stdlib
	
### Install puppet-lint:
sudo gem install puppet-lint

Emacs puppet-mode: M-x package-install RET puppet-mode


## Fabric
[The below is to be saved in a file and executed]
```
#!/usr/bin/env bash
#Install nginx on a server and start it
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get autoremove && sudo apt-get autoclean
sudo pip3 uninstall Fabric
sudo apt install python3-testresources
sudo apt-get install libffi-dev
sudo apt-get install libssl-dev
sudo apt-get install build-essential
sudo apt-get install python3.4-dev
sudo apt-get install libpython3-dev
sudo pip3 install pyparsing
sudo pip3 install appdirs
sudo pip3 install setuptools==40.1.0
sudo pip3 install cryptography==2.8
sudo pip3 install bcrypt==3.1.7
sudo pip3 install PyNaCl==1.3.0
sudo pip3 install Fabric3==1.14.post1
```


## Momento Setup
1) Create account:
   	```
	momento account signup aws \
	--email YOUR_EMAIL \
	--region us-east-1
3) Setup: momento configure


## Other Resources
- Install Postbird :- sudo snap install postbird
- Install Postman :- sudo snap install postman
- Use Sentry for bug reporting :- https://sentry.io/
- Use Siege for concurrency testing :- https://www.joedog.org/siege-manual/
- Use Datadog for monitoring - https://www.datadoghq.com/
- Use SqlDBM for database modelling - https://sqldbm.com/Home/
- Use Balsamiq for ui mockups - https://balsamiq.com/


## Dev Resources
a) https://developer.mozilla.org/en-US/
b) https://www.digitalocean.com/community/tutorials
