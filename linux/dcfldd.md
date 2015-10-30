dcfldd
======

#### Installation

	$ apt-get install dcfldd

#### Imaging

	$ dcfldd if=[FILE] hash=md5,sha256 hashwindow=1G md5log=md5.txt \
	sha256log=sha256.txt hashconv=after conv=noerror,sync of=[OUTPUT]