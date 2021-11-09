Reading Notes 12 - C.R.U.D.

## Status Codes

From [Moesif.com](https://www.moesif.com/blog/technical/api-design/Which-HTTP-Status-Code-To-Use-For-Every-CRUD-App/)

1. In your own words, describe what each group of status code represents:
 - 100’s = These are informational responses, they are usually a provisional response before the normal response comes.
 - 200’s = A success, things are okay/accepted/created etc.
 - 300’s = These ones mean the browser needs to do more to complete the request like redirect.
 - 400’s = Indicates and error on the client side, like a bad request, access denied/forbidden or not found.
 - 500’s = Server side error, internal or service not available.
2. What is a status code 202?
  - The request was accepted. It's good.
3. What is a status code 308?
  - This indicates a permanent redirection to a different URI.
4. What code would you use if an update didn’t return data to a client?
  - 204 for no content.
5. What code would you use if a resource used to exist but no longer does?
  - 410 Gone for data that has been removed and has no forwarding.
6. What is the ‘Forbidden’ status code?
  - The client is recognized but not authorized to receive the requested resource.

## Build a REST API


1.  Why do we need to pull our MongoDB database string out of our server and put it into our .env?
  - Because it is what we use to access the mongoDB but it's private information so we'll need to keep it separate. Plus when we deploy outside localhost we'll need to reference that location. 
2.  What is middleware?
  - A middleware function is one that combines multiple similar functions dealing with the same request.
3.  What does app.use(express.json()) do?
  - Allows the server to accept JSON as the body inside of a GET/POST etc.
4.  What does the /:id mean in a route?
  - It is a parameter on a request.
5.  What is the difference between PUT and PATCH?
  - PATCH updates only the specific piece of information that gets passed as compared with PUT which updates the whole item.
6.  How do you make a default value in a schema?
  - Using 'default' as the key and a default value and the value.
7.  What does a 500 error status code mean?
  - It means there is an error on the server, as apposed to the client. Some kind of internal issue or bad configuration/code.
8.  What is the difference between a status 200 and a status 201?
  - 200 indicates the request succeeded and includes describing the result of a PUT/POST request but the 201 specifically reports that the new resources were created after a POST (and some PUT) requests.


From the YouTube video on [Web Dev Simplified](https://www.youtube.com/channel/UCFbNIlppjAuEX4znoulh0Cw)

## Things I want to know more about

- MongoDB schema planning
- How to let a server use UDP to stream data instead of send/receive TCP.
