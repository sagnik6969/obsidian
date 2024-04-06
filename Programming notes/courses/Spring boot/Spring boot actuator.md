#### Problem
1. How can I monitor and manage my application.
2. How can I check the application health.
3. How can I access application metrics.

#### Solution
1. Exposes endpoints to monitor and manage your application.
2. You easily get dev DevOps functionality out of the box.
3. Simply add the dependency to your pom file.
4. REST endpoints are automatically added to your endpoint. (by using those end points you can monitor your application.)
```xml
<dependency> 
   <groupId>org.springframework.boot</groupId> 
   <artifactId>spring-boot-starter-actuator</artifactId> 
</dependency>
```
#### Endpoints
1. endpoints are prefixed with `/actuator`
2. `/health` => health information about your application.
3. By default only health endpoint is exposed.
4. The `/info` endpoint can provide information about your application.
5. TO expose info `management.endpoints.web.exposure.include=health`