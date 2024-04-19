- Similar to migrations in laravel.
- Creates a table based on java code with JPA / hibernate annotations. 
- Useful for development and testing.
- JPA / Hibernate will generate the SQL and execute operations in the database.
#### Configuration
- In `application.properties` add `spring.jpa.hibernate.ddl-auto=create` 
- When you run your app, JPA / Hibernate will drop tables and then create them based on JPA / Hibernate annotations in your java code.
- Unlike laravel we don't need to write the migrations separately. Hibernate will generate the SQL query for crating tables based on the `@Entity` classes.
![[Pasted image 20240419215215.png]]
- If you want to create table once and then keep the data, use `update` command.
- It will alter the database schema based on the latest code updates.
- Use `update` only for basic projects.
- Don't do this in production databases because you don't want to drop your production data.
- Instead for production you should have dbas run sql scripts.
#### Use cases
- Automatic table generation is useful for
1. Database integration testing with in-memory databases.
2. Basic small hobby projects.
#### Recommendations
- In general auto generation is not recommended for enterprise / Realtime applications because you can very easily drop production data if you are not careful.
###### SQL scripts are recommended because
- Corporate dbas prefer SQL scripts for governance and code review.
- SQL scripts can be customized and fine tuned for complex database design.
- SQL scripts can be version controlled.
- Can also work with schema migration tools such as liquibase and flyway.
