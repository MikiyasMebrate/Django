# Model

first create a database model application

Example:

```python
from django.db import models

# Create your models here.
class product(models.Model):
    title  = models.TextField()  
    description = models.TextField()
    price = models.FloatField()
```

write command in the terminal

```python
python manage.py makemigrations
python manage.py migrate
```

To add your database into Admin Page

```python
from .models import class_name
admin.site.register(class_name)
```

### Adding and Accessing element using Python Shell

Active python shell

```python
python manage.py shell
```

Accessing the database

```python
from app_name.models from class_name
class_name.objects.all()  #get how many elements are founded
```

Adding Elements

```python
class_name.objects.create(attributes)
#Example
post_news.objects.create(title='News Title', description = 'some description', link = 'www.google.com')
```

More Modifying Database

 

```python
class Product(models.Model):
      title = models.CharField(max_length=120)  #When we use CharField should have max_length
      description = models.TextFiled(black=True, null=True) 
```

- Options in Models

```python
gender = [('Male', 'Male'),('Female','Female')]  #Actual Value and Human Readable name
country = [('ET', 'Ethiopia'), ('US','United State of America')] #Actual Value -> ET and Human Readable -> Ethiopia

MEDIA_CHOICES = [
    (
        "Audio",
        (
            ("vinyl", "Vinyl"),
            ("cd", "CD"),
        ),
    ),
    (
        "Video",
        (
            ("vhs", "VHS Tape"),
            ("dvd", "DVD"),
        ),
    ),
    ("unknown", "Unknown"),

#--> Audio
       # Vinyl
       # CD
#--> Video
       # VHS Tape
       # DVD
#--->unkown
       #unknown

model_gender = models.CharField(blank=False, max_length=7,  null=False,choices=gender)
Media = models,CharField(max_length=10, choice=MEDIA_CHOICES)

```

- Model Attributes

```python
updated = models.DateTimeField(auto_now=True)  #auto_now -> Changes evertime updated 
created  = models.DateTimeField(auto_now_add=True) #auto_now_add -> When created time stamp
```

[Relationship’s ](Model%200e5d63aa5de74f8ea9c0e7a817c364ed/Relationship%E2%80%99s%205271ce1f8862412abea2d66208e012fe.md)

[Definitions and Class](Model%200e5d63aa5de74f8ea9c0e7a817c364ed/Definitions%20and%20Class%2079e0667aacd2424aba297f53ac79eea7.md)