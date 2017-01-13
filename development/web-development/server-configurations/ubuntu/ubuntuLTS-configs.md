Ubuntu LTS configuration & Hardening
=======================================

#### SSH

    nano /etc/ssh/sshd_config

change or add the following:

```
    Port [PORT_NUMBER]  # change ssh port to non standard
    Protocol 2          # ensure ssh v.2 is used
    PermitRootLogin no  # disable root login after non root user created
    DebianBanner no     # prevent broadcasting of ssh banner

```

    service ssh restart  # if using Digital Ocean power cycle machine


#### UFW

    apt-get install ufw
    ufw allow [PORT_NUMBER]
    ufw enable

Restart system

    reboot
    ufw status verbose  # check status
    

#### Cloud 9 setup

    apt-get update
    apt-get install nodejs
    apt-get install npm


#### System


Secure shared Memory

    nano /etc/fstab
    
add the following:

```

tmpfs     /run/shm     tmpfs     defaults,noexec,nosuid     0     0

```

persist changes (or reboot):

    mount -a

#### Sysctrl 

    nano /etc/sysctl.conf    

add to the file:

```
    # IP Spoofing protection
    net.ipv4.conf.all.rp_filter = 1
    net.ipv4.conf.default.rp_filter = 1
    
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
    net.ipv4.tcp_syncookies = 1
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
    
    # Disable IPV6 
    net.ipv6.conf.all.disable_ipv6 = 1
    net.ipv6.conf.default.disable_ipv6 = 1
    net.ipv6.conf.lo.disable_ipv6 = 1


```

reload sysctrl:

    nano sysctrl -p


#### IRQBALANCE

disable to avoid hardware interrupts in threads

    nano /etc/default/irqbalance

edit the file:

```
    ENABLED=0

```


#### /tmp

    dd if=/dev/zero of=/usr/tmpDSK bs=1024 count=1024000
    mkfs.ext4 /usr/tmpDSK
    # creates 1GB filesystem for tmp partition in usr directory

    cp -avr /tmp /tmpbackup
    # creates backup of tmp directory

    mount -t tmpfs -o loop,noexec,nosuid,rw /usr/tmpDSK /tmp
    chmod 1777 /tmp
    # mount partition to /tmp

    cp -avr /tmpbackup/* /tmp/
    rm -rf /tmpbackup
    # copy the backup into the new tmp directory

    nano /etc/fstab
    # set /tmp dir in fstab

add to the file:

```

/usr/tmpDSK /tmp tmpfs loop,nosuid,noexec,rw 0 0

```

    mount -a


#### /var/tmp

    mv /var/tmp /var/tmpold
    ln -s /tmp /var/tmp
    cp -avr /var/tmpold/* /tmp/
    # creates a symbolic link to new /tmp directory

#### Heartbleed

Check version:

    openssl version -v

Anything older than Mon Apr 7 20:33:29 UTC 2014 is vulnerable

    apt-get update
    apt-get upgrade openssl libssl-dev
    apt-cache policy openssl libssl-dev

Check version again:

    openssl version -b  # check version


#### Shellshock

Run script to determine if vulnerable:

    env i='() { :;}; echo Your system is Bash vulnerable' bash -c "echo Bash vulnerability test"

If vulnerable:

    apt-get update ; sudo apt-get install --only-upgrade bash



#### Fail2ban

    apt-get update
    apt-get install fail2ban
    
configure:

    cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local

start:
    
    service fail2ban start
