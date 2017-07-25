Vim cheats
==========


#### Editing

	vim file_to_edit

Once file is open in buffer:

	i      # enter insert mode to write/edit file
	esc    # leave insert mode

	yy     # executes a yank and creates a copy buffer of the line
	5yy    # copies the first 5 lines into a buffer
	10yy   # copies the first 10 lines into a buffer
	
	p      # pastes the line from buffer on a new line
	P      # pastes the line from buffer into line above cursor
	o      # adds a blank line after the cursor
	

	R      # replaces or writes over text at cursor 
	dd     # deletes one line at a time at posi	tion of cursor
	3dd    # deletes three lines at a time after cursor
	cc     # clears an entire line at cursor and enters insert mode
	cw     # clears an entire word at cursor and enters insert mode

	u      # undo last edit


#### Searching

	/test       # searches top down for the pattern 'test'
	?test       # searches bottom up for pattern 'test'
	n           # goes to the next instance below the keyword
	shift n     # goes to the next instance above the keyword
	

#### Movement

	gg        # sends cursor to top of file
	shift h   # sends cursor to top of file
	
	shift gg  # sends cursor to end of file
	shift l   # sends cursor to the end of file

#### Saving and Closing

	:=    # prints out number of lines in file

	:w    # save without quitting
	:wq   # save and quit
	:q!   # quit without saving



#### Replacement Patterns

	:%s/string_replacing/string_replacing_with  # global replace
	:1s/string_replacing/string_replacing_with  # replace instance on the 1st line only

#### Executing Commands Inside VIM

	:! mkdir test    # creates a folder 'test' in the current directory
	:! ls            # executes ls command
	:! ls /etc      
	:! nano test.py  # opens nano to create a file 'test.py' in current directory

#### Loading Files

	:e /test.txt   # loads contents of a file into current file 
	:r /test.txt   # loads contents of a file at the point of the cursor



















