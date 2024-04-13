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
- 