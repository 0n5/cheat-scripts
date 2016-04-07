Rails testing
=============

#### Rspec

	$ nano Gemfile

add to the file: 

``` ruby 

group :development, :test do
	gem 'rspec-rails', '~> 2.0'	
end

```

	$ bundle

Run all tests

	$ rake spec

Formats

	$ spec --format=documentation spec/path/to/test.rb   # prints out name of test when running


#### Capybara

	$ nano Gemfile

add to the file: 

``` ruby 
group :test do 
	gem 'capybara', '~> 2.1.0'
end

```

	$ bundle

#### Shoulda Matchers

	$ nano Gemfile

add to the file: 

``` ruby 
group :test do
  gem 'shoulda-matchers', '~> 3.1'
end

```

	$ bundle


	$ nano spec_helper

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




