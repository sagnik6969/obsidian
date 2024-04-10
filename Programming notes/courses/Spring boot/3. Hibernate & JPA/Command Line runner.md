- `ConnandLineRunner` is hook that allows us to execute code after the spring beans have been loaded into the application context.
#### Lambda expressions (functions) in java
- Similar to lambda expressions in other languages.
- Example 
```java
runner -> {  
     System.out.println("Hello world");  
};
```
#### Command line runner code
```java
@SpringBootApplication  
public class CruddemoApplication {  
  
    public static void main(String[] args) {  
       SpringApplication.run(CruddemoApplication.class, args);  
    }  
  
    @Bean  
    public CommandLineRunner commandLineRunner(){  
       return runner -> {  
       System.out.println("Hello world");  
       };  
    }  
  
}
```
- Code inside the function `commandLineRunner` will be automatically executed after all the beans are loaded into the application context.

#### To turn off the following banner
![[Pasted image 20240410093305.png]]
- add `spring.main.banner-mode=off` to `application.properties`

#### To reduce logging level 
`logging.level.root=warn`


