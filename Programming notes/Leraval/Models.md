1. they are `php` classes and they represent database tables in laravel. typically each model bound to a single database table.
2. they are defined in `app/models`
3. `php artisan make:model model_name -m` => `-m` flag tells laravel to alse generate a migration file 
4. migrations are stored in `\database\migrations`
5. once you create a model you can use it to interact with the database
6. models use object relational mapping (mapping classes to database tables)
7. if you have a model name `Task` then in the migration file laravel will automatically name the table `tasks` (video no 27)
8. migrations are essentially a version control of the database schema in laravel.
9. it lets you create modify and delete database tables with `php` code. without writing `sql` code.
10. laravel migrations has 2 methods `up()` => responsible for going forward. and `down()` => responsible for going backsword.
11. run `php artisan migrate` command to apply the migration to the database 
```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration

{
    public function up(): void

    {

        Schema::create('tasks', function (Blueprint $table) {
        
            $table->id();
            $table->timestamps();
        });
    }

    public function down(): void
    {
        Schema::dropIfExists('tasks');
    }
};
```
12. migrations are also stored in migrations table in MySQL. In this way laravel wont apply same migration twice.
13. to rollback the last migration `php artisan migrate:rollback`