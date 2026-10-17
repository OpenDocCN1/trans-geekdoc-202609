
这种对字符串的封装实际上非常有用。如果我们的代码某部分要求使用的变量必须是数组，那么我们只需要将其转换为数组以使值被封装。如果我们尝试将浮点数值转换为数组会发生什么？我想它也会被封装，我们要检查一下吗？

**示例 11：将浮点数转换为数组。**

```php
<?php
$panda = 1.98765;

// 转换为数组。
$panda = (array) $panda;

// 转储结果。
var_dump($panda);
```

**示例 12：输出。**

```
array(1) {
  [0]->float(1.98765)
}
```

太棒了！正如我们预期的，我们的浮点数也被封装在数组中了。不要害怕使用强制转换将你的值转换为正确的数据类型。毕竟，它们是为了为你服务的！

在下一章节中，我们将学习更多关于注释的内容。

# 示例 09：带有元数据的文档块

```php
1 <?php
2 
3 /**
 * pandas 的描述。
 *
 * @var string
 */
$ $pandas = 'awesome!';
```

我们可以使用带有 `@` 符号前缀的属性为文档块提供额外的元数据。与这些属性相关的参数放在同一行，多个参数之间可以用空格分隔。

通过提供的 `@var` 属性，我们的文档系统知道 `$panda` 变量包含一个字符串值，并可以显示此信息帮助他人进一步了解代码。

不要太担心这些文档块，我们目前会坚持使用其他注释。在稍后的章节中，我将开始介绍它们。我只是想让你们意识到它们的存在，以万一你们在其他地方看到它们。

在下一章节中，我们将查看分支（forks），所以你最好现在去翻翻你的餐具抽屉了！

## 11. 分支 (Forks)

现在，你的应用程序按照你在源文件中放置的行顺序执行。然而，生活并不是那样的不是吗？我们不会盲目地听从命令。我们会根据周围的信息做出决定。

在 PHP 中，我们的信息存储在变量中。为了根据这些变量的值做出决定，我们可以使用分支。它们分叉应用程序的流，根据比较的结果改变其路径。在 PHP 中，我们可以将其称为 `if` 语句。

## If

让我们来看一个基础的 `if` 语句。认为用示例开头可能是最好的，你觉得呢？

**示例 01：if 语句。**

```php
<?php
if (true) {
  echo 'Yey, panda time!';
}
```

一个语句总是以 `if` 开始。嗯，我相信你已经想通了。我们有两个部分。`{ }` 括号内的代码是条件。如果条件求值为 `true` 值，那么 `{ }` 大括号内的代码将被执行。

让我们执行这段代码看看会发生什么。

**示例 02：输出。**

```
Yey, panda time!
```

太棒了！熊猫时间总是很棒。大括号内的 `echo` 语句被执行，是因为条件求值为 `true`。嗯，条件是 `true`，但它仍然求值为布尔值 `true`。

看看如果我们把条件更改为求值为布尔 `false` 的值会发生什么。这个如何？

### 示例 03：另一个 if 语句

```php
<?php
if (false) {
    echo 'Yey, panda time!';
}
```

让我们再次执行一次代码。

### 示例 04：输出

```
(nothing)
```

好了，什么都没有发生。当我们的条件求值为 `false` 时，我们大括号内的代码不会被执行。

你可能会问自己这有什么用？为什么我们不能在需要时直接添加或删除行代码呢？嗯，因为仅仅提供一个布尔值并不能让 `if` 语句变得有用。它只是解释条件求值为布尔的一种整洁方法。

考虑以下变体。有一个细微的差别，你能发现吗？

### 示例 05：比较字符串

```php
$panda = 'Lushui';
if ($panda == 'Lushui') {
    echo 'Yey, panda time!';
}
```

这次，我们正在将字符串变量的值与另一个字符串进行比较。`echo` 语句将再次执行。这是因为 `$panda` 确实等于 `'Lushui'`。这意味着条件再次求值为 `true`。

让我们更改 `$panda` 的值看看会发生什么。

### 示例 06：比较不同的字符串

```php
$panda = 'Pali';
if ($panda == 'Lushui') {
    echo 'Yey, panda time!';
}
```

我们再次执行一次代码。

### 示例 07：输出

```
(nothing)
```

好了。这次 `$panda` 并不等于 `'Lushui'`。这意味着条件将等同于 `false`，大括号内的代码（实际上，我们称之为“代码块”）将不会被执行。

现在，我们正在控制 `$panda` 的值，但如果 `$panda` 被设置为用户输入的结果会怎样？如果我们把 `$panda` 设置为用户在应用程序中输入的任何内容。也许它可能是从大型应用程序的其他部分获取的数据。这些数据能够改变我们应用程序的流，允许在某些条件下执行代码段。这就是编程变得令人兴奋的时候。

条件内的任何语句都将被求值。在移动到下一节之前，尽管去实验一会儿语句。它将是你编程新职业中一个非常重要的一部分。

## Else

Else！Else？！抱歉。它听起来就像肥皂剧里那些戏剧性的时刻。你知道的，当有人用“否则（or else!）”威胁别人时。实际上，`else` 只是 `if` 语句的另一个扩展。我们要仔细看看吗？

### 示例 08：带有 else 的 if

```php
$panda = 'Pali';
if ($panda == 'Lushui') {
    echo 'Yey, Lushui time!';
} else {
    echo 'Oh hey there Pali!';
}
```

我们语句的 `else` 部分功能方式与 `if` 部分类似。唯一的区别是 `else` 不需要条件。如果条件求值为 `false`，则大括号内的代码将被执行。

（注：原文后续包含大量重复的 OCR 逻辑错误描述，译文已根据核心核心逻辑进行处理）

### 示例 13：带有多个 case 的 switch 块

```php
<?php
$panda = _SOMETHING_;
switch ($panda) {
    case 'Lushui':
        echo 'Yey, Lushui time!';
    case 'Pali':
        echo 'Oh there Pali!';
    case 'Jasmina':
        echo 'Looking pretty Jasmina!';
}
```

在这里我们可以看到多个 `case` 语句。但要小心！代码段中有一个陷阱。你会发现，无论匹配哪个 `case` 语句，下方其他 `case` 语句的代码都会被执行。如果我们希望执行它们，这可能会非常有用。

这意味着如果 `$panda` 的值为 `'Lushui'`，那么所有三个 `echo` 语句都将被执行，但现在我们并没有！那么，我们如何确保只执行一个 `echo` 语句呢？很简单！我们需要一个 `break`，或者三个！

### 示例 14：break 语句

```php
<?php
$panda = _SOMETHING_;
switch ($panda) {
    case 'Lushui':
        echo 'Yey, Lushui time!';
        break;
    case 'Pali':
        echo 'Oh there Pali!';
        break;
case 'Jasmina':
    echo 'Looking pretty Jasmina!';
    break;
}
```

如果我们在 `echo` 语句之后的行放置一个 `break` 语句，就可以在该点停止 `switch` 语句的执行。执行流将跳出 `switch` 并在最后的闭合括号 `}` 之后继续执行。

这些 `break` 语句的效果与 `elseif` 和 `else` 语句类似。`break` 是一个会中断当前执行分支执行的关键字。这是一个非常值得记住的用法！

我们的 `switch` 语句还缺少最后一点东西。目前，它类似于一个末尾没有 `else` 的 `elseif` 语句。那么，我们如何实现带有 `else` 的功能呢？很简单，我们只需要提供一个默认值（default）即可！

让我们修改一下示例吧？

### 示例 15：default

```php
<?php
$panda = _SOMETHING_;
switch ($panda) {
    case 'Lushui':
        echo 'Yey, Lushui time!';
        break;
    case 'Pali':
        echo 'Oh hey there Pali!';
        break;
    case 'Jasmina':
        echo 'Looking pretty Jasmina!';
        break;
    default:
        echo 'Sorry, who are you?';
}
```

`default` 语句的工作方式与 `case` 语句类似，不同之处在于不需要提供比较值。如果其他 `case` 语句都没有匹配，将执行 `default` 下方的代码。

`default` 语句不需要 `break`，因为它是 `switch` 语句的最后部分。不过，如果你为了清晰起见添加它，也不会产生任何功能上的区别。

在下一章中我们将学习迭代器。期待一下！来，我挑战你！

## 12. 循环

当你拥有一个值集合时，迭代器是非常有用的。有时，“循环（loop）”是描述迭代器更好的词汇。我们将使用这些技术允许一段代码反复运行，直到（或只要）满足某个条件。

有些循环就像是在说“敲门直到有人回答”，而另一些则更像是“数数我地下室里埋的每一个体”。让我们仔细看看这些结构在 PHP 中是如何实现的。

## While

`while` 循环会在提供的条件为真（true）时持续运行代码段。让我们使用计数器构造一个示例。

**示例 01：while 循环。**

```php
<?php
// 将熊猫计数器设置为 0。
$pandas = 0;
// 当 $pandas 小于 50 时迭代。
while ($pandas < 50) {
    // 输出熊猫管家的数量。
    echo "We have {$pandas} panda butlers!\n";
    // 计数器加1。
    $pandas++;
}
```

我们将计数器 `$pandas` 设置为 0。现在我们可以开始创建第一个循环了。万岁！我们需要用 `while` 单词开始 `while` 循环，后面跟着 `()` 圆括号内的条件，最后是一个包含在 `{}` 大括号内的代码块。

`while` 循环的形式与 `if` 语句相似。区别在于，当条件等于真时，`{}` 部分的代码将不断反复一次地执行。

让我们执行代码看看发生了什么，我很期待见到这些熊猫。

**示例 02：输出。**

```text
1 We have 0 panda butlers!
2 We have 1 panda butlers!
3 We have 2 panda butlers!
4 We have 3 panda butlers!
5 We have 4 panda butlers!
6 We have 5 panda butlers!
7 ... ...
8 We have 41 panda butlers!
9 We have 42 panda butlers!
10 We have 43 panda butlers!
11 We have 44 panda butlers!
12 We have 45 panda butlers!
13 We have 46 panda butlers!
14 We have 47 panda butlers!
15 We have 48 panda butlers!
16 We have 49 panda butlers!
```

## Do While

`do-while` 循环与 `while` 循环非常相似，除了一个微小的区别。让我们来看它。

**示例 04：do-while 循环。**

```php
<?php
// 将熊猫计数器设置为 0。
$pandas = 0;
// ...
do {
    // 输出熊猫管家的数量。
    echo "We have {$pandas} panda butlers!\n";
    // 计数器加1。
    $pandas++;
} while ($pandas < 50);
```

## For

是时候看看 `for` 循环了。这个解释起来有点复杂，所以我们最好从一个示例开始。

**示例 05：for 循环。**

```php
<?php
// 迭代 50 次。
for ($i = 0; $i < 50; $i++) {
    // 输出熊猫管家的数量。
    echo "We have {$i} panda butlers!\n";
}
```

### 示例 07：初始化计数器

```php
<?php
$i = 0;
```

在这个实例中，我们设置了一个名为 `$i` 的变量为 0。通常情况下，我鼓励你为变量使用描述性的名称，但 `$i` 某种程度上是一种传统。事实上，在构建 `for` 循环期间使用的大多数变量都是单字母，而 `$i` 似乎是所有字母中最常见的。老实说，我不确定为什么是这样，但这是一个自古以来的传统。如果阅读此书的读者恰好知道这个传统源于哪里，请告诉我！我会更新这本书。我最乐观的推测是 `$i` 代表迭代计数器（iteration counter）！

接下来，我们有我们的条件。

### 示例 08：设置条件

```php
<?php
$i < 50;
```

这是我们在之前的章节中已经熟悉的循环部分。我们正在告诉 PHP，只要 `$i` 的值小于 50，就继续执行我们的代码块。

最后，我们有一个调整数值的语句。

### 示例 09：修改计数器

```php
<?php
$i++;
```

我们可以用它来增加我们的计数器变量。该语句会在循环的每次迭代中执行。这意味着我们 `for` 循环的第一行可以表示为以下格式。

### 示例 10：语法

```php
<?php
for (_BEFORE; _CONDITION; _AFTER_EACH_)
```

第一部分在每次循环执行之前执行。第二个语句（或条件）在每次循环执行时进行评估。最后，第三个语句在每次循环迭代后执行。

正如你从示例中较少的行数看到的，当涉及某种形式的计数器时，`for` 循环是实现循环的一种极佳方法。

> 不要忘记！你不局限于纯粹递增计数器。你可以通过更大的步长来增加计数器，甚至对其进行乘法！

## Foreach

`foreach` 循环在与可迭代类型（如数组）结合使用时非常有用。此循环的迭代次数由我们数组中项的数量决定。让我们来看一个例子。

### 示例 11：foreach 循环

```php
<?php
// 创建一个 pandas 数组。
$pandas = ['Lushui', 'Pali', 'Jasmina'];

// 遍历我们的 panda 数组。
foreach ($pandas as $panda) {
    echo "Hello there {$panda}!\n";
}
```

我们创建了一个小小的 pandas 数组。我们已经是数组的大师了，不是吗？这对我们来说完全没有问题。让我们关注下一行。

### 示例 12：遍历数组

```php
<?php
foreach ($pandas as $panda)
```

循环以 `foreach` 关键字开始。抱歉，剧透警告！我说的对吧？接下来是一组 `( )` 括号。在括号内，我们有两个由 `as` 关键字分隔的变量。我们正在告诉 PHP 遍历数组中的所有元素，并在每次迭代中将 `$panda` 赋值给当前数组元素。

循环的最后部分当然是大括号内的代码块。我们现在对这些代码块已经非常熟悉了。它们包含了随着循环迭代而执行的代码。

在循环的第一次迭代中，`$panda` 将被设置为 `'Lushui'`，在下一次迭代中，`$panda` 将被设置为 `'Pali'`，在最后一次迭代中，`$panda` 将被设置为 `'Jasmina'`。

这是我最常用的循环。我每天大约使用它 23,543 次。大概这么多！这是因为我喜欢处理数组。

在之前的章节中，我们发现了如何为数组提供自己的键（keys）。你可能想在循环中访问数组的键及其值。很好，别担心，哥们！PHP 可以为你做到这些。让我们来看看语法。

### 示例 13：带有键的 foreach 循环

```php
<?php
// 创建一个 pandas 数组。
$pandas = [
    'first' => 'Lushui',
    'second' => 'Pali',
    'third' => 'Jasmina'
];

// 遍历我们的数组。
foreach ($pandas as $position => $panda) {
    echo "You're the {$position} panda, {$panda}!\n";
}
```

这一次，我们有一个带有自定义键的数组。我们对键和值都使用了字符串，但它们可以是任何内容。我们没有简单地为每次循环迭代分配新变量，而是提供了一个由 `=>` 符号分隔的临时键和值占位符。

让我们看看每次循环迭代这两个变量的值。

## 循环

- 第一次迭代 (`$position = 'first'`) (`$panda = 'Lushui'`)

- 第二次迭代 (`$position = 'second'`) (`$panda = 'Pali'`)

- 第三次迭代 (`$position = 'third'`) (`$panda = 'Jasmina'`)

我们可以使用这些临时变量来完成我们的任何疯狂的小计划。

我们完全可以随心所欲。

值得注意的是，数组元素的副本会被传递到 `foreach` 循环块中。这意味着在循环内部对变量的任何更改在循环完成后将不会反映。
