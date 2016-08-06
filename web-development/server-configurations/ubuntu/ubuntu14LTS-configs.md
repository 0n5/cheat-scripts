Ubuntu 14LTS bare metal configurations
======================================

#### Create non root user

    $ useradd -m [USER]
    $ passwd [USER]
    $ adduser [USER] sudo


#### SSH only login

    $ nano /etc/ssh/sshd_config

Edit this line to say:

```
PasswordAuthentication no
ChallengeResponseAuthentication no

```

    $ service ssh restart
    

    
#### Network Security

    $ nano /etc/sysctl.d/10-network-security.conf 
    
add to the file:

``` 
# Ignore ICMP broadcast requests
net.ipv4.icmp_echo_ignore_broadcasts = 1

# Disable source packet routing
net.ipv4.conf.all.accept_source_route = 0
net.ipv6.conf.all.accept_source_route = 0 
net.ipv4.conf.default.accept_source_route = 0
net.ipv6.conf.default.accept_source_route = 0

# Ignore send redirects
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0

# Block SYN attacks
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_synack_retries = 2
net.ipv4.tcp_syn_retries = 5

# Log Martians
net.ipv4.conf.all.log_martians = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1

# Ignore ICMP redirects
net.ipv4.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0 
net.ipv6.conf.default.accept_redirects = 0

# Ignore Directed pings
net.ipv4.icmp_echo_ignore_all = 1

```

    $ service procps start

#### Heartbleed

Check version:

    $ openssl version -v

Anything older than Mon Apr 7 20:33:29 UTC 2014 is vulnerable

    $ apt-get update
    $ apt-get upgrade openssl libssl-dev
    $ apt-cache policy openssl libssl-dev

Check version again:

    $ openssl version -b  # check version
    
#### Shellshock

Run script to determine if vulnerable:

    $ sudo env i='() { :;}; echo Your system is Bash vulnerable' bash -c "echo Bash vulnerability test"

If vulnerable:

    $ sudo apt-get update ; sudo apt-get install --only-upgrade bash

    
#### UFW

    $ apt-get install ufw

Allow to port:

    $ ufw allow [PORT]


Allow to port from IP address:

    $ ufw allow from [IP] to any port [PORT]

Enable:

    $ ufw enable
    $ ufw status

#### Fail2ban

    $ apt-get update
    $ apt-get install fail2ban
    
configure:

    $ cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local





