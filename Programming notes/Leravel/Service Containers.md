1. Used for performing automatic dependency injection
2. dependency injection means class dependencies are injected into the object via constructor and seter methods.
3. We just need to type hint the dependency in the dependency in the constructor or in the setter method. Laravel will automatically create an appropriate object and pass it to the function.

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
