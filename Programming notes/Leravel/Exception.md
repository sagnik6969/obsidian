1. To make a custom exception `php artisan make:exception UserNotFoundException --render`
2. render method returns an array which is used to convert the exception to a http response.
3. in case of model relations if `()` is used then we can apply additional queries if `()` is not used then it fetches data directly.