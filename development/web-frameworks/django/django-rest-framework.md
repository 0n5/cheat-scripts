Django Rest Framework
=====================

#### Installation

    $ pip install djangorestframework
    $ pip install markdown       # Markdown support for the browsable API.
    $ pip install django-filter  # Filtering support

#### Register

    $ nano settings.py
    
``` python 

INSTALLED_APPS = (
    ...
    'rest_framework',
)

```

#### Browsable API

    $ nano urls.py

``` 

urlpatterns = [
    ...
    url(r'^api-auth/', include('rest_framework.urls', namespace='rest_framework'))
]

```

#### Configuration

    $ nano settings.py

add to the file:

``` python 

REST_FRAMEWORK = {
    # Use Django's standard `django.contrib.auth` permissions,
    # or allow read-only access for unauthenticated users.
    'DEFAULT_PERMISSION_CLASSES': [
        'rest_framework.permissions.DjangoModelPermissionsOrAnonReadOnly'
    ]
}

```


#### JSONP support

    $ pip install djangorestframework-jsonp
    $ nano settings.py
    
add to the REST_FRAMEWORK dict:

``` python 

REST_FRAMEWORK = {
    # Use Django's standard `django.contrib.auth` permissions,
    # or allow read-only access for unauthenticated users.
    'DEFAULT_PERMISSION_CLASSES': [
        'rest_framework.permissions.DjangoModelPermissionsOrAnonReadOnly'
    ],
        'DEFAULT_RENDERER_CLASSES': (
        'rest_framework_jsonp.renderers.JSONPRenderer',
        # jsonp
        'rest_framework.renderers.BrowsableAPIRenderer',
        # browsable API
    ),

}

```


#### Serializers 

    $ nano serializers.py

add to the file:

``` python 
from rest_framework import routers, serializers, viewsets, generics
from [APP].models import *

class aSerializer(serializers.ModelSerializer):
    # convert related objects so they show the string instead of id in API
    object_one = serializers.StringRelatedField(many=True)
    # for many to many field
    object_two = serializers.StringRelatedField()
    # for foreign key relationship
    
    class Meta:
        model = [MODEL]
        fields = ('id', 'object_one', 'object_two', 'object_three',)
        # last field must have trailing comma


```

#### Create ViewSet

    $ nano serializers.py

add to the file:

``` python

class aViewSet(viewsets.ModelViewSet):
    queryset = [MODEL].objects.all()
    serializer_class = aSerializer

```

Register routes for ViewSet

    $ nano urls.py

add to the file:

``` python

router.register(r'[URL_PATH]', aViewSet)

```

#### ViewSets w/ parameters 

    $ nano serializers.py
    
add to the file:

``` python

class aViewSet(viewsets.ModelViewSet):
    serializer_class = aSerializer
    def get_queryset(self):
        queryset = [MODEL].objects.all()
        get_year = self.request.query_params.get('[QUERY_PARAMETER]', None)

        if get_year is not None:
            queryset = queryset.filter([FIELD]=get_year)
        return queryset

```

Register routes for ViewSet

    $ nano urls.py

add to the file:

``` python

router.register(r'[URL_PATH]', aViewSet, '[BASE_NAME_ARGUMENT')
# base_name argument can be anything in this case

```

