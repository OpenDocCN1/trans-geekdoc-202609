```
from django.urls import path
from . import views
urlpatterns = [
    path('', views.index, name='index'),
]
```

In the above code, you are passing a message to the Django project that you've to trigger this function in the views.py file.
Don't be scared; you'll be changing that file too.
In the above code, you've imported the django.urls package and path function from there.
The path () function is new functionality in Django 2.0. If you have any previous versions, it's better to upgrade.
This code passes two arguments, first there is the URL which was searched and relayed to the URL bar from the browser. The other argument is to run the file or function, which is an index function.
Now, you'll be changing the urls.py file in the main Django project.
There is only a single item on the list and you'll need to add the new data.

```
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('admin/', admin.site.urls),
]
```

After including the apps urls.