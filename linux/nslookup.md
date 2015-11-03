nslookup
========

#### Usage

	$ nslookup [DOMAIN]      # find A record or ip address
	$ nslookup [IP_ADDRESS]   # reverse domain lookup

	$ nslookup -query=any [DOMAIN]   # queries all DNS records
	$ nslookup -query=mx [DOMAIN]    # queries mail exchange record
	$ nslookup -query=ns [DOMAIN]    # queries name server record
	$ nslookup -type=soa [DOMAIN]    # queries start of authority record

	$ nslookup -debug [DOMAIN]       # debug mode

	$ nslookup -port 54 [DOMAIN]     # executing nslookup on non standard dns port

