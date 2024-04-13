#### Create
```java
@Transactional  
public void save(Student student){  
    entityManager.persist(student);  
}
```
#### Read
```java
@Override  
public Student findById(int id) {  
    return entityManager.find(Student.class,id);  
}
```
> For read operation 