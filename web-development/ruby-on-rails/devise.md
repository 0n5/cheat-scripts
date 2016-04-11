Devise
======

#### Installation

	$ echo "gem 'devise'" >> 'Gemfile'
	$ bundle install
	$ rails generate devise:install

creates the following:

	config/initializers/devise.rb
    config/locales/devise.en.yml

add root path to routes

    $ nano config/routes.rb

add to the file:

    root to: '[CONTROLLER]#index'

add flash messages:

    $ nano app/views/layouts/application.html.erb

addo to the file:

    <p class="notice"><%= notice %></p>
    <p class="alert"><%= alert %></p>

Prevent precompiling assets

    $ nano config/application.rb

add to the file:

    $ config.assets.initialize_on_precompile = false


#### Create User Model

	$ rails g devise user

creates the following: 

    db/migrate/YYYYMMDDHHMMSS_devise_create_users.rb
    app/models/user.rb
    test/models/user_test.rb
    test/fixtures/users.yml
    route  devise_for :users	

run migration:

	$ rake db:migrate

Paths:

	/users/sign_in
	/users/sign_up

Functions:

	new_user_session_path         # login path
    new_user_registration_path    # user registration 
    edit_user_registration_path   # edit user account
	destroy_user_session_path     # logout path
    current_user                  # current logged in user


Conditionals:

``` ruby

	<% if current_user %>    # content bound by conditional
		...
	<% end %>
```

Navbar Links for Template

    <% if user_signed_in? %>
        <%= link_to current_user.name, edit_user_registration_path %>
        <%= link_to "Log Out", destroy_user_session_path, method: :delete %>
    
    <% else %>
        <%= link_to "Register", new_user_registration_path %>
        <%= link_to "Log in", new_user_session_path %>
    <% end %>


#### Create Admin Model
	
	$ rails g devise Admin

creates the following: 

    db/migrate/YYYYMMDDHHMMSS_devise_create_admins.rb
    app/models/admin.rb
    test/models/admin_test.rb
    test/fixtures/admins.yml
    app/models/admin.rb
    route  devise_for :admins

    $ rake db:MIGRATION_FILE


Paths:

	/admins/sign_in
	/admins/sign_up


#### Generate Views

	$ rails generate devise:views

creates the following:

    app/views/devise/shared
    app/views/devise/shared/_links.html.erb
    app/views/devise/confirmations
    app/views/devise/confirmations/new.html.erb
    app/views/devise/passwords
    app/views/devise/passwords/edit.html.erb
    app/views/devise/passwords/new.html.erb
    app/views/devise/registrations
    app/views/devise/registrations/edit.html.erb
    app/views/devise/registrations/new.html.erb
    app/views/devise/sessions
    app/views/devise/sessions/new.html.erb
    app/views/devise/unlocks
    app/views/devise/unlocks/new.html.erb
    app/views/devise/mailer
    app/views/devise/mailer/confirmation_instructions.html.erb
    app/views/devise/mailer/password_change.html.erb
    app/views/devise/mailer/reset_password_instructions.html.erb
    app/views/devise/mailer/unlock_instructions.html.erb


#### Add field to Devise Model


``` ruby

	class AddFieldToUser < ActiveRecord::Migration
	# class name must be same as migration name

	  def change
	    add_column :users, :[FIELD], :string
	  end

	end
```

Edit User Registration form

	$ nano app/views/devise/registrations/new.html.erb
	$ nano app/views/devise/registrations/edit.html.erb

add to both the file:


``` ruby

	<%= f.input :[FIELD], required: true %>

```


Modify Controller to persist data and sanitize:

	$ nano app/controllers/application_controller.rb

``` ruby 

class ApplicationController < ActionController::Base

    protect_from_forgery with: :exception
    before_filter :configure_permitted_parameters, if: :devise_controller?

    protected

        def configure_permitted_parameters
            devise_parameter_sanitizer.for(:sign_up) { |u| u.permit(:[NEWFIELD], :email, :password) }
            devise_parameter_sanitizer.for(:account_update) \
            { |u| u.permit(:[NEWFIELD], :email, :password, :current_password) }
        end
end

```








