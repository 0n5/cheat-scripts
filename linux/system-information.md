System Information
==================

#### Version information

	$ cat /etc/issue   # distribution version
	$ lsb_release -a   # distribution Version
	$ uname -a         # kernel version

#### Processes

	$ ps aux               # detailed list of running processes
	$ ps -ef               # process list
	$ ps aux | grep root   # prints out all running root processes

	$ cat /proc/cpuinfo   # shows all info about cpu, flags, cache size etc
	$ cat /proc/iomem     # shows all memory locations currently in use

#### Services

	$ service --status-all
	$ service [SERVICE] status   # checks status of service

#### Disk information

	$ df -h                  # disk usage info
	$ mount                  # lists disks and file systems

	$ mount /dev/sda1  /mnt/usbkey   # mount usb drive that doesnt auto mount

#### Shells

	$ cat /etc/shells    # lists all of the shells available to a system
	$ history            # view users terminal history
	$ !5                 # executes line 5 in history

