1. they are `php` classes and they represent database tables in laravel. typically each model bound to a single database table.
2. they are defined in `app/models`
3. `php artisan make:model model_name -m` => `-m` flag tells laravel to alse generate a migration file 
4. migrations are stored in `\database\migrations`
5. once you create a model you can use it to interact with the database
6. models use object relational mapping (mapping classes to database tables)
7. if you have a model name `Task` then in the migration file laravel will automatically name the table `tasks` (video no 27)
8. migrations are essentially a version control of the database schema in laravel.
9. it lets you create modify and delete database tables with `php` code. with 