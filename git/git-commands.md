Git command cheats
================================

#### Install

	$ apt-get install git


#### Configuration

	$ git config --global user.name your_username
	$ git config --global user.email your_email address
	$ git config --global credential.helper "cache --timeout=3600"

#### View username and email

	$ git config user.name
	$ git config user.email

#### HTTPS Remote Origin

	$ git remote add origin https://github.com/user/repo.git      # add remote origin
	$ git remote set-url origin https://github.com/user/repo.git  # reset remote origin
	$ git remote -v                                               # view remote origins


#### Cloning repositories (HTTPS)

	$ git clone https://github.com/username/repo.git

#### Cloning repositories (SSH)

	$ git clone git@github.com:username/repo.git

#### Clone raw GitHub content 

	$ curl -o https://raw.githubusercontent.com/username/path_to_file /output_path

#### Push

	$ git add --all           # adds everything in current path
	$ git add .               # adds everything in current path
	$ git add [file]          # adds only the specific file 
	$ git commit -m "first"
	$ git push
 
#### Pull changes 

	$ git pull origin master

#### Resync .gitignore

	$ git rm -r --cached
	$ git add --all # or git add .
	$ git commit -m "resync"
	$ git push

