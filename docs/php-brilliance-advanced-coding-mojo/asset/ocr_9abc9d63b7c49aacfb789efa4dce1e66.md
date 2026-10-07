# Encapsulating our ideas.

Which is fine of course. At least until we reach that point where a colleague starts instantiating objects from class names held in variables. You know the thing that I mean: Dynamic class resolution.

```
// Scary code
$className = $propertyName 'Validator';
$validator = new $className($propertyValue);
return $validator;
```

The only places where things of this sort be happening inside factories, abstract or otherwise, and where the object returned conforms to a clear and well understood interface. If it happens out in the wilds, the code that forms the application's normal process flow, then you're, well, bugged to put it bluntly. The game over has knelt, it's time to start prompting the rewrite.

Instead of trying to wiggle out of it, let's say we're not going to do it. The concepts of loose coupling and dependency injection will be discussed at length later in this book. So too will the idea of developing an allergy to using the new keyword. For now though, I'd just like you to take it as read that instantiating validator instances inside our User class is a strictly-no scenario. I say take it as read', if this is already a second or more reading of this book, you'll already know why this should be so.

See? I told you. Polar bears!

So how do we get the validator into the User class then? One answer, certainly, to pass it in the constructor as well. Our next refactor does exactly this.

```
public function __construct(
    array $userData,
    UserDataValidator $udv
) {
    if (!$this->isValid($userData)) {
        throw new Exception(
            $udv->getErrorMessage(),
            $udv->getErrorCode()
        );
    }
    $this->userData = $userData;
}
```