Ruby on Rails
=============


#### Installation

Requires RVM

	$ rvm use 2.x.x
	$ gem install rails


#### Create Project

	$ rails new [PROJECT_NAME] 


#### Install gem (package)

	$ nano GemFile

Add to the file:

	gem 'bootstrap-sass', '~> 3.3.6'

Saved and exit. 

	$ bundle install


#### Controllers

	$ rails g controller [controller] [action]



#### Models

	$ rails g model [MODEL]


#### Migrations

	/db/migrate/[MIGRATION_FILE]_create_[MODEL].rb

Run Migration:

	rake db:migrate


#### Running Web Server with webrick

	$ rails s -b $IP -p $PORT


#### Structure

Configuration Files

	config/initializers


Routes

	config/routes.rb


Controllers

	app/controllers/[CONTROLLER]_controller.rb

Views

Root index page:

	app/views/home/index.html.erb


Layout

	app/views/layouts/application.html.erb


Stylesheets

	app/assets/stylesheets/application.css
	app/assets/stylesheets/styles.css
	app/assets/stylesheets/[CONTROLLER].css

JavaScript
	
	app/assets/javascript/application.js
	app/assets/stylesheets/[CONTROLLER].coffee	
	

Images

	app/assets/images


3rd Party Stylesheets:

	vendor/assets/stylesheets/[VENDOR_CSS]

3rd Party JavaScript

	vendor/assets/stylesheets/[VENDOR_JS]


#### Sass


files appended with .scss extension


#### Structure

Rename application.css file .scss

	app/assets/stylesheets/application.scss    # all scss files must be imported here
	app/assets/stylesheets/styles.scss
	app/assets/stylesheets/tools.scss
	app/assets/stylesheets/variables.scss

#### Importing

In application.scss file:

	@import "bootstrap"
	@import "styles	"
	@import "tools"
	@import "variables"
