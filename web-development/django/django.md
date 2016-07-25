Django
======

#### Installation

    $ pip install django

#### Create Application

    $ django-admin.py startproject [PROJECT]
    

#### Run server

on Cloud9

    $ python manage.py runserver $IP:$PORT
    
#### Using Postgres

Installation 

    $ sudo apt-get update
    $ sudo apt-get install libpq-dev python-dev
    $ sudo apt-get install postgresql postgresql-contrib
    $ sudo pip install psycopg2

Create DB

    $ sudo su postgres
    $ createdb [DATABASE]
    $ createuser [USER] -P
    $ psql
    postgres=# GRANT ALL PRIVILEGES ON DATABASE [DATABASE] TO [USER];
    postgres=# \q

Connect to Django

    $ nano [PROJECT]/settings.py

``` python

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': '[DATABASE]',
        'USER': '[USER]',
        'PASSWORD': '[PASSWORD]',
        'HOST': 'localhost',
        'PORT':  '',
    }
}

```

Migrate

    $ python manage.py migrate
    
    
#### Create Application

    $ python manage.py startapp [APP]

Register app with project

    $ nano [PROJECT]/settings.py

```python

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    '[APP]',
]

```

