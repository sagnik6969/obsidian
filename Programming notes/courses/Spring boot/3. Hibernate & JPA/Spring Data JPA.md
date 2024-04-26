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
