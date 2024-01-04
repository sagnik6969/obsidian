In PHP, the `static` return type indicates that the method will return an instance of the class on which it is called.
`api` allows different software applications to communicate with eachother.

laravel debugger https://github.com/barryvdh/laravel-debugbar

````php
class TestClass {

    public function fetch(?array $extensions)
    {
        //...
    }        
}
````
=> the above code means that it can either be null or any array.
### Authentication
#### 'auth' middle wire in laravel
1. used for blade cookie based autication
#### 'auth:sangtom'  middlewire in laravel
1. used for token based authentication in api s.

```
public function __construct()
    {
        $this->middleware('auth:sanctum')->only('destroy');
    }
```

or
```
Route::middleware('auth:sanctum')->get('/user', function (Request $request) {
    return $request->user();
});
```

