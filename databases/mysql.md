MySQL
=====

#### Install for LAMP stack

	$ apt-get update
	$ apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql mysql-client


#### Install on OSX

[MySQL Community Edition](https://dev.mysql.com/downloads/mysql/)

	$ nano ~/.bash_profile

add to the file:

	export PATH=$PATH:/usr/local/mysql/bin

save and edit.


#### Secure MySQL installation

	$ apt-get install mysql-server
	$ mysql_secure_installation

#### Install Drivers

PyMySQL

	$ pip install pymysql


#### Create Database

	$ msyql -u [USERNAME] -p
	mysql> create database [DATABASE];
	mysql> show databases;

#### Users

Create User

	msyql> create user '[USERNAME]'@'localhost' indentified by '[PASSWORD]';

Create Remote User

	msyql> create user '[USERNAME]'@'[HOST]' indentified by '[PASSWORD]';

Show Users

	mysql> select * from mysql.user;
	mysql> select host, user, password from mysql.user;

Change Username

	mysql> use mysql;
	mysql> update user set user='[NEW_USERNAME]' where user='[OLD_USERNAME]';

Grant Access to User

	mysql> grant all privileges on *.* to '[USERNAME'@'[HOST]';
	mysql> grant update, alter, delete, select on [DATABASE].* to '[USERNAME'@'[HOST]';

Grant Access to Remote User

	mysql> grant all on [DATABASE].* to [USER]@'[REMOTE_USER_IP]' identified by '[PASSWORD]';
	mysql> flush privileges;

Show Grants

	mysql> show grants for '[USER]'@'[HOST]';

Delete User

	mysql> drop user '[USER]'@'[HOST]';


#### Query Database

	$ mysql -u [USERNAME] -p
	mysql> show databases;
	mysql> use [DATABASE];

Show Schema

	mysql> describe [DATABASE].[TABLE];

Query Table

	mysql> select * from [TABLE];


#### Configuration

	$ nano /etc/mysql/my.cnf

In [mysqld] section:

Binding:
	
	bind-address = 0.0.0.0        # Will bind to any IP address
	bind-address = 127.0.0.1      # Will bind to localhost
	bind-address = [IP_ADDRESS]   # Will bind to specific IP address 

Disable local file loading:

	local-infile=0



#### Remote Connection

	$ mysql -u [USER] -h [IP_ADDRESS] -p

#### Backup Database

	$ mysqldump -u root -p[PASSWORD] [DATABASE] > dumpfilename.sql


#### Restore Database

	$ mysql -u root -p[PASSWORD] [DATABASE] < dumpfilename.sql	

#### Troubleshooting

Workflow

* Check if mysql is running using netstat
* Make sure nothing else is running on port 3306; if so, kill it
* Check if mysql is running on correct port
* Check mysql logs at /var/log
* Check bind address configuration 
* Make sure skip networking is disabled
* Make sure socket is correct in /etc/my.cnf file
* Is firewall blocking incoming mysql connections on port 3306?
* Does user have correct privileges to mysql?

Check if mysql is running

	$ ps aux | grep mysql

or

	$ netstat -tap | grep mysql

Restart Mysql

	$ service mysql restart

or

	$ /etc/init.d/mysql restart


Check if mysql is using the correct port

	$ less /etc/mysql/my.cnf

if incorrect edit the file using nano and restart service 


Check mysql logs

	$ tail /var/log/mysql.err
	$ tail /var/log/mysql.log

Check bind address

	$ less /etc/mysql/my.cnf

if bind-address=localhost; edit and add your ip address or delete alltogether and restart


Disable skip networking

	$ less /etc/mysql/my.cnf


make sure skip-networking is commented out; if not, edit with nano and restart


Check socket variable

	$ less /etc/mysql/my.cnf


if socket= /var/lib/mysql/mysqld.sock is set to anything else edit with nano and restart service


Grant user permission to connect to mysql

	$ msyql -u root -p

enter pwd

	> GRANT ALL PRIVILEGES ON *.* TO 'testuser'@'localhost';   

Resetting root pwd

	$ service mysql stop

or 

	$ /etc/init.d/mysql stop   
	$ mysqld_safe --skip-grant-tables  # start in safe mode

	> mysql -u root -p

enter password

	> use mysql;
	> update user set password=PASSWORD("new password") where USER='root';
	> flush privileges;
	> quit

	$ mysql -u root -p

login with new credentials

Remove mysql

	$ apt-get remove --purge mysql-server mysql-client mysql-common
	$ apt-get autoremove
	$ apt-get autoclean
	$ rm -rf /etc/mysql /var/lib/mysql /var/lib/mysql



