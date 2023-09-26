# Form Validations

- Model.py

```python
from django import forms
from .models import Blog_Attribute

class ContactForm(forms.ModelForm):
    title = forms.CharField(max_length=100, error_messages={'required': 'Title can not be empty'})
    description = forms.CharField(widget=forms.TextInput())
    image = forms.ImageField()

    class Meta:
        model = Blog_Attribute
        fields = "__all__"

    def clean_title(self):
        title = self.cleaned_data['title']
        if not title:
            raise forms.ValidationError('Title can not be empty')
        return title
    
    def clean_description(self):
        description = self.cleaned_data['description']
        if not description:
            raise forms.ValidationError('Description can not be empty')
        return description
    
    def clean_image(self):
        image = self.cleaned_data['image']
        print(image)
        if not image:
            raise forms.ValidationError('Please add Image')
        return image
```

- Views

```python
from django.shortcuts import render
from .models import Blog_Attribute
from .forms import ContactForm

def homepage(request):
    context = {
        'blogs' : Blog_Attribute.objects.all()
    }

    return render(request, 'index.html', context)

def contact(request):
    if request.method == 'POST':
        form = ContactForm(request.POST or None, request.FILES or None)
        if form.is_valid():
            form.save()
            form = ContactForm()
    else:
        form = ContactForm()

    return render(request, 'create_blog.html', {'form': form})
```

- Html

```python
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC"
      crossorigin="anonymous"
    />
  </head>
  <body>
    <div class="container d-inline align-items-center">
      <div class="row d-flex justify-content-center">
        <div class="col-md-6 border shadow">
          <form method="post" enctype="multipart/form-data">
            {% csrf_token %}
            <div class="mt-3">
              <label for="id_title">Title</label>
              <input
                type="text"
                id="id_title"
                class="form-control"
                name="title"
              />

              {% for err in form.title.errors %}
              <small class="text-danger">{{err}}</small>
              {% endfor %}
            </div>
            <div class="mt-3">
              <label for="id_description">Description</label>
              <textarea
                type="text"
                id="id_description"
                class="form-control"
                name="description"
                rows="10"
              ></textarea>

              {% for err in form.description.errors %}
              <small class="text-danger">{{err}}</small>
              {% endfor %}
            </div>

            <input
              type="file"
              class="form-control mt-3"
              name="image"
              id="id_image"
            />
            {% for err in form.image.errors %}
                <small class="text-danger">{{err}}</small>
                {% endfor %}

            <div class="mt-3 mb-3">
                <button type="submit" class="btn mt-3 mb-3 btn-secondary">Submit</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </body>
</html>
```