1. To use a outside variable inside an anonyms function use need to use the `use()` keyword like the following
```
Route::get('/', function () use ($tasks) {

    return view('index', [

        'tasks' => $tasks

    ]);

});

```

#### Blade examples
1. most of the blade functions are similar to `php` functions
```blade
 @if (count($tasks) > 0)
    <ul>
@foreach($tasks as $task)
        <li>
            {{ $task->title }}
        </li>
@endforeach
    </ul>
    @else
    <p>No task found</p>
    @endif
```

2. **Forelse**
```blade
@forelse($tasks as $task)

        <div>{{ $task -> title }}</div>

    @empty

        <div>No task found</div>

    @endforelse
```
- if tasks is empty then `    @empty` will be executed.
- ` <a href="{{ route('tasks.show',['id' => 12]) }}">{{ $task -> title }}</a>` => to use a named route in href in blade
- 


