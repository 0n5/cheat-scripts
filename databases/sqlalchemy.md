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
    main(url='[SQL_FLAVOR]+[DRIVER]://[USERNAME]:[PASSWORD]@localhost/[DATABASE]', debug='False', repository='../[REPOSITORY')

save and exit

```

	$ python manage.py version_control

Check version of database

	$ python manage.py db_version


Check highest version available

	$ python manage.py version



