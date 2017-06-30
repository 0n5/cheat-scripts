Django w/ Postgres
==================

#### Installation 

    sudo apt-get update
    sudo apt-get install libpq-dev python-dev
    sudo apt-get install postgresql postgresql-contrib
    sudo pip install psycopg2

#### Create DB

    sudo su postgres
    createdb [DATABASE]
    createuser [USER] -P
    psql
    postgres=# GRANT ALL PRIVILEGES ON DATABASE [DATABASE] TO [USER];
    postgres=# \q

#### Connect to Django

    nano [PROJECT]/settings.py

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

#### Migrate

    python manage.py migrate