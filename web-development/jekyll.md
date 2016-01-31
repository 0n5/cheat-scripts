Jekyll
======


### OSX

#### Installation

Install XCode Command Line Tools, Homebrew & RVM first

	$ rvm use 2.x.x
	$ gem install jekyll

#### Running Server

In the root jekyll application directory

	$ jekyll serve

visit site at localhost:4000


#### YAML file

	$ nano _config.yml

Edit and set any of the following variables: 

	
	layout 		# will use files from the _layouts directory
	permalink   # renders url with permalink instead
	published   # set to fale to hide a post
	tags		# tags that post belongs too
	categories  # category that a post belongs to, in lieu of folders
	markdown    # specify the markdown parser

#### Redcarpet

	$ nano _config.yml

Add the following: 

	markdown: redcarpet
	redcarpet:
	    extensions: ["no_intra_emphasis", "fenced_code_blocks", "autolink", "tables", "with_toc_data"]
	    # must be indented four spaces

#### Directory Structure

	_config.yml # configuration variables go here
	_includes   # put the headers and footers here
	_layouts    # wraps posts, specfied in the front matter
	_drafts     # where the unpublished posts go
	_posts      # posts, must be named: YEAR-MONTH-DAY-title.md
	_data       # YAML files autoloaded here
	_site       # generated site, should not be tracked version control
	/css        # where css files should go
	/images     # where images should go
	/js			# where to put javascript files
	.gitignore


#### Site Variables
	
	site.time   # current time
	site.posts  # reverse chronological list of posts
	site.pages  # list of all pages


#### Page Variables
	
	page.url         # url of post without domain
	page.date        # date assigned to post
	page.categories  # categories the post belongs to
	page.tags        # tags assigned to post


#### File Includes

add the following to a file:

	{% include file.html %}  


#### Bootstrap integration

	$ git clone https://github.com/twbs/bootstrap.git
	$ cd bootstrap/dist/css
	$ mv bootstrap-theme.css bootstrap-theme.min.css bootstrap.css bootstrap.min.css /css
	$ cd bootstrap/dist/js
	$ mv bootstrap.js bootstrap.min.js /js

	$ nano _includes/header.html

add to the head:

	&lt;link rel="stylesheet" href="{{ site.url }}/css/bootstrap.css&gt;

save and exit

	$ nano _includes/footer.html 
	
add to the file: 

	&lt;script src="{{ site.url }}/js/bootstrap.js"&gt;&lt;/script&gt;
	&lt;script src="http://code.jquery.com/jquery-1.xx.x.min.js"&gt;&lt;/script&gt;

save and exit

#### Font Awesome

	$ git clone https://github.com/FortAwesome/Font-Awesome.git    
		# Font Awesome
	$ git clone https://github.com/aristath/elusive-iconfont.git
		# elusive
	$ git clone https://github.com/Keyamoon/IcoMoon--limited-.git 
		# icomoon

Move folders to the /css folder

	$ nano _includes/header.html

add to the head:

	&lt;link href="//netdna.bootstrapcdn.com/font-awesome/4.x.x/css/font-awesome.css" rel="stylesheet"&gt;

save and exit

#### Troubleshooting

If localhost:4000 socket stays open:

	$ sudo lsof -wni tcp:4000

mark down what pid is using the socket

	$ sudo kill -9 [PID]
