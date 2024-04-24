- The convention is to use plural for of the entity name as http endpoint name. Example: `/api/employees`.
- `POST` => create a new entity.
- `GET` => To read a list of entities or a single entity.
- `PUT` => Update an existing entity.
- `DELETE` => delete an existing entity.

#### Example
- `get => /api/employees` => to get a list of employees
- `get => /api/employees/{employeeId}` => To fetch a single employee.
- `post =>  /api/employees` => To create a new employee.
- `put =>  /api/employees/{employeeId}` => To update an existing employee.
- `delete => /api/employees/{employeeId}` => To delete an existing employee.


#### Anti patterns
- These are rest anti patterns / bad practices.
- Don't include action name in the endpoint.
- Example: `api/employList`, `api/deleteEmployee` etc
- instead use `GET => api/employees, delete => api/employees`
