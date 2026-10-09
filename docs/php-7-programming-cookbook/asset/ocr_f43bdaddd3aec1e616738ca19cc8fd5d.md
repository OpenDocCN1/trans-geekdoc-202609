+   4. We also throw in an implementation of __invoke() that returns an instance of the *stack* property. This allows us to use the object in a direct function call:

```
public function __invoke()
{
    return $this->stack;
}
```

# How it works...

One possible use for a stack is to store messages. In the case of messages, it is usually desirable to retrieve the latest first, thus it is a perfect use case for a stack. Define the Application\Generic\Stack class as discussed in this recipe. Next, define a calling program that sets up autoloading and creates an instance of the *stack*:

```
<?php
// setup class autoloading
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
use Application\Generic\Stack;
$stack = new Stack();
```

To do something with the stack, store a series of messages. As you would most likely store messages at different points in your application, you can use *sleep*() to simulate other code running:

```
echo 'Do Something ... ' . PHP_EOL;
$stack->push('1st Message: ' . date('H:i:s'));
sleep(3);

echo 'Do Something Else ... ' . PHP_EOL;
$stack->push('2nd Message: ' . date('H:i:s'));
sleep(3);

echo 'Do Something Else Again ... ' . PHP_EOL;
$stack->push('3rd Message: ' . date('H:i:s'));
sleep(3);
```

Finally, simply iterate through the stack to retrieve messages. Note that you can call the *stack* object as if it were a function, which returns the SplStack instance:

```
echo 'What Time Is It?' . PHP_EOL;
foreach ($stack() as $item) {
    echo $item . PHP_EOL;
}
```