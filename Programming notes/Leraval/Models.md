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
  
return new class extends Migration {
    /**
     * Run the migrations.
     */
    public function up(): void

    {
        Schema::create('tasks', function (Blueprint $table) {
            // 1st argument is table name
            // 2nde argument is a function which gets $table as an input        

            $table->id();
            //creates an id column with auto increment and primary key
            // laravel's default way of creating id
            $table->timestamps();
            // create 2 columns created_at and updated at which will automatically get updated.
            
            $table->string('title');
            // varchar(255)
            $table->string('description');
            $table->string('long_description')->nullable();
            // by default columns are not nullable
            // to make them nullable use the above syntax.
            $table->boolean('completed')->default(false);
            // tinyint(1)
        });
    }
    /**
     * Reverse the migrations.
     */
    public function down(): void
    {
        Schema::dropIfExists('tasks');
    }
};
```
12. migrations are also stored in migrations table in MySQL. In this way laravel wont apply same migration twice.
13. to rollback the last migration `php artisan migrate:rollback`
14. models are used to add or delete rows in a table.
15. migration are used to create , alter, delete a table.
