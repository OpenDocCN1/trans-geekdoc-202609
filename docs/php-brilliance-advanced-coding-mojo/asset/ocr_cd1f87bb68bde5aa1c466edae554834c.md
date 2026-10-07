Inheriting wealth vast is not always good.

```
try {
    $sportsCar = $factoryInstance->getCar();
} catch (CarException $e) {
    Logger::crit('Whoopsies');
}
```

Since our SportsCarException is a type of CarException, the try/catch block in our client code can accommodate it happily. What happens then if we went the other way?

```
class SportsCarFactory extends CarFactory
{
    public function getCar()
    {
        throw new VehicleException('Cannot make sportscar');
    }
}
```

This time we violated the definition that our abstract parent sets out by throwing a more generic type of exception and as a result, we are emitting an exception that our client code isn’t prepared to handle. Since our definition tells us to expect a certain type of exception, as brilliant PHP developers, should be coding up the client code in a way that can handle it. Or rather, we should be coding up child classes in a way that remains compatible with what the client code is expecting.

As long as we follow this rule, exceptions thrown by overriding methods of the child class should be of the same or a more specific type, we should be able to rest easy. After all, none of us caught exceptions to be thrown in production. When an application dies from an uncaught exception, we end losing valuable time.

By this point, you may well have noticed that I’ve been pushing my data type concept quite a bit. There’s a very solid reason for this; I’m keen to promoted that idea. When it comes to inheritance hierarchies, inheritance inheritance hierarchy I strongly believe that you should keep them as flat as possible. The flattest hierarchy possible consists of only two values: a parent and a child. The more that you can adhere to this, the more resilient your code becomes. As you might very well expect, I’m about to explain why doing the opposite is a bad thing.