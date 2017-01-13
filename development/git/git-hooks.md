Git Hooks
=========

#### Checkout latest tree into web server
	
	$ mkdir web_server && cd web_server
	$ git init --bare 
	$ cd .git/hooks
	$ nano post-receive 

Edit the file:

	#!/bin/sh
	GIT_WORK_TREE=/path/to/web_server git checkout -f

Save and Exit.

	$ chmod +x post-receive