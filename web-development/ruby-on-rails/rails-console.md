Rails Console
=============

#### Usage

	$ rails console						   # runs in default dev env
	$ RAILS_ENV=production rails console   # runs in production env

	$ [MODEL].delete_all   # deletes all models in db
	

#### Running scripts

if Script is some_test.rb

	$ rails console
	irb(main) s = SomeTest.new

Run function in script

	irb(main) s.