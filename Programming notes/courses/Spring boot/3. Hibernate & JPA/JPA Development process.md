#### To do list
1. Annotate the java class 
2. Develop java code to perform database operations.

- Hibernate is the default JPA implementation of spring boot.
- In the following notes we are going to say `jpa` instead of saying `jpa hibernate`.

#### Terminology
1. Entity class: a java class which is mapped to a database table. (similar to a model class in laravel).
2. Object Relational Mapping (ORM): Mapping a java class to a database table. Similar to laravel.

#### Entity Class:
1. Must be annotated by `@Entity`.
2. Must have a public or protected no argument constructor.
3. The class can have other constructors.
4. If you don't declare a constructor you will get a no argument constructor for free.
5. However If you declare a constructor with arguments you wont get a no argument constructor for free