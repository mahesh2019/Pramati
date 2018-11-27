# Setup

    create a new accounts directory for our code on the Desktop
    install Django with Pipenv
    start the virtual environment shell
    create a new Django project called my_project
    create a new Sqlite database with migrate
    run the local server

# The Django auth app

Django automatically installs the auth app when a new project is created. Look in the settings.py under INSTALLED_APPS and you can see auth is one of several built-in apps Django has installed for us.

# Login Page
Use the below commands for login page

mkdir template
mkdir templates/registration
touch templates/registration/login.html
Add LOGIN_REDIRECT_URL = '/' to settings.py

# Creating User

python manage.py createsuperuser

Below are the fields you need to fill

Username (leave blank to use mahesh):
Email address: 
Password:
Password (again):

# Create Home Page

touch templates/base.html

<html>
<head>
  <meta charset="utf-8">
  <title>{% block title %}Django Auth Tutorial{% endblock %}</title>
</head>
<body>
  <main>
    {% block content %}
    {% endblock %}
  </main>
</body>
</html>


touch templates/home.html

{% extends 'base.html' %}

{% block title %}Home{% endblock %}

{% block content %}
{% if user.is_authenticated %}
  Hi {{ user.username }}!
{% else %}
  <p>You are not logged in</p>
  <a href="{% url 'login' %}">login</a>
{% endif %}
{% endblock %}

After this run manage.py file

















