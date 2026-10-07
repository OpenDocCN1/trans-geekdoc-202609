Code, but in the abstract sense.

```
```nreturn password_verify($rawPassword, $hashedPassword);
```
```

Familiar, no? Welcome back PasswordManager class, our doer from the previous chapter. We've taken a process, the concept of turning a user supplied string into a hashed representation of that same string and written out the code that we need to accomplish this task. I'll grant you, abstraction isn't especially complex in the humid, fetid jungles of the body of the getPasswordHas() method on lines 7-11. Note however that this code isn't floating freely within our codebase, it's locked away inside a method. When our calling code requires a hashed password value, it doesn't get to use that code directly because we've abstracted away inside a method call. This method call gets invoked when we need to trigger the complex process that's behind it.

The beauty of this is of course that gives us the ability to change what's happening behind the scenes without interrupting the operation of our application. If we need to increase the cost of the hashing operation, we can do that. If we need to supplement the PASSWORD_BCRY algorithm with a newer, more secure algorithm, we can do too. As long as the method continues to accept a raw password and return a hashed one, we don't necessarily need to know what processes have been abstracted away behind that very simple interface.

This is abstraction of control – hiding the details of a set of actions (computing the hash of a string) behind a different set of actions (invoking the method and collecting the return value).

# Summary

On our journey through abstraction, we started out in the humid, fetid jungles of abstraction abuse by considering how the notion of code reuse gets mistakenly tangled up in the process of abstracting to and inheriting from classes. By now I would hope that you're in agreement that taking advantage of abstraction as a means to avoid duplication is not a sound approach to respecting the DRY principle. With any kind of luck, I strengthened that argument by taking in the notion of convenience methods along the way.

As a quick refresher though, convenience methods are those methods that you might be tempted to add to a parent class just to provide easy access to a useful routine or