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
#### Code
##### `StudentRestController`
```java  
@RestController  
@RequestMapping("/api")  
public class StudentRestController {  
  
    private List<Student> students;  
  
    @PostConstruct  
    public void loadData(){  
        students = new ArrayList<>();  
        students.add(new Student("Sagnik","Jana"));  
        students.add(new Student("BC","Jana"));  
  
    }  
  
  
    @GetMapping("/students/{studentId}")  
    public Student getStudent(@PathVariable int studentId){  
        if(studentId < 0 || studentId >= this.students.size()){  
            throw new StudentNotFoundException("Student with id = " + studentId + " not found");  
        }  
        return students.get(studentId);  
    }  
  
    @ExceptionHandler  
    ResponseEntity<StudentErrorResponse> handleException(StudentNotFoundException studentNotFoundException){  
        StudentErrorResponse studentErrorResponse = new StudentErrorResponse();  
        studentErrorResponse.setStatus(HttpStatus.NOT_FOUND.value());  
        studentErrorResponse.setMessage(studentNotFoundException.getMessage());  
        studentErrorResponse.setTimestamp(System.currentTimeMillis());  
  
        return  new ResponseEntity<StudentErrorResponse>(studentErrorResponse,HttpStatus.NOT_FOUND);  
    }  
  
  
}
```

##### `StudentNotFoundException`
```java
package com.sagnik.restcrud.rest;  
  
public class StudentNotFoundException extends RuntimeException {  
  
    public StudentNotFoundException(String message) {  
        super(message);  
    }  
  
  
    public StudentNotFoundException(String message, Throwable cause) {  
        super(message, cause);  
    }  
  
    public StudentNotFoundException(Throwable cause) {  
        super(cause);  
    }  
  
  
}
```

##### `StudentErrorResponse`
```java
package com.sagnik.restcrud.rest;  
  
public class StudentErrorResponse {  
    private int status;  
    private String message;  
    private long timestamp;  
  
    public StudentErrorResponse(){  
  
    }  
  
    public StudentErrorResponse(int status, String message, long timestamp) {  
        this.status = status;  
        this.message = message;  
        this.timestamp = timestamp;  
    }  
  
    public int getStatus() {  
        return status;  
    }  
  
    public void setStatus(int status) {  
        this.status = status;  
    }  
  
    public String getMessage() {  
        return message;  
    }  
  
    public void setMessage(String message) {  
        this.message = message;  
    }  
  
    public long getTimestamp() {  
        return timestamp;  
    }  
  
    public void setTimestamp(long timestamp) {  
        this.timestamp = timestamp;  
    }  
}
```