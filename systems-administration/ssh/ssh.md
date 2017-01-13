SSH cheats
==========

#### Create key pair

	ssh-keygen -t rsa    # generates a key pair

Copy public key in authorized keys file on server at ~/.ssh


#### Authorized Keys

	cd ~/.ssh
	nano authorized_keys
	
Add public keys to the file, save and exit. 


#### Change standard SSH port
	
	cp /etc/ssh/sshd_config /etc/ssh/sshd_config_backup   # create back up of config file
	nano /etc/ssh/sshd_config

Edit the file:

```
	# What ports, IPs and protocols we listen for
	Port [new_port]
	# Use these options to restrict which interfaces/protocols sshd will bind to
	#ListenAddress ::
	#ListenAddress 0.0.0.0
```

Exit and save the file.

	reload ssh

To login:

	ssh [USER]@[IP] -p [PORT]


#### SSH config alias

	nano ~/.ssh/config

Add to this file:

```
	Host [HOST]
	  User [USER]
	  HostName  [IP]
	  Port [PORT]
	  IdentityFile [PATH_TO_PRIVATE_KEY]
```

To log in alias:

	ssh [HOST]

#### SSH Key only login

	nano /etc/ssh/sshd_config

Edit this line to say:	
    
```	
	PermitRootLogin without-password

```

Exit and save file.

	reload ssh

#### Prevent Root Login

	nano /etc/ssh/sshd_config

Edit this line to say:

```
	PermitRootLogin no

```
Save and exit. 

	reload ssh
