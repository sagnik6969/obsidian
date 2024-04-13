#### Create
```java
@Transactional  
public void save(Student student){  
    entityManager.persist(student);  
}
```
#### Read
