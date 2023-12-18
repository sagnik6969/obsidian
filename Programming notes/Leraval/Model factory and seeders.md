1. `factories` provide fake data for the a model
2. `seeders`loads the fake data in the database.
3. factories and seeders can be found inside `database` folder
4. `php artisan db:seed` => to store the fake records in the database.
5. To create a new factory `php artisan make:factory TaskFactory --model=Task`