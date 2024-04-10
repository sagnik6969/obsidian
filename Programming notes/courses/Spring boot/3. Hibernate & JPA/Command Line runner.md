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
public CommandLineRunner commandLineRunner(){  
    return runner -> {  
    System.out.println("Hello world");  
    };  
}
```