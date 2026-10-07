
尽管 `name()` 函数的处理非常简单，但我们选择使用独立函数而不是在 `IntOption.Name()` 方法中实现它。这使得方法变得很短，并且我们可以在其他选项中复用该功能。`GenericOption.Name()` 和 `StringOption.Name()` 方法与 `IntOption.Name()` 方法的主体相同。这是 Go 中的一种常见模式，差异在于它的 `Value` 字段类型是字符串，且它的 `IsValid()` 方法在 `Value` 非空时返回 `true`。对于 `FloatOption`，我们使用了接口嵌入来展示它是如何做的。

```go
type FloatOption struct {
    Optioner // 匿名字段（嵌入：需要具体类型）
    Value float64 // 具名字段（聚合）
}
```

这是 `FloatOption` 的完整实现。嵌入的 `Optioner` 字段意味着当我们创建 `FloatOption` 值时，必须分配满足 `Optioner` 接口的数值。

```go
type GenericOption struct {
    OptionCommon // 匿名字段（嵌入）
}
func (option GenericOption) Name() string {
    return name(option.ShortName, option.LongName)
}

func (option GenericOption) IsValid() bool {
  return true
}
```

这是 `GenericOption` 的完整实现。`FloatOption` 类型有一个嵌入的 `Optioner`，所以 `FloatOption` 值需要一个满足 `Optioner` 接口的具体类型。现在我们已经有了所有部分（`IntOption`、`FloatOption` 等），让我们看看如何创建和使用它们。

```go
floatOption := StringOption(OptionCommon{"f"
```

```
name-top = valid=true * value=0 * max=100
name-file = valid=true * value=index.html
name-size = valid=true * value=19.5
```

`fileOption` 是按照惯创建的，每个字段都分配了合适的值。但对于 `topOption`，我们只需要为 `OptionCommon` 和 `Max` 字段赋值。Go 允许我们通过 `fieldName:fieldValue` 语法创建结构体并初始化我们需要的字段。未显式分配的字段将自动设置为它们的零值。`FloatOption` 的第一个字段是 `Optioner` 接口，我们可以使用 `[]Optioner`（满足接口值的切片）遍历它们。在循环中，`option` 变量持有每个选项（`IntOption`）。我们可以通过调用 `Name()` 和 `IsValid()` 调用 `Optioner` 接口指定的任何方法。每个选项类型都有 `Value` 字段，但它们是不同的类型——例如 `IntOption` 是 `int`，所以为了能够访问 `Value` 特有的字段（以及其他类型特定的字段），必须将给定的选项转换为正确的类型。这通过 `type switch` 很容易于实现。

## 6.5 示例

现在我们已经知道了如何创建自定义类型，准备好查看一些真实的示例了。第一个示例展示了如何创建一个自定义值。第二个示例展示了如何使用嵌入创建一组相关的结构体，并提供一个可以创建所有导出类型的工厂函数。第三个示例展示了如何实现一个完整的泛型类型。

### 6.5.1 示例：FuzzyBool——单一类型

在本节中，我们将学习如何创建一个单一类型及其支持的方法。此示例位于 `fuzzy/fuzzybool.go` 并基于结构体。内置的 `bool` 类型是二（true 和 false），但在某些领域使用了模糊布尔值。这些值对应于 "true" 和 "false"，以及它们之间的中间值。在我们的实现中，我们使用浮点值，`0.0` 表示 false，`1.0` 表示 true。在这个系统中，`0.5` 表示 50% true（50% false），`0.25` 表示 25% true（75% false），依此类推。以下是一些用法示例及其产生的结果。

```go
func main() {
	a := fuzzy.New(0) // 忽略错误是
	b := fuzzy.New(.25) // 已知的有效值；检查是否使用
	c := fuzzy.New(.75) // 尽管是变量。
	d := c.Copy()
	if err := d.Set(1); err != nil {
		fmt.Println(err)
	}
	process(a, b, c)
	s := []*FuzzyBool{a, b, c, d}
	fmt.Println(s)
}

func process(a, b, c, d *FuzzyBool) {
	fmt.Println("Not:", a.Not(), b.Not(), c.Not())
	fmt.Println("Not Not:", a.Not().Not(), b.Not().Not(), c.Not().Not(), d.Not().Not())
	fmt.Printf("And(.25):%v, .25.And(.75,1):%v, .75.And(1):%v\n", a.And(b), b.And(c), c.And(d))
	fmt.Printf("Or(.25):%v, .25.Or(.75):%v, .75.Or(1):%v\n", a.Or(b), b.Or(c), c.Or(d))
	fmt.Println("Bool: ", a.Bool())
	fmt.Println("Bool: < a, c = a, c: >", a.Less(c), a.Equal(c), c.Less(a))
	fmt.Println("Bool:", a.Bool(), b.Bool(), c.Bool(), d.Bool())
	fmt.Println("Float:", a.Float(), b.Float(), d.Float())
}
```

# 284 第 6 章 对象面向编程

（约定），用于创建模糊布尔（Fuzzy Booleans）。当然，这可以确保只创建有效的模糊布尔。

由于 `FuzzyBool` 类型基于包含一个值的结构体，该值的类型在结构体内部，我们可以将类型简化为 `type FuzzyBool struct { float32 }`。这意味着需要更改访问值的代码——我们将在其中一个方法中看到——将 `fuzzy.value` 改为 `fuzzy.float32`。我们倾向于使用命名变量，部分是因为我们觉得它更符合审美，另一部分是因为如果我们想更改底层类型（例如改为 `float64`），需要做的更改会更少。

由于结构体只包含一个值，因此还有其他变体。例如，我们可以将类型更改为 `type FuzzyBool float32`，使其直接基于 `float32`。这样做效果良好，但需要稍多代码，并且对于实现我们使用的基于结构体的方法来说会稍微复杂一些。

然而，如果我们将自己限制在创建不可变的模糊布尔（唯一的区别是，不再通过 `Set()` 方法设置值，而是必须分配一个新的模糊布尔），我们可以通过直接基于 `float32` 类型来大大简化代码。

```go
func New(value interface{}) (*FuzzyBool, error) {
    amount, err := float32ForValue(value)
    return &FuzzyBool{amount}, err
}
```

为了方便模糊布尔用户使用，我们不只接受 `float32` 作为初始化值，还接受 `float64`（Go 的默认浮点类型）、`int`（整数类型）和 `bool`。这种灵活性通过使用自定义的 `float32ForValue()` 函数实现，该函数为给定值返回 `float32` 和 `nil`——或者在值类型不是它能处理的类型时返回一个错误。

如果我们传递了一个无效类型的值，说明我们犯了编程错误，并希望发现它。但我们不希望应用程序在用户那里崩溃。因此，我们不仅返回一个 `*FuzzyBool`，还返回一个 `error`。如果我们向 `New` 传递一个已知有效的字面量（如前面的代码段：283），我们可以安全地忽略错误；但如果我们传递一个变量，应该检查返回的错误，以防它不为 `nil`。

`New()` 函数返回一个指向 `FuzzyBool` 的指针而不是值，因为我们选择让此实现中的模糊布尔是可变的。这意味着那些修改模糊布尔的方法（在本例中，即 `Set()` 方法）必须接收指针接收者，而不是值接收者。*

> * 事实上，我们可以返回 `FuzzyBool` 值并保持类型为可变的，正如书中代码的 `fuzzy_value` 示例所示。

## 6.5. 示例

一个合理的经验法则是：对于不可变类型，创建接收接收值的方法；对于可变类型，创建接收指针的方法。（对于可变类型，让某些方法接收值而其他方法接收指针是完全可能的——但在实践中可能不方便。）对于大型结构体类型（例如具有两个或更多字段的类型），最好使用指针，以将传递它们的成本保持在单个指针上。

```go
func float32ForValue(value interface{}) (float32, error) {
	var fuzzy float32
	switch value := value.(type) { // 影子变量
	case float32:
		fuzzy = value
	case float64:
		fuzzy = float32(value)
	case int:
		fuzzy = float32(value)
	case bool:
		fuzzy = 0
		if value {
			fuzzy = 1
		}
		default:
		return 0, fmt.Errorf("float32ForValue(): %v is not a number or Boolean", value)
	}
	if fuzzy < 0 {
		fuzzy = 0
	} else if fuzzy > 1 {
		fuzzy = 1
	}
	return fuzzy, nil
}
```

这个导出的辅助函数被 `New()` 和 `Set()` 方法用于将值转换为 `[0.,1]` 范围内的 `float32`。通过使用类型分支（5.2.2.2, 17），可以轻松完成对不同类型的处理。

如果调用函数时的值无效，我们将返回一个非 `nil` 错误。这让调用者有责任检查返回值并在发生错误时做出相应响应。调用者可以在出错时触发 `panic` 并导致应用程序带回溯跟踪地崩溃，也可以自行处理问题。对于此类低级函数，当它们遇到问题时返回错误通常更好，因为它们并不了解程序的逻辑，不足以知道如何处理，因此应该将问题向上推给调用者，而调用者应该处于更合适的位置知道该做什么。

## 第 6 章 对象面向编程

虽然我们认为传递无效类型的值是一个编程错误，因此值得返回一个非 `nil` 错误，但我们选择对超出范围的值处理得更宽容一些，并简单地将它们限制（clamp）到最接近的值。

```go
func (fuzzy *FuzzyBool) String() string {
	return fmt.Sprintf("%0f%%", 100*fuzzy.value)
}
```

我们选择模糊布尔的字符串表示为整数百分比。（回想一下，`"%0f"` 字符串格式指定一个没有小数点的浮点数。）

（此处后续 OCR 文本存在重复和乱码，已根据逻辑流进行处理。）

```go
func (fuzzy *FuzzyBool) Set(value interface{}) error {
	f, err := float32ForValue(value)
	if err != nil {
		return err
	}
	fuzzy.value = f
	return nil
}
```

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

当我们拥有一组相关的类（例如形状）并并且我们可能想在其上面应用某些泛型操作（例如，让形状自己绘制自己）时，有两种宽泛的方法可以来实现它们。最可能让 C++、Java 和 Python 程序员熟悉的方法是使用层级结构——在 Go 的情况下是使用嵌入接口。然而，创建可以自由组合的独立接口通常更方便、更多变。在本节中，我们将展示这两种方法，第一种在 `shape1/shapes.go` 中，第二种在 `shape2/shapes.go` 中。（注意，当“包”（packages）的类型、函数和方法相同时——我们将简单地称为“shapes 包”。自然地，在讨论特定于某一个包的代码时，我们将它们区分为“shape1 包”或“shape2 shapes 包”。）

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
