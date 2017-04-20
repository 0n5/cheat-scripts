File Redirects
==============

#### Redirecting cat

	cat file1 > newfile.txt   # redirects stdout to new file or overwrites existing
	cat file1 >> newfile.txt  # redirects stdout to new file or appends existing


	cat file1.txt file2.txt > mystdoutput.txt 2> mystderror.txt 
		# redirects the stdout to one file and the stderr to another
	
	cat file1.txt file2.txt > mystdoutput.txt 2>&1
		# redirects the stdout and stderr to the same file


#### Redirecting ls

	ls ur8ueoidajfda 2> newfile.txt   # redirects the stderr to a new file or overwrites existing  
	ls ur8ueoidajfda 2>> newfile.txt  # redirects the stderr to a new file or appends existing
	ls ur8ueoidajfda 2>> /dev/null    # redirects stderr to dev null
