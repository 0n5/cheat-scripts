cat
===

Responsible for reading, concatenating or creating files

#### Overwriting

	set -o noclobber  # prevents overwriting of files
	set +o noclobber  # turns off overwriting prevention 

#### Usage

	cat file1 file 2   # cats both files two stdout
	cat file* | wc -l  # combines all files starting with 'file' and counts the number of lines

