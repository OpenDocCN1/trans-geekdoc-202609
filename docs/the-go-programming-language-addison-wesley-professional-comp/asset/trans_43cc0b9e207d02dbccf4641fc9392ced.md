

## 6.1 方法

### 方法调用与接收者

在方法调用中，接收者参数出现在方法名称之前。这与声明时的情况一致，在声明中接收者参数也出现在方法名称之前。

[点击此处查看代码图像](#part0136_split_003.html#id156pro02_r)

```go
p := Point{1, 2}
q := Point{4, 6}
fmt.Println(Distance(p, q)) // "5", 函数调用
fmt.Println(p.Distance(q))  // "5", 方法调用
```

上述两个名为 `Distance` 的函数声明之间没有冲突。第一个声明了一个包级函数 `geometry.Distance`。第二个声明了 `Point` 类型的一个方法，因此其名称为 `Point.Distance`。

### 选择器

表达式 `p.Distance` 被称为 *选择器*，因为它为类型为 `Point` 的接收者 `p` 选择了合适的 `Distance` 方法。选择器也用于选择结构体类型的字段，如 `p.X`。由于方法和字段处于同一命名空间，在结构体类型 `Point` 上声明一个名为 `X` 的方法会产生歧义，编译器会报错拒绝。

### 命名类型的方法

由于每个类型都有其自己的方法命名空间，我们可以为其他类型的方法使用 `Distance` 这个名字，只要它们属于不同的类型即可。让我们定义一个表示线段序列的 `Path` 类型，并为它也定义一个 `Distance` 方法。

[点击此处查看代码图像](#part0136_split_004.html#id156pro03_r)

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

`Path` 是一个命名的切片类型，而非像 `Point` 那样的结构体类型，但我们仍然可以为它定义方法。在允许将方法关联到任意类型这一点上，Go 语言与许多其他面向对象语言不同。为数字、字符串、切片、映射，有时甚至是函数等简单类型定义额外的行为通常很方便。只要底层类型既不是指针也不是接口，就可以在同一个包中为任何命名类型声明方法。

这两个 `Distance` 方法拥有不同的类型。它们彼此毫无关联，尽管 `Path.Distance` 在内部使用 `Point.Distance` 来计算连接相邻点的每个线段的长度。

### 方法名解析

让我们调用这个新方法来计算一个直角三角形的周长：

[点击此处查看代码图像](#part0136_split_005.html#id157pro01_r)

```go
perim := Path{
    {1, 1},
    {5, 1},
    {5, 4},
    {1, 1},
}
fmt.Println(perim.Distance()) // "12"
```

在上面两个对名为 `Distance` 的方法的调用中，编译器根据方法名和接收者的类型来决定调用哪个函数。在第一个调用中，`path[i-1]` 的类型是 `Point`，因此调用 `Point.Distance`；在第二个调用中，`perim` 的类型是 `Path`，因此调用 `Path.Distance`。

### 方法的优势

给定类型的所有方法必须拥有唯一的名称，但不同类型可以为方法使用相同的名称，就像 `Point` 和 `Path` 的 `Distance` 方法那样；无需通过限定函数名（例如 `PathDistance`）来消除歧义。在这里我们看到了使用方法而非普通函数的第一个好处：方法名可以更短。对于包外部发起的调用，这一优势更加明显，因为它们可以使用更短的名称*并*省略包名：

[点击此处查看代码图像](#part0136_split_006.html#id157pro02_r)

```go
import "gopl.io/ch6/geometry"

perim := geometry.Path{{1, 1}, {5, 1}, {5, 4}, {1, 1}}
fmt.Println(geometry.PathDistance(perim)) // "12", 独立函数
fmt.Println(perim.Distance())             // "12", geometry.Path 的方法
```

## 6.2 指针接收者的方法

### 指针接收者声明

因为调用函数会对每个参数值进行复制，如果函数需要更新一个变量，或者参数太大我们希望避免复制，就必须传递该变量的地址（即指针）。对于需要更新接收者变量的方法也是如此：我们将它们绑定到指针类型，例如 `*Point`。

[点击此处查看代码图像](#part0136_split_007.html#id158pro01_r)

```go
func (p *Point) ScaleBy(factor float64) {
    p.X *= factor
    p.Y *= factor
}
```

该方法的名称为 `(*Point).ScaleBy`。括号是必需的；没有括号，该表达式会被解析为 `*(Point.ScaleBy)`。

在实际程序中，惯例规定：如果 `Point` 的任意方法使用了指针接收者，那么 `Point` 的*所有*方法都应该使用指针接收者，即使有些方法并不严格要求这样做。我们在 `Point` 上打破了这条规则，以便展示两种方法。

命名类型（`Point`）及其指针（`*Point`）是唯一可以出现在接收者声明中的类型。此外，为了避免歧义，不允许在本身就是指针类型的命名类型上声明方法：

[点击此处查看代码图像](#part0136_split_008.html#id158pro02_r)

```go
type P *int
func (P) f() { /* ... */ } // 编译错误：无效的接收者类型
```

### 调用指针接收者的方法

`(*Point).ScaleBy` 方法可以通过提供一个 `*Point` 接收者来调用，如下所示：

```go
r := &Point{1, 2}
r.ScaleBy(2)
fmt.Println(*r) // "{2, 4}"
```

或者这样：

```go
p := Point{1, 2}
pptr := &p
pptr.ScaleBy(2)
fmt.Println(p) // "{2, 4}"
```

或者这样：

```go
p := Point{1, 2}
(&p).ScaleBy(2)
fmt.Println(p) // "{2, 4}"
```

但后两种情况比较笨拙。幸运的是，语言在这方面帮了我们。如果接收者 `p` 是类型为 `Point` 的*变量*，但方法需要 `*Point` 接收者，我们可以使用这种简写：

```go
p.ScaleBy(2)
```

编译器会对变量隐式执行 `&p` 操作。这仅适用于变量，包括结构体字段如 `p.X` 和数组或切片元素如 `perim[0]`。我们不能在不可寻址的 `Point` 接收者上调用 `*Point` 方法，因为无法获取临时值的地址。

[点击此处查看代码图像](#part0136_split_009.html#id159pro01_r)

```go
Point{1, 2}.ScaleBy(2) // 编译错误：无法获取 Point 字面量的地址
```

### 隐式取地址与解引用

但我们*可以*用 `*Point` 接收者调用像 `Point.Distance` 这样的 `Point` 方法，因为有一种方法可以从地址获取值：只需加载接收者指向的值。编译器会为我们插入一个隐式的 `*` 操作。这两个函数调用是等价的：

```go
pptr.Distance(q)
(*pptr).Distance(q)
```

### 接收者参数规则总结

让我们再次总结这三种情况，因为它们是常见的困惑点。在每一个合法的方法调用表达式中，以下三个陈述恰好有一个为真。

要么接收者参数与接收者形参具有相同的类型，例如两者都是类型 `T` 或都是类型 `*T`：

[点击此处查看代码图像](#part0136_split_010.html#id159pro02_r)

```go
Point{1, 2}.Distance(q) //  Point
pptr.ScaleBy(2)         // *Point
```

要么接收者参数是类型 `T` 的*变量*，而接收者形参类型为 `*T`。编译器隐式地取变量的地址：

```go
p.ScaleBy(2) // 隐式 (&p)
```

要么接收者参数类型为 `*T`，而接收者形参类型为 `T`。编译器隐式地解引用接收者，即加载该值：

[点击此处查看代码图像](#part0136_split_011.html#id159pro03_r)

```go
pptr.Distance(q) // 隐式 (*pptr)
```

