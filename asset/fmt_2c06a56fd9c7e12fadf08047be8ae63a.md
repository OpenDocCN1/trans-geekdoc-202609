
`class GiantPanda extends Panda` {

    // 噔噔噔噔噔——！

}

```
万岁！有一些新语法。这意味着我们正要为我们的武器库添加一个新工具！

这个`extends`关键字是干什么的？我们实际上是在告诉 PHP，`GiantPanda`类应该继承自`Panda`类。你可以说`GiantPanda`类将从`Panda`那里借鉴遗传材料。这意味着`GiantPanda`获得了访问`Panda`所有属性和方法的权限。

## 证明给你看！

噢吗？不相信我？我要拼命证明给你看！在下一节中，请假设类定义仍然在那里。为了清晰起见，我会省略它们。我不想成为那种为了增加页数而重复大量代码的俗作者！我们现在是朋友了！我绝不会对你那样做。现在你不觉得不信任我而感到内疚吗？

### 示例 03：使用子类

```php
<?php

// 创建一个新的大熊猫实例。
$giantPanda = new GiantPanda;

// 获取毛皮类型。
echo $giantPanda->getCoat();
```

我们创建了`GiantPanda`类的新实例，并在上面调用了`getCoat()`方法。我们输出了这个值，因为我们想看到结果。让我们看看输出。

### 示例 04：输出

```
fluffy
```

哇。它太蓬松了，我要晕了！

正如你所看到的，我们的大熊猫从它的熊猫父母那里继承了`getCoat()`方法和`$coat`属性（带有默认值）。

虽然红熊猫和大熊猫相似，但大熊猫的毛皮没有那么蓬松，所以我们需要在`GiantPanda`类中表示这一点。让我们试一下！

### 示例 05：重写属性

```php
class Panda
{
    // 属性
    var $coat = 'fluffy';
    var $colour;

    // 方法
    function getCoat()
    {
        return $this->coat;
    }

    // 方法
    function getColour()
    {
        return $this->colour;
    }
}

class GiantPanda extends Panda
{
    var $coat = 'less fluffy';
}
```

在上面的示例中，我们重写了来自`Panda`类的`$coat`属性。在`GiantPanda`类中，我们重新声明了`$coat`为`'less fluffy'`。我们完全没有修改`getCoat()`方法。现在尝试调用这个方法。

### 示例 06：访问被重写的属性

```php
<?php

// 创建一个新的大熊猫实例。
$giantPanda = new GiantPanda;

// 获取毛皮类型。
echo $giantPanda->getCoat();
```

### 示例 07：输出

```
less fluffy
```

正如你看到的，父类`Panda`中的`getCoat()`方法尊重了我们对子类`GiantPanda`类中`$coat`变量的修改。它返回了值`less fluffy`。我们重写了这个字段的值。

## 继承

我们也可以重写来自父类的类方法。你只需要在子类中重新声明你想重写的属性或方法即可。如果还不清楚，"父"类就是你所扩展的类。在上面的示例中，父类是`Panda`。"子"类是实现`extends`关键字的那个类。在上一个示例中它就是`GiantPanda`。

类可以拥有继承链。这里有一个关于属于继承链的类的示例。

### 示例 08：继承链

```php
class First
{
    var $legendary = 'Barney Stinson';
}

class Second extends First
{
}

class Third extends Second
{
}

class Fourth extends Third
{
}
```

在上面的示例中：

- `Second`继承自`First`
- `Third`继承自`Second`
- `Fourth`继承自`Third`

看起来像这样：`First <- Second <- Third <- Fourth`

## 类型提示

在之前的章节中，我们发现了如何对变量进行提示，但它们并不是唯一可以提示的类型。你看，你也可以对参数进行提示（不用担心功能，我们只是在考虑结构）。让我们通过创建类来演示。

### 示例 09：类的类型提示

```php
<?php

class Sephiroth
{
    function equipWeapon($weapon)
    {
        echo 'Die die!';
    }
}

class Weapon
{
}
```

这意味着你只能向此方法传递`Weapon`类实例。让我们尝试一下。

### 示例 10：将类实例作为参数

```php
<?php

// 创建一个 Sephiroth 类。
$sephiroth = new Sephiroth;

// 创建一个 Weapon 类。
$weapon = new Weapon;

// 调用 equipWeapon() 方法。
$sephiroth->equipWeapon($weapon);
```

如果我们执行代码，就会看到预期的`'Die die!'`。去尝试这种类型的参数。我可以向你保证，PHP 不会高兴。

早些时候我告诉过只有提示类型的实例是被允许的，实际上我撒了小谎。你看，你也可以传递继承自提示类型的类。让我们看看实际效果。

### 示例 11：将子类传递给父类类型提示方法

```php
<?php

class Sephiroth
{
    function equipWeapon(Weapon $weapon)
    {
        echo 'Die die!';
    }
}

class Weapon
{
}

class Masamune extends Weapon
{
}

class Murasame extends Weapon
{
}

// 创建一个 Sephiroth 类。
$sephiroth = new Sephiroth;

// 创建一个 Masamune 类。
$masamune = new Masamune;

// 创建一个 Murasame 类。
$murasame = new Murasame;

// 使用 masamune 调用 equipWeapon() 方法。
$sephiroth->equipWeapon($masamune);

// 使用 murasame 调用 equipWeapon() 方法。
$sephiroth->equipWeapon($murasame);
```

## 18. 作用范围 (Scope)

我们都有秘密，不是吗？我的秘密就是我从卡迪夫动物园偷了无数只小熊猫。我把它们都藏在我的地下室里，在那里训练它们参加第三次世界大战。实际上，假装你没听到刚才那些话就好了。

如果你有一些不想让别人碰的东西，你会希望让它保持**私有 (private)**。有些东西注定是要分享的，并且将**公开 (publicly)** 可用。有时，你愿意分享你的秘密，但你会想要**保护 (protect)** 它们，以免它们伤害到你。

你的代码也不大区别。其他人可能想使用你的类，这没关系，你不希望他们乱改可能会破坏其功能的东西。我们可以通过在方法和属性上定义作用范围，帮助他人以合理的方式使用我们的代码。

## 公有 (Public)

目前为止，我们一直在使用`var`来声明类属性，并仅使用`function`来创建类方法。以这种方式声明变量会使其变成公共的。

公共属性可以使用对象运算符`->`从类实例外部访问。例如：

### 示例 01：访问类属性

```php
<?php

$panda = new Panda;

echo $panda->name;
```

公共方法可以再次使用对象运算符`->`在实例上调用。

## 示例 02：访问类方法

```php
<?php

$panda = new Panda;

echo $panda->squeak();
```

由于我们目前的属性和方法都是公共的，为什么我们不开始使用具描述性的关键字来指示它们的作用范围呢？

事实是，大多数程序员不会使用`var`来声明他们的类属性。相反，使用`public`关键字更好。让我们来看一个例子，好吗？

## 示例 03：一个公共属性

```php
<?php

class Panda {
    public $coat = 'fluffy';
}
```

从现在起你就这样声明类属性，不是吗？去吧，答应我！这只是更好的实现方法！

那些公共方法呢？我们也可以对它们应用`public`关键字，而且你应该这样做。让我们来看一个快速的例子。

## 示例 04：一个公共方法

```php
<?php

class Panda {
    public $coat = 'fluffy';

    public function getCoat() {
        return $this->coat;
    }
}
```

## 作用范围 (Scope)

我们将`public`关键字放在`function`关键字之前。这不会产生任何区别，但现在更清楚了该函数是公共的。

所以我们在这一节中没有学到任何新花样，对吧？至少我们找到了一种让代码更具描述性的方法。别担心！在下一节中我们将学习一些新东西。我保证！

## 私有 (Private)

在上一节中，我们使用`public`关键字将我们的类属性和方法标记为公共。让我们尝试将一个类属性标记为私有，好吗？

我们将从修改之前的示例开始。

### 示例 05：一个私有属性

```php
<?php

class Panda
{
    // 声明一个私有属性...
    private $coat = 'fluffy';

    // ... 以及一个公共方法。
    public function getCoat()
    {
        return $this->coat;
    }
}
```

在上面的示例中，你会注意到`$coat`属性现在已使用`private`关键字标记为私有。目前，我们将`getCoat()`方法保持为公共。

让我们尝试玩玩那个私有的`$coat`属性。我们只尝试把它输出出来。

## 作用范围 (Scope)

### 示例 06：访问私有属性

```php
<?php

// 创建一个新的熊猫。
$panda = new Panda;

// 尝试输出 coat 属性。
echo $panda->coat;
```

你认为执行上述代码时会发生什么？让我们来发现吧！

### 示例 07：输出

```
Fatal error: Cannot access private property Panda::$coat
```

由于我们的属性现在被标记为私有，因此我们无法从类外部访问它。如果我们决定这样做，将会收到致命错误（fatal error）。我们从我们肮脏的小手中保护了`$coat`属性！

你同样不能设置该属性！让我们试一下。

### 示例 08：设置私有属性

```php
<?php

// 创建一个新的熊猫。
$panda = new Panda;

// 尝试设置 coat 属性。
$panda->coat = 'slime';
```

让我们再次执行代码。

### 示例 09：输出

```
Fatal error: Cannot access private property Panda::$coat
```

我们收到了和尝试获取属性值时相同的错误信息。

让我们尝试访问那个公共方法。

## 19. 常量

在之前的章节中，我们学习了变量，以及它们如何被存储各种不同类型的信息。你可以给变量重新赋值一个新值，而 PHP 根本不在乎！

有时候，有些事情是不该被改变的。老人们总是倾向于穿米色色的衣服。政府会不断尝试挥霍你的钱。小熊猫在寒冷季节总是会变得兴奋。

## 定义常量

你的代码中有些值可能也不太想改变。例如，让我们用电视节目里那种摇摇晃晃的淡入出效果回到过去，重新看一遍`$pi`变量的赋值。

### 示例 01：一个 PI 变量

```php
$pi = 3.14159265359;
```

就在那儿。真美。

你认为 PI 的值将会发生改变吗？我的意思是，当然，聪明的穿白褂的专家们总可以计算出更多小数位的数字，但它在你的程序中改变的可能性大吗？

我深表怀疑。事实上，如果有人真的这么做了……

### 示例 02：将 PI 设置为 5

```php
$pi = 5;
```

……那么我们的周长计算就会陷入大麻烦。我们会看到初中数学老师正对我们皱眉，而我们可不想那样。

如果我们能把`$pi`变量锁定在某个特定值上，让它完全无法被改变，那就太好了。事实证明，我们需要的并不是变量。我们需要的是一种被称为"常量"的东西。

在类之外使用的常量（我喜欢称之为全局作用域）是通过一个特殊的函数定义的。让我们来看。

## 常量

### 示例 03：定义一个 PI 常量

```php
define('PI', 3.14159265359);
```

我们使用`define()`函数将 PI 常量设置为正确的值。如你所见，常量名是函数的第一个参数，而它的值是第二个。

> 你会注意到常量名是用全大写的。这不仅适用于 PI 常量。程序员的一个习惯是用大写字母写常量，并用下划线代替空格。例如：`THIS_IS_A_CONSTANT`。

让我们尝试使用我们的常量。它和变量非常相似，区别在于它不以`$`符号开头。让我们尝试执行我们的常量。

### 示例 04：使用 PI 常量

```php
// 定义我们的常量。
define('PI', 3.14159265359);

// 输出 PI 的值。
echo PI;
```

执行我们的代码段会得到结果：

### 示例 05：输出

```
3.14159265359
```

太棒了！这正是我们使用变量会得到的结果。现在让我们尝试重新定义该常量。例如：

### 示例 06：尝试重新定义常量

```php
// 重新定义我们的常量。
define('PI', 42);
```

你认为当我们尝试执行代码会发生什么？让我们试一下。

### 示例 07：输出

```
Notice: Constant PI already defined in <file> on line <number>
```

一个提示（notice）！它告诉我们已经定义了 PI，并且不能改变它的值。这个提示不会破坏我们的代码，但它会保护我们不意外改变常量的值。我们的周长计算是安全的。

常量的命名限制与变量相同，你可以定义任意数量的常量。常量最好的描述是"不可变的"，它们不会被改变。

## 类常量

上一节中定义的常量被认为是"全局的"，并且可以被应用程序的所有部分访问。有时，我们只需要供我们的类使用的常量。

例如，让我们创建一个简单的圆类。

### 示例 08：圆类

```php
<?php

class Circle {

    /**
     * PI 的值。
     *
     * @var float
     */
    private $pi = 3.14159265359;

    /**
     * 计算周长。
     *
     * @param float $diameter
     * @return float
     */
    public function circumference($diameter) {
        return $this->pi * $diameter;
    }
}
```

## 常量

### 示例 09：使用类

```php
$circle = new Circle();
echo $circle->circumference(10);
```

### 示例 10：属性

```php
<?php

class Circle {
    private $pi = 3.14159265359;

    public function circumference($diameter) {
        return $this->pi * $diameter;
    }
}
```

### 示例 11：定义常量

```php
class Circle {
    const PI = 3.14159265359;

    public function circumference($diameter) {
        return self::PI * $diameter;
    }
}
```

### 示例 12：访问常量

```php
class Circle {
    const PI = 3.14159265359;

    public function circumference($diameter) {
        return self::PI * $diameter;
    }
}
```

### 示例 13：通过实例访问

```php
$circle = new Circle();
echo $circle::PI;
```

### 示例 14：通过类名访问

```php
echo Circle::PI;
```

### 示例 15：self 引用

```php
return $diameter * self::PI;
```

### 示例 16：通过类定义访问

```php
return $diameter * Circle::PI;
```
