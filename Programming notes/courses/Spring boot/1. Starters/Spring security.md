1. you may not want to expose all spring boot actuator end points to all user.
2. To protect these endpoints use spring security.
3. `ther /health endpoint will still be exposed` => you can manually disable it.
```xml
<dependency>
   <groupId>org.springframework.boot</groupId> 
   <artifactId>spring-boot-starter-security</artifactId> 
</dependency>
```
4. Now when you access `/actuator/bins` => spring security will prompt you to login.
5. default username is `user`.
6. For the password you have to to look into the console.
7. to override default username and password `spring.security.user.name=sagnik`
8. To override default password `spring.security.user.password=jana`
9. To exclude specific endpoints ``management.endpoints.web.exposure.exclude=health,info`
10. 