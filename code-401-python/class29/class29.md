# read 29: API Deployment

## Django Settings Best Practices:[source](https://djangostars.com/blog/configuring-django-settings-best-practices/)

### Managing Django Settings: Issues

* **Different environments. Usually, you have several environments: local, dev, ci, qa, staging, production, etc. Each environment can have its own specific settings (for example: DEBUG = True, more verbose logging, additional apps, some mocked data, etc)**
  
* **Sensitive data. You have SECRET_KEY in each Django project. On top of this there can be DB passwords and tokens for third-party APIs like Amazon or Twitter. This data cannot be stored in VCS.**
  
* **Sharing settings between team members**
* **Django settings are a Python code.**

### Setting Django Configurations: Different Approaches 

1. **settings_local.py**
   **This is the oldest method. I used it when I was configuring a Django project on a production server for the first time. I saw a lot of people use it back in the day, and I still see it now.**

  * `settings.py file:`
    ```
        ALLOWED_HOSTS = ['example.com']
        DEBUG = False
        DATABASES = {
            'default': {
                'ENGINE': 'django.db.backends.postgresql',
                'NAME': 'production_db',
                'USER': 'user',
                'PASSWORD': 'password',
                'HOST': 'db.example.com',
                'PORT': '5432',
                'OPTIONS': {
                    'sslmode': 'require'
                }
            }
        }
        
        
        
        from .settings_local import *
    ```

  * `settings_local.py file:`

```
    ALLOWED_HOSTS = ['localhost']
    DEBUG = True
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': 'local_db',
            'HOST': '127.0.0.1',
            'PORT': '5432',
        }
    }
```
        

### 12 Factors
**12 Factors is a collection of recommendations on how to build distributed web-apps that will be easy to deploy and scale in the Cloud. It was created by Heroku, a well-known Cloud hosting provider.**


1. Codebase 
2. Dependencies 
3. Config 
4. Backing services 
5. Build, release, run 
6. Processes 
7. Port binding 
8. Concurrency 
9. Disposability 
10. Dev/prod parity 
11. Logs 
12. Admin processes


### django-environ
**Based on the above, we see that Django env variables are the perfect place to store settings.**


**Technically it’s a merge of:**

* envparse
* honcho
* dj-database-url
* dj-search-url
* dj-config-url
* django-cache-url


### Naming Conventions
**Naming of variables is one of the most complex parts of development. So is naming of settings. We can’t imply on Django or third-party applications, but we can follow these simple rules for our custom (project) settings:**

* Give meaningful names to your settings.
* Always use the prefix with the project name for your custom (project) settings.
* Write descriptions for your settings in comments.