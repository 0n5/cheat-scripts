Django Models
=============

#### Create Models

    $ nano [APP]/models.py

``` python

from __future__ import unicode_literals

from django.db import models

class [TABLE](models.Model):
    [FIELD_NAME] = models.[FIELD_TYPE](max_length=255)

    def __unicode__(self):
        return self.[FIELD_NAME]

```

#### Register Models in Admin

    $ nano [APP]/admin.py

``` python

from .models import [TABLE_A], [TABLE_B]
admin.site.register(TABLE_A)
admin.site.register(TABLE_B)

```

#### Migrate Changes

    $ python manage.py makemigrations [APP]  # creates new migrations based on Models
    $ python manage.py migrate               # applies migrations 
 
    $ python showmigrations                  # displays migration & version info
    $ python sqlmigrate [APP] [VERSION]      # displays SQL for migration
