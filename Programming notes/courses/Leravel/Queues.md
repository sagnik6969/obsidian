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
8. `php artisan queue:work` to run all the works inside the queue. This command => process should be always running in the background in the production environment.
#### To execute a job in queue
1. it should implement `shouldQueue` interface. and laravel will put that job in queue.

#### Configuration file
`config/queue.php`
If you dispatch a job without explicitly defining which queue it should be dispatched to, the job will be placed on the queue that is defined in the `queue` attribute of the connection configuration:
in `queue.php`
```php
// This job is sent to the default connection's default queue...
ProcessPodcast::dispatch();

// This job is sent to the default connection's "emails" queue...
ProcessPodcast::dispatch()->onQueue('emails');
```
#### To give priority to queues
1. `php artisan queue:work --queue=high,default`
2. `high` has higher priority than `default`.
3. to put a job to high queue `ProcessPodcast::dispatch()->onQueue('high');`
4. we don't need to create queues separately laravel will automatically do that for us. 

#### Dealing with failed jobs
1. `php artisan queue:failed-table php artisan migrate` => to create a table for storing failed jobs.
2. `php artisan queue:failed` => to see list of failed jobs.
3. `php artisan queue:work --tries=3` => During the execution of a job if it fails laravel retry 3 times after that the job will be added to failed jobs table.
4. `php artisan queue:retry <id>` => to retry a job with id = `id`  We can get id from `php artisan queue failed
#### Creating and dispatching custom jobs`
1. to create a job `php artisan make:job <job name>`
2. jobs are like events and listeners bundled in a single file. 
3. They can be `dispatched` like events.
4. and they have `handle` method like `listeners` which is called when the job is `dispatched`.
5. arguments to `dispatch` method are passed to job constructor.
#### Rate Limiter for queues
1. In `AppServiceProvider.php`
```php
RateLimiter::for('backups', function (object $job) {
return $job->user->vipCustomer()
? Limit::none()
: Limit::perHour(1)->by($job->user->id);
});
```
2. in the job file
```php
public function middleware(): array
{
     return [new RateLimited('backups')];
}
```
3. Each time the job exceeds the rate limit, this middleware will release the job back to the queue with an appropriate delay based on the rate limit duration.
4. If you do not want a job to be retried when it is rate limited, you may use the `dontRelease` method: `new RateLimited('backups')->dontRelease()`

#### Tries
1. How many times a job should be retried before sending it to failed jobs.  
2. In the terminal `php artisan queue:work --tries=3` 
3. alternatively you can specify `public $tries = 3;` in the jobs file. this will override whatever specified in the terminal.
#### Timeout
1. How many seconds a job should run before it also times out.
2. In the terminal `php artisan queue:work --timeout=3`
3. alternatively you can specify `public $timeout = 3;` in the jobs file. this will override whatever specified in the terminal.
