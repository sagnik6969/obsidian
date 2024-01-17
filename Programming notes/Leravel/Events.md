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

#### Event discovery in Production
1. It is not very efficient for the framework to scan all of your listeners on every request
2. run `php artisan event:cache` to cache the event discovery
3. `php artisan event:clear` to destroy the cache.

#### Creating Events
1. Event class is essentially a data container which holds information / objects related to an event. These information/objects will be used by the listeners to perform different actions.

```php
<?php

namespace App\Events;
use App\Models\Order;
use Illuminate\Broadcasting\InteractsWithSockets;
use Illuminate\Foundation\Events\Dispatchable;
use Illuminate\Queue\SerializesModels;

class OrderShipped
{

use Dispatchable, InteractsWithSockets, SerializesModels;

/**
* Create a new event instance.
*/

public function __construct(
public Order $order,
) {}

}
```
