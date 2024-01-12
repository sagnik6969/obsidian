1. dependency injection
2. queues
3. all the configuration files are stored in /config
4. [Request Lifecycle - Laravel 10.x - The PHP Framework For Web Artisans](https://laravel.com/docs/10.x/lifecycle)
5. service container https://youtu.be/aQw7t0r9Vc8?si=abpEqc9Vz7u0YY5H
### Service containers
$app->make() === resolve() =>resolves the dependency

### Elloquest
has => only loads the rows which has a specific attribute / relation set.
![[Pasted image 20240112125811.png]]
=>also check conditions

doesnothave => opposite to has
![[Pasted image 20240112130318.png]]

### Type Hinting

add `?` before type to make the variable nullable

> find($id) takes an id and returns a single model. If no matching model exist, it returns null.
    
>   findOrFail($id) takes an id and returns a single model. If no matching model exist, it throws an error1.

### Cache
```
 $cacheKey = 'books:' . $filter . ':' . $title;

        $books = cache()->remember($cacheKey, 3600, fn() => $books->paginate());
```
To delete cache
`cache()->forget('book:' . $review->book_id))`


