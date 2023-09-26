# Django Templating Engine Basics

- Let's say you have a common page in your site, such as a navbar or a title, that is used on multiple pages. Instead of duplicating the code on each page, you can create a separate HTML file for that page and then include it in the other pages. This is useful for reducing code duplication and making it faster to access the page.
- For example, if you have a head tag with a title that is the same on multiple pages, you can create a separate file for that title and include it in each page.

---

Using Extend 

```python
#title.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>From Navbar</title>
</head>
<body>
    {% block content%} 
        #Here we'll repace the html code 
    {%endblock%}
</body>
</html>

#Home_page.html
{%extends 'navbar.html'%} #First extend the page 
{%block content%}   #Replace by this code 
    <h1>Home page</h1>
    <p>From Templets</p>
    <p>{{request.user}}</p>
{%endblock%}

```

- The Final output will be

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>From Navbar</title>
</head>
<body>
   <h1>Home page</h1>
    <p>From Templets</p>
</body>
</html>
```

we can also use include 

 

```python
{%include 'navbar.html'%}
```