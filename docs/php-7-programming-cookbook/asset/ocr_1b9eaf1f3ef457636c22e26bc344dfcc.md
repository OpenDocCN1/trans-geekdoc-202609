```
public static function getInstance()
{
    if (!self::$instance) {
        self::$instance = new self();
    }
    return self::$instance;
}
public function __get($key)
{
    return $this->registry[$key] ?? NULL;
}
public function __set($key, $value)
{
    {
        $this->registry[$key] = $value;
    }
}
```

![](bbox=[0.18, 0.45, 0.28, 0.51])

> You can mark a method as **final** to prevent it from being overridden. Mark a class as **final** to prevent it from being extended.

+   Normally, class constants are considered to have a visibility level of public. As of PHP 7.1, you can declare class constants to be *protected* or *private*. In the following example, the TEST_WHOLE_WORLD class constant behaves exactly as in PHP 5. The next two constants, TEST_INHERITED and TEST_LOCAL, follow the same rules as any protected or private property or method:

```
class Test
{
    public const TEST_WHOLE_WORLD   = 'visible.everywhere';

    // NOTE: only works in PHP 7.1 and above
    protected const TEST_INHERITED = 'visible.in.child.classes';

    // NOTE: only works in PHP 7.1 and above
    private const TEST_LOCAL= 'local.to.class.Test.only';

    public static function getTestInherited()
    {
        return static::TEST_INHERITED;
```