```
public function doStuff($param)
{
    if (is_callable(array($param, 'quack')) {
        return call_user_func(array($param, 'quack'));
    }
}
```

Since we're not type hinting in the method signature, we're testing for that quack()
method before invoking it. In this regard, as long as the thing can quack we don'tnactually care what it is.

There's danger in these hills hough, danger that comes us as another form
of name collision. Admittedly, with a quack() method this will hardly ever be the
case since quacking is most definitely an unambiguously specific activity.

Nevertheless, invoking $employee->fire() will most likely have a different set of
outcomes compared to invoking $gun->fire(). The more common the method name,
the greater the opportunity to go wrong. How often do you see a run()
method? Or a doStuff()?

Nevertheless, we will certainly encounter duck typing from time to time, especially
in class constructors where it'll tend to take the form of testing a constructor parameter
to see whether it's an object or a string representation of the desired object's class
name. Like this.

```
class MyProcessor
{
    private $adapter;

    public function __construct($adapter)
{
        if (is_object($adapter)) {
            $this->adapter = $adapter;
        } else if (is_string($adapter) && class_exists($adapter)) {
            $this->adapter = new $adapter;
        } else {
            throw new \Exception("Invalid adapter param");
        }
    }
}
```