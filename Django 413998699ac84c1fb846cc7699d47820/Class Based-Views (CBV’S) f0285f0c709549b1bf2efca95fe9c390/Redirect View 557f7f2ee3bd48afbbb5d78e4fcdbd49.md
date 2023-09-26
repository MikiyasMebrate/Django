# Redirect View

- Redirects to a given URL
- Inherited methods and attributes
- Import→ django.views,generic.base.View

Example: 

URL’s 

```python
******from django.views.generic.base import RedirectView******

path('link', RedirectView.as_view(url='https://www.youtube.com/watch?v=Ds2cjOlYtTs&list=RD-aKJPWl5jrM&index=2'), name='yt-link')

```

Templates

```html
<div><a href="{% url 'yt-link' %}">YT</a></div>
```