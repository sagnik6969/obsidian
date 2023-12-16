```php
// routes/web.php
use Illuminate\Support\Facades\Route;
Route::get('/', function () {
    return view('welcome');
});
```
1. routing is a process to direct user requests to an action
2. view is a laravel function => going to cover later

```php
Route::get('/', function () {

    return "Main page";

    // Main page is displayed

});
```
3. "Main Page is displayed to the user"

#### Route example
```php
Route::get('/hello', function () {

    return 'hello';

});
```
#### Dynamic routes
```php
Route::get('/greet/{name}', function ($name) {

    return "Hello $name";

});
```
#### Redirecting
```php
Route::get('/hallo', function () {
    return redirect('/hello');
});
```
#### Named routes
```php
Route::get('/hello', function () {

    return 'hello';

})->name('hello');

Route::get('/hellow', function () {

    return redirect()->route('hello');

    //   redirects to the route named hello;

});
```

#### If no other route has been matched
```php
Route::fallback(function () {

    return 'Route not found';

});
```

#### Important points
1. `Route::get` => get is `get` method here
2. `php artisan route:list` => gives a list of all the routes in the application
3. `GET` => fetch data
4. `POST` => store new data
5. `PUT` => modify an existing field
6. `delete` => delete data