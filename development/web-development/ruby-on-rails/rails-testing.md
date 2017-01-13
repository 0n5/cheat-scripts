Rails testing
=============

#### Rspec

	$ nano Gemfile

add to the file: 

``` ruby 

group :development, :test do
    gem 'rspec-rails', '~> 2.0' 
end

group :test do 
    gem 'capybara', '~> 2.1.0'
end

```

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


Run all tests

	$ rake spec
	$ rake spec spec/features   # runs all tests in features folder

Formats

	$ spec --format=documentation spec/path/to/test.rb   # prints out name of test when running


#### Shoulda Matchers

	$ nano Gemfile

add to the file: 

``` ruby 
group :test do
  gem 'shoulda-matchers', '~> 3.1'
end

```

	$ bundle


	$ nano /spec/views/spec_helper

add configuration to the file:


``` ruby

Shoulda::Matchers.configure do |config|
  config.integrate do |with|
    # Choose a test framework:
    with.test_framework :rspec

    # Choose one or more libraries:
    with.library :active_record
  end
end

```

#### Rspec Helpers

	$ mkdir /spec/support
	$ nano helpers.rb

``` ruby

module Helpers
	def some_function(a)
		// some code
	end

```

enable helper

	$ nano /spec/views/spec_helper.rb
 
make the file look like this: 

``` ruby

	RSpec.configure do |config|
		config.include Helper, type:feature

```






