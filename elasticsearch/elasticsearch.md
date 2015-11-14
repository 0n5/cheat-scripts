Elasticsearch
=============

#### Install Java

	$ add-apt-repository ppa:webupd8team/java
	$ apt-get update		
	$ apt-get install oracle-java7-installer

#### Installation

	$ wget -qO - http://packages.elasticsearch.org/GPG-KEY-elasticsearch | sudo apt-key add - 
	$ echo 'deb http://packages.elasticsearch.org/elasticsearch/1.4/debian stable main' >> /etc/apt/sources.list
	$ apt-get update
	$ apt-get install elasticsearch


#### Configuration

	$ update-rc.d elasticsearch defaults 95 10   # starts automatically on boot


#### Usage

	$ service elasticsearch start

Make sure port 9200 is open on the firewall
Visit [IP_ADDRESS:9200] to verify that it is running


#### Enabling CORS

Cross Origin Resource Sharing

	$ nano /etc/elasticsearch/elasticsearch.yml

Add to the file: 

	http.cors.enabled : true
	http.cors.allow-origin : "*"
	http.cors.allow-methods : OPTIONS, HEAD, GET, POST, PUT, DELETE
	http.cors.allow-headers : X-Requested-With,X-Auth-Token,Content-Type, Content-Length

Save and exit. 

	$ service elasticsearch restart


#### ElasticHQ

Enable CORS if not on same server

	$ cd /usr/share/elasticsearch
	$ ./plugin install royrusso/elasticsearch-HQ
    $ service elasticsearch restart

Visit [IP_ADDRESS]:9200/_plugin/HQ


#### NewRelic ElasticSearch plugin

Requires Ruby or RVM and Bundler

	$ git clone https://github.com/secondimpression/newrelic_elasticsearch_agent.git
    $ cd newrelic_elasticsearch_agent	
	$ bundle install 	

Configuration

	$ cd newrelic_elasticsearch_agent/config
	$ nano newrelic_plugin.yml

Change these lines: 
	
	license_key: '[NEWRELIC_LICENSE]'
	name:        '[APPLICATION_NAME]'
	url:         '[URL:PORT_NUMBER]'

Save and exit.

Running the Agent

	$ cd newrelic_elasticsearch_agent
	$ ./newrelic_elasticsearch_agent

	$ ./newrelic_elasticsearch_agent.daemon start
	$ ./newrelic_elasticsearch_agent.daemon status
	$ ./newrelic_elasticsearch_agent.daemon stop
	









