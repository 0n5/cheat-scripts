Grep
====

Name comes from the ed command g/re/p (globally search a regular expression and print),

#### Regular expression symbols

	^    # begins with
	$    # ends with
	[]   # character reference

#### Exit codes

	0: successfull
	1: no matches
	2: syntax errors

#### Usage Patterns

	grep ^hello [FILE]     # finds all lines that begin with hello in file and prints to screen
	grep -c ^hello [FILE]  # lines that begin with hello in file and prints the number to screen
	grep hello[FILE]       # lines that end with hello in file and prints them to screen

	grep [e] [FILE]        # matches every instance of the character e
	grep [hel] [FILE]      # matches every intance of all characeters h,e,l
	grep ^[h] [FILE]       # matches every instance of character h that begin each line
	grep -i ^[h] [FILE]    # matches every instance of character h that begin each line; case insensitive
	grep [a-g] [FILE]      # matches every instance of characters a-g
	grep [1-9] [FILE]      # matches every instance of numbers 1 thru 9

	grep -f [FILE1] [FILE2]  # searches one file with the contents of another
	grep -lr php /etc        # searches for all instances of php recursively in /etc

#### egrep Patterns

	egrep 'hello.*world' [FILE]    # matches anything that has hello with world in the same line
	egrep 'hello|world' [FILE]     # matches any line with hello or world
	egrep -v 'hello|world' [FILE]  # does not match any line with hello or world 
	
	egrep 'hello|world' [FILE] | grep -v [USER]   # matches any line with hello or world but not [USER]
