netstat
=======

#### Usage

	$ netstat -a | more  # all tcp and udp ports
	$ netstat -ant       # all tcp connections
	$ netstat -lt        # tcp ports listening
 
	$ netsat -tulpn      # all connections with pid
	
	$ netstat -au        # udp connections
	$ netstat -lu        # udp ports listening
	
	$ netstat -lx        # unix listening ports
	
	$ netstat -s         # stats by protocol
	$ netstat -tp        # service name with pid
	
	$ netstat -r         # kernel routing table
	$ netstat -i         # network interface transactions
	
	
	$ netstat -ap | grep http   # find programs listening on http

	$ netstat -c         # continous mode
