NTP (network time protocol)
===========================

#### Installation

	apt-get install ntp

#### Configuration

	nano /etc/ntp.conf

Change server pool to:

```
	server 0.us.pool.ntp.org
	server 1.us.pool.ntp.org
	server 2.us.pool.ntp.org
	server 3.us.pool.ntp.org

```

	service ntp restart
