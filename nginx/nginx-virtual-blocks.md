Nginx Virtual Blocks
====================

#### Multiple Virtual Blocks

	$ mkdir -p /var/www/example1.com/html 
	$ mkdir -p /var/www/example2.com/html

	$ chown -R $USER:$USER /var/www/example1.com/html   # gives ownership to current user
	$ chown -R $USER:$USER /var/www/example2.com/html

	$ chmod -R 755 /var/www

	$ nano /var/www/example1.com/html/index.html    # create html content to test
	$ nano /var/www/example2.com/html/index.html

	$ cp /etc/nginx/sites-available/default /etc/nginx/sites-available/example1.com  # copy config file
  	$ cp /etc/nginx/sites-available/default /etc/nginx/sites-available/example2.com

  	$ nano etc/nginx/sites-available/example1.com

 Edit the server block file:

	 server {
	    listen 80 default_server;
	    listen [::]:80 default_server ipv6only=on;

	    root /var/www/example1.com/html;
	    index index.html index.htm;

	    server_name [your_host_name_or_ip];

	    location /page1 {
	        try_files $uri $uri/ =404;
	    }
	}

Save and exit.

	$ nano etc/nginx/sites-available/example2.com

Edit the server block file:

	server {
	    listen 80;
	    listen [::]:80;

	    root /var/www/example2.com/html;
	    index index.html index.htm;

	    server_name [your_host_name_or_ip];

	    location /page2 {
	        try_files $uri $uri/ =404;
	    }
	}

Save and exit.

	$ ln -s /etc/nginx/sites-available/example1.com /etc/nginx/sites-enabled/
    $ ln -s /etc/nginx/sites-available/example2.com /etc/nginx/sites-enabled/

    $ rm /etc/nginx/sites-enabled/default    # removes and disables default block


    $ nano /etc/nginx/nginx.conf

Edit the conf file and uncomment this line:

	server_names_hash_bucket_size 64;  # prevents server name length error


	$ service nginx restart 


Visit example1.com/page1 & Visit example2.com/page2





