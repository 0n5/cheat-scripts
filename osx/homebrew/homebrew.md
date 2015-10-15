Homebrew Package Manager 
========================

#### Installation

Must be admin/root

	$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Files are installed in the cellar

	$ cd /usr/local && find cellar

#### Commands


	$ brew search              # search for available applications
	$ brew list                # lists all applications installed by homebrew

	$ brew install [NAME]  # installs application using homebrew

	$ brew remove [NAME]   # removes application

	$ brew doctor              # diagnoses common problems


#### Brewfiles
	
	$ brew tap Homebrew/bundle
	$ nano Brewfile

Add to the file:

	brew 'ack'
	brew 'cowsay'
	brew 'htop'
	brew 'imagemagick'
	brew 'openssl'
	brew 'tig'
	brew 'tree'
	brew 'vnstat'
	brew 'wget'

Save file, exit and run:
	
	$ brew bundle

Create new Brewfile with installed packages

	$ brew bundle dump --force


