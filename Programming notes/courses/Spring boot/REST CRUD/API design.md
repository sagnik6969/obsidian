- The convention is to use plural for of the entity name as http endpoint name. Example: `/api/employees`.
- `POST` => create a new entity.
- `GET` => To read a list of entities or a single entity.
- `PUT` => Update an existing entity.
- `DELETE` => delete an existing entity.

#### Anti patterns
- These are rest anti patterns / bad practices.
- Don't include action name in the endpoint.
- Example: `api/employList`, `api/deleteEmployee` etc
- instead use `GET to => api/employees, delete to => api/employees`
