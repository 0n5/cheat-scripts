RVM (ruby version manager)
==========================

RVM cheat sheet (official): [http://cheat.errtheblog.com/s/rvm](http://cheat.errtheblog.com/s/rvm)

#### Requirements

Install commmand line tools:

	$ xcode-select --install


#### Installation:

	$ echo "gem: --no-document" >> ~/.gemrc   # do not install gem docs
	$ \curl -sSL https://get.rvm.io | bash -s stable

Add path to bash_profile (if not already there):

    [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"

Reload the profile: 

    $ source ~/.bash_profile


#### Finding Ruby Versions & gems

	$ rvm list
	$ rvm list gemsets
	$ rvm list known

#### Installing Ruby version

	$ su [ADMIN_USER]
	$ rvm install 2.x.x

#### Using Ruby Versions

	$ su [ADMIN_USER]
	$ bash --login

	$ rvm use 2.x.x    # use RVM ruby  
	$ rvm system       # fallback to using system installed ruby


#### Remove RVM

	$ sudo rvm implode
	$ sudo rm /etc/rvmrc
	$ gem uninstall rvm

Remove environment variables in bash_profile file
Check to make sure that there are no more variables set: 

	$ env | grep -i rvm

