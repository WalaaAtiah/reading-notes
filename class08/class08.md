
# Class 08

## Readings: APIs:

## API Design Best Practices [source  ](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design) 

<br>



### 1- What does REST stand for?
is an architectural style for building distributed systems based on hypermedia

### 2-REST APIs are designed around a ____.
resources,which are any kind of object, data, or service that can be accessed by the client.

### 3-What is an identifier of a resource? Give an example.
the URI for a particular customer order might be:
### 4- What are the most common HTTP verbs?
The most common operations are GET, POST, PUT, PATCH, and DELETE.
### 5- What should the URIs be based on?
nouns (the resource) and not verbs (the operations on the resource).
### 6- Give an example of a good URI.
/customers is the path to the customers collection, and /customers/5 is the path to the customer with ID equal to 5. This approach helps to keep the web API intuitive.

### 7- What does it mean to have a ‘chatty’ web API? Is this a good or a bad thing?
bad thing :that expose a large number of small resources. Such an API may require a client application to send multiple requests to find all of the data that it requires. Instead, you might want to denormalize the data and combine related information into bigger resources that can be retrieved with a single request.

### 8-What status code does a successful GET request return?
HTTP status code 200 (OK)
### 9-What status code does an unsuccessful GET request return?
404 (Not Found).
### 10-What status code does a successful POST request return?
 HTTP status code 201 (Created).
### 11-What status code does a successful DELETE request return?
return HTTP status code 204 (No Content) 



## Things I want to know more about
need to read it again to get all information inside it