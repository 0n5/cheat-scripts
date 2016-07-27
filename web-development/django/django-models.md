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


#### Model Field Types (common)

* BooleanField()
* CharField(max_length=None)
* DateField()
* DateTimeField()
* DecimalField(max_digits=None, decimal_places=None)
* EmailField()  # max_length=254
* FileField()  # file upload field
* FloatField()
* ImageField()
* IntegerField()  # -2147483648 to 2147483647
* SlugField()   # max_length=50
* SmallIntegerField()   # -32768 to 32767
* TextField()
* URLField()  # max_length=200
* ForeignKey(Model) # many to one relationship
* ManyToManyField(Model)  # many to many relationship
* OneToOneField(Model)   # one to one relationship