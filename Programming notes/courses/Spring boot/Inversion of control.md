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
2. 