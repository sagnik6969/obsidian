#### Example
1. To fetch an employee or list or employees. `=>` role should be `>=` Employee.
2. To create or update an employee. `=>` role should be `>=` Manager.
3. To delete an employee. `=>` role should be `=` Admin.
#### Restricting Access to Roles
- `requestMatchers(<<http method>>,<<path to match>>).hasRole(<<Authorized roles>>)` 
#### Cross site request forgery (CSRF)
- Spring security can protect against CSRF attacks.
- Embed additional authentication data / token into all HTML forms.
- On subsequent requests the web app will verify token before processing.
- Primary use case is traditional web applications. (HTML forms etc)
#### When to use CSRF protection
- The spring security team recommends
      - Use CSRF protections for any browser web requests.
      - Traditional web apps with HTML forms to add / modify data.
  - If you are building a rest api for non browser clients you want to disable CSRF protection.
  - In general CSRF is not required for stateless rest `api`s that use that use POST, PUT, DELETE or PATCH.

#### Coding
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
  
    @Bean  
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {  
        http.authorizeHttpRequests(  
                configurer ->  configurer  
                .requestMatchers(HttpMethod.GET,"/api/employees").hasRole("EMPLOYEE")  
                .requestMatchers(HttpMethod.GET,"/api/employees/**").hasRole("EMPLOYEE")  
                .requestMatchers(HttpMethod.POST,"/api/employees").hasRole("MANAGER")  
                .requestMatchers(HttpMethod.PUT,"/api/employees").hasRole("MANAGER")                           .requestMatchers(HttpMethod.DELETE,"/api/employees/**").hasRole("ADMIN")  
        );  
  
        // Tell spring security that we are using basic authentication  
        http.httpBasic(Customizer.withDefaults());  
  
        //Disable CSRF  
        http.csrf(csrf -> csrf.disable());  
  
        return http.build();  
  
  
    }  
  
}
```


   
