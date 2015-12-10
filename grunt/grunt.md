Grunt
=====

Requirements: install NVM (node version manager)

#### Installation
	
	$ nvm use stable
	$ npm update -g npm
	$ npm install -g grunt-cli


#### Usage

After creating package.json and Gruntfile.js

	$ grunt

--save will add the module to the package.json file 

#### grunt-init

	$ npm install -g grunt-init



#### grunt-reponsive-images

requires ImageMagick

	$ npm install grunt-responsive-images --save

add to the Gruntfile

	grunt.loadNpmTasks('grunt-responsive-images');