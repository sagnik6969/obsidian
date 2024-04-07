- By default when your application starts all beans (`@Component` etc) are initialized.
-  Spring will create an instance of each and make them available.
- Instead of creating all beans up front we can specify lazy initialization.
- A bean will only be initialized in the following cases. 
     1. When it is needed for dependency injection.
     2. Or it is explicitly required.
- Add the `@Lazy` annotation to a given class.
- To specify that all beans should be lazy add `spring.main.lazy-initialization=true` to `application.properties` file.
![[Pasted image 20240407085241.png]]
