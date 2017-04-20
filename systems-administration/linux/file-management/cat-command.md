cat
===

Responsible for reading, concatenating or creating files

#### Overwriting

	set -o noclobber  # prevents overwriting of files
	set +o noclobber  # turns off overwriting prevention 

#### Usage

	cat file1 file 2   # cats both files two stdout
	cat file* | wc -l  # combines all files starting with 'file' and counts the number of lines


#### Redirects

	cat file1 > newfile.txt   # redirects stdout to new file or overwrites existing
	cat file1 >> newfile.txt  # redirects stdout to new file or appends existing

	cat file1.txt file2.txt > mystdoutput.txt 2> mystderror.txt 
		# redirects the stdout to one file and the stderr to another
	
	cat file1.txt file2.txt > mystdoutput.txt 2>&1
		# redirects the stdout and stderr to the same file
