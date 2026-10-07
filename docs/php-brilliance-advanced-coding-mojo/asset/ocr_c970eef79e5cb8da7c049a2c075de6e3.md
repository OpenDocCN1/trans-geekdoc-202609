# PHP7

```
```php
declare(strict_types=1);

interface ReturnTypesInterface
{
    public function getFloat(): float;
    public function getString(): string;
    public function getArray(): array;
    public function getDatabaseAdapter(): PDO;
}
```
```

As we can see quite clearly, the application of the return type hinting at the interface level gives us the power to extend the coverage of the guarantee that we provide quite significantly. Any objects that implement such an interface, even though they may be perfectly unrelated to each other in every other sense, would be required to honour the return type declarations of such a guarantee. This is fantastic news for the maintenance of type safety within our application code.

To illustrate this effect, let's consider the following code

```
```php
declare(strict_types=1);

interface FooGuarantee
{
    public function getFoo(): Foo;
}
```
```

Here we have the interface declaration that requires implementers to provide a getFoo() method. Those implementers must also ensure that their version of this method includes the Foo return type exactly as it is written. That is, the implemented method must also specify `: Foo” in its method declaration.

Since we are now required to provide the return type hint, our implementations of this method will now also be required to actually return a value that is either a specific instance of a Foo object or an instance of a child class that extends the Foo parent.