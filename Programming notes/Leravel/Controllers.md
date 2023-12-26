instead of keeping all the logics in `web.php` in bigger laravel applications logic is kept at classes called controllers.

- To make a controller: `php artisan make:controller controller_name`
- controllers are located inside `app/http/controllers`
- define the actions (methods) inside controllers
- you can call these actions from the `web.php`
- laravel works on `mvc` pattern. 
- m => model => to handle data
- view => to handle 