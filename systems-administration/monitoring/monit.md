Monit
=====

#### Installation

	apt-get install monit

#### Enable Web Interface

	service monit stop
	nano /etc/monit/monitrc

Add to the file

	set httpd port 2812 and
	    use address [IP_ADDRESS]
	    allow [USERNAME]:[PASSWORD]
	    allow @monit
	    allow @users readonly

Save and exit. 

	service monit reload
	service monit start

Visit [IP_ADDRESS:2812] <br>
Enter Username and Password from monitrc file


#### Elasticsearch monitoring

	service monit stop
	nano /etc/monit/monitrc

Add to the file:

	check host [HOSTNAME] with address [IP_ADDRESS]
	IF FAILED URL [URL]:9200/ with timeout 15 seconds
	    then alert 

Save and exit. 

	service monit reload
	service monit start


#### Slack Integration

Visit [TEAM].slack.com/services# <br>
Select Configured Integrations<br>
Click Incoming Webhooks<br>
Click Add button<br>
Notate the Link created

	nano slack.rb

Add to the file:

``` ruby
#!/usr/bin/ruby

require 'net/https'
require 'json'

uri = URI.parse("[SLACK_HOOKS_URL")
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
request = Net::HTTP::Post.new(uri.request_uri, {'Content-Type' => 'application/json'})
request.body = {
    "channel"  => "#[CHANNEL_NAME]",
    "username" => "[USERNAME]",
    "text"     => "[#{ENV['MONIT_HOST']}] #{ENV['MONIT_SERVICE']} - #{ENV['MONIT_DESCRIPTION']}"
}.to_json
response = http.request(request)
puts response.body
```

Save and exit.

	service monit stop
	nano /etc/monit/monitrc

Add to the file:

	[CHECK_SOMETHING_LINE1]
	[CHECK_SOMETHING_LINE2]
	    then exec  /path/to/slack.rb

if using RVM instead indicate full path to ruby

	[CHECK_SOMETHING_LINE1]
	[CHECK_SOMETHING_LINE2]
		then exec "/path/to/.rvm/rubies/ruby-2.2.3/bin/ruby /path/to/slack.rb"
	
Save and exit.

	service monit reload
	service monit start

