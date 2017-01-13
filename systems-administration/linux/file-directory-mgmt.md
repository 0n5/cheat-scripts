Linux Files & Directories
=========================

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

#### Cat

	set -o noclobber  # prevents overwriting of files
	set +o noclobber  # turns off overwriting prevention 

	cat file1 file 2   # cats both files two stdout
	cat file* | wc -l  # combines all files starting with 'file' and counts the number of lines

#### Cut

	cut -f1 -d : /etc/passwd > output.txt   
		# cut field 1, use : as a delimiter and create or overwrite output.txt

	cut -f1 -d : /etc/passwd >> output.txt   
		# cut field 1, use : as a delimiter and create or append output.txt

#### Split

	split -l 1 file1.txt    # splits each line into a seperate file (starting with xaa)
	split -l 2 file1.txt    # splits every two lines into a seperate file (starting with xaa)
	split -b 256 file1.txt  # splits every 256 byte chunks into seperate files


#### Diff

	diff file1 file2   # compares the lines of two files

#### Find

	find . -name 'cron*'           # finds any file starting with cron in the pwd
	find / -name 'cron*'           # finds any file starting with cron in the / path
	find . -type f -name 'cron*'   # only search for files 
	find . -type d -name 'cron*'   # only search for directories
	find /home -perm 777           # finds all the files with permission 777 in the /home folder
	find . -mtime +1               # find all files in pwd directory that were modified in the last day

#### Locate

	locate [NAME]  			   # will locate all files/programs with [NAME] indexed in its database 
	updatedb                   # updates the locate database
	locate kernel | grep usr   # locates all kernel files in the usr directory


#### Checksums

	md5sum -t [FILE]  			    # compute md5 hash of file
	echo -n "[STRING]" | md5sum     # compute hash of string
	sha1sum [FILE]   				# compute sha1 hash of file

