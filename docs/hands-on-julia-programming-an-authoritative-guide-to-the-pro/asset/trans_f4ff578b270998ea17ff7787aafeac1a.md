
`show` 用于在任何类型的输出设备上显示数据，而 `print` 只能用于输出文本表示形式。当没有引入特定的 `print` 例程时，调用 `print` 时内部会使用 `show`。

```
julia> print(a)
a1: 1 a2: 2.0
```

# 

此函数可用于将任何类型转换为其字符串表示形式。当未提供合适的转换方法时，会在内部调用 `print` 函数以获取数据类型的文本表示形式。

```
julia> string(a)
"a1: 1 a2: 2.0\n"
```

在前面的代码中可以清楚地看到 `print` 或底层 `show` 的用法。此外，`String` 中额外的行尾可以归因于 `println` 的使用，它会在语句后添加一个 EOL（行尾符）。

# 

尽管 Julia 是一门动态类型语言，但类型是该语言的基础。它们在 JIT 编译期间被推断，并在很大程度上促成了 Julia 语言的性能提升。虽然我们在本章中简要概述了数据类型，但随着我们学习函数和方法，数据类型的很大一部分将被揭示出来。通过数据类型使用多重分发接口是语言基础的重要组成部分，我们也将对此进行介绍。

# 

1.  是否有为半精度浮点数（`Float16`）定义的字面量？如何初始化它们？

2.  使用别名 `Int`，如何判断机器是 32 位还是 64 位机器？

3.  元组可以有超过 2 个元素吗？

4.  `struct` 的默认打印形式是结构体名称，后跟大括号内作为元组的成员。这种表示形式有什么优势吗？（你可能需要了解构造函数才能体会到这一点）。

5.  复合类型的成员可以是 `nothing` 吗？这种情况有什么优势吗？

---

[1](#qpxadky7.html#n4upl4fndmk) Julia 文档（手册 --> 变量） **[https://docs.julialang.org/en/v1/manual/variables/](https://docs.julialang.org/en/v1/manual/variables/)**

[2](#qpxadky7.html#n4upl4fndml) LLVM 项目是模块化且可复用的编译器和工具链技术的集合。该工具提供了一种中间语言，有助于以平台中立的方式编写编译器。 **[https://llvm.org/](https://llvm.org/)**

[3](#qpxadky7.html#n4upl4fndmm) 基本类型，Julia 文档， **[https://docs.julialang.org/en/v1/manual/types/#Primitive-Types](https://docs.julialang.org/en/v1/manual/types/#Primitive-Types)**

[4](#qpxadky7.html#n4upl4fndmo) 有理数是分数的一种表示，具有整数分子和整数分母。它们是实数。然而，有理数在计算中相对较少使用。分数大多表示为浮点数。

[5](#qpxadky7.html#n4upl4fndmp) 大多数基于对象的语言都有成员属性和方法。方法提供了多态的灵活性。然而，Julia 类型没有任何成员方法。当使用具有不同函数参数的函数来模拟多态行为时，它们被称为方法。对于大多数实际用途，函数和方法是相似的。这是一个方法 `f()` 的示例：

```
f(x) = 2x
f(x, y) = x*y
```

[6](#qpxadky7.html#n4upl4fndmp) 代码示例取自 Julia 语言 GitHub 仓库中的 `base/rational.jl`。未包含一些高级表达式。

有理数除法运算符，写作 `<<numerator>>//<<denominator>>`。

[8](#qpxadky7.html#n4upl4fndmq) Julia GitHub 仓库

按位相等，通常意味着两个对象是同一个。此运算符不能被重载。类型也是对象。

Julia GitHub 仓库

有理数是分数的一种表示，具有整数分子和整数分母。它们是实数。然而，有理数在计算中相对较少使用。分数大多表示为浮点数。

基本类型，Julia 文档， **[https://docs.julialang.org/en/v1/manual/types/#Primitive-Types](https://docs.julialang.org/en/v1/manual/types/#Primitive-Types)**

代码示例取自 Julia 语言 GitHub 仓库中的 `base/rational.jl`。未包含一些高级表达式。

大多数基于对象的语言都有成员属性和方法。方法提供了多态的灵活性。然而，Julia 类型没有任何成员方法。当使用具有不同函数参数的函数来模拟多态行为时，它们被称为方法。对于大多数实际用途，函数和方法是相似的。这是一个方法 `f()` 的示例：

```
f(x) = 2x
f(x, y) = x*y
```

LLVM 项目是模块化且可复用的编译器和工具链技术的集合。该工具提供了一种中间语言，有助于以平台中立的方式编写编译器。 **[https://llvm.org/](https://llvm.org/)**

Julia 文档（手册 --> 变量） **[https://docs.julialang.org/en/v1/manual/variables/](https://docs.julialang.org/en/v1/manual/variables/)**

可以看出，变量名不能以数字开头。变量名可以包含 Unicode 字符。变量命名有诸多限制，作者建议查阅 Julia 文档[1] 以详细了解变量命名规则。Julia 中的关键字不能用作变量。Julia 的关键字很少。其中一些包括：`baremodule`、`begin`、`break`、`catch`、`const`、`continue`、`do`、`else`、`elseif`、`end`、`export`、`false`、`finally`、`for`、`function`、`global`、`if`、`import`、`let`、`local`、`macro`、`module`、`quote`、`return`、`struct`、`true`、`try`、`using`、`while`。Julia 还有多词关键字（`mutable struct`、`abstract type` 等）和中缀运算符关键字（`in`、`isa` 等）。作者建议详细查阅语言文档中的关键字以获得详尽的理解。

基本类型是 LLVM[2] 支持的数据类型。Julia 将代码编译为 LLVM 等价形式，随后再编译为原生 CPU 机器码，以 **JIT** 方式执行。因此，将 LLVM 类型引入 Julia 是非常合乎逻辑的。这些基本类型是位值。以下是 Julia[3] 中定义的一组基本类型。

基本类型是 LLVM[2] 支持的数据类型。Julia 将代码编译为 LLVM 等价形式，随后再编译为原生 CPU 机器码，以 **JIT** 方式执行。因此，将 LLVM 类型引入 Julia 是非常合乎逻辑的。这些基本类型是位值。以下是 Julia[3] 中定义的一组基本类型。

与其他实例对象一样，它们可以被比较和赋值。这是来自 `base/boot.jl` 的代码片段。[8]

Julia 中的复合类型具有成员属性，没有成员函数或方法。Julia 的多重分发架构用于使函数针对特定类型表现得像方法[5]，但它们与面向对象语言中的方法并不相同。有一类特殊的函数可以成为类型的成员。它们被称为 **构造函数**。当我们讨论函数时，将详细回顾构造函数。复合类型中成员的类型信息并不总是需要指定。

