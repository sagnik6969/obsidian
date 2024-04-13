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
- Data access objct 
