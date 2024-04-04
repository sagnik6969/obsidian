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
3. 