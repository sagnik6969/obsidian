- Using JPA & Hibernate

#### Data access object (DAO)
- It is a common design pattern.
- Used for interacting with the database.
- Simar to models in laravel.
- for example student access will contain the following methods
- `save()`
- `findById()`
- `findAll()`
- `findByLastName()`
- `update()`
- `delete()`
- `deleteAll()`
- DAO needs a `jpa entityManager`.
- JPA Entity manager is the main component for saving and retrieving entities.
- Data access object interacts with the database using the entity manager.
#### JPA entity manager
- Our `jpa` entity manager needs a data source.
- The data source defines database connection info,
- The `jpa` entity manager and the data source is automatically created by spring boot, based on `application.properties` and `pom.xml` file.
- We can auto wire / Inject the JPA entity manager into student data access object.

#### JPA repository
- It is an alternative to `EntityManager`
- We will discuss it later.
- If you need low level control and flexibility use entity manager.
- If you want high level abstraction you can use JPA repository.
- Choice depends on customer requirements and developer preference.
- You can also use both of them in the same project.
- For learning purpose learn entity manager first then learn JPA repository.

#### Development process
1. Define DAO interface
2. Define DAO implementation and Inject the entity manager.
4. Update the main app.
![[Pasted image 20240413140400.png]]
![[Pasted image 20240413140427.png]]

#### `@Transactional` annotation
- If we add transactional annotation before a function, spring automatically begins and ends the transaction for the JPA code inside the function.
![[Pasted image 20240413140853.png]]
#### `@Repositary` annotation
- This is for annotating DAOs.
- This allows spring to automatically register the DAO implementation thanks to component scanning.
- Spring also provides translation to any JDBC related exceptions.
![[Pasted image 20240413141156.png]]
- `@RestController` and `@Repository` are sub annotation of `@Component`
- 

