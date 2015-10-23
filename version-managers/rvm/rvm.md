RVM (ruby version manager)
==========================

RVM cheat sheet (official): [http://cheat.errtheblog.com/s/rvm](http://cheat.errtheblog.com/s/rvm)

#### Requirements

Install commmand line tools:

	$ xcode-select --install


#### Installation:

	$ echo "gem: --no-document" >> ~/.gemrc
	$ \curl -sSL https://get.rvm.io | bash -s stable

Add path to bash_profile (if not already there):

    [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"

Reload the profile: 

    $ source ~/.bash_profile


#### Using RVM

	$ rvm list
	$ rvm list gemsets

	$ rvm system        # fallback to using system installed ruby
	$ rvm user 2.x.x    # use RVM ruby  


#### Installing Ruby version

	$ su [ADMIN_USER]
	$ rvm install 2.x.x


#### Using Ruby Version

	$ su [ADMIN_USER]
	$ bash --login
	$ rvm use 2.x.x


#### Remove RVM

	$ sudo rvm implode
	$ sudo rm /etc/rvmrc
	$ gem uninstall rvm

Remove environment variables in bash_profile file
Check to make sure that there are no more variables set: 

	$ env | grep -i rvm

