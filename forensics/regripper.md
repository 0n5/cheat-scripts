Regripper
=========

#### Installation

	perl -MCPAN -e 'install Parse::Win32Registry'
	mkdir -p /opt/regripper
	cd /opt/regripper
	wget https://regripper.googlecode.com/files/rrv2.5.zip
	unzip rrv2.5.zip
	cat rip.pl | sed 's|\r$||g' > /tmp/riplin0.pl
	cat /tmp/riplin0.pl | sed "s| c:\\\\perl\\\\bin\\\\perl.exe|`which perl`|" > /tmp/riplin1.pl
	cat /tmp/riplin1.pl | sed 's|plugins\\\\|plugins/|' > riplin.pl
    chmod +x riplin.pl

#### Download Plugins
	
	cd /opt/regripper
	wget https://regripper.googlecode.com/files/plugins20130429.zip -O plugins.zip
	unzip  plugins.zip -d /plugins	# path must be /plugins/pluginname

#### Usage

	perl rip.pl -l # lists all plugins installed
	
	perl rip.pl -r [HIVE_FILE] -p [PLUGIN_NAME]




