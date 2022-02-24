# Reading Notes 09 -- WRRC and Java

## Review: High-level HTTP

From [Things I Brushed Up On This Week: The HTTP Request Lifecycle](https://dev.to/dangolant/things-i-brushed-up-on-this-week-the-http-request-lifecycle-)

The Lifecycle Overview:
1. Local processing
  - The browser parses the web address i.e `<protocol>://<host><:optional port>/<path/to/resource><?query>`
  - The browser checks if it can resolve the ip with local caches.
2. Resolve and IP
  - If no local resolution exists for the ip the browser sends a DNS request to a DNS server.
  - This request is sent via UDP to be fast but it still may have to bounce to a few servers to fulfill the request.
3. Establish a TCP connection
  - With the ip in hand the browser can get a TCP connection set established. 
  - TCP is more reliable that UDP because the protocol requires handshaking -- three-way.
4. Send an HTTP request
  - The request that was parsed from the web address includes the request details.
  - After the server gets the request the server generates a response and sends that back
5. Tearing Down and Cleaning Up
  - The browser processes the response and displays the website.


## Java HTTP Request example

From [Baeldung article](https://www.baeldung.com/java-http-request)

1. Overview
  - HttpUrlConnection is older and HttpClientAPI is meant to be its replacement.
2. HttpUrlConnection
  - HttpUrlConnection is a class for HTTP requests without additional libraries.
  - It is more invonvenient and doesn't provide advanced functionality for adding headers and authentication
3. Creating a request
  - The `openConnection()` method can be used with a the URL class on an instance of HttpUrlConnection.
  - The request type can be set to GET, POST, HEAD, OPTIONS, PUT, DELETE, or TRACE.
4. Adding request parameters
  - To use set the HttpUrlConnection's `doOutput` property to true.
  - Keyvalue pairs can be used to add parameters.
  - A builder can be setup to convert a map into a string with the correct syntax.
5. Setting request headers
  - Use the `setRequestProperty()` method.
  - Read the value of a header from a connection with `getHeaderField()`
6. Configuring timeouts
  - `setConnectionTimeout()`
  - `setReadTimeout()`
7. Handling cookies
  - To read cookies from a response get the value from the "Set-Cookie" header field.
  - To add cookies a "cookie store" can be used to collect all the cookies and a StringUtils method `join()` can be used to parse the cookie store data.
8. Handling redirects
 - Connections can have redirects enabled or disabled with the `setInstantceFollowRedirects()` method.
 - All connections can be set with `HttpUrlConnection.setFollowRedirects()`
9. Reading the response
  - Get status with the `getResponseCode()` method.
  - The response can be read as a an input stream into a BufferedReader and ultimately into a StringBuffer.
  - Close the connection with `close()` and disconnect with the `disconnect()` method.
10. Reading the response on failed requests
  - If the status response is in the error range we can use `getErrorStream` to get the error.
11. Building the full response
  - Since its not possible to get the full response directly we could set up a FullResponseBuilder class.
