### configuration
1. install => `composer require phpunit/phpunit`
2. to run a test file `./vendor/bin/phpunit <path_to_file>`
3. to run tests in test directory => `./vendor/bin/phpunit ./tests`
4. `./vendor/bin/phpunit ./path_to_file  --filter=functionName` => to only run a specific test in a file.
5. the test file names must end with Test
6. the test cases inside the test file should start with keyword `test`
7. the test class must extend `PHPUnit\Framework\TestCase`
8. the goal of unit testing is to isolate each part of program and check each part of the program works as expected.
9. make the test method names as descriptive as possible.
10. 

### Assert
1. `$this->assertEquals(4, 2 + 2);`

### phpunit.xml
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<phpunit colors="true">
    <testsuites>
        <testsuite name="Test Suite">
            <directory>tests</directory>
        </testsuite>
    </testsuites>
</phpunit>
```
### Example

```php
<?php
use PHPUnit\Framework\TestCase;
require 'User.php';
class UserTest extends TestCase
{
    public function testReturnsCorrectFullName()
    {
        $user = new User();
        $user->first_name = "a";
        $user->last_name = "b";
        $this->assertEquals($user->fullName(), "a b");
    }

    public function testFUllNameIsEmptyByDefault()
    {
        $user = new User();
        $this->assertEquals($user->fullName(), "");
    }
}
```
### Autoloading
```php
  "autoload": {
        "psr-4": {
            "":"src/"
        }
    }
```
=> `psr4` autoloading => namespace is equal to path to the class file from root directory of the project.


1. 