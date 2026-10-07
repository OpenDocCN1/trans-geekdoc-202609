
Proding the polymorph.

```php
class RegularBullet {
    private $baseDamage = 10;
    public function getDamagePoints() {
        return $this->baseDamage;
    }
}
class HollowPoint extends RegularBullet {
    public function getDamagePoints() {
        $damagePoints = 2 * $this->baseDamage;
        return $damagePoints;
    }
}
```

Hopefully this rather simple bit of code quite clearly illustrates the idea that is subtype polymorphism. Our child class, HollowPoint overrides the parent’s getDamagePoints() method and in so changes the logic for how damage points are calculated when a round of a particular type hits the target. This still satisfies our earlier definition of polymorphism as being “Same name, different logic”. With subtype polymorphism, we are achieving the same name qualification by providing methods in the child class that override the identically named methods of the parent class.

If you hadn't already guessed, I'm about to go off on one of my gripes here. The main thrust of this particular gripe is that this generally the extent of those pesky tutorials that I have so much beef with. Let’s return to the second sentence of that Webopedia.com definition.

More specifically, it is the ability to redefine methods for derived classes.

How much do I wish that statement was better qualified? How much do I wish that the containing article went into detail about proper usage, pitfalls and gotchas. How much do I wish our juniors were presented with better quality information when they first perform an online search for articles on polymorphism?

Let's measure up our example, but in a way that conforms perfectly with this supposed definition of polymorphism.

```php
class ExplosiveRound extends RegularBullet
{
    public function getDamagePoints(Player $enemyPlayer )
    {
        $armorFactor = $enemyPlayer->getArmorPoints();
        $damagePoints = $this->getDamagePoints();
        $damagePoints = $damagePoints * 2;

        $damagePoints -= $armorFactor;
        return $damagePoints;
    }
}
```

At first glance this seems to satisfy the requirements of subtype polymorphism just after, we've successfully redefined the getDamagePoints() method in our derived class. Granted, we're probably now going to have to modify that whole enemy taking damage routine just to make sure we treat the player instance in the event that he takes a hit from an ExplosiveRound but hey, we can do that.

Polymorphism achieved! Check! Broken our application?

Yet this is the typical extent to which the basic tutorials take the topic of polymorphism. What are our poor junior developers supposed to do when they code above ought to be the sort of code that elicits a torrent of tears to cause a flood of near biblical proportions?

For the developer that truly wants to achieve PHP brilliance, or he will know in order to use subtype polymorphism correctly, or he will have to tread very carefully indeed. Fortunately for us, you've already put yourself through the pain and torture of the preceding two chapters on Abstraction and Inheritance and as a result, you already know that the code above is a monstrous huge no-no.

You already know this because, in the preceding chapter concerning Inheritance, you may or not have realised that I've already dealt with subtype polymorphism even though I didn't use the term specifically. In our child class implementations of the data type declared by our abstract parent, we can provide methods that override those of the same name as declared in the parent. We just need to keep those three rules in mind when we do.

Any changes to the method signature in the overriding method must remain compatible with the method signature as declared in the parent class. Any changes to the value that is returned from the overriding method in the child class must remain compatible with the type of return value declared in the parent class. And finally, if the overriding method in the child class can throw exceptions (or indeed, trigger an exception to be thrown) then these exceptions must be of the same type or derived from the exceptions that can be thrown by the same method in the parent. As long as we follow these three rules we're keeping any future bugs and headaches down to a minimum. One telltale sign to look out for, one that quietly inform us that we're failing to keep these rules, is if you find yourself needing to implement special logic in the client code to accommodate the quirks of one or more child classes from a particular inheritance hierarchy. That is to say, if you find yourself writing conditional statements to determine whether you're dealing with a RegularBullet or an ExplosiveRound then you can be sure that your child classes aren't conforming to the data type definition that the parent class provides.

There, I did warn you that I would repeat myself.

Nevertheless, this is how subtype polymorphism should be handled. To the well-informed, this is going to look an awful lot like I'm trying to bend subtype polymorphism to the will of parametric polymorphism. Which I am, of course.

# Parametric Polymorphism

Before I enter to start the definition of parametric polymorphism, I feel that I have to state that PHP isn't generally considered to be a language that natively supports the concept. Even so, the extraordinarily loosely typed nature of the language means that parametric polymorphism can be achieved straight out of the box, so to speak.

Consider the following code snippet.

```php
<?php
function multiplier($a, $b) {
    return $a * $b;
}

echo multiplier((int)2,(int)4); // Output '8'

echo multiplier((float)2.5, (float)6.0); // Output '15'

echo multiplier('abc', 5); // Output '0'
```

The function illustrated above can be considered to support parametric polymorphism since it will execute irrespective of the types. Nevertheless, and we got too carried away with the background details, the important point to make is that as long as the renderVehicle() method receives a parameter that is identifiably an instance of the Vehicle data type then that method should execute successfully and without complaint.
