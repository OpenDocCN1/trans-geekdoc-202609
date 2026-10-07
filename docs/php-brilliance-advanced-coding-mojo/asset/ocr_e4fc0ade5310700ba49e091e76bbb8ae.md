And favour Composition too.

```
class Order
{
    private $status;
    private $orderState;
    public function setState(OrderStateAbstract $state)
{
        $this->status = $state->getValue();
        $this->orderState = $status;
    }
    public function isDispatched()
{
        return $this->orderState->isDispatched();
    }
    public function canBeCancelled()
{
        return $this->orderState->canBeCancelled();
    }
}
```

The first thing to note with these changes is that we're now modifying the Order object's status property indirectly by injecting an appropriate order state instance and allowing that to govern the corresponding value. If we were previously providing a setState() method on our Order object's interface, we can now safely remove it.

The second thing to note is that all of the implemented status related methods defer the responsibility for answering questions to the injected state instance. The interface that the Order object exposes to its collaborators remains unchanged. Therefore, the code that used to work with the previous version will continue to work with the new version. No refactoring required. Bonus!

This last point does highlight a common issue with the State Pattern though. Since this is a form of delegate polymorphism, we have a natural requirement to implement the forwarders, the proxy methods, in the order to make it work. That's potentially a lot of method names in the composed behaviour that need to be duplicated in the composing class.

The benefits outweigh the cost of this additional work though. With the rest of the order object having a low change expectancy, it's superbly cacheable. When we pop the thing out of whichever caching mechanism that we choose to employ,