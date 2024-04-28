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
#### Step 1: Develop SQL Script To Setup The Database Table
```sql
--  
-- Table structure for table `users`  
--   
CREATE TABLE `users` (  
  `username` varchar(50) NOT NULL,  
  `password` varchar(50) NOT NULL,  
  `enabled` tinyint NOT NULL,  
  PRIMARY KEY (`username`)  
) ENGINE=InnoDB DEFAULT CHARSET=latin1;  
--  
-- Table structure for table `authorities`  
--  
CREATE TABLE `authorities` (  
  `username` varchar(50) NOT NULL,  
  `authority` varchar(50) NOT NULL,  
  UNIQUE KEY `authorities_idx_1` (`username`,`authority`),  
  CONSTRAINT `authorities_ibfk_1` FOREIGN KEY (`username`) REFERENCES `users` (`username`)  
) ENGINE=InnoDB DEFAULT CHARSET=latin1;  
```
#### Step 2: Update Spring security to use JDBC
![[Pasted image 20240428193054.png]]

> Note for the authorities table. Authority should be prefixed with `ROLE_` for example if role name is admin it should be `ROLE_ADMIN`


