- By default spring boot reads properties from `application.properties` file.
- You can define any custom properties i this file.
- Your spring boot app can access these using `@Value`
```java
@Value("${spring.application.name}")  
String app_name;
```
