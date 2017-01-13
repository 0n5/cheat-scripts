Rbenv
=====

Ruby environment manager

#### Installation

	$ git clone https://github.com/rbenv/rbenv.git ~/.rbenv

	$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
	$ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
	$ source ~/.bash_profile  # reload profile 
	$ rbenv                   # test installation 
	$ which ruby              # check ruby binary path, should be rbenv shim


#### Ruby-Build plugin

	$ git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build


#### Installing Ruby

	$ rbenv install 2.x.x


#### Choosing a version

	$ rbenv global 2.x.x.
	$ ruby -v    # check the version


#### Installing Gems

	$ gem install bundler
	$ rbenv rehash