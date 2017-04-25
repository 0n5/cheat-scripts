User Accounts
=============

#### Account info

	id                    # returns current username, group
	whoami		          # current logged in username
	w                     # all logged on users
	last -a               # list of last users logged on
	getent passwd | sort  # users in the password database sorted by name

#### Account switching

	sudo su         # change to root
	sudo -s         # change to root
	sudo -i         # change to root

	su [USERNAME]   # change to another user

#### Create User

	adduser [USERNAME]     # creates user with home directory and defaults

#### Change Password

	passwd [USERNAME]      # change users password
	passwd -l [USERNAME]   # lock the users account
	passwd -u [USERNAME]   # unlock the users account


#### Remove User

	userdel [USERNAME]                  # remove user, but leave files
	userdel -r [USERNAME]               # remove user, files and home directory 
	cat /etc/passwd | grep [USERNAME]   # grep password file for user to ensure deleted

#### Manage User Processes

	nano /etc/security/limits.conf

Edit the file and change the user's max number of allowable proceses
		
	[USERNAME] hard nproc 25   # hard prevents anymore than limit
	[USERNAME] soft nproc 30   # soft warns anymore than limit
