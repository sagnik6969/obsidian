### configuration
1. install => `composer require phpunit/phpunit`
2. to run a test file `./vendor/bin/phpunit <path_to_file>`
3. to run tests in test directory => `./vendor/bin/phpunit ./tests`
4. the test file names must end with Test
5. the test cases inside the test file should start with keyword `test`
6. the test class must extend `PHPUnit\Framework\TestCase`

### Assert
1. `$this->assertEquals(4, 2 + 2);`
2. the goal of unit testing is to isolate each part of program and check each part of the program works as expected.
3. 