# Dynamic URL’s

Example:

Model:

```python
from django.db import models

# Create your models here.
class Room(models.Model):
    name = models.CharField(max_length=20)
    description  = models.TextField(null=True, blank=True)
    updated = models.DateTimeField(auto_now=True)
    created = models.DateTimeField(auto_now_add=True)

    def __str__(self) -> str:
        return self.name
```

Views

```python
from django.shortcuts import render, HttpResponse
from .models import Room
# Create your views here.
def homepage(request):
    context = {
        'data' : Room.objects.all()
    }
    return render(request, 'index.html', context)

def description(request, pk):
    req_data = Room.objects.get(id = pk)
    context = {
        'data' : req_data
    }
    return render(request, 'description.html',context)
```

url

```python
from django.urls import path
from .views import homepage, description

urlpatterns = [
    path('', homepage, name='Home_page'),
    path('des/<str:pk>/', description, name='des')
]
```

html →title.html

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body> 
    <h2>{{data.name}}</h2>
    <h2>{{data.description}}</h2>
    <h2>{{data.created}}</h2>
    <h2>{{data.updated}}</h2>
</body>
</html>
```

html →index.html

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    {% for i in data %}
      <p><a href="{% url 'des' i.id %}">{{i.name}}</a></p>
    {% endfor %}
</body>
</html>
```