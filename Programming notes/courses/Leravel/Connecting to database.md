1. write the appropriate database credentials inside `.env` file
2. in `config/database.php` (actual database configuration exists here) these credentials are accessed using `env` function. its first argument is environment variable name. second argument is the default value when environment variable is not found.
3. `php artisan migrate` use to migrate the database for laravel use. if the database name specified in the credentials is not present then a new database with the same name will be created.
