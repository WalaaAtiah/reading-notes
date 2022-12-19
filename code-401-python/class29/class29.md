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


<br>

## What Is SSH: Understanding Encryption, Ports and Connection:[source](https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work)

### What Is SSH?

SSH, or Secure Shell Protocol, is a remote administration protocol that allows users to access, control, and modify their remote servers over the internet.

SSH service was created as a secure replacement for the unencrypted Telnet and uses cryptographic techniques to ensure that all communication to and from the remote server happens in an encrypted manner.

### How Does SSH Work

If you’re using Linux or Mac, then using SSH is very simple. If you use Windows, you will need to utilize an SSH client to open SSH connections. The most popular SSH client is PuTTY.

### Understanding Different Encryption Techniques

The significant advantage offered by SSH over its predecessors is the use of encryption to ensure a secure transfer of information between the host and the client. Host refers to the remote server you are trying to access, while the client is the computer you are using to access the host. There are three different encryption technologies used by SSH:

1. Symmetrical encryption

2. Asymmetrical encryption

3. Hashing

**Symmetric Encryption**

Symmetric encryption is a form of encryption where a secret key is used for both encryption and decryption of a message by both the client and the host. Effectively, anyone possessing the key can decrypt the message being transferred.

Symmetrical encryption is often called shared key or shared secret encryption. There is usually only one key that is used, or sometimes a pair of keys, where one key can easily be calculated using the other key.

**Asymmetric Encryption**

Unlike symmetrical encryption, asymmetrical encryption uses two separate keys for encryption and decryption. These two keys are known as the public key and the private key. Together, both these keys form a public-private key pair.

A public key can be used by any individual to encrypt a message and can only be decrypted by the recipient who possesses their particular private key, and vice versa.

**Hashing**

One-way hashing is another form of cryptography used in Secure Shell Connections. One-way-hash functions differ from the above two forms of encryption in the sense that they are never meant to be decrypted. They generate a unique value of a fixed length for each input that shows no clear trend which can be exploited. This makes them practically impossible to reverse.

It is easy to generate a cryptographic hash from a given input, but impossible to generate the input from the hash. This means that if a client holds the correct input, they can generate the cryptographic hash and compare its value to verify whether they possess the correct input.

SSH uses hashes to verify the authenticity of messages. This is done using HMACs, or Hash-based Message Authentication Codes. This ensures that the command received is not tampered with in any way.

