

```php
} else {
    echo "Can do better";
}
?>
```

这段代码使用 `if...elseif...else` 结构来评估变量 `$grade` 的值，并根据该值显示一条消息。其工作原理如下：

1. 变量 `$grade` 初始化为值 `75`。
2. 程序首先通过 `if ($grade >= 90)` 条件检查 `$grade` 的值是否大于或等于 `90`。由于情况并非如此（`75` 不大于或等于 `90`），我们继续检查下一个条件。
3. 接着，程序通过 `elseif` 条件 `($grade >= 80)` 检查 `$grade` 的值是否大于或等于 `80`。由于 `75` 小于 `80`，此条件也不满足。
4. 最后，程序执行 `else` 子句中的代码块，因为之前的所有条件均未满足。它随即显示 "Can do better"。

简而言之，这段代码显示 "Can do better" 是因为 `$grade` 的值不够高，无法满足 `if` 和 `elseif` 代码块的条件。

![Image](images/image-35.png)

请注意，在 PHP 中，你可以在一个 `if` 子句后使用任意数量的 `elseif` 子句。这允许你依次测试多个不同的条件，直到其中一个为真，或者直到所有条件都已测试且均为假。让我们按如下方式修改前面的示例：

```php
<?php
$grade = 64;

if ($grade >= 90) {
    echo "Excellent work!";
} elseif ($grade >= 80) {
    echo "Very good work!";
} elseif ($grade >= 70) {
    echo "Good work!";
} elseif ($grade >= 60) {
    echo "Average work!";
} elseif ($grade >= 50) {
    echo "Can do better!";
} else {
    echo "Change group";
}
?>
```

这段代码评估变量 `$grade` 的值，并根据该分数显示一条消息。

*   如果分数大于或等于 `90`，则显示消息 "Excellent work!"。
*   否则，如果分数大于或等于 `80` 但严格小于 `90`，则显示消息 "Very good work!"。
*   否则，如果分数大于或等于 `70` 但严格小于 `80`，则显示消息 "Good work!"。
*   否则，如果分数大于或等于 `60` 但严格小于 `70`，则显示消息 "Average work!"。
*   否则，如果分数大于或等于 `50` 但严格小于 `60`，则显示消息 "Can do better!"。
*   否则，如果不满足上述任何条件（即分数低于 `50`），则显示消息 "Change group"。

在本例中，分数为 `64`，因此显示消息 "Average work!"，因为这是在所有评估的条件中第一个满足的条件。

![Image](images/image-36.png)

请注意，当你在初始 `if` 后依次使用多个 `elseif` 语句时，第一个评估为 `TRUE` 的 `elseif` 语句将被执行。换句话说，`elseif` 语句仅在前面的 `if` 和所有前面的 `elseif` 语句均评估为 `FALSE`，且你的 `elseif` 语句评估为 `TRUE` 时才会执行。这提供了一系列替代条件，其中每个 `elseif` 指令按顺序评估，直到满足某个条件，从而确保流畅且精确的控制逻辑。

## 条件结构与布尔变量

如果 `if` 或 `elseif` 语句中要评估的条件是一个布尔变量，其行为非常简单直接。如果布尔变量包含值 `TRUE`，则评估为真 (`TRUE`)；如果包含值 `FALSE`，则评估为假 (`FALSE`)。

示例：

```php
<?php
$truth = true; // 声明一个值为 TRUE 的布尔变量

if ($truth) {
    echo "The condition is true."; // 此指令将被执行，因为 $truth 包含值 TRUE
} else {
    echo "The condition is false";
}
?>
```

在本例中，布尔变量 `$truth` 包含值 `TRUE`，因此 `if` 语句中的条件 `$truth` 评估为 `TRUE`，执行 `if` 代码块内的代码，显示 "The condition is true."。如果 `$truth` 变量包含值 `FALSE`，则将执行 `else` 代码块，显示 "The condition is false"。

在某些情况下，评估条件的否定更有意义。在前面的示例中，如果你想测试布尔变量 `$truth` 的否定，只需在条件中使用逻辑否定运算符 (`!`) 即可。具体做法如下：

```php
<?php
$truth = true; // 声明一个值为 TRUE 的布尔变量

if (!$truth) {
    echo "The condition is false."; // 此指令将被执行，因为 !$truth 评估为 FALSE
} else {
    echo "The condition is false";
}
?>
```

## 条件嵌套

条件嵌套，也称为嵌套条件控制结构，是 PHP 编程中的常见做法。它由将一个条件语句放置在另一个条件语句内部组成。可以创建一系列嵌套的 `if` 语句来处理不同的条件，但随着条件数量的增加，这种方法很快会变得复杂。

以下是 PHP 中条件嵌套的示例：

```php
<?php
$grade = 17;

if ($grade >= 18) {
    echo "Excellent work!";
} else {
    if ($grade >= 16) {
        echo "Very good work!";
    } else {
        if ($grade >= 14) {
            echo "Good job!";
        } else {
            echo "Can do better!";
        }
    }
}
?>
```

如果你运行这段代码，应该会得到以下结果：

![Image](images/image-37.png)

本示例中的代码是一系列嵌套的 `if` 语句，用于评估 `$grade` 变量，以根据学生的表现提供消息。

*   首先，代码检查分数是否为 `18` 或以上。如果是，则显示 "Excellent work!"。
*   如果第一个条件不成立，意味着分数低于 `18`。代码随后进入第二个条件，检查分数是否大于或等于 `16`。如果是，则显示 "Very good work!"。
*   如果第二个条件也不成立，意味着分数低于 `16`。代码随后进入第三个条件，检查分数是否大于或等于 `14`。如果是，则显示 "Good work!"。
*   最后，如果上述条件均不成立，分数低于 `14`，代码显示 "Can do better!"。

由于变量 `$grade` 的值为 `17`，第一个 `if` 语句的条件不成立，代码继续执行下一条语句。

第二个 `if` 语句（嵌套在第一个的 `else` 中）检查 `$grade` 是否大于或等于 `16`，这为真（`$grade = 17`），因此满足此条件并显示消息 "Very good work!"。

总之，嵌套控制结构（如前面示例中所用）对于基于多个条件做出决策非常有效。然而，随着条件数量的增加，代码的可读性和可维护性会迅速下降。嵌套控制结构的复杂性会使代码难以理解和管理，增加出错风险，并使未来的修改更加繁琐。

因此，必须密切关注代码的设计和可读性，尽可能避免过度嵌套的控制结构。只要可能，最好使用 `switch` 结构或函数等替代方案来简化代码逻辑，使其更易于理解和维护。

## 多重条件

多重条件，也称为组合条件，允许我们在单个控制语句中评估多个布尔表达式。当我们需要同时检查多个标准以做出决策时，通常会使用这些条件。

使用逻辑运算符通过减少嵌套条件块的数量来简化控制结构。这使代码更易于阅读和维护。

### 逻辑与运算符 (`&&`) 的使用

