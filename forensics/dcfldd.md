dcfldd
======

Enhanced version of dd tool used in security and forensics. Developed by DoD.<br>
Should not be used to image faulty drives, can misalign data and enter infinite loop. 

#### Installation

	apt-get install dcfldd

#### Imaging

	dcfldd if=[INPUT_FILE] hash=md5,sha256 hashwindow=1G md5log=md5.txt \
	sha256log=sha256.txt hashconv=after conv=noerror,sync of=[OUTPUT_FILE]