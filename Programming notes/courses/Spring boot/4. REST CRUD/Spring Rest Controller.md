```java
@RestController
@RequestMapping('/test) // all the http endpoints in this class will be prefixed with "/test"
public class DemoController {
    @GetMapping("hello")
    public String sayHello(){
        return "Hello world"
    }
}
```