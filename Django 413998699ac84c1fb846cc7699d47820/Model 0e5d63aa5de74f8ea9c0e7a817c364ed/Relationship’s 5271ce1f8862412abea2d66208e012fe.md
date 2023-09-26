# Relationship’s

let’s you have to models and you want to connect but how?

1. one to many relationship 

```python
class Room(models.Model):
    name = models.CharField(max_length=20)
    description  = models.TextField(null=True, blank=True)
    updated = models.DateTimeField(auto_now=True)
    created = models.DateTimeField(auto_now_add=True)

    def __str__(self) -> str:
        return self.name

class message(models.Model):
    room = models.ForeignKey(Room, on_delete=models.CASCADE)  #Should to be specified #Models.CASCADE means when parrent deleted child also deleted
   #room = models.ForeignKey(Room, on_delete=models.SET_NULL) #The data exist in the database but the value is NULL

```

```python
from django.db import models
from django.contrib.auth.models import User
# Create your models here.
    
class Topic(models.Model):
    name = models.CharField(max_length=200)
    def __str__(self) -> str:
        return self.name
    
class Room(models.Model):
    host = models.ForeignKey(User, on_delete=models.CASCADE)
    Topic = models.ForeignKey(Topic, on_delete=models.SET_NULL, null=True)
    name = models.CharField(max_length=20)
    description  = models.TextField(null=True, blank=True)
    updated = models.DateTimeField(auto_now=True)
    created = models.DateTimeField(auto_now_add=True)

    def __str__(self) -> str: 
        return self.name

class Message(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    room = models.ForeignKey(Room, on_delete=models.CASCADE)
    body = models.TextField()  
    updated = models.DateTimeField(auto_now=True)
    created = models.DateTimeField(auto_now_add=True)

    def __str__(self) -> str:
        return self.body[0:50]
```