# read 28 : Authentication & Production Server

##  JSON Web Tokens [source](https://jwt.io/introduction/)

### What is JSON Web Token?
**SON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed.**

### When should you use JSON Web Tokens?

* **Authorization**:Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token.
  
* **Information Exchange**: ou can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.
  
### What is the JSON Web Token structure?

**In its compact form, JSON Web Tokens consist of three parts separated by dots (.), which are:**

* Header
  ```
  {
  "alg": "HS256",
  "typ": "JWT"
  }

  ```
* Payload
  ```
   {
     "sub": "1234567890",
     "name": "John Doe",
     "admin": true
   }
  ```

* Signature
  ```
  HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
  ```

`xxxxx.yyyyy.zzzzz`

### How do JSON Web Tokens work?

![Tokens](https://cdn2.auth0.com/docs/media/articles/api-auth/client-credentials-grant.png)


##  DRF JWT Authentication [source](https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html)

### How to Use JWT Authentication with Django REST Framework

### * **Installation & Setup**
   
 1.    `pip install djangorestframework_simplejwt`
 2.    project settings.py 
         
         ```
         REST_FRAMEWORK = {
            'DEFAULT_AUTHENTICATION_CLASSES': [       
                  'rest_framework_simplejwt.authentication.JWTAuthentication',
             ],
        }

         ``` 
3. project urls.py
    ```
    from django.urls import path
    from rest_framework_simplejwt import views as jwt_views
    
    urlpatterns = [
        # Your URLs...
        path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
        path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
    ]
    ```

## Django Runserver Is Not Your Production Server [source](https://vsupalov.com/django-runserver-in-production/)

**If you want to run Django in production, be sure to use a production-ready web server like Nginx, and let your app be handled by a WSGI application server like Gunicorn.**

**If you plan on running on Heroku, a web server is provided implicitly. You don’t have to take care of it. You just need to specify a command to run your application server (again, Gunicorn is fine) in the Procfile.**
