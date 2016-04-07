Grunt
=====

Requirements: install NVM (node version manager)

#### Installation
	
	$ nvm use stable
	$ npm update -g npm
	$ npm install -g grunt-cli
	$ npm install grunt --save-dev

#### grunt-init

	$ npm install -g grunt-init
    $ git clone https://github.com/gruntjs/grunt-init-gruntfile.git ~/.grunt-init/gruntfile
    $ grunt-init gruntfile


#### Install dependencies

	$ npm install   # reads from package.json file


#### Usage

After creating package.json and Gruntfile.js

	$ grunt

--save will add the module to the package.json file 


#### grunt-reponsive-images

requires ImageMagick

	$ npm install grunt-responsive-images --save

add to the Gruntfile

	grunt.loadNpmTasks('grunt-responsive-images');


#### grunt-wget

	$ npm install grunt-wget --save
