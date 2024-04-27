#### Example
1. To fetch an employee or list or employees. `=>` role should be `>=` Employee.
2. To create or update an employee. `=>` role should be `>=` Manager.
3. To delete an employee. `=>` role should be `=` Admin.
#### Restricting Access to Roles
- `requestMatchers(<<http method>>,<<path to match>>).hasRole(<<Authorized roles>>)` 
- 