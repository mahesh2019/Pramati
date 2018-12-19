# Sign Up in Django

1. Since we’re making our own view and url for registration, we need to create a dedicated app. Let’s call it accounts.
(python manage.py startapp accounts)
2. Make sure to add the new app to the INSTALLED_APPS setting in our my_project/settings.py file.
3. Then add a project-level url for the accounts app above our included Django auth app. Django will look top to bottom for url patterns so when it sees a url route within our accounts app that matches one in the built-in auth app, it will choose the accounts route first.
4. Create a new urls file in our accounts app. Note that we are importing a view called SignUp which we’ll implement in the next section.
(touch accounts/urls.py)
5. Final step. Create a template signup.html within the existing project-level templates folder.
(touch templates/signup.html)
6. Finally run the server and open http://127.0.0.1:8000/signup/ in the browser.
