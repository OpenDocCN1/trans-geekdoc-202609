# Favour Interfaces.

Unshifting an array with a string value will give us an array that contains the unshifted string in its first index.

This is type safety at work. No developer in their right mind would try to divide a string by an array and expect a boolean result. Stuff just doesn't happen that way.

It's very same notion that we should be able to apply to the custom data types that we create. The abstract classes and the interface definitions we set down in code describe things that we can type hint for method signatures.

When we type hint for these things, we are relying on the same kind of knowledge that we can apply when operating on the native data types. Just so long as we continue to honour the guarantees that an interface declaration provides. And just so long as we continue to honour the interface that our abstract classes describe.

When we do this, when we ensure that our custom data types behave consistently, then we are achieving type safety within our code and by extension, we eliminate the possibility of bugs to occur as a result of our failing to do so.

This is what underpins the idea “programming to an interface, not an implementation.” When we can hint for a particular type of data in a method signature, the code within that method can operate reliably in conjunction with those input parameters. But only if we take those interfaces and abstract classes seriously.

The key concept in all of this is that our client code, our method bodies, should be able to operate consistently with those input parameters irrespective of the actual, concrete identity of those parameters.

In real terms, practising this particular principle means not doing this:

```
<?php
class AbstractDocument
{
    private $db;
    public function __construct(mysqli $db)
    {
        $this->db = $db;
    }
}
```

But instead, doing this