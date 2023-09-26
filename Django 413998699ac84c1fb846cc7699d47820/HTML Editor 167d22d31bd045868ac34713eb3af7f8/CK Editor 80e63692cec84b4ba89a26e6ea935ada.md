# CK Editor

```python
pip install django-ckeditor
```

Setting.py

```python
INSTALLED_APPS = [
    .
    .

    .
    'ckeditor',
]
```

- Model.py

```python
from django.db import models
from ckeditor.fields import RichTextField 

class BlogPost(models.Model):
    blog_title = models.CharField(max_length=200)
    blog_content = RichTextField()
    publish_date = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.blog_title
```