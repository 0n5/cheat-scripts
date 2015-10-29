Scalpel cheats
==============

#### Installation

	$ apt-get install scalpel

#### Configuration

	$ nano /etc/scalpel/scalpel.conf

edit config file and uncoment extension type to look for:

	# GIF and JPG files (very common)
	#      gif     y       5000000         \x47\x49\x46\x38\x37\x61        \x00\x3b
	#      gif     y       5000000         \x47\x49\x46\x38\x39\x61        \x00\x3b
	       jpg     y       200000000       \xff\xd8\xff\xe0\x00\x10        \xff\xd9
	

#### Carve out unallocated space

	$ apt-get install sleuthkit
	$ blkls -a [IMAGE] > [OUTPUT_IMAGE]


#### Carve files

	$ scalpel [IMAGE] -o [OUTPUT_DIR]
