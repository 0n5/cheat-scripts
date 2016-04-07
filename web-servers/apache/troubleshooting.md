Apache troubelshooting
======================

Workflow 

* check logs
* is Apache installed?
* is Apache running?
* check for syntax and config errors with automatic tools
* are ports open?
* is DNS configured properly
* check DocumentRoot path is correct in Virtualhost config file
* check DirectoryIndex path is correct in Virtualhost config file
* does Apache have correct permissions to serve files?
* is .htaccess file being used and is it overriding settings?

#### Restart Service

	$ service apache2 restart   # restart ubuntu
	$ service httpd restart     # restart rhel

	$ service apache2 reload    # reload ubuntu
	$ service httpd reload      # reload rhel

#### Logging

	$ tail -f /var/log/apache2/error.log   # log errors in real time; ubuntu
	$ tail -f /var/log/httpd/error_log     # log errors in real time; rhel

	$ tail -f /var/log/apache2/access.log  # log server access in real time; ubuntu
	$ tail -f /var/log/httpd/access_log    # log server access in real time; rhel


#### Debugging

	$ apachectl -t           # automatic syntax checker  ubuntu
	$ httpd -t               # automatic syntax checker   rhel

	$ apachectl configtest   # auto config file checker ubuntu

	$ apache2ctl -S          # checks virtualhost settings; ubuntu
	$ httpd -S    		     # checks virtualhost settings; rhel

	$ netstat -plunt | grep apache2  # check if apache process is running; ubuntu
	$ netstat -plunt | grep httpd    # check if apache process is running; rhel

	$ nc -z -v your_ip_address 80    # netcat port scan HTTP
	$ nc -z -v your_ip_address 443   # netcat port scan HTTPS

	$ host -t A yoursite.com         # check DNS resolution
