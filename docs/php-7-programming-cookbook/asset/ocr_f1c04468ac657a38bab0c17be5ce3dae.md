+   3. The constructor initializes these properties. We also throw in `__toString()`, in case we need quick access to the name of this publisher:

```
```
public function __construct($name)
{
    $this->name = $name;
    $this->data = array();
    $this->subscribers = array();
    $this->linked = array();
}

public function __toString()
{
    return $this->name;
}
```
```

+   4. In order to associate a subscriber with this publisher, we define `attach()`, which is specified in the `SplSubject` interface. We accept an `SplObserver` instance as an argument. Note that we need to add entries to both the `$subscribers` and `$linked` properties. `$linked` is then sorted by value, represented by the priority, using `arsort()`, which sorts in reverse and maintains the key:

```
```
public function attach(SplObserver $subscriber)
{
    $this->subscribers[$subscriber->getKey()] = $subscriber;
    $this->linked[$subscriber->getKey()] =
        $subscriber->getPriority();
    arsort($this->linked);
}
```
```

+   5. The interface also requires us to define `detach()`, which removes the subscriber from the list:

```
```
public function detach(SplObserver $subscriber)
{
    unset($this->subscribers[$subscriber->getKey()]);
    unset($this->linked[$subscriber->getKey()]);
}
```
```

+   6. Also required by the interface, we define `notify()`, which calls `update()` on all the subscribers. Note that we loop through the linked list to ensure the subscribers are called in order of priority:

```
```
public function notify()
{
    foreach($this->linked as $key => $value)
    {
        $this->subscribers[$key]->update($this);
    }
}
```
```