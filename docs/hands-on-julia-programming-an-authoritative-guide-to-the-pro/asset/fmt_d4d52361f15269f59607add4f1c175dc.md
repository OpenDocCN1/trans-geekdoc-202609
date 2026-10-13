
# Julia 日期时间与日志记录

## 日期时间比较与运算

`DateTime` 和 `Date` 可以相互比较，也可以在同类型内部比较。

```julia
julia> DateTime(d)
2020-10-31T00:00:00

julia> t > d  # t is DateTime and d is a Date
true

julia> DateTime(2020) < now()  # both date time
true

julia> DateTime(2020) == Date(2020)
true
```

两个 `Date` 的差值，或两个 `DateTime` 的差值，会产生 `Period` 类型的子类型。常用的周期类型有 `Year`、`Day`、`Month`、`Hour`、`Minute`、`Second` 和 `Millisecond`。这些类型的组合可形成 `CompositePeriod` 类型。`Periods` 可与 `Date` 和 `DateTime` 结合，生成相应的 `Date` 和 `DateTime`。

```julia
julia> p = Month(3) + Day(10) + Hour(15)
3 months, 10 days, 15 hours

julia> typeof(p)
Dates.CompoundPeriod

julia> now() + p
2021-03-11T01:24:53.251

julia> Date(now()) + Day(300)
2021-09-24

julia> now() - DateTime(2020)
28728026709 milliseconds

julia> now() - Date(2020)
MethodError: no method matching -(::DateTime, ::Date)

julia> Date(now()) - Date(2020)
332 days
```

### 访问器构造函数

访问器构造函数用于估算从上一个较大周期过去的周期。例如，`Month()` 计算从年初过去的月数，`Day()` 计算从上个月结束过去的天数。不过，`Week()` 计算从年初过去的周数。小写函数返回 `Int64` 数量而非 `Period`。

```julia
julia> Year(now())
2020 years

julia> Month(now())
11 months

julia> Day(now())
28 days

julia> Week(now())
48 weeks

julia> year(now())
2020
```

### 调整器

Julia 提供了许多称为 **adjustors** 的有趣函数，有助于计算特定日期。例如，查找下一个感恩节（11 月的第 4 个周四）可基于以下代码：

```julia
julia> tonext(today()) do d
           dayofweek(d) == Thursday &&
           dayofweekofmonth(d) == 4 &&
           month(d) == November
       end
2021-11-25
```

---

## 日志记录

Julia 广泛用于后端服务器编程，这意味着必须跟踪长时间运行进程的错误和故障。标准库中的 `Logging` 模块在一定程度上满足了这一需求。Julia 中的消息可以在不同的日志级别记录。以下是按严重程度递增顺序排列的示例：

```julia
julia> @error "This is an error"
┌ Error: This is an error
└ @ Main REPL[1]:1

julia> @warn "This is a warning"
┌ Warning: This is a warning
└ @ Main REPL[2]:1

julia> @info "This is an info"
[Info: This is an info

julia> @debug "This is debug message $(sum(rand(10)))"
julia>
```

由于默认日志级别设为 `info`，而 `debug` 级别低于该级别，因此调试消息根本未被计算。根据系统终端能力和所用记录器，日志消息可能以各种颜色和高亮渲染。上述渲染来自 REPL 的默认渲染。例如，info 消息中不报告行号。

当宏参数不是字符串时，它们将显示为键，后跟其实际计算值。

```julia
julia> A = ones((3, 4))

julia> @info "A is all ones" A
┌ Info: A is all ones
│   A =
│    3×4 Array{Float64,2}:
│     1.0  1.0  1.0  1.0
│     1.0  1.0  1.0  1.0
└     1.0  1.0  1.0  1.0
```

每个应用程序都有一个注册的记录器，它将日志事件作为输入并根据记录器能力有效渲染。能力包括应用程序日志的写入流，如文件系统、`stderr` 或任何其他流。迄今为止我们一直在使用全局记录器。全局记录器可通过 `global_logger(logger::AbstractLogger)` 方法覆盖。应用程序也可使用 `with_logger(f, logger)` 方法设置局部记录器。以下代码使用 `SimpleLogger` 将日志写入文件：

```julia
julia> using Logging

julia> open("file.log", "w") do f
           with_logger(SimpleLogger(f)) do
               @info "This is my simple info log"
               @error "This is an error written to file"
               @warn "This is a warning message"
               @info "Current logger is same as global logger" current_logger() == global_logger()
           end
       end

julia> write(stdout, read("file.log"));
┌ Info: This is my simple info log
└ @ Main In[72]:3
┌ Error: This is an error written to file
└ @ Main In[72]:4
┌ Warning: This is a warning message
└ @ Main In[72]:5
┌ Info: Current logger is same as global logger
│   current_logger() == global_logger() = false
└ @ Main In[72]:6

julia> @info "Current logger is same as global logger" current_logger() == global_logger()
┌ Info: Current logger is same as global logger
│   current_logger() == global_logger() = true
└ @ Main In[72]:10
```

由于局部记录器在 `with_logger` 块内覆盖了当前记录器，因此当前记录器不同于全局记录器。然而，在 `with_logger` 块外部，`current_logger()` 与 `global_logger()` 相同。`SimpleLogger` 提供了一个非常简单的接口，用于覆盖日志流和要在记录器中显示的消息级别。日志事件还可以包含模块、消息标识符、文件、行号、日志消息显示的最大次数以及作为日志一部分显示的异常。
