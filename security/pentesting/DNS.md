DNS
===

Zone transfer: Zone file replicated from a primary DNS server to a secondary


#### Record Types

	SRV   # Service, host and port number of services 
	SOA   # Start of Authority, primary name server
	PTR   # Pointer, maps IP address to host name, Reverse DNS lookups
	NS    # Name Server, name servers in the namespace
	MX    # Mail Exchnage, email servers in domain
	CNAME # Canonical Name, domain name aliases in zone
	A     # Address, maps IP address to host name, DNS lookups


#### SOA Record

	Source Host    # host name of the SOA server
	Contact Email  # contact email for zone file maintainer
	Serial Number  # revision number of zone file
	Refresh Time   # time secondary DNS server waits before asking for updates
	Retry Time     # time a secondary server will to retry if zone transfer fails
	Expire Time    # max time a secondary server will spend to compete a zone transfer
	TTL            # time to live for all records in the zone










