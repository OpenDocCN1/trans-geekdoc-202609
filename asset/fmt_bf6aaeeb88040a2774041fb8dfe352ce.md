
`<strong>Int</strong>` 对象与 `<strong>Int64</strong>` 进行比较，如果它们相同，则 `<strong>UInt</strong>` 初始化为 `<strong>UInt64</strong>`，否则初始化为 `<strong>UInt32</strong>`。因此 `<strong>UInt</strong>` 根据机器架构充当 `<strong>UInt64</strong>` 或 `<strong>UInt32</strong>` 的别名。

### isa

提供实例是否为特定类型的信息。`<strong>isa</strong>` 也可用作中缀运算符。

```
julia> isa(1, Number)
true
julia> isa(1, Matrix)
false
julia> isa(1, Int)
true
julia> 1 isa Number
true
```

### supertype

此函数返回类型的直接父类型。

```
julia> supertype(Int32)
Signed
```

### <:

此运算符用于表示一个类型是否为另一个类型的子类型。

```
julia> Int32 <: Integer
true
julia> Int32 <: AbstractFloat
false
julia> Int32 <: Real
true
julia> Int32 <: Signed
true
```

## 显示与输出

定义复杂数据类型时，需要以有意义的方式呈现数据。默认情况下，所有成员将作为元组打印。

```
julia> struct A
           a1::Int32
           a2::Float64
       end
julia> a = A(1, 2)
A(1, 2.0)
```

其次，数据总是会在 REPL 中打印。要禁止在 REPL 中打印数据，可以在语句末尾加上分号 (`;`)。

```
julia> a;
julia> a
A(1, 2.0)
```

但为什么会有这种行为？让我们看更多示例。

```
julia> b = 2.0
2.0
julia> a; b
2.0
```

用分号分隔行时，仅打印最后一个表达式的输出，本例中即为 `b`。

```
julia> nothing
```

`<strong>Nothing</strong>` 默认不标记输出。当分号用作语句结束时，其行为类似于在分号末尾添加了一个 `<strong>nothing</strong>`。因此无输出被打印。

```
julia> a
A(1, 2.0)
julia> a;
julia> a; nothing
```

### 使用 show 自定义显示

默认情况下，要在 REPL 上显示输出，会在数据类型上调用关联的 `show` 方法。

```
julia> struct A
           a1::Int32
           a2::Float64
       end
julia> a = A(1, 2)
A(1, 2.0)
julia> function Base.show(io::IO, a::A)
           println(io, "a1: ", a.a1, " a2: ", a.a2)
       end
julia> a
a1: 1 a2: 2.0
```

`show` 用于在任何类型的输出设备上显示数据，而 `print` 只能用于输出文本表示形式。当没有引入特定的 `print` 例程时，调用 `print` 时内部会使用 `show`。

```
julia> print(a)
a1: 1 a2: 2.0
```

### string

此函数可用于将任何类型转换为其字符串表示形式。当未提供合适的转换方法时，会在内部调用 `print` 函数以获取数据类型的文本表示形式。

```
julia> string(a)
"a1: 1 a2: 2.0\n"
```

在前面的代码中可以清楚地看到 `print` 或底层 `show` 的用法。此外，`String` 中额外的行尾可以归因于 `println` 的使用，它会在语句后添加一个 EOL（行尾符）。

## 总结

尽管 Julia 是一门动态类型语言，但类型是该语言的基础。它们在 JIT 编译期间被推断，并在很大程度上促成了 Julia 语言的性能提升。虽然我们在本章中简要概述了数据类型，但随着我们学习函数和方法，数据类型的很大一部分将被揭示出来。通过数据类型使用多重分发接口是语言基础的重要组成部分，我们也将对此进行介绍。

## 练习

1.  是否有为半精度浮点数（`Float16`）定义的字面量？如何初始化它们？

2.  使用别名 `Int`，如何判断机器是 32 位还是 64 位机器？

3.  元组可以有超过 2 个元素吗？

4.  `struct` 的默认打印形式是结构体名称，后跟大括号内作为元组的成员。这种表示形式有什么优势吗？（你可能需要了解构造函数才能体会到这一点）。

5.  复合类型的成员可以是 `nothing` 吗？这种情况有什么优势吗？

---

### 参考文献

1.  Julia 文档（手册 --> 变量） [`docs.julialang.org/en/v1/manual/variables/`](https://docs.julialang.org/en/v1/manual/variables/)

2.  LLVM 项目是模块化且可复用的编译器和工具链技术的集合。该工具提供了一种中间语言，有助于以平台中立的方式编写编译器。 [`llvm.org/`](https://llvm.org/)

3.  基本类型，Julia 文档， [`docs.julialang.org/en/v1/manual/types/#Primitive-Types`](https://docs.julialang.org/en/v1/manual/types/#Primitive-Types)

4.  有理数是分数的一种表示，具有整数分子和整数分母。它们是实数。然而，有理数在计算中相对较少使用。分数大多表示为浮点数。

5.  大多数基于对象的语言都有成员属性和方法。方法提供了多态的灵活性。然而，Julia 类型没有任何成员方法。当使用具有不同函数参数的函数来模拟多态行为时，它们被称为方法。对于大多数实际用途，函数和方法是相似的。这是一个方法 `f()` 的示例：

    ```
    f(x) = 2x
    f(x, y) = x*y
    ```

6.  代码示例取自 Julia 语言 GitHub 仓库中的 `base/rational.jl`。未包含一些高级表达式。

7.  有理数除法运算符，写作 `<<numerator>>//<<denominator>>`。

8.  Julia GitHub 仓库

9.  按位相等，通常意味着两个对象是同一个。此运算符不能被重载。类型也是对象。

10. Julia GitHub 仓库

11. 有理数是分数的一种表示，具有整数分子和整数分母。它们是实数。然而，有理数在计算中相对较少使用。分数大多表示为浮点数。

12. 基本类型，Julia 文档， [`docs.julialang.org/en/v1/manual/types/#Primitive-Types`](https://docs.julialang.org/en/v1/manual/types/#Primitive-Types)

13. 代码示例取自 Julia 语言 GitHub 仓库中的 `base/rational.jl`。未包含一些高级表达式。

14. 大多数基于对象的语言都有成员属性和方法。方法提供了多态的灵活性。然而，Julia 类型没有任何成员方法。当使用具有不同函数参数的函数来模拟多态行为时，它们被称为方法。对于大多数实际用途，函数和方法是相似的。这是一个方法 `f()` 的示例：

    ```
    f(x) = 2x
    f(x, y) = x*y
    ```

15. LLVM 项目是模块化且可复用的编译器和工具链技术的集合。该工具提供了一种中间语言，有助于以平台中立的方式编写编译器。 [`llvm.org/`](https://llvm.org/)

16. Julia 文档（手册 --> 变量） [`docs.julialang.org/en/v1/manual/variables/`](https://docs.julialang.org/en/v1/manual/variables/)

17. 可以看出，变量名不能以数字开头。变量名可以包含 Unicode 字符。变量命名有诸多限制，作者建议查阅 Julia 文档[1] 以详细了解变量命名规则。Julia 中的关键字不能用作变量。Julia 的关键字很少。其中一些包括：`baremodule`、`begin`、`break`、`catch`、`const`、`continue`、`do`、`else`、`elseif`、`end`、`export`、`false`、`finally`、`for`、`function`、`global`、`if`、`import`、`let`、`local`、`macro`、`module`、`quote`、`return`、`struct`、`true`、`try`、`using`、`while`。Julia 还有多词关键字（`mutable struct`、`abstract type` 等）和中缀运算符关键字（`in`、`isa` 等）。作者建议详细查阅语言文档中的关键字以获得详尽的理解。

18. 基本类型是 LLVM[2] 支持的数据类型。Julia 将代码编译为 LLVM 等价形式，随后再编译为原生 CPU 机器码，以 **JIT** 方式执行。因此，将 LLVM 类型引入 Julia 是非常合乎逻辑的。这些基本类型是位值。以下是 Julia[3] 中定义的一组基本类型。

19. 基本类型是 LLVM[2] 支持的数据类型。Julia 将代码编译为 LLVM 等价形式，随后再编译为原生 CPU 机器码，以 **JIT** 方式执行。因此，将 LLVM 类型引入 Julia 是非常合乎逻辑的。这些基本类型是位值。以下是 Julia[3] 中定义的一组基本类型。

20. 与其他实例对象一样，它们可以被比较和赋值。这是来自 `base/boot.jl` 的代码片段。[8]

21. Julia 中的复合类型具有成员属性，没有成员函数或方法。Julia 的多重分发架构用于使函数针对特定类型表现得像方法[5]，但它们与面向对象语言中的方法并不相同。有一类特殊的函数可以成为类型的成员。它们被称为 **构造函数**。当我们讨论函数时，将详细回顾构造函数。复合类型中成员的类型信息并不总是需要指定。

## Rational4 和 Complex 数据类型

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

## 复合语句

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

## 条件语句

条件语句是任何编程语言的核心。它们为代码中定义分支提供了途径，也是迭代编程的基础。带有局部 `goto` 的分支足以模拟编程语言中的任何迭代模型。

### if…else

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

### switch…case 替代方案

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

#### else if 对比 elseif

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

## if-elseif-else 结构化分支

```julia
julia> if val == 1
           "one"
       elseif val == 2
           "two"
       elseif val == 3
           "three"
       elseif val == 4
           "four"
       else
           if val >= 5
               "above five"
           else
               "below five"
           end
       end
"three"
```
