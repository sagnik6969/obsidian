#### Controller
```java
@Controller  
public class HelloWorldController {  
  
  
    @RequestMapping("/showForm")  
    public String showForm(){  
        return "helloworld-form";  
    }  
  
    @RequestMapping("/processForm")  
    public  String processForm(){  
        return  "helloworld2";  
    }  
}
```
#### `helloworld-form.html`
```html
<form th:action="@{/processForm}" method="GET">  
    <input type="text" name="studentName" placeholder="Whats your name" />  
    <input type="submit" />  
</form>  
```

#### `Helloworld2.html`
```html
<p th:text="'Hello ' + ${param.studentName}"></p>  
```
