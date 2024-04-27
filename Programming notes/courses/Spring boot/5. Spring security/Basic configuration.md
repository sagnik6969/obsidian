#### Our users

| User Id | password | Role                     |
| ------- | -------- | ------------------------ |
| john    | test123  | Employee                 |
| mary    | test123  | Employee, Manager        |
| susan   | test123  | Employee, Manager, Admin |
#### Development process
1. Create a spring security configuration class. (`@Configuration`)
2. Add user, passwords and roles
#### Create Spring Security Configuration
```java
@Configuration
public class DemoSecurityConfig {
 // Add our security configuration here
}
```
#### Spring security password storage:
- In spring security passwords are stored using specific format.
- `id{encodedPassword}`
- 

