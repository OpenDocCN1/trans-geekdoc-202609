
```php
if($grade >= 18) {
    echo "Excellent work!";
} else {
    if($grade >= 16) {
        echo "Very good work!";
    } else {
        if($grade >= 14) {
            echo "Good job!";
        } else {
            echo "Can do better!";
        }
    }
}
?>
```

运行此代码后，您应得到以下结果：

![](img/caba2aa22f5409ba73dea47176330677_105_0.png)

本示例中的代码是一系列嵌套 if 语句，用于评估 $grade 变量，以根据学生的表现提供消息。

- 首先，代码检查分数是否为 18 或以上。如果是，则显示 "Excellent work!"。
- 如果第一个条件不为真，则意味着分数低于 18。代码接着进入第二个条件，该条件检查成绩是否大于或等于 16。如果是，则显示 "Very good work!"。
- 如果第二个条件也不为真，则意味着分数低于 16。代码接着进入第三个条件，该条件检查成绩是否大于或等于 14。如果是，则显示 "Good job!"。
- 最后，如果上述条件均不为真，则分数低于 14，代码显示 "Can do better!"。

由于变量 $grade 的值为 17，第一个 if 语句的条件未被检查，代码移到下一条语句。

第二个 if 语句（嵌套在第一个的 else 中）检查 $grade 是否大于或等于 16，这为真（$grade = 17），因此该条件满足，并显示消息 "Very good work!"。

总之，嵌套控制结构（如前面示例中使用的那些）对于基于多个条件做出决策非常有效。但是，随着条件数量的增加，代码的可读性和可维护性可能会迅速恶化。嵌套控制结构的复杂性会使代码难以理解和管理，增加出错的风险，并使未来的修改更加费力。

因此，密切关注代码的设计和可读性非常重要，尽可能避免过度嵌套的控制结构。只要有可能，最好使用 switch 结构或函数等替代方案来简化代码逻辑，使其更易于理解和维护。

## 多个条件

多个条件（也称为组合条件）允许我们在单个控制语句中评估多个布尔表达式。当我们需要同时检查多个标准以做出决策时，通常会使用这些条件。

使用逻辑运算符可以简化控制结构，因为它减少了嵌套条件块的数量。这使得代码更易于阅读和维护。

### 使用逻辑 AND 运算符（&&）

逻辑 AND 运算符（&&）仅当所有组合条件均为真时返回真。示例如下：

```php
<?php
$a = 10;
$b = 25;
if($a > 5 && $b < 100) {
    echo "You succeeded, condition true";
} else {
    echo "Sorry, condition false";
}
?>
```

执行此代码后，您将得到以下结果：

![](img/caba2aa22f5409ba73dea47176330677_108_0.png)

在此示例中，我们有两个变量 $a 和 $b。我们使用逻辑运算符 AND（&&）来组合两个条件：

if 条件使用逻辑运算符 && 组合两个条件：$a > 5 和 $b < 100。
由于两个条件均为真，组合条件 $a > 5 && $b < 100 也为真。因此，将执行 if 块并显示消息 "You succeeded, condition true"。

### 使用逻辑 OR 运算符（||）

逻辑 OR 运算符（||）在至少一个组合条件为真时返回真。示例如下：

```php
<?php
$role = "admin";
$permission = "read";

if ($role == "admin" || $permission == "write") {
    echo "You have the necessary authorizations.";
} else {
    echo "You do not have the necessary authorization";
}
?>
```

运行此代码后，您将得到以下结果：

![](img/caba2aa22f5409ba73dea47176330677_109_0.png)

在此示例中，if 语句的条件使用逻辑 OR 运算符（||）组合两个条件：$role == "admin" 和 $permission == "write"。第一个条件 $role == "admin" 得到验证，因为变量 $role 包含值 "admin"。由于我们使用逻辑 OR 运算符，只要有一个条件为真，整个 if 语句就为真。因此，组合条件也被视为真。结果，将执行 if 块。

### 组合逻辑运算符

我们也可以组合多个逻辑运算符用于更复杂的条件。示例如下：

```php
<?php
$age = 25;
$role = "admin";

if ((($age >= 18 && $role == "admin") || $role == "moderator")) {
  echo "You have access to advanced features";
} else {
  echo "You do not have access to advanced features";
}
?>
```

运行此代码后，您应得到以下结果：

![](img/caba2aa22f5409ba73dea47176330677_111_0.png)

在此示例中，我们有两个条件使用逻辑 OR 运算符（||）组合。第一个条件（$age >= 18 && $role == "admin"）检查用户年龄是否为 18 岁或以上 且 角色是否为管理员。仅当组成它的两个子条件（即 $age >= 18 和 $role == "admin"）均为真时，此条件才为真。在我们的情况中，两个子条件确实均为真。

第二个条件 $role == "moderator" 检查用户是否具有版主角色。

由于我们使用逻辑 OR 运算符（||），只要有一个条件为真，整个 if 语句就为真。在我们的示例中，由于第一个组合条件为真（$age >= 18 && $role == "admin"），用户将有权访问高级功能，从而显示消息 "You have access to advanced features"。

## switch 控制结构

PHP 的 switch 控制结构是一个强大的工具，可让您根据表达式的值执行不同的操作。

您可以将其视为一个可以在不同位置之间切换的开关。每个位置代表一个不同的 case。如果开关设置为与表达式值对应的 case，则将执行与该 case 关联的操作。

### 语法和用途

switch 结构的一般语法如下：

```
switch (expression) {
case value1:
instruction1;
break;
case value2:
instruction2;
break;
...
default:
default_instruction;
}
```

在此语法中：

- **expression**：这是您希望评估的表达式。它可以是变量、常量或任意表达式。

- **value1, value2, ...** 这些是您希望与表达式进行比较的值。每个值对应一个特定的 case。

- **instruction1, instruction2, ...** 这些是如果表达式与对应值匹配时要执行的指令。

- **break**：此指令指示 PHP 在执行对应 case 的指令后退出 switch 结构。如果没有 break，PHP 将继续执行后续 case 的指令，这可能导致意外行为。

- **default**：这是一个可选选项，用于指定如果没有任何值与表达式匹配时要执行的代码。

switch 结构只评估一次表达式，并将其结果与 case 中指定的每个值进行比较。如果找到匹配项，则执行相应的指令，直到遇到 break 为止。如果没有找到匹配项且存在 **default** 子句，则执行默认指令。

以下是一个具体示例来说明这个想法：假设您想根据星期几显示不同的消息。您可以为此使用 switch 结构：

```php
<?php
$day = "Monday";
switch ($day) {
case "Monday":
echo "Today is Monday.";
break;
case "tuesday":
    echo "Today is Tuesday.";
    break;
case "Wednesday":
    echo "Today is Wednesday.";
    break;
default:
    echo "Today is not Monday, Tuesday or Wednesday.";
}
?>
```

在此示例中，我们有 $day（switch）变量，并为每个星期几指定了不同的 "case"。如果 $day 的值与指定的某一天匹配，则将显示与该天关联的消息。如果没有 case 匹配，则将执行 default 块，显示默认消息。在此示例中，由于 $day 的值为 "Monday"，执行此代码将显示句子 "Today is Monday"。

当您需要根据单个表达式的值处理多个 case 时，可以使用 switch 结构。它使您的代码更清晰、更简洁，尤其是当您有一系列需要逐个评估的条件时。当变量具有有限的可能值集并且您需要根据这些值执行不同操作时，switch 结构特别有用。

除了使用 switch 结构外，我们还可以使用条件结构编写前面的代码
