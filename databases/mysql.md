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


#### Install Drivers

PyMySQL

	$ pip install pymysql


#### Create Database

	$ msyql -u [USERNAME] -p
	mysql> create database [DATABASE];
	mysql> show databases;

Create User

	msyql> create user '[USERNAME]'@'localhost' indentified by '[PASSWORD';

Grant Access to User

	mysql> grant all privileges on *.* to '[USERNAME'@'localhost';


#### Query Database

	$ mysql -u [USERNAME] -p
	mysql> show databases;
	mysql> use [DATABASE];

Show Schema

	mysql> describe [DATABASE].[TABLE];

Query Table

	mysql> select * from [TABLE];


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


