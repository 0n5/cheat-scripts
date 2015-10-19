Linux anti-forensics
====================

#### Bash History

	$ echo "" > ~/.bash_history          # clear bash history of current user
	$ rm ~/.bash_history -rf             # delete bash history file
	$ history -c                         # clear current terminal session history
	$ ln /dev/null ~/.bash_history -sf   # permantly send all bash history to dev null

	$ unset HISTFILE                     # must log out after setting
	$ export HISTFILESIZE=0              # sets history max lines to 0
	$ export HISTSIZE=0                  # sets history max commands to 0

#### Shredding

	-v: verbose
	-f: allow writes
	-z: overwrite to hide shredding
	-n: number of times to overwrite 

	shred -f -u file                     # overwrite and delete file
	shred -vfz -n 10 /dev/sda5           # overwrite hard drive partition 10 times
