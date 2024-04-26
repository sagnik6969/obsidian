```java
@GetMapping("/students/{studentId}")  
int getStudent(@PathVariable int studentId){  
    return studentId;  
}
```

- By default the parameter in the `@GetMapping` and input param name in the function must match up.
