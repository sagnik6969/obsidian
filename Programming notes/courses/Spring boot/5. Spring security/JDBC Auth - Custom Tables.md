- Custom tables for spring security.
#### Development Process
###### 1. Create our custom table with SQL
###### 2. Update spring security configuration
- Provide query to find user by `username`.
- provide a query to find roles by username.
#### Updated configuration for Custom tables
```java

@Configuration  
public class DemoSecurityConfig {  
  
  
    @Bean  
    public UserDetailsManager userDetailsManager(DataSource dataSource){
      
    JdbcUserDetailsManager jdbcUserDetailsManager = new JdbcUserDetailsManager(dataSource);  
        
    // Define query for retrieve a user by username  
    jdbcUserDetailsManager.setUsersByUsernameQuery(  
                "select user_id, pw, active from members where user_id=?"  
    );  
    
    jdbcUserDetailsManager.setAuthoritiesByUsernameQuery(  
                "select user_id, role from roles where user_id = ?"  
    );  
  
    // Define a query to retrieve the authorities/roles by username  
    return jdbcUserDetailsManager;  
    }  
}
```

#### To log errors in spring security
- By default spring security wont log errors in the console.
- To enable error logging in the console `logging.level.org.springframework.security=debug` in `application.properties.`
