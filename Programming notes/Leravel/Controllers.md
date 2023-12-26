instead of keeping all the logics in `web.php` in bigger laravel applications logic is kept at classes called controllers.

- To make a controller: `php artisan make:controller controller_name`
- controllers are located inside `app/http/controllers`
- define the actions (methods) inside controllers
- you can call these actions from the `web.php`
- laravel works on `mvc` pattern. 
- m => model => to handle data
- v => view => to handle user interface
- c => controller => to handle logic => responsible for gluing together models and views to produce final output.
- to make a resource controller `--resource` resource controllers are the controllers which has some predefined set of actions. Example
![[Pasted image 20231226105648.png]]
- Resource controller will automatically implement these methods