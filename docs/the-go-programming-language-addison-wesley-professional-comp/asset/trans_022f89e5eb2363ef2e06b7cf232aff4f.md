

而且如果函数必须修改其参数，则这是必需的，因为在像 Go 这样的按值调用语言中，被调用函数仅接收参数的一个副本，而不是对原始参数的引用。

[点击此处查看代码图像](#part0134_split_058.html#id103pro05_r)

```
func AwardAnnualRaise(e *Employee) {
    e.Salary = e.Salary * 105 / 100
}
```

由于结构体通常通过指针来处理，因此可以使用这种简写符号来创建并初始化一个 `struct` 变量并获取其地址：

```
pp := &Point{1, 2}
```

它完全等同于

```
pp := new(Point)
*pp = Point{1, 2}
```

但 `&Point{1, 2}` 可以直接用在表达式中，例如函数调用。

### 4.4.2 比较结构体

如果结构体的所有字段都是可比较的，则该结构体本身就是可比较的，因此该类型的两个表达式可以使用 `==` 或 `!=` 进行比较。`==` 操作按顺序比较两个结构体的对应字段，因此下面打印的两个表达式是等价的：

[点击此处查看代码图像](#part0134_split_059.html#id104pro01_r)

```
type Point struct{ X, Y int }

p := Point{1, 2}
q := Point{2, 1}
fmt.Println(p.X == q.X && p.Y == q.Y) // "false"
fmt.Println(p == q)                   // "false"
```

可比较的结构体类型，像其他可比较类型一样，可用作 map 的键类型。

[点击此处查看代码图像](#part0134_split_060.html#id104pro02_r)

```
type address struct {
    hostname string
    port     int
}

hits := make(map[address]int)
hits[address{"golang.org", 443}]++
```

### 4.4.3 结构体嵌入和匿名字段

在本节中，我们将看到 Go 独特的 `struct embedding`（结构体嵌入）机制如何让我们将一个命名的结构体类型作为另一个结构体类型的 `anonymous field`（匿名字段），提供了一种方便的语法糖，使得像 `x.f` 这样的简单点表达式可以代表像 `x.d.e.f` 这样的字段链。

考虑一个 2D 绘图程序，它提供了一个形状库，如矩形、椭圆、星星和轮子。以下是它可能定义的两种类型：

```
type Circle struct {
    X, Y, Radius int
}

type Wheel struct {
    X, Y, Radius, Spokes int
}
```

`Circle` 拥有其圆心 `X` 和 `Y` 坐标的字段，以及一个 `Radius`。`Wheel` 拥有 `Circle` 的所有特性，外加 `Spokes`，即内切辐条的数量。让我们创建一个轮子：

```
var w Wheel
w.X = 8
w.Y = 8
w.Radius = 5
w.Spokes = 20
```

随着形状集合的增长，我们必然会注意到它们之间的相似性和重复性，因此提取它们的公共部分可能会很方便：

```
type Point struct {
    X, Y int
}

type Circle struct {
    Center Point
    Radius int
}

type Wheel struct {
    Circle Circle
    Spokes int
}
```

这样应用程序可能会更清晰，但这项更改使得访问 `Wheel` 的字段变得更加冗长：

```
var w Wheel
w.Circle.Center.X = 8
w.Circle.Center.Y = 8
w.Circle.Radius = 5
w.Spokes = 20
```

Go 允许我们声明一个只有类型没有名字的字段；这样的字段称为 `anonymous fields`（匿名字段）。该字段的类型必须是一个命名类型或指向命名类型的指针。下面，`Circle` 和 `Wheel` 各有一个匿名字段。我们说 `Point` 被 `嵌入` 到了 `Circle` 中，而 `Circle` 被嵌入到了 `Wheel` 中。

```
type Circle struct {
    Point
    Radius int
}

type Wheel struct {
    Circle
    Spokes int
}
```

得益于嵌入，我们可以在不给出中间名字的情况下引用隐式树叶子节点的名字：

[点击此处查看代码图像](#part0134_split_061.html#id106pro01_r)

```
var w Wheel
w.X = 8        // 等同于 w.Circle.Point.X = 8
w.Y = 8        // 等同于 w.Circle.Point.Y = 8
w.Radius = 5   // 等同于 w.Circle.Radius = 5
w.Spokes = 20
```

注释中显式的形式仍然有效，这表明“匿名字段”某种程度上是个误称。字段 `Circle` 和 `Point` 确实有名字——即命名类型的名字——但这些名字在点表达式中是可选的。在选择其子字段时，我们可以省略任意或所有的匿名字段。

遗憾的是，结构体字面量语法没有相应的简写，所以下面两个都无法编译：

[点击此处查看代码图像](#part0134_split_062.html#id106pro02_r)

```
w = Wheel{8, 8, 5, 20}                       // 编译错误：未知字段
w = Wheel{X: 8, Y: 8, Radius: 5, Spokes: 20} // 编译错误：未知字段
```

结构体字面量必须遵循类型声明的结构，所以我们必须使用下面两种形式之一，它们彼此等价：

[点击此处查看代码图像](#part0134_split_063.html#id106pro03_r)

`gopl.io/ch4/embed`

```
w = Wheel{Circle{Point{8, 8}, 5}, 20}

w = Wheel{
    Circle: Circle{
        Point:  Point{X: 8, Y: 8},
        Radius: 5,
    },
    Spokes: 20, // 注意：此处尾随逗号是必需的（Radius 处也是）
}

fmt.Printf("%#v\n", w)
// Output:
// Wheel{Circle:Circle{Point:Point{X:8, Y:8}, Radius:5}, Spokes:20}

w.X = 42

fmt.Printf("%#v\n", w)
// Output:
// Wheel{Circle:Circle{Point:Point{X:42, Y:8}, Radius:5}, Spokes:20}
```

注意 `#` 修饰符如何导致 `Printf` 的 `%v` 动词以类似 Go 语法的形式显示值。对于结构体值，这种形式包含每个字段的名字。

因为“匿名”字段确实有隐式名字，所以你不能有两个相同类型的匿名字段，因为它们的名字会冲突。而且因为字段的名字由其类型隐式决定，所以字段的可见性也是如此。在上面的例子中，`Point` 和 `Circle` 匿名字段是导出的。如果它们是未导出的（`point` 和 `circle`），我们仍然可以使用简写形式

[点击此处查看代码图像](#part0134_split_064.html#id106pro04_r)

```
w.X = 8 // 等同于 w.circle.point.X = 8
```

但注释中显式的长形式将在声明包之外被禁止，因为 `circle` 和 `point` 将不可访问。

到目前为止我们看到的结构体嵌入，只是用于选择结构体字段的点表示法上的一点语法糖。稍后我们将看到，匿名字段不必是结构体类型；任何命名类型或指向命名类型的指针都可以。但为什么你想嵌入一个没有子字段的类型呢？

答案与方法有关。用于选择嵌入类型字段的简写表示法，同样适用于选择其方法。实际上，外部结构体类型不仅获得了嵌入类型的字段，还获得了它的方法。这种机制是将复杂对象行为从简单行为中组合起来的主要方式。`Composition`（组合）是 Go 面向对象编程的核心，我们将在 [6.3 节](#part0056.html#id-composition) 中进一步探讨它。

## 4.5 JSON

JavaScript Object Notation（JSON）是一种用于发送和接收结构化信息的标准表示法。JSON 不是唯一的此类表示法。XML（[§7.14](#part0074.html#id-exampletokenbasedxmldecoding)）、ASN.1 和 Google 的 Protocol Buffers 服务于类似的目的，各有其适用场景，但由于其简单性、可读性和通用支持，JSON 是应用最广泛的。

Go 通过标准库包 `encoding/json`、`encoding/xml`、`encoding/asn1` 等为这些格式的编码和解码提供了出色的支持，这些包都拥有相似的 API。本节简要概述 `encoding/json` 包最重要的部分。

JSON 是 JavaScript 值——字符串、数字、布尔值、数组和对象——作为 Unicode 文本的编码。它是第 3 章基本数据类型和本章复合类型——数组、切片、结构体和 map——的一种高效且可读的表示形式。

