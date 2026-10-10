

# gopl.io/ch6/geometry

```go
package geometry

import "math"

type Point struct{ X, Y float64 }

// 传统函数
func Distance(p, q Point) float64 {
    return math.Hypot(q.X-p.X, q.Y-p.Y)
}

// 同样的功能，但作为 Point 类型的方法
func (p Point) Distance(q Point) float64 {
    return math.Hypot(q.X-p.X, q.Y-p.Y)
}
```

额外的参数 `p` 称为方法的 **接收器**，这是早期面向对象语言的遗留术语，那些语言将调用方法描述为“向对象发送消息”。

在 Go 中，我们不像其他语言那样使用 `this` 或 `self` 这种特殊名称作为接收器；我们选择接收器名称的方式与选择其他参数名称的方式相同。由于接收器名称会被频繁使用，最好选择简短的名称，并在所有方法中保持一致。常见的做法是使用类型名称的首字母，例如 `Point` 使用 `p`。

在方法调用中，接收器实参出现在方法名之前。这与声明时的顺序一致，在声明中接收器参数出现在方法名之前。

[点击此处查看代码图像](#ch06_images.html#id156pro02_r)

```go
p := Point{1, 2}
q := Point{4, 6}
fmt.Println(Distance(p, q)) // "5", 函数调用
fmt.Println(p.Distance(q))  // "5", 方法调用
```

上述两个名为 `Distance` 的函数声明之间不存在冲突。第一个声明了一个包级函数 `geometry.Distance`。第二个声明了 `Point` 类型的方法，因此其名称为 `Point.Distance`。

表达式 `p.Distance` 称为 **选择器**，因为它为类型为 `Point` 的接收器 `p` 选择了合适的 `Distance` 方法。选择器也用于选择结构体类型的字段，如 `p.X`。由于方法和字段处于同一命名空间，在结构体类型 `Point` 上声明方法 `X` 会产生歧义，编译器会报错拒绝。

因为每个类型都有自己的方法命名空间，我们可以为其他类型的方法使用相同的名称 `Distance`。让我们定义一个表示线段序列的 `Path` 类型，并为它也定义一个 `Distance` 方法。

[点击此处查看代码图像](#ch06_images.html#id156pro03_r)

```go
// Path 表示由直线连接各点形成的路径。
type Path []Point

// Distance 返回沿路径行进的距离。
func (path Path) Distance() float64 {
    sum := 0.0
    for i := range path {
        if i > 0 {
            sum += path[i-1].Distance(path[i])
        }
    }
    return sum
}
```

`Path` 是一个命名的切片类型，而非像 `Point` 那样的结构体类型，但我们仍然可以为它定义方法。在允许将方法关联到任意类型这点上，Go 与许多其他面向对象语言不同。为数字、字符串、切片、映射等简单类型，有时甚至为函数定义额外的行为通常很方便。只要在同一个包中定义了命名类型，且其底层类型既不是指针也不是接口，就可以为其声明方法。

这两个 `Distance` 方法拥有不同的类型。它们彼此毫无关联，尽管 `Path.Distance` 在内部使用 `Point.Distance` 来计算连接相邻点的每个线段的长度。

让我们调用这个新方法来计算一个直角三角形的周长：

[点击此处查看代码图像](#ch06_images.html#id157pro01_r)

```go
perim := Path{
    {1, 1},
    {5, 1},
    {5, 4},
    {1, 1},
}
fmt.Println(perim.Distance()) // "12"
```

![Image](graphics/triangle.png)

在上述两个调用名为 `Distance` 的方法的代码中，编译器根据方法名和接收器的类型来决定调用哪个函数。在第一个调用中，`path[i-1]` 的类型是 `Point`，因此调用 `Point.Distance`；在第二个调用中，`perim` 的类型是 `Path`，因此调用 `Path.Distance`。

给定类型的所有方法必须具有唯一的名称，但不同类型可以为方法使用相同的名称，就像 `Point` 和 `Path` 的 `Distance` 方法那样；无需通过限定函数名（例如 `PathDistance`）来消除歧义。这里我们看到了使用方法而非普通函数的第一个好处：方法名可以更短。对于包外部的调用，这一优势更加明显，因为它们既可以使用较短的名称，又可以省略包名：

[点击此处查看代码图像](#ch06_images.html#id157pro02_r)

```go
import "gopl.io/ch6/geometry"

perim := geometry.Path{{1, 1}, {5, 1}, {5, 4}, {1, 1}}
fmt.Println(geometry.PathDistance(perim)) // "12", 独立函数
fmt.Println(perim.Distance())             // "12", geometry.Path 的方法
```

## 6.2 指针接收器的方法

因为调用函数会对每个实参值进行拷贝，如果函数需要更新变量，或者实参过大导致我们希望避免拷贝，就必须传递变量的地址，即使用指针。对于需要更新接收器变量的方法也是如此：我们将它们绑定到指针类型，例如 `*Point`。

[点击此处查看代码图像](#ch06_images.html#id158pro01_r)

```go
func (p *Point) ScaleBy(factor float64) {
    p.X *= factor
    p.Y *= factor
}
```

该方法的名称是 `(*Point).ScaleBy`。括号是必需的；没有括号，该表达式会被解析为 `*(Point.ScaleBy)`。

在实际编程中，惯例规定：如果 `Point` 的任意方法使用了指针接收器，那么 `Point` 的 **所有** 方法都应该使用指针接收器，即使是那些并不严格需要指针接收器的方法。我们在 `Point` 上打破了这条规则，以便展示两种方法。

只有命名类型（`Point`）及其指针（`*Point`）才能出现在接收器声明中。此外，为了避免歧义，不允许在本身就是指针类型的命名类型上声明方法：

[点击此处查看代码图像](#ch06_images.html#id158pro02_r)

```go
type P *int
func (P) f() { /* ... */ } // 编译错误：无效的接收器类型
```

`(*Point).ScaleBy` 方法可以通过提供 `*Point` 接收器来调用，如下所示：

```go
r := &Point{1, 2}
r.ScaleBy(2)
fmt.Println(*r) // "{2, 4}"
```

或这样：

```go
p := Point{1, 2}
pptr := &p
pptr.ScaleBy(2)
fmt.Println(p) // "{2, 4}"
```

或这样：

```go
p := Point{1, 2}
(&p).ScaleBy(2)
fmt.Println(p) // "{2, 4}"
```

但后两种方式显得笨拙。幸运的是，语言对此提供了帮助。如果接收器 `p` 是类型为 `Point` 的 **变量**，但方法需要 `*Point` 接收器，我们可以使用这种简写：

```go
p.ScaleBy(2)
```

编译器会对变量隐式执行 `&p` 操作。这仅适用于变量，包括结构体字段（如 `p.X`）和数组或切片元素（如 `perim[0]`）。我们不能在不可寻址的 `Point` 接收器上调用 `*Point` 方法，因为无法获取临时值的地址。

[点击此处查看代码图像](#ch06_images.html#id159pro01_r)

```go
Point{1, 2}.ScaleBy(2) // 编译错误：无法获取 Point 字面量的地址
```

但我们 **可以** 使用 `*Point` 接收器调用像 `Point.Distance` 这样的 `Point` 方法，因为可以通过地址获取值：只需加载接收器指向的值。编译器会为我们隐式插入 `*` 操作。这两个函数调用是等价的：

```go
pptr.Distance(q)
(*pptr).Distance(q)
```

让我们再次总结这三种情况，因为它们是常见的困惑点。在每一个合法的方法调用表达式中，以下三个陈述恰好有一个为真。

要么实参接收器与形参接收器具有相同的类型，例如都是类型 `T` 或都是类型 `*T`：

[点击此处查看代码图像](#ch06_images.html#id159pro02_r)

```go
Point{1, 2}.Distance(q) //  Point
pptr.ScaleBy(2)         // *Point
```

要么实参接收器是类型 `T` 的 **变量**，而形参接收器类型为 `*T`。编译器会隐式获取变量的地址：

```go
p.ScaleBy(2) // 隐式 (&p)
```

