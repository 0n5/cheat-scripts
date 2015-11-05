Nmap
====

#### Installation

	apt-get install nmap

#### Scanning

	$ nmap -v -n [IP_ADDRESS]      # basic scan
	$ nmap -F [IP_ADDRESS]         # fast scan
	$ nmap -sS [IP_ADDRESS]        # stealth scan
	$ nmap -T4 -A -v [IP_ADDRESS]  # intense scan
	
	$ nmap --open [IP_ADDRESS]     # only show open ports
	$ nmap -sV -n [IP_ADDRESS]     # os fingerprint
	$ nmap -sP [IP_ADDRESS]/24     # ping scan for all devices and servers that are up
	$ nmap -PO [IP_ADDRESS]        # protocol ping scan 
	$ nmap -PU [IP_ADDRESS]        # UDP ping scan
	$ nmap -sT [IP_ADDRESS]        # syn scan for most commonly used ports
	$ nmap -p 80-200 [IP_ADDRESS]  # only scan ports 80 thru 200

	$ nmap -sA [IP_ADDRESS]   # determine if host is behind firewall
	$ nmap -PN [IP_ADDRESS]   # do not ping, scan host if behind firewall
	$ nmap -sN [IP_ADDRESS]   # null scan to check firewall
	$ nmap -sF [IP_ADDRESS]   # TCP fin scan to check firewall
	$ nmap -sX [IP_ADDRESS]   # xmas scan; sets all flags to probe firewall

	$ nmap --spoof-mac 01:23:45:67:89:ab [IP_ADDRESS]   # spoof mac and scan firewall

