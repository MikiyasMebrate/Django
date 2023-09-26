# Pure Django Form

```python
class RawProductForm(forms.Form):
    title =forms.CharField()
    description = forms.CharField()
    link = forms.CharField()
```

```python
from .forms import createNewsPost,RawProductForm

def create_form_post(request):
    my_form = RawProductForm()
    if request.method == 'POST':
       my_form = RawProductForm(request.POST)
       if my_form.is_valid():
           post_news.objects.create(**my_form.cleaned_data)
    context = {
        'form':my_form
    }
    return render(request, 'form.html', context)
```

```python
<form method="post">{% csrf_token %}
         {{form.as_p}}
         <button type="submit">Submit</button>
    </form>
```