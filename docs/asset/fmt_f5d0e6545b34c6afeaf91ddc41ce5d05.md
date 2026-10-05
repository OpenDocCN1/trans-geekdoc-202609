
public $name = 'Hamish';

public static function beCute()

{

    $pandaName = $this->name;

    echo "$pandaName rolls around the snow.";

}

}

## 静态 (Statics)

没有实例可以进行操作。由于没有实例，`$this` 将解析为无内容。任何尝试使用它的行为都会导致 PHP 致命错误（fatal error）。

这意味着我们无法在类的静态方法中调用其他非静态方法，因为我们必须使用 `$this->otherMethod()` 来实现这一点。

这是否意味着我们的静态方法可以调用其他方法呢？嗯，并不完全。我们的静态方法可以调用其他的静态方法。这里有一个例子。

## 示例 10：链式调用静态方法

```php
class RedPanda {

    public static function eat() {

        return self::eatLeaves();

    }

    private static function eatLeaves() {

        return 'The Panda munches on some tasty leaves.';

    }

}
```

好了，让我们过一遍。我们有一个名为 `eat()` 的公共静态方法，它调用了 `eatLeaves()` 方法并返回结果。注意，`eatLeaves()` 方法是私有的（private），不能直接在类上调用。它只能在类的另一个方法内部被调用。

在上面的示例中，我们使用了 `self` 关键字。它用于指代自身或当前类。因此 `self::eatLeaves()` 意味着：请对该类的 `eatLeaves()` 方法进行静态调用。

当我们运行 `RedPanda::eat()` 时，我们得到了：

### 示例 11：输出

`The Panda munches on some tasty leaves.`

许多开发者使用这些公共静态方法来创建它们所所属类的实例。例如……

### 示例 12：工厂方法

```php
<?php

class RedPanda

{

    protected $name;

    public function __construct($name = null)

    {

        $this->name = $name;

    }

    public static function make()

    {

        return new self('Hamish');

    }

    public function getName()

    {

        return $this->name;

    }

}
```

在上面的示例中，我们的 `RedPanda` 类通过构造函数接收一个可选的 `$name` 参数。然后，它将受保护属性 `$name` 设置为你传递的值。公共函数 `getName()` 可用于访问熊猫的名字。

我们还有一个 `make()` 公共静态方法，它通过返回 `new self()` 来创建当前类的新实例并将其返回。它甚至将 `'Hamish'` 作为名称传递，因此我们可以使用 `RedPanda::make()` 快速创建一个新的 Hamish 熊猫实例。

> 我们提到过你不能从静态方法中访问实例方法，但反过来是完全允许的！例如，你可以在非静态方法中使用 `self::staticMethodHere()`，PHP 会完全没问题的。

## 晚期静态绑定 (Late Static Binding)

晚期静态绑定是 PHP 5.3 版本引入的一个特性。它的名字非常令人困惑，所以让我们用代码来演示。首先，我们需要两个类，并涉及一点继承。

### 示例 13：带有继承的静态方法

```php
<?php

class Panda

{

    public static function whoAmI()

{

        return self::getType();

    }

    public static function getType()

{

        return 'I am a Giant panda!';

    }

}

class RedPanda extends Panda

{

    public static function getType()

{

        return 'I am a Red panda!';

    }

}
```

这里有两个类。`Panda` 是我们的基类，代表大熊猫。`RedPanda` 继承自 `Panda`，代表红熊猫……显而易见。基类有一个名为 `getType()` 的静态方法，它告诉你是大熊猫。这个方法在 `RedPanda` 类中被重写（overridden），让你知道它是一只红熊猫。

我们可以在两个类上使用静态方法 `whoAmI()` 来找出我们拥有什么种类型的熊猫。我们现在调用它……

### 示例 14：我是谁？

```php
<?php

echo Panda::whoAmI() . PHP_EOL;

echo RedPanda::whoAmI();
```

运行这段代码后，我们得到了以下输出。

### 示例 15：输出

```
1 I am a Giant panda!

2 I am a Giant panda!
```

等等，为什么它们都是大熊猫？！我们在 `RedPanda` 类中重写了 `getType()` 方法，所以 PHP 不应该尊重继承关系吗？实际上，`self` 关键字只会引用基类。如果我们想使用晚期静态绑定，我们需要将 `self` 关键字替换为 `static`。让我们来看看这种转换。

## 示例 16：晚期静态绑定

```php
<?php

class Panda

{

    public static function whoAmI()

    {

        return static::getType();

    }

    public static function getType()

    {

        return 'I am a Giant panda';

    }

}

class RedPanda extends Panda

{

    public static function getType()

    {

        return 'I am a Red panda';

    }

}
```

你会注意到，我们所做的只是将 `self` 替换为 `static`。现在尝试执行一次代码。

### 示例 17：输出

```
1 I am a Giant panda!

2 I am a Red panda!
```

搞定！PHP 现在尊重了继承关系以及对 `getType()` 方法的重写。理解静态方法的概念是一件棘手的事。在我职业生涯的很晚之后，我才开始有效地使用它们。如果你觉得这一章有点困惑，我建议暂时先使用实例继续进行，等积累了更多经验后再回到这一章。至少，你已经知道如何通过关键字识别静态属性和方法。

## 异常 (Exceptions)

异常让我们知道程序运行没有达到预期。如果出现问题且我们的代码无法按预期继续，那么我们就使用异常来让用户知道。

## 抛出 (Throwing)

让我们创建一个函数。最好先确保如何使用它。

## 示例 01：熊猫喂食函数

```php
<?php

/**

 * 给熊猫喂一些食物。

 * @param string $food

 * @return void

 */

function feedPanda($food)

{

    echo "The panda eats {$food}";

}
```

做得好！现在我想起来了。这里有一个函数让我们给熊猫喂食，对吧？让我们给它喂一些苹果。

## 示例 02：给熊猫喂一个苹果

```php
<?php

feedPanda('apple');
```

让我们运行代码。

### 示例 03：输出

```
The panda eats the apple.
```

太棒了！那巧克力呢？你认为熊猫喜欢巧克力吗？不，因为巧克力对熊猫是有毒的。我们不想让它们吃巧克力。

嘿，我有一个主意。如果有人给熊猫喂巧克力，我们不要抛出一个异常怎么样？让我们试试看。

### 示例 04：抛出异常

```php
<?php

/**

 * 给熊猫喂一些食物。

 * @param string $food

 * @return void

 */

function feedPanda($food)

{

    if ($food === 'chocolate') {

        throw new Exception('NO CHOCOLATE FOR THE PANDA!');

    }

    echo "The panda eats {$food}";

}
```

首先，检查我们要给熊猫喂的食物是否等于字符串 `'chocolate'`。如果字符串匹配，我们需要使用异常。让我们孤立地看这段代码。

### 示例 05：抛出异常

```php
<?php

throw new Exception('NO CHOCOLATE FOR THE PANDA!');
```

完美，我们的熊猫是安全的。我保证熊猫不会受到伤害。让我们执行代码。

## 示例 06：给熊猫喂巧克力

```php
<?php

feedPanda('chocolate');
```

### 示例 07：输出

```
PHP Fatal error: Uncaught exception 'Exception' with message 'NO CHOCOLATE FOR THE PANDA!' in file:<line>
```

你会注意到，除了扩展 `Exception` 类之外，我们还定义了一个属性。你还记得 `protected`（保护级）是如何工作的吗？如果不记得，现在是检查范围（scope）章节进行复习的绝佳时机。

你会发现，`Exception` 类有一个名为 `$message` 的属性。这通常会被设置为我们在构造函数中传递给它的参数。由于该属性是 `protected` 的，我们是否可以在我们的对象类中重写它的值？这意味着我们在定义扩展时，不再需要传递消息了。

让我们抛出我们的 `PandaException` 吧。

## 示例 09：抛出 `PandaException`

```php
<?php

/**

 * 给熊猫喂一些食物。

 * @param string $food

 * @return void

 */

function feedPanda($food) {

    if ($food === 'chocolate') {

        throw new PandaException();

    }

echo "The panda eats {$food}";

}
```

我们在没有传递任何参数的情况下抛出了 `PandaException`。让我们看看给函数传递一些巧克力时会发生什么。

## 示例 10：输出

```
PHP error: Uncaught exception 'PandaException' with message 'NO CHOCOLATE\nFOR THE PANDA!' in <file>:<line>
```

太棒了！我们的异常现在更具描述性，而且仍然带有我们想要的消息。让我们再进一步，将我们的单个异常扩展为两个。

## 示例 11：两个异常

```php
<?php
class PandaChocolateException extends Exception
{
    protected $message = 'NO CHOCOLATE FOR THE PANDA!';
}
class PandaChilliException extends Exception
{
    protected $message = 'NO CHILLI FOR THE PANDA. OUCH!';
}
```

现在我们有两个异常：`PandaChocolateException` 和 `PandaChilliException`，分别对应熊猫脆弱的消化系统难以处理的两种食物。

我们可以抛出的异常数量上没有限制，所以让我们继续修改我们的代码吧。

## 示例 12：抛出两个异常

```php
<?php
/**
 * 给熊猫喂一些食物。
 * @param string $food
 * @return void
 */
function feedPanda($food) {
    // 根据食物进行分支。
    switch ($food) {
        // 处理巧克力。
        case 'chocolate':
            throw new PandaChocolateException;
        // 处理辣椒。
        case 'chilli':
            throw new PandaChilliException;
    }
}
```

## 异常

```
// 处理其他食物。
default:
    echo "The panda eats the {$food}";
}
```

在这里，我们使用了 `switch` 来处理不同类型的食物。为什么要用 `switch` 呢？这是一个确保你学会了它们如何工作的绝佳理由。

在 `switch` 部分，我们发现应该使用 `break` 关键字来停止应用程序的执行。等一下，我们在上面的 `switch` 语句中没有使用 `break` 关键字。你认为这是为什么呢？

嗯，异常也会停止执行线程，所以我们不需要 `break` 语句了。让我们尝试触发 `PandaChilliException` 吧，好吗？

### 示例 13：输出

+ 1 Fatal error: Uncaught exception 'PandaChilliException' with message 'NO CHILLI FOR THE PANDA. OUCH!' in <file> on line <line>

太棒了！看起来我们已经是抛出异常的大师了。问题是，这比仅仅使用 PHP 函数如 `exit()` 或 `die()` 来停止执行要好在哪里呢？我们能获得什么？嗯，我们还没有完全掌握！

> `exit()` 或 `die()` 函数可以终止 PHP 应用程序。如果你传递一个字符串作为参数，它将在退出前显示该字符串。非常有用！

## Try & Catch（尝试与捕获）

现在我们学会了如何抛出异常，是时候学习如何捕获它们了。戴上你的棒球手套。

如果我们的代码抛出了异常，我们可以使用 `try` 和 `catch` 来妥善处理它们。这样，我们的代码就可以恢复，并捕捉它真正的终点。

让我们考虑上一个部分的代码片段。

## 示例 14：再次抛出异常

```php
<?php
/**
 * 给熊猫喂一些食物。
 * @param string $food
 * @return void
 */
function feedPanda($food) {
    // 根据食物进行分支。
    switch ($food) {
        // 处理巧克力。
        case 'chocolate':
            throw new PandaChocolateException;
        // 处理辣椒。
        case 'chilli':
            throw new PandaChilliException;
        // 处理其他食物。
        default:
            echo "The panda eats the {$food}";
    }
}
```

让我们从小开始。让我们处理熊猫被喂了巧克力的情况。这是我们可能实现这一点的方法。

## 示例 15：捕获异常

```php
<?php
// 设置食物类型。
$food = 'chocolate';
try {
    feedPanda($food);
} catch (PandaChocolateException $exception) {
    echo 'That was a close one! No chocolate for the panda.';
}
```

这里有一些新语法，不是吗？让我们把它从代码中提取出来以便清晰。

### 示例 16：捕获任何异常

```php
<?php
try {
    // 可能会触发异常的代码。
} catch (Exception $exception) {
    // 处理异常的代码。
}
```

### 示例 22：数据库连接

```php
try {
    $database->connect('username', 'password');
} catch (DatabaseException $databaseException) {
    echo 'Unable to connect to the database.';
    die();
} 
finally {
    $database->fetchRecords();
}
```

我们将连接数据库的代码封装在一个 `try` 块中。我们无法确定用户名和密码是否正确，如果与事实不符，就会抛出一个异常。

为了防止此异常以一种糟糕的方式停止代码运行，我们捕获该异常，并带有有用的错误消息退出应用程序。

如果连接数据库成功，我们可以使用它来获取我们需要的记录，我们的应用程序就可以正常继续运行。
