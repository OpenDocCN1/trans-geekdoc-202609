

```go
type Coordinates struct {
	x int
	y int
}

type Circle struct {
	center Coordinates
	radius int
}

func main() {
	c := Circle(Coordinates(1, 2), 3)
	fmt.Printf("%+v\n", c)
}
```

## 4.1.3 嵌入结构体

要将结构体嵌入其他结构体中，必须将其声明为匿名字段。在示例 4.5 中，通过将 `Coordinates` 结构体嵌入 `Circle` 类型中，我们使得字段 `x` 和 `y` 可以访问。坐标实例也可以像访问 `Coordinates` 字段一样被访问。

示例 4.5：嵌入结构体。

```go
package main

import "fmt"

type Coordinates struct {
	x int
	y int
}

type Circle struct {
	Coordinates
	radius int
}

func main() {
	c := Circle(Coordinates(1, 2), 3)
	fmt.Printf("%+v\n", c)
	fmt.Printf("%+v\n", c.Coordinates)
	fmt.Println(c.x, c.y)
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_48_0.png)

> 只有当编译器发现没有歧义时，才能嵌入结构体。考虑以下代码：

```go
type A struct { fieldA int }

type B struct { fieldA int }

type C struct {
	A
	B
}

a := A(18)
b := B(20)
c := C{a, b}
// fmt.Println(c.fieldA) // -> 访问冲突
fmt.Println(c.A.fieldA, c.B.fieldA)
```

由于 `fieldA` 可能属于不同的结构体，这种访问是具有歧义的，会在编译期间触发错误。我们必须指定该字段属于哪个结构体。

## 4.2 方法

在面向对象的世界中，方法被定义为与类相关的过程。在 Go 中，没有类这种说法。然而，Go 将方法定义为带有接收者的特殊函数。接收者设置了可以调用该函数的类型。

假设我们有一个 `Rectangle` 类型并想要添加一些操作，例如计算表面积。在示例 4.6 中，方法 `Surface()` 是带有接收者 `(r Rectangle)` 的函数。这意味着任何矩形都可以调用此方法。在方法内部，可以访问当前实例 `r` 的字段 `Height` 和 `Width`。

示例 4.6：`Rectangle` 类型方法的定义。

```go
package main

import "fmt"

type Rectangle struct {
	Height int
	Width int
}

func (r Rectangle) Surface() int {
	return r.Height * r.Width
}

func main() {
	r := Rectangle(2,3)
	fmt.Printf("rectangle %v has surface %d\n", r, r.Surface())
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_49_0.png)

接收者非常重要，因为它们定义了方法内部逻辑的“接收”方。在示例 4.7 中，我们定义了两个逻辑相同的方法。方法 `Enlarge` 接收一个 `Rectangle` 类型的值，而方法 `EnlargeP` 接收一个 *Rectangle* 类型。如果你观察输出，你会发现 `Enlarge` 没有修改原始变量的任何字段，而 `EnlargeP` 修改了。这是因为 `EnlargeP` 接收的是 rect 的指针，而 `Enlarge` 接收的是一个拷贝。

### 示例 4.7：值接收者和指针接收者。

```go
package main

import "fmt"

type Rectangle struct{
	Height int
	Width int
}

func (r Rectangle) Enlarge(factor int) {
	r.Height = r.Height * factor
	r.Width = r.Width * factor
}

func (r *Rectangle) EnlargeP(factor int) {
	r.Height = r.Height * factor
	r.Width = r.Width * factor
}

func main() {
	rect := Rectangle{2,2}
	fmt.Println(rect)

	rect.Enlarge(2)
	fmt.Println(rect)

	rect.EnlargeP(2)
	fmt.Println(rect)
}
```

> 在示例 4.7 中，`EnlargeP` 方法需要一个指针。然而，使用 `rect.EnlargeP(2)` 调用方法时，`rect` 并不是一个指针。这是可能的，因为 Go 解释器将其翻译为 `(&rect).EnlargeP(2)`。

> 如果一个方法可以有值接收者也可以有指针接收者，你应该使用哪一个？通常，使用指针更高效，因为减少了拷贝次数。然而，在某些情况下，你可能觉得使用值接收者更舒服。无论如何，你应该保持一致性，不要混合使用。

## 4.2.1 嵌入方法

当一个结构体被嵌入到其他结构体时，它的方法也将变为可用。这充当了 Go 中的某种继承。在示例 4.8 中，`Rectangle` 嵌入了类型。观察 `Surface` 方法如何被直接调用。

### 示例 4.8：嵌入方法。

```go
package main

import "fmt"

type Rectangle struct {
	Height int
	Width int
}

func (r *Rectangle) Surface() int {
	return r.Height * r.Width
}

type Box struct {
	Rectangle
	depth int
}

func (b Box) Volume() int {
	return b.Surface() * b.depth
}

func main() {
	b := Box{
	}
	fmt.Printf("%v\n", b)
	fmt.Println("Volume:", b.Volume())
}
```

> 只有在没有歧义时，嵌入方法才有效。考虑以下示例：

```go
type A struct {}
func (a A) Hi() string {
	return "A says Hi"
}

type B struct {}
func (b B) Hi() string {
	return "B says Hi"
}

type Greeter struct {
	A
	B
}

func (g Greeter) Speak() string {
	return g.Hi() // 这个方法属于 A 还是 B?
}
```

## 4.3 接口

接口是一组方法签名。任何实现了接口所有方法的类型都被视为实现了该接口。这是隐式完成的；你不需要显式声明某个类型实现了某个接口。

示例 4.9：接口声明

```go
package main

import "fmt"

type Speaker interface {
	Speak() string
}

type Dog struct {
	Name string
}

func (d Dog) Speak() string {
	return d.Name + " says Woof!"
}

type Cat struct {
	Name string
}

func (c Cat) Speak() string {
	return c.Name + " says Meow!"
}

func main() {
	var s Speaker
	s = Dog{Name: "Rover"}
	fmt.Println(s.Speak())

	s = Cat{Name: "Whiskers"}
	fmt.Println(s.Speak())
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_52_0.png)

接口允许多态。你可以编写接受接口类型的函数，这些函数与任何实现了该接口的类型工作。

```go
func printSpeaker(s Speaker) {
	fmt.Println(s.Speak())
}

func main() {
	d := Dog{Name: "Rover"}
	c := Cat{Name: "Whiskers"}
	printSpeaker(d)
	printSpeaker(c)
}
```

接口也可以有多个方法。一个类型必须实现所有方法才能作为该接口的实现。

```go
type ReaderWriter interface {
	Read() string
	Write(string)
}

type File struct{}

func (f File) Read() string { return "reading file" }
func (f File) Write(s string) { fmt.Println("writing:", s) }

func main() {
	var rw ReaderWriter
	rw = File{}
	fmt.Println(rw.Read())
	rw.Write("some data")
}
```

