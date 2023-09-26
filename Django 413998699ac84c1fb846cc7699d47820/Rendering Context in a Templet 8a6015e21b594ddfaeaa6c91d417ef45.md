# Rendering Context in a Templet

- How do we pass data to our templates?
- In the previous section, we learned about URLs and templates. In Python, we include the HTML file using the `render()` function.
- The `render()` function has three main parameters: the request, the template, and the data. Let's take a look at an example of how to pass data.

```python
def home_view(request):
#I want to pass this data into my template page and access in template page 
    my_context = {
        'name':'Mikiyas',
        'age' : 22
    }
    return render(request, 'index.html', my_context) 
```

- Accessing the data using templates

```python
{%extends 'navbar.html'%}
{%block content%}
    <h1>Home page</h1>
    <p>From Templets</p>
    <p>{{request.user}}</p> #This is build django function to know who is accessing
    <h3>Name: {{name}}</h3> #As we know dictionaries in Python has key and value so to get the value we should use the key name the we can get it
    <h3>Age: {{age}}</h3>
{%endblock%}
```

- Here is the result

![Untitled](Rendering%20Context%20in%20a%20Templet%208a6015e21b594ddfaeaa6c91d417ef45/Untitled.png)

## loop in templet

- What if we have dictionaries of list example:

```python
my_dict = {
    'name' : 'Mikiyas',
    'Age' : 22,
    'skills' : ['JavaScript', 'Python', 'Django']
}
#how I render it 
```

- If I use in as the previous Example the output will be

![Untitled](Rendering%20Context%20in%20a%20Templet%208a6015e21b594ddfaeaa6c91d417ef45/Untitled%201.png)

- As we can see the skill is in the list it doesn’t impress us so the simple way to make separate we can use loop as we know in python.

```python
{%extends 'navbar.html'%}
{%block content%}
    <h1>Home page</h1>
    <p>From Templets</p>
    <p>{{request.user}}</p>
    <h3>Name: {{name}}</h3>
    <h3>Age: {{age}}</h3>
    <h3>Skill:</h3>
    {% for skill in skills %}
        <h4>{{skill}}</h4>
    {% endfor %}
{%endblock%}
```

- Now we can Access them separately easy

## Condition in Templets

Let as assume in the previous example we have skill but what if we don’t want print  ‘Python’ and replace it by ‘Java; so we can use also use conditions in templets 

 

```python
{%extends 'navbar.html'%}
{%block content%}
    <h1>Home page</h1>
    <p>From Templets</p>
    <p>{{request.user}}</p>
    <h3>Name: {{name}}</h3>
    <h3>Age: {{age}}</h3>
    <h3>Skill:</h3>
    {% for skill in skills %}
          {%if skill == 'python' %}
             <h4>Java</h4>
           {%else%}       
             <h4>{{skill}}</h4>
          {%endif%}
    {% endfor %}
{%endblock%}
```

- Useful Filter

```python
{{name|capfirst}} #Mikiyas
{{name|upper}}  #MIKIAS
```