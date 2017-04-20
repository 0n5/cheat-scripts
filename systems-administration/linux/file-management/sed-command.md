sed (stream editor)
===================

Filters and transforms text

#### Regular Expressions

	[]   # character class
	^    # used inside of character class means that it does not include 
	*    # means anything can match except whats in the character class

#### Usage

	sed 's/[OLD]/[NEW]/'  [FILE]             # replaces first instance of oldstring with newstring
	sed 's/[OLD]/[NEW]/g' [FILE]             # replaces all instances of oldstring with newstring
	sed 's/[OLD]/[NEW]/w [NEW_FILE]' [FILE]  # writes the modified stream to a new file
