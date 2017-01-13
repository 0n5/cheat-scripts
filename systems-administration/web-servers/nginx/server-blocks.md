Nginx server block cheats
=========================

#### Single Default Server Block

	$ mkdir -p /var/www/example.com/html
	$ chown -R $USER:$USER /var/www/example.com/html
	$ chmod -R 755 /var/www

Create sample HTML page for testing

	$ nano /var/www/example.com/html/index.html

Save and exit.

	$ cp /etc/nginx/sites-available/default /etc/nginx/sites-available/example.com
	$ nano /etc/nginx/sites-available/example.com

Edit the file to look like this: 
	
	server {
	    listen 80 default_server;
	    listen [::]:80 default_server ipv6only=on;

	    root /var/www/example.com/html;
	    index index.html index.htm;

	    server_name example.com www.example.com;

	    location / {
	        try_files $uri $uri/ =404;
	    }
	}

Save and exit.

	$ ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
	$ rm /etc/nginx/sites-enabled/default
	$ nano /etc/nginx/nginx.conf

Uncomment this line:

	server_names_hash_bucket_size 64;   # allows for larger domain name sizes

Save and exit.

	$ service nginx restart

Visit example.com/	


