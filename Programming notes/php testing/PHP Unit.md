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
2. `array_pop` => removes items from the end of an array
3. `array_shift` => removes the items from the start of the array
4. `$this->expectException(QueueException::class);`
5. `$this->expectExceptionMessage('queue is full');`
6. 
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
```json
  "autoload": {
        "psr-4": {
            "":"src/"
        }
    }
```
=> `psr4` autoloading => namespace is equal to path to the class file from root directory of the project.
=> in the above configuration if the class name is not found composer will look inside the `src/` directory.

```json
"autoload": {
        "psr-4": {
            "App\\": "app/",
            "Database\\Factories\\": "database/factories/",
            "Database\\Seeders\\": "database/seeders/"
        }
    }
```
=> in this example if class's namespace is `App\` then it will look for the class in `app/` and so on.
=> to generate composer autoload file `composer dump-autoload` => the generated file will be responsible for generating the autoloading the classes.
=> for the autoloader to work we need to import it from `vendor/autoload.php`
=> note by default `php unit` will automatically use `vendor/autoload.php` as auto loader.

### Set Up
```php
protected function setUp(): void
    {
        $this->queue = new Queue;
        // this function will run before every test
        // this is called fixture
    }
```
### Tear Down
```php
protected function tearDown(): void
{
  unset($this->queue);
 // this function will run after every test
 // don't need to use
 // only use tearDown method if you are creating lot of objects and need to clear the memory
}
```

### Set Up Before Class
```php
public static function setUpBeforeClass(): void
    {
        // runs before first test is run
        // equivalent to beforeAll in vitest
        // should be public static
    }
```
### Tear Down After Class
```php
 public static function tearDownAfterClass(): void
    {
        // runs after last test is run
        // equivalent to afterAll in vitest
        // should be public static
    }
```

### Testing for exceptions
```php
$this->expectException(QueueException::class);
$this->expectExceptionMessage('queue is full');
// to test for exception. 
$this->queue->push('extra');
```
=> note we need to place the expect exception block before the code which results in exception.
=> to throw an exception `throw new QueueException('queue is full');`

### Mocking
```php
$mailer = $this->createMock(Mailer::class);
//used to create a mock version of the class
// when we create a mock version of the class it inherits all the methods
// and properties => all the methods does not do anything and  return null by default in the mock implementation.

$mailer->method('sendMessage')->willReturn(true);
$result = $mailer->sendMessage('a@b.com', 'Hi');
$this->assertTrue($result);
```
