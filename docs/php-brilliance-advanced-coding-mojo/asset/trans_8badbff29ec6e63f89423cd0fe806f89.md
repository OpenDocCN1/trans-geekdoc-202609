
产生多态。

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

希望这段简单的代码能相当清晰地说明**子类多态（subtype polymorphism）**的概念。我们的子类 `HollowPoint` 重写了父类的 `getDamagePoints()` 方法，从而改变了特定类型子弹击中目标时计算伤害点的逻辑。这仍然符合我们早期对多态的定义，即“同名、不同逻辑”。通过子类多态，我们通过在子类中提供重写父类中同名方法的方法，实现了相同的同名限定。

如果你还没有猜到，我正要开始抱怨我的其中一个不满点了。这个抱怨的核心点在于，通常情况下，我非常反感的那些该死的教程就仅限于此水平。让我们回到 Webopedia.com 那个定义的第二句。

更具体地说，它是为派生类重新定义方法的能力。

我多希望那句陈述能更严谨啊？我多希望包含该定义的文章能详细介绍正确的用法、陷阱和注意事项啊。我多希望我们的初级开发者在第一次在网上搜索关于多态的文章时，能看到更高质量的信息？

让我们来衡量一下我们的例子，但用一种完全符合这个所谓多态定义的方式。

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

乍看之下，这似乎满足了子类多态的要求——紧接着，我们在派生类中成功地重新定义了 `getDamagePoints()` 方法。诚然，我们现在可能不得不修改整个敌人受伤害的程序，以确保在玩家被 `ExplosiveRound`击中时能正确处理玩家实例，但嘿，这点我们可以做得到。

多态达成！检查！搞崩了我们的应用程序？

然而，这就是基础教程对待多态这一主题的典型程度。当我们可怜的初级开发者编写上述代码时，他们该怎么办？这种代码本应该是那种引发泪水洪水、导致类似圣经规模洪水的代码。

对于真正想要实现 PHP 卓越境界的开发者来说，他将知道为了正确使用子类多态，否则他必须表现得非常小心。我们来说幸运的是，你已经经历了前两章关于“抽象”和“继承”的痛苦和折磨，作为结果，你已经知道上面的代码是一个巨大的禁忌。

你已经知道这一点了，因为在上一章关于“继承”的章节中，你可能意识到（也可能没有）我已经处理过子类多态了，尽管我没有专门使用这个术语。在对抽象父类声明的数据类型的子类实现中，我们可以提供重写父类中声明的同名方法。我们只需要在执行时记住这三条规则即可。

重写方法中方法签名的任何更改必须与父类中声明的方法签名保持兼容。子类中重写方法返回值的任何更改必须与父类中声明的返回类型保持兼容。最后，如果子类中的重写方法可以抛出异常（或者实际上是触发异常抛出），那么这些异常必须与父类中相同方法可以抛出的异常类型相同，或派自这些异常。只要我们遵循这三条规则，就能将未来的 Bug 和头疼问题降到最低。一个需要注意的迹象（一个静静告诉我们未能遵守这些规则的信号）是：如果你发现自己需要在客户端代码中实现特殊逻辑，以适应特定继承层级中一个或多个子类的奇特行为。也就是说，如果你发现自己正在编写条件语句来判断你处理的是 `RegularBullet` 还是 `ExplosiveRound`，那么你可以确定，你的子类没有符合父类提供的数据类型定义。

好了，我确实警告过我会重复一遍了。

尽管如此，这才是应该处理子类多态的方式。对于见多识的人来说，这看起来非常像我正试图让子类多态服从参数多态（parametric polymorphism）的意志。当然，我确实是。

# 参数多态 (Parametric Polymorphism)

在我开始定义参数多态之前，我觉得必须声明，PHP 通常不被认为是一种原生支持该概念的语言。尽管如此，这种语言极其松散的类型特性意味着，参数多态可以说“开箱即用”。

考虑以下代码片段。

```php
<?php
function multiplier($a, $b) {
    return $a * $b;
}

echo multiplier((int)2,(int)4); // 输出 '8'

echo multiplier((float)2.5, (float)6.0); // 输出 '15'

echo multiplier('abc', 5); // 输出 '0'
```

上述示例函数可以被认为支持参数多态，因为它无论类型如何都能执行。然而，我们太沉溺于背景细节了，要说明的重点是：只要 `renderVehicle()` 方法接收到的是一个标识为 `Vehicle` 数据类型实例的参数，该方法就应该成功执行且不报错。

