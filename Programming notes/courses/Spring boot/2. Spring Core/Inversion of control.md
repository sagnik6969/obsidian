- The process of outsourcing the construction and management of objects. (like service containers in laravel.)
- https://www.udemy.com/course/spring-hibernate-tutorial/learn/lecture/5165294#announcements
- https://stackoverflow.com/questions/3058/what-is-inversion-of-control
- spring containers are used to inversion of control.
- Spring container works like an object factory. If we ask spring container for a given object, In the background spring will determine which object to create based on the configuration and create and return the object. It works similar to service container in laravel.
- to configure spring container we use java annotations or java source code.

#### Primary functions of spring container
1. Create and manage objects (Inversion of control).
2. Inject the object dependencies. (Dependency Injection).

#### Spring Dependency injection
1. works on dependency inversion principle.
2. The client delegates to another object the responsibility of providing its dependencies.

#### Spring dependency injection types
1. There are multiple injection types available with spring.
2. Constructor injection
3. Setter injection
#### Constructor Injection
1. Use this when you have required dependencies
2. This is recommended by spring.io development team.
#### Setter Injection
1. Use this when you have optional dependencies,
2. If the dependency is not provided Your app can provide reasonable default logic.

#### Spring auto wiring
1. For dependency injection spring can make use of auto wiring.
2. Spring will look for a class that matches (matches by type: class or interface) and inject it automatically
3. This works similar to service container in laravel.

#### Development process: constructor injection
1. Define the dependency interface and class
2. Create demo rest controller.
3. create constructor in your class for injection.
4. add `@GetMapping` for the3 endpoint.
![[Pasted image 20240406184925.png]]
#### `@component` annotation
1. `@Component` marks a class as spring bein.
2. spring bein is a regular java class that is managed by spring.
3. `@Component` also makes the bein available for dependency injection.

![[Pasted image 20240406185352.png]]
![[Pasted image 20240406185422.png]]
- `@AutoWired` annotation tells spring to inject the dependency.
- If you have only one constructor then the `@AutoWired` is optional.
- If there are multiple implementations of `Coach` interface then we need additional configurations to figure out which implementation to use. It will be discussed later.


