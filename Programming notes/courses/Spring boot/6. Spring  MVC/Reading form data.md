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

#### Reading Form data inside Controller & adding data to model
#### Controller
```java
@RequestMapping("/processFormVersion2")  
public  String processFormVersion2(HttpServletRequest request, Model model){  
    // HttpServletRequest request => used to read form request data inside controller  
    // model is initially empty => we can add data inside it so    
    // that they can be accessed inside view template  
    String studentName = request.getParameter("studentName");  
    studentName = studentName.toUpperCase();  
  
    String result = "Yo! " + studentName;  
    model.addAttribute("message",result);  
  
    return  "helloworld2";  
}
```
#### View
```html
<p th:text="'message = ' + ${message}"></p>
```


