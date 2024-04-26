- spring data rest creates rest end points by adding an *S* at the end of the entity name.
- But it cant handle complex plural forms. Example: person, syllabus
- In this case you need to specify plural name manually.
#### Solution
- Specify plural name with annotation in the repository interface.
```java
@RepositaryRestResource(path="members")
public interface EmployeeRepository extends JpaRepository<Employee,Integer> {  
    // Thats it, no need to write any code  
}
```
#### Pagination
- By default spring data rest will return first 20 elements.
- You can navigate to different pages using query params.
- Example: `/employees?page=0`
#### Spring data rest configurations
- `spring.data.rest.base-path=/api` `=>` Base path to expose repository resources.
- `spring.data.rest.default-page-size=10` `=>` default size of page (In pagination)
- `spring.data.rest.max-page-size` `=>` Maximum size of pages.
#### Sorting
- You can sort by the property name of your entity.
- Example: Sort by last name: `/employees?sort=lastName`
- Sort by first name descending:  `/employees?sort=firstName,desc`
- Sort by first name then last name in descending order `/employees?sort=firstName,lastName,desc`
- 