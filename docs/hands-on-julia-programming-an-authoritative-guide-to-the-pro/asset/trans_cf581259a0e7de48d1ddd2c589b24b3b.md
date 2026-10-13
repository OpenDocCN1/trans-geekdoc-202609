

# Rational4 和 Complex 数据类型

`Rational4` 和 `Complex` 数据类型虽然属于数值类型，但并非原始类型。它们是使用复合数据类型创建的，我们将在用户定义类型部分回顾这些内容。

`Any` 作为一种类型会引入不必要的间接层，因此可能效率低下。有时类型并不一定影响算法，但会引入不同的数据位大小。例如，前面在数值数据类型背景下介绍的 `Rational` 数据类型：分子和分母可以是任意整数数据类型，如 `Int8`、`Int16`、`Int32`、`Int64` 或 `Int128`。`Rational` 数据类型的定义如下：

# 分支与控制流

分支与控制流是命令式编程风格的核心。作为一门函数式编程语言，Julia 支持所有著名的命令式风格和构造。本章将向你展示其中的大部分内容。

## 章节主题

在本章中，我们将涵盖以下主题：

*   复合语句
*   条件执行
*   迭代执行
*   异常处理
*   并行执行

## 学习目标

在本章中，读者将能够理解复合语句。我们将讨论分支与控制流，如 `if…else`，循环如 `while` 和 `for`，以及异常处理。控制流是编程逻辑的核心，有助于构建复杂的应用程序。

# 复合语句

位于 `begin` 和 `end` 块之间的任何一组语句都被视为一个大的复合执行单元。

```
julia> z = begin
           x = 1
           y = 2
           x + y
         end
3
julia> z
3
```

块中最后一个表达式的值被视为复合块的值。同一个表达式也可以使用分号和大括号写成单行。

```
julia> z = (x = 1; y = 2; x+y)
3
```

以下也是有效的复合语句。

```
julia> z = (x = 1;
           y = 2;
           x + y)
3
```

```
julia> z = begin x=1; y=2; x+y end
3
```

# 条件语句

条件语句是任何编程语言的核心。它们为代码中定义分支提供了途径，也是迭代编程的基础。带有局部 `goto` 的分支足以模拟编程语言中的任何迭代模型。

## `if…else`

`if…else` 是 Julia 中最常见的条件执行形式。典型的 if 条件如下所示：

```
if <Boolean condition>
    #do something
else
    #do the something else
end
```

`else` 部分是可选的。条件必须是布尔值。具有与布尔值 true 或 false 相同值的整数不能替代它们。

```
julia> if 1
           println("I am here")
       end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

```
julia> if Bool(1)
           println("I am here")
       end
I am here
```

`if` 表达式返回被执行的那个分支的值。

```
julia> i = 1
1
julia> str = if i > 1
               "Greater"
           else
               "Less"
           end
"Less"
julia> str
"Less"
```

同一个表达式也可以使用 `?` 和 `:` 表示为三元运算符：

```
julia> str = i > 1 ? "Greater" : "Less"
"Less"
```

虽然在大多数表达式中通常不需要空白字符，但这里强制要求在 `?` 和 `:` 周围有空白字符。

```
julia> str = i > 1? "Greater" : "Less"
ERROR: syntax: space required before "?" operator
julia> str = i > 1 ? "Greater": "Less"
ERROR: syntax: space required before colon in "?" expression
```

## `switch…case` 替代方案

`switch…case` 表达式通常用于需要大量比较作为多重分支操作的情况。C/C++ 中的示例 `switch…case` 语句可能如下所示：

```
res = ""
switch (val) {
case 1: res = "One"; break;
case 2: res = "Two"; break;
case 3: res = "Three"; break;
case 4: res = "Four"; break;
...
default: res = "Unknown"; break
}
```

Java 和其他语言也有类似的构造。然而，此类表达式在 Julia 中不存在。关于在 Julia 中包含或排除类似结构一直有大量争论。虽然这是一种简洁的表示，但 `switch…case` 结构存在两个已知的重要问题：回落到下一个 case 需要特定的 break 语句；其次，C/C++ switch 语句仅适用于整数类型。

Julia 通过 `if…else if…else` 结构来满足此类构造的需求。以下内容可以阐明语法：

```
julia> val = 3
3
julia> if val == 1
           "one"
       elseif val == 2
           "two"
       elseif val == 3
           "three"
       elseif val == 4
           "four"
       else
           "unknown"
       end

"three"
```

### `else if` 对比 `elseif`

让我们看看以下代码片段：

```
julia> if val == 1
           "one"
       elseif val == 2
           "two"
       elseif val == 3
           "three"
       elseif val == 4
           "four"
       else if val >= 5
ERROR: syntax: use "elseif" instead of "else if"
```

