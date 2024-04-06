- By default spring boot reads properties from `application.properties` file.
- You can define any custom properties i this file.
- Your spring boot app can access these using `@Value`
```java
@Value("${spring.application.name}")  
String app_name;
```
- deferent options of spring boot (example: port number) is configured in `application.properties`
- list of all properties https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html
- 