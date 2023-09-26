# Homepage into Custom page

let’s do some simple example 

let Assume we have an application called blog and open views py code 

```python
from django.http import HttpRespose 

def home_view(requries):
    return HttpRespose("<h1>Hello World")
```

Now it go back to our main project called my_site and open urls

```python
from blog.views import home_view

#under the urlpatter add this list
path('', home_view,name='Home page')

```