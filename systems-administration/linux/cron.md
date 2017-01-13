Cron
====

#### Cron file locations

	/etc/crontab      # editable only by root
	/var/spool/cron   # location of user cron
	/var/log/syslog   # location of cron logs in ubuntu

#### Edit Crontab

	crontab -e   # opens dialog to select cron editor

#### Crontab configuration

	*/1    *    *     *    *    # runs every minute, hour, day and month 
	*/1    2,6  *     *    *    # runs every minute on hours 2 and 6 every day every month
	*/1    2-6  *     *    *    # runs every minute between hrs 2 & 6 every day every month
	*/1    *    1     *    *    # runs every minute, every where on first day of every month
	*/1    *    *     *    5    # runs every minute, every hour, every day, every month on Friday
	*/1    /3   *     *    *    # runs every minute on every 3rd day

	*/1    *    *     *    5 echo 'test' >> test.txt 
	   # every minute, hour, day, month on friday cron will append test to the file