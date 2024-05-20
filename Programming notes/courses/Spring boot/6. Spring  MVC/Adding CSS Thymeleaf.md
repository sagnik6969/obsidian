- By default spring will look for static resources in the directory `/src/main/resources/static`
- Spring boot will search the following directories for static resources under `/resources`
- `/META-INF/resources`
- `/resources`
- `/static`
- `/public`
- Spring boot will search them in top to down manner.

```html
<!DOCTYPE html>  
<html lang="en" xmlns:th="http://www.thymeleaf.org">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Document</title>  
     <!-- Adding CSS to thymeleaf template -->
    <link rel="stylesheet" th:href="@{/css/demo.css}">  
</head>  
<body>  
<p th:text="'Time in the server is' + ${theDate}" class="funny"></p>  
</body>  
</html>
```
- `@` in file path references application root.
#### Adding custom CSS libraries
- Added in same way as in normal html.
- 