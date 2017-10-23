Network Adapters
================

#### Change mac address of wireless card

	ifconfig wlan0 down
	ifconfig wlan0 hw ether 00:00:00:00:00:00
	ifconfig wlan0 up

#### Host-only network

	cd /etc/network
	nano interfaces

Add to the file

	auto eth1
	iface eth1  inet dhcp

