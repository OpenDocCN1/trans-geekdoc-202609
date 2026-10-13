
# Julia 控制流：循环与异常处理

## for 循环嵌套与 break 行为

在 Julia 中，`for` 循环可用于迭代器和范围对象。以下示例展示了嵌套循环中 `break` 的不同行为：

```julia
julia> for i=1:3, j=1:2
           println((i, j))
           if i == j
               break
           end
       end
(1, 1)
```

```julia
julia> for i=1:3
           for j=1:2
               println((i, j))
               if i == j
                   break
               end
           end
       end
(1, 1)
(2, 1)
(2, 2)
(3, 1)
(3, 2)
```

第一个示例中，`break` 直接跳出了最外层循环；第二个示例中，`break` 仅跳出内层循环。

## while 循环

`while` 循环更灵活，可作用于任意条件。只要条件为真，循环就会持续执行。通用语法如下：

```julia
while <Boolean_condition is true>
    <loop>
end
```

例如计算 1 到 10 的和：

```julia
julia> s, n = 0, 10
julia> while n > 0
           s = s + n
           n = n - 1
       end
julia> s
55
```

与 `for` 循环一样，可使用 `continue` 跳过本次迭代，用 `break` 终止循环。

## do-while 循环的变通实现

`while` 循环在开头判断条件。若需无条件执行一次循环体，再在末尾判断条件决定是否继续（即 `do...while` 结构），Julia 目前不直接支持，但可通过变通实现：

```julia
skip_eval = true
while skip_eval || Boolean_condition_is_true
    if skip_eval
        skip_eval = false
    end
    loop
end
```

示例：持续读取 REPL 输入，直到输入 `q` 为止：

```julia
julia> skip_eval, ch = true, Char(0)
(true, '\0')
julia> println("press q <enter> to end the loop")
press q <enter> to end the loop
julia> while skip_eval || ch != 'q'
           skip_eval = false
           ch = read(stdin, Char)
       end
a
q
```

## 异常处理

当程序出现异常状况，执行函数可能无法返回有效值或使程序恢复。Julia 提供 `try...catch` 机制捕获异常并恢复执行。

### 基本语法

```julia
julia> try
           sqrt(-1)
       catch e
           println(e)
       end
DomainError(-1.0, "sqrt will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).")
```

- 预期可能抛出异常的代码放在 `try` 后。
- 异常处理代码放在 `catch` 后。
- `end` 结束 `try` 块。

若无 `try...catch`，REPL 会打印默认错误信息和堆栈跟踪：

```julia
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at .\math.jl:33
 [2] sqrt at .\math.jl:573 [inlined]
 [3] sqrt(::Int64) at .\math.jl:599
 [4] top-level scope at REPL[10]:1
```

Julia 内置多种标准异常类型，如 `ErrorException`、`DomainError`、`ArgumentError`、`BoundsError` 等，均派生自抽象类型 `Exception`。

### 重新抛出异常

使用 `rethrow()` 可将捕获的异常继续向上传播：

```julia
julia> try
           sqrt(-1)
       catch e
           rethrow()
       end
ERROR: DomainError with -1.0:
sqrt will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at .\math.jl:33
 [2] sqrt at .\math.jl:573 [inlined]
 [3] sqrt(::Int64) at .\math.jl:599
 [4] top-level scope at REPL[11]:2
```

### 抛出自定义异常

可用 `throw` 抛出任意对象作为异常，不一定非要是 `Exception` 类型：

```julia
julia> try
           throw(1)
       catch e
           println(typeof(e))
       end
Int64
```

### 最佳实践

- 异常仅用于处理**异常状况**；常规控制流请用 `if...else` 等结构。
- 异常处理有显著性能开销，请谨慎使用，仅在必要时启用。
