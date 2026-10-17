
> 如果你想在`foreach`循环期间更改元素的值，只需使用`key => value`格式，并访问`key => value`

这是我最常用的循环。我每天大约使用它 23,543 次。大概这么多！这是因为我喜欢处理数组。

在之前的章节中，我们发现了如何为数组提供自己的键。你可能想在循环中访问数组的键及其值。很好，别担心，哥们！PHP 可以为你做到这些。让我们来看看语法。

### 示例 13：带有键的 `foreach` 循环

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

这一次，我们有一个带有自定义键的数组。我们对键和值都使用了字符串，但它们可以是任何内容。我们没有简单地为每次循环迭代分配新变量，而是提供了一个由`=>`符号分隔的临时键和值占位符。

让我们看看每次循环迭代这两个变量的值。

## 循环

- 第一次迭代（`$position = 'first'`）（`$panda = 'Lushui'`）
- 第二次迭代（`$position = 'second'`）（`$panda = 'Pali'`）
- 第三次迭代（`$position = 'third'`）（`$panda = 'Jasmina'`）

我们可以使用这些临时变量来完成我们的任何疯狂的小计划。

我们完全可以随心所欲。

值得注意的是，数组元素的副本会被传递到`foreach`循环块中。这意味着在循环内部对变量的任何更改在循环完成后将不会反映。

> 如果你想在`foreach`循环期间更改元素的值，只需使用`key => value`格式，并访问`key => value`

这是我最常用的循环。我每天大约使用它 23,543 次。大概这么多！这是因为我喜欢处理数组。

在之前的章节中，我们发现了如何为数组提供自己的键。你可能想在循环中访问数组的键及其值。很好，别担心，哥们！PHP 可以为你做到这些。让我们来看看语法。

## 控制

当你发现某段代码在应用程序中重复多次时，它是一个良好的指标，说明你应该使用函数代替。

### 示例 14：跳出循环

```php
<?php
// 创建一个 pandas 数组。
$pandas = ['Lushui', 'Pali', 'Jasmina'];

];
    'first' => 'Lushui',
    'second' => 'Pali',
    'third' => 'Jasmina'
];

// 遍历我们的数组。
foreach ($pandas as $panda) {
    echo "You're the {$position} panda, {$panda}!\n";
    break;
}
```

正如你所看到的，一旦 PHP 遇到`break`语句，它将退出循环并进入下次迭代（等等，“跳过”和“继续”混在一起了）。

让我们来看一个例子。

### 示例 15：继续迭代

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
    if ($position == 'second') {
        // 跳过迭代。
        continue;
    }
    // 输出。
    echo "You are the {$position} panda, {$panda}!\n";
}
```

看看循环。我们有一个`if`语句，如果`$position`数组键等于字符串`'second'`，它将继续下一次迭代。让我们来看看结果，好吗？

### 示例 16：输出

```
You are the first panda, Lushui!
You are the third panda, Jasmina!
```

正如你所看到的，循环的第二次迭代遇到了`continue`关键字，跳过了`echo`语句并进入第三次迭代。

在下一个章节中，我们将学习函数。它们将帮助为代码提供一些结构。

## 13. 函数

函数是组织应用程序的一种极佳方法。它们可以用于避免代码重复。当你发现某段代码在应用程序中重复多次时，它是一个良好的指标，说明你应该使用函数代替。

你可以把函数想象成小工厂机器。你的变量（小盒子）进入机器一侧的插槽，齿轮旋转，产生咯吱声，然后其他东西从另一侧出来。

## 基础用法

让我们来看一个函数。你已经跟我看了很多章节，我确定你知道它是如何工作的！

### 示例 01：我的第一个函数

```php
<?php
function echoSong() {
    echo "So take the photographs, and still frames in your mind.\n";
    echo "Hang it on a shelf in good health and good time.\n";
    echo "Tattoos and memories and dead skin on trial.\n"
    echo "For what it's worth, it was worth all the while.\n";
}

echoSong();
```

对，这些都是全新的！在开始解释之前，让我们先执行一下代码。我们收到的输出是什么？

### 示例 02：输出

- 1 所以拍下照片，并在脑海中定格这些画面。
- 2 在健康和美好的时光里，把它们挂在架子上。
- 3 纹身、记忆和老掉的皮肤正在接受审判。
- 4 无论值多少几何，这一切都是值得的。

我们看到了一首经典歌曲的歌词。如果你能说出艺术家和歌名，会加分。朋友们，请在明信片上写下答案！实际上你也可以直接发推特给我！

我们应该看一眼函数的定义。在函数（小机器）被使用之前，我们必须告诉 PHP 它是做什么的。这就是我们的定义。这里是我要说的部分。

### 示例 03：函数定义

```php
<?php
function echoSong() {
    echo "So take the photographs, and still frames in your mind.\n";
    echo "Hang it on a shelf in good health and good time.\n";
    echo "Tattoos and memories and dead skin on trial.\n";
    echo "For what it's worth, it was worth all the while.\n";
}
```

我们知道`echo`是做什么的，所以为了清晰起见，让我们去掉函数定义的体。

### 示例 04：函数框架

```php
<?php
function echoSong() {
    // 在此处执行操作。
}
```

示例中的第一行被称为方法签名（method signature）。它描述了方法及其它的形状。对于这样一个简单的函数，我们真正拥有的只有一个名字。我们用关键字`function`开始函数定义，后面跟着我们正在定义的函数名。函数的命名规则与变量相似，因此为了保持一致性，我们将使用驼峰命名法（camelCase）。

## 函数

接下来，我们有一对圆括号。稍后我们将学习如何给函数传递参数，这些括号将会变得更有趣，但现在让它们保持为空！最后，我们有一个大括号括起来块。这与我们在前面的章节中看到的循环和分支类似。

我们的代码段正在让 PHP 知道，当我们调用`echoSong()`函数时，它应该打印出一首经典歌曲的歌词，而你正因为忘记了歌名而懊恼。

现在我们已经告诉了 PHP 关于我们的函数，就可以使用它了。这就是这行代码的作用。

### 示例 05：调用函数

```php
<?php
echo echoSong();
```

我们可以通过提供函数名和一组圆括号来执行函数。我们定义的函数内部的块将被执行，我们的歌词将显示出来。

我们可以根据需要任意多次执行我们的函数。这意味着我们创建的代码段现在可以在整个应用程序中复用。我们正在提高效率。

这里有一个多次调用函数的示例。

### 示例 06：多次调用函数

```php
<?php
function echoSong() {
    echo "So take the photographs, and still frames in your mind.\n";
    echo "Hang it on a shelf in good health and good time.\n";
    echo "Tattoos and memories and dead skin on trial.\n";
    echo "For what it's worth, it was worth all the while.\n";
}
echoSong();
echoSong();
echoSong();
```

让我们执行代码段以查看输出。

### 示例 07：输出

- 1 所以拍下照片，并在脑海中定格这些画面。
- 2 在健康和美好的时光里，把它们挂在架子上。
- 3 纹身、记忆和老掉的皮肤正在接受审判。
- 4 无论值多少几何，这一切都是值得的。
- 5 所以拍下照片，并在脑海中定格这些画面。
- 6 在健康和美好的时光里，把它们挂在架子上。
- 7 纹身、记忆和老掉的皮肤正在接受审判。
- 8 无论值多少几何，这一切都是值得的。
- 9 所以拍下照片，并在脑海中定格这些画面。
- 10 在健康和美好的时光里，把它们挂在架子上。
- 11 纹身、记忆和老掉的皮肤正在接受审判。
- 12 无论值多少几何，这一切都是值得的。

## 函数

### 示例 16：输出

- 1 欢迎来到 PHP Pandas，读者！

做得好！我们收到了热烈的欢迎。我们为什么不尝试一些不同的值呢？这将证明该函数现在是动态的。

### 示例 17：不同的参数

```php
1 <?php
2 // 欢迎某人！
3 function welcome($name) {
4 echo "Welcome to PHP Pandas, {$name}!\n";
5
6 }
7
8 // 调用 welcome 函数。 // 就是你！
9 welcome('reader');
10 welcome('Captain Jon Morgan'); // 这是一个很棒的家伙！
11 welcome('Arno Dorian'); // 万事皆虚...
12 welcome(64.54); // 那不是名字！
```

在这里，我们调用了四次函数。每次，我们都提供了一个不同的值。第四个值是一个浮点数（float），这证明了向我们的函数提供什么类型的数据并不重要。我还在`echo`语句中添加了一个换行符（`\n`）以让它看起来更清晰。让我们执行这段代码段。

### 示例 18：输出

```
- 1 Welcome to PHP Pandas, reader!
2 Welcome to PHP Pandas, Captain Jon Morgan!
3 Welcome to PHP Pandas, Arno Dorian!
4 Welcome to PHP Pandas, 64.54!
```

我们看到函数的结果每次都发生变化，取决于我们提供的输入。这让我们对函数有了更多的控制权，并能够对不同的值做出不同的反应。正如你从第四个值看到的，传递到函数中的数据类型是什么并不重要，我们的代码运行得很愉快。

我们并不局限于一个参数。我们可以在函数中使用尽可能多的参数。让我们充分滥用一下这个特性吧，好吗？让我们创建一个带有……整整五个参数的函数！我们是多么叛逆啊！

### 示例 19：多个参数

```php
<?php
// 累加一些值。
function addify($first, $second, $third, $fourth, $fifth) {
    return $first + $second + $third + $fourth + $fifth;
}

// 调用 addify。
echo addify(1, 1, 2, 3, 5);
```

我们写了一个函数，它将接受 5 个值作为参数，并返回它们的和。使用我们的`addify()`函数，顺序并不重要，但值得注意的是，你提供的参数顺序与函数签名中的占位符是匹配的。在上面的示例中，`$first`的值将是 1，`$fifth`的值将是 5。

五个参数很棒，但感觉对于像`addify()`这样的函数不应该有限制。我们应该能够累加任意数量的参数。我刚刚得了一个主意！让我们使用`func_get_args()`。这是一个特殊的 PHP 函数，它将返回一个包含所有参数传递给函数的数值数组。更棒的是，我们不需要定义任何参数就可以工作。这里有一个例子。

### 示例 20：无限参数

```php
<?php
function welcome() {
    // 获取所有函数参数。
    $names = func_get_args();

    // 遍历名称并欢迎他们。
    foreach ($names as $name) {
        echo "Welcome, $name!\n";
    }
}
```

我们在自己的函数内部使用了另一个名为`func_get_args()`的函数。这意味着，函数也可以使用其他函数！当我们使用`func_get_args()`时，我们以索引数组的形式接收传递给函数的任何参数。我们甚至不需要为它们创建占位符变量。这意味着上面的函数可以接受任意数量的参数。这里有一个 true 例：

### 示例 21：大量参数

```php
welcome('Dayle', 'James', 'Andrea', 'Ben', 'Mateusz');
```

我们使用五个名字调用该函数，并收到了以下响应。

### 示例 22：输出

```
Welcome, Dayle!
Welcome, James!
Welcome, Andrea!
Welcome, Ben!
Welcome, Mateusz!
```

所有五个人都收到了欢迎。如果我们改变参数的数量会发生什么？让我们尝试用两个名字。

### 示例 23：两个参数

```php
<?php
welcome('Anthony', 'Alex');
```

我们的函数不在乎。从`func_get_args()`返回的数组现在将包含两个值，循环将正常继续。

### 示例 24：输出

```
Welcome, Anthony!
Welcome, Alex!
```

## 类型提示（Type Hinting）

在本章稍早些时候，我们提到了那些函数。即接收特定参数的函数。我确定你已经见过它们。那么，如果你把一个数组放在参数所在的位置会发生什么呢？你认为它能工作吗？它会造成一个巨大的混乱！

你说得对！我们会得到到处都是错误。有时候，函数只是为了接收特定类型而设计的。如果我们想确保参数是某种类型，我们可以使用名为“类型提示”（type-hinting）的技术。让我们来看看实际操作。

### 示例 25：对数组进行类型提示

```php
<?php
// 向一组人打招呼。
function sayHello($names) {
    foreach ($names as $name) {
        echo "Hello, $name!\n";
    }
}
sayHello(['Katie', 'Corissa', 'Lucy']);
```

我们得到了另一个名为`sayHello()`的函数。在这个例子中，我们遇到的唯一情况是输入`$names`在参数占位符之前被类型提示为数组（array）。如果我们执行代码，就会得到预期的输出。

### 示例 26：输出

```
Hello, Katie!
Hello, Corissa!
Hello, Lucy!
```

让我们改变函数调用以传递一个数字。我们是不是很调皮？

### 示例 27：调皮

```php
<?php
sayHello(4);
```

现在发生了什么？

### 示例 28：输出

```
PHP fatal error: Argument 1 passed to sayHello() must be of the type array, integer given.
```

有趣！PHP 现在对我们发火了。有了类型提示，PHP 将仅允许将数组传递给`sayHello()`函数。如果我们传递其他任何内容，就会得到一个致命错误。`catchable`部分意味着我们可以使用`try`块来处理此错误，但我们稍后会说。类型提示非常有用，不是吗？很好，你可以类型提示`string`、`boolean`或`float`等值。这很痛苦，但你必须处理它。这看起来很奇怪，不是吗？很好，你可以类型提示参数，不是吗？好，你将发现你可以类型提示类（classes），但我们会在学习类后对其进行详细解释。一步一步来，小学徒。

## 14. 闭包（Closures）

我们要来点 closure 吗？好的，那个很糟糕。虽然这个词很奇怪，不是吗？闭包是特殊的函数。这些类型的函数没有名字。就像武士一样！

## 谁需要名字？

### 示例 01：闭包

```php
<?php
function () {
    return 'bar';
}
```

太棒了！等等。如何调用一个没有名字的函数？由于闭包是特殊的，我们可以像赋值简单值一样赋值它们。让我们来看看语法。

### 示例 02：将闭包赋值给变量
