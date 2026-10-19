```
use Illuminate\Container\Container;

/**
 * Create a new class instance.
 *
 * @param \Illuminate\Container\Container $container
 * @return void
 */
public function __construct(Container $container)
{
    $this->container = $container;
}
```

# Automatic Injection

Alternatively, and importantly, you may type-hint the dependency in the constructor of a class that is resolved by the container, including controllers, event listeners, middleware, and more.

Additionally, you may type-hint dependencies in the handle method of queued jobs. In practice, this is how most of your objects should be resolved by the container.

For example, you may type-hint a repository defined by your application in a controller's