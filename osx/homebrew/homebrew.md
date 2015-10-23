Homebrew Package Manager 
========================

#### Installation

Must be admin

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

Must be admin
	
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
	brew 'autoconf'
    brew 'automake'
    brew 'libtool'
    brew 'apple-gcc42'
    brew 'libyaml'
    brew 'libxslt'
    brew 'libksba'
    
Save file, exit and run:
	
	$ brew bundle

Create new Brewfile with installed packages

	$ brew bundle dump --force


#### Troubleshooting

Error: Cannot write to /usr/local/Cellar

	$ chown -R $USER /usr/local


#### Uninstall

Create uninstall shell script:

	#!/bin/sh
	# Just copy and paste the lines below (all at once, it won't work line by line!)
	# MAKE SURE YOU ARE HAPPY WITH WHAT IT DOES FIRST! THERE IS NO WARRANTY!

	function abort {
	  echo "$1"
	  exit 1
	}

	set -e

	/usr/bin/which -s git || abort "brew install git first!"
	test -d /usr/local/.git || abort "brew update first!"

	cd `brew --prefix`
	git checkout master
	git ls-files -z | pbcopy
	rm -rf Cellar
	bin/brew prune
	pbpaste | xargs -0 rm
	rm -r Library/Homebrew Library/Aliases Library/Formula Library/Contributions 
	test -d Library/LinkedKegs && rm -r Library/LinkedKegs
	rmdir -p bin Library share/man/man1 2> /dev/null
	rm -rf .git
	rm -rf ~/Library/Caches/Homebrew
	rm -rf ~/Library/Logs/Homebrew
	rm -rf /Library/Caches/Homebrew

Make script executable and run.
Clean up:

	$ rm -rf /usr/local/Cellar /usr/local/.git

If "unable to unlink old 'share/doc/homebrew/Acceptable-Formulae.md" error:
	
	$ rm -rf /usr/local



