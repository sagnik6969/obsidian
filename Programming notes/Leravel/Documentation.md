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

### Resource
1. guarded => wont be automatically serialized when converting to json.
2. whenLoaded ......
### Traits

```
  

trait CanLoadRelationships

{

    public function loadRelationships(

        Model|QueryBuilder|EloquentBuilder $for,

        ?array $relations = null

    ): Model|QueryBuilder|EloquentBuilder {

  

        $relations = $relations ?? $this->relations ?? [];

  

        foreach ($relations as $relation) {

            $for->when($this->shouldIncludeRelation($relation),

                fn($query) =>

                $for instanceof Model ? $for->load($relation) : $query->with($relation));

        }

        return $for;

    }

  

    protected function shouldIncludeRelation(string $relation): bool

    {

        $include = request()->query('include');

  

        if (!$include) {

            return false;

        }

  

        $relations = array_map('trim', explode(',', $include));

  

        return in_array($relation, $relations);

    }

}
```
### User Authentication
1. `Hash::check($request->password, $user->password)`
2. `Hash::make('')`
3. `$token = $user->createToken('api-token')->plainTextToken;`
4. $request->user()->tokens()->delete()
5. expiration time of a token can be set in sangtom.php

### Gates / Policies
### Make artisan command
`php artisan make:command command_name`
### Task scheduling
`console/kernal.php`
```
  protected function schedule(Schedule $schedule): void

    {

        // $schedule->command('inspire')->hourly();

        $schedule->command('app:send-event-reminder')->daily();

        // To run the scheduled tasks `php artisan schedule:work`

    }
```

### Notification
`php artisan make:notification Notification_name`
`Notifiable trait`
`user->notify(new EventReminder())`
### Queues
### Queries
1. whereHas
2. orWhere
3. orWhereHas
4. where also accepts function 
### Login
```
if (Auth::attempt($credentials, $remember)) {

            return redirect()->intended('/');

        } else {

            return redirect()->back()->with('error', 'Invalid email or password');

        }
```
### Logout
`Auth::logout()`
### File Upload
```
        $file = $request->file('cv');

        $path = $file->store('cvs', 'private');
```
### Custom middlewire
```
public function handle(Request $request, Closure $next): Response

    {

        if ($request->user() === null || $request->user()->employer === null)

            return redirect()->route('employer.create')

                ->with('error', 'You have to register as an employer to create a job application.');

  

        return $next($request); // calls the next middlewire / function

    }
```
### Soft Delete
### Events
### Queues
`implements ShouldQueue`
##### To run a queue
`php artisan queue:work`
  
1. Queues allow some time consuming tasks to run in background
2. Good example of using queues is sending emails
3. in production environment redis or amazon sqs is used to store the queue
4. locally to just see how queue works we will use mysql
5. `php artisan queue:table , php artisan migrate`  => to create a queue table
6. QUEUE_CONNECTION=sync => to run every job in the queue synchronously without using the queue
7. QUEUE_CONNECTION=database => to use database to store the queue
8. `php artisan queue:work` to run all the works inside the queue. This command => process should be always
9. running in the background in the production environment.
### Match
```
 $books = match ($filter) {

            '' => $books->withCount('reviews')->withAvg('reviews', 'rating')->latest(),

            'popular_last_month' => $books->popularLastMonth(),

            'popular_last_6months' => $books->popularLast6Months(),

            'highest_rated_last_month' => $books->highestRatedLastMonth(),

            'highest_rated_last_6months' => $books->highestRatedLast6Months(),

            'default' => $books->withCount('reviews')->withAvg('reviews', 'rating')->latest(),

        };
```

### Log
### DB
`all paginate first` => don't require `get()`

### COmmands
1. to run scheduled tasks `php artisan schedule:work`
2. to run queue `php artisan queue:work`
3. to make the queue table in database `php artisan queue:table php artisan migrate`
4. 

