# Definitions and Class

```python
from django.db import models

# Create your models here.
class Blog(models.Model):
    title = models.CharField(max_length=50)
    description = models.TextField()
    image = models.ImageField(upload_to='Blog_Poster')
    updated = models.DateTimeField(auto_now=True)
    created = models.DateTimeField(auto_now_add=True)

    def __str__(self) -> str:
        return self.title
```

- Str function→ Which return self.[some attribute]

```python
def __str__(self) -> str:
        return self.title
```

- Meta class →

```python
class Meta:
        ordering = ['updated','created'] #Oldest First

class Meta:
        ordering = ['-updated','-created'] #New's First

```