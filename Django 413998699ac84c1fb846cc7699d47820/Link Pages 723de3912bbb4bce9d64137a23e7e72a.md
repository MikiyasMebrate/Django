# Link Pages

- In URL’s give first give a name for each url’s

```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('',view_homepages, name='Homepage'),
    path('post/', post_Blogs, name='Post_Blog') #Example for post page name is 'Post_Blog' 
]
```

- Then go to your templates add this code in herf code

```python
<li><a href="{% url 'Post_Blog' %}">Post</a></li> 
```