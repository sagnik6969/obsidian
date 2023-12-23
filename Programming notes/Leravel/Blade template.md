1. Blade is a templating engine of laravel.
2. similar to `ejs` is `node.js`
3. blade templates will be stored in `resources/views`
4. `index.blade.php` => name of blade file
5. to render a blade template
```php
//routes/web.php
use Illuminate\Support\Facades\Route;

Route::get('/', function () {
    return view('index');
});

```
6. `view()` => an inbuilt function to render a blade template
7. we don't need to provide relative paths to blade templates. It is assumed that everything inside `resources/views` is blade template. 
#### To pass data to blade template
```php
Route::get('/', function () {

    return view('index', [

        'name' => 'Sagnik'

    ]);

});
```

```
//index.blade.php
 <h1>{{ $name }} Jana</h1>
```

1. In the blade file the variable 'name' will be replaced by 'Sagnik'
2. Interpolation syntax is similar to vue
3. You can pass html tags inside the variables
#### Isset
```
<body>

    @isset($name)

    <h1>{{ $name }} Jana</h1>

    @endisset

</body>
```
1. The h1 will only be displayed if $name is set