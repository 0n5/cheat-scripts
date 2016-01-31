Git command cheats
================================

#### Install

	$ apt-get install git


#### Removal

	$ rm -r .git 

#### Configuration

	$ git config --global user.name your_username
	$ git config --global user.email your_email address
	$ git config --global credential.helper "cache --timeout=3600"
	
	$ git config core.fileMode false    # git will not track chmod 

#### View username and email

	$ git config user.name
	$ git config user.email

#### HTTPS Remote Origin

	$ git remote add origin https://github.com/user/repo.git      # add remote origin
	$ git remote rm origin                                        # remove remote origin
	$ git remote set-url origin https://github.com/user/repo.git  # reset remote origin
	$ git remote -v                                               # view remote origins

#### SSH Remote Origin

	$ git remote add production ssh://[USER]@[HOST]/PATH/TO/TARGET/DIRECTORY/
	or (if using non standard SSH port):
	$ git remote add production ssh://[USER]@[HOST]:[SSH_PORT]/PATH/TO/TARGET/DIRECTORY/


#### Cloning repositories (HTTPS)

	$ git clone https://github.com/username/repo.git

#### Cloning repositories (SSH)

	$ git clone git@github.com:username/repo.git

#### Clone raw GitHub content 

	$ curl -o https://raw.githubusercontent.com/username/path_to_file /output_path

#### Push

Push to existing repository

	$ git add --all           # adds everything in current path
	$ git add .               # adds everything in current path
	$ git add [file]          # adds only the specific file 
	$ git commit -m "first"
	$ git push
 
 Push to new empty repository

 	$ git init
 	$ git remote add origin https://github.com/[USERNAME]/[REPO].git
 	$ git add .
 	$ git commit "say something"
 	$ git push --set-upstream origin master

#### Pull changes 

	$ git pull origin master

Pull changes and remove local files

	$ git fetch --all
	$ git reset --hard origin/master


#### Git Ignore

Global

	$ git config --global core.excludesfile ~/.gitignore_global
	$ nano ~/.gitignore_global

Resync .gitignore

	$ git rm -r --cached
	$ git add --all # or git add .
	$ git commit -m "resync"
	$ git push

Untrack files already commited

	$ echo [FILE] >> ~/.gitignore
	$ git rm -r --cached [FILE]
	$ git add -u
	$ git commit -m "remove cached git files"
	$ git pull
	$ git push

Untrack Renamed file/folder already commited

	$ git rm -r --cached [FILE]  # file will be deleted on next commit/push







