Nginx Configuration for Flask + Rails multi site
================================================

``` bash

upstream app {
  server unix:/path/to/myproject.sock fail_timeout=0;
}
 
upstream app1 {
   server unix:/path/to/shared/sockets/unicorn.sock fail_timeout=0;
}

server {
    listen 80;
    server_name example.com www.example.com;
    root /path/to/app/app;
    access_log /path/to/app/app/logs/error.log;


   location / {
        alias /path/to/app;
        include proxy_params;
        proxy_read_timeout 300s;
        proxy_pass http://app;
}

    location ^~ /static/ {
	alias /path/to/app/app/static/;
	autoindex on;
}	

  location /railsapp {
    alias /path/to/app/public;
    try_files $uri/index.html $uri @unicorn_proxy;
   }

  location @unicorn_proxy {
    proxy_pass http://app1;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header Host $http_host;
    proxy_redirect off;

  }

  location ~ ^/assets/ {
    root /path/to/app/public;
    expires 1y;
    add_header Cache-Control public;
    add_header ETag "";
    break;
  }
}


```