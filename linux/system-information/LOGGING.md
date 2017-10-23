Logging
=======

	tail -n 20 /var/log/cron   # prints out the last 20 lines of the cron file

	tail -f /var/log/cron      # monitors log file in real time

	cat fail2ban.log auth.log > [OUTPUT]  # combines the two log files into a custom log file

	tail -f [OUTPUT]                      # monitors the new log in real time

	cat [OUTPUT] | grep fail  
		# cats the new log and pipes the stdout to grep and seachess for 'fail'

	cat [OUTPUT] | grep BREAK-IN   
		# searches the stdout for 'BREAK-IN'

	cat [OUTPUT] | grep fail | grep authentication  
		# cats the log file and pipes one grep stdout to another

	cat /etc/*syslog*.conf | grep -v “^#”   # prints list of log files
