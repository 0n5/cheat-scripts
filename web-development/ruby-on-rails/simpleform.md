Simple Form
===========

#### Installation

	$ echo "gem 'simple_form'" >> 'Gemfile'
	$ bundle install
	$ rails generate simple_form:install --bootstrap   # adds forms with bootstrap classes

creates the following:

    config/initializers/simple_form.rb
    config/initializers/simple_form_bootstrap.rb
    config/locales/simple_form.en.yml
    lib/templates/erb/scaffold/_form.html.erb

#### Usage

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

#### Collections



``` ruby

<%= f.input :user_id, collection: User.all, label_method full_name %>

```