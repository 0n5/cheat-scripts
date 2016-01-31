Postgresql
==========

#### Installation

Ubuntu

	$ apt-get install postgresql postgresql-contrib


#### Usage

	$ su postgres
	$ psql

#### psql commands

	\i [FILE.sql]    # initialize database with sql file
	\c [DATABASE]    # connect to database
	\dt              # show tables
	\q               # quit postgres client               

#### Create Database

	$ psql 
	# create user [USER] with password '[PASSWORD]';
	# create database [DATABASE] owner [USER] encoding 'utf-8';
	# \c [DATABASE]

#### Delete Database

	$ psql
	# DROP DATABASE [DATABASE]

#### Grant permissions

	$ psql
	# \c [DATABASE]
	# grant all privileges on all tables in schema public to [USER];
	# grant usage on all sequences in schema public to [USER];


#### Create backup

SQL

	$ pg_dump [DATABASE_FILE] > [OUTPUTFILE].sql

CSV

	$ su postgres
	$ psql
	# \c [DATABASE]
	# \copy (SELECT * FROM movie) TO '/tmp/[FILE_NAME].csv' DELIMITER ',' CSV HEADER

#### Import SQL dump file

	Remove PRAGMA foreign_keys=OFF; line
	Modify columns to match Postgres data types

	$ psql -d [POSTGRES_DATABASE] -W < [DUMP_FILE]


#### Issues

ImportError: dlopen(/Users/[USER]/anaconda/lib/python2.7/site-packages/psycopg2/_psycopg.so.... 

	$ export DYLD_FALLBACK_LIBRARY_PATH=$HOME/anaconda/lib/:$DYLD_FALLBACK_LIBRARY_PATH


Error: pg_config executable not found.
	
	$ nano ~/.bash_profile

add: 

	PATH="/Applications/Postgres.app/Contents/Versions/9.x/bin:$PATH"

save and close

	$ source ~/.bash_profile


When installing psycopg2 on Ubuntu: Command "python setup.py egg_info" failed with error code 1.... 

	$ sudo apt-get install libpq-dev python-dev


duplicate key value violates unique constraint "[TABLE_NAME]_pkey"

	# psql
	# \c [DATABASE]
	# select setval(pg_get_serial_sequence('[TABLE_NAME]', 'id'), MAX(id)) from [TABLE_NAME];

