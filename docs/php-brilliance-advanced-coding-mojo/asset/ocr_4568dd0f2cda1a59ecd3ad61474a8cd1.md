And favour Composition too.

```
<?php
class Warrior implements Damageable
{
    public function getHealth()
{
        return $this->health + $this->subject->getHealth();
    }
}
```

Finally, we are in a position to start decorating our Warrior instance in an appropriate manner.

```
<?php
class BoiledLeatherArmour extends ArmourDecorator
{
    protected $health = 150;
}

class ChainMailHauberk extends ArmourDecorator
{
    protected $health = 200;
}

class OakShield extends ArmourDecorator
{
    protected $health = 75;
}

$decoratedWarrior = new OakShield(
    new ChainMailHauberk(
        new BoiledLeatherArmour(
            new Warrior()
        )
    )
);
echo $decoratedWarrior->getHealth();
// output: 525
```

Our end result? A Warrior instance "wrapped" in boiled leather, chain mail and an oak shield. Once we send this character into battle each layer of armour take as