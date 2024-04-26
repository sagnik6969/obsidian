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
###### Student entity
```java
package com.sagnik.cruddemo.entity;  
import jakarta.persistence.*;  
  
@Entity  
@Table(name = "student")  
public class Student {  
    public Student(){  
    }  
  
    public Student(String firstName, String lastName, String email) {  
        this.firstName = firstName;  
        this.lastName = lastName;  
        this.email = email;  
    }  
  
    public int getId() {  
        return id;  
    }  
  
    public void setId(int id) {  
        this.id = id;  
    }  
  
    public String getFirstName() {  
        return firstName;  
    }  
  
    public void setFirstName(String firstName) {  
        this.firstName = firstName;  
    }  
  
    public String getLastName() {  
        return lastName;  
    }  
  
    public void setLastName(String lastName) {  
        this.lastName = lastName;  
    }  
  
    public String getEmail() {  
        return email;  
    }  
  
    public void setEmail(String email) {  
        this.email = email;  
    }  
  
    @Override  
    public String toString() {  
        return "Student{" +  
                "id=" + id +  
                ", firstName='" + firstName + '\'' +  
                ", lastName='" + lastName + '\'' +  
                ", email='" + email + '\'' +  
                '}';  
    }  
  
    @Column(name = "id")  
    @Id  
    @GeneratedValue(strategy = GenerationType.IDENTITY)  
    private int id;  
  
    @Column(name = "first_name")  
    private String firstName;  
  
    @Column(name = "last_name")  
    private  String lastName;  
  
    @Column(name = "email")  
    private  String email;  
  
  
}
```
###### `StudentDAO` interface
```java
package com.sagnik.cruddemo.dao;   
import com.sagnik.cruddemo.entity.Student;  
public interface StudentDAO {  
   public void save(Student student);  
   public Student findById(int id);  
}
```
###### `StudentDAO` implementation
```java
package com.sagnik.cruddemo.dao;  
import com.sagnik.cruddemo.entity.Student;  
import jakarta.persistence.EntityManager;  
import org.springframework.beans.factory.annotation.Autowired;  
import org.springframework.stereotype.Repository;  
import org.springframework.transaction.annotation.Transactional;  
  
@Repository  
public class StudentDAOImpl implements StudentDAO{  
  
    private EntityManager entityManager;  
  
    @Autowired  
    public StudentDAOImpl(EntityManager entityManager){  
        this.entityManager = entityManager;  
    }  
  
    @Override  
    @Transactional    public void save(Student student){  
        entityManager.persist(student);  
    }  
  
    @Override  
    public Student findById(int id) {  
        return entityManager.find(Student.class,id);  
    }  
  
}
```
###### Main application function
```java
package com.sagnik.cruddemo;   
import com.sagnik.cruddemo.dao.StudentDAO;  
import com.sagnik.cruddemo.entity.Student;  
import org.springframework.boot.CommandLineRunner;  
import org.springframework.boot.SpringApplication;  
import org.springframework.boot.autoconfigure.SpringBootApplication;  
import org.springframework.context.annotation.Bean;  
  
@SpringBootApplication  
public class CruddemoApplication {  

    public static void main(String[] args) {  
       SpringApplication.run(CruddemoApplication.class, args);  
    }  
  
    @Bean  
    public CommandLineRunner commandLineRunner(StudentDAO studentDAO){  
       return runner -> {  
       System.out.println("Hello world");  
//     createStudent(studentDAO);  
          readStudent(studentDAO);  
       };  
    }  
  
    private void readStudent(StudentDAO studentDAO) {    
       System.out.println("Creating new student ....");  
       Student student = new Student("Sagnik","Jana","sag@gmail.com");  
       System.out.println("Saving student ....");  
       studentDAO.save(student);  
       System.out.println("saved student with id = " + student.getId());  
       System.out.println("Retrieving the student");  
       Student retrievedStudent = studentDAO.findById(student.getId());  
       System.out.println("Retrieved student details: " + retrievedStudent.toString());  
    }  
  
    private void createStudent(StudentDAO studentDAO) {  
       System.out.println("Creating new student ....");  
       Student student = new Student("Sagnik","Jana","sag@gmail.com");  
       System.out.println("Saving student ....");  
       studentDAO.save(student);  
       System.out.println("saved student with id = " + student.getId());  
    }  
  
}
```

- `entityManager.marge` => can both save and update an entity. if id of the entity is 0 then it will save a new entity else it5 will update the existing entity.
- 

