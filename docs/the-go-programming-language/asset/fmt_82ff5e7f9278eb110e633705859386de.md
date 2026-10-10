
或者接收者实参的类型是 `*T`，而接收者形参的类型是 `T`。编译器会隐式地解引用接收者，换句话说，加载该值：

[Click here to view code image](#ch06_images.html#id159pro03_r)

```
pptr.Distance(q) // implicit (*pptr)
```

如果一个命名类型 `T` 的所有方法的接收者类型都是 `T` 本身（而不是 `*T`），那么复制该类型的实例就是安全的；调用其任何方法必然会产生一个副本。例如，`time.Duration` 的值会被大量复制，包括作为函数参数传递时。但如果有任何方法使用了指针接收者，你应该避免复制 `T` 的实例，因为这样做可能会破坏内部不变量。例如，复制 `bytes.Buffer` 的实例会导致原始值和副本别名引用（[§2.3.2](#ebook_split_022.html#id-aliasing)）同一个底层字节数组。后续的方法调用将产生不可预测的效果。

### 6.2.1 Nil 是合法的接收者值

正如某些函数允许 `nil` 指针作为参数一样，某些方法也允许其接收者为 `nil`，特别是当 `nil` 是该类型有意义的零值时，就像映射和切片那样。在这个简单的整数链表中，`nil` 代表空列表：

[Click here to view code image](#ch06_images.html#id159pro04_r)

```
// An IntList is a linked list of integers.
// A nil *IntList represents the empty list.
type IntList struct {
    Value int
    Tail  *IntList
}

// Sum returns the sum of the list elements.
func (list *IntList) Sum() int {
    if list == nil {
        return 0
    }
    return list.Value + list.Tail.Sum()
}
```

当你定义一个其方法允许 `nil` 作为接收者值的类型时，在其文档注释中显式指出这一点是值得的，就像我们上面所做的那样。

这里是 `net/url` 包中 `Values` 类型定义的一部分：

[Click here to view code image](#ch06_images.html#id160pro01_r)

net/url

```
package url

// Values maps a string key to a list of values.
type Values map[string][]string

// Get returns the first value associated with the given key,
// or "" if there are none.
func (v Values) Get(key string) string {
    if vs := v[key]; len(vs) > 0 {
        return vs[0]
    }
    return ""
}

// Add adds the value to key.
// It appends to any existing values associated with key.
func (v Values) Add(key, value string) {
    v[key] = append(v[key], value)
}
```

它将其底层表示作为映射暴露出来，但也提供了简化映射访问的方法，其值是字符串切片——这是一个*多重映射*。它的客户端可以根据喜好使用其内在操作符（`make`、切片字面量、`m[key]` 等）、其方法，或两者兼用：

[Click here to view code image](#ch06_images.html#id160pro02_r)

gopl.io/ch6/urlvalues

```
m := url.Values{"lang": {"en"}} // direct construction
m.Add("item", "1")
m.Add("item", "2")

fmt.Println(m.Get("lang")) // "en"
fmt.Println(m.Get("q"))    // ""
fmt.Println(m.Get("item")) // "1"      (first value)
fmt.Println(m["item"])     // "[1 2]"  (direct map access)

m = nil
fmt.Println(m.Get("item")) // ""
m.Add("item", "3")         // panic: assignment to entry in nil map
```

在最后一次调用 `Get` 时，`nil` 接收者的行为类似于空映射。我们本可以等价地写成 `Values(nil).Get("item"))`，但 `nil.Get("item")` 无法编译，因为 `nil` 的类型未被确定。相比之下，最后一次调用 `Add` 会引发 panic，因为它试图更新一个 `nil` 映射。

因为 `url.Values` 是一个映射类型，而映射间接引用其键/值对，`url.Values.Add` 对映射元素所做的任何更新和删除对调用者都是可见的。然而，与普通函数一样，方法对引用本身所做的任何更改，如将其设为 `nil` 或使其引用不同的映射数据结构，都不会反映在调用者中。

## 6.3 通过结构体嵌入组合类型

考虑类型 `ColoredPoint`：

[Click here to view code image](#ch06_images.html#id161pro01_r)

gopl.io/ch6/coloredpoint

```
import "image/color"

type Point struct{ X, Y float64 }

type ColoredPoint struct {
    Point
    Color color.RGBA
}
```

我们本可以将 `ColoredPoint` 定义为一个包含三个字段的结构体，但我们选择*嵌入*一个 `Point` 来提供 `X` 和 `Y` 字段。正如我们在[第 4.4.3 节](#ebook_split_038.html#id-embedding)所见，嵌入让我们能以一种语法捷径来定义一个包含 `Point` 所有字段以及一些额外字段的 `ColoredPoint`。如果我们愿意，可以在不提及 `Point` 的情况下选择由嵌入的 `Point` 贡献的 `ColoredPoint` 字段：

```
var cp ColoredPoint
cp.X = 1
fmt.Println(cp.Point.X) // "1"
cp.Point.Y = 2
fmt.Println(cp.Y) // "2"
```

类似的机制适用于 `Point` 的*方法*。我们可以使用 `ColoredPoint` 类型的接收者来调用嵌入的 `Point` 字段的方法，即使 `ColoredPoint` 没有声明任何方法：

[Click here to view code image](#ch06_images.html#id161pro02_r)

```
red := color.RGBA{255, 0, 0, 255}
blue := color.RGBA{0, 0, 255, 255}
var p = ColoredPoint{Point{1, 1}, red}
var q = ColoredPoint{Point{5, 4}, blue}
fmt.Println(p.Distance(q.Point)) // "5"
p.ScaleBy(2)
q.ScaleBy(2)
fmt.Println(p.Distance(q.Point)) // "10"
```

`Point` 的方法已被*提升*到 `ColoredPoint`。通过这种方式，嵌入允许通过多个字段的*组合*来构建拥有许多方法的复杂类型，每个字段提供几个方法。

熟悉基于类的面向对象语言的读者可能会倾向于将 `Point` 视为基类，将 `ColoredPoint` 视为子类或派生类，或者将这两种类型之间的关系理解为 `ColoredPoint` “是一个” `Point`。但这将是一个错误。请注意上面对 `Distance` 的调用。`Distance` 有一个 `Point` 类型的参数，而 `q` 不是 `Point`，所以虽然 `q` 确实有一个该类型的嵌入字段，但我们必须显式地选择它。尝试传递 `q` 将会报错：

[Click here to view code image](#ch06_images.html#id162pro01_r)

```
p.Distance(q) // compile error: cannot use q (ColoredPoint) as Point
```

`ColoredPoint` 不是 `Point`，但它“有一个” `Point`，并且它拥有从 `Point` 提升的两个额外方法 `Distance` 和 `ScaleBy`。如果你更倾向于从实现角度思考，嵌入字段指示编译器生成额外的包装方法来委托给声明的方法，等价于以下代码：

[Click here to view code image](#ch06_images.html#id162pro02_r)

```
func (p ColoredPoint) Distance(q Point) float64 {
    return p.Point.Distance(q)
}

func (p *ColoredPoint) ScaleBy(factor float64) {
    p.Point.ScaleBy(factor)
}
```

当第一个包装方法调用 `Point.Distance` 时，其接收者值是 `p.Point`，而不是 `p`，并且该方法无法访问嵌入了 `Point` 的 `ColoredPoint`。

匿名字段的类型也可以是命名类型的*指针**，在这种情况下，字段和方法会从被指向的对象间接提升。增加一层间接引用让我们能够共享通用结构并动态地改变对象之间的关系。下面的 `ColoredPoint` 声明嵌入了一个 `*Point`：

[Click here to view code image](#ch06_images.html#id162pro03_r)

```
type ColoredPoint struct {
    *Point
    Color color.RGBA
}

p := ColoredPoint{&Point{1, 1}, red}
q := ColoredPoint{&Point{5, 4}, blue}
fmt.Println(p.Distance(*q.Point)) // "5"
q.Point = p.Point                 // p and q now share the same Point
p.ScaleBy(2)
fmt.Println(*p.Point, *q.Point) // "{2 2} {2 2}"
```

一个结构体类型可以有多个匿名字段。如果我们像下面这样声明 `ColoredPoint`：

```
type ColoredPoint struct {
    Point
    color.RGBA
}
```
