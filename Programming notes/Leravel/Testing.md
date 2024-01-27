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
### Resetting database after each test

`use Illuminate\Foundation\Testing\RefreshDatabase;` => trait
`use RefreshDatabase;`

> note this will remove all the data from database. so make sure to use separate
> database for testing.
>  does not migrate your database if your schema is up to date but clears all the data.

>  Any records added to the database by test cases that do not use this trait may still exist in the database.  

> In each function the database is refreshed
### Sqlite
1. it is a small filesystem based database. 
2. `<env name="DB_DATABASE" value=":memory:"/>` => `:memory:` means database will not be stored in the disk instead it will be stored in the ram temporarily.

> Laravel test functions must start with `test` prefix.

> Each test must not make more than 1 http request

> Unlike cookies the local and session storage items are not sent automatically with request. Session storage data is deleted when browser tab is closed while local storage data persists indefinitely. (Can be deleted manually through javascript). 

### Http tests
1. check my portfolio backend tests

```php
$this->put("/posts/{$post->id}", $params)
```
#### Cookies
```php
$response = $this->withCookies([
'color' => 'blue',
'name' => 'Taylor',
])->get('/');
```
#### Sessions
```php
$this->withSession(['banned' => false])->get('/');

$this->post('/posts', $params)
->assertStatus(302)
->assertSessionHas('status');
$this->assertEquals(session('status'), 'Blog post was created!');

$messages = session('errors')->getMessages();
$this->assertEquals($messages['title'][0], 'The title must be at least 5 characters.');
$this->assertEquals($messages['content'][0], 'The content must be at least 10 characters.');
```
#### Authentication
-> note this method will only work in case of session based authentication. wont work in case of cooky based authentication.
```php
$response = $this->actingAs($user)->get('/')
```
#### database
```php
$this->assertDatabaseHas('blog_posts', [
'title' => 'New title'
]);
$this->assertDatabaseMissing('blog_posts', $post->toArray());
$this->assertSoftDeleted('blog_posts', $post->toArray());
```


