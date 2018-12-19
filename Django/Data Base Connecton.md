# Data Base Connecton

Django is a flexible framework for quickly creating Python applications. By default, Django applications are configured to store data into a lightweight SQLite database file. While this works well under some loads, a more traditional DBMS can improve performance in production.

1.Create a Database and Database User.
(sudo su - postgres)
You should now be in a shell session for the postgres user. Log into a Postgres session by typing:
(psql)

2.Create a databse for our django.
(CREATE DATABASE myproject;)
(CREATE USER myprojectuser WITH PASSWORD 'password';)

3.Now, all we need to do is give our database user access rights to the database we created:
(GRANT ALL PRIVILEGES ON DATABASE myproject TO myprojectuser;)
Exit the SQL prompt to get back to the postgres user's shell session:(\q)
Exit out of the postgres user's shell session to get back to your regular user's shell session:
(exit)
4.Configure the Django Database Settings
(nano ~/myproject/myproject/settings.py)
change the settings like below:
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'myproject',
        'USER': 'myprojectuser',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '',
    }
}
5.Migrate the Database and Test your Project
(cd ~/myproject
python manage.py makemigrations
python manage.py migrate)

6.After creating the database structure, we can create an administrative account by typing:
(python manage.py createsuperuser)
(python manage.py runserver 0.0.0.0:8000)

7.We will get Django root page at:
(http://server_domain_or_IP:8000)

By accessing the admin interface, we have confirmed that our database has stored our user account information and that it can be appropriately accessed.



