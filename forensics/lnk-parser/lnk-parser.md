lnk-parser
==========

#### Installation

Requires Perl

	$ wget https://revealertoolkit.googlecode.com/svn-history/r107/trunk/tools/lnk-parse-1.0.pl
	$ perl -pi -e 's/\r\n/\n/g' lnk-parse-1.0.pl  # convert to unix line endings
	$ chmod +x lnk-parse-1.0.pl 

#### Usage

	$ perl lnk-parser.pl [LNK_FILE]   # run on single file
	$ perl lnk-parser.pl C:\Users\[USER]\Desktop


