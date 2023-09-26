# Render Data From Database

- Keep it as simple
- first import the model that you were created and assign the object into dictionaries.

```python
from django.shortcuts import render
from .models import post_news
# Create your views here.
def home_view(request):
    my_dict = {
        'my_dict': post_news.objects.all() 
    }
    return render(request, 'index.html', my_dict)
```

- When you render in you use like referring an object

```python
{%extends 'navbar.html'%}
{%block content%}
    <h1>Home page</h1>
    <p>From Templets</p>
    <p>{{request.user}}</p>
    {% for news in my_dict %}
       <p>Title:{{news.title}}</p>
        <p>Description: {{news.description}}</p>
    {% endfor %}
{%endblock%}
```