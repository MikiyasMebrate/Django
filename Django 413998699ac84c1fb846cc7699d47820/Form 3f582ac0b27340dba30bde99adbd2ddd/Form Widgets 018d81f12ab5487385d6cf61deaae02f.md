# Form Widgets

Create new file called forms.py

[django-widget-tweaks · PyPI](https://pypi.org/project/django-widget-tweaks/)  —> Good for Customization in html

Import django from and import your Model class

example:

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

```python
from django import forms
from .models import Post_news

class Form_Post_news(forms.ModelForm):
    class Meta:
        model = Post_news
        fields = (
            'title',
            'description',
            'image'
        ) 
      #OR
       fields = "__all__"
        labels = {
            'title':'*Item Title',
            'description':'*Item Descriptions',
            'image':'*Item Image'
        }

        widgets = {
            'title': forms.TextInput(attrs={
            'class' : 'form-control',
            'placeholder' : 'Enter Your Title',
            }),
            'description' : forms.Textarea(attrs={
            'class' : 'form-control',
            'placeholder' : 'Enter Your Description'
            }),
            'image' :  forms.FileInput(attrs={
            'class' : 'form-control',
            'placeholder' : 'Enter Your Description'
            }),
        }
```

- To Accept files from forms

```python
def post_Blogs(request):
    form = Blog_form(request.POST or None, request.FILES or None)
    if form.is_valid():
        form.save()
        form = Blog_form()
    context = {
        'Blog_Form' : Blog_form
    }
    return render(request, 'forms.html', context)
```