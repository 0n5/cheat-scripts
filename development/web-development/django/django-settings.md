Settings.py
===========


#### Production Configurations

``` python

DEBUG = False
# never run debug in production

ALLOWED_HOSTS = [
# prevents HTTP HOST header attacks
# with debug = true, all traffic is allowed
# can be FQDN or not

'.[YOUR_DOMAIN]'
]


INSTALLED_APPS = [
# list of applications that are enabled in the project
    'django.contrib.admin',
    'django.contrib.auth',
     ...
]

TEMPLATES = [
# determines default template path and engine
# default engine is jinja
# by default templates will load from template directory

    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

DATABASES = {
# database connection settings
# by default is set to use sqlite3
# when using any other RDBMS you must also set user, password, host and port
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': '[DBNAME]',
    }
}

STATIC_URL = '/static/'
# defines the static url folder. must use this static variable name


    ```