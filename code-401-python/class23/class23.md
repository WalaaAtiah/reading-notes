# Read 23 :Django Custom User

## Django Custum User Model:[source](https://learndjango.com/tutorials/django-custom-user-model)

### Setup
* create and navigate into a dedicated directory called accounts for our code
* install Django
* make a new Django project 
* make a new app 
* start the local web server

**Note that we did not run migrate to configure our database. It's important to wait until after we've created our new custom user model before doing so.**

### AbstractUser vs AbstractBaseUser

### Custom User Model
1. update django_project/settings.py
  ```
  AUTH_USER_MODEL = "accounts.CustomUser"
  ```
2. create a new CustomUser model
  
  ```
    from django.contrib.auth.models import AbstractUser
    from django.db import models
    
    class CustomUser(AbstractUser):
        pass
        # add additional fields in here
    
    def __str__(self):
      return self.username

3. create a new file in the accounts app called forms.py.
4. create new UserCreation and UserChangeForm
  ```
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

    
5. update the admin
  ```
  # accounts/admin.py
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
6.  `python manage.py makemigrations accounts`

7.  `python manage.py migrate`

8.  create Superuser  `python manage.py createsuperuser`

9. create `home.html` with links to log in, log out, and sign up. Start by updating settings.py to use a project-level templates directory.

10. **django_project/settings.py**
```
   LOGIN_REDIRECT_URL = "home"
   LOGOUT_REDIRECT_URL = "home"
  ``` 
11. inside the templates folder 
```
(.venv) %touch templates/registration/login.html
(.venv) % touch templates/registration/signup.html
(.venv) % touch templates/base.html
(.venv) % touch templates/home.html
```
12.  **templates/registration/login.html**
 ```
   {% extends "base.html" %}
   
   {% block title %}Log In{% endblock %}
   
   {% block content %}
   <h2>Log In</h2>
   <form method="post">
     {% csrf_token %}
     {{ form.as_p }}
     <button type="submit">Log In</button>
   </form>
   {% endblock %}
   ```
13.  **templates/registration/signup.html**
 ```  
   {% extends "base.html" %}
   
   {% block title %}Sign Up{% endblock %}
   
   {% block content %}
   <h2>Sign Up</h2>
   <form method="post">
     {% csrf_token %}
     {{ form.as_p }}
     <button type="submit">Sign Up</button>
   </form>
   {% endblock %}
   ```
14. **django_project/urls.py**
```
    from django.contrib import admin
    from django.urls import path, include
    from django.views.generic.base import TemplateView
    
    urlpatterns = [
        path("", TemplateView.as_view(template_name="home.html"),     name="home"),
        path("admin/", admin.site.urls),
        path("accounts/", include("accounts.urls")),
        path("accounts/", include("django.contrib.auth.urls")),
    ]
```

15. **accounts/urls.py** app
```
urlpatterns = [
    path("signup/", SignUpView.as_view(), name="signup"),
]
```

16. **accounts/views.py**app
```
class SignUpView(CreateView):
    form_class = CustomUserCreationForm
    success_url = reverse_lazy("login")
    template_name = "registration/signup.html"
```

## DjangoX :[source](https://github.com/wsvincent/djangox)

### Docker
**To use Docker with PostgreSQL as the database update the DATABASES section of django_project/settings.py to reflect the following:**

1. **django_project/settings.py**
```
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
```
2. **django_project/settings.py**
```
# config/settings.py
# django-debug-toolbar
import socket
hostname, _, ips = socket.gethostbyname_ex(socket.gethostname())
INTERNAL_IPS = [ip[:-1] + "1" for ip in ips]
```

3.  `docker-compose up -d --build`
4.  `docker-compose exec web python manage.py migrate`
5.  `docker-compose exec web python manage.py createsuperuser`

6. Add environment variables. There are multiple packages but I personally prefer environs.`pip install environs`
7. Add gunicorn as the production web server.`pip install gunicorn`
8. Update the EMAIL_BACKEND and connect with a mail provider.
Make the admin more secure.
```
from django.core.mail import send_mail

send_mail(
    'Subject here',
    'Here is the message.',
    'from@example.com',
    ['to@example.com'],
    fail_silently=False,
)
```

9. django-allauth supports social authentication if you need that.