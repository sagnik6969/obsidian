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
2. 
