1. Controls how certain classes should be created and how dependencies should be passed.
2. Used for performing automatic dependency injection
3. dependency injection means class dependencies are injected into the object via constructor and seter methods.
4. We just need to type hint the dependency in the dependency in the constructor or in the setter method. Laravel will automatically create an appropriate object and pass it to the function.

#### Zero Configuration resolution
1. If a class has no dependencies or only depends on other concrete classes (not interfaces), the container does not need to be instructed on how to resolve that class.
2. It will be done automatically.

> Service containers work in `controllers`, `Event listeners` and `middlewires`

#### Bindings
1. Almost all the service container bindings are registered in the service providers
2. register the bindings in the `register()` method if service provider.
3. you can access the service container via `$this->app` 

```
$this->app->bind(Transistor::class, function (Application $app) {

return new Transistor($app->make(PodcastParser::class));

});
```
4. `$app->make` used to resolve sub dependencies.
5. `$this->app->singleton` => the container that should only be resolved one time. Once a singleton binding is resolved, the same object instance will be returned on subsequent calls into the container.
6. you may bind your user defined services to the container in app service provider.

#### To resolve the service containers
1. inside the service providers `$app->make(PodcastParser::class)`
2. other places `App::make(PodcastParser::class)`


### Facades
1. resolves a specific service container binding.
2. the methods of the returned object by the binding can be accessed as static `::` methods of the Facade.

```
class Cache extends Facade
{
    protected static function getFacadeAccessor()
    {
        return 'cache';
    }
}
```

### Contracts
1. Contracts are a `php interface` 
2. are created manually without using artisan command
3. interfaces only contain method signature.
4. to use a  Contract we need to bind then in any service provider to a class or an object. same way we bind other services.
5. the class we are binding to the contract must implement the contract interface.
6. To use a contract we need to type hint the contract in the method/ constructor defination.

### Contracts vs Fecades
1. contracts are used through dependency injection facades are imported directly.
2. 