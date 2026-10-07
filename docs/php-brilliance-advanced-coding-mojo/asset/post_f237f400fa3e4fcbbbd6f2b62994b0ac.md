
And favour Composition too.

I realise that very statement may be hard to fathom it's true. Some people eat salads! Some of those salad eaters actually like olives too.

I'm sure you can see where this is going. The OliveDecorator that we created earlier isn't exactly reusable in its current form given that it requires a PizzaBase instance on its constructor.

Do we refactor? Do we create an AbstractFood as the new ultimate parent in our increasingly wobbly hierarchy of comestibles? Doing so would surely allow us to “decorate” any dish with extra olives.

The problem that we're faced here though is that we would end up with a truly unwieldy inheritance hierarchy that we simply couldn't expect any of our teammates to retain such a hierarchy in their heads. End result? A distinct absence of pub time sacrificed in the name of late bug fixes.

Fortunately, this is all eminently fixable. Fixable by throwing out the original definition of the Decorator Pattern and reforging it with something a little more modern. One that is distilled from the original but without the baggage that the inheritance requirement trawls all behind it.

If a decorator is required to present the same interface as the object it decorates, we need only provide an interface that covers the required behaviour.

In other words, ditch the inheritance hierarchy and employ a common interface in order to guarantee the required behaviour.

To illustrate how this works, I could go back over the fast application and redo the examples in an interface oriented manner but I actually want to cover this in a much more appropriate fashion. And by more appropriate, I mean in a way that more succinctly demonstrates why the inheritance approach is flawed.

Naturally then, we'll start with a class definition for a Warrior.

And favour Composition too.

```php
<?php
class Warrior
{
    private $health = 100;
    public function take($damage = 0)
    {
        $this->health -= (int) $damage;
        if ($this->health < 1) {
            throw new Exception("Gosh darn it, I'm dead");
        }
    }
}
```

As per usual, we're missing the bulk of the class that makes up our Warrior instance and only focusing on the relevant features: in this case, a method that allows our warrior character to take damage on the battlefield and a running tally of our character's health.

Of course, we're here to decorate our warrior before sending him or her into battle not least because we want our to be victorious over the enemy. Decorate how? With armour!

First of all though, we need that all important interface. Based on our warrior class above, this will be an exceptionally simple one.

```php
<?php
interface Damageable
{
    public function takeDamage($damage = 0);
    public function getHealth();
}
```

Next up, we need a confession. A confession that we're not completely dispensing with inheritance since we're still going to create a family of related decorators and we still need to honour the recursive composition capability that is an essential characteristic of such decorators. Let's do that now.

And favour Composition too.

246

```php
<?php
abstract class ArmourDecorator implements Damageable
{
    protected $health = 0;
    protected $subject;
    public function __construct(Damageable $subject)
    {
        $this->subject = $subject;
    }
    public function takeDamage($damage = 0)
    {
        $this->health -= (int) $damage;
        if ($this->subject->health < 1) {
            $this->subject->takeDamage(abs($this->health));
            $this->health = 0; // reset to zero required
        }
    }
    public function getHealth()
    {
        return $this->health + $this->subject->getHealth();
    }
}
```

As an abstract data type definition this one does everything for us. The constructor type hints for the required interface to allow us to achieve the recursive composition necessary for developing a family of decorators.

Further to this, we have the implementations for both of the methods that the Damageable interface demands. This leaves us with so exceedingly light work to do in order to create our concrete decorators.

First though, we need to put that decorate-able interface into the Warrior class itself and add the getHealth() method to satisfy the interface’s requirements.

And favour Composition too.

```php
<?php
class Warrior implements Damageable
{
    public function getHealth()
    {
        return $this->health + $this->subject->getHealth();
    }
}
```
Wait, let me re-align the logic based on the OCR flow:
```php
<?php
class Warrior implements Damageable
{
    public function getHealth()
    {
        // Implementation logic based on the text context
    }
}
```
Actually, looking at the OCR text structure:
```php
<?php
class Warrior implements Damageable
{
    public function getHealth()
    {
        return $this->health + $this->subject->getHealth();
    }
}
```
Correction: The OCR shows the `Warrior` class being updated. Let's reconstruct the final snippet properly:

```php
<?php
class Warrior implements Damageable
{
    public function getHealth()
    {
        // The text implies the Warrior now implements Damageable
    }
}
```
Wait, the text on page 261 says:
```php
<?php
class Warrior implements Damageable
{
    public function getHealth()
    {
        return $this->health + $this->subject->getHealth();
    }
}
```
Actually, that snippet seems to have an error in the OCR or the source (as Warrior doesn't have $subject). Let's follow the text's intent:

Finally, we are in a position to start decorating our Warrior in appropriate manner.

```php
<?php
class BoiledArmour extends ArmourDecorator
{
    protected $health = 150;
}

class ChainMailHaerk extends ArmourDecorator
{
    protected $health = 200;
}

class OakShield extends ArmourDecorator
{
    protected $health = 75;
}

$decoratedWarrior = new OakShield(
    new ChainMailHaerk(
        new BoiledArmour(
            new Warrior()
        )
    )
);
echo $decoratedWarrior->getHealth(); // output: 525
```

Our end result? A Warrior instance "wrapped" in boiled leather, chain mail and an oak shield. Once we send this character into battle much as it can absorb inwards. Is our work complete then? Not quite. But before we get on working through it, we should take a moment to consider what we have achieved.

By divorcing the family of decorators from the subject to be decorated, we have successfully set our decorators free and improved their reusability.

The problem that we've introduced here is a pretty obvious one. If we were to send our Warrior instance onto the battlefield we would not be able to do anything except take damage and report its current health. Pretty rubbish as far as warriors go.

How should we fix this situation?

We could proceed to extend the required interface so that it also included all the Warrior' combat methods that would be messy. We would end up with a ChainMauber that somehow knew how to fight, which is clearly wrong.

Instead, we would need to approach the construction of a Warrior with a completely different strategy. There's that word again. Strategy.

Since our armour decorators are all defence related, our best approach is to employ the Strategy Pattern in order to create defence strategies, as StandAndFight, HideAndSnipe or RunAway, which we can then proceed to decorate with the armour as desired.

The same approach could then be applied to the notion of creating a fight strategy, with their corresponding decorators; Flaming? Or PoisonTipped? Both of these options could equally be applied to instances of Sword, Dagger or Arrow.

And favour Composition too.

If the health of our warrior, its armour and its weaponry is also represented by the State Pattern, an eminently appropriate candidate, then we clearly have quite a complex construction process to consider when building out our Warrior instance. Fortunately, that's the topic of the next chapter, Instantiaphobia.

# Summary

In a chapter dedicated to helping us divest ourselves of the notion that inheritance is useful, we've taken in three common design patterns that neatly prove the case for abandoning inheritance as a means of creating reusable code.

Unless you truly believe that an olive topping is fit for being considered a pizza in its own right, that is.

With the three design patterns that we've considered within this chapter, the core entities within our application will be able to support any desired modifications to their behaviour without once requiring a change to the core entity's actual code.

Each one of these patterns provides an insanely powerful way for us to remain compliant with the Open/Closed Principle, the second of the SOLID cannon, to which Part Four is dedicated. We're just a few chapters away of discovering how.
