SQLAlchemy
==========

#### Installation

	$ pip install sqlalchemy

#### Migrations

	$ pip install sqlalchemy-migrate

Create change repository

	$ migrate create [REPOSITORY] "[PROJECT]"

Put database under version control

	$ cd [REPOSITORY]
	$ nano manage.py

add to the file:

``` python

#!/usr/bin/env python
from migrate.versioning.shell import main

if __name__ == '__main__':
    main(url='[SQL_FLAVOR]+[DRIVER]://[USERNAME]:[PASSWORD]@localhost/[DATABASE]', \
    debug='False', repository='../[REPOSITORY')

save and exit

```

	$ python manage.py version_control

Check version of database

	$ python manage.py db_version


Check highest version available

	$ python manage.py version



#### Create Table migration

	$ python manage.py script "create table"   # output will be /versions/001_create_table.py
	$ nano versions/001_create_table.py

add to the file:

``` python

from sqlalchemy import Boolean, Table, MetaData, Column, VARCHAR, INTEGER
from migrate import *

def upgrade(migrate_engine):
	meta = MetaData(bind=migrate_engine)
	[TABLENAME] = Table('[TABLENAME]', meta,
	    Column('id', INTEGER, primary_key=True, autoincrement=True)
	)
	meta.create_all()

```

