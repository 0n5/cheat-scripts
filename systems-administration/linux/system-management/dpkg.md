dpkg (Debian package)
=====================

#### Install

	dpkg -i [PACKAGE].deb

If it fails because of dependencies:

	apt-get update
	apt-get upgrade
	apt-get install -f
	dpkg -i [PACKAGE].deb
	which [PACKAGE]         # check installation

#### Search

	dpkg --get-selections   # displays all packages on your system
		
#### Remove 

	dpkg --remove [PACKAGE]   # removes package files, binaries but not config file
	dpkg --purge  [PACKAGE]   # removes everything including config file
