#### Example
1. To fetch an employee or list or employees. `=>` role should be `>=` Employee.
2. To create or update an employee. `=>` role should be `>=` Manager.
3. To delete an employee. `=>` role should be `=` Admin.
#### Restricting Access to Roles
- `requestMatchers(<<http method>>,<<path to match>>).hasRole(<<Authorized roles>>)` 
#### Cross site request forgery (CSRF)
- Spring security can protect against CSRF attacks.
- Embed additional authentication data / token into all HTML forms.
- On subsequent requests the web app will verify token before processing.
- Primary use case is traditional web applications. (HTML forms etc)
#### When to use CSRF protection
- The spring security team recommends
      - Use CSRF protections for any browser web requests.
      - Traditional web apps with HTML forms to add / modify data.

   
