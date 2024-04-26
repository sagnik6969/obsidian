https://stackoverflow.com/questions/62599259/purpose-of-service-interface-class-in-spring-boot

There are a few reasons why you might want to define an interface for a @Service in Spring Boot:

#### Decoupling:  
defining an interface for your service decouples your code from the concrete implementation. This makes it easier to test your code, as you can mock the interface and inject it into your tests. It also makes it easier to change the implementation of your service in the future, without having to change the code that uses it.
#### Testability:
Defining an interface for your service makes it easier to test your code, as you can mock the interface and inject it into your tests. This allows you to test the functionality of your service without having to worry about the underlying implementation.

#### Flexibility:
Defining an interface for your service makes your code more flexible, as you can easily swap out different implementations of the service without having to change the code that uses it. This can be useful for testing, or for switching between different implementations of the service in different environments.
