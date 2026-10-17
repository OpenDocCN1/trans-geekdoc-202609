
## 重构

我们的代码可以工作，但它没有明确提及矩形。一个粗心的开发者可能会尝试向这些函数提供三角形的宽度和高度，而没有意识到它们会返回错误的结果。

我们可以给函数起更具体的名称，比如 `RectangleArea`。更优雅的解决方案是定义我们自己的 `type` 称为 `Rectangle`，它为我们封装了这个概念。

我们可以使用一个 `struct` 创建一个简单类型。结构体只是一个命名字段的集合，你可以在其中存储数据。

像这样声明一个结构体

```go
type Rectangle struct {
    Width  float64
    Height float64
}
```

现在让我们重构测试，使用 `Rectangle` 而不是普通的 `float64`s。

```go
func TestPerimeter(t *testing.T) {
    rectangle := Rectangle{10.0, 10.0}
    got := Perimeter(rectangle)
    want := 40.0

    if got != want {
        t.Errorf("got %.2f want %.2f", got, want)
    }
}

func TestArea(t *testing.T) {
    rectangle := Rectangle{12.0, 6.0}
    got := Area(rectangle)
    want := 72.0

    if got != want {
        t.Errorf("got %.2f want %.2f", got, want)
    }
}
```

在尝试修复之前请记得运行你的测试。测试应该显示一个有帮助的错误，例如

```
./shapes_test.go:7:18:  not enough arguments in call to Perimeter
    have (Rectangle)
    want (float64, float64)
```

你可以使用 `myStruct.field` 的语法访问结构体的字段。

修改这两个函数以修复测试。

```go
func Perimeter(rectangle Rectangle) float64 {
    return 2 * (rectangle.Width + rectangle.Height)
}

func Area(rectangle Rectangle) float64 {
    return rectangle.Width * rectangle.Height
}
```

我希望你会同意，将 `Rectangle` 传递给函数能更清晰地表达我们的意图，但使用结构体还有更多好处，我们稍后会介绍。

我们的下一个需求是为圆编写一个 `Area` 函数。

## 先写测试

```go
func TestArea(t *testing.T) {
    t.Run("rectangles", func(t *testing.T) {
        rectangle := Rectangle{12, 6}
        got := Area(rectangle)
        want := 72.0

        if got != want {
            t.Errorf("got %g want %g", got, want)
        }
    })

    t.Run("circles", func(t *testing.T) {
        circle := Circle{10}
        got := Area(circle)
        want := 314.1592653589793

        if got != want {
            t.Errorf("got %g want %g", got, want)
        }
    })
}
```

如你所见，`f` 已被 `g` 替换，有其原因。使用 `g` 会在错误消息中打印更精确的小数（`fmt` 选项）。例如，使用半径 1.5 计算圆面积，`f` 会显示 7.068583，而 `g` 会显示 7.0685834705770345。

## 尝试运行测试

```
./shapes_test.go:28:13: undefined: Circle
```

## 为测试运行编写最少量的代码并检查失败的测试输出

我们需要定义我们的 `Circle` 类型。

```go
type Circle struct {
    Radius float64
}
```

现在再次尝试运行测试

```
./shapes_test.go:29:14: cannot use circle (type Circle) as type Rectangle in argument to Area
```

一些编程语言允许你这样做：

```go
func Area(circle Circle) float64     {}

func Area(rectangle Rectangle) float64 {}
```

但在 Go 中不行

```
./shapes.go:20:32: Area redeclared in this block
```

我们有两个选择：

- 你可以在不同的 `packages` 中声明同名函数。因此我们可以将 `Area(Circle)` 创建在新包中，但在这里感觉太过分了。

- 我们可以在新定义的类型上定义 [`方法`](#) 代替。

## 什么是方法？

到目前为止我们只编写了 `functions`，但我们使用了一些方法。当我们调用 `t.Errorf` 时，我们是在 `t` (`testing.T`) 的实例上调用方法 `Errorf`。

```
./shapes_test.go:29:16: circle.Area undefined (type Circle has no field or method Area)
```

## Circle 类型没有字段或方法 Area

我想再次强调，这里的编译器有多么出色。花时间慢慢阅读你得到的错误信息非常重要，从长远来看，这会帮助你。

## 编写最少的代码，让测试运行并检查失败的测试输出

## 为我们的类型添加一些方法

```go
type Rectangle struct {
    Width  float64
    Height float64
}

func (r Rectangle) Area() float64 {
    return 0
}

type Circle struct {
    Radius float64
}

func (c Circle) Area() float64 {
    return 0
}
```

声明方法的语法几乎与函数相同，那是因为它们非常相似。唯一的区别在于方法接收者的语法：`func (receiverName ReceiverType) MethodName(args)`。

当你的方法在该类型的变量上被调用时，你通过 `receiverName` 变量获取对数据的引用。在许多其他编程语言中，这是隐式完成的，你通过 `this` 访问接收者。

在 Go 中，约定是让接收者变量为类型的首字母。

```
r Rectangle
```

如果你尝试重新运行测试，它们现在应该能够编译，并给你一些失败的输出。

## 编写足够的代码让它通过

现在，让我们通过修复新方法来让矩形测试通过。

```go
func (r Rectangle) Area() float64 {
    return r.Width * r.Height
}
```

如果你重新运行测试，矩形测试应该通过，但 Circle 测试仍然会失败。

为了让 Circle 的 `Area` 函数通过，我们将借用 `math` 包中的 `Pi` 常量（记得导入它）。

```go
func (c Circle) Area() float64 {
    return math.Pi * c.Radius * c.Radius
}
```

## 重构

我们的测试中有一些重复。

我们想做的只是拿一组 `图形`，对它们调用 `Area()` 方法，然后检查结果。

我们希望能够编写一个 `checkArea` 函数，既能传入 `Rectangles` 和 `Circles`，但如果我们试图传入不是图形的东西，就会编译失败。

使用 Go，我们可以用 `接口` 将这种意图明确地表达出来。

[接口]() 在像 Go 这样的静态类型语言中是一个非常强大的概念，因为它们允许你创建可以用于不同类型的函数，并生成高度解耦的代码，同时仍然保持类型安全。

让我们通过重构测试来引入这一点。

```go
func TestArea(t *testing.T) {

    checkArea := func(t testing.TB, shape Shape, want float64) {
        t.Helper()
        got := shape.Area()
        if got != want {
            t.Errorf("got %g want %g", got, want)
        }
    }

    t.Run("rectangles", func(t *testing.T) {
        rectangle := Rectangle{12, 6}
        checkArea(t, rectangle, 72.0)
    })

    t.Run("circles", func(t *testing.T) {
        circle := Circle{10}
        checkArea(t, circle, 314.1592653589793)
    })
}
```

我们正在创建一个辅助函数，就像我们在其他练习中一样，但这次我们要求传入一个 `Shape`。如果我们试图用不是图形的东西调用它，那么它就不会编译。

一个东西怎样才能成为一个图形？我们只需使用接口声明告诉 Go 什么是 `Shape`。

```go
type Shape interface {
    Area() float64
}
```

我们正在创建一个新类型，就像我们创建 `Rectangle` 和 `Circle` 一样，但这次它是一个接口，而不是结构体。

一旦你把它添加到代码中，测试就会通过。

## 等等，什么？

这与大多数其他编程语言中的接口非常不同。通常你必须编写代码来说明“我的类型 `Foo` 实现了接口 `Bar`”。

但在我们的情况中

- `Rectangle` 有一个名为 `Area` 的方法，返回 `float64`，因此它满足 `Shape` 接口

- `Circle` 有一个名为 `Area` 的方法，返回 `float64`，因此它满足 `Shape` 接口

- `string` 没有这样的方法，所以它不满足该接口

- 等等。

在 Go 中，**接口解析是隐式的**。如果你传入的类型符合接口的要求，它就会编译。

## 解耦

注意我们的辅助函数不需要关心图形是 `Rectangle`、`Circle` 还是 `Triangle`。通过声明一个接口，辅助函数与具体类型解耦，并且只需要它完成工作所需的方法。

这种使用接口只声明**你所需内容**的方法在软件设计中非常重要，将在后面的章节中更详细地介绍。

## 进一步重构

既然你对结构体有了一些理解，我们就可以引入“表驱动测试”。

[表驱动测试](Table driven tests) 在你想构建一组可以用相同方式测试的测试用例时非常有用。

```go
func TestArea(t *testing.T) {
    areaTests := []struct {
        shape Shape
        want  float64
    }{
        {Rectangle{12, 6}, 72.0},
        {Circle{10}, 314.1592653589793},
    }

    for _, tt := range areaTests {
        got := tt.shape.Area()
        if got != tt.want {
            t.Errorf("got %g want %g", got, tt.want)
        }
    }
}
```

这里唯一的新语法是创建一个“匿名结构体” `areaTests`。我们使用 `[]struct` 声明一个结构体切片，带有两个字段：`shape` 和 `want`。然后我们用各种用例填充这个切片。

然后我们像遍历任何其他切片一样遍历它们，使用结构体字段运行测试。

你可以看到，开发者要引入一个新图形、实现 `Area`、然后把它添加到测试用例中，是多么容易。此外，如果发现 `Area` 有 bug，在修复之前也很容易添加一个新的测试用例来复现它。

表驱动测试可以是你工具箱中的一件利器，但要确保你确实需要测试中的这些额外噪音。当你希望测试一个接口的多种实现，或者传给函数的数据有很多不同的需求需要测试时，它们是非常合适的。

让我们通过添加并测试另一个图形来演示这一切：三角形。

## 先编写测试

为我们的新图形添加一个新测试非常容易。只需将 `{Triangle{12, 6}, 36.0},` 添加到我们的列表中。

```go
func TestArea(t *testing.T) {

    areaTests := []struct {
        shape Shape
        want  float64
    }{
        {Rectangle{12, 6}, 72.0},
        {Circle{10}, 314.1592653589793},
        {Triangle{12, 6}, 36.0},
    }

    for _, tt := range areaTests {
        got := tt.shape.Area()
        if got != tt.want {
            t.Errorf("got %g want %g", got, tt.want)
        }
    }
}
```

## 尝试运行测试

记住，不断尝试运行测试，并让编译器引导你找到解决方案。

## 编写最少的代码，让测试运行并检查失败的测试输出

```
./shapes_test.go:25:4: undefined: Triangle
```

我们还没有定义 `Triangle`。

```go
type Triangle struct {
    Base    float64
    Height  float64
}
```

再试一次。

```
./shapes_test.go:25:8: cannot use Triangle literal (type Triangle) as type Shape in field value:
    Triangle does not implement Shape (missing Area method)
```

它告诉我们，不能将 `Triangle` 用作图形，因为它没有 `Area()` 方法，所以添加一个空实现来让测试工作。

```go
func (t Triangle) Area() float64 {
    return 0
}
```

最终代码编译通过，我们得到了错误：

```
shapes_test.go:31: got 0.00 want 36.00
```

## 编写足够的代码让它通过

```go
func (t Triangle) Area() float64 {
    return (t.Base * t.Height) * 0.5
}
```

然后我们的测试通过了！

## 重构

同样，实现没有问题，但我们的测试可以做一些改进。

当你看到这段代码时：

```
{Rectangle{12, 6}, 72.0},
{Circle{10}, 314.1592653589793},
{Triangle{12, 6}, 36.0},
```

这些数字代表什么并不是一目了然，而你应该努力让你的测试易于理解。

到目前为止，你只看到了创建结构体实例的语法 `MyStruct{val1, val2}`，但你也可以选择给字段命名。

让我们看看它长什么样：

```
{shape: Rectangle{Width: 12, Height: 6}, want: 72.0},
{shape: Circle{Radius: 10}, want: 314.1592653589793},
{shape: Triangle{Base: 12, Height: 6}, want: 36.0},
```

在《Test-Driven Development by Example》中，Kent Beck 将一些测试重构到某一点，并断言：

> 测试能更清晰地向我们表达，仿佛它是一种对真相的断言，**而非一系列操作**

（引文中的强调是我加的。）

现在我们的测试——更准确地说，是测试用例列表——对形状及其面积做出了真值断言。

## 确保你的测试输出有帮助

请记住我们之前在实现 `Triangle` 时遇到的失败测试？它打印了 `shapes_test.go:31: got 0.00 want 36.00`。

我们知道这与 `Triangle` 有关，因为我们当时正好在处理它。但如果系统在表格中的 20 个用例之一中出现了 bug，开发者如何知道哪个用例失败了？这对开发者来说不是很好的体验，他们必须手动查看用例才能找出实际失败的用例。

我们可以将错误信息改为 `%#v got %g want %g`。`%#v` 格式字符串会打印出结构体及其字段中的值，这样开发者可以一目了然地看到正在测试的属性。

为了进一步提高测试用例的可读性，我们可以将 `want` 字段重命名为更具描述性的名称，例如 `hasArea`。

使用表驱动测试的最后一个小技巧是使用 `t.Run` 并为测试用例命名。
