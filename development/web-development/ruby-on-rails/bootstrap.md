Bootstrap
=========


#### twitter-bootstrap-rails

Installation

	$ echo "gem 'twitter-bootstrap-rails', :git => 'git://github.com/seyhunak/twitter-bootstrap-rails.git'" >> 'Gemfile'
	$ bundle install
	$ rails generate bootstrap:install static

creates or modifies the following files:

	app/assets/javascripts/application.js
    app/assets/javascripts/bootstrap.js.coffee
    app/assets/stylesheets/bootstrap_and_overrides.css
    config/locales/en.bootstrap.yml
    app/assets/stylesheets/application.css


#### less-rails-bootstrap

Installation

	$ nano GemFile

add to the file:

	gem 'therubyracer'  # If using Ruby
	gem 'therubyrhino'  # If using JRuby
	gem 'jquery-rails'  # May already be installed
	gem 'less-rails-bootstrap'

save and exit

	$ bundle install

Configuration

	$ nano application.css
	
add to the file: 
	
	/*
	*= require twitter/bootstrap
	*/

save and exit.

	$ nano application.js

add to the file: 

	//= require jquery
	//= require jquery_ujs
	//= require twitter/bootstrap

save and exit. 