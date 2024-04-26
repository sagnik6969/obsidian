- Exception handler code is only for a specific rest controller.
- it cant be reused by other controller.
- We need global exception handlers.
       1. Promotes reuse.
       2. Centralized exception handling.
#### Spring `@ControllerAdvice`
- `@ControllerAdvice` is similar to an interceptor or filter. 
- Preprocess request to controllers.
- Postprocess responses to handle exceptions.
- Perfect for global exception handling.
- This is real time use of aspect oriented programming.
- `@ControllerAdvice` will preprocess requests going to controllers and postprocess responses coming out of controllers.

#### Development process
- Just cut and paste the `@ExceptionHandler` code from controller to `@ControllerAdvice`
- The only difference is that this exception handler code will be available to all the controllers.

#### Code
```java
package com.sagnik.restcrud.rest;  

@ControllerAdvice  
public class StudentRestExceptionHandler {  
  
    @ExceptionHandler  
    ResponseEntity<StudentErrorResponse> handleException(StudentNotFoundException studentNotFoundException){  
        StudentErrorResponse studentErrorResponse = new StudentErrorResponse();  
        studentErrorResponse.setStatus(HttpStatus.NOT_FOUND.value());  
        studentErrorResponse.setMessage(studentNotFoundException.getMessage());  
        studentErrorResponse.setTimestamp(System.currentTimeMillis());  
  
        return  new ResponseEntity<StudentErrorResponse>(studentErrorResponse,HttpStatus.NOT_FOUND);  
    }  
  
    @ExceptionHandler  
    ResponseEntity<StudentErrorResponse> handleException(Exception e){  
        StudentErrorResponse studentErrorResponse = new StudentErrorResponse();  
        studentErrorResponse.setMessage(e.getMessage());  
        studentErrorResponse.setStatus(HttpStatus.BAD_REQUEST.value());  
        studentErrorResponse.setTimestamp(System.currentTimeMillis());  
        return new ResponseEntity<>(studentErrorResponse,HttpStatus.BAD_REQUEST);  
    }  
}

```
