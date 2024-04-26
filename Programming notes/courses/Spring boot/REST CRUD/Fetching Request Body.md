```java
@PostMapping("/employees")  
public Employee addEmployee(@RequestBody Employee employee){  
    employee.setId(0);  
    return employeeService.save(employee);  
}
```
