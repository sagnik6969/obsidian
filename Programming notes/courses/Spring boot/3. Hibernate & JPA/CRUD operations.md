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
> For read operation we don't need `@Transactional` annotation. Because we are not performing any create / update operation in the database.


#### Full Coding
###### 