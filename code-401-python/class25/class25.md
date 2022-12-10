# Read-25: Django REST Framework & Docker

## Beginner's Guide to Docker:[source](https://wsvincent.com/beginners-guide-to-docker/)

* ### Docker:
   which is a way to isolate and run entire applications. With Docker it doesn’t matter if you are using a Mac, Windows, or Linux computer anymore. The entire development environment is isolated: programming language, software packages, databases, and more.

* ### Linux Containers
Docker is really just Linux containers which are a type of virtualization.

* ### Containers vs Virtual Environments
   * Virtual environments : are used to isolate Python  software packages locally. We can create an isolated  box for individual projects so one can use Python 2. 7 and Django 1.5 while another can use Python 3.5  and Django 2.1 on the same computer. Virtual  environments are great.
   * 
   * virtual environments can only isolate Python packages. They still rely on a global, system-level installation of Python albeit they can refer to the proper version.

* ### Install Docker
 1. [download the desktop app on our computer](https://www.docker.com/get-started/)
 2. 
 3.  if you are on Linux, you will need to add it manually. You can do this by running the command `sudo pip install docker-compose`
 4.  `docker-compose --version`
 5.  To confirm Docker installed correctly we can run our first command `docker run hello-world`
 6.  `docker info`
   
      ```
      $ docker info
      Containers: 1
       Running: 0
       Paused: 0
       Stopped: 1
       Images: 1
      ```
 7. `docker image ls`
     ```
    $ docker image ls
    REPOSITORY          TAG        IMAGE ID                CREATED             SIZE
    hello-world         latest     fce289e99eb9            12 months ago       1.84kB
        ```
   
 8. `docker container ls -la`

```
$ docker container ls -la
CONTAINER ID IMAGE        COMMAND   CREATED  STATUS     PORTS  NAMES
c827847463a1 hello-world  "/hello"  About... Exited (0)        blissful_swartz
```

### Images and Containers
* **Images** 
  1. First create a local directory on your computer for our code
    ```
    $ cd ~/Desktop
    $ mkdir code && cd code
    $ mkdir python3.7 && cd python3.7
    ```
  2. Now we need to define the image with a Dockerfile. This is similar to a Pipenv or a requirements.txt file
    ```
    $ touch Dockerfile

    ```
* **Image Builds**
    ```
    $ docker image build .
    Sending build context to Docker daemon  2.048kB
    Step 1/1 : FROM python:3.7-alpine
    3.7-alpine: Pulling from library/python
    c9b1b535fdd9: Pull complete
    2cc5ad85d9ab: Pull complete
    53a2fca3c2ea: Pull complete
    30fce49de8b1: Pull complete
    49bcb9571cc7: Pull complete
     Digest:sha256:7655eea15dfd981eeb7d243af21e8561e967709caba938d50b136cdb992f3546
    Status: Downloaded newer image for python:3.7-alpine
     ---> b2c276538711
    Successfully built b2c276538711

  ```

### The important takeaways from this tutorial are this:

Docker is a way to run Linux containers
Containers are a lightweight alternative to Virtual Machines
Dockerfile is a list of instructions for creating an image
Images are made up of one or more layers
Containers are a running instance of an image
docker-compose.yml controls how to run the container
Containers are stateless and ephemeral in nature. We can link the local filesystem via volumes but things become more complex with databases (which we didn’t cover here).



## Django for APIs - Library Website:[source](https://djangoforapis.com/library-website-and-api/)