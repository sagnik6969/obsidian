- If there is an error return the error as JSON.
#### Development process
1.  Create a custom error response class.
2. Create a custom exception class.
3. Update the rest service to throw exception based on condition.
4. Add exception handler method using `@ExceptionHandler`
#### Custom Error Response Class
1. This will be sent back to the client as json.
2. We will define a java POJO.
3. `jackson` will be responsible for converting the POJO to json. 
#### Create a custom exception
1. The custom exception will be used by rest service to throw an exception based on condition.
2. Example: `StudentNotFoundException`
#### Add exception handler method
- Define exception handler method with `@ExceptionHandler` annotation from spring.
- exception handler will return a response entity. 
- response entity is just a wrapper for for HTTP response object.
- Response entity provides fine grained control to specify
     1. HTTP Status code
     2. HTTP headers 
     3. response body


 