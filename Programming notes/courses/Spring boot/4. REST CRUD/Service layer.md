- `@Service` is used to define service layer.
- This layer sits between controller and DAO (Data access object).
#### Purpose of service layer
- It follows **Service Facade** design pattern.
- Intermediate layer for custom business logic.
- Integrate data from multiple sources. (DAO / Repositories).

> Spring provides `@service` annotation.
> `@Service`, `@Repositary`, `@RestController` are sub annotations of `@Component`.

#### Development Process
- Define service interface.
- Define service implementation.
- Inject the employee DAO in service implementation.

#### Code

```java

@Service  
public class EmployeeServiceImpl implements EmployeeService{  
  
    private final EmployeeDAO employeeDAO;  
  
    @Autowired  
    public EmployeeServiceImpl(EmployeeDAO employeeDAO){  
        this.employeeDAO = employeeDAO;  
    }  
  
    @Override  
    public List<Employee> findAll() {  
        return employeeDAO.findAll();  
    }  
}
```
