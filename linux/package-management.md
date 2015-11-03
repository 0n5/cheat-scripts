Package Management
==================

#### Apt

Installs

	$ apt-get install [PACKAGE] -y

Updates

	$ apt-get update -y         # updates the repository metadata
	$ apt-get upgrade -y        # updates all packages that are out of date
	
	$ apt-get dist-upgrade -y   # upgrades the linux distribution

Removal 

	$ apt-get clean             # removes all package files except the lock file
	$ apt-get auto-clean        # removes packages no longer available on system
	
Searching

	$ apt-cache search [PACKAGE]    # search for packages available in repository
	$ apt-get -s install [PACKAGE]  # simulates installing package to see messages

Sources

	$ nano /etc/apt/sources.list     # edit sources file
	$ apt-get source [PACKAGE]       # downloads source so you can compile the program manually

Repository Cache

	$ apt-cache stats              # prints out repository totals info
	$ apt-cache pkgnames           # lists all names of packages in the apt-cache
	$ apt-cache depends [PACKAGE]  # prints out a packages dependencies
	$ apt-cache unmet              # prints out unmet dependencies


#### Dpkg

Installs

	$ dpkg -i [PACKAGE].deb

If it fails because of dependencies:

	$ apt-get update
	$ apt-get upgrade
	$ apt-get install -f
	$ dpkg -i [PACKAGE].deb
	$ which [PACKAGE]         # check installation

Search

	$ dpkg --get-selections   # displays all packages on your system
		
Removal 

	$ dpkg --remove [PACKAGE]   # removes package files, binaries but not config file
	$ dpkg --purge  [PACKAGE]   # removes everything including config file


#### Aptitude

	$ aptitude  # launches GUI

Installs

	$ aptitude install [PACKAGE]

Updates

	$ aptitude update   # updates repository metadata

Search

	$ aptitude search [PACKAGE]

#### Tar

Create

	$ tar cf [FILE].tar [FILES]        # create tar package
	$ tar czf [FILE].tar.gz [FILES]    # creates tar.gz package
	$ tar cjf [FILE].tar.bz2 [FILES]   # creates .bz2 package

Extract 

	$ tar xf [FILE].tar        # extract tar
	$ tar xzf [FILE].tar.gz    # extract tar.gz
	$ tar xjf [FILE].tar.bz2   # extract tar.bz2

#### Zip

Create

	$ zip -r [FILE].zip [DIRECTORY]    # creates zip archive of the directory and subs
