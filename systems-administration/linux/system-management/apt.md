apt (advanced package management)
=================================

#### Install

	apt-get install [PACKAGE] -y

#### Update

	apt-get update -y         # updates the repository metadata
	apt-get upgrade -y        # updates all packages that are out of date
	
	apt-get dist-upgrade -y   # upgrades the linux distribution

#### Remove

	apt-get clean             # removes all package files except the lock file
	apt-get auto-clean        # removes packages no longer available on system
	
#### Searching

	apt-cache search [PACKAGE]    # search for packages available in repository
	apt-get -s install [PACKAGE]  # simulates installing package to see messages

#### Sources

	nano /etc/apt/sources.list     # edit sources file
	apt-get source [PACKAGE]       # downloads source so you can compile the program manually

#### Repository Cache

	apt-cache stats              # prints out repository totals info
	apt-cache pkgnames           # lists all names of packages in the apt-cache
	apt-cache depends [PACKAGE]  # prints out a packages dependencies
	apt-cache unmet              # prints out unmet dependencies
