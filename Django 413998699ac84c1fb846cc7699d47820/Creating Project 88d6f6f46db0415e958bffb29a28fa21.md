# Creating Project

- First create virtual environment

```python
pyhton -m venv environment_name
```

- Activate it

```python
environment_name\Scripts\activate
```

- To Deactivate it

```python
deactivate
```

- Then install django to your project

```python
pip install django 
```

- Creating Project

```python
django-admin startproject project_name
```

- Run Server

```python
python manage.py runserver
```

- Creating Apps

```python
python manage.py startapp app_name
#And register your app in the setting
```

- To Check or to run your data base

```python
python [manage.py](http://manage.py/) migrate
```