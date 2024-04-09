#### Hibernate
- it is a framework for saving java objects in database.
- It provides object relational mapping
- It works similar to models in laravel.
- A java class is mapped to a given database table

#### JPA
- Jakarta Persistence API
- Standard api for ORM.
- It provides only specifications.
- Defines a set of interfaces
- Hibernate is an implementation of `JPA Spec`

#### Benefits of JPA
- By having a standard api you are not locked to vendors implementation.
- Maintain portable and flexible code by coding to JPA spec.
- Can theoretically switch vendor implementations.
- For example if vendor `ABC` stops supporting their product you can switch to vendor `xyz` without vendor lock in.
![[Pasted image 20240409235153.png]]
![[Pasted image 20240409235329.png]]
![[Pasted image 20240409235447.png]]

#### How Hibernate / JPA related to JDBC
- Hibernate / JPA uses `jdbc` for all database communication.
- 
