Nokogiri
========

#### Installation

	$ echo "gem 'nokogiri'" >> 'Gemfile'
	$ bundle install
	$ nano config/initializers/noko.rb

create file and add:

``` ruby

	require 'nokogiri'
	require 'open-uri'
```

#### Usage

	$ irb
	$ doc = Nokogiri::HTML(open("[URL"))    # parse HTML file
	$ doc = Nokogiri::HTML(open("[URL"))    # parse XML file

	$ doc.css('script').remove                            # removes inline Javascript
	$ doc.at("//h1[@itemprop = 'name']").text             # returns text at h1 tag matching 
															the element given in query
	$ doc.at("//span[@itemprop = 'rating']").text.to_i    # returns integer from text in element
	$ doc.at_css('#movie-image-section img')['src']       # selects text at css id

