

```go
func (fuzzy *FuzzyBool) Equal(other *FuzzyBool) bool {
  return fuzzy.value == other.value
}
```

这两个方法允许我们根据它们包含的 float32 值来比较模糊布尔值；两者都会产生布尔结果。

```go
func (fuzzy *FuzzyBool) Bool() bool {
  return fuzzy.value >= .5
}

func (fuzzy *FuzzyBool) Float() float64 {
  return float64(fuzzy.value)
}
```

`fuzzybool.New()` 构造函数可以看作是一个转换函数，因为给定的一个 float32、64、int 或 bool，它就能产生一个 *FuzzyBool*。这两个方法执行了相反方向的类似转换。

`FuzzyBool` 类型提供了一个完整的布尔数据类型，可以像任何其他自定义数据类型一样使用。因此，*FuzzyBool 可以存储在切片中，也可以作为 map 的键或值存储*。或者，如果我们使用 *FuzzyBool 作为键，即使它们的值相同，我们也将能够存储多个模糊布尔值，因为每个值都有唯一的地址。一种解决方案是使用基于值的 FuzzyBool（例如书籍源代码中的模糊值示例）。另一种是我们可以使用一种存储指针但使用其值进行比较的自定义集合类型：自定义 map 可以映射到这一点，并提供一个合适的“小于”函数 (6.5.3, ► 302)。

除了本节所示的模糊布尔类型外，书籍示例中还包含了三种可选的模糊布尔实现以供比较：这些在书中没有显示，在本段落之后也没有讨论。第一种可选方案位于 `fuzzybool/fuzzybool.go` 和 `fuzzy_mutable/fuzzybool.go` 文件中——它们的功能与本节描述的版本（在 `fuzzybool/fuzzy.go` 文件中）完全相同。模糊值是基于 Fuzzy 布尔值而非 *FuzzyBools* 运行的，而模糊可变版本是直接基于 float32 而不是结构体。模糊可变版本的代码比这里显示的基于结构体的版本稍长且更复杂一些。第三种可选方案提供的功能稍少一点，因为它提供了一个不可变的模糊布尔类型。同样，它直接基于一个 float32；该版本位于 `immutable/fuzzy-bool/fuzzybool.go` 文件中。它是三种实现中最简单的。

## 6.5. 示例

## 6.5.2. 示例：形状——自定义类型族

当我们拥有一组相关的类（例如形状）并并且我们可能想在其上面应用某些泛型操作（例如，让形状自己绘制自己）时，有两种宽泛的方法可以来实现它们。最可能让 C++、Java 和 Python 程序员熟悉的方法是使用层级结构——在 Go 的情况下是使用嵌入接口。然而，创建可以自由组合的独立接口通常更方便、更多变。在本节中，我们将展示这两种方法，第一种在 `shape1/shapes.go` 中，第二种在 `shape2/shapes.go` 中。（注意，当“包”（packages）的类型、函数和方法相同时——它们大多数都是如此——我们将简单地称为“shapes 包”。自然地，在讨论特定于某一个包的代码时，我们将它们区分为“shape1 包”或“shape2 shapes 包”。）

图 6.3 显示了 `shapes` 包可以做的事情的一个示例——在本例中，它被用于创建一个白色矩形，并在上面画一个圆和一些具有不同边数并使用不同颜的多边形。

![](img/005bb569dac79e0facc29f476bd67ade_305_0.png)

图 6.3 shaper 示例的 shapes.png 文件

`shapes` 包提供了三个用于处理图像的导出函数和三个用于创建形状值的类型——其中两个是导出的。层级结构的 `shape1 shapes` 包提供了三个导出的接口，而组合的 `shape2 shapes` 包提供了五个导出的接口。我们将从与图像相关的代码——便利函数开始，然后查看接口（在两个独立的子节中），最后，我们将回顾具体的形状相关的代码。

### 6.5.2.1. 包 级便利函数

标准库的 `image` 包提供了 `image.Image` 接口。该接口提供了三个方法：`image.ColorModel()` 返回颜色模型（作为 `color.Model`），`image.Bounds()` 返回图像的边界框（作为 `image.Rectangle`），以及 `image.At(x, y)` 返回给定像素的颜色。注意，没有用于设置像素的 `image.Image` 方法——尽管几个图像类型都提供了 `Set(x, y, color.Color)` 方法。

# 第 6 章 面对象编程

然而，`image/draw` 包提供了 `draw.Image` 接口，它嵌入了 `image.Image` 接口，并且也有 `Set(x, y)` 方法。`draw.Image` 接口由标准库的 `image.Draw` 和 `img.RGBA` 类型实现。

```go
func FilledImage(width, height int, fill color.Color) draw.Image {
	if fill == nil { // 我们静默地将空颜色视为黑色
		fill = color.Black
	}
	width = saneLength(width)
	height = saneLength(height)
	img := image.NewRGBA(image.Rect(0, 0, width, height))
	draw.Draw(img, img.Bounds(), &image.Uniform{fill}, image.Point{}, draw.Src)
}
```

这是一个创建图像的便利函数。我们首先简单地将空颜色替换为黑色，确保尺寸是合理的。`draw.Draw` 函数接收一个目标图像、一个源图像、一个起点和一个指定如何进行绘制的操作（即 `draw.Src`）。`draw.Image` 接口由标准库的 `image.Draw` 和 `img.RGBA` 类型实现。

```go
var saneLength, saneRadius, saneSides func(int) int

func init() {
	saneLength = makeBoundedFunc(1, 4096)
	saneRadius = makeBoundedFunc(1, 1024)
	saneSides = makeBoundedFunc(1, 60)
}
```

我们定义了三个导出变量来持有函数，它们都接收一个 int 并返回一个 int。

```go
func makeBoundedFunc(minimum, maximum int) func(int) int {
	return func(x int) int {
		valid := x
		switch {
		case x < minimum:
			valid = minimum
		case x > maximum:
			valid = maximum
		}
		if valid != x {
			log.Printf("%s(): replaced %d with %d\n", caller(1), x, valid)
		}
		return valid
	}
}
```

该函数返回一个函数，该函数在给定值在 minimum 和 maximum 之间时返回 x，否则返回最接近的值。如果 x 超出，除了返回一个有效的替代值外，我们还记录了问题。我们不想报告问题存在于此处函数（即在 `saneLength()`、`saneRadius()` 或 `saneSides()` 中），因为问题属于它们的调用者。因此，我们不是记录此处创建的函数的名称，而是使用自定义 `caller()` 记录调用者的名称。

```go
func caller(steps int) string {
    name := "?"
    if pc, _, ok := runtime.Caller(steps + 1); ok {
        name = filepath.Base(runtime.FuncForPC(pc).Name())
    }
    return name
}
```

`runtime.Caller()` 函数提供了关于当前 goroutine 中已调用但尚未返回函数的信息。int 参数表示我们想要查看多远（即多少个函数）。参数为 0 查看当前函数（即 `this.caller()`），参数为 1 查看此函数的调用者，依此类推。我们加上 1 以从此函数的调用者开始。

