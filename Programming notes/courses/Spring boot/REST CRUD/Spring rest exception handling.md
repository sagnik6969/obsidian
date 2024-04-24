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

 