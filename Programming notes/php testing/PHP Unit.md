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
6. `$this->assertNotEmpty()`
7. `$thts->assertEmpty()`
8. `$this->assertIsInt()`
9. ` $this->assertStringStartsWith('example', $result);`
10. `$this->assertIsString($result);`

###### assert Equals vs assert Same
1. `assertEquals` => equivalent to `(==)` in `js`
2. `assertSame` => does strict comparison. => equivalent to `(===)` in `js`
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
##### Passing the mock through dependency injection
```php
public function test_notification_is_sent()
    {
        $user = new User();
        $mockMailer = $this->createMock(Mailer::class);
        $mockMailer->method('sendMessage')->willReturn(true);
        $user->setMailer($mockMailer);
        $result = $user->notify('Hi');
        $this->assertTrue($result);
    }
```

##### Assertion on the mock function
```php
$mockMailer
->expects($this->once())
// expects($this->once()) => tels that sendMessage method must be called once
->method('sendMessage')
->with($this->equalTo('a@b.com'), $this->equalTo('Hi'))
// with verifies the method arguments.
->willReturn(true);
```
##### To throw an exception inside mock function
1. `$mockMailer->method('sendMessage')->will($this->throwException(new Exception));`
##### Get mock Builder
```php
 $mockMailer = $this->getMockBuilder('Mailer')
            ->onlyMethods([])
            ->getMock();
// if we want to mock some of the methods  while keeping others as it is use getMockBuilder
->onlyMethods([]) => the methods specified here will only be mocked rest will remain as it is in the original class
// at last we need to call ->getMock() to get the mock implementation.
```

##### Mockery
1.  to install mockery => `composer require mockery/mockery --dev`
2. to use mockery either we can extend `Mockery\Adapter\Phpunit\MockeryTestCase class`  or we can call `Mockery::close()` in `tearDown()` method;
3. To create a mock object of a non existent class.
```php
       $gateway = Mockery::mock('PaymentGateway');
       $gateway->shouldReceive('charge') // method name is 'charge'
               ->once() // the method will be called once
               ->with(200) // with the argument 200
               ->andReturn(true); // the method should return true;
```

##### Returning different values on subsequent method calls
###### Using PHPUNIT create Mock
```php
public function test_correct_average_is_returned()
    {
        $service = $this->createMock(TemperatureService::class);
        $map = [
            ['12:00', 20],
            ['14:00', 26],
        ];
        $service
            ->expects($this->exactly(2)) // will be called twice
            ->method('getTemperature')
            ->willReturnMap($map);
        $weather = new WeatherMonitor($service);
        $this->assertEquals(23, $weather->getAverageTemperature('12:00', '14:00'));
    }
```
###### Using Mockery
```php
 public function test_correct_average_is_returned_mockery()
    {
        $service = Mockery::mock(TemperatureService::class);
        $service->shouldReceive('getTemperature')
        ->once()
        ->with("12:00")
        ->andReturn(20);
        $service->shouldReceive('getTemperature')
        ->once()
        ->with("14:00")
        ->andReturn(26);
        $map = [
            ['12:00', 20],
            ['14:00', 26],
        ];

        $weather = new WeatherMonitor($service);
        $this->assertEquals(23, $weather->getAverageTemperature('12:00', '14:00'));
    }
```
###### Mockery spies => make assertions after tests
```php
public function test_order_is_processed_using_spy()
    {
        $order = new Order2(3, 1.99);
        $this->assertEquals(5.97, $order->amount);

        $gatewayMock = Mockery::spy('PaymentGateway');
        $order->process($gatewayMock);

        $gatewayMock->shouldHaveReceived('charge')
            ->once()
            ->with(5.97);
        
    }
```
=> with spies you cant specify a return value.

#### To Test protected methods
> Create a dummy child class for the class under test. In the child class create a public function and return the protected method/property of the parent class.

#### To test private methods with `php` reflectors
1. Reflectors allow us to reverse engineer classes
2. Example: 
```php
  $item = new Item;
  $reflector = new ReflectionClass(Item::class);
  $method = $reflector->getMethod('getToken');
  $result = $method->invoke($item);
  $this->assertIsString($result);
```
3. To pass arguments to a reflected method. `$result = $method->invokeArgs($item, ['example']);`
4. private method are part of internal implementation of the class and should not be tested.

#### Test private and protected properties with `php` reflectors
```php
$product = new Product;
$reflector = new ReflectionClass(Product::class);
$property = $reflector->getProperty('product_id');
$property->setAccessible(true);
$this->assertIsInt($property->getValue($product));
```
#### Testing abstract classes
1. abstract class in `php` can contain concrete methods
2. 1 way is to create a concrete class by inheriting the abstract class and test the child concrete class
3. 2nd way is to use mock builder
```php
  $mock = $this
            ->getMockBuilder(AbstractPerson::class)
            ->setConstructorArgs(['Green']) // for setting constructor args
            ->getMockForAbstractClass();
  
            // by default only abstract methods will be mocked
            // concrete methods wont be mocked.

   $mock->method('getTitle')->willReturn('Dr.');
   $this->assertEquals('Dr. Green', $mock->getNameAndTitle());
```

#### Test Driven Development
> With test driven development we write tests first. the test will fail initially. Then we write code to pass the tests.
> At first we try to write a bare minimum code to pass the tests. then we try to improuve the code without breaking the tests.

#### PHP Functions
1. `str_replace(' ', '_', $slug);` => replaces blank with under score.
2. `preg_replace('/\s+|[^\w]+/', '_', $slug)` => replace the substring whic