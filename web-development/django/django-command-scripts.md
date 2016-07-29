Django Command Scripts
======================

#### Folder Structure 

Create file structure like so with commands and management directories<br>
_private.py will not be able to run using manage.py

``` python

[APP]/
    __init__.py
    models.py
    management/
        __init__.py
        commands/
            __init__.py
            _private.py 
            [COMMAND_SCRIPT_NAME].py
    tests.py
    views.py
    
```

#### Create Command Script

    $ nano [APP]/management/commands/[COMMAND_SCRIPT_NAME].py
    
``` python

from django.core.management import BaseCommand

# The class must be named Command, and subclass BaseCommand
class Command(BaseCommand):
    help = "Describe the purpose"

    def _some_function(self):
        # some logic

    def handle(self, *args, **options):
        self._create_movie()

```


#### Calling script

    $ python manage.py [COMMAND_SCRIPT_NAME].py