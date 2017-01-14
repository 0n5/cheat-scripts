Common file & directory commands
================================

#### Directory commands

	pwd      # current working directory
	ls       # shows directory contents
	ll       # detailed list of directory contents
	ls -al   # detailed list of directory contents


#### Copying

	cp -R [DIR_1] [DIR_2] # copy the contents of one directory to another  


#### File Location

	which [PROGRAM]         # returns the full path of the program or script
	whereis [PROGRAM]       # prints out the full path, source and man page for a program or script
	whereis -b [PROGRAM]    # only shows binary path

	echo $PATH   # prints out the paths that point to executables


#### File Redirects

	cat file1 > newfile.txt   # redirects stdout to new file or overwrites existing
	cat file1 >> newfile.txt  # redirects stdout to new file or appends existing

	ls ur8ueoidajfda 2> newfile.txt   # redirects the stderr to a new file or overwrites existing  
	ls ur8ueoidajfda 2>> newfile.txt  # redirects the stderr to a new file or appends existing
	ls ur8ueoidajfda 2>> /dev/null    # redirects stderr to dev null

	cat file1.txt file2.txt > mystdoutput.txt 2> mystderror.txt 
		# redirects the stdout to one file and the stderr to another
	
	cat file1.txt file2.txt > mystdoutput.txt 2>&1
		# redirects the stdout and stderr to the same file


#### Checksums

	md5sum -t [FILE]  			    # compute md5 hash of file
	echo -n "[STRING]" | md5sum     # compute hash of string
	sha1sum [FILE]   				# compute sha1 hash of file

