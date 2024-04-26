```java
@RestController  
@RequestMapping("/api")  
public class EmployeeRestController {  
    private final EmployeeService employeeService;  
    @Autowired  
    public EmployeeRestController(EmployeeService employeeService){  
        this.employeeService = employeeService;  
    }  
  
    @GetMapping("/employees")  
    public List<Employee> findAll(){  
        return employeeService.findAll();  
    }  
  
    @GetMapping("/employees/{employeeId}")  
    public Employee findOne(@PathVariable int employeeId){  
        Employee employee = employeeService.findById(employeeId);  
        if(employee == null){  
            throw new RuntimeException("Employee id not found - " + employeeId);  
        }  
        return employee;  
    }  
  
    @PostMapping("/employees")  
    public Employee addEmployee(@RequestBody Employee employee){  
        employee.setId(0);  
        return employeeService.save(employee);  
    }  
  
    @PutMapping("/employees")  
    public Employee updateEmployee(@RequestBody Employee employee){  
        return employeeService.save(employee);  
    }  
  
    @DeleteMapping("/employees/{employeeId}")  
    public String deleteEmployee(@PathVariable int employeeId){  
        Employee employee = employeeService.findById(employeeId);  
        if(employee == null){  
            throw new RuntimeException("Employee id not found - " + employeeId);  
        }  
        employeeService.deleteById(employeeId);  
        return "Employee deleted successfully - " + employeeId;  
    }  
  
}
```

