NVM (Node Version Manager)
==========================

If the bash_profile file does not exist create:

	$ touch ~/.bash_profile 	

#### Installation

	$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash

#### Usage

	$ nvm install stable   # downloads most current stable version of Node
	$ nvm use stable       # specifies which installed version of node to use
