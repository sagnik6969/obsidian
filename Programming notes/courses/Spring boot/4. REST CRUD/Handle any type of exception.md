```java
@ExceptionHandler  
ResponseEntity<StudentErrorResponse> handleException(Exception e){  
    StudentErrorResponse studentErrorResponse = new StudentErrorResponse();  
    studentErrorResponse.setMessage(e.getMessage());  
    studentErrorResponse.setStatus(HttpStatus.BAD_REQUEST.value());  
    studentErrorResponse.setTimestamp(System.currentTimeMillis());  
    return new ResponseEntity<>(studentErrorResponse,HttpStatus.BAD_REQUEST);  
}
```
- the `handleException` method will accept all type of exceptions
