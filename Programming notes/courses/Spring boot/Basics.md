1. in spring also there are controllers
2. syntax = 
```java
@RestController  
public class FunRestController {  
    @GetMapping("/")  
    public String hello(){  
        return  "Hello World";  
    }  
}
```
3. `spring projects` => additional spring modules built on top of spring framework. for example 
4. `spring security` => for security services.
5. https://spring.io/projects

#### Maven
- maven is a project management tool for your application
- Most popular use of maven is for `build management` and `dependencies`
#### What problems does maven solve ?
when building your java project you may need additional jar files for example: Spring, Hibernate, JSON etc. One approach is to download those jar files manually and manually add then to your build path / class path.
Other approach is to use maven. Tell maven the projects you are working with (dependencies)(For example spring hibernate etc.) Maven will go out and download JAR files for those projects for you.  And maven will make those jar files available during compilation and run. 
#### How maven works ?
- maven reads the project configuration file (similar to `package.json` in `nodejs`) . Then maven will check maven local repo in your computer (maven cache) to look for the required package. If the package is not available locally maven will go to internet and download those dependencies (`jar` files). And finally maven will save them to local repository (local cache). Maven will use these to build and run our project
#### Building and Running
- when you build and run your app maven will handle class / build path for you. 
- Based on config file, Maven will add JAR files accordingly.

#### Standard directory structure in maven
- Normally when you join a new project Each development team dreams up their own directory structure. Not ideal for new comers and not standardized.
- Maven solves this problem by providing standard directory structure.
- 