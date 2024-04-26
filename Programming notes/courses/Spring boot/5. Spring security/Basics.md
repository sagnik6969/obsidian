1. Works similar to auth middleware in laravel.
#### Authentication
- Check user id and password with credentials stored in DB.
#### Authorization
- Check to see if user has an authorized role.
- Example: Admin.
#### Declarative Security
- Define applications security constraints in configurations.
- All java config: `@Configuration`
- Advantage of this is that provides separation of concerns between application code and security.
#### Programmatic security
- Spring security provides an api for custom application coding. 
- Provides greater customization for specific app requirements.

#### Enable spring Security
1. Edit `pom.xml` file and add `spring-boot-starter-security`.
2. This will automatically secure all endpoints of the application.
3. Now when y6ou access your application spring security will prompt you to log in.
4. Default username is `user`
5. Default password is printed in the application logs.
6. 

