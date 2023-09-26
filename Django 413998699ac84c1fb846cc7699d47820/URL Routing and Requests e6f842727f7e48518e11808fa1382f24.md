# URL Routing and Requests

to make different url routhing first you should have functions under application view  

example:

 

```python
def view_home(request):
     return HttpResponse("<h1>Homepage</h1>")

def about(request):
    return HttpResponse("<h1>About Page</h1>")

def contact(request):
    return HttpResponse("<h1>Contact Page</h1>")
```

- As we can see we have some function now when broweser request like /about return “About Page” and requests /contact return “Contact Page”
- To make this go head to your main project file open [urls.py](http://urls.py) include the library of the application

Example:

```python
from product.views import view_home,about,contact
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', home_view, name='Home Page')
    path('about/',about, name='About Page')
    path('contact', contact, name='Contact Page') 
] #Done check your browser
```