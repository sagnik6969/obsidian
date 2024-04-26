#### Why spring data JPA
- We already saw how to create a DAO.
- What if we need to create DAO for multiple entities.
- Every DAO will have some common methods like `findBYId`,`findAll`
- If we follow standard DAO procedure then there will be a lot of code repetitions.
#### My Wish
I wish we could tell spring 
     - Create a DAO for me
     - Plugin my entity type and primary key.
     - Give me all the basic crud features for free.

#### Spring data JPA is the solution
- Create a DAO and just plugin your entity type and primary key.
- and spring will give you a crud implementation for free.
- This helps to minimize boiler plate code.
#### JPA repository
- Spring data JPA provides the interface: `JPA repository`.
- exposes methods (some by inheritance from parents).
- `findAll()`
- `findById()`
- `save()`
- `deleteById()`
- etc
#### Development process
1. Extent JPA repository interface.
2. Use your repository in your app.
3. No need for an implementation class.
![[Pasted image 20240426104848.png]]
#### All methods in JPA repository
https://docs.spring.io/spring-data/jpa/docs/current/api/org/springframework/data/jpa/repository/JpaRepository.html

#### Advanced Features
Spring data JPA also has some advanced features like
- Extending and adding custom queries with JPQL.
- Query domain specific language (QDSL)
- Defining custom methods (Low level coding)

#### Coding
```java
public interface EmployeeRepository extends JpaRepository<Employee,Integer> {  
    // THats it, no need to write any code  
}
```

> Spring data jpa provides `@Transactional` annotations automatically. So we don't need to write it separately. 
