
panic: runtime error: slice bounds out of range [recovered]
    panic: runtime error: slice bounds out of range

哦不！重要的是要注意测试已经*编译*通过了，这是一个运行时错误。编译时错误是我们的朋友，因为它们帮助我们编写可工作的软件，运行时错误是我们的敌人，因为它们会影响我们的用户。

## 编写足够代码使其通过

```
func SumAllTails(numbersToSum ...[]int) []int {
    var sums []int
    for _, numbers := range numbersToSum {
        if len(numbers) == 0 {
            sums = append(sums, 0)
        } else {
            tail := numbers[1:]
            sums = append(sums, Sum(tail))
        }
    }

    return sums
}
```

## 重构

我们的测试中再次出现了断言周围的一些重复代码，所以让我们将其提取到一个函数中

```
func TestSumAllTails(t *testing.T) {

    checkSums := func(t testing.TB, got, want []int) {
        t.Helper()
        if !reflect.DeepEqual(got, want) {
            t.Errorf("got %v want %v", got, want)
        }
    }
}
```

```
t.Run("make the sums of tails of", func(t *testing.T) {
    got := SumAllTails([]int{1, 2}, []int{0, 9})
    want := []int{2, 9}
    checkSums(t, got, want)
})

t.Run("safely sum empty slices", func(t *testing.T) {
    got := SumAllTails([]int{}, []int{3, 4, 5})
    want := []int{0, 9}
    checkSums(t, got, want)
})
}
```

这有一个方便的副作用，即为我们的代码增加了一些类型安全性。如果开发者错误地添加了一个新的测试与 `checkSums(t, got, "dave")`，编译器会立即阻止他们。

```
$ go test
./sum_test.go:52:21: cannot use "dave" (type string) as type []int
```

## 总结

我们已涵盖

- 数组
- 切片
  - 创建它们的各种方式
  - 它们具有*固定*容量，但你可以使用 `append` 从旧切片创建新切片
  - 如何切片，切片！
- `len` 用于获取数组或切片的长度
- 测试覆盖率工具
- `reflect.DeepEqual` 及其有用之处，但可能降低代码的类型安全性

我们使用切片和数组处理整数，但它们也适用于任何其他类型，包括数组/切片本身。因此，如果需要，你可以声明 `[][]string` 类型的变量。

查看 Go 博客关于切片的文章以深入了解切片。尝试编写更多测试来巩固阅读所学内容。

除了编写测试之外，Go 游乐场是实验 Go 的另一种便捷方式。你可以尝试大多数内容，如果需要提问，还可以轻松分享你的代码。我为你准备了一个包含切片的 Go 游乐场供你实验。

这里有一个切片数组的例子，以及如何改变切片会影响原始数组；但切片的“副本”不会影响原始数组。另一个例子说明了为什么在对非常大的切片进行切片后，最好复制切片。

## 结构体、方法与接口

你可以在这里找到本章的所有代码

假设我们需要一些几何代码来根据高度和宽度计算矩形的周长。我们可以编写一个 `Perimeter(width float64, height float64)` 函数，其中 `float64` 用于像 `123.45` 这样的浮点数。

TDD 循环到现在应该对你来说相当熟悉了。

## 先写测试

```
func TestPerimeter(t *testing.T) {
    got := Perimeter(10.0, 10.0)
    want := 40.0

    if got != want {
        t.Errorf("got %.2f want %.2f", got, want)
    }
}
```

注意新的格式字符串？`f` 用于我们的 `float64`，`.2` 表示打印 2 位小数。

## 尝试运行测试

```
./shapes_test.go:6:9: undefined: Perimeter
```

## 为测试运行编写最少量的代码并检查失败

## 测试输出

```
func Perimeter(width float64, height float64) float64 {
	return 0
}
```

结果为 shapes_test.go:10: got 0.00 want 40.00.

## 编写足够代码使其通过

```
func Perimeter(width float64, height float64) float64 {
	return 2 * (width + height)
}
```

到目前为止，很简单。现在让我们创建一个名为 Area(width, height float64) 的函数，它返回矩形的面积。

尝试自己完成，遵循 TDD 循环。

你应该得到类似这样的测试

```
func TestPerimeter(t *testing.T) {
	got := Perimeter(10.0, 10.0)
	want := 40.0

	if got != want {
		t.Errorf("got %.2f want %.2f", got, want)
	}
}
```

```
func TestArea(t *testing.T) {
	got := Area(12.0, 6.0)
	want := 72.0

	if got != want {
		t.Errorf("got %.2f want %.2f", got, want)
	}
}
```

以及类似这样的代码

```
func Perimeter(width float64, height float64) float64 {
    return 2 * (width + height)
}

func Area(width float64, height float64) float64 {
    return width * height
}
```

## 重构

我们的代码可以工作，但它没有明确提及矩形。一个粗心的开发者可能会尝试向这些函数提供三角形的宽度和高度，而没有意识到它们会返回错误的结果。

我们可以给函数起更具体的名称，比如 `RectangleArea`。更优雅的解决方案是定义我们自己的 *type* 称为 `Rectangle`，它为我们封装了这个概念。

我们可以使用一个 **struct** 创建一个简单类型。结构体只是一个命名字段的集合，你可以在其中存储数据。

像这样声明一个结构体

```
type Rectangle struct {
    Width  float64
    Height float64
}
```

现在让我们重构测试，使用 `Rectangle` 而不是普通的 `float64`s。

```
func TestPerimeter(t *testing.T) {
    rectangle := Rectangle{10.0, 10.0}
    got := Perimeter(rectangle)
    want := 40.0
```

```
if got != want {
    t.Errorf("got %.2f want %.2f", got, want)
}
}
```

```
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

你可以使用 myStruct.field 的语法访问结构体的字段。

修改这两个函数以修复测试。

```
func Perimeter(rectangle Rectangle) float64 {
    return 2 * (rectangle.Width + rectangle.Height)
}
```

```
func Area(rectangle Rectangle) float64 {
    return rectangle.Width * rectangle.Height
}
```

我希望你会同意，将 Rectangle 传递给函数能更清晰地表达我们的意图，但使用结构体还有更多好处，我们稍后会介绍。

我们的下一个需求是为圆编写一个 Area 函数。

## 先写测试

```
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

如你所见，f 已被 g 替换，有其原因。使用 g 会在错误消息中打印更精确的小数（fmt 选项）。例如，使用半径 1.5 计算圆面积，f 会显示 7.068583，而 g 会显示 7.0685834705770345。

## 尝试运行测试

```
./shapes_test.go:28:13: undefined: Circle
```

## 为测试运行编写最少量的代码并检查失败的测试输出

我们需要定义我们的 `Circle` 类型。

```
```go
type Circle struct {
    Radius float64
}
```
```

现在再次尝试运行测试

```
```text
./shapes_test.go:29:14: cannot use circle (type Circle) as type
Rectangle in argument to Area
```
```

一些编程语言允许你这样做：

```
```go
func Area(circle Circle) float64     {}
func Area(rectangle Rectangle) float64 {}
```
```

但在 Go 中不行

```
```text
./shapes.go:20:32: Area redeclared in this block
```
```

我们有两个选择：

- 你可以在不同的 *packages* 中声明同名函数。因此我们可以将 `Area(Circle)` 创建在新包中，但在这里感觉太过分了。
- 我们可以在新定义的类型上定义 [*方法*](#) 代替。

## 什么是方法？

到目前为止我们只编写了 *functions*，但我们使用了一些方法。当我们调用 `t.Errorf` 时，我们是在 `t` (`testing.T`) 的实例上调用方法 `Errorf`。
