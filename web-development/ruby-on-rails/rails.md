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


#### Gems

[RubyGems](https://rubygems.org/)
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

Commands

	$ gem list             # lists all local gems
	$ gem search [GEM]     # searches remove gems
	$ gem help             # gem help commands
	$ gem help commands    # lists all available gem commands
	$ gem help [command]   # shows all options available for the command
	$ gem environment      # shows all path and environment info

#### Running Web Server

	$ rails s

go to localhost:3000


If on Cloud9 IDE:

	$ rails s -b $IP -p $PORT


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


#### Rspec

	$ nano Gemfile

Add to file:

``` ruby

group :development, :test do
	gem 'rspec-rails', '~> 2.0'	
end

group :test do 
	gem 'capybara', '~> 2.1.0'
end


```

save and exit

	$ bundle
	$ bin/rails generate rspec:install

Creates the following:

	.rspec
    spec
    spec/spec_helper.rb

Configuration

	$ nano spec/spec_helper.rb

Add to the top of file under last require:

	$ require 'capybara/rspec'

	$ bundle binstubs rspec-core
	$ git rm -rf /test       # remove default test directory


Testing

	$ rake spec


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

	$ rake db:migrate                 # migrates current environment
	$ rake db:migrate RAILS_ENV=test  # migrates test environment


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



#### Database

	$ rake db:purge   # removes all models, data from database



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

#### Bootstrap

	$ echo "gem 'twitter-bootstrap-rails', :git => 'git://github.com/seyhunak/twitter-bootstrap-rails.git'" >> 'Gemfile'
	$ bundle install
	$ rails generate bootstrap:install static

creates or modifies the following files:

	app/assets/javascripts/application.js
    app/assets/javascripts/bootstrap.js.coffee
    app/assets/stylesheets/bootstrap_and_overrides.css
    config/locales/en.bootstrap.yml
    app/assets/stylesheets/application.css


#### Simple Form

	$ echo "gem 'simple_form'" >> 'Gemfile'
	$ bundle install
	$ rails generate simple_form:install --bootstrap   # adds forms with bootstrap classes

creates the following:

    config/initializers/simple_form.rb
    config/initializers/simple_form_bootstrap.rb
    config/locales/simple_form.en.yml
    lib/templates/erb/scaffold/_form.html.erb

usage

``` ruby

<%= simple_form_for @user do |f| %>
  <%= f.input :username %>
  <%= f.input :password %>
  <%= f.button :submit %>
<% end %>

```

overwriting default classes

``` ruby 

<%= simple_form_for @user, defaults: { input_html: { class: 'default_class' } } do |f| %>
  <%= f.input :username, input_html: { class: 'special' } %>
  <%= f.input :password, input_html: { maxlength: 20 } %>
  <%= f.input :remember_me, input_html: { value: '1' } %>
  <%= f.button :submit %>
<% end %>

```

Collections



``` ruby

<%= f.input :user_id, collection: User.all, label_method full_name %>

```

#### Nokogiri

	$ echo "gem 'nokogiri'" >> 'Gemfile'
	$ bundle install
	$ nano config/initializers/noko.rb

create file and add:

``` ruby

	require 'nokogiri'
	require 'open-uri'
```

usage

	$ irb
	$ doc = Nokogiri::HTML(open("[URL"))    # parse HTML file
	$ doc = Nokogiri::HTML(open("[URL"))    # parse XML file

	$ doc.css('script').remove                            # removes inline Javascript
	$ doc.at("//h1[@itemprop = 'name']").text             # returns text at h1 tag matching 
															the element given in query
	$ doc.at("//span[@itemprop = 'rating']").text.to_i    # returns integer from text in element
	$ doc.at_css('#movie-image-section img')['src']       # selects text at css id


#### Sass


files appended with .scss extension


Structure

Rename application.css file .scss

	app/assets/stylesheets/application.scss    # all scss files must be imported here
	app/assets/stylesheets/styles.scss
	app/assets/stylesheets/tools.scss
	app/assets/stylesheets/variables.scss

Importing

In application.scss file:

	@import "bootstrap"
	@import "styles	"
	@import "tools"
	@import "variables"
