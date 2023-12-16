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
1. It contains some case files that laravel automatically generates.
2. no need to know
#### Config
1. Contains configurations for verious as