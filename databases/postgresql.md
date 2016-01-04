Postgresql
==========

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

#### Grant permissions

	$ psql
	# \c [DATABASE]
	# grant all privileges on all tables in schema public to [USER];


#### Import SQL dump file

	Remove PRAGMA foreign_keys=OFF; line
	Modify columns to match Postgres data types

	$ psql -d [POSTGRES_DATABASE] -W < [DUMP_FILE]


#### Issues

ImportError: dlopen(/Users/[USER]/anaconda/lib/python2.7/site-packages/psycopg2/_psycopg.so.... 

	$ export DYLD_FALLBACK_LIBRARY_PATH=$HOME/anaconda/lib/:$DYLD_FALLBACK_LIBRARY_PATH

