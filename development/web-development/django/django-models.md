Django Models
=============

#### Create Models

    nano [APP]/models.py

``` python

from __future__ import unicode_literals

from django.db import models

class [MODEL](models.Model):
    [FIELD_NAME] = models.[FIELD_TYPE](max_length=255)

    def __unicode__(self):
        return self.[FIELD_NAME]

```

#### Register Models in Admin

    nano [APP]/admin.py

``` python

from .models import [TABLE_A], [TABLE_B]
admin.site.register(TABLE_A)
admin.site.register(TABLE_B)

```

#### Migrate Changes

    python manage.py makemigrations [APP]  # creates new migrations based on Models
    python manage.py migrate               # applies migrations 
 
    python showmigrations                  # displays migration & version info
    python sqlmigrate [APP] [VERSION]      # displays SQL for migration

    python manage.py migrate [APP] zero    # rolls back to version 0, just delete old versions
    
    python manage.py flush                 # wipes data in database 

#### Model Field Types (common)

add verbose field name as a parameter to set Field Label Name<br>
ForeignKey and ManyToManyField require Model to be first arg, use verbose_name

``` python

first_name = models.CharField("person's first name", max_length=30)
ManyToManyField(Model, verbose_name="Director") 

```    

Fields are blank=False by default, pass in blank=True arg to allow empty field

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

 
#### ImageField Paths 

    nano [PROJECT]/settings.py

``` python 

ENV_PATH = os.path.abspath(os.path.dirname(__file__))
MEDIA_ROOT = os.path.join(ENV_PATH, 'media/')
MEDIA_URL = 'media/'

```

#### QuerySet

Drop into Django shell to test Models, query from cli 

    python manage.py shell
    >>> from django.db import models
    >>> from [APP].models import [MODEL]

All Objects:

    >>> [MODEL].objects.all()
    
    >>> for x in [MODEL].objects.():
            print(x.[MODEL])

Order By:

    >>> [MODEL].objects.order_by('[COLUMN')

Get:

    >>> [MODEL].objects.get(pk=1)  # returns object with primary key == 1

Filter:

    >>> [MODEL].objects.filter([COLUMN]__startswith='E')
        # returns all objects whose Column startswith character 'E'

    >>> [MODEL].objects.filter([COLUMN]__exact=[VALUE]):
        # returns only exact matches

    >>> if [MODEL].objects.filter([FIELD]=[VALUE]).count() != 0:
    >>>     do something...
        # query that checks if there are any objects after filtering 
        
Create:

Only for one-to-one and one-to-many relationships<br>
Must save objects first and then assign for many-to-many 

    >>> create_object = [MODEL].objects.create([FIELD]=[VALUE],[FIELD]=[VALUE])
    >>> [MODEL].save()


Create Many-to-many object

    >>> new_many2many_object = [MODEL]([FIELD]=[VALUE])
    >>> new_many2many_object.save()


Add Many-to-many relationship to another object

    >>> many2many_query = [MODEL].objects.get([FIELD]=[VALUE])
    >>> other_object.many2many_query.add([NEW_OBJECT])
