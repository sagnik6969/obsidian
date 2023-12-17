1. ` @yield('title')` => placeholders
2. `@section('title') @endsection` => will replace `@yield('title')`
3. `@extends('layouts.app')` => template inheritance => the path should be separated by "." the path to `app.blade.php` is `layouts/app.blade.php`

```
Route::get('/tasks/{id}', function ($id) use ($tasks) {

  $task = collect($tasks)->firstWhere('id', $id);

  // collect function converts an array to laravel collections
  // php arrays are not object => main limitation.
  // Thats why we cant add functions to them.

  if (!$task) {
    abort(Response::HTTP_NOT_FOUND);
    // returns a 404 not found error
    //need to use Illuminate\Http\Response;
  }
  return view('show', ['task' => $task]);

})->name('tasks.show');
```

4. `abort(Response::HTTP_NOT_FOUND)` => used to return 404 not found error and close the request execution.
5. we beed to use the namespace `Illuminate\Http\Response` for `Response::HTTP_NOT_FOUND`
6. `$task = collect($tasks)->firstWhere('id', $id);` => collect function converts an array to laravel collections. 