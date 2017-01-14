IPtables
========

#### Information Gathering

	iptables-save -c > [FILE_NAME]  # dump iptables rules to file
	iptables-restore [FILE_NAME]    # restores iptables from file
	iptables -L -v                  # list all iptables rules
	iptables -F                     # flush iptables rules

#### Allow SSH port 22 inbound

	iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
	iptables -A OUTPUT -o eth0 -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT

#### Allow SSH port 22 outbound

	iptables -A OUTPUT -o eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
	iptables -A INPUT -i eth0 -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT

#### Allow HTTP and HTTPS

	iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
	iptables -A OUTPUT -o eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT

#### DoS Prevention

	iptables -A INPUT -p tcp --dport 80 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT

#### Ignore Ping and ICMP traffic

	iptables  -I  INPUT  -i  ech0  -p   icmp  -s  0/0  -d  0/0   -j  DROP

#### Block IP Address

	iptables -A INPUT -s [IP_ADDRESS] -j DROP   

#### Unblock IP Address

	iptables -D INPUT -s [IP_ADDRESS] -j DROP







