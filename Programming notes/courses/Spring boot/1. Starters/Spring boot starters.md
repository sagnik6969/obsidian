### The problem
1. Building a spring application is really hard.
2. which maven dependencies do I need ? 
3. It would be great if there was a simple list of Maven dependencies collected as a group of dependencies .... one-stop shop.
4. So don't have to search for each dependency.
#### The solution - Spring Boot Starters.
1. A curated list of maven dependencies. 
2. A collection of dependencies grouped together.
3. Tested and verified by the spring development team.
4. Makes it much easier for developers to get started with spring.
```xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-web</artifactId>  
</dependency>
```
5. The above starter contains list of other dependencies.
6. It also makes sure you have compatible versions of all the dependencies.
### Spring Initializer
1. In spring initializer, simply select **Spring web** dependency
2. you will automatically get `spring-boot-starter-web` in `pom.xml`.
![[Pasted image 20240404175417.png]]
### List of all Spring boot starters
https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#using.build-systems.starters

#### How do I know what is inside the starters.
1. Most IDES have a dependency management / View feature. 
2. for `intellij` users open the `external libraries` in sidebar.

#### Spring boot starter parent
1. Spring boot provides `Starter Parent`.
2. This is a special starter that provides Maven defaults.
3. Default compiler level.
4. `UTF-8` source encoding.
5. Others...
6. TO override a default property in parent
![[Pasted image 20240404184626.png]]
7. For `spring-boot-starter-*` dependencies, no need to list versions 
8. the version will automatically get inherited from starter parent.
9. starter parent provides default configuration of spring boot plugin.
### Benefits of the spring boot starter parent
- Default maven configuration: Java version, UTF-encoding etc.
- Dependency management
- Use version on parent only
- `spring-boot-starter-*` dependencies inherit version from parent
- Default configuration of spring boot plugin.
-  