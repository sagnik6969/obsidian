1. Based on observer patterns
2. events are stored in `app/Events`
3. listeners are stored in `app/listeners`

#### Registering events
1. `eventServiceProvider.php -> $listen array`

```
protected $listen = [

OrderShipped::class => [
SendShipmentNotification::class,
     ],
];
```

#### Generating Event and Listeners
1. `php artisan make:event PodcastProcessed`
2. `php artisan make:listener SendPodcastNotification`

#### Automatic Event Discovery
1. laravel links events and listeners automatically
2. When Laravel finds any listener class method that begins with `handle` or `__invoke`, Laravel will register those methods as event listeners for the event that is type-hinted in the method's signature.
3. To enable automatic event discovery modify `shouldDiscoverEvents` method in `EventServiseProvider.php` to `return true`

```
public function shouldDiscoverEvents(): bool
    {
        return false;
    }
```

