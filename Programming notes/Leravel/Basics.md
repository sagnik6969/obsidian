1. Composer => used to create a `php` project and manage dependencies
2. to create a `laravel` project `composer create-project laravel/laravel example-app`
### Folders
#### APP:
1. app => contains main logic of the project
2. `laraval` use a auto loading standard called `psr-4`
```php
namespace App\Http\Controllers;

use Illuminate\Foundation\Auth\Access\AuthorizesRequests;

use Illuminate\Foundation\Validation\ValidatesRequests;

use Illuminate\Routing\Controller as BaseController;
```

3. `namespace`  => define name of current script => path to parent directory
4. `use` => import file from other namespaces.
5. We map name spaces to directories in composer.json
```php
"autoload": {

        "psr-4": {

            "App\\": "app/",

            "Database\\Factories\\": "database/factories/",

            "Database\\Seeders\\": "database/seeders/"

        }
```
6. App namespace prefix is mapped to app directory
#### bootstrap:
1. It contains some cash files that laravel automatically generates.
2. no need to know
#### Config
1. Contains configurations for vicious aspects of the app
2. database connection
3. mail server
4. cashing 
5. etc.
#### Database
1. contains all the database related files.
2. **Migration** => change the database table schema
3. **Seeds** => populate the database with some data
4. **Factories** => How your model should generate some fake data
#### public
1. all the publicly assessable assets.
2. eg index.php
3. 
#### Resources:
1. contains `css` and `js`
2. `vuejs` components are placed here

#### Routes
1. route definitions for the application
2. web routes, api routes etc
3. Example 
```
Route::get('/', function () {

    return view('welcome');

});
```
#### Storage
1. stores generated files like logs and cash data, file uploads etc.
#### Tests
1. Contains test suit for unit ant feature  testing
#### Vendor
1. managed by composer.
2. do not try to change anything in this directory.

#### Composer.json
1. define all the dependencies for the project
2. `require` => all the required libraries.
3. `require-dev` => required only while development.
4. `scripts` => similar to npm
```
 "require": { 

        "php": "^8.1",

        "guzzlehttp/guzzle": "^7.2",

        "laravel/framework": "^10.10",

        "laravel/sanctum": "^3.3",

        "laravel/tinker": "^2.8"

    },

    "require-dev": {

        "fakerphp/faker": "^1.9.1",

        "laravel/pint": "^1.0",

        "laravel/sail": "^1.18",

        "mockery/mockery": "^1.4.4",

        "nunomaduro/collision": "^7.0",

        "phpunit/phpunit": "^10.1",

        "spatie/laravel-ignition": "^2.0"

    },
```

#### To start a laravel application
`php artisan serve`