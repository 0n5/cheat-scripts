Nginx cheats
============

#### Install

	apt-get udpate
	apt-get install nginx

upgrade

	apt-get upgrade nginx

#### Start/stop/restart

	service nginx start
	service nginx restart
	service nginx reload
	service nginx stop

#### Logging

to override default, add to each server block:

	error_log /var/log/nginx/[SERVER_NAME].error.log error;
    access_log /var/log/nginx/[SERVER_NAME].access.log;

#### Error Pages

	mkdir /etc/nginx/[ERROR_PAGE_DIRECTORY]

add to the server block

```
	server {
	    error_page 401 403 404 /404.html;
	    location = /404.html {
	            root /etc/nginx/[ERROR_PAGE_DIRECTORY]/;
	            internal;
	    }
	}

```