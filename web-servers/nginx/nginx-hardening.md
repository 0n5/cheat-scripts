Nginx Hardening
===============

#### Disable server_tokens

prevents nginx from displaying version on error pages

```
server {

	server_tokens        off;
	
```

#### Block User Agents, Bad Bots

	nano blockedagents.rules

add to the file:

```
map $http_user_agent $blockedagent {
default           0;  # not blocked
~Pingdom          0;  # not blocked
~Googlebot        0;  # not blocked
~*malicious       1;  # all 1's are blocked
~*bot             1;
~*backdoor        1;
"~*^Bigfoot"      1;
"~*^Black.Hole"   1;
"~*^BlackWidow"   1;
~*wget            1; # block to prevent site downloads
~*curl            1; # block to prevent site downloads
```

add to the server block:

```
include /etc/nginx/blockuseragents.rules;

server {

    if ($blockedagent) {
        return 403;
    }


```

testing: 

	wget --user-agent "[BANNED BOT]" [YOUR-IP-ADDRESS]
	


#### Verb Management

```
server {

	if ($request_method !~ ^(GET|HEAD|POST)$) {
	return 444;
	}

}

```