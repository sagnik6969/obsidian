- Spring security can read user account info from database.
- By default, you have to follow spring securities predefined table schemas.

#### Customize database access with spring security
- Can also customize the table schemas.
- Useful if you have custom tables specific to your project  / custom.
- You will be responsible for developing the code to access the data.
#### Development Process
1. Develop sql script to setup database table for storing user data.
2. Add database support to maven pom file.
3. Create JDBC properties file.
4. Update spring security configuration to use JDBC.
#### Default Spring Security database schema
###### Users
- username `varchar(50)`
- password `varchar(50)`
- enabled `tinyint(1)`
##### authorities
- username `varchar(50)`
- authority `varchar(50)`
