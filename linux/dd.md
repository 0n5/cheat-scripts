dd
==

#### Basic Settings

	if   # read from file/image/disk
	of   # write to file/image/disk
	bs   # BYTES, read and write up to [bs] at a time

#### CONV symbols

	noerror   # continue after read errors
	notrunc   # do not truncate output file 

#### FLAG symbols

	sync -  use synchronized i/o for data and metadata

#### Basic Usage

	$ dd if=[DRIVE_PATH] of=[OUTPUT] conv=notrunc,noerror
