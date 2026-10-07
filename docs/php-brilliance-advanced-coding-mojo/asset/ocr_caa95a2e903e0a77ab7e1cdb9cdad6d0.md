# Do shoot the messenger

Now that we have had at least a very brief look at dependency injection containers, the time has come to examine another anti-pattern. Regrettable? Yes. Avoidable? No.

The anti-pattern in question is one known as *The Courier.*

The reason that *The Courier* crops up so frequently when a dependency injection container enters in to do with that second problem that I intimated at in the latter half of the previous chapter.

If you instantiate an instance of a “super factory” at bootstrap time, how do you make it available to the objects that need it?

The answer is not to turn objects into couriers in order to ferry the container to where it is needed.

We are getting ahead of ourselves though. Just what is the anti-pattern known as *The Courier?* The term was coined by Tom Butler in his blog post [OOP: The courier anti-pattern]¹ and I’m paraphrasing somewhat to describe it as thus:

> The Courier is used as a means of making dependencies accessible to parts of a system which them by passing those dependencies through components that do not.

If we push Lizzie to one side for a second, we can use her machine to code up a quick and dirty example to illustrate this idea.

First, we need a dependency.

```
// bootstrap.php
$db = new PDO($dsn);
```

¹https://t.je/oop-courier-anti-pattern.html