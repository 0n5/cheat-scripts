Networking
==========

#### Connections

	$ lsof -i    # lists established connections

#### Network Adapters

Change mac address of wireless card

	$ ifconfig wlan0 down
	$ ifconfig wlan0 hw ether 00:00:00:00:00:00
	$ ifconfig wlan0 up

Configure adapters for Host-only network

	$ cd /etc/network
	$ nano interfaces

Add to the file

	auto eth1
	iface eth1  inet dhcp

Save and exit. 


#### Configuration

DNS Server

	$ echo "nameserver 8.8.8.8" > /etc/resolv.conf        # add DNS server

ICMP traffic

	$ echo  1  > /proc/sys/net/ipv4/icmp_echo_ignore_all  # ignore ICMP traffic
