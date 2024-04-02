1. Spring boot makes use of standard maven directory structure.
2. `mvnw` =>allows you to run a maven project. No need to have Maven installed or present on your path. If correct version of maven is not found on your computer. Automatically download correct version and runs maven.
3. `mvnw.cmd` => for windows
4. `mvnw.sh` => for Linux/Mac
5. to run a maven project `mvn clean compile test` => if maven is installed in your system else `./mvnw.cmd clean compile test`.
6. `pom.xml` => includes info that you entered at spring initializer website.
7. `spring-boot-starter-web` => spring boot starters are a collection of maven dependencies. for example `spring-boot-starter-web`  consists of `spring-web`, `spring-webmvc`, `tomcat` etc) => it saves the developer from having to list all of the individual dependencies.
![[Pasted image 20240402223945.png]]

