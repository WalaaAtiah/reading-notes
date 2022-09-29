# Class 12

## CRUD:craete Read Update Destroy


## Status Codes Based On REST Methods [source  ](https://www.moesif.com/blog/technical/api-design/Which-HTTP-Status-Code-To-Use-For-Every-CRUD-App/) 

<br>



### 1-In your own words, describe what each group of status code represents:

* 100's =tell the client that the header part of the request has been received and the server will try to use different protocol or telling the client that its request will fail 
* 200's =tell the client that its request was accepted
* 300's = the resource they are requesting isn’t available 
* 400's = the client had error codes
* 500's =server error codes.

### 2- What is a status code 202?
This code tells the client that the request was valid, but its processing will finish sometime in the future

### 3-What is a status code 308?
This tells the client to use another URL to access the resource and not use the current URL anymore.


### 4- What code would you use if an update didn't return data to a client?
204 No Content

### 5-What code would you use if a resource used to exist but no longer does?


### 6-What is the 'Forbidden' status code?

he client has authorized or doesn’t need to authorize itself, but still has no permissions to access the resource.


 [videos  ](hhttps://www.youtube.com/channel/UCFbNIlppjAuEX4znoulh0Cw) 

<br>

### 1- Why do we need to pull our MongoDB database string out of our server and put it into our .env?

### 2- What is middleware?
is software that provides common services and capabilities to applications outside of what’s offered by the operating system. Data management,helps developers build applications more efficiently

### 3- What does app.use(express.json()) do?
It parses incoming JSON requests and puts the parsed data in req
### 4- What does the /:id mean in a route?
### 5- What is the difference between PUT and PATCH?
PUT is a method of modifying resource where the client sends data that updates the entire resource . PATCH is a method of modifying resources where the client sends partial data that is to be updated without modifying the entire data
### 6- How do you make a default value in a schema?

### 7- What does a 500 error status code mean?
the server encountered an unexpected condition that prevented it from fulfilling the request.
### 8- What is the difference between a status 200 and a status 201?
The 200 status code is by far the most common returned. It means, simply, that the request was received and understood and is being processed. A 201 status code indicates that a request was successful and as a result, a resource has been created
<br>
<br>


## Things I want to know more about
