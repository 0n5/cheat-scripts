User & Group Account Management
===============================

#### Account info

	$ id                    # returns current username, group
	$ whoami		        # current logged in username
	$ w                     # all logged on users
	$ last -a               # list of last users logged on
	$ getent passwd | sort  # users in the password database sorted by name


#### Account switching

	$ sudo su         # change to root
	$ sudo -s         # change to root
	$ sudo -i         # change to root

	$ su [USERNAME]   #change to another user


#### User maintenance

	$ adduser [USERNAME]     # creates user with home directory and defaults

	$ passwd [USERNAME]      # change users password
	$ passwd -l [USERNAME]   # lock the users account
	$ passwd -u [USERNAME]   # unlock the users account

	$ userdel [USERNAME]                  # remove user, but leave files
	$ userdel -r [USERNAME]               # remove user, files and home directory 
	$ cat /etc/passwd | grep [USERNAME]   # grep password file for user to ensure deleted


#### Group maintenance

	$ groupadd group_name            # create group
	$ cut -d: -f1 /etc/group | sort  # list all groups sorted by name

	$ usermod -G [GROUPNAME] [USERNAME]        # adds user to group or changes current group
	$ usermod -G [GROUP1],[GROUP2] [USERNAME]  # adds user to two groups
	$ usermod -a  -G [GROUP] [USERNAME]        # adds user to group in addition to current group
	$ groups                                   # prints out current users group

#### Add to Sudoers

	$ sudo visudo

add to the file:
	
	[USERNAME] ALL=(ALL) ALL    # adds user to sudoers
	[GROUPNAME] ALL=(ALL) ALL   # adds group and all of its users to sudoers

#### Manage User Processes

	$ nano /etc/security/limits.conf

Edit the file and change the user's max number of allowable proceses
		
	[USERNAME] hard nproc 25   # hard prevents anymore than limit
	[USERNAME] soft nproc 30   # soft warns anymore than limit
















