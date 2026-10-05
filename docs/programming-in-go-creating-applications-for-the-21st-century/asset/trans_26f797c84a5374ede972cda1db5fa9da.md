

## 2.4. 示例：统计程序

![](img/005bb569dac79e0facc29f476bd67ade_89_0.png)

图 2.2 Linux 和 Windows 上的统计程序程序

### 2.4.1. 实现简单的统计函数

为了方便起见，我们创建了一个聚合类型，用于存储用户输入的数字以及我们计划计算的两个统计数据。

```go
type statistics struct {
    numbers []float64
    mean float64
    median float64
}
```

Go 结构体类似于 C 结构体或具有公共数据字段且没有方法的 Java 类——但不像 C++ 结构体，因为它不是类。正如我们将要看到的，Go 结构体对聚合和嵌入提供了很好的支持（$6.4, ➤ 275），并且通常是 Go 面向对象功能的核心（第 6 章）。

```go
func getstats(numbers []float64) (stats statistics) {
    stats.numbers = numbers
    sort.Float64s(stats.numbers)
    stats.mean = sum(numbers) / float64(len(numbers))
    stats.median = median(numbers)
    return stats
}
```

该函数接收一个数字切片（在这种情况下，通过我们的 `process-Request()` 函数 ➤ 77 获取），并用适当的值填充其统计结果（类型为 `statistics`）。为了计算中位数，我们需要将数字按升序排序；这是通过 `sort` 包的 `Float64s()` 函数实现的，该函数会对 `[]float64` 进行就地排序。这意味着 `getStats()` 函数会修改其参数——这在将切片、引用或指针传递给函数时是非常常见的现象。如果我们想保留切片的原始顺序，可以使用内置的 `copy()` 函数（§4.2.3, ➤ 156）将其拷贝到临时切片中，并在副本上进行操作。

平均值（或平均数）简单来说就是序列中值之和除以序列中值的个数。我们使用了一个单独的函数来求和，并将长度（数字计数）转换为 `float64`，以便 `sum()` 返回 `float64`。这也确保了我们得到浮点除法，并避免了使用整数时会截断。中位数是中间值；我们使用 `median()` 函数单独计算。

我们没有检查除以零的情况，因为程序的逻辑意味着 `getStats()` 只在至少有一个数字时才被调用；如果我们破坏了逻辑，程序将会在运行时 panic（崩溃）并终止。对于在出现问题时不应终止的任务关键型，我们可以使用 Go 的 `recover()` 函数来捕获 panic，恢复应用程序到正常状态并继续运行（§5.5, ➤ 212）。

```go
func sum(numbers []float64) (total float64) {
    for _, x := range numbers {
        total += x
    }
    return total
}
```

这使用 `for ... range` 循环来遍历所有数字（丢弃它们的索引位置）以产生总和。得益于 Go 将变量（包括命名返回值）初始化为零值，`total` 从零开始。

```go
func median(numbers []float64) float64 {
    middle := len(numbers) / 2
    result := numbers[middle]
    if len(numbers)%2 == 0 {
        result = (result + numbers[middle-1]) / 2
    }
    return result
}
```

此函数必须带有一个排序好的 `float64` 切片调用。它最初将中间值视为中位数，但如果数字个数是偶数，实际上有两个中间值，因此情况下我们将这两个值求和并除以二，以得到两个中间值的平均值。最后我们返回结果。

在本小节中，我们涵盖了特定特定的处理。在下一个小节中，我们将介绍实现支持单页 Web 应用程序的基础设施。（对 Web 编程感兴趣的读者可能更倾向于跳到练习或下一章。）

### 2.4.2. 实现基础 HTTP 服务器

统计程序在本地主机上提供单个 页面。以下是它的 `main()` 函数。

```go
func main() {
    http.HandleFunc("/", home)
```

`http.HandleFunc()` 函数接收两个参数：路径和一个在请求该路径时调用的函数。该函数的签名必须是 `func(http.ResponseWriter, *http.Request)`。我们可以根据需要注册任意多个路径-函数对。在这里，我们将路径（即 Web 应用程序的首页）注册了一个自定义的 `homePage()` 函数。

`http.ListenAndServe()` 函数在指定的 TCP 网络地址上启动 Web 服务器；这里使用了 `localhost` 和端口号 9001。如果只给出端口号，则假设为本地主机——我们同样可以使用 "localhost:9001" 或 "127.0.0.1:9001" 地址。（我们选择的端口号是随机的——如果与现有服务器冲突，只需更改代码使用另一个即可。）第二个参数用于指定使用哪种服务器——通常我们传递 `nil` 表示我们想使用默认类型。

程序有几个字符串常量，但我们将仅展示其中一个

```html
<form action="/" method="POST">
    <label for="numbers">数字（逗号分隔）：</label>
    <input type="text" name="numbers" size="30"><br>
    <input type="submit" value="Calculate">
</form>
```

统计程序提供了输入。

第 2 章 布尔值与数字

```go
func home(w http.ResponseWriter, r *http.Request) {
    form, err := r.ParseForm()
    if err != nil {
        fmt.Fprintf(w, "Error: %v", err)
        return
    }
    numbers := form.Form["numbers"]
    if len(numbers) == 0 {
        fmt.Fprintf(w, "未输入数字")
        return
    }
    var stats []float64
    for _, s := range numbers {
        n, err := strconv.ParseFloat(s, 64)
        if err == nil {
            stats = append(stats, n)
        }
    }
    mean, median := getStats(stats)
    fmt.Fprintf(w, "平均值: %f\n中位数: %f", mean, median)
}
```

