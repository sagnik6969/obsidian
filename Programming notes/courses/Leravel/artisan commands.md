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
13. `php artisan cache:clear` => to clear cache
14. `php artisan make:controller Api/AttendeeController --api` => to make a controller for api s.
15. `php artisan make:seeder AttendeeSeeder` => to make a seeder
16. `php artisan make:resource AttendeeResource` => to make a resource => converts model to json for api response.
17. `php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider` => for publishing (copying some code from vendor to codebase).
18. To create a policy `php artisan make:policy EventPolicy --model=Event`
19. To make a custom artisan command `php artisan make:command SendEventReminder`
20. To run the scheduled tasks (in kernal.php) `php artisan schedule:work`
21. `php artisan make:notification EventReminderNotification` => to make a notification.
22. to run queue `php artisan queue:work`
23. To create a livewire component `php artisan make:livewire CreatePoll`
24. `php artisan make:model Job -mf` => to create a Model with migration and factory.
25. `php artisan make:component Layout --view` to create a blade component without corresponding `php` class.
26. `php artisan db:wipe` => to delete all the tables in the database
27. `php artisan make:controller asdf --resource` => to make a resource controller
28. auth controller is also a resource controller.
29. `php artisan make:middlewire abcdnjh` => to make a middleware

