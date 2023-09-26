# Form

- First create python file called [forms.py](http://forms.py) then import django libraries and the database model

```python
from django import forms
from .models import post_news
```

- Now create a class

```python
class createNewsPost(forms.ModelForm):
    class Meta:
        model = post_news
        fields = [
            'title',
            'description',
            'link',
            'featured'
        ]
```

- Go to view and import class from forms

```python
from .forms import createNewsPost
```

- Create a function that sent to the user

```python
def create_form_post(request):
    form = createNewsPost(request.POST or None)
    if form.is_valid():
        form.save()
        form = createNewsPost()
    context = {
        'form':form
    }
    return render(request, 'form.html', context)
```

- Create html file

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
    <form method="post">{% csrf_token %}
        {{form.as_p}}
        <button type="submit">Submit</button>
    </form>
</body>
</html>
```

- Add to urls

```python
from blog.views import home_view,create_form_post
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', home_view, name='Home Page'),
    path('form/',create_form_post, name='form')
]
```

---

## Topics

---

[Custom Form Design](Form%203f582ac0b27340dba30bde99adbd2ddd/Custom%20Form%20Design%20b2821d4bf0b64f01b60e4c49932b6f60.md)

[Pure Django Form](Form%203f582ac0b27340dba30bde99adbd2ddd/Pure%20Django%20Form%2093dad5e9d52f40949a203965dc978bd8.md)

---

[Form Widgets](Form%203f582ac0b27340dba30bde99adbd2ddd/Form%20Widgets%20018d81f12ab5487385d6cf61deaae02f.md)

[Form Validations](Form%203f582ac0b27340dba30bde99adbd2ddd/Form%20Validations%20b1d31f8cd66c4d1eb6b763cd50a50cbc.md)

[Text Manipulation as HTML](Form%203f582ac0b27340dba30bde99adbd2ddd/Text%20Manipulation%20as%20HTML%200435f4b9f7a6469a87c446e131abac5b.md)

[filter](Form%203f582ac0b27340dba30bde99adbd2ddd/filter%20f3c6484ae2f5431da70ff2c433e22fc2.md)