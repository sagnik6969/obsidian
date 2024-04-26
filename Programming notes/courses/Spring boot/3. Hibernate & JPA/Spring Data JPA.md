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
- Spring data JPA provides the interface: JPA repository.
- exposes methods (some by inheritance from parents).
- `findAll()`
- `findById()`
- `save()`
- `deleteById()`
- etc

