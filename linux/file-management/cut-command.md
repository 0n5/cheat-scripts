cut
===

	cut -f1 -d : /etc/passwd > output.txt   
		# cut field 1, use : as a delimiter and create or overwrite output.txt

	cut -f1 -d : /etc/passwd >> output.txt   
		# cut field 1, use : as a delimiter and create or append output.txt
