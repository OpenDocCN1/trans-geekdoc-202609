Expressing good traits.

```
trait LoggingTrait
{
    private $logger;

    public function log($msg, $level)
    {
        $this->filename = $this->logFileName;
        $this->logger->setFileName($filename)
        ->log($msg, $level);
    }
}
```

Even though PHP is quite happy to let us do this, we absolutely must not allow this sort of thing to happen for quite obvious reasons. For properties and not for class constants either. Sure, we can now add a constant definition to the trait’s corresponding interface but we are now well aware that constants that are defined in interfaces are of the constant constant variety, we are actually wasting our time entirely. The consuming class wouldn’t be able to change it, so it might as well be written into the trait directly.

In any event, our trait has become far too concerned with the things that lay beyond its boundaries. If it can’t be covered in the corresponding interface, it shouldn’t be included in the trait’s code. Methods are safe since they do have the opportunity to appear in the interface. Constants are sometimes safe as long as we remember that, when declared in the interface they become immutable. When a trait references a property that is defined outside of itself, it is never safe.

Our next leaky scenario is one that bridges the gap between the previous leaks and the more general issue of method overrides. It’s also pretty nasty.