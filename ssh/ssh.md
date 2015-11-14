SSH cheats
=======================

#### Create key pair

	$ ssh-keygen -t rsa    # generates a key pair

Copy public key in authorized keys file on server at ~/.ssh

#### Change standard SSH port
	
	$ cp /etc/ssh/sshd_config /etc/ssh/sshd_config_backup   # create back up of config file
	$ nano /etc/ssh/sshd_config

Edit the file:

	# What ports, IPs and protocols we listen for
	Port [new_port]
	# Use these options to restrict which interfaces/protocols sshd will bind to
	#ListenAddress ::
	#ListenAddress 0.0.0.0

Exit and save the file.

	$ sudo service ssh restart

To login:

	$ ssh user@[ip_address] -p [new_port]


#### SSH config alias

	$ nano ~/.ssh/config

Add to this file:

	Host [your_host_name]
	  User [user_name]
	  HostName  [your_ip_address]
	  Port [port_number]
	  IdentityFile [your_private_key_path]

To log in:

	$ ssh [your_host_name]

#### SSH only login

	$ nano /etc/ssh/sshd_config

Edit this line to say:	
    
    PasswordAuthentication no
    ChallengeResponseAuthentication no

Exit and save file.

	$ sudo service ssh restart


#### Disable Root Login

	$ nano /etc/ssh/sshd_config

Change to: 

	PermitRootLogin no

Save and exit. 

	$ sudo service ssh restart







