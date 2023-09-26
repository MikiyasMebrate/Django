# Image Manipulation

Create Models

Example:

```python
from django.db import models

# Create your models here.
class Blogs(models.Model):
    title = models.CharField(max_length=100)
    description = models.TextField()
    image = models.ImageField(upload_to='')

    def __str__(self) -> str:
        return self.title
```

To manipulate Image first we have to install Pillow 

```python
pip install pillow
```

```python
    image = models.ImageField(upload_to='') #Telling where Django store the image --> by Default it saves into media file
```

It not enough to manipulate image we have tell django where the image is located 

in the Project setting

```python
import os
MEDIA_URL="media/"
MEDIA_ROOT=os.path.join(BASE_DIR,"media/")
```

Also we should add in the project urls

```python
from django.contrib import admin
from django.urls import path
from blog.views import view_home_page, create_blog
from django.conf import settings
from django.conf.urls.static import static
urlpatterns = [
    path('admin/', admin.site.urls),
    path('',view_home_page, name='Homepage'),
    path('create_form/', create_blog, name ='blog')
]
urlpatterns += static(settings.MEDIA_URL,document_root=settings.MEDIA_ROOT)
```

Uploading Images

```python
def add_form(request):
    form = Form_Post_news(request.POST or None, request.FILES or None)
    if form.is_valid():
        form.save()
        form = Form_Post_news()
    context = {
        'form' : form
    }

    return render(request, 'form.html',context)
```