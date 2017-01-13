Vagrant
=======


#### Troubleshooting

Vagrant could not detect VirtualBox! Make sure VirtualBox is properly installed:

	$ nano ~/.bash_profile

Add to the file:

	export PATH="/Applications/VirtualBox.app/Contents/MacOS:$PATH"

Save and exit.

	$ source ~/.bash_profile