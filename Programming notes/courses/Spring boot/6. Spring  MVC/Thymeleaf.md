- Works just like `views` in laravel.
- Can do server side rendering.
- We need to to include the dependency in maven pom file.
- `thymeleaf` files are stored in `resources/templates` directory
- templates will have `.html` extension.

#### Maven dependency
```xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-thymeleaf</artifactId>  
</dependency>
``` 
#### Code
###### `controller.java`
```java
@Controller  
public class DemoController {  
  
    @GetMapping("/hello")  
    public String sayHello(Model model){  
  
        //Model: An interface provided by Spring that allows you to pass data to the view.  
        model.addAttribute("theDate",java.time.LocalDateTime.now());  
        return "helloworld";  
        // spring will look for a file called helloworld.html in resources/template directory  
    }  
}
```
###### `helloworld.html`
```html
<!DOCTYPE html>  
<html lang="en" xmlns:th="http://www.w3.org/1999/xhtml">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Document</title>  
</head>  
<body>  
    <h1>        Sagnik  
    </h1>  
<p th:text="'Time in the server is' + ${theDate}"></p>  
</body>  
</html>
```
- Note in `Spring MVC` we use `@Controller` while previously we have used `@RestController`
- The difference is `@RestController` automatically converts the return value of the functions to `json` objects. In other words we cant return a `view` (`Thymeleaf template`) from  `@RestController`.
- Read more here https://www.geeksforgeeks.org/difference-between-controller-and-restcontroller-annotation-in-spring/
- 