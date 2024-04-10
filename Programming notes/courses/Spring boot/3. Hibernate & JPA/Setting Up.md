#### Automatic data source configuration
- In spring boot hibernate is the default implementation of JPA.
- `EntityManager` is main component for creating queries etc.
- `EntityManager` is from JPA.
- Based on configs spring will automatically create  the beans for `EntityManager`, `DataSource` etc.
- You can then inject these in your app.

#### Dependencies for JPA
- MySql driver: mysql-connect