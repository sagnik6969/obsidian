#### My Wish
I wish I could tell spring: Create a rest API for me 
1. Use my existing JPA repository
2. and give me all the rest api crud features for free.
#### Spring data rest is the solution
- Leverages your existing JPA repository.
- Spring will give you rest crud implementation for free.
- Helps to minimize boiler plate rest code.
- Spring data rest will expose crud end points for free.
#### Spring data rest : How it works
- Spring data rest will scan your project for `JpaRepository`
- Expose REST APIs for each entity type for your JPA repository.
#### Rest end points
- Dy default spring data rest will create end points based on entity type.
- Simple pluralized form.
- For example for entity `Employee` the rest endpoints will be `get => /employees` etc.
#### Development process
1. Add `spring-boot-starter-data-rest` to your maven pom file
2. And that's it! No need for additional coding.
3. `spring-data-rest` will scan JPA repositories and expose the endpoints for free.

#### Summery
For spring data rest you need only 3 items
1. Your entity: `Employee`
2. JPA repository: `EmployeeRepository extends JpaRepository<Employee,Integer>`
3. Maven POM dependency for `spring-boot-starter-data-rest` 