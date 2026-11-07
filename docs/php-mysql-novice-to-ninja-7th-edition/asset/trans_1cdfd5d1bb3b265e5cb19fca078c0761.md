
你可以使用 `while` 循环来创建一个计数器，其结果与 `for` 循环类似。

**示例：[PHP-WhileCount](https://github.com/spbooks/phpmysql7/tree/PHP-WhileCount)**

```
$count = 1;
while ($count <= 10) {
  echo $count . ' ';
  ++$count;
}
```

这与 `for` 循环的工作方式完全相同，你会注意到很多相同的语句只是位置不同。这段代码看起来可能有点吓人，我知道，但让我逐行为你讲解：
*   `$count = 1;`. 第一行创建了一个名为 `$count` 的变量并将其值赋为 `1`。
*   `while ($count <= 10)`. 第二行是 `while` 循环的开始，其条件是 `$count` 的值小于或等于 (`<=`) 10。
*   `{`. 开括号标记了 `while` 循环条件代码块的开始。这段条件代码通常被称为循环的 **主体**，只要条件成立，就会一遍又一遍地执行。
*   `echo $count . ' ';`. 这行代码只是输出 `$count` 的值，后面跟着一个空格。
*   `++$count;`. 第四行将 `1` 加到 `$count` 的值上。`++$count` 是 `$count = $count + 1` 的简写。`$count++` 在这里也有效！`++` 的位置可能很重要，但在这种情况下无关紧要。如果 `++` 在变量名之前，计数器会在读取值之前递增。当 `$count` 为零时，代码 `echo ++$count;` 会打印 `1`，而 `echo $count++;` 会打印 `0`。使用 `++` 时要小心，将其放在错误的位置可能会导致错误。
*   `}`. 闭括号标记了 `while` 循环主体的结束。

下面是这段代码执行时发生的情况。第一次检查条件时，`$count` 的值为 `1`，因此条件肯定为真。`$count` 的值 `1` 被输出，并且 `$count` 被赋予新的值 `2`。第二次检查条件时条件仍然为真，因此值 `2` 被输出并分配新的值 `3`。此过程继续，输出值 `3`、`4`、`5`、`6`、`7`、`8`、`9` 和 `10`。最后，`$count` 被赋值为 `11`，条件被判定为假，从而结束循环。

代码的净结果如下图所示。

![while 循环代码的净结果](Images/count10.php_example.png)

`while` 循环通常不用于这种简单的计数器；这通常是 `for` 循环的工作。虽然你可以用 `while` 循环创建计数器，但通常它们用于在某事发生之前保持运行代码。例如，我们可能想一直掷骰子直到掷出 6。在编写代码时无法知道需要多少次掷骰：可能一次就能掷出六点，也可能需要上百次。因此你可以将掷骰子放在 `while` 循环中。

**示例：[PHP-DiceRoll-While](https://github.com/spbooks/phpmysql7/tree/PHP-DiceRoll-While)**

```
$roll = 0;
while ($roll != 6) {
  $roll = rand(1, 6);
  echo '<p>You rolled a ' . $roll . '</p>';

  if ($roll == 6) {
    echo '<p>You win!</p>';
  }
  else {
    echo '<p>Sorry, you didn\'t win, better luck next time!</p>';
  }
}
```

这将一直掷骰子直到掷出 6。每次运行代码时，在获胜之前所需的掷骰次数都会不同。

`while` 语句使用条件 `$roll != 6`。为了使 `while` 循环第一次运行，`$roll` 变量必须为初始比较设置一个值。这就是 `while` 循环上方 `$roll = 0;` 行的目的。通过初始将值设为零，当 `while` 循环第一次运行时，条件 `$roll != 6` 成立，因为 `$roll` 等于零而不是 6，循环将开始。如果在开始循环之前未创建 `$roll` 变量，你会收到错误，因为 `$roll` 变量在使用前未被设置任何值。

`while` 循环有一个变体称为 `do … while`，在这种情况下很有用。它允许你在没有条件的情况下运行一些代码，然后如果代码未设置则再次运行。它采用以下结构：

```
do {
 statement(s) to execute and then repeat if the condition is true
}
while (condition);
```

对于上面的掷骰子示例，这允许你忽略第一行。

**示例：[PHP-DiceRoll-DoWhile](https://github.com/spbooks/phpmysql7/tree/PHP-DiceRoll-DoWhile)**

```
do {
  $roll = rand(1, 6);
  echo '<p>You rolled a ' . $roll . '</p>';

  if ($roll == 6) {
    echo '<p>You win!</p>';
  }
  else {
    echo '<p>Sorry, you didn\'t win, better luck next time!</p>';
  }
}
while ($roll != 6);
```

这次，因为条件在底部，到 `while` 语句运行时，`$roll` 变量已经被赋予了值，因此你不需要给它一个初始的零值来强制循环第一次运行。

### 编码风格

PHP 不在乎你如何格式化代码，并且会忽略空白。你可以像这样编写之前的示例：

```
do {
  $roll = rand(
  1,
  6);

  echo '<p>You rolled a ' . $roll . '</p>';

  if (
      $roll == 6
  ) 
  {
    echo '<p>You win!</p>';
  }
  else
  {
    echo '<p>Sorry, you didn\'t win, better luck next time!</p>';
  }
}
while ($roll != 6);
```

脚本将以完全相同的方式执行。不同的程序员有不同的首选风格，例如使用制表符或空格进行缩进，或将开括号放在语句同一行或其后。甚至还有 [编码风格指南](https://www.php-fig.org/psr/psr-12/) 规定大括号和方括号应放置的位置以及代码应如何格式化。但计算机并不关心大括号是在同一行还是下一行，所以使用你感觉最舒适的风格即可。

## 数组

一个 **array** 是一种包含多个值的特殊变量。如果你把变量想象成包含一个值的盒子，那么数组可以被想象成一个带隔间的盒子，其中每个隔间都能存储一个单独的值。

要在 PHP 中创建数组，请使用方括号（`[` 和 `]`）包含你想要存储的值，用逗号分隔：

```
$myArray = ['one', 2, '3'];
```

### `array` 关键字与方括号

PHP 中的数组也可以使用 `array` 关键字定义。以下代码等同于上面的方括号表示法：

```
$myArray = array('one', 2, 3);
```

方括号表示法是在 PHP 5.4 中引入的，并被 PHP 开发者所偏爱，因为它更少打字，并且在 `if` 语句和 `while` 循环等控制结构中的圆括号中，方括号更易于辨认。

这段代码创建了一个名为 `$myArray` 的数组，包含三个值：`'one'`、`2` 和 `'3'`。就像普通变量一样，数组中的每个空间可以包含任何类型的值。在这种情况下，第一和第三个空间包含字符串，而第二个包含数字。

要访问存储在数组中的值，你需要知道其 **index**。通常，数组使用数字作为索引来指向它们包含的值，从零开始。也就是说，数组的第一个值（或元素）的索引为 0，第二个为 1，第三个为 2，以此类推。因此，数组中第 n 个元素的索引为 n–1。一旦你知道感兴趣的值的索引，你就可以通过在数组变量名后放置该索引在方括号中来检索该值：

```
echo $myArray[0];    // outputs 'one'
echo $myArray[1];    // outputs '2'
echo $myArray[2];    // outputs '3'
```

存储在数组中的每个值称为一个 **element**。你可以使用方括号中的键来添加新元素，或为现有数组元素分配新值：

```
$myArray[1] = 'two';     // assign a new value
$myArray[3] = 'four';    // create a new element
```
