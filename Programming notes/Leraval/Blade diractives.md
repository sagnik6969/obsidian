1. To use a outside variable inside an anonyms function use need to use the `use()` keyword like the following
```
Route::get('/', function () use ($tasks) {

    return view('index', [

        'tasks' => $tasks

    ]);

});

```
