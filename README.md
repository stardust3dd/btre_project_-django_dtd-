01. conda activate <> # activate project VE
02. conda env list # list all available VEs
03. pip freeze > requirements.txt # create requirements file
04. pip list # list all dependencies from current VE
05. django-admin startproject <> . # create project inside current folder
06. git init # initialize empty git repo in current folder
07. create .gitignore in root folder. Specify in .gitignore what need not be pushed to git
    Search for django in gitignore.io to know what to ignore
08. git add . # add all content from current folder to initialised repo
09. git commit -m "message" # commit the repo with optional message
10. python manage.py runserver # run django server on default port 8000
11. python manage.py startapp <new_app> # create a django app
12. add 'new_app.apps.PagesConfig' to INSTALLED_APPS in settings.py
11. db.sqlite3 is the default sqlite database supplied by django. Not good for production environments. Suitable for small sites, prototyping & testing.
12. __init__ is always empty. No need to touch.
13. settings.py
    - Contains mostly key-value pairs.
    - SECRET_KEY should be kept hidden. Do not include it in file
    - DEBUG is True when in development, False in production
    - Include domain names in ALLOWED_HOSTS
    - Include all apps in INSTALLED_APPS
    - STATIC_ROOT = os.path.join(BASE_DIR, 'static')
    - STATICFILES_DIRS = [os.path.join(BASE_DIR, 'btre/static')]
14. urls.py
    - Routing file
15. wsgi.py
    - Web Server Gateway Interface that specifies how the web server communicates with the web app
16. create static folder inside the automatically created project folder
    add /static, /media to .gitignore
16. python manage.py collectstatic # collect static files
17. python manage.py migrate # to apply unapplied migratons

POSTGRESQL
17. pip install psycopg2 # to interface python w postgresql
17. Download from postgresql.org, also download pgadmin
18. \password postgres # assign password to existing user postgres
19. CREATE DATABASE btredb OWNER postgres;    
    - in settings.py paste
    DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'btredb',
        'USER': 'postgres',
        'PASSWORD': 'mayukh',
        'HOST': 'localhost',
        'PORT': '1234',
    }
}
20. \l # list all available postgresql databases
21. \q # to exit

## DATABASE SCHEMA
    ### LISTING
        - id: INT, AUTO INC
        - realtor: INT, FOREIGN KEY[realtor]
        - title: STR
        - address: STR
        - city: STR
        - state: STR
        - zipcode: STR
        - desc: TEXT
        - price: INT
        - bedrooms: INT
        - bathrooms: INT
        - garage: INT, DEFAULT 0
        - sqft: INT
        - lot_size: FLOAT
        - list_date: DATE
        - is_published: BOOL, DEFAULT 1
        - photo_main: STR
        - photo_1: STR
        - photo_2: STR
        - photo_3: STR
        - photo_4: STR
        - photo_5: STR
        - photo_6: STR
    ### REALTOR
        - id: INT, AUTO INC 
        - name: STR
        - photo: STR
        - desc: TEXT
        - email: STR
        - phone: STR
        - is_mvp: BOOL, DEFAULT 0
        - hire_date: DATE
    ### CONTACT
        - id: INT, AUTO INC 
        - user_id: INT
        - listing: INT
        - listing_id: INT
        - name: STR
        - email: STR
        - phone: STR
        - message: TEXT
        - contact_date: DATE

22. python manage.py makemigrations
22. python manage.py sqlmigrate <app> 0001 # to view the actual SQL commands running during makemigrations

23. python manage.py createsuperuser # to create admins

24. create new git repo
25. git remote add origin (4th coomand)
26. git push -u origin master (5th command)