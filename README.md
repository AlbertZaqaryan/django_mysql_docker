A batteries-included Django starter project. To learn more visit LearnDjango.com.

 djangox_screencast.mov 
🚀 Features
Django 5.0 & Python 3.12
Install via Pip or Docker
User log in/out, sign up, password reset via django-allauth
Static files configured with Whitenoise
Styling with Bootstrap v5
Debugging with django-debug-toolbar
DRY forms with django-crispy-forms
Custom 404, 500, and 403 error pages
Table of Contents
Installation
Pip
Docker
Next Steps
Contributing
Support
License
📖 Installation
DjangoX can be installed via Pip or Docker. To start, clone the repo to your local computer and change into the proper directory.

$ git clone https://github.com/wsvincent/djangox.git
$ cd djangox
Pip
$ python -m venv .venv

# Windows
$ Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
$ .venv\Scripts\Activate.ps1

# macOS
$ source .venv/bin/activate

(.venv) $ pip install -r requirements.txt
(.venv) $ python manage.py migrate
(.venv) $ python manage.py createsuperuser
(.venv) $ python manage.py runserver
# Load the site at http://127.0.0.1:8000
Docker
To use Docker with PostgreSQL as the database update the DATABASES section of django_project/settings.py to reflect the following:

# django_project/settings.py
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "postgres",
        "USER": "postgres",
        "PASSWORD": "postgres",
        "HOST": "db",  # set in docker-compose.yml
        "PORT": 5432,  # default postgres port
    }
}
The INTERNAL_IPS configuration in django_project/settings.py must be also be updated:

# config/settings.py
# django-debug-toolbar
import socket
hostname, _, ips = socket.gethostbyname_ex(socket.gethostname())
INTERNAL_IPS = [ip[:-1] + "1" for ip in ips]
And then proceed to build the Docker image, run the container, and execute the standard commands within Docker.

$ docker-compose up -d --build
$ docker-compose exec web python manage.py migrate
$ docker-compose exec web python manage.py createsuperuser
# Load the site at http://127.0.0.1:8000
Next Steps
Add environment variables. There are multiple packages but I personally prefer environs.
Add gunicorn as the production web server.
Update the EMAIL_BACKEND and connect with a mail provider.
Make the admin more secure.
django-allauth supports social authentication if you need that.
I cover all of these steps in tutorials and premium courses over at LearnDjango.com.

🤝 Contributing
Contributions, issues and feature requests are welcome! See CONTRIBUTING.md.

⭐️ Support
Give a ⭐️ if this project helped you!

License
The MIT License
