# Custom Form Design

- Previously we have seen about form but the form already provided by django now we’ll create our new form

In view Create a new method function 

```python
def create_form_post(request):
    if request.method == 'POST':  #If we sent the form in POST 
        my_new_title = request.POST.get('title')  #to get the value of title it get elements by there names
        print(my_new_title) #Print the input from client data

        
    context = {} #we don't need any data for now
    return render(request, 'form.html', context)
```

The Html code

```python
<form method="post">{% csrf_token %} #if we use post method we should add {% csrf_token %} to encryption method
         <input type="text" name="title" id="" placeholder="Your Title">
         <button type="submit">Submit</button>
    </form>
```