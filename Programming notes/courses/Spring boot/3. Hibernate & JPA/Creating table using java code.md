- Similar to migrations in laravel.
- Creates a table based on java code with JPA / hibernate annotations. 
- Useful for development and testing.
- JPA / Hibernate will generate the SQL and execute operations in the database.
#### Configuration
- In `application.properties` add `spring.jpa.hibernate.ddl-auto=create` 
- When you run 