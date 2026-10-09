```
```text
{
    $Changed = array();
    $filtered = /* perform filtering operation on $item */
    if ($filtered !== $item)
        $Changed = Messages::$Messages['callback_key'];
    return new Result($filtered, $Changed);
}
} 
```
```

The callbacks themselves must implement the interface and return a `Result` instance. We can take advantage of the PHP 7 **anonymous class** capability by having our callbacks return an anonymous class that implements `CallbackInterface`. Here is how an array of filtering callbacks might look:

```
```text
use Application\Filter\{ Result, Messages, CallbackInterface };
$config = ['filters' => [
    'trim' => new class () implements CallbackInterface
    {
        public function __invoke($item, $params) : Result
        {
            $Changed = array();
            $filtered = trim($item);
            if ($filtered !== $item)
                $Changed = Messages::$Messages['trim'];
            return new Result($filtered, $Changed);
        }
    },
    'strip_tags' => new class ()
    implements CallbackInterface
    {
        public function __invoke($item, $params) : Result
        {
            $Changed = array();
            $filtered = strip_tags($item);
            if ($filtered !== $item)
                $Changed = Messages::$Messages['strip_tags'];
            return new Result($filtered, $Changed);
        }
    },
    // etc.
]
};
```
```