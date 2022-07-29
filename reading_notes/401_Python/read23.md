# Readings: Django Custom User

> Django Best Practices: Custom User Models 
- AbstractUser vs AbstractBaseUser 
  - There are two modern ways to create a custom user model in Django: AbstractUser and AbstractBaseUser. 
  - In both cases we can subclass them to extend existing functionality however AbstractBaseUser requires much, much more work.
  - using AbstractUser which actually subclasses AbstractBaseUser but provides more default configuration.


> Custom User Model Steps 
- Creating our initial custom user model requires four steps:
  - update django_project/settings.py
  - create a new CustomUser model
  - create new UserCreation and UserChangeForm
  - update the admin
- Add `account` in INSTALLED_APPS 
- command `AUTH_USER_MODEL = "accounts.CustomUser"   new`
- update `accounts/models.py` with a new User model which we'll call CustomUser.
```
accounts/models.py
from django.contrib.auth.models import AbstractUser
from django.db import models
class CustomUser(AbstractUser):
    pass
    add additional fields in here
    def __str__(self):
        return self.username
```
- create a new file in the `accounts` app called `forms.py`.
```
accounts/forms.py
from django import forms
from django.contrib.auth.forms import UserCreationForm, UserChangeForm
from .models import CustomUser
class CustomUserCreationForm(UserCreationForm):
    class Meta:
        model = CustomUser
        fields = ("username", "email")
class CustomUserChangeForm(UserChangeForm):
    class Meta:
        model = CustomUser
        fields = ("username", "email")
```
- update `admin.py` since the Admin is highly coupled to the default User model.
```
accounts/admin.py
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin
from .forms import CustomUserCreationForm, CustomUserChangeForm
from .models import CustomUser
class CustomUserAdmin(UserAdmin):
    add_form = CustomUserCreationForm
    form = CustomUserChangeForm
    model = CustomUser
    list_display = ["email", "username",]
admin.site.register(CustomUser, CustomUserAdmin)
```
- Add these lines in the `settings.` file
```
django_project/settings.py
LOGIN_REDIRECT_URL = "home"
LOGOUT_REDIRECT_URL = "home"
```
- Create your Templates 
- Update `urls` file
```
urlpatterns = [
    path("accounts/", include("accounts.urls")),
    path("accounts/", include("django.contrib.auth.urls")),
]
```
- Create your `views`
- Then check your database via admin panel


> DjangoX 
- Djangox Python, Django, Docker, Whitenoise, Starter Template 
- A batteries-included Django starter project. For a production-ready version see the book Django for Professionals .


> Features
- Django 3.1 & Python 3.8
- Install via Pip , Pipenv , or Docker
- User log in/out, sign up, password reset via django-allauth
- Static files configured with Whitenoise
- Styling with Bootstrap v4
- Debugging with django-debug-toolbar
- DRY forms with django-crispy-forms


> Installation Steps using Docker
- DjangoX can be installed via Pip, Pipenv, or Docker depending upon your setup. To start, clone the repo to your local computer and change into the proper directory.
- `$ git clone https://github.com/wsvincent/djangox.git`
- `$ cd djangox`
- `$ docker build .`
- `$ docker-compose up -d`
- `$ docker-compose exec web python manage.py migrate`
- `$ docker-compose exec web python manage.py createsuperuser`
- Load the site at http://127.0.0.1:8000
- For Docker, the INTERNAL_IPS configuration in config/settings.py must be updated to the following:
  - `config/settings.py`
  - `django-debug-toolbar`
  - `import socket`
  - `hostname, _, ips = socket.gethostbyname_ex(socket.gethostname())`
  - `INTERNAL_IPS = [ip[:-1] + "1" for ip in ips]`
- Setup
  - Run Migrations
    - `(djangox) $ python manage.py migrate`

  - Create a Superuser
    - `(djangox) $ python manage.py createsuperuser`

  - Confirm everything is working:
    - `(djangox) $ python manage.py runserver`
  - Load the site at http://127.0.0.1:8000


> Resources 
- create custom user model a steps : https://dev.to/earthcomfy/getting-started-custom-user-model-5hc 
- DjangoX: https://pythonlang.dev/repo/wsvincent-djangox/ 
- Create custom user model: https://learndjango.com/tutorials/django-custom-user-model
- GitHub Repo DjangoX: https://github.com/wsvincent/djangox 
- Configuration: https://docs.djangoproject.com/en/3.0/topics/auth/customizing/auth-custom-user 