
Inheriting vast wealth is not always good.

```
class SportsCarFactory extends CarFactory
{
    public function getCar() {
        // make a sports car
        return new Vehicle();
    }
}
```

I've substituted the return type so that the getCar() method returns a more generic Vehicle instance. According to our rule, this is wrong. If we follow the logic, we can confirm that it's wrong. Remember, our definition in the abstract parent states that a Car instance is being returned from this method call. As a result, our client code is geared to work with the Car instances that it expects to get back from invoking this method. Yet here, when our client code encounters a SportsCarFactory instance, it's yielding the more generic Vehicle type. We know from our hierarchy that a Vehicle is not a type of Car. When the client expects to work with a Car instance but gets a Vehicle instance instead, problems are sure to follow. End result? Less pub time.

We'd be better off keeping the return types identical but happily, real world expectations will generally map the second rule. A more specialised child class can emit more specialised return types.

So what of our last rule? Our last rule is super easy since it maps the logic of our second rule onto the use of exceptions. Let's spell it out: The overriding methods of our child classes may only throw the same or more specialised instances of the exceptions that can be thrown in the overridden method of our parent class.

Let’s start with the very same data type again.

Inheriting vast wealth is not always good.

```
abstract class CarFactory
{
    /**
     * @throws CarException
     */
    public function getCar()
    {
        throw new CarException('Cannot make car');
    }
}
```

This time, I'm only focusing on the exceptions that are being thrown. We have a new inheritance hierarchy to deal with but since it's a direct parallel to our Vehicle hierarchy, I'll skip the code and just express it like this: VehicleException->CarException->SportsCarException. As before, our data type is selecting the middle type as being the one it emits, but since it's an exception it will be thrown instead of returned.

Let's look now at our modified SportsCarFactory, which would be coded up like this.

```php
class SportsCarFactory extends CarFactory
{
    public function getCar()
    {
        throw new SportsCarException('Cannot make sportscar');
    }
}
```

Our specialised child instance is now throwing a more specific type of exception. This is ok still. Our data type definition states that a CarException can be thrown by this method so correspondingly, our client code is prepared for it.

Inheriting wealth vast is not always good.

```php
try {
    $sportsCar = $factoryInstance->getCar();
} catch (CarException $e) {
    Logger::crit('Whoopsies');
}
```

Since our SportsCarException is a type of CarException, the try/catch block in our client code can accommodate it happily. What happens then if we went the other way?

```php
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

By this point, you may well have noticed that I’ve been pushing my data type concept quite a bit. There’s a very solid reason for this; I’m keen to promote that idea. When it comes to inheritance hierarchies, inheritance inheritance hierarchy I strongly believe that you should keep them as flat as possible. The flattest hierarchy possible consists of only two values: a parent and a child. The more that you can adhere to this, the more resilient your code becomes. As you might very well expect, I’m about to explain why doing the opposite is a bad thing.

## Respect your elders

Good parenting should always include encouraging your offspring to respect the guidelines laid down by the parents. In an object oriented sense, this means sure that your child classes continue to honour the promises made by their parents through the interfaces that the parents have exposed. If the child can achieve this, it doesn't actually matter whether the parent class has been declared abstract or not so long as you remember what the client code is expecting to be able to do with the instances that arise from this hierarchy.

Once this has been achieved, there clearly isn't any genuine limit to the number of tiers in the hierarchies that you create. If each child recognizes and respects the requirements that are laid down by your parent, with specific regard to the three rules that I have described above, your application should continue along its merry way without stumbling over a type safety glitch.

Nevertheless, there is one particular factor that seems to get in the way of adhering to these rules. Humans. Pesky humans. Pesky little of the programmer variety who aren't quite logical in their information processing as the chips and circuits that they seek to manipulate.

When you create larger tiers of inheritance hierarchies, it's just so tiresome trying to keep track of what is in each particular layer. If you or your colleagues have to trace the execution of a method call up and down multiple layers of inheritance, you may just find yourself missing the one subtle but critically important nuance in the flow. If you handed me a troublesome stack of inheriting class definitions, I can guarantee that it'd take the sloppy puddle of grey mess between my ears a not insignificant amount of time to absorb all of the details, let alone find the problem. But when you flatten those stacks, when you keep your hierarchies down to the least number of layers as possible (ideally two), you make the code far palatable, far more digestible for the very same humans.

For our child classes to be compatible with the parents they extend, you are virtually guaranteed to find that bugs will appear. Bugs that are directly attributable to this very specific set of circumstances. This should obviously be a situation that you, as a buddingly Brilliant PHP developer, should be keen to avoid, regardless of whether you value your pub time or not.

Inheriting wealth is not always good.

## Inheritance Abuse

I couldn't easily get to the end of a chapter without going into something I've come to call Inheritance Abuse. You'll recall earlier in this chapter that I made mention of a particular horror story, one in which a company's framework had the controllers extending the view? Well it wasn't quite simple as all that.

It didn't just have the developer create a controller by extending the View class directly. Instead, there were two, three or four intermediary levels of derived classes to contend with. If I recall correctly, the worst violation had seven in its hierarchy with the View class at one and the Controller class at the other. The View class itself provided an init() method that allowed for the execution of some page setup routines. In some, but not all, of the derived classes the init() method was overridden. For example, a page controller within the admin section of the site would need to extend a particular admin-flav child of the View class because its overriding init() method included a test to see whether the visitor accessing an admin page was a) logged in and b) had admin rights.

Let's be thankful for merci though. PHP does not support multiple like C++; each class may only extend a single parent. As we have seen though, it places no restriction on the creation of multi-tier inheritance hierarchies. Any developer so without such thoughts can create their own “word ladders” in code, one little bit in each tier until finally the two extremities are connected. This is, in essence, the very thing that leads to what is known as the Yo-Yo problem, which I have personally experienced few more times than I would have preferred.

The Wikipedia page on the Yo-Yo problem makes a very apt description of it, so I shall simply quote the first sentence here:
