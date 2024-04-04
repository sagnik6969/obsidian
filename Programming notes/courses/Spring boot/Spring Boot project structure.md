1. Spring boot makes use of standard maven directory structure.
2. `mvnw` =>allows you to run a maven project. No need to have Maven installed or present on your path. If correct version of maven is not found on your computer. Automatically download correct version and runs maven.
3. `mvnw.cmd` => for windows
4. `mvnw.sh` => for Linux/Mac
5. to run a maven project `mvn clean compile test` => if maven is installed in your system else `./mvnw.cmd clean compile test`.
6. `pom.xml` => includes info that you entered at spring initializer website.
7. `spring-boot-starter-web` => spring boot starters are a collection of maven dependencies. for example `spring-boot-starter-web`  consists of `spring-web`, `spring-webmvc`, `tomcat` etc) => it saves the developer from having to list all of the individual dependencies.
![[Pasted image 20240402223945.png]]
### Application Properties
1. By default spring boot load properties from a file called `application.properties`
2. to change server port add `server.port = 8080` to `application.properties`
3. To use application properties defined in  `application.properties`
![[Pasted image 20240404172349.png]]
### Static
1. By default spring boot will load static resources (`HTML`,`CSS`,`JS`,`Images`) from `/static` directory.

> Do not use `/src/main/webapp` directory if you are going to package your app in `jar`. It will only work in `war`.

![[Pasted image 20240404173442.png]]
