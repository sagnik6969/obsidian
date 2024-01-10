1. we can use `dd` inside tests

### Unit Testing
Unit tests are tests that focus on a very small, isolated portion of your code. In fact, most unit tests probably focus on **a single method**. Tests within your "Unit" test directory do not boot your Laravel application and therefore are **unable to access your application's database or other framework services**.

### Feature Tests
Feature tests may test a larger portion of your code, including how several objects interact with each other or even a full HTTP request to a JSON endpoint. **Generally, most of your tests should be feature tests. These types of tests provide the most confidence that your system as a whole is functioning as intended.**

### To run test 
`php artisan test`

### phpunit.xml
All the environment variables are defined in `phpunit.xml`.

### `config:clear`

> make sure to clear your configuration cache using the `config:clear` Artisan command before running your tests!

### To make a feature test
```
php artisan make:test UserTest
```
### To make a unit test
```
php artisan make:test UserTest --unit
```
### To check How much application code is covered by testcases
```
php artisan test --coverage
```
### To check which test cases taking most time
```
php artisan test --profile
```
