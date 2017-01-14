find
====

#### Usage

	find . -name 'cron*'           # finds any file starting with cron in the pwd
	find / -name 'cron*'           # finds any file starting with cron in the / path
	find . -type f -name 'cron*'   # only search for files 
	find . -type d -name 'cron*'   # only search for directories
	find /home -perm 777           # finds all the files with permission 777 in the /home folder
	find . -mtime +1               # find all files in pwd directory that were modified in the last day
