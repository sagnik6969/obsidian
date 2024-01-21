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
