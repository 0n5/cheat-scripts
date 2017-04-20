chmod (change mode)
===================

#### Permissions

To view permissions of a directory execute ls -al or ll

	d     # directory
	-     # file
	r     # read
	w     # write
	x     # execute

 
	1st character          # its a file or directory 	
	2nd, 3rd, 4th lines    # owner permissions
	5th, 6th, 7th lines    # group permissions
	8th, 9th, 10th lines   # world permissions

	7  # read, write, execute
	6  # read, write
	5  # read, execute
	4  # read
	3  # write, execute
	2  # write
	1  # execute
	0  # no permission

#### Usage

	chmod o+r [FILE]    # gives world permission to read
	chmod o-r [FILE]    # removes permission to read

	chmod 755 [FILE]    # rwx to owner, rx to group and world
	chmod -R 755 [DIR]  # changes permissions recursively to directory

	chmod +x [FILE]     # makes file executable
