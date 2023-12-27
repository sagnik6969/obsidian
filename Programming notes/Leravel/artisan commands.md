1. `php artisan serve` => starts the server
2.  run `php artisan migrate` command to apply the migration to the database 
3. `php artisan db:seed` => to store the fake records in the database.
4. `php artisan migrate:refresh --seed` to recreate the migrations along with seeding we need to write
5. To create a new factory `php artisan make:factory TaskFactory --model=Task`
6. to recreate the migrations along with seeding we need to write `php artisan migrate:refresh --seed`
7. `php artisan make:model model_name -m` => `-m` flag tells laravel to also generate a migration file
8. to rollback the last migration `php artisan migrate:rollback`
9. `php artisan route:list` => gives a list of all the routes in the application
10. `php artisan tinker` => command line interface for laravel application => we can write queries in oop way
11. `php artisan make:request request_name` =>to create a from request file. Form request are extracting the form validation rules to one place. 
12. `php artisan make:component StarRating` => to make a star rating component.
13. 

