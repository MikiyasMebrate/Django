# App’s URL

```python
from django.urls import path
from .import views

urlpatterns = [
    path('',views.homepage, name='Home')
]
```

Configure project urls

 

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('base.urls'))
]
```