Django Installation
===================


#### Global

dependencies

    sudo apt-get update
    sudo apt-get install python-pip python-dev build-essential 
    sudo pip install --upgrade pip 
    sudo apt-get install libpq-dev python-dev

Installation

    sudo pip install django

#### Create Project

    django-admin.py startproject [PROJECT]
    cd [PROJECT]
    python manage.py migrate    
    python manage.py createsuperuser


#### Run server

on Cloud9

    nano [DJANGO_PROJECT]/settings.py

add the following:

```python 

ALLOWED_HOSTS = [u'CLOUD9_HOST']

```

    python manage.py runserver $IP:$PORT

