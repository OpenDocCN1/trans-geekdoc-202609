
这是算法和人工智能领域的一个经典问题。目标是在棋盘上放置尽可能多的皇后，使得没有皇后能攻击到另一个。下图展示了一种可能的排列。然而，这个解并不唯一。我们将编写一个程序来求解八皇后问题的一种排列：

![](n4upl4fndqm.jpeg)

**图 4.1：** 八皇后问题——众多可能解之一

在设计完整的解决方案之前，我们必须先有一个程序单元，它接受两个皇后的位置作为输入，并报告它们是否互相攻击。

# 函数

Julia 中这些小型编程单元被称为**函数**。我们将创建一个函数，接受两个皇后的位置作为输入，并返回它们的路径是否重叠。以下是皇后互相攻击的条件：

1.  皇后拥有相同的 x 或 y 坐标：`x[2] = x[1]` 或 `y[2] = y[1]`
2.  皇后位于彼此的对角线上，即：`|x[2] - x[1]| = |y[2] - y[1]|`

如果两边符号相同，我们得到：`x[1] - y[1] = x[2] - y[2]`。类似地，如果符号相反，我们得到：`x[1] + y[1] = x[2] + y[2]`。

基于上述观察，我们在 Julia 中有如下函数：

```julia
julia> function attacks(x1, y1, x2, y2)
           if x1 == x2
               return true
           elseif y1 == y2
               return true
           elseif x1 - y1 == x2 - y2
               return true
           elseif x1 + y1 == x2 + y2
               return true
           else
               return false
           end
       end
julia> attacks(1, 2, 4, 5)
true
julia> attacks(1, 2, 4, 6)
false
```

`function…end` 是定义函数的分隔符。`return` 语句用于从函数返回最终输出。一个函数可以有多条 `return` 语句。前面的函数有多条返回语句，均返回 `Bool` 值。

# 运算符与简化写法

在前面的函数中，我们结合几个变量使用了一些运算符。显然，`+` 和 `-` 是两个数字之间的加法和减法二元运算符。C/C++ 程序员能认出 `==` 是两个数字之间的相等运算符。在 Julia 中，运算符被视为普通函数，它们可以返回值。`==` 运算符返回 `Bool` 值。该函数仅由 `if` 条件和 `Bool` 返回值组成；我们可以使用逻辑“或”运算符（写作 `||`）的简单组合来重写该函数。

```julia
julia> function attacks(x1, y1, x2, y2)
           return x1 == x2 || y1 == y2 || x1 - y1 == x2 - y2 || x1 + y1 == x2 + y2
       end
```

虽然推荐使用 `return` 关键字，但它对于 Julia 函数来说并非强制。如果未指定，`end` 语句前的表达式值将作为函数的返回值返回。因此，以下是前面函数的另一种表示形式：

```julia
julia> function attacks(x1, y1, x2, y2)
           x1 == x2 || y1 == y2 || x1 - y1 == x2 - y2 ||
           x1 + y1 == x2 + y2
       end
```

Julia 进一步简化了函数，使其看起来更像数学表达式。同一个函数也可以写成：

```julia
julia> attacks(x1, y1, x2, y2) =
           (x1 == x2 || y1 == y2 || x1 - y1 == x2 - y2 ||
           x1 + y1 == x2 + y2)
attacks (generic function with 1 method)
```

Julia 通过在 `begin…end` 之间指定复杂的复合表达式，提供了表示它们的灵活性。然而，对于超过单条语句的 Julia 短函数形式，这不被视为良好的实践。虽然以下是一个有效的 Julia 函数，但作为风格指南，它是不推荐的。

```julia
julia> attacks(x1, y1, x2, y2) = begin
           if x1 == x2
               return true
           elseif y1 == y2
               return true
           elseif x1 - y1 == x2 - y2
               return true
           elseif x1 + y1 == x2 + y2
               return true
           else
               return false
           end
       end
attacks (generic function with 1 method)
```

# 匿名函数与变量赋值

Julia 中的函数可以像任何其他对象一样，被赋值给变量。我们可以定义一个匿名函数并将其赋值给变量 `attacks_var`，代码如下：

```julia
julia> attacks_var = (x1, y1, x2, y2) ->
           (x1 == x2 || y1 == y2 ||
           x1 - y1 == x2 - y2 || x1 + y1 == x2 + y2)
#1 (generic function with 1 method)
julia> attacks_var(1, 2, 3, 4)
true
```

`attacks_var` 虽然表现得像个函数，但实际上是一个被赋予了匿名函数的变量。这赋予了 Julia 实质性的灵活性，其功能可以被视为类似于 Python 或 Lisp 中的 lambda 表达式。

# 函数参数与错误处理

函数 `attacks` 有四个输入参数，并返回皇后路径是否重叠。

如果我们用 5 个或 3 个参数调用该方法会怎样？

```julia
julia> attacks(1, 2, 3, 4, 5)
ERROR: MethodError: no method matching attacks(::Int64, ::Int64, ::Int64, ::Int64, ::Int64)
Closest candidates are:
  attacks(::Any, ::Any, ::Any, ::Any) at REPL[1]:1

julia> attacks(1, 2, 3)
ERROR: MethodError: no method matching attacks(::Int64, ::Int64, ::Int64)
Closest candidates are:
  attacks(::Any, ::Any, ::Any, ::Any) at REPL[1]:1
```

报告错误称该函数仅定义为接受 4 个参数或输入参数。然而，该函数可以接受任何类型作为数据输入。这之所以可能，是因为参数类型是 `Any`，考虑到函数定义中未指定参数类型。

输入参数是可选的。以下是一个没有输入参数的函数：
