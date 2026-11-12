

## if...elseif...else 如下：

```php
<?php
$day = "Monday";
if ($day == "Monday") {
    echo "Today is Monday.";
} elseif ($day == "Tuesday") {
    echo "Today is Tuesday.";
} elseif ($day == "Wednesday") {
    echo "Today is Wednesday.";
} else {
    echo "Today is not Monday, Tuesday or Wednesday.";
}
?>
```

这两段代码执行的任务基本相同，即检查变量 $day 的值并根据该值显示消息。但是，它们使用了不同的控制结构来实现相同的结果。

总体而言，这两种方法都是有效的，可以根据程序的具体需求和开发者的偏好来使用。

但是，如果我们有几个需要测试的情况，每个情况都需要与单个值进行比较，那么通常更倾向于使用 switch-case 方法。这是因为其结构清晰简洁，能够轻松处理多个情况，而无需每次重复比较。

当要测试的变量只有有限数量的可能值，并且我们希望根据这些值执行不同的代码块时，使用 switch-case 尤其合适。这种方法还避免了代码重复，使代码更易读且更易于维护。

## switch 中的多个情况分组

PHP 的 switch 结构提供了在单个块中对多个情况进行分组的可能性，从而为管理不同条件提供了一种更简洁、更有条理的方法。下面是一个具体示例，用于说明这一想法：

```php
<?php

$day = "Thursday";

switch ($day) {
case "Monday":
case "Tuesday":
case "Wednesday":
    echo "This is the beginning of the work week.";
    break;
case "Thursday":
case "Friday":
    echo "The end of the week is approaching.";
    break;
case "Saturday":
case "Sunday":
    echo "It's the weekend!";
    break;
default:
    echo "Day not recognized.";
}
?>
```

在这个示例中，"Monday"、"Tuesday" 和 "Wednesday" 这几天被归类在同一个块中，因为它们都需要执行相同的操作：指示工作周的开始。换句话说，如果 $day 的值是 "Monday"、"Tuesday" 或 "Wednesday"，程序将显示 "This is the start of the work week" 并退出 switch。

同样，"Thursday" 和 "Friday" 这几天被归类在一起，以表示周末即将到来，而 "Saturday" 和 "Sunday" 这几天被归类在一起，以表示周末。如果没有任何情况匹配，则执行 default 块以指示未识别该天。

在这个示例中，由于变量 $day 的值为 "Thursday"，执行此代码将显示 "The end of the week is approaching"。

![](img/caba2aa22f5409ba73dea47176330677_118_0.png)

## match 控制结构

PHP 8 引入的 **match** 控制结构，为将值与一系列情况进行比较并执行相应代码提供了一种比 switch 结构更简洁、更具表现力的替代方案。它的工作方式与 switch 结构类似，但具有更简化、更具表现力的语法。

match 控制结构的语法如下：

```
match (expression) {
    value1 => instruction1;
    value2 => instruction2;
    ...
    default => default_instruction;
}
```

在此语法中：

- expression：这是你希望求值的表达式。它可以是变量、常量或任意表达式。

- value1, value2, ... 这些是你希望与表达式进行比较的值。每个值对应一个特定的情况。

- instruction1, instruction2, ... 这些是如果表达式与相应的值匹配时要执行的指令。

- default：这是一个可选选项，用于指定如果没有值与表达式匹配时要执行的代码。它相当于 switch 结构中的 "default" 子句。

match 结构会对表达式求值，并将其结果与每个指定的值进行比较。如果找到匹配项，则执行相应的指令。如果未找到匹配项且存在 default 子句，则执行 default 指令。

下面是一个简单示例，说明 match 结构的使用：

```php
<?php
$day = "friday";
$message = match ($day) {
    'Monday' => "Today is Monday.",
    'Tuesday' => "Today is Tuesday.",
    'Wednesday' => "Today is Wednesday.",
    default => "Today is not Monday, Tuesday, or Wednesday."
};
echo $message;
?>
```

在这段 PHP 代码中，我们有一个包含字符串 "friday" 的变量 $day。然后，我们使用 match 结构将变量 $day 的值与几个情况进行比较。每个情况对应一周中的某一天：'Monday'、'Tuesday'、'Wednesday'。如果 $day 的值与其中某个情况匹配，我们将设置变量 $message，为该天分配一条适当的消息。如果 $day 的值与任何这些情况都不匹配，我们将使用 default 情况来设置对应未指定星期几的消息。

![](img/caba2aa22f5409ba73dea47176330677_121_0.png)

最后，我们使用 echo 语句显示变量 $message 中定义的消息。

在 PHP 中使用 match 结构简化了基于变量值检查多个情况的过程，并使其更易读。这通常替代了多个 if 和 else if 语句的使用。

## 将 match 结果保存在变量中

当你希望在代码的后续部分使用结果时，match 控制结构可以将其结果存储在变量中。当你需要在程序的多个位置使用与相应条件关联的值时，这很有用。

使用变量存储 match 结果还可以使代码更具可读性和模块化，因为你可以为变量赋予有意义的名称，以表示与特定条件对应的结果。

下面是一个说明这一想法的示例：

```php
<?php

$state = "California";

$message = match ($state) {
    "California" => "You're in the Golden State!",
    "New York" => "Welcome to the Empire State!",
    "Texas" => "Howdy from the Lone Star State!",
    "Florida" => "Sunshine State greetings from Florida!",
    default => "You're not in California, New York, Texas, or Florida."
};

echo $message;

?>
```

这段 PHP 代码使用新的 match 模式匹配结构，将变量 $state 的值与多个情况进行比较。详细解释如下：

$state = "California"; ：我们将字符串 "California" 赋值给变量 $state。

$message = match ($state) { ... }; ：我们使用 match 结构将 $state 的值与不同的情况进行比较。

"California" => "You're in the Golden State!" ；：如果 $state 的值为 "California"，则消息 "You're in the Golden State!" 会被赋值给变量 $message。

"New York" => "Welcome to the Empire State!" ；：如果 $state 的值为 "New York"，则消息 "Welcome to the Empire State!" 会被赋值给变量 $message。

"Texas" => "Howdy from the Lone Star State!" ；：如果 $state 的值为 "Texas"，则消息 "Howdy from the Lone Star State!" 会被赋值给变量 $message。

"Florida" => "Sunshine State greetings from Florida!" ；：如果 $state 的值为 "Florida"，则消息 "Sunshine State greetings from Florida!" 会被赋值给变量 $message。

default => "You're not in California, New York, Texas, or Florida." ：如果 $state 的值与任何前面的情况都不匹配，则消息 "You're not in California, New York, Texas, or Florida." 会被赋值给变量 $message。

echo $message; ：最后，使用 echo 语句在屏幕上显示变量 $message 中包含的消息。

总之，这段代码根据变量 $state 的值显示不同的消息，使用 match 结构来简化不同情况的检查。

