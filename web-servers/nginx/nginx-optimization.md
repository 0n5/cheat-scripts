Nginx Optimization
==================

#### Client Directives

	nano /etc/nginx/conf.d/buffer.conf

add to the file:

```

client_body_buffer_size  128k;
# handles POST actions sent from client
client_header_buffer_size 1k;
client_max_body_size 8m;
# max size of client request
large_client_header_buffers 4 4k;

```

Including in server block not needed since conf file has `include /etc/nginx/conf.d/*.conf;` rule

