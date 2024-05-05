#### Our users

| User Id | password | Role                     |
| ------- | -------- | ------------------------ |
| john    | test123  | Employee                 |
| mary    | test123  | Employee, Manager        |
| susan   | test123  | Employee, Manager, Admin |

#### Development process
1. Create a spring security configuration class. (`@Configuration`)
2. Add user, passwords and roles
3. Remember `@Configuration` was also discussed in dependency injection.
#### 1. Create Spring Security Configuration
```java
@Configuration
public class DemoSecurityConfig {
 // Add our security configuration here
}
```
#### Spring security password storage:
- In spring security passwords are stored using specific format.
- `{id}encodedPassword`
- id stores hashing algorithm used for password.

| id     | Description               |
| ------ | ------------------------- |
| noop   | Plain text passwords.     |
| bcrypt | one way hashing algorithm |
- Example: `{noop}test123`


#### 2. Add users passwords and roles
```java  
@Configuration  
public class DemoSecurityConfig {  
    @Bean  
    public InMemoryUserDetailsManager inMemoryUserDetailsManager(){  
        UserDetails john = User  
                .builder()  
                .username("john")  
                .password("{noop}test123")  
                .roles("EMPLOYEE")  
                .build();  
  
        UserDetails mary = User  
                .builder()  
                .username("mary")  
                .password("{noop}test123")  
                .roles("EMPLOYEE","MANAGER")  
                .build();  
          
        UserDetails susan = User  
                .builder()  
                .username("susan")  
                .password("{noop}test123")  
                .roles("EMPLOYEE","MANAGER","ADMIN")  
                .build();  
  
        return new InMemoryUserDetailsManager(john,mary,susan);  
  
    }  
  
  
}
```
> When you add `@Configuration` for spring security spring will ignore default username and password in `application.properties`
#### Postman
- In authentication tab select basic security
- and then type username and password.

