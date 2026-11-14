
## 排序进阶

`Len` 和 `Swap`，即 `reverse` 的另外两个方法，由原始的 `sort.Interface` 值隐式提供，因为它是一个嵌入字段。导出函数 `Reverse` 返回一个包含原始 `sort.Interface` 值的 `reverse` 类型实例。

### 按不同列排序

要按不同列排序，我们必须定义一个新类型，例如 `byYear`：

```
type byYear []*Track

func (x byYear) Len() int           { return len(x) }
func (x byYear) Less(i, j int) bool { return x[i].Year < x[j].Year }
func (x byYear) Swap(i, j int)      { x[i], x[j] = x[j], x[i] }
```

使用 `sort.Sort(byYear(tracks))` 对 `tracks` 按年份排序后，`printTracks` 显示按时间顺序排列的列表：

```
Title       Artist          Album              Year  Length
-----       ------          -----              ----  ------
Go          Moby            Moby               1992  3m37s
Go Ahead    Alicia Keys     As I Am            2007  4m36s
Ready 2 Go  Martin Solveig  Smash              2011  4m24s
Go          Delilah         From the Roots Up  2012  3m38s
```

对于每种切片元素类型和每种排序函数，我们都声明一个新的 `sort.Interface` 实现。可以看到，`Len` 和 `Swap` 方法对所有切片类型都有相同的定义。在下一个示例中，具体类型 `customSort` 将切片与函数结合，让我们只需编写比较函数即可定义新的排序顺序。顺便提一下，实现 `sort.Interface` 的具体类型不总是切片；`customSort` 是一个结构体类型。

```
type customSort struct {
    t    []*Track
    less func(x, y *Track) bool
}

func (x customSort) Len() int           { return len(x.t) }
func (x customSort) Less(i, j int) bool { return x.less(x.t[i], x.t[j]) }
func (x customSort) Swap(i, j int)      { x.t[i], x.t[j] = x.t[j], x.t[i] }
```

让我们定义一个多层排序函数，其主排序键是 `Title`，次排序键是 `Year`，第三排序键是运行时间 `Length`。以下是使用匿名排序函数调用 `Sort` 的方式：

```
sort.Sort(customSort{tracks, func(x, y *Track) bool {
    if x.Title != y.Title {
        return x.Title < y.Title
    }
    if x.Year != y.Year {
        return x.Year < y.Year
    }
    if x.Length != y.Length {
        return x.Length < y.Length
    }
    return false
}})
```

结果如下。注意标题为 "Go" 的两首曲目之间的平局倾向于较早的那首。

```
Title       Artist          Album              Year  Length
-----       ------          -----              ----  ------
Go          Moby            Moby               1992  3m37s
Go          Delilah         From the Roots Up  2012  3m38s
Go Ahead    Alicia Keys     As I Am            2007  4m36s
Ready 2 Go  Martin Solveig  Smash              2011  4m24s
```

虽然对长度为 *n* 的序列排序需要 O(*n* log *n*) 次比较操作，但测试序列是否已排序最多只需 *n*−1 次比较。`sort` 包的 `IsSorted` 函数为我们检查这一点。像 `sort.Sort` 一样，它使用 `sort.Interface` 抽象序列及其排序函数，但它从不调用 `Swap` 方法。以下代码演示了 `IntsAreSorted` 和 `Ints` 函数以及 `IntSlice` 类型：

```
values := []int{3, 1, 4, 1}
fmt.Println(sort.IntsAreSorted(values)) // "false"
sort.Ints(values)
fmt.Println(values)                     // "[1 1 3 4]"
fmt.Println(sort.IntsAreSorted(values)) // "true"
sort.Sort(sort.Reverse(sort.IntSlice(values)))
fmt.Println(values)                     // "[4 3 1 1]"
fmt.Println(sort.IntsAreSorted(values)) // "false"
```

为方便起见，`sort` 包提供了针对 `[]int`、`[]string` 和 `[]float64` 的函数和类型的特化版本，使用它们的自然排序。对于其他类型，如 `[]int64` 或 `[]uint`，我们需要自己处理，尽管路径很短。

### 练习

**练习 7.8：** 许多 GUI 提供带有状态多层排序的表格控件：主排序键是最近点击的列标题，次排序键是第二近点击的列标题，依此类推。为这种表格定义一个 `sort.Interface` 实现。将该方法与使用 `sort.Stable` 重复排序的方法进行比较。

**练习 7.9：** 使用 `html/template` 包（§4.6）替换 `printTracks`，编写一个将曲目显示为 HTML 表格的函数。利用上一个练习的解决方案，使每次点击列标题都发起 HTTP 请求对表格进行排序。

**练习 7.10：** `sort.Interface` 类型可适配于其他用途。编写函数 `IsPalindrome(s sort.Interface) bool`，报告序列 `s` 是否为回文，即反转序列不会改变它。假设索引 `i` 和 `j` 处的元素相等，如果 `!s.Less(i, j) && !s.Less(j, i)`。

## 7.7 `http.Handler` 接口

在第 1 章中，我们看到了如何使用 `net/http` 包实现 Web 客户端（§1.5）和服务器（§1.7）。本节将更仔细地研究服务器 API，其基础是 `http.Handler` 接口：

```go
package http

type Handler interface {
    ServeHTTP(w ResponseWriter, r *Request)
}

func ListenAndServe(address string, h Handler) error
```

`ListenAndServe` 函数需要一个服务器地址，如 `"localhost:8000"`，以及一个 `Handler` 接口实例，所有请求都应分派给它。它会永远运行，直到服务器失败（或启动失败）并返回一个非 nil 的错误。

设想一个电子商务网站，其数据库将待售商品映射为美元价格。下面的程序展示了最简单的实现。它将库存建模为映射类型 `database`，并为其附加了 `ServeHTTP` 方法，使其满足 `http.Handler` 接口。处理器遍历映射并打印商品。

```go
func main() {
    db := database{"shoes": 50, "socks": 5}
    log.Fatal(http.ListenAndServe("localhost:8000", db))
}

type dollars float32

func (d dollars) String() string { return fmt.Sprintf("$%.2f", d) }

type database map[string]dollars

func (db database) ServeHTTP(w http.ResponseWriter, req *http.Request) {
    for item, price := range db {
        fmt.Fprintf(w, "%s: %s\n", item, price)
    }
}
```

如果我们启动服务器：

```
$ go build gopl.io/ch7/http1
$ ./http1 &
```

然后用 §1.5 的 `fetch` 程序（或 Web 浏览器）连接它，得到以下输出：

```
$ go build gopl.io/ch1/fetch
$ ./fetch http://localhost:8000
shoes: $50.00
socks: $5.00
```

目前，服务器只能列出其全部库存，且对每个请求都如此，无论 URL 如何。更现实的服务器定义多个不同的 URL，每个触发不同行为。我们把现有的称为 `/list`，再添加一个 `/price`，报告单个商品的价格，作为请求参数指定，如 `/price?item=socks`。
