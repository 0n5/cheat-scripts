Django Admin
============

    $ python manage.py createsuperuser

navigate to [SITE]/admin

    $ python manage.py changepassword [USER]  # reset admin password

#### Sub Class Admin Mode

``` python

from django.contrib import admin

# Register your models here.
from .models import [TABLE_A], [TABLE_B]

class NewTableAAdmin(admin.ModelAdmin):
    fields = ['[FIELD_NAME']

class NewTableBAdmin(admin.ModelAdmin):
    fields = ['[FIELD_NAME']

admin.site.register(TABLE_A, NewTableAAdmin)  # model must first before admin model
admin.site.register(TABLE_B, NewTableBAdmin)

```