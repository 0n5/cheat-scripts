Ruby on Rails
=============

Use RVM or Rbenv version/environment manager


#### Preperation 

	$ gem install bundler
	$ gem install sqlite3


#### Installation

	$ gem install rails


#### Create Project

	$ rails new [PROJECT_NAME] 
	$ rails new [PROJECT_NAME] -d postgresql   # use postgres as default


#### Configuring Database

if using Postgres

	$ sudo -u postgres createuser -s [USERNAME]   # create user
	$ sudo -u postgres psql                       # drop into psql
	=#  \password psql							  # set password
	=#  \q

	$ nano config/database.yml
	
make default look like this:

	default: &default
	  adapter: postgresql
	  encoding: unicode
	  pool: 5
	  host: localhost
	  template: template0 # fixes unicode errors

change variables in Production 

	production:
	  <<: *default
	  database: [APPNAME]_production
	  username: [APPNAME]
	  password: <%= ENV['[APPNAME]_DATABASE_PASSWORD'] %>
	  template: template0   # fixes unicode errors
	

#### Configure Environment Variables

if using rbenv 

	$ cd ~/.rbenv/plugins
	$ git clone https://github.com/sstephenson/rbenv-vars.git
	$ cd /railsapp
	$ rake secret
	$ nano .rbenv-vars
	
add to the file:

	SECRET_KEY_BASE='[SECRET]'
	[APPNAME]_DATABASE_PASSWORD='[PASSWORD]'

save and exit

	$ rbenv vars
	

#### Create Production Database

	$ RAILS_ENV=production rake db:create


#### Gems

[RubyGems](https://rubygems.org/) <br>
[Ruby Toolbox](https://www.ruby-toolbox.com/)

Installation

	$ nano GemFile

Add to the file:

	gem 'bootstrap-sass', '~> 3.3.6'

Saved and exit. 

	$ bundle

or

	$ gem install [GEM]
	$ gem install [GEM] -v [VERSION_NUMBER]

Updating

	$ gem update [GEM]


Uninstalling

	$ gem uninstall [GEM]
	$ gem uninstall [GEM] -v [VERSION_NUMBER]

Commands

	$ gem list             # lists all local gems
	$ gem search [GEM]     # searches remove gems
	$ gem help             # gem help commands
	$ gem help commands    # lists all available gem commands
	$ gem help [command]   # shows all options available for the command
	$ gem environment      # shows all path and environment info
	$ gem content [GEM]    # lists all files in gem

#### Running Web Server

	$ rails s

go to localhost:3000


If on Cloud9 IDE:

	$ rails s -b $IP -p $PORT
	$ RAILS_ENV=production rails s -b $IP -p $PORT


#### Structure

when rails new [APP] is run:

	project-name/
		app/
			assets/
				images/
				javascripts/
				stylesheets/
			controllers/
				application_controller.rb
			helpers/
			mailers/
			models/
			views/
				layouts/
					application.html.rb
		bin/
		config/
			environments/
			initializers/
			locales/
			application.rb
			boot.rb
			database.yml
			environment.rb
			routes.rb
			secrets.yml
		db/
		lib/
		log/
		public/
		test/
		tmp/
		vendor/
			assets/
			    javascripts/
			    stylesheets/
		config.ru
		Gemfile
		Gemfile.lock
		Rakefile
		README.rdoc
	README.md


#### Scaffolding Models

	$ rails generate scaffold movie title:string hotness:integer image_url:string\
	                                synopsis:text rating:string genre:string\
	                                director:string runtime:string user_id:integer\
	                                --no-stylesheets

creates the following:

    db/migrate/YYYYMMDDHHMMSS_create_movies.rb
    app/models/movie.rb
    test/models/movie_test.rb
    test/fixtures/movies.yml
    route resources :movies
    app/controllers/movies_controller.rb
    app/views/movies
    app/views/movies/index.html.erb
    app/views/movies/edit.html.erb
    app/views/movies/show.html.erb
    app/views/movies/new.html.erb
    app/views/movies/_form.html.erb
    test/controllers/movies_controller_test.rb
    app/helpers/movies_helper.rb
    app/views/movies/index.json.jbuilder
    app/views/movies/show.json.jbuilder
    app/assets/javascripts/movies.coffee
    

    $ rake db:migrate

go to localhost/[model] for crud form


#### Migrations

	$ rake db:migrate                        # migrates current environment
	$ RAILS_ENV=test rake db:migrate         # migrates test environment
	$ RAILS_ENV=production rake db:migrate   # migrates production environment

Structure:

	db/migrate/

format:

	YYYYMMDDHHMMSS_create_[DESCRIPTION].rb


Create Migration to change data types

	$ rails g migration change_data_type


``` ruby

	class change_data_type < ActiveRecord::Migration
	  def change
	    change_column :[TABLE], :[COLUMN], :[DATA_TYPE]
	  end
```

Rolling Back Migration

	$ rake db:migrate:down VERSION=[VERSION_NUMBER]


methods:

	add_column :[TABLE], :[COLUMN], :[DATA_TYPE]      # adds column
	change_column :[TABLE], :[COLUMN], :[DATA_TYPE]   # adds column	
	add_index :[TABLE], :[COLUMN]                     # adds index
	remove_column :[TABLE], :[COLUMN]                 # removes column


#### Assets


	$ RAILS_ENV=production rake assets:precompile    # precompiles files to public/assets
	$ rake assets:clobber	                         # removes assets

View changes in production

w/ nginx + unicorn

	$ RAILS_ENV=production rake assets:precompile
	$ service unicorn_[APPNAME] restart
	$ service nginx restart


#### Routes


	/config/routes.rb

	$ rake route   # shows all routes application is using

set application root

	$ nano config/routes.rb

add to the file:

	root '[MODEL]#[VIEW]'


#### Validation

[Active Record Validations docs](http://guides.rubyonrails.org/active_record_validations.html)

	$ nano /app/models/[MODEL].rb

edit the file:

``` ruby

	class [MODEL_CLASS] < ActiveRecord::Base

		validates :[FIELD], presence: true
		validates :[FIELD], numericality: true, :allow_nil => true
		validates :[FIELD], length: { minimum: 3 }
	end
```

save and exit


#### Models

	$ rails g model [MODEL] [FIELD]:references [FIELD]:string
	$ rails g model [MODEL] [FIELD]:references [FIELD]:string -p   # previews generation

	$ rake db:migrate
	$ rake db:migrate RAILS_ENV=test    # migrates test environment


creates:

      invoke  active_record
      create    db/migrate/20160406054455_create_[FIELD].rb
      create    app/models/[FIELD].rb
      invoke    rspec
      create      spec/models/[FIELD]_spec.rb

associations

has_many:

	$ nano app/models/item.rb

``` ruby

belongs_to :user

```

	$ nano app/models/user.rb

``` ruby

has_many :items

```


#### Controllers

	$ rails g controller [CONTROLLER] [ACTION]
	$ rails g controller [CONTROLLER] [ACTION] -p  # preview without running	

creates the following:

    app/controllers/pages_controller.rb
    route  get 'pages/home'
    app/views/pages
    app/views/pages/home.html.erb
    test/controllers/pages_controller_test.rb
    app/helpers/pages_helper.rb
    app/assets/javascripts/pages.coffee
    app/assets/stylesheets/pages.scss


#### Flashing

	$ nano app/views/layouts/application.html.erb

add to the file:


``` ruby 

</body>

<%= flash.each do |type, message| %>
  <div class ="alert flash" <%= type %>">
    <%= message %>
  </div>
<% end %>

```

#### Database

	$ rake db:purge   # removes all models, data from database


