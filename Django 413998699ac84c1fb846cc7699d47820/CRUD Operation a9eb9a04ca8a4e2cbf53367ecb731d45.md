# CRUD Operation

Update: To update content first we need to have to search which content is going to be updated. 

```python
#View
def edit_form(request, pk):
    news = Blog.objects.get(id=pk)
    form = Blog_Form(instance=news)
    if request.method == 'POST':
        form = Blog_Form(request.POST or None, request.FILES or None, instance=news)
        if form.is_valid():
            form.save()
            return redirect('index')
    context = {
        'form' : form
    }
    return render(request, 'news_form.html', context)
```

Delete: 

- First Create html file to confirm otherwise to return to the previous page

```html
<!--delete.html-->
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
    {% include 'index.html' %}
    <form action="" method="POST">
       {% csrf_token %}
       <p>Are you sure you want to delete {{obj}}?</p>
       <a href="{{request.META.HTTP_REFERER}}">Go Back</a>  <!--To go back to previous page-->
       <input type="submit" value="Confirm">
    </form>
    
  </body>
</html>
```

- To be deleted and we should to pass id to delete it

```html
<body class="bg-light">
    {% include 'navbar.html'%}

     <div class="container">
      <div class="row mt-5 d-flex justify-content-center">
        <div class="col-md-8">
          <img src="/media/{{news.image}}" alt="" class="img-fluid">
          <h4 class="mt-2">{{news.title}}</h4>
           <p class="mt-2">{{news.description}}</p>
           <a href="{% url 'edit_form' news.id %}" class="btn btn-secondary mt-2">Edit</a>
           <a href="{% url 'delete' news.id %}" class="btn btn-danger mt-2">Delete</a>
        </div>
       </div>
     </div>
  </body>
```

- URL’s

```python
path('delete/<str:pk>/', views.delete_form, name='delete')
```

- Views

```python
def delete_form(request, pk):
    news = Blog.objects.get(id=pk)
    if request.method == 'POST':
        news.delete()
        return redirect('index')
    context = {
        'obj' : news
    }

    return render(request, 'delete.html',context)
```