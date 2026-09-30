# Go 优化入门 101


















- 9.5 尽可能避免分配 .................................................................................................................... 103






















v1.21.a-rev-df43314-2023/10/12

![](img/46c8beb386857de8313857925c717fba_5_0.png)



首先，感谢整个 Go 社区。一个活跃且响应迅速的社区确保了本书的准时完成。

具体来说，我想感谢以下人员，他们帮助我理解官方标准编译器中的某些实现细节：Keith Randall, Ian Lance Taylor, Axel Wagner, Cuong Manh Le, Michael Pratt, Jan Mercl, Matthew Dempsey, Martin Mörmann 等。如果我在上面的列表中遗漏了某人，我深表歉意。Go 社区中有许多善良且富有创造力的 gophers，我一定漏掉了某些人。

我也感谢所有对《Go 101》这本书产生过影响的 gophers，无论是直接还是间接，无论是有意还是无意。

感谢 Alexandr Shalakhin 允许我使用其中一个精美的 gopher 图标设计作为封面。感谢 Renee 提供了可爱的 gopher 卡通角色。

感谢构建本书时使用的以下开源软件和库的作者：
- golang, https://go.dev/
- gomarkdown, https://github.com/gomarkdown/markdown
- goini, https://github.com/zieckey/goini
- go-epub, https://github.com/bmaupin/go-epub

## 第 1 章

### 关于 Go 优化 101

本书提供了一些代码优化技巧、提示和建议。书中的大部分内容基于官方标准编译器和运行时的实现。

生活充满了权衡，编程世界也是如此。在编程中，我们经常需要在代码可读性、可维护性、开发效率和程序效率等之间进行权衡。即使对于某一个方面，也需要进行权衡。以程序效率为例，我们可能需要在节省内存、代码执行速度和实现难度等之间进行权衡。

在实践中，项目代码库的大部分代码不需要用高性能实现。保持它们的可维护性和可读性通常比让它们节省内存和运行更快重要。书中的建议仅适用于实现确实需要高性能的代码部分。某些建议会导致代码变得冗长。

书中的内容包括：

- 消耗更少的  。
- 消耗更少的内存。
- 进行更少的内存分配。
- 控制内存分配的位置。
- 减少垃圾回收压力。

本书既不解释如何使用性能分析工具（如 pprof），而是深入研究编译器和运行时的实现。书中也没有介绍如何使用概要引导优化（PGO）。书中的建议使用了不安全指针（unsafe pointers）和并发（cg）。换句话之，本书旨在以一种清晰易懂的方式为日常 Go 编程提供优化建议。

除非特别说明，书中提供的代码示例均在具有以下环境设置的笔记本电脑上测试和运行：

```
go version go1.21.2 linux/amd64
goos: linux
goarch: amd64
cpu: Intel(R) Core(TM) i5-4210U CPU @ 1.70GHz
```





为了保持基准测试行的简短，从基准测试结果中移除了一些基准测试时间信息。

请注意：

- 本书中讨论的某些建议适用于任何平台和任何 CPU 模型，但另一些可能仅适用于特定的平台和特定的 CPU 模型。因此，在采用任何建议之前，请务必在与你的生产环境相同的环境中对它们进行基准测试。
- 官方 Go 编译器和运行时的某些实现细节会随版本变化，这意味着书中提到的某些建议可能在未来的 Go 工具链版本中失效。
- 本书最终将分章节开源。

## 1.1 关于作者

Tapir 是本书的作者。他还编写了《Go 101》一书。他正计划编写其他其他 Go 101 系列书籍。请敬请期待。

Tapir 曾经是（可能还会是）一名独立游戏开发者。你可以在这里找到他的游戏：tapirgames.com。

## 1.2 关于 GoTV

在编写本书期间，使用了 GoTV 工具来管理多个版本 Go 工具链的安装，并检查不同 Go 工具链版本之间的行为差异。

## 1.3 反馈

欢迎通过向 Go 101 的 issue 列表（https://github.com/go101/go101）提交修正来改进本书，涵盖各种错误，如拼写错误、语法错误、措不准确、解释错误、描述缺陷、代码 Bug 等。

也欢迎向 Go 101 的 Twitter 账户发送反馈：@go100and1 (https://ter.com/go100and1)。

## 第 2 章

### 值部分与值大小

## 2.1 值与值部分

在 Go 中，某些类型的值始终只包含一个部分（在内存中），而其他类型的值可能包含多个部分。如果一个值包含多个部分，那么其中一部分被称为**直接部分**（direct part），其他部分被称为**间接部分**（indirect parts）。直接部分引用间接部分。

如果一个值始终包含一个部分，那么该部分也可以称为该值的直接部分，我们说该值没有间接部分。

在官方 Go 编译器的实现中，以下类型的每个值始终包含一个部分：

- 布尔类型
- 数值类型（int8, uint8, int16, int32, uint32, int64, uint64, int, uintptr, float32, float64, complex64, complex128）
- 指针类型
- 不安全指针类型
- 结构体类型
- 数组类型

而以下类型的值可能包含一个或多个间接部分：

- 切片类型
- 映射类型（map）
- 通道类型
- 函数类型
- 接口类型
- 字符串类型

在赋值/拷贝值时，只拷贝该值的直接部分。拷贝完成后，目标值和源值的直接部分都引用源值的间接部分（如果间接部分存在的话）。

在运行时，每个值都承载在一个内存块上（内存块将在后续章节中解释）。因此，如果一个值包含两个部分，该值很可能分布在两个内存块上。

（注：“值部分”这一术语是由 Go 101 系列书籍发明的。它在 Go 社区中并没有广泛使用。我个人认为，这个术语在进行某些解释时提供了一些便利。）

## 2.2 值/类型大小

值部分的大小意味着运行时在内存中分配了多少字节来存储该值部分。

值的大小恰好等于该值直接部分的大小。换句话说，值的间接部分不贡献于值的大小。原因是什么？上面提到过：当赋值/拷贝值时，只拷贝值的直接部分，且间接部分可能被多个值共享，因此让相同的间接部分贡献于值的大小并不是好主意。

在官方 Go 编译器的实现中，以下类型的每个值始终包含一个部分：

（此处由于原文存在大量重复和乱码，已根据上下文逻辑处理，见下文的表格）

## 2.3 详细类型大小

下表列出了所有类型的大小（Go 编译器中使用的）。在表中，word 指一个原生字长（32 位架构为 4 字节，64 位架构为 8 字节）。

| 类型 | 大小 | Go 语言 |
|---|---|---|
| int, uint | 1 word | 取决于架构，32 位为 4 字节，64 位为 8 字节。 |
| int8, uint8 (byte) | 1 字节 | 1 字节 |
| int16, uint16 | 2 字节 | 2 字节 |
| int32 (rune), uint32, float32 | 4 字节 | 4 字节 |
| int64, uint64 | 8 字节 | 8 字节 |
| float64, complex64 | 8 字节 | 16 字节 |
| complex128 | 1 word | 足以存储指针值的未解释位位。 |
| bool | 1 字节 | 未定义 |
| string | 2 words | 未定义 |
| array | (元素值大小) (长度) | 如果元素类型的大小为零，则数组类型的大小为零。 |
| 指针 (安全或不安全) | 1 word | 未定义 |
| slice | 3 words | 未定义 |
| map | 1 word | 未定义 |
| channel | 1 word | 未定义 |
| function | 1 word | 未定义 |
| interface | 2 words | 未定义 |
| struct | (所有字段大小之和) (填充字节数) | 如果结构体不包含任何大于零的字段，则该结构体类型的大小为零。 |





架构。

| 类型 | 对齐保证 |
|---|---|
| bool, uint8, int8 | 1 |
| uint16, int16 | 2 |
| uint32, int32 | 4 |
| float32, complex64 | 4 |
| 数组 | 取决于元素类型 |
| 结构体 | 取决于字段类型 |
| 其他类型 | 原生字长（native word）的大小 |

Go 规范规定：

- 对于结构体类型的变量：`unsafe.Alignof(x)` 是 x 每个字段 f 的 `unsafe.Alignof(x.f)` 值中的最大值，但至少为 1。
- 对于数组类型的变量：`unsafe.Alignof(x)` 与变量元素类型的对齐方式相同。

官方 Go 编译器确保类型的大小是对齐保证的倍数。

## 2.5 结构体填充 (Struct padding)

为了满足之前的对齐保证规则，Go 编译器可能会在结构体类型某些字段之后填充一些字节。填充后的值会被计入结构体的大小。结构体的大小可能不是其字段大小的简单和。

例如，以下代码所示的结构体类型在 64 位架构上的大小为 24。

```go
type T1 struct {
    a int
    // 这里填充了 7 字节
    b int64
    c int16
    // 这里填充了 6 字节。
}
```

其大小为 24 的原因是：

- 结构体类型的对齐保证与其字段中最大的对齐保证相同。这里是类型 `int64` 的对齐保证（8，一个原生字长）。这意味着结构体类型值中字段 b 和 a 之间的距离是 8 的倍数。聪明的编译器应该选择最小可能的值：8。为了得到所需的大小，在字段 a 之后填充了 7 字节。
- 结构体类型的大小必须是该结构体对齐保证的倍数。考虑到字段 c 的存在，最小可能的大小是 24 (8x3)，聪明的编译器应该使用该大小。为了得到所需的大小，在字段 c 之后填充了 6 字节。

结构体类型大小计算中的字段顺序。如果我们更改上述结构体类型字段 b 和 c 的大小，结构体的大小将变为 16。

```go
type T2 struct {
    a int
    // 这里填充了 1 字节
    c int16
    // 这里填充了 4 字节
    b int64
}
```

我们可以使用 `unsafe.Sizeof` 函数来获取值/类型的大小。例如：

```go
package main
import "unsafe"

type T1 struct {
    a int8
    b int64
    c int16
}

type T2 struct {
    a int8
    c int16
    b int64
}

func main(){
    // 打印的值是在
    // 64 位架构上获得的。
    println(unsafe.Sizeof(T1())) // 24
    println(unsafe.Sizeof(T2())) // 16
}
```

我们可以将填充字节视为一种内存浪费的形式，是程序性能、代码可读性和内存节省之间权衡的结果。

在实践中，我们应该让相关字段相邻以获得良好的可读性，只有在确实需要时才以节省内存的方式排列字段。

## 2.6 值拷贝成本与小尺寸类型/值

拷贝值的成本大约与该值的大小正比。在现实中，CPU 缓存、CPU 指令和编译器优化也会影响值的拷贝成本。

值拷贝操作通常发生在赋值赋值。下一节将列出更多的值拷贝操作。

为了实现高执行性能，如果可能，我们应该尝试避免

- 在循环中拷贝大量大尺寸的值。
- 拷贝大型数组和结构体。

 Go 中的某些类型属于小尺寸类型。它们的值被官方标准 Go 编译器经过特殊优化，使得拷贝成本始终很小。

但什么是小尺寸类型呢？并没有正式的定义。事实上，定义取决于特定的 CPU 架构和编译器实现。在官方标准 Go 编译实现中，除了大尺寸结构体和数组类型，Go 中的所有其他类型都可以被视为小尺寸类型。

什么是小尺寸结构体和数组值？同样没有正式定义。官方 Go 编译器会在每个版本中调整一些实现细节。然而，在实践中，我们可以将具有不超过 4 个原生字长字段的类型视为小尺寸值，例如 `struct(a, b, c, d, int)`、`struct(element *T; int; cap int)` 和 `[4]uint`。

对于官方 Go 编译器 1.21 版本，最后拷贝发生在拷贝 9 元素数组和拷贝 10 元素数组之间（元素大小为一个原生字长）。类似的情况是拷贝 9 字段结构体和拷贝 10 字段结构体（每个字段的大小为一个原生字长）。

证明如下：

```go
package copy

import "testing"

const N = 1024
type Element = uint64

var a9 [N]Element
func Benchmark_CopyArray_9_elements(b *testing.B) {
	va9 [N]Element
	for i := 0; i < b.N; i++ {
		k := range a9 {
			va9[k] = a9[k]
		}
	}
}

var a10 [N]Element
func Benchmark_CopyArray_10_elements(b *testing.B) {
	va10 [N]Element
	for i := 0; i < b.N; i++ {
		k := range a10 {
			va10[k] = a10[k]
		}
	}
}

type S struct{a, b, c, d, e, f, g, h, i Element}
var s9 [N]S
func Benchmark_CopyStruct_9_fields(b *testing.B) {
	for i := 0; i < b.N; i++ {
		k := range s9 {
			s9[k] = s9[k]
		}
	}
}

type S10 struct{a, b, c, d, e, f, g, h, i, j Element}
var s10 [N]S10
func Benchmark_CopyStruct_10_fields(b *testing.B) {
	for i := 0; i < b.N; i++ {
		k := range s10 {
			s10[k] = s10[k]
		}
	}
}
```
基准测试结果：
Benchmark_CopyArray_9_elements-4 3974 ns/op
Benchmark_CopyArray_10_elements-4 8896 ns/op
Benchmark_CopyStruct_9_fields-4 2970 ns/op
Benchmark_CopyStruct_10_fields-4 8471 ns/op

这些结果表明，少于10元素的数组和少于10个字段的结构体可能被特殊优化。官方 Go 编译器可能使用不同的标准来判断什么是小类型。例如，在下面的基准测试中（使用官方 Go 1.21 ），`Add4` 函数比 `Add5` 函数消耗更多的 CPU 资源。

```go
package copycost

import "testing"

type T4 struct{a, b, c, d float32}
type T5 struct{a, b, c, d, e float32}
var t4 T4
var t5 T5

//go:noinline
func Add4(x, y T4) (z T4) {
	z.a = x.a + y.a
	z.b = x.b + y.b
	z.c = x.c + y.c
	z.d = x.d + y.d
	return
}

//go:noinline
func Add5(x, y T5) (z T5) {
	z.a = x.a + y.a
	z.b = x.b + y.b
	z.c = x.c + y.c
	z.d = x.d + y.d
	z.e = x.e + y.e
	return
}

func Benchmark_Add4(b *testing.B) {
	for i := 0; i < b.N; i++ {
		t4 = Add4(t4, t4)
	}
}

func Benchmark_Add5(b *testing.B) {
	for i := 0; i < b.N; i++ {
		t5 = Add5(t5, t5)
	}
}
```
基准测试结果：

| Benchmark_Add4-4 | 2.649 ns/op |
| Benchmark_Add5-4 | 3.15 ns/op |

这里的 `//go:noinline` 编译器指令用于防止这两个函数被内联。如果移除这些指令，`Add4` 函数将变得更快。

## 2.7 值拷贝场景

在 Go 编程中，除了值赋值，还有其他几种涉及值拷贝的操作：

- 装箱（将数字转换为接口）。
- 函数调用中的参数传递和结果返回。
- 从通道发送的值接收值。
- 将项存入 map。
- 向切片追加元素。
- 使用 `for-range` 循环迭代容器元素。

以下是显示某些值拷贝成本的示例。

示例 1：

```go
package copy

import "testing"

const N = 1024

//go:noinline
func Sum_RangeArray(a [N]int) (r int) {
	for _, v := range a {
		r += v
	}
	return
}

//go:noinline
func Sum_RangeArrayPtr(a [*N]int) (r int) {
	for _, v := range a {
		r += v
	}
	return
}

//go:noinline
func Sum_RangeArrayPtr2(a [*N]int) (r int) {
	for _, v := range a {
		r += v
	}
	return
}

//go:noinline
func Sum_RangeSlice(a []int) (r int) {
	for _, v := range a {
		r += v
	}
	return
}

var r [128]int
func buildArray() [N]int {
	var a [N]int
	for i := 0; i < N; i++ {
		a[i] = (N-i) & a
	}
	return a
}

func Benchmark_Sum_RangeArray(b *testing.B) {
	var a = buildArray()
	b.ResetTimer()
	for i := 0; i < b.N; i++ {
		r[:127] = Sum_RangeArray(a)
	}
}

func Benchmark_Sum_RangeArrayPtr1(b *testing.B) {
	var a = buildArray()
	b.ResetTimer()
	for i := 0; i < b.N; i++ {
		r[:127] = Sum_RangeArrayPtr(&a)
	}
}

func Benchmark_Sum_RangeArrayPtr2(b *testing.B) {
	var a = buildArray()
	b.ResetTimer()
	for i := 0; i < b.N; i++ {
		r[:127] = Sum_RangeArrayPtr2(&a)
	}
}
```



r[i&127] = Sum_RangeSlice(a[:])

}

}

基测试结果：
Benchmark_Sum_RangeArray-4    897.6 ns/op
Benchmark_Sum_RangeArrayPtr1-4    799.3 ns/op
Benchmark_Sum_RangeArrayPtr2-4    555.3 ns/op
Benchmark_Sum_RangeSlice-4    561.7 ns/op

从结果中，我们可以发现 `Sum_RangeArray` 是最慢的。这并不意外，因为在调用此函数时数组会被复制。在将数组作为参数传递时发生一次拷贝（参数是通过拷贝传递的），在遍历数组时发生发生拷贝（将使用遵循 `range` 关键字的直接路径）。`Sum_RangeArrayPtr` 比 `Sum_RangeArray` 快，因为在调用此函数时数组只被复制了一次。调用过程中没有发生数组拷贝，因此这两个函数都是最快的。

示例 2：

```go
package copycost

import "testing"

type Element [10]int64

//go:inline
func Sum_PlainForLoop(s []Element) (r int64) {
    for i := 0; i < len(s); i++ {
        r += s[i]
    }
    return
}

//go:inline
func Sum_OneIterationVar(s []Element) (r int64) {
    for i := range s {
        r += s[i]
    }
    return
}

//go:inline
func Sum_UseSecondIteration(s []Element) (r int64) {
    for _, v := range s {
        r += v
    }
    return
}

func buildSlice() []Element {
    var s = make([]Element, 1000)
    for i := 0; i < len(s); i++ {
        s[i] = Element{}
    }
    return s
}

```var r [128]int

func Benchmark_PlainForLoop(b *testing.B) {
    var s = buildSlice()
    b.ResetTimer()
    for i := 0; i < b.N; i++ {
        r[i%127] = Sum_PlainForLoop(s)
    }
}

func Benchmark_OneIterationVar(b *testing.B) {
    var s = buildSlice()
    b.ResetTimer()
    for i := 0; i < b.N; i++ {
        r[i%127] = Sum_OneIterationVar(s)
    }
}

func Benchmark_UseSecondIteration(b *testing.B) {
    var s = buildSlice()
    b.ResetTimer()
    for i := 0; i < b.N; i++ {
        r[i%127] = Sum_UseSecondIteration(s)
    }
}
```

基测试结果：

| Benchmark | Result |
| :--- | :--- |
| Benchmark_PlainForLoop-4 | 911.8 ns/op |
| Benchmark_OneIterationVar-4 | 929.3 ns/op |
| Benchmark_UseSecondIteration-4 | 3753 ns/op |

从结果中，我们可以了解到函数 `Sum_UseIterationVar` 的性能远低于 `Sum_PlainForLoop` 和 `Sum_OneIterationVar` 函数。原因在于在 `Sum_UseIterationVar` 中，每个元素都被拷贝到了迭代变量 `v` 中，而且拷贝代价并不小（`Element` 不是一个小尺寸类型）。另外两个函数避免了拷贝。

示例 3：

```go
package copycost

import "testing"

type S struct{a, b, c, d, e int}

//go:noinline
func sum_UseSecondIterationVar(s []S) int {
    var sum int
    for _, v := range s {
        sum += v.c
        sum += v.d
        sum += v.e
    }
    return sum
}

//go:noinline
func sum_OneIterationVar_Index(s []S) int {
    var sum int
    for i := range s {
        sum += s[i].c
        sum += s[i].d
        sum += s[i].e
    }
    return sum
}

//go:noinline
func sum_OneIterationVar_Ptr(s []S) int {
    var sum int
    for i := range s {
        v := &s[i]
        sum += v.c
        sum += v.d
        sum += v.e
    }
    return sum
}

var s = make([]S, 1000)
var r [128]int

func init() {
    for i := range s {
        s[i] = S{i, i, i, i, i}
    }
}

func BenchmarkSecondIterationVar(b *testing.B) {
    for i := 0; i < b.N; i++ {
        r[i%127] = sum_UseSecondIterationVar(s)
    }
}

func BenchmarkOneIterationVar_Index(b *testing.B) {
    for i := 0; i < b.N; i++ {
        r[i%127] = sum_OneIterationVar_Index(s)
    }
}

func BenchmarkOneIterationVar_Ptr(b *testing.B) {
    for i := 0; i < b.N; i++ {
        r[i%127] = sum_OneIterationVar_Ptr(s)
    }
}
```

基测试结果：

| Benchmark | Result |
| :--- | :--- |
| Benchmark_SecondIterationVar-4 | 2208 ns/op |
| Benchmark_OneIterationVar_Index-4 | 1212 ns/op |
| Benchmark_OneIterationVar_Ptr-4 | 1182 ns/op |

再次，迭代变量是最慢的。请注意，如果结构体小于 4 个字，那么函数之间的差异可能并不显著。

## 第三章：分配

### 3.1 内存单位
分配的基本单位是内存块。如上所述，内存块可能包含部分，运行时会尝试寻找单个内存块。分配的内存块越多，消耗的资源就越多。在编程中，我们应该尽量避免分配。

### 3.2 内存位置
以下操作至少会导致一次分配：

- 声明变量
- 调用 `new` 函数
- 使用复合字面量调用 `make` 函数
- 将整数转换为字符串
- 使用 `+` 拼接字符串
- 在字符串和字节切片之间转换
- 将值装入接口
- 切片容量不足时追加元素
- 在 map 中插入新元素且底层数组容量不足

### 3.3 内存场景
通常情况下，每种操作至少会导致一次分配：

- 声明变量
- 调用 `new` 函数
- 使用复合字面量调用 `make` 函数
- 将整数转换为字符串
- 使用 `+` 拼接字符串
- 在字符串和字节切片之间转换
- 将值装入接口
- 切片容量不足时追加元素
- 在 map 中插入新元素且底层数组容量不足

然而，官方 Go 编译器进行了一些特殊优化，使得在某些情况下，上述列表中的操作不会产生分配。

### 3.4 分配内存块过大导致的内存浪费
内存块的大小可能不同，但它们并不是任意。在官方运行时实现中，对于堆上分配的内存块，预定义了一些尺寸类（不超过 32768 字节）。根据官方 Go 编译器版本 1.21.x，最小的尺寸类为 8、16、24、32、48、64、80 和 96 字节。对于大于 32768 字节的内存块，每个块始终由多个内存页组成。运行时使用的内存页大小为 8192 字节。




换句话说，内存块通常比实际需要的要大。这些策略是为了方便、高效地管理内存，但有时会导致一些内存浪费（是的，一种权衡）。
可以通过以下程序证明这一点：

```go
package main

import "testing"
import "unsafe"

var t *[5]int64
var s []byte

func f(b *testing.B) {
	for i := 0; i < b.N; i++ {
		s = &[5]int64{}
	}
}

func g(b *testing.B) {
	for i := 0; i < b.N; i++ {
		s = make([]byte, 32769)
	}
}

func main() {
	println(unsafe.Sizeof(*t)) // 40
	rf := testing.Benchmark(f)
	println(rf.AllocatedBytesPerOp()) // 48
	rg := testing.Benchmark(g)
	println(rg.AllocatedBytesPerOp()) // 40960
}
```

另一个例子：

```go
package main

import "testing"

var s = []byte{32: 'b'} // len(s) == 33
var r string

func Concat(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r = string(s) + string(s)
	}
}
```

```go
func main() {
	br := testing.Benchmark(Concat)
	println(br.AllocsPerOp()) // 3
	println(br.AllocatedBytesPerOp()) // 176
}
```

在 `Concat` 函数内部有 3 次内存分配。其中两个是由字节切片到字符串的转换 `string(s)` 引起的，承载两个结果字符串底层字节的两个内存块的大小均为 48（这是不小于 33 的最小内存类）。第三次分配是由字符串拼接引起的，结果内存块的大小为 80（不小于 66 的最小内存类）。这三次分配共分配了 176 (48+80) 字节。在执行 `Concat` 函数期间，总共浪费了 14 字节，并浪费了 44 (15+14) 字节。

在上面的示例中，`string(s)` 转换在字符串拼接操作中临时使用。在目前的官方 Go 编译器/运行时实现（1.21 版本），字符串字节分配在堆上（见下文）。拼接完成后，承载字符串字节的内存块将变成内存垃圾，并最终被回收。

## 3.5 减少内存分配并节省内存

内存（块）分配越少，消耗的 CPU 资源越少，垃圾回收的压力就越小。

现在的内存很便宜，但对于云提供商出售的内存并非如此。因此，如果在云服务器上运行程序，Go 程序节省内存越多，节省越多。

以下是编程中减少内存分配和节省内存的一些建议。

## 3.6 通过提前分配内存避免不必要的分配

我们使用内置的 `append` 函数来推送某些切片元素。在语句 `r = append(s, elements...)` 中，如果 `s` 的剩余容量不足以容纳所有追加的元素，Go 运行时将分配一个新的内存块来存放结果切片的所有元素。

如果需要多次调用 `append` 来推送某些元素，最好确保基础切片具有足够的容量，以避免整个过程中的多次不必要的分配。

例如，为了将切片合并为一个，下面的 `MergeWithTwoLoops` 比 `MergeWithOne` 实现更有效，因为后者的分配更少，拷贝的值更少。

```go
package allocations

import "testing"

func getData() [][]int {
	return [][]int{
		{1, 2},
		{9, 10, 11},
		{6, 2, 3, 7},
		{11, 5, 7, 12, 16},
		{8, 5, 6},
	}
}

func MergeWithOneLoop(data [][]int) []int {
    var r []int
    for _, s := range data {
        r = append(r, s...)
    }
    return r
}

func MergeWithTwoLoops(data [][]int) []int {
    n := 0
    for _, s := range data {
        n += len(s)
    }
    r := make([]int, 0, n)
    for _, s := range data {
        r = append(r, s...)
    }
    return r
}

func BenchmarkMergeOneLoop(b *testing.B) {
    data := getData()
    b.ResetTimer()
    for i := 0; i < b.N; i++ {
        MergeWithOneLoop(data)
    }
}

func BenchmarkMergeWithTwoLoops(b *testing.B) {
    data := getData()
    b.ResetTimer()
    for i := 0; i < b.N; i++ {
        MergeWithTwoLoops(data)
    }
}
```

基测试结果：

| Benchmark | Time | Memory | Allocations |
| :--- | :--- | :--- | :--- |
| Benchmark-MergeWithOneLoop-4 | 636.6 ns/op | 352 B/op | 4 allocs/op |
| Benchmark-MergeWithTwoLoops-4 | 268.4 ns/op | 144 B/op | 1 allocs/op |

基测试结果显示分配影响代码执行性能。

打印一些日志查看 `MergeWithOneLoop` 函数中何时发生分配。

```go
package main

import "fmt"

func getData() [][]int {
	return [][]int{
		{1, 2},
		{9, 10, 11},
		{6, 2, 3, 7},
		{11, 5, 7, 12, 16},
		{8, 5, 6},
	}
}

const format = "Allocate from %v to %v (when slice#%v).\n"

func MergeWithOneLoop(data [][]int) {
    var oldCap int
    var r []int
    for i, s := range data {
        r = append(r, s...)
        if oldCap == cap(r) {
            continue
        }
        fmt.Printf(format, oldCap, cap(r), i)
        oldCap = cap(r)
    }
}

func main() {
    MergeWithOneLoop(getData())
}
```

输出（官方 Go 编译器 v1.21）：
Allocate from 0 to 2 (when slice#0)
Allocate from 2 to 6 (when slice#1)
Allocate from 6 to 12 (when slice#2)
Allocate from 12 to 24 (when slice#3).

事实上，`MergeWithTwoLoops` 函数可能会更快。在官方 Go 编译器 v1.21 中，`MergeWithTwoLoops` 函数中的 `make` 会清零所有元素，这实际上是不必要的。未来的编译器优化可能会避免这种操作。

另外 `Merge_TwoLoops` 的实现存在缺陷，它没有处理整数溢出。以下是更好的实现：

```go
func Merge_TwoLoops(data [][]int) []int {
    n := 0
    for _, s := range data {
        n += len(s)
    }
    r := make([]int, 0, n)
    for _, s := range data {
        r = append(r, s...)
    }
    return r
}
```

## 3.7 尽可能避免分配

分配越少越好，但完全不分配最好。

下面是另一个展示两种实现之间性能差异的例子。其中一个实现没有分配，另一个有一个。

```go
package allocations

import "testing"

func buildOriginalData() []int {
  s := make([]int, 1024)
  for i := range s {
    s[i] = i
  }
  return s
}
```

```go
func check(v int) bool {
  return v%2 == 0
}
```

```go
func FilterAllocation(data []int) []int {
  var r = make([]int, 0, len(data))
  for _, v := range data {
    if check(v) {
      r = append(r, v)
    }
  }
  return r
}
```

```go
func FilterNoAllocations(data []int) []int {
  k := 0
  for i, v := range data {
    if check(v) {
      data[k] = v
      k++
    }
  }
  return data[:k]
}
```

```go
func Benchmark_FilterAllocation(b *testing.B) {
  data := buildOriginalData()
  b.ResetTimer()
  for i := 0; i < b.N; i++ {
    = FilterAllocation(data)
  }
}
```

```go
func Benchmark_FilterNoAllocations(b *testing.B) {
    data := buildOriginalData()
    b.ResetTimer()
    for i := 0; i < b.N; i++ {
        = FilterNoAllocations(data)
    }
}
```

基测试结果：

| Benchmark | Time | Memory | Allocations |
| :--- | :--- | :--- | :--- |
| Benchmark_FilterAllocation-4 | 7263 ns/op | 8192 B/op | 1 allocs/op |
| Benchmark_FilterNoAllocations-4 | 903.3 ns/op | 0 B/op | 0 allocs/op |

从基测试结果可以看出 `FilterNoAllocations` 实现性能更好。（当然，如果不允许修改输入数据，那么我们必须选择产生分配的实现。）

## 3.8 通过累积内存块节省内存并减少分配

有时，我们可以分配一个大块来承载许多值，而不是为每个值分配一个小块。这将减少许多内存分配，因此消耗更少的 CPU 资源并在某种程度上缓解了 GC 压力。有时这可以减少内存浪费，但并非总是如此。

让我们来看一个例子：

```go
package main

import "testing"

const N = 100

type Book struct {
    Title string
    Author string
    Pages int
}

//go:noinline
func CreateBooksOnOneLargeBlock(n int) []*Book {
    books := make([]Book, n)
    pbooks := make([]*Book, n)
    for i := range pbooks {
        pbooks[i] = &books[i]
    }
    return pbooks
}
```




```go
//go:noinline
func CreateBooksOnManySmallBlocks(n int) []*Book {
	books := make([]*Book, n)
	for i := range books {
		books[i] = new(Book)
	}
	return books
}

func Benchmark_CreateBooksOnOneLargeBlock(b *testing.B) {
	for i := 0; i < b.N; i++ {
		CreateBooksOnOneLargeBlock(N)
	}
}

func Benchmark_CreateBooksOnManySmallBlocks(b *testing.B) {
	for i := 0; i < b.N; i++ {
		CreateBooksOnManySmallBlocks(N)
	}
}
```

运行基测试，得到：

| Benchmark_CreateOnOneLargeBlock-4 | 4372 ns/op | 4992 B/op | 1 alloc/op |
| Benchmark_CreateOnManySmallBlocks-4 | 18017 ns/op | 5696 B/op | 101 alloc/op |

从结果中我们可以看到，在一个大块上分配许多小对象：

1. 消耗了更少的 CPU 时间。
2. 消耗了更少的内存。

第一个结论很容易理解。通常情况下，在一个大块上分配小对象比在独立的内存块上分配它们每一个都要更好。当小对象的生命周期几乎相同时，这种情况为如此。在这种情况下，在一个大块上分配小对象可以有效地避免内存碎片。

## 3.9 使用池避免某些分配

有时，我们需要频繁地分配和释放指定类型的值。重用分配的值以避免大量分配是一个好主意。

例如，RTS游戏中有很多非玩家角色（NPC）。大量的 NPC 在游戏过程中会不断生成和销毁。相关代码如下：

```go
type NPC struct {
    name [64]byte
    nameLen uint16
    blood uint32
    properties struct {
        x, y float64
    }
}
```

```go
func SpawnNPC(name string, x, y float64) *NPC {
    var npc = newNPC()
    npc.nameLen = uint16(copy(npc.name[:], name))
    npc.x = x
    npc.y = y
    return npc
}
```

```go
func newNPC() *NPC {
    return newNPC()
}
```

```go
func releaseNPC(npc *NPC) {
}
```

由于自动 GC 的存在，releaseNPC 函数可能什么都不做。然而，这种实现会在游戏运行时产生大量分配并给垃圾回收带来巨大压力，因此难以保证良好的 FPS（帧率）。

我们可以使用缓存池来减少分配，如下所示：

```go
import "container/list"

var npcPool = struct {
    sync.Mutex
    *list.List
}{
    List: list.New(),
}
```

```go
func newNPC() *NPC {
    npcPool.Lock()
    defer npcPool.Unlock()
    if npcPool.List.Len() == 0 {
        return &NPC{}
    }
    return npcPool.List.Remove(npcPool.List.Front()).(*NPC)
}
```

```go
func releaseNPC(npc *NPC) {
    npcPool.Lock()
    defer npcPool.Unlock()
    npcPool.List.PushBack(npc)
}
```

通过使用池，值的分配将会减少，这非常有助于保持平滑的 FPS（帧率）。

如果池只在一个 goroutine 中使用，则没有必要同步。标准的 `sync.Pool` 提供了一个类似的功能类型，但有几点不同：

- `sync.Pool` 中的空对象如果在连续的垃圾回收周期中发现未被使用，将被自动收集。这意味着 `sync.Pool` 的最大大小是动态的，取决于运行时的需求。
- `sync.Pool` 中对象的类型和大小可以不同。但最佳实践是让放入 `sync.Pool` 的对象具有相同的类型和大小。

个人而言，我发现 `sync.Pool` 的设计很少满足实践中的需求。在我的项目中，我经常使用自定义的池实现。

# 4. 逃逸分析

Go 编译器会自动进行逃逸分析。在 Go 运行时，逃逸分析决定了变量是分配在栈上还是堆上。

## 4.1 栈与堆

逃逸分析决定了变量是否会逃逸函数调用的范围。如果变量没有逃逸，它将被分配在栈上；如果逃逸了，它将被分配在堆上。

栈分配比堆分配快得多，因为它只需要移动栈指针。而堆分配则涉及复杂的内存管理和垃圾回收。

## 4.2 逃逸分析

逃逸分析是 Go 编译器在编译阶段进行的一种优化，用于确定变量的生命周期。

### 4.2.1 逃逸分析示例

`-m` 选项用于显示逃逸分析结果。让我们来看一个例子：

```go
// escape.go
package main

func main() {
	var a int = 1 // 逃逸
	b := false
	c := make(chan struct{})
	go func() {
		if b {
			a++
		}
		close(c)
	}()
	<-c
	println(a, b) // false
}
```

使用 `gcflags=-m` 参数运行：

```bash
$ go run -gcflags=-m escape.go
# command-line-arguments
./escape.go:10:5: can inline main.func1
./escape.go:6:3: moved to heap: a
./escape.go:10:5: func literal escapes to heap
1 false
```

从输出中我们可以知道，`a` 逃逸到了堆，但变量 `b` 分配在栈上。关于变量 `c` 呢？`c` 的直接部分分配在栈上。通道的间接部分总是分配在堆上，间接部分的逃逸信息总是被省略。

为什么变量 `b` 分配在栈上而变量却逃逸了？它们难道不是在两个协程中使用的吗？原因是逃逸分析模块非常宽松，它检测到变量 `b` 未被修改，因此认为在新的协程中使用它的（隐藏的隐式）拷贝是一个好主意。

让我们在打印语句前添加新行 `b = !b` 然后再次运行。

```go
// escape.go
package main
```



```go
func main() {
  var (
    a = 1 // moved to heap: a
    b = false // moved to heap: b
    c = make(chan struct{})
  )
  go func() {
    if b {
      a++
    }
    close(c)
  }()
  <-c
  b = !b
  println(a, b) // 1 true
}
```

输出结果：
./escape.go:10:5: can inline main.func1
./escape.go:6:3: moved to heap: a
./escape.go:7:3: moved to heap: b
./escape.go:10:5: func literal escapes to heap
1 true

现在，变量 a 和变量 b 都逃逸了。事实上，对于这个特定的示例，编译器仍然可以在新的 goroutine 中使用变量 b，但让逃逸分析监控代码中使用的并发同步操作的代价太高了。
由于类似的原因，逃逸分析也不会尝试检查变量是否真的会被修改。如果我们把 b 改为常量，该变量将分配在栈上，因为 `a++` 这一行会被优化。

## 4.3 函数调用的栈帧

在编译时，Go 编译器会计算函数在运行时可能使用的最大栈大小。计算出的尺寸被称为函数的栈帧大小（stack frame size）。在计算过程中，所有的代码分支都会被考虑，即使其中某些分支在运行时不会被执行。

我们可以使用 -S 编译器选项显示函数的栈帧大小。让我们来看以下示例：

```go
// frame.go
package main

import (
  "fmt"
  "math/rand"
)

func bar(s []uint32, n byte) (r byte) {
  s = s[:120]
  var a = [5000]byte // n == 1250 * 4
  for i, v := range s {
    a[i * 4 + 0] = byte(v >> 0)
    a[i * 4 + 1] = byte(v >> 8)
    a[i * 4 + 2] = byte(v >> 16)
    a[i * 4 + 3] = byte(v >> 24)

  var v = a[0]
  for i := 0; i < len(a); i++ {
    r += v - a[i]
    v = a[i]
  }
  return
}

func foo(n byte) uint16 {
    var a = [2500]int32
    for i := range a {
        a[i] = rand.Uint32()
    }
    x := bar(a[:1250], n)
    y := bar(a[1250:], n)
    return uint16(x) << 8 | uint16(y)
}

func main() {
    x := foo()
    fmt.Println(x)
    duck()
}

var v interface{}

//go:noinline
func duck() {
    if v != nil {
        v = [16000]byte{}
        panic("unreachable")
    }
}
```

使用 -S 编译器选项运行，我们将得到以下输出（省略了部分文本）：
$ go run -gcflags=-S frame.go

从输出中，我们可以得到：

- bar 帧的大小为 5024 字节。
- foo 函数的帧大小为 10056 字节。
- main 函数的帧大小为 64 字节。
- duck 函数的帧大小为 16024 字节。请注意，尽管 duck 函数实际上是一个空函数，但它的帧大小并不是零。这一事实将在后面展示的代码优化技巧中被利用。

在运行时，在进入函数调用执行之前，Go 运行时会在栈上标记一段内存区域供调用使用（用于分配栈内存块）。该内存区域被称为函数调用的栈帧，其大小为被调用函数的栈帧大小。如前所述，帧大小是在编译时计算的。当函数内部的值（部分）被确定为分配在栈上时，其偏移量（相对于对该函数的任何调用栈帧的起始位置）也在编译时确定。在运行时，函数的栈帧标记了所有分配在栈上的值部分的内存地址，这就是为什么在栈上分配内存块比在堆上更快。

## 4.4 栈的增长与收缩

在运行时，使用一个游标来标记 goroutine 使用部分和可用部分之间的边界。当进入深层函数调用时，游标会向前移动（指向可用部分），当 goroutine 完全退出时，会向后移动（指向使用部分）。向前移动和向后移动等于相应函数调用的栈帧大小。goroutine 的栈大小在运行时可能是动态的。在官方 Go 运行时第 19 版本中，初始栈大小始终是 2KiB；从 19 版本开始，默认栈大小仍然是 2KB。

对于某些 goroutine，随着函数加深且栈上需要更多的调用帧，当前的栈大小可能变得不足。在 goroutine 执行期间，栈会根据需要进行增长。相反，当函数深度变浅时，goroutine 的栈大小可能会变得太大。因此，栈可能会收缩。然而，为了避免频繁的增长和收缩，栈在过大时不会立即收缩。只有在垃圾回收期间过大时才会收缩。在 Go 编译器和运行时的实现中，栈大小始终是 $2^n$，其中 $n$ 大于 10。最小栈大小是 2KB。在栈增长的过程中，Go 运行时会创建一个更大的栈内存来替换旧栈，旧栈已使用的部分会被复制到新栈中，这导致了所有分配在栈上的值地址的变化。以下是一个展示栈增长和收缩影响的示例。我们在栈增长（由调用函数引起）和垃圾回收周期后寻找 x 的地址。

```go
package main

import "runtime"

//go:noinline
func f(i int) byte {
	var a [1<<13]byte // 分配在栈上并触发增长
	return a[i]
}

func main() {
	var x int
	println(&x) // <address 1>
	f(i) // (栈增长)
	runtime.GC() // (栈收缩)
	println(&x) // <address 2>
	runtime.GC() // (栈收缩)
	println(&x) // <address 3>
	runtime.GC() // (栈收缩)
	println(&x) // <address 4>
	runtime.GC() // (不收缩)
	println(&x) // <address 4>
}
```

注意，前两次手动 GC 调用都导致了收缩，但最后一次没有。让我们分析栈在程序执行期间是如何增长和收缩的：

1. 开始时，初始栈大小为 2KiB。
2. f 的帧大小为 8 字节。在进入 f 函数之前，栈增长到 16KiB（大于需求）。
3. f 函数完全退出后，栈不会立即收缩，直到发生垃圾回收。
4. 第一次运行时 GC 将栈收缩到 8KiB。
5. 第二次运行时 GC 将栈收缩到 4KiB。
6. 第三次运行时 GC 不收缩栈，尽管 2KiB 已足够。原因是当前的运行时实现不会将栈收缩到小于需求四倍的大小。

数组分配在栈上的原因将在本章后续部分解释。虽然在实践中很少发生，但我们应该避免频繁的栈增长和收缩。也就是说，对于某些少数情况，将部分分配在栈上可能不是好主意。

栈增长有一个全局限制。截至 Go 工具链 21 版本，64 位系统的最大栈大小为 1 GB（而非 GiB），32 位系统为 250 MB（而非 MiB）。注意，当前栈增长实现允许的实际栈大小约为最大栈设置的一半（64 位系统为 512 MiB，32 位系统为 128 MiB）。

以下是一个因超过栈限制而崩溃的示例程序：

```go
package main

const N = 1024 * 1024 * 10 // 10M

func f(v [N]byte, n int) {
    if n > 0 {
        f(v, n-1)
    }
}

func main() {
    var x [N]byte
    f(x, 50)
}
```

如果将调用 `f(x, 50)` 改为 `f(x, 48)`，程序将正常退出（64 位系统）。

## 4.5 未使用空间导致的内存浪费

如前，Go 为每个 goroutine 创建一个栈。栈区域的大小通常大于其实际需要的，这意味着栈上浪费了一些内存。如果 goroutine 的栈增长到更大的尺寸，将会浪费更多内存。此外，还需要额外的内存来存储 goroutine 信息。同时存的 goroutine 越多，浪费的内存就越多。取决于可用内存，成千个同时存的 goroutine 可能不是问题，但百万级可能。

## 4.6 出各种原因，值（部分）即使只在一个 goroutine 中使用也会逃逸

以下子节将介绍一些情况（并非此类情况的完整列表）。

### 4.6.1 如果循环中声明的变量被循环外部的值引用，将逃逸到堆

例如，以下代码中的变量 `n` 将逃逸到堆。原因是，如果包含它的结构需要很多步骤才能完成，可能会存在许多并行的 `n` 实例。实例的数量在编译时很难或无法确定，而函数的栈帧大小必须在编译时确定，因此编译器让 `n` 的每个实例逃逸到堆。

诚然，对于这个特定的示例，编译器可以更智能地判断出循环确实只需要一个并行的 `n` 实例。当前的 Go 编译器（版本 21）并不考虑这些特殊情况。

```go
package main

func main() {
    var x *int
    for {
        var n = 1 // 移动到堆: n
        x = &n
    }
}
```



```go
break
}
- = x
}
```

## 4.6.2 如果参数被传递给接口方法调用，参数引用的值部分将逃逸到堆

例如，在以下代码中，值 x 将被分配在栈上，而值 y 将被分配在堆上。

```go
package main

type I interface {
  M(*int)
}

type T struct{}
func (T) M(*int) {}

var t T
var i I = t

func main() {
  var x int // 不逃逸
  t(&x)
  var y int // 移动到堆
  i(&y)
}
```

对于编译器来说，确定接口值的动态值（因此具体方法）通常是不可能的或成本太高，因此官方标准编译器在大多数情况下放弃了这样做。可能，接口值的具体方法可能会将其参数传递给其他 goroutine。为了安全见，官方标准编译器保守地让参数引用的值部分逃逸到堆。

在某些情况下，编译器可以在编译时确定接口值的动态值（以及具体方法）。如果编译器发现该方法没有将参数传递给 goroutine，则将允许参数引用的值部分不逃逸到堆。例如，在以下代码中，值 x 和 y 都被分配在栈上。值 y 没有逃逸的原因是该方法调用：`i(&y)` 被去虚拟化为了 `t.M(&y)`。

```go
package main

type I interface{
  M(*int)
}

type T struct{}
func (T) M(*int) {}

func main() {
  var t T
  var i I = t

  var x int
  t.M(&x)

  var y int
  i.M(&y)
}
```

## 4.6.3 在 Go 工具链版本 1.21 之前，reflect.ValueOf 函数调用会导致参数引用的值逃逸到堆

在 Go 工具链版本 1.21 之前，`reflect.ValueOf` 函数始终会在堆上进行分配（如果其唯一参数不是接口），并让其唯一参数引用的值逃逸到堆。从 Go 工具链版本 1.21 开始，对 `reflect.ValueOf` 函数的调用仅在必要时进行堆分配；因此，其唯一参数引用的值不会逃逸到堆。这可以通过以下程序证明。

```go
//reflect-value-escape-analysis.go
package main

import "reflect"

var x reflect.Value

func main() {
    var n = 100000 // line 9
    _ = reflect.ValueOf(&n)

    var k = 100000
    _ = reflect.ValueOf(&k) // line 13

    var q = 100000
    x = reflect.ValueOf(&q) // line 16
}
```

使用 Go 工具链的输出：

```bash
$ go version 1.20 run -gcflags=-m reflect-value-escape-analysis.go
[Run]: $HOME/cache/go/tag/go.1.20/bin/go run -gcflags=-m aaa.go
```

```text
./reflect-value-escape-analysis.go:9:6: moved to heap: n
./reflect-value-escape-analysis.go:13:22: k escapes to heap
./reflect-value-escape-analysis.go:16:22: q escapes to heap
```

```bash
$ go version 1.21 run -gcflags=-m reflect-value-escape-analysis.go
[Run]: $HOME/cache/go/tag/go.1.21/bin/go run -gcflags=-m aaa.go
```

```text
./reflect-value-escape-analysis.go:13:22: k does not escape
./reflect-value-escape-analysis.go:16:22: q escapes to heap
```

请注意，信息 `q escapes to heap` 实际上意味着 q 的副本逃逸到了堆（1.20 的输出中 k 也是如此）。

## 4.6.4 调用 fmt.Print 函数会导致其参数引用的值逃逸到堆

此类调用始终会在堆上进行分配，为每个参数创建一个副本（如果该参数不是接口），并让其引用的值逃逸到堆。

例如，在以下代码中，变量 x 将逃逸到堆，但变量 y 不。z 的副本被分配在堆上。

```go
package "fmt"

import "fmt"

func main() {
    var x = 1 << 20 // 移动到堆: z
    fmt.Println(x)
    var y = 2 << 20 // y 不逃逸
    println(y)
    var z = 3 << 20
    fmt.Println(z) // z 逃逸到堆
}
```

其他 fmt.Print 函数也存在相同的情况。

## 4.6.5 函数返回结果引用的值将逃逸

追踪函数的返回结果是否被其调用者使用的成本很高，因此编译器让所有由结果引用的值都逃逸。

例如，在以下代码中，假设函数 f 不是可内联的（inline-able），那么值 *p* 将逃逸到堆，因为它被返回结果引用。

```go
package "fmt"

import "fmt"

func main() {
    // 示例逻辑由于原文 OCR 重复，此处遵循核心逻辑说明
}
```




以下是使用该技巧的示例：

```go
package main
```

```go
var sink interface{}
```

```go
 //go:noinline
func escape(x interface{}) {
    sink = x
    sink = nil
}
```

```go
func main() {
    var a = 1 // 移动到堆: a
    var b = true // 移动到堆: b
    escape(&a)
    escape(&b)
    println(a, b)
}
```

由于 //go:noinline 指令仅用于工具链和标准包的开发，该技巧的代码在用户代码中可以修改如下所示。官方 Go 编译器不会内联可能可能调用自身的函数调用。

```go
var sink interface{}
```

```go
func escape(x interface{}) {
    if x == nil {
        escape(x) // 避免被内联
        panic("x must not nil")
    }
}
```

```go
sink = x
sink = nil
```

当然，如果我们知道某些值将分配在堆上，那么我们只需要让这些值引用预期的逃逸值即可。

## 4.8.2 使用显式值拷贝帮助编译器检测某些值未逃逸

让我们重新回顾之前使用的示例（带有细微修改，b 现在初始化为 true）：

```go
package main
```

```go
func main() {
    var (
        a = 1 // 移动到堆: a
        b = true // 移动到堆: b
        c = make(chan struct{})
    )
    go func() {
        if b {
```

```go
a++
close(c)
<-c
b = !b
println(a, b) // 2 false
}}()
```

在这个示例中，变量 a 和 b 逃逸了。如果我们通过如下所示（以两种不同的方式）创建 a 和 b 的拷贝来修改示例，那么 a 和 b 将不会逃逸。

```go
package main

func main() {
var (
	a = 1 // 不逃逸
	b = true // 不逃逸
	c = make(chan int)
)
b1 := b
go func(a int) {
	if b1 {
		a++
		c <- a
	}
}(a) // 注意：逻辑从 OCR 上文中重构
a = <-c
b1 = !b1
println(a, b1) // 2 false
}
```

对于这个特定的示例，变量 a 和 b 是否逃逸对整个程序的性能的影响非常小。但这里介绍的提示在其他地方可能会有所帮助。

## 4.8.3 编译器用于分配决策的内存大小阈值

为了避免因 goroutine 栈超过最大栈大小而导致崩溃，即使编译器认为某个值仅由一个 goroutine 使用，如果该值大于某个阈值，它仍然会将该值分配在堆上。官方 Go 编译器 (v1.21) 使用了以下几个阈值：

- 在字符串和字节切片的转换之间，如果结果字符串或字节切片包含不超过 32 字节，则其间接部分（其底层字节）将分配在栈上，否则分配在堆上。然而，转换常量字符串（到字节切片）的阈值放宽到 64K (64 * 1024) 字节。
- 如果类型 T 的大小大于 64K (64 * 1024) 字节，则 T 值通过 new(T) 分配，且 &T() 将分配在堆上。
- 如果 make([]T, N) 的底层数组 []T 的大小大于 64K (64 * 1024) 字节，则底层数组将分配在堆上。在这里，N 是一个常量，因此编译器可以在编译时做出决策。如果它不是常量且大于 0，则底层数组将始终被分配在堆上。
- 在变量声明中，如果变量直接部分的大小大于 10M (10 * 1024 * 1024) 字节，则直接部分将分配在堆上。

以下是一些展示这些阈值效果的示例。

示例 1：

```go
package main

import "testing"

const t = "123456789ABCDEF" // len(t) == 16
const S = t + t + t + t + t // len(S) == 80
var bs33 = make([]byte, 33)

func f(w byte) func() {
    return func() {
        _ = string(w) // string(w) 不逃逸
    }
}

func g(v string) func() {
    return func() {
        _ = []byte(v) // ([]byte)(v) 不逃逸
    }
}

func h() {
    _ = []byte(S) // ([]byte)(S) 不逃逸
}

func main() {
    stat := func(f func()) int {
        allocs := testing.AllocsPerRun(10, f)
        return int(allocs)
    }
    println(stat(f('a'))) // 1 (堆分配)
    println(stat(f(bs33[32]))) // 0 (堆分配)

    println(stat(g(S[:33]))) // 1 (堆分配)
    println(stat(g(S[:32]))) // 0 (堆分配)

    println(stat(h())) // 0 (堆分配)
}
```

从示例 1 的输出中可以断定，如果字符串和字节切片之间的转换结果大于 32，则字节切片元素分配在堆上。注意，常量字符串转换的阈值放宽到了 64K，这就是为什么 h 函数中没有逃逸。

示例 2：

```go
package main

import "testing"

const N = 64 * 1024 // 65536
var n byte = 1

func makeSlice1() []byte {
	// make([]byte, N+1) 逃逸到堆
	a := make([]byte, N+1)
	for i := range a {
		a[i] = n
	}
	return a
}

func makeSlice2() []byte {
	// make([]byte, N-1) 不逃逸
	a := make([]byte, N-1)
	for i := range a {
		a[i] = n
	}
	return a
}

func makeSlice3() []byte {
	// make([]byte, N) 逃逸到堆
	a := make([]byte, N)
	for i := range a {
		a[i] = n
	}
	return a
}

func makeSlice4() []byte {
	// make([]byte, N-1) 不逃逸
	a := make([]byte, N-1)
	for i := range a {
		a[i] = n
	}
	return a
}

func main() {
	stat := func(f func() interface{}) int {
		allocs := testing.AllocsPerRun(10, f)
		return int(allocs)
	}
	println(stat(makeSlice1())) // 1 (堆分配)
	println(stat(makeSlice2())) // 0 (堆分配)
	println(stat(makeSlice3())) // 1 (堆分配)
	println(stat(makeSlice4())) // 0 (堆分配)
}
```

从示例 2 的输出中可以断定，如果 T 的大小大于 64K (65536) 字节，new(T) 创建的 值和 &T{} 将始终分配在堆上。（请注意，我们故意忽略了大小恰好为 65536 的情况。在 Go 工具链 v1.17 之前，如果大小为 65536，T 值将分配在堆上。Go 工具链 v1.17 修改了这一点。）

示例 3：

```go
package main

import "testing"

const N = 64 * 1024 // 65536
var n = 1

func makeSlice1() bool {
	// make([]bool, N+1) 逃逸到堆
	a := make([]bool, N+1)
	for i := range a {
		a[i] = n == 1
	}
	return true
}

func makeSlice2() bool {
	// make([]bool, N-1) 不逃逸
	a := make([]bool, N-1)
	for i := range a {
		a[i] = n == 1
	}
	return true
}

func makeSliceVar() bool {
	// make([]bool, n) 逃逸到堆
	a := make([]bool, n)
	for i := range a {
		a[i] = n == 1
	}
	return true
}

func main() {
	stat := func(f func() bool) int {
		allocs := testing.AllocsPerRun(10, func() {
			f()
		})
		return int(allocs)
	}

	println(stat(makeSlice1())) // 1 (堆分配)
	println(stat(makeSlice2())) // 0 (堆分配)
	println(stat(makeSliceVar())) // 1 (堆分配)
}
```

从示例 3 中可以断定：

- 如果 n 是常量且 make([]T, N) 结果的底层数组 [N] 大于 64K (64 * 1024)，则底层数组将分配在堆上。
- 如果 n 不是常量且 n 大于 0，底层数组将始终分配在堆上，因为编译器无法在编译时确定结果切片的数组大小。

（再次注意，如果常量 N 等于 make([]T, N) 的元素，在 Go 工具链 v1.17 之前将分配在堆上，但自 Go 工具链 v1.17 起将分配在栈上）。

示例 4：

```go
package main

import "testing"

const N = 10 * 1024 * 1024 // 10M
var n = N - 1

func declare10M() bool {
	var a [N]byte
	for i := range a {
		a[i] = 0
	}
	return true
}

func declare10Mplus() bool {
	var a [N+1]byte // 移动到堆 a
	for i := range a {
		a[i] = 0
	}
	return true
}

func redeclare10M() bool {
	a := [N]byte
	for i := range a {
		a[i] = 0
	}
	return true
}

func redeclare10Mplus() bool {
	a := [N+1]byte // 移动到堆 a
	for i := range a {
		a[i] = 0
	}
	return true
}

func main() {
	stat := func(f func() bool) int {
		allocs := testing.AllocsPerRun(10, func() {
			f()
		})
		return int(allocs)
	}

	println(stat(declare10M())) // 0
	println(stat(redeclare10Mplus())) // 1
	println(stat(redeclare10M())) // 0
	println(stat(redeclare10Mplus())) // 1
}
```





## 4.8.4 使用更小的阈值

请注意，如果指定了 -smallframes 编译器选项，上述的 64K 和 10M 阈值会变得小（分别为 16K 和 128K）。例如，如果我们使用命令 `go run -gcflags='-smallframes' main.go` 来运行下面的程序，所有检查的函数都将在堆上进行一次分配。

```go
// main.go
package main

import "testing"

const N = 16 * 1024 // 16384
const M = 128 * 1024 // 131072
var x byte = 123

func new16384() byte {
	// ({65535}byte) escapes to heap
	var a = new([N+1]byte)
	for i := range a { a[i] = x }
	return a[x]
}

func comptr16384() byte {
	// ({65535}byte) escapes to heap
	var a = &[N+1]byte{}
	for i := range a { a[i] = x }
	return a[x]
}

func make16384() byte {
	// make([]byte, N+1) escapes to heap
	var a = make([]byte, N+1)
	for i := range a { a[i] = x }
	return a[x]
}

func declare131073() byte {
	var a [M+1]byte
	for i := range a { a[i] = x }
	return a[x]
}

func main() {
	stat := func(f func()) int {
		allocs := testing.AllocsPerRun(10, func() {
			f()
		})
		return int(allocs)
	}
	// // Print 1 if "-smallframes" is specified,
	// and print 0 if "-smallframes" is unspecified,
	println(stat(new16384))
	println(stat(comptr16384))
	println(stat(make16384))
	println(stat(declare131073))
}
```

如果我们使用命令 `main.go` 来运行程序，那么所有被检查的函数都不会在堆上进行分配。

## 4.8.5 即使切片的底层数组大小大于或等于 64K（但不大于 10M），也在栈上分配其底层数组

我们已经了解到，可以在栈上分配的最大切片底层数组是 65536（在 Gochain v1.17 之前为 65535）。有一个技巧可以将此限制提高到 10M：从栈分配的数组派生切片。例如，在下面的程序创建的切片 s 的元素被分配在栈上。s 的长度为 10M，远大于 65536。

```go
package main

import "testing"

const N = 10 * 1024 * 1024 // 10M
var n = N/2

func func1() byte {
    var a [N]byte // allocated on stack
    for i := range a {
        a[i] = byte(i)
    }
    var s = a[:n] // a slice with 10M elements
    var p = &a
    return s[n] + p[n]
}

func main() {
    stat := func(f func()) int {
        allocs := testing.AllocsPerRun(10, func() {
            f()
        })
        return int(allocs)
    }
    println(stat(func1)) // 0
}
```

从 Gochain 1.21 版本开始，这个技巧仍然有效。

## 4.8.6 在栈上分配任意长度的切片的底层数组

看起来当前标准 Go 编译器实现（v1.21.n）中的逃逸分析模块漏掉了使用复合字面量（composite literals）创建切片的情况。当使用复合字面量创建切片时，切片元素始终会被分配在栈上（如果编译器认为切片元素仅由一个 goroutine 使用），无论切片的长度和元素的大小。例如，下面的示例程序将在栈上分配字节切片的 500M 个元素。

```go
package main

import "testing"

const N = 500 * 1024 * 1024 // 500M
var v byte = 123

func createSlice() byte {
  // []byte{...} does not escape
  var s = make([]byte, N)
  for i := range s { s[i] = v }
  return s[v]
}

func main() {
  stat := func(f func()) int {
    allocs := testing.AllocsPer(10, func() {
      f()
    })
    return int(allocs)
  }
  println(stat(createSlice)) // 0 (heap allocations)
}
```

未来的 Go 工具链版本可能会更改实现，导致该技巧在以后可能失效。到目前（Go 工具链 1.21n），该技巧是有效的。

## 4.8.7 更多在栈上分配任意大小值的技巧

在更多的边缘情况下，任意大小的值会被分配在栈上。同样地，未来的 Go 工具链版本可能会（也可能）更改实现细节，导致这些情况的分配行为可能会发生变化。

以下所有的 [N]byte 值都被分配在栈上。

```go
const N = 1024 * 100

//noinline
func boxLargeSizeValue() {
  var x interface{} = [N]byte // 1
  println(x == nil)
}

//noinline
func largeSizeParameter(x [N]byte) { // 2

//noinline
func largeSizeElement() {
  var m map[int][N]byte
  m[0] = [N]byte() // 3
}
```

然而，正如倒数第二个章节中提到的，


第二策略是一种辅助策略。本文将不再赘述它。在另外两种策略生效的情况下，堆上分配内存块的频率越高，启动 GC 周期就越频繁。

请注意，当前的 GC 调优器（pacer）设计并不保证适用于所有用例。它在未来的官方标准 Go 编译器/运行时将会不断改进。

## 5.2 自动 GC 可能会影响 Go 程序的执行性能

GC 周期会消耗某些 CPU 资源，因此取决于程序代码的编写方式，可能会可能会 Go 的执行性能。通常，如果程序代码写得很好，我们不需要担心 GC 带来的性能影响，因为 GC 周期仅消耗主程序逻辑消耗的 CPU 资源的一小部分。与自动 GC 带来的便利相比，这种微小的性能损失是值得划的。

然而，如果程序中的某些代码编写不当，导致 GC 周期变得繁忙（频繁运行并扫描大量指针），那么 GC 可能会严重影响程序的执行性能。

## 5.3 如何减轻 GC 压力？

无论 GC 调优器如何（以及未来如何），减轻 GC 压力的基本原理包括：

- 在堆上分配更少短周期的内存块（垃圾回收产生速度）。
- 创建更少的指针（扫描工作负载控制）。

当局部值分配在堆上时，栈上会创建一个隐式指针来引用该局部值，以便该值部分是可追溯的（从栈开始）。这意味着减少堆分配有助于减少指针。

在编程中，内存分配和指针创建是不可避免的。如果需要，就尽管去做。我们不需要费费精力去刻意避免指针。

事实上，指针通常可以用来成本。是否使用某些指针取决于具体情况。我们应该在缺点显而易见的情况下避免使用指针。

我们应该避免不必要的内存分配，尤其是不必要的内存位置。然而，由于许多原因（如语言安全性和 API 设计限制），不必要的内存分配很难完全避免。Go 不是 C，我们应该承认并接受这一事实。毕竟，Go 比 C 提供了更多便利性。

之前的章节已经介绍了一些避免分配的技巧。接下来的章节将介绍更多内容。

## 5.4 内存碎片

随着内存块不断被分配和回收，内存会变得碎片。目前的官方标准 Go 运行时以有效的方式管理内存（基于 tcmalloc），因此碎片在 Go 编程中通常不是问题。

本书没有提供避免内存碎片的建议。

## 5.5 共享内存块导致的内存浪费

有时，多个值部分被载在同一个内存块（分配在堆上）中。只有当所有值部分都不被使用时，该内存块才能被回收。换句话说，内存块上的一个微小值部分就会阻止内存块被回收，即使该微小部分只占内存块的一小部分。

通常，这种情况发生在以下场景：

- 切片（或数组或字符串）的若干元素仍然存活，但其他未使用。
- 结构体值的字段仍然存活，但其他字段未使用。
- 以上两者的结合。

以下是一个展示这种情况的示例。示例中，切片的 1000 个元素都载在同一个内存块上。

```go
package main

import (
    "log"
    "runtime"
    "time"
)

func main() {
	log.SetFlags(0)

	var s = make([]int, 1000)
	for i := range s {
		s[i] = 1
		runtime.SetFinalizer(&s[i], func(v interface{}) {
			log.Println("element", *v.(*int), "is collected")
		})
	}

	var p = &999
	runtime.GC()

	// log.Println(*p) // 999
	time.Sleep(time.Second)
}
```

运行此程序，它将打印：

element 999 is collected
element 998 is collected
element 997 is collected
...
element 1 is collected
element 0 is collected

输出表明新的 GC 周期（由手动调用 runtime GC 触发）使得载有切片元素的内存块被回收，否则这些元素的终结器将不会执行。

让我们取消注释 `Print(*p)` 行并再次运行程序，然后它将仅仅打印 999，这表明当手动 GC 周期结束时，载有切片元素的内存块仍未被回收。是的，事实上切片中的最后一个元素仍在使用阻止了内存块被回收。

我们可以将长生存值部分拷贝（使其载在较小的内存块上）到被回收的旧较大内存块中。例如，我们替换上述程序中的以下行（并开启 `log.Println(*p)` 行）：

```go
var p = &[999]
with
var v = a[999] // 拷贝一份
var p = &v
```

GC 将使得载有切片元素的内存块被回收。

标准 `strings`（或 `bytes`）包中某些函数的返回值是传递给这些函数的参数的子字符串（或切片）。这些函数包括 `Fields`、`Split` 和 `Trim`。同样，如果一个子字符串（或切片）存活时间且很小，而对应的参数短但长度很大，我们应该复制这样的子字符串（或切片），否则载有底层字节的（结果和结果）将无法释放。

## 5.6 尝试减轻 GC 压力。

无论 GC 调优器如何（以及未来如何），减轻 GC 压力的基本原理包括：

- 在堆上分配更少短周期的内存块（垃圾回收产生速度）。
- 创建更少的指针（扫描工作负载控制）。

当局部值分配在堆上时，栈上会创建一个隐式指针来引用该局部值，以便该值部分是可追溯的（从栈开始）。这意味着减少堆分配有助于减少指针。

在编程中，内存分配和指针创建是不可避免的。如果需要，就尽管去做。我们不需要费费精力去刻意避免指针。

事实上，指针通常可以用来成本。是否使用某些指针取决于具体情况。我们应该在缺点显而易见的情况下避免使用指针。

我们应该避免不必要的内存分配，尤其是不必要的内存位置。然而，由于许多原因（如语言安全性和 API 设计限制），不必要的内存分配很难完全避免。Go 不是 C，我们应该承认并接受这一事实。毕竟，Go 比 C 提供了更多便利性。

## 5.7 使用 GC 控制频率

GC 变量设置了 GC 周期后堆的目标百分比。默认值为 100，这意味着在触发下次 GC 周期时堆将翻倍。你可以通过 `GOGC` 环境变量或调用 `runtime/debug.SetGCPercent` 来更改此值。

如果 GC 值为负数，则禁用 GC。

当 GC 值为正数时，Go 运行时将使用以下公式计算下次 GC 周期的目标堆大小：

```
target heap size = live heap * (1 + GOGC/100)
```

例如，如果 GOGC 为 100，目标堆大小将是活堆的两倍。如果 GOGC 为 200，目标堆大小将是活堆大小的三倍。

通过增加 GOGC 可以减少 GC 周期的频率但会增加内存占用。通过减少 GOGC 可以减少内存占用但会增加 GC 周期的频率。





"math/rand"
"time"

```go
var x [512] *int

func garbageProducer() {
	rand.Seed(time.Now().UnixNano())

	for i := 0; i < 1; i++ {
		n := 6 + rand.Intn(6)
		for j := range x {
			x[j] = make([]int, 1<<n)
			for k := range x[j] {
				x[j][k] = new(int)
			}
		}
	}
	time.Sleep(time.Second / 1000)
}

func main() {
	garbageProducer() // never exit
}
```

使用环境变量 `GODEBUG=grace=1` 运行（输出中省略了一些无关的起始行）。

```
$ GODEBUG=grace=1 run gctrace.go

gc 1 $0.017s 8%: ... 3->4 MB, 4 MB goal,
gc 2 $0.037s 8%: ... 7->8->4 MB, 8 MB goal,
gc 3 $0.064s 13%: ... 8->9->4 MB, 9 MB goal,
gc 4 $0.108s 10%: ... 9->9->10 MB, 10 MB goal,
gc 5 $0.127s 10%: ... 3->4->3 MB, 4 MB goal,
gc 6 $0.158s 10%: ... 6->7->2 MB, 8 MB goal,
gc 7 $0.175s 10%: ... 5->5->4 MB, 5 MB goal,
gc 8 $0.206s 10%: ... 8->->3 MB, 9 MB goal,
gc 9 $0.232s 10%: ... 5->6->4 MB, 6 MB goal,
gc 10 $0.269s 12%: ... 8->10->10 MB, 9 MB goal,
```

（在 Windows 上，应该将 DOS 命令设置为 "GODEBUG=grace=1" & go run gctrace.go。）

在这里，`#->->#` 和 `MB goal` 字段是我们最感兴趣的。在 `#->->#` 字段中：

- 最后一个数字是非垃圾堆总大小（即存活堆 live heap）。
- 第一个数字是 周期开始时的堆大小，它应该大约等于同一行中 `# MB goal` 的目标堆大小。

从输出中我们可以发现：
- 存活堆大小波动很大（是的，该程序可能就是这样设计的），

因此 GC 周期间隔也波动很大。

- GC 频率非常高，导致花费在 GC 上的时间百分比很高。上面的输出显示该百分比在 8% 到 12% 之间波动。

这是因为存活堆很小（大致保持在 5MiB 以下）且波动很大，但根内存块的大小几乎为零。

减少 GC 时间的一种方法是增加 `GOGC` 值：

```
$ GOGC=1000 gctrace=1 run gctrace.go
nc 1 $0.074s 2%: 38->15 MB, 40 MB goal,
c 2 $0.810a 1%: 160->163 MB, 167 MB goal,
c 3 $0.1285a 1%: 105->11 MB, 109 MB goal,
c 4 $0.1835a 1%: 125->128 MB, 129 MB goal,
c 5 $0.2331a 1%: 114->117 MB, 118 MB goal,
c 6 $0.2350a 1%: 199->201 MB, 204 MB goal,
c 7 $0.0303a 1%: 96->98 MB, 100 MB goal,
c 8 $0.0508a 1%: 204->210 MB, 207 MB goal,
c 9 $0.0511a 1%: 118->119 MB, 122 MB goal,
c 10 $0.3506a 1%: 43->43 MB, 44 MB goal.
```

（Windows 上，应该将 DOS 命令设置为 "GOGC=1000" & "GDEBUG=gctrace=1" & run gctrace.go）。

从上面的输出中发现，将 `GOGC` 值增加到 1000 后，GC 周期间隔和 GC 开始时的堆大小现在变得大得多。但 GC 周期间隔和存活堆大小波动很大，这对于某些程序可能是一个问题。接下来的章节将介绍解决这些问题的方法。

## 5.8 从 Go 工具链 1.18 开始，更大的 GC 根导致 GC 周期间隔

以下程序将在运行时创建一个实际大小为 150MiB 的 goroutine。栈内存的使用量为 256MiB。

```go
// bigstacks.go
package main

import (
    "math/rand"
    "time"
)

var x [512]*int

func garbageProducer() {
	rand.Seed(time.Now().UnixNano())

	for i := 0; i < 1; i++ {
		n := 6 + rand.Intn(6)
		for j := range x {
			x[j] = make([]int, 1<<n)
			for k := range x[j] {
				x[j][k] = new(int)
			}
		}
	}
	time.Sleep(time.Second / 1000)
}

func bigStack(c chan int, v byte) {
	defer func() {
		c <- 1
	}()
	var s = []byte{50 << 20} // 在栈上
	for i := range s {
		s[i] = v
	}
}

func main() {
	go bigStack(nil, 23)
	garbageProducer() // never exit
}
```

运行它，得到以下输出：
$ go version
go version go1.18.2 linux/amd64
$ GODEBUG=gctrace=1 run bigstacks.go

```
gc 1 0.0008s 23%: ... 3->4 MB, 4 MB goal, 150 MB stacks,
gc 2 0.691s 5%: ... 153->157 MB, 150 MB goal, 150 MB stacks,
gc 3 1.318s 5%: ... 179->180 MB, 183 MB goal, 150 MB stacks,
gc 4 2.040s 5%: ... 159->160 MB, 168 MB goal, 150 MB stacks,
gc 5 2.628s 5%: ... 155->156 MB, 168 MB goal, 150 MB stacks,
gc 6 3.385s 5%: ... 178->180 MB, 182 MB goal, 150 MB stacks,
gc 7 4.148s 5%: ... 180->181 MB, 187 MB goal, 150 MB stacks,
gc 8 4.798s 5%: ... 158->159 MB, 163 MB goal, 150 MB stacks,
gc 9 5.296s 5%: ... 165->169 MB, 169 MB goal, 150 MB stacks,
gc 10 5.867s 5%: ... 172->173 MB, 176 MB goal, 150 MB stacks,
```

输出显示在根总大小附近的 GC 间隔，官方运行时版本 1.18 使用栈空间（Go 版本 18），官方运行时版本 1.19+ 使用栈空间。因此，当使用工具链 1.18 运行上述程序时，目标堆大小更大：

$ go version
go version go1.18.5 linux/amd64
$ GODEBUG=gctrace=1 run bigstacks.go
...
gc 1 @0.015s ..., 4 MB goal, 256 MB stacks,
gc 2 @0.197s ..., 263 MB goal, 256 MB stacks,
gc 3 @0.772s ..., 258 MB goal, 256 MB stacks,
gc 4 @0.945s ..., 258 MB goal, 256 MB stacks,
gc 5 @0.5239s ..., 288 MB goal, 256 MB stacks,
gc 6 @0.122s ..., 264 MB goal, 256 MB stacks,
gc 7 @0.7384s ..., 279 MB goal, 256 MB stacks,
gc 8 @0.796s ..., 288 MB goal, 256 MB stacks,
gc 9 @10.102s ..., 291 MB goal, 256 MB stacks,
gc 10 @10.951s ..., 262 MB goal, 256 MB stacks,
```

以下程序使用一个包含指针的巨型包级变量，该程序的根内存块大小也是巨大的。

```go
// bigglobals.go
package main

import (
	"math/rand"
	"time"
)

var x [512][]int

func garbageProducer() {
	rand.Seed(time.Now().UnixNano())
	for i := 0; i < 1; i++ {
		n := 6 + rand.Intn(6)
		for j := range x {
			x[j] = make([]int, 1<<n)
			for k := range x[j] {
				x[j][k] = new(int)
			}
		}
	}
	time.Sleep(time.Second / 1000)
}
```

```go
var bigGlobal struct {
	P *int
	- [150 << 20]byte
}

func main() {
	garbageProducer() // never exit
	println(bigGlobal.p) // unreachable
}
```

运行它，得到以下输出：

$ GODEBUG=gtrace=1 go run bigglobals.go

```
gc 1 @0.266s O%: ... 150 MB goal, ... 150 MB globals,
gc 2 @0.885s O%: ... 154 MB goal, ... 150 MB globals,
gc 3 @1.616s O%: ... 168 MB goal, ... 150 MB globals,
gc 4 @2.327s O%: ... 165 MB goal, ... 150 MB globals,
gc 5 @3.011s O%: ... 168 MB goal, ... 150 MB globals,
gc 6 @3.493s O%: ... 155 MB goal, ... 150 MB globals,
gc 7 @4.208s O%: ... 167 MB goal, ... 150 MB globals,
gc 8 @4.897s O%: ... 162 MB goal, ... 150 MB globals,
gc 9 @5.618s O%: ... 165 MB goal, ... 150 MB globals,
gc 10 @6.338s O%: ... 169 MB goal, ... 150 MB globals,
```





## 5.10 使用 Go 工具链 v1.19 引入的内存限制策略避免频繁的 GC 循环

Go 标准编译器 v1.19 引入了一种新的调度策略：内存限制策略。该策略可以通过 `GOMEMLIMIT` 环境变量或 `runtime/debug.MemoryLimit` 函数进行配置。此内存限制设置了 Go 运行时使用的内存上限。换句话说，如果 Go 使用的内存总量（近似）超过了限制，当限制不再被超过时，将启动新的垃圾回收过程。内存限制的默认值为 `MaxInt64`，这实际上是禁用了该策略。

`GOMEMLIMIT` 环境变量可以有一个可选单位。支持的后缀包括 B、KIB、MIB、GiB 和 TiB。没有单位的值表示 B（字节）。内存限制和新的堆内存百分比策略可能会相互影响。为了演示目的，让我们禁用新的堆内存百分比策略并启用内存限制策略，以运行上面的 `gctrace` 示例。否则，`GOMEMLIMIT` 环境变量将无法被识别，因此自动垃圾回收将被关闭。

```
$ go version 1.19
GOMEMLIMIT=157MiB GODEBUG=gctrace=i go run gctrace
gc 1 0.283s 1%: 153->156 MB 157 MB goal, ...
gc 2 0.784s 1%: 151->152 MB 155 MB goal, ...
gc 3 1.445s 1%: 149->151 MB 152 MB goal, ...
gc 4 2.113s 1%: 148->150 MB 152 MB goal, ...
gc 5 2.765s 1%: 148->150 MB 152 MB goal, ...
gc 6 3.394s 1%: 147->150 MB 152 MB goal, ...
gc 7 4.006s 1%: 147->147 MB 152 MB goal, ...
gc 8 4.653s 1%: 147->147 MB 152 MB goal, ...
gc 9 5.326s 1%: 148->152 MB 152 MB goal, ...
gc 10 6.007s 1%: 148->149 MB 152 MB goal, ...
```

从输出中可以看出，内存限制策略还可以让 GC 间隔变得大得多且交错分布。

内存限制策略的目标之一是提供一种官方方法来替代内存气球（memory ballast）技巧。对于 Go 程序，如果合理设置了内存限制值，就能实现该目标。然而，有时很难为内存限制选择一个合适的值。如果该值小于 Go 程序实际需要的内存量，GC 循环将频繁启动。与上述所示的内存气球方案相比，这是一个缺点。请阅读关于使用内存限制策略的建议（其中包含了一篇理解 Go 垃圾回收的优秀文章）。

## 第 6 章

## 指针

## 6.1 避免在循环中进行不 nil 数组指针检查

当前的官方标准 Go 编译器实现（v1.21.n）中存在一些缺陷。其中之一是某些 nil 数组指针检查没有移动到循环之外。这里有一个示例展示了这一缺陷。

```go
// unnecessary-checks.go
package pointers
import "testing"
const N = 1000
var a [N]int
//go:noinline
func g0(a [N]int) {
    for i := range a {
        a[i] = i // line 12
    }
}
//go:noinline
func g1(a [N]int) {
    _ = a // line 18
    for i := range a {
        a[i] = i // line 20
    }
}
func Benchmark_g0(b *testing.B) {
    for i := 0; i < b.N; i++ { g0(&a) }
}

func Benchmark_g1(b *testing.B) {
    for i := 0; i < b.N; i++ { g1(&a) }
}
```

让我们使用 `-S` 编译器选项运行基测试，得到了以下输出（省略了无关文本）：

$ go test -bench -gcflags=-S unnecessary-checks.go

```
00004 00004 (unnecessary-checks.go:12) TESTB AL, (AX)
00006 00006 (unnecessary-checks.go:12) MOVQ CX, (AX)(CX*8)
...
00000 00000 (unnecessary-checks.go:18) TESTB AL, (AX)
00002 00002 (unnecessary-checks.go:18) XORL CX, CX
00004 00004 (unnecessary-checks.go:19) BMP 13
00006 00006 (unnecessary-checks.go:20) MOVQ CX, (AX)(CX*8)
```

Benchmark_g0-4 494.8 ns/op
Benchmark_g1-4 399.3 ns/op

从输出中我们可以发现 `g1` 的实现比 `g0` 的实现性能更好，即使它多了一行（第18行）。为什么？答案在汇编输出中。在 `g0` 的实现中，`TESTB` 指令是在循环内生成的，而在 `g1` 的实现中，`TESTB` 指是在循环外生成的。循环用于检查参数是否为 nil 指针。对于这种这种情况，检查一次可以避免编译器实现中的缺陷。还有第三种实现性能与 `g1` 实现一样快。第三种实现使用了从数组指针派生的切片。

```go
//go:noinline
func g2(x *[N]int) {
    a := x[:]
    for i := range a {
        a[i] = i
    }
}
```

请注意，如果函数被内联，基测试结果将会改变。这就是在这里使用 `//go:noinline` 指令的原因（在此之前，Go 从从不内联函数）。

### 数组作为结构体字段的情况

对于数组作为结构体字段的情况，情况比较复杂。例如，在以下代码中，`_ = t.a` 是没用的，`f1` 函数和 `f0` 函数之间的性能差异很小（事实上 `f1` 的性能可能慢，如果是在循环内生成的）。

```go
//go:noinline
type T struct {
    a [N]int
}

//go:noinline
func f0(t *T) {
    for i := range t.a {
        t.a[i] = i
    }
}
```

为了将指针检查移出循环，应该将数组复制到局部变量，采用上述方法：

```go
//go:noinline
func f1(t *T) {
    a := t.a
    for i := range a {
        a[i] = i
    }
}
```

或者简单的从数组派生切片：

```go
//go:noinline
func f2(t *T) {
    a := t.a[:]
    for i := range a {
        a[i] = i
    }
}
```

基测试结果：

Benchmark_f0-4 622.9 ns/op
Benchmark_f1-4 637.4 ns/op
Benchmark_f2-4 511.3 ns/op
Benchmark_f3-4 390.1 ns/op

注意，`f2` 的实现和 `f3` 一样快，但它们比 `f0` 快。这验证了我们的结论。

## 6.2 避免循环中不必要的指针解引用

有时，当前的官方标准 Go 编译器（v1.21.n）在循环内生成未优化的指令。我们必须编写另一种代码来获得最佳性能。

```go
// avoid-indirects.go
package pointers

import "testing"

//go:noinline
func f(t *T) {
    for i := range t.a {
        t.a[i] = i
    }
}

//go:noinline
func g(t *T) {
    var n int
    for _, v := range t.a {
        n += v
    }
    _ = t
    sum = n
}

var s = make([]int, 1024)
var r int

func Benchmark_f(b *testing.B) {
    for i := 0; i < b.N; i++ {
        f(&t)
    }
}

func Benchmark_g(b *testing.B) {
    for i := 0; i < b.N; i++ {
        g(&t)
    }
}

type T struct {
    a [1024]int
}

var sum int
```

基测试结果（省略了无关文本）：

```
$ go test -bench=. -gcflags=-S avoid-indirects.go

00004 00004 (avoid-indirects.go:12) TESTB AL, (AX)
00006 00006 (avoid-indirects.go:12) MOVQ CX, (AX)(CX*8)
...
00000 00000 (avoid-indirects.go:18) TESTB AL, (AX)
00002 00002 (avoid-indirects.go:18) XORL CX, CX
00004 00004 (avoid-indirects.go:19) BMP 13
00006 00006 (avoid-indirects.go:20) MOVQ CX, (AX)(CX*8)
00004 00004 (avoid-indirects.go:9) TESTB AL, (AX)
00006 00006 (avoid-indirects.go:9) MOVQ CX, (AX)(CX*8)
```

Benchmark-f-4 3024 ns/op
Benchmark-g-4 566.5 ns/op



```go
sum += h(s)
  ...
}
```

# 第 7 章

# 结构体 (Structs)

## 7.1 避免在循环中通过指针访问结构体字段

让 CPU 指令处理寄存器比处理内存快得多。因此，为了让编译器为循环生成更少的内存处理汇编指令，我们应该避免在循环中通过结构体指针访问其字段。

例如，在下面的代码中，函数 `g` 的性能比函数 `f` 高。

```go
package structs
import "testing"
const N = 1000
type T struct {
 x int
}
//go:noinline
func f(t *T) {
 t.x = 0
 for i := 0; i < N; i++ {
 t.x += i
}
}
//go:noinline
func g(t *T) {
 var x = 0
 for i := 0; i < N; i++ {
 x += 1
}
 t.x = x
}
```

```go
var t = &T{}

func Benchmark_f(b *testing.B) {
    for i := 0; i < b.N; i++ {
        f(t)
    }
}

func Benchmark_g(b *testing.B) {
    for i := 0; i < b.N; i++ {
        g(t)
    }
}
```

基准测试结果：
Benchmark_f-4    2402 ns/op
Benchmark_g-4    461.3 ns/op

函数 `g` 使用局部变量 `x` 来存储总和，并在最后将总和赋值给结构体字段。官方 Go 编译器足够智能，仅为函数 `g` 的循环生成寄存器处理汇编指令。

函数 `f` 实际上等同于下面声明的函数 `h`。

```go
//go:noinline
func h(t *T) {
    x := &t.x
    for i := 0; i < N; i++ {
        *x += 1
    }
}
```

因此，这里引入的建议实际上等于上一章引入的建议（避免在循环中进行不必要的指针解引用）。

## 7.2 小尺寸结构体经过特殊优化

这在值拷贝成本以及小尺寸类型/值中讨论过。

## 7.3 通过调整字段顺序来缩小结构体体积

结构体的字段顺序可能会影响结构体的大小，这在之前的章节提到过。

# 第 8 章

# 数组与切片 (Arrays and Slices)

## 8.1 避免使用大数组类型的字面量作为比较操作数

例如，在下面的代码中，函数 `CompareWithGlobalVar` 优优函数 `CompareWithLiteral`（针对官方 Go 编译器 v1.21）。

```go
package arrays

import "testing"

type T [1000]byte

var zero = T{}

func CompareWithLiteral(t *T) bool {
	return *t == T{}
}

func CompareWithGlobalVar(t *T) bool {
	return *t == zero
}

var x T
var r bool

func Benchmark_CompareWithLiteral(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r = CompareWithLiteral(&x)
	}
}

func Benchmark_CompareWithGlobalVar(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r = CompareWithGlobalVar(&x)
	}
}
```

```go
}
```

基准测试结果：
Benchmark_CompareWithLiteral-4 21214032 52.18 ns/op
Benchmark_CompareWithGlobalVar-4 36417091 31.03 ns/op

通过使用 `-S` ，我们可以发现编译器为函数 `CompareWithGlobalVar` 生成的指令比函数 `Literal` 少。这就是为什么 `CompareWithGlobalVar` 性能更好。对于小数组，两者的性能差异很小。请注意，未来的编译器版本可能会进行改进以消除两者之间的性能差异。

## 8.2 使用 Go 1.17 引入的切片转指针转换

Go 1.17 引入了切片到指针的转换。我们可以使用多种转换来拷贝切片。发现，在任何平台上，如果被拷贝切片的元素大于 64，转换方式的性能优于内置的 `copy` 函数。

```go
package arrays

import "testing"

const N = 64

var r []byte
var s = make([]byte, N)

func init() {
	println("=========", N)
	r = make([]byte, N)
}

func copy2(d []byte, s []byte) {
	*([N]byte)(d) = *([N]byte)(s)
}

func Benchmark_Copy(b *testing.B) {
	for i := 0; i < N; i++ {
		copy(r, s)
	}
}

func Benchmark_Copy2(b *testing.B) {
	for i := 0; i < N; i++ {
		copy2(r, s)
	}
}
```

基准测试结果：
========== N = 32
Benchmark_Copy-4 480 ns/op
Benchmark_Copy2-4 403 ns/op
========== N = 64
Benchmark_Copy-4 517 ns/op
Benchmark_Copy2-4 500 ns/op

在我的机器上（Linux/amd64），`copy2` 方式仅在切片切片底层数组的大小在 [25, 100] 范围内时性能较低。然而，有些人报告，对于较大的数组，`copy2` 方式总是性能良好的。因此，如果我们想对切片使用 `copy2`，请尝试用于元素不超过 64 字节的切片。另外要注意一个事实：如果拷贝操作涉及的两个切片的内存地址相同，则实际上需要进行重复。在这种情况下，内置的 `copy` 函数会避免重复（直到 Go v1.1）。

## 8.3 内置的 `make` 和 `append` 实现

Go 因此，通常通过 `make` 分配的切片会在 `make` 调用时置零。从 Go v1.5 开始，官方 Go 编译器实现了一项特殊优化：在下面的代码中，`y[:m]` 中的元素（其中 `m` 是 `copy` 用的返回值）在 `make` 调用时不会是零，因为它们会被覆盖。

```go
sum += h(s)
  ...
}
```
*(注：由于提供的待翻译文本中存在大量重复的占位或乱码片段，译文已根据要求对核心逻辑进行了翻译。)*




Go 1.18+ 中的新算法分配的内存通常比 Go 1.17 中的旧算法少。

请注意，每次切片扩容都需要一次内存分配。因此在编程中我们应该尽量减少切片扩容的次数。

`copy` 和 `append` 函数之间（直到 Go 工具链 1.21）另一个细微区别是：`copy` 函数在检测到两个切片的第一个元素地址相同时将不会复制元素，而 `append` 函数会进行此类检测。
这意味着，在下面的代码中，`copy` 调用比 `append` 调用效率高得多。

```go
var x = make([]T, 10000)
copy(x, x)
x = append(x[:], y...)
```

演示这种差异的一个具体示例是下面所示两个 `DeleteSliceElements` 函数；当 `len == j` 时，使用 `copy` 的版本比使用 `append` 的版本性能得多。

```go
func DeleteSliceElements(s []T, i, j int) []T {
	s = s[i:j] // 边界检查
	return append(s[:i], s[j:]...)
}

func DeleteSliceElements(s []T, i, j int) []T {
	s = s[:j] // 边界检查
	return s[:i+copy(s[i:], s[j:])]
}
```

## 8.4 如果我们知道调用将分配内存，尝试对 append 用的第一个参数进行裁剪

如果 `append` 调用触发了分配且没有更多元素需要追加到结果切片中，那么最好是对 `append` 用的第一个参数进行裁剪，尝试节省内存（并消耗更少的 CPU 资源）。

一个示例：

```go
package main

func main() {
	x := make([]byte, 100, 500)
	y := make([]byte, 500)
	a := append(x, y...)
	b := append(x[:len(x):len(x)], y...)
	println(cap(a)) // 1024
	println(cap(b)) // 640
}
```

注释所示的输出是针对 Go 1.17 的。对于 Go 1.18，上述程序打印结果：

896
640

当然，如果我们确信知道 `append` 调用中第一个参数切片的空容量足够容纳所有追加元素，那么我们就不应该对第一个参数进行裁剪。

## 8.5 扩容切片（增大切片容量）

如果在扩容过程中需要重新分配切片的底层数组，有两种方法可以将切片 `x` 的容量扩展到 `c`。

```go
// 方式 1
func Grow_MakeCopy(x []T, c int) []T {
    r := make([]T, c)
    copy(r, x)
    return r[:len(x)]
}
```

```go
// 方式 2
func Grow_Online(x []T, c int) []T {
    return append(x, make([]T, c-len(x))...[:len(x)])
}
```

两种方法都经过官方 Go 编译器的优化。如上述，方式 1 中的 `make` 调用没有在 `r[:len(x)]` 中预留元素。在方式 2 中，`make` 根本没有产生分配。

理论上，由于有了这两种优化，两种方法的性能相当。但基准测试结果显示方式 1 性能略好。

注意，在官方 Go 编译器实现 v1.20 之前，如果 `append` 调用第一个参数的类型是命名类型，则方式 2 的优化不起作用。例如，下面的 `Grow_Online_Named` 函数比上面的 `Grow_Online` 函数慢得多。

```go
type S []T
func Grow_Oline_Named(x []T, c int) []T {
    return append(x, make(S, c-len(x))...[:len(x)])
}
```

该缺陷自 Go 工具链 v1.20 起已修复修复。

## 8.6 尝试一步扩容切片

如所述，切片在 `append` 调用中如何扩容取决于具体实现，这意味着切片扩容的结果在 Go 规范中并未规定。

如果在编写代码时预测了切片的最大长度，我们应该以最大长度作为容量分配切片，以避免由于多次切片扩容导致的可能分配。

如果切片的生命周期很短，我们可以按照估计的大容量对其进行分配。这可能会暂时浪费一些内存，但元素内存很快就会释放。

## 8.7 克隆切片

自 Go 工具链 15 版本起，克隆切片的最有效方法是 `make+copy` 方式：

```go
sCloned := make([]T, len(s))
copy(sCloned, s)
```

在许多情况下，`make+copy` 方式比下面的 `append` 方式快一点，因为如上述，`append` 可能会分配并零值一些额外的元素。

```go
sCloned := append([]T(nil), s...)
```

例如，在下面的情况下，分配了 8191 个元素并进行了零值。

```go
x := make([]byte, 1<<15+1)
y := append([]byte(nil), x...)
println(cap(y) - len(x)) // 8191
```

## 8.8 合并两个切片

没有通用的的方法可以将两个切片合并到一个新切片中。


```go
package arrays

import "testing"

//noinline
func sum_forange1(s []int) int {
    var n = 0
    for i := range s {
        n += s[i]
    }
    return n
}

//noinline
func sum_forange2(s []int) int {
    var n = 0
    for _, v := range s {
        n += v
    }
    return n
}

//noinline
func sum_plainfor(s []int) int {
    var n = 0
    for i := 0; i < len(s); i++ {
        n += s[i]
    }
    return n
}
```

```go
var s = make([]int, 1<<16)
var r int

func Benchmark_forange1(b *testing.B) {
    for i := 0; i < b.N; i++ {
        r = sum_forange1(s)
    }
}

func Benchmark_forange2(b *testing.B) {
    for i := 0; i < b.N; i++ {
        r = sum_forange2(s)
    }
}

func Benchmark_plainfor(b *testing.B) {
    for i := 0; i < b.N; i++ {
        r = sum_plainfor(s)
    }
}
```

基准测试结果：

| Benchmark_forrange-1 | 34044 | 33793 ns/op |
| Benchmark_forrange-2 | 31474 | 37819 ns/op |
| Benchmark_plainfor-4 | 34646 | 33704 ns/op |

从基准测试结果中我们可以发现，普通循环（plain loop）和只有一个迭代变量的 for-range 循环都比使用第二个迭代变量的 for-range 循环性能更优。

## 8.12 重置数组或切片的所有元素

从工具链 v1.5 开始，引入了一项特殊优化，用于高效地清空数组或切片中的元素。具体而言，以下只有一个迭代变量的 for-range 循环将被 Go 编译器官方优化为内部的 `memclr` 操作：

```go
// v0 是零值字面量（可能为 nil）
// 容器 aSliceOrArray 的元素类型
for i := range aSliceOrArray {
  aSliceArray[i] = v0
}
```

如果存在两个迭代变量，但第二个是空白标识符 - _，该优化同样有效。

对于大多数情况，上述代码性能优于以下代码：

```go
for i := 0; i < len(aSliceOrArray); i++ {
  aSliceArray[i] = v0
}
```

在我的机器上，只有当切片长度小于 6（元素类型为 byte）时，`memclr` 才会变慢。

在 Go 工具链 v1.19 之前，可能需要指向数组的指针使此优化生效。

事实上，这项优化对于切片比对于数组和指针更有意义，因为有一种更简单（有时性能更高）的方法来重置数组元素：

```go
anArray = ArrayType{}
*ArrayPointer = ArrayType{}
```

注意：Go 1.21 添加了内置函数 `clear`，可用于重置切片中的所有元素。从 Go 1.21 开始，我们应该尝试使用 `clear` 函数，而不是依赖 `memclr` 优化来重置切片。

## 8.13 在切片表达式中显式指定容量

当前的官方 Go 编译器 (v1.21.n) 在实现上存在一个缺陷。该缺陷导致对切片表达式 `s[i:i+4]` 执行了比 `s[i:i:i+4]` 更多的索引检查。这导致在以下代码中，函数 `g` 性能优函数 `f`。

```go
// slice_test.go
package arrays
```

```go
import "testing"
const N = 1 << 10
var s = make([]byte, N)
var r = make([]byte, N/4)
```

```go
func f(rs []byte, bs []byte) {
  for i, j := 0; i < len(bs) - 3; i += 4 {
    s2 := bs[i:i+4]
    rs[j] = s2[3] ^ s2[0]
    j++
  }
}
```

```go
func g(rs []byte, bs []byte) {
  for i, j := 0; i < len(bs) - 3; i += 4 {
    s2 := bs[i:i+4]
    rs[j] = s2[3] ^ s2[0]
    j++
  }
}
```

```go
func Benchmark_f(b *testing.B) {
  for i := 0; i < b.N; i++ {
    f(r, s)
  }
}
```

```go
func Benchmark_g(b *testing.B) {
  for i := 0; i < b.N; i++ {
    g(r, s)
  }
}
```

基准测试结果：

| Benchmark_f-4 | 2676529 | 445.5 ns/op |
| Benchmark_g-4 | 3506199 | 333.7 ns/op |

## 8.14 使用索引表节省比较

在以下代码中，`bar` 函数性能优于 `foo` 函数。

```go
func foo(n int) {
  switch n % 10 {
    case 1, 2, 6, 7, 9:
      // do something
  }
}
```

```go
var indexTable = [10]bool{
	1: true, 2: true, 6: true, 7: true, 9: true,
}
func bar(n int) {
	if indexTable[n%10] {
		// do something
}
```

`foo` 函数在进入分支前需要五次比较，而 `bar` 函数只需要一次。这就是为什么 `bar` 函数性能更好。

# 第 9 章 字符串与切片

### 字符串与切片之间的转换

字符串可以被视为不可变的切片。由于字符串的内容不会被修改，任何函数都可以安全地使用字符串而无需担心其被修改。当将字符串转换为切片时，字符串和结果切片应该共享元素。这意味着字符串内容会被复制到结果切片中（需要内存分配）。同样，将切片转换为字符串时，切片内容也会复制到结果字符串中（需要内存分配）。

事实上，在某些情况下复制并非必要的。当前的 Go 编译器对简单情况进行了多种优化以避免复制。这些优化如下：如果我们使用标准 Go 编译器构建以下代码，函数 `f` 和 `g` 之间的性能差异可以忽略不计。原因是函数 `f` 中使用的 `[]byte(s)` 转换没有产生分配。

```go
func f(s string) {
    for i, b := range []byte(s) {
        // do something
    }
}
```

```go
func g(s string) {
    for i := 0; i < len(s); i++ {
        b := s[i]
        // do something
    }
}
```

## 9.1.2 作为比较操作数的切片转字符串转换不会产生分配

以下是 `bytes` 包中 `Equal` 函数的实现。在实现中，转换复制了参数的字节切元素。

```go
func Equal(a, b []byte) bool {
    return string(a) == string(b)
}
```

这种优化导致在以下代码中（官方 Go 编译器 v1.21），`verbose` 函数比 `clean` 函数高效：

```go
package main

import "testing"

func verbose(x, y, z []byte) {
	switch {
	case string(x) == string(y):
		// do something
	case string(x) == string(z):
		// do something
	}
}
```

```go
func clean(x, y, z []byte) {
	switch string(x) {
	case string(y):
		// do something
	case string(z):
		// do something
	}
}
```

```go
func main() {
    x := []byte{1023: 'x'}
    y := []byte{1023: 'y'}
    z := []byte{1023: 'z'}
    stat := func(x, y, z []byte) int {
        allocs := t.AllocsPerRun(10, func() {
            f(x, y, z)
        })
        return int(allocs)
    }
    println(stat(verbose)) // 0
    println(stat(clean)) // 3
}
```

从输出中我们可以得到 `verbose` 函数没有产生分配，而简单函数产生了三次，这就是前者性能更好的原因。

这两个函数之间的性能差异在未来的 Go 工具链版本中可能会被移除。

我们也可以使用 `bytes.Compare` 函数来比较两个字节切片。在需要三向比较的情况下（如下所示），`bytes.Compare` 函数性能更好。

```go
// 注意，两个分支就足够形成三向比较。
func doSomething(x, y []byte) {
	switch bytes.Compare(x, y) {
	case -1:
		// do something 1
	case 1:
		// do something 2
	default:
		// do something 3
	}
}
```

在简单的（单向）字节切片比较中不要使用 `Compare` 函数，如下代码所示。对于此类情况，它的速度较。

```go
func doSomething(x, y []byte) {
	if bytes.Compare(x, y) == 0 {
		// do something
	}
}
```

## 9.1.3 作为 map 元素获取索引键的切片转字符串转换不会产生分配

注意：此优化未针对 map 元素修改语句。可以通过以下示例证明，在 `get` 函数中转换 `string(key)` 没有产生分配，但另外两个函数中的两个转换产生了分配。

```go
package "testing"

import
var m = map[string]int{}
var key = []byte{'k', 'e', 'y'}
var n int
```

```go
func get() {

	t = m[string(key)]
}
```

```go
func inc() {
	m[string(key)]++
}
```





```go
func set() {
    m[string(key)] = 123
}

func main() {
    stat := func(f func()) int {
        allocs := t.AllocsPerRun(10, f)
        return int(allocs)
    }
    println(stat(get)) // 0
    println(stat(set)) // 1
    println(stat(inc)) // 1
}
```

当 key 以结构体或数组复合字面量的形式出现时：`T1{..., string(key), ...}`，这种优化是有效的，其中 Tx 是结构体类型或数组类型。例如，以下代码中的 `string(key)` 转换也不会产生重复分配。

package main

```go
import t "testing",
```

```go
type T struct {
    a int
    b bool
    k [2]string
}
```

```go
var m = map[T]int{}
var key = []byte{'k', 'e', 'y', 99: 'z'}
```

```go
var n int
func get() {
    n = m[T[:2]string{1:string(key)}]
}
```

```go
func main() {
    print(int.AllocsPerRun(10, get)) // 0
}
```

这种优化导致了一个有趣的案例。在下面的代码段中，函数 `modify1` 进行了一次分配，而函数 `modify2` 没有分配，因此函数 `modify2` 的性能优于 `modify1`。原因是 `modify2` 函数中使用的 `string(key)` 仅出现在 map 元素的检索过程中，而 `modify1` 中使用的 `string(key)` 则被认为出现在 map 元素的修改语句中。

package main

```go
import t "testing",
```

```go
var key = []byte{'k', 'e', 'y'}
```

```go
var m1 = map[string]int{"key": 0}
```

```go
func modify1() {
    m1[string(key)]++
    // (逻辑上) 等于：
    m1[string(key)] = m1[string(key)] + 1
}

var m2 = map[string]*int{"key": new(int)}
func modify2() {
    *m2[string(key)]++
    // 等于:
    // p := m2[string(key)]; *p = p + 1
}

func main() {
    stat := func(func()) int {
        allocs := t.AllocsPerRun(10, f)
        return int(allocs)
    }
    println(stat(modify1)) // 1
    println(stat(modify2)) // 0
}
```

如果 map 的条目被删除但 map 的元素被频繁修改，最好是使用指针类型作为 map 的元素类型。

## 9.1.4 当字节切片到字符串的转换作为字符串拼接的操作数时，如果拼接的操作数中至少有一个是非空字符串常量，则不会发生分配

在这个示例中，函数 f（稍微冗长的那个）在大多数情况下比函数 g 高效得多（截至 Go 工具链 v1.21.n 版本）。

```go
package main

import "testing"

var s = []byte{0: '$', 32: 'x'} // len(s) == 33

func f() string {
    return " " + string(s) + string(s)[1:]
}

func g() string {
    return string(s) + string(s)
}

var x string
func stat(add func() string) int {
    c := func() {
        x = add()
    }

allocs := testing.AllocsPerRun(10, c)

return int(allocs)

func main() {
    println(stat(f)) // 1
    println(stat(g)) // 3
}
```

请注意，目前（Go 工具链 1.21 版本），这种优化仅适用于长度大于 32 的字节切片。如果我们通过声明将字符串 s 改为 32（`var s = []byte(31: 'x')`），那么函数 f 和 g 之间的性能差异将变得微不足道。请阅读下一节。

稍微冗长其实有一个缺点：它浪费了至少一个字节的内存。如果在编码时，我们知道某个操作数指定索引处的值始终为 s，就可以避免这个缺点。例如，下面的代码展示了为了避免浪费更多内存：

```go
func f() string {
    return "$" + string(s[1:]) + string(s)
}
```

请注意，未来的 Go 工具链版本可能不再支持这种优化。

### 如果操作的结果是字符串或字节切片，且结果的长度大于 32，则结果的字节元素将始终分配在堆上

事实上，上一节的示例使用了 32 字节的字节切片，其 True为了避免将字符串拼接的字节元素分配在栈上。两个函数唯一的区别在于涉及的字节切片和字符串的长度。

package main

```go
import "testing"

var str = "1234567890abcdef" // len(str) == 16
```

```go
func f() {
    x := str + str // 不逃逸
    y := []byte(x) // 不逃逸
    println(len(y), cap(y)) // 32
    z := string(y) // 不逃逸
    println(len(x), len(z)) // 32
}

func g() {
    x := str + str + "x" // 不逃逸
    y := []byte(x) // 不逃逸
    println(len(y), cap(y)) // 33
    z := string(y) // 不逃逸
    println(len(x), len(z)) // 33
}
```

```go
func stat(fn func()) int {
    allocs := testing.AllocsPerRun(10, fn)
    return int(allocs)
}

func main() {
    println(stat(f)) // 0
    println(stat(g)) // 3
}
```

在下面的基准测试代码中，`concat_split` 性能优于 `concat` 方式，但以前方法中的转换并没有产生堆分配。

package "testing"

```go
var s37 = [37]byte{'x'} // 修正了原文中可能的符号错误
var str = "1234567890abcdef" // len(str) == 16
```
*(注：原文后半部分存在大量重复和逻辑断裂，已根据语境进行了对齐化处理)*



```go
//go:noinline
func Concat_WithPlus(a, b, c, d string) string {
	return a + b + c + d
}

//go:noinline
func Concat_WithBytes(ss ...string) string {
	var n = 0
	for _, s := range ss {
		n += len(s)
	}
	var bs []byte
	if n > 64 {
		bs = make([]byte, 0, n) // 逃逸到堆
	} else {
		bs = make([]byte, 0, 64) // 不逃逸
	}
	for _, s := range ss {
		bs = append(bs, s...)
	}
	return string(bs)
}
```

```go
func Benchmark_Concat_WithPlus(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r = Concat_WithPlus(s, s, s, s)
	}
}
```

```go
func Benchmark_Concat_WithBytes(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r = Concat_With_Bytes(s, s, s)
	}
}
```

基准测试结果（当 s 的长度为 16 时）：

Benchmark_Concat_WithPlus-4   235.1 ns/op
Benchmark_Concat_WithBytes-4  208.3 ns/op

基准测试结果（当 s 的长度为 17 时）：

Benchmark_Concat_WithPlus-4   236.3 ns/op
Benchmark_Concat_WithBytes-4  357.5 ns/op

我们还可以在将切片转换为最终字符串之前，根据需要修改切片中的字节元素。这是与其他方法相比的另一个优势。

## 9.3 将字符串和字节切片合并为新的字节切片

有时，我们需要将一个字符串 (str) 合并到一个字节切片 (bs) 中生成一个新的字节切片。实现这一目标有两种方法。

方式 1（一行代码法）：

```go
var newByteSlice = append([]byte(str), bs...)
```

方式 2（详细描述法）：

```go
var newByteSlice = make([]byte, len(str) + len(bs))
copy(newByteSlice, str)
copy(newByteSlice[len(str):], bs)
```

通常，如果字符串的长度远大于字节切片，那么详细描述的方法性能更好。另一方面，如果切片的长度远大于字符串，则一行代码的方法性能更好。

遗憾的是（在 Go 工具链 1.21 版本中），没有一种极高性能的合并方法：

- 在一行代码的方法中，`[]byte(str)` 的转换会复制字符串的底层数据，这是不必要的。
- 在详细描述的方法中，`newByteSlice[len(str):]` 的元素会在 `make` 执行时被不必要地清零。

## Strings.Compare 函数现在的性能并不理想

目前（Go 1.21），`strings.Compare` 函数的实现是刻意以最高性能的方式实现的。换句话说，现在不建议在实践中使用它。相反，建议 Go 开发者使用比较运算符来比较字符串。在我诚实看来，这对于所有场景都是一个不可行的想法。毕竟，这两者都有各自最佳的使用场景。

以下代码展示了 `strings.Compare` 函数的当前实现。对于两个参数字符串不等但长度相同的情况，该实现效率低下。对于此类情况，执行了两次比较。

```go
package strings

func Compare(a, b string) int {
	if a == b {
		return 0
	}
	if a < b {
		return -1
	}
	return +1
}
```

作为对比，`bytes.Compare` 函数的实现通过调用内部函数 `bytealg.Compare` 被高度优化。

```go
package bytes

func Compare(a, b []byte) int {
	return bytealg.Compare(a, b)
}
```

希望未来的版本能够优化这个函数。

`strings.Compare` 函数预期用于三路字符串比较，如下代码所示：

```go
func foo(x, y string) {
	switch strings.Compare(x, y) {
	case -1:
		// 执行操作 1
	case 0:
		// 执行操作 2
	case 1:
		// 执行操作 3
	}
}
```

由于 `strings.Compare` 函数现在并不高效，一些人可能会使用比较运算符来完成这项工作。请注意，如果比较操作数的长度并不经常相等，那么我们不应该在默认分支中处理“相等”的情况。例如，在以下代码中，如果比较操作数的长度不相等，函数 `x == y` 会比 `x < y` 和 `x > y` 快得多。

```go
func f1(x, y string) {
	switch {
	case x == y: // .. 处理 1
	case x < y: // .. 处理 2
	default: // .. 处理 3
	}
}
```

```go
func f2(x, y string) {
	switch {
	case x < y: // .. 处理 2
	case x == y: // .. 处理 1
	default: // .. 处理 3
	}
}
```

```go
func f3(x, y string) {
	switch {
	case x < y: // .. 处理 2
	case x > y: // .. 处理 3
	default: // .. 处理 1
	}
}
```

另一个注意是，即使 `strings.Compare` 函数经过了高度优化，我们仍然不应该在使用 `==` 或 `!=` 运算符的比较中将其与 0 进行比较。具体来说，

```go
strings.Compare(x, y) == 0
strings.Compare(x, y) != 0
```

当 x 和 y 的长度不等时，它们的效率低于：

```go
x == y
x != y
```

## 9.5 尽可能避免分配

字符串和字节切片操作通常涉及内存分配。此类操作中分配的内存块都是短寿命的。为了程序运行高效，我们应该尽量减少短寿命内存块的分配。

在本节中将提供一些示例展示如何在某些情况下节省分配。

在以下示例中，函数 `f` 比 `g` 性能更好。原因是前者没有进行分配，而后者有。



```go
}

var s = string(make([]byte, 500))
var w io.Writer = DummyWriter{}
var bytesw = NewBytesWriter(DummyWriter{}, 512)

func Benchmark_BytesWriter(b *testing.B) {
	for i := 0; i < b.N; i++ {
		bytesw.WriteString(s)
	}
}

func Benchmark_GeneralWriter(b *testing.B) {
	for i := 0; i < b.N; i++ {
		w.Write([]byte(s))
	}
}
```

基准测试结果：

Benchmark_BytesWriter-4    21.03 ns/op    0 B/op    0 allocs/op
Benchmark_GeneralWriter-4  390.3 ns/op    512 B/op    1 allocs/op

从基准测试结果中我们可以发现，Bytes 方式比通用的 io.Writer 方式性能优越得多，因为前者没有分配内存（除了单次缓冲区分配外）。

请注意，标准包中有一个类型 `bufio.Writer`，它的作用类似于 `BytesWriter` 类型。通常，我们应该使用该类型。

# 第 10 章

# BCE (边界检查消除，Bound Check Eliminate)

Go 是一种内存安全的语言。在数组/切片/字符串元素索引和切片操作中，Go 运行时会检查涉及的索引是否越界。如果索引越界，将产生 panic 以防止无效索引造成危害。这被称为边界检查（bounds checking）。

边界检查让我们的代码运行更安全，但另一方面，它们也让我们的代码运行变慢。这是安全语言必须做的权衡。

从 Go v1.7 开始，标准 Go 编译器开始支持 BCE（边界检查消除）。BCE 可以避免一些不必要的检查，使得标准 Go 编译器能够生成更高效的程序。

以下将列出一些示例，展示 BCE 在什么情况下生效，在什么情况下不生效。

我们可以使用 `-d=ssa/check_bce` 编译器选项来显示哪些代码行需要边界检查。

## 10.1 示例 1

一个简单的示例：

```go
// example1.go
package main

func fla(s []struct{}, index int) {
	s = s[index] // line 5: Found IsInBounds
	s = s[index]
	s = s[index:]
	s = s[:index+1]
}

func flb(s []byte, index int) {
	s = s[index-1] = 'a' // line 12: Found IsInIndex
	s = s[:index]
}
```

```go
func fic(a [5]int) {
    _ = a[0]
    _ = a[4]
}
```

```go
func fid(s []int) {
    if len(s) > 2 {
        _, _, _ = s[0], s[1], s[2]
    }
}
```

```go
func fie(s []byte) {
    if len(s) >= 2 {
        r := len(s) % 2
        _ = s[r]
    }
}
```

```go
func main() {}
```

使用 `-d=ssa/check_bce` 编译器选项运行它：

$ go run -gcflags="-d=ssa/check_bce" example1.go
./example1.go:5:7 Found IsInBounds
./example1.go:12:3 Found IsBounds

输出显示，示例代码中只有两行需要边界检查。

注意，版本小于 1.19 的 Go 工具链无法移除 `fie` 函数中不必要的边界检查。
另外请注意，截至目前（Go 工具链 v1.21），如果泛型函数的操作涉及类型参数且泛型函数从未被实例化，官方标准编译器不会对泛型函数中的操作检查 BCE。例如，命令 `go run -gcflags="-d=ssa/check_bce bar.go` 将无任何报告。

```go
// bar.go
package bar
```

```go
func foo(s []E) {
    _ = s[0] // line 5
    _ = s[1] // line 6
    _ = s[2] // line 7
}
```

```go
// var _ = foo[bool]
```

然而，如果启用了变量声明，编译器将报告：

```
./bar.go:5:7 Found IsInBounds
./bar.go:6:7 Found IsInBounds
./bar.go:7:7 Found IsInBounds
./bar.go:4:6 Found IsInBounds
```

## 10.2 示例 2

以下所示切片元素索引和切片操作中的所有边界检查都被消除了。

```go
// example2.go
package main

func f2a(s []int) {
	for i := range s {
		_ = s[i]
		_ = s[:len(s)]
		_ = s[:i+1]
	}
}

func f2b(s []int) {
	for i := 0; i < len(s); i++ {
		_ = s[i]
		_ = s[:len(s)]
		_ = s[:i+1]
	}
}

func f2c(s []int) {
	for i := len(s) - 1; i >= 0; i-- {
		_ = s[i]
		_ = s[:len(s)]
		_ = s[:i+1]
	}
}

func f2d(s []int) {
	for i := len(s); i > 0; i-- {
		_ = s[i]
		_ = s[:len(s)]
		_ = s[:i+1]
	}
}

func f2e(s []int) {
	for i := 0; i < len(s); i++ {
		_ = s[i]
		_ = s[:len(s)]
		_ = s[:i+1]
	}
}

func main() {}
```

运行它，我们会发现没有任何输出。是的，官方 Go 编译器非常聪明，它发现上述示例中的边界检查是可以被移除的。

$ go run -gcflags="-ssa/check_bce" example2.go

仍然存在细微的缺陷。如果我们按照如下代码所示修改 `f2c` 和 `f2e` 函数，编译器（v1.21）将无法移除边界检查。

```go
// exampleb.go
package main

func f2c(s []int) {
	for i := len(s) - 1; i >= 0; i-- {
		_ = s[i]
		_ = s[:len(s)]
		_ = s[:i+1]
	}
}

func f2e(s []int) {
	for i := 0; i < len(s); i++ {
		_ = s[i]
		_ = s[:len(s)]
		_ = s[:i+1]
	}
}
```

运行它，你会得到如下：

$ go run -gcflags="-ssa/check_bce" example2.go
./example2.go:7:8 Found IsBounds
./example2.go:14:8 Found IsBounds

```

我们可以通过开启某些提示来消除这些边界检查。

## 10.3 示例 3

在以下示例中，如果 `s[3]` 尽可能早地进行，那么 `s[3]` 就可以被消除。

```go
// example3.go
package main

func f3(s []int) {
    if len(s) >= 2 {
        r := len(s) % 2
        _ = s[r]
    }
}

func f4(s []int) {
    if len(s) > 2 {
        _, _, _ = s[0], s[1], s[2]
    }
}

func main() {}
```

使用 `-d=ssa/check_bce` 编译器选项运行它：

$ go run -gcflags="-d=ssa/check_bce" example3.go
./example3.go:7:9 Found IsInBounds
./example3.go:12:9 Found IsInBounds
./example3.go:13:9 Found IsInBounds
./example3.go:14:9 Found IsInBounds

输出显示，示例代码中只有两行需要边界检查。

注意，版本小于 1.19 的 Go 工具链无法移除 `f3` 函数中不必要的边界检查。

## 10.4 示例 4

由于 `len(s) > 2`，`f4` 函数中的边界检查被消除了。

```go
// example4.go
package main

func f4(s []int) {
    if len(s) > 2 {
        _, _, _ = s[0], s[1], s[2]
    }
}
```

运行它：

$ go run -gcflags="-d=ssa/check_bce" example4.go
./example4.go:6:13 Found IsInBounds
./example4.go:6:13 Found IsInBounds
./example4.go:6:13 Found IsInBounds




请注意，截至 Go 工具链 v1.21.n，f4c 和 f4d 函数中使用的两个提示（hints）并不生效（但它们本应该是有效的）。

在这个示例中，通过在函数 `NumSameBytes_2` 中添加一个冗余的代码块，循环中所有的边界检查都被消除了。

```go
type T = string
```

```go
func NumSameBytes_1(x, y T) int {
    if len(x) > len(y) {
        x, y = y, x
    }
    for i := 0; i < len(x); i++ {
        if x[i] != y[i] {
            // Found IsInBounds
            return i
        }
    }
    return len(x)
}
```

```go
func NumSameBytes_2(x, y T) int {
    if len(x) > len(y) {
        x, y = y, x
    }

    // 一个成功的提示
    if len(x) > len(y) {
        panic("unreachable")
    }

    for i := 0; i < len(x); i++ {
        if x[i] != y[i] { // BCE已消除!
            return i
        }
    }
    return len(x)
}
```

当 T 为字符串类型或切片类型时，上述提示是有效的；而下述两个提示中的每一个都仅适用于一种情况（截至 Go 工具链 v1.21.n）。

```go
func NumSameBytes_3(x, y T) int {
    if len(x) > len(y) {
        x, y = y, x
    }

    y = y[:len(x)] // 一个提示，仅当 T 是 slice 时有效
    for i := 0; i < len(x); i++ {
        if x[i] != y[i] {
            return i
        }
    }
    return len(x)
}
```

```go
func NumSmarBytes(x, y T) int {
    if len(x) > len(y) {
        x, y = y, x
    }

    _ := y[:len(x)] // 一个提示，仅当 T 是 string 时有效
    for i := 0; i < len(x); i++ {
        if x[i] != y[i] {
            return i
        }
    }
    return len(x)
}
```

请注意，未来的 Go 标准编译器版本将变得更加智能，因此上述提示将不再需要。

# 10.6 编写对代码友的方式

在示例中，f7b 和 f7c 比 f7a 少了 3 次边界检查。

```go
func f7a(s []byte, i int) {
	s = s[i+3] // Found IsInBounds
	s = s[i+2] // Found IsInBounds
	s = s[i+1] // Found IsInBounds
	s = s[1] // Found IsInBounds
}
```

```go
func f7b(s []byte, i int) {
	s = s[i:i+4] // Found IsSliceInBounds
	s = s[3]
	s = s[2]
	s = s[1]
	s = s[0]
}
```

```go
func f7c(s []byte, i int) {
	s = s[i+4:i+4] // Found IsSliceInBounds
	s = s[3]
	s = s[2]
	s = s[1]
	s = s[0]
}
```

但是请注意，可能还有其他影响程序性能的因素。在我的机器上（Intel i5-4210U CPU @ 1.70GHz, Linux/amd64），上述 3 个函数中，f7b 函数实际上性能最低。

Benchmark_f7a-4 3861 ns/op
Benchmark_f7b-4 4223 ns/op
Benchmark_f7c-4 3477 ns/op

在实践中，鼓励使用三索引简洁形式 (f7c)。
在本示例中，基准测试结果显示：

- f8z 函数性能最高（符合预期）
- 但 f8y 函数的性能与 f8x 函数一样（出乎意）。

```go
func f8x(s []byte) {
  var n = len(s)
  s = s[:n]
  for i := 0; i <= n - 4; i += 4 {
    s = s[i+3] // Found IsInBounds
    s = s[i+2] // Found IsInBounds
    s = s[i+1] // Found IsInBounds
    s = s[i]
  }
}
```

```go
func f8y(s []byte) {
  for i := 0; i <= len(s) - 4; i += 4 {
    s2 := s[i]
    s2 := s[3] // Found IsInBounds
    s2 := s[2]
    s2 := s[1]
    s2 := s[0]
  }
}
```

```go
func f8z(s []byte) {
  for i := 0; len(s) >= 4; i += 4 {
    s = s[3]
    s = s[2]
    s = s[1]
    s = s[0]
  }
}
```

事实上，基准测试结果显示 f8y 函数的性能与 f8z 函数相当，而 f8y 函数的性能与 f8x 函数持平。因此在实践中鼓励使用三索引简洁形式。

```go
func f8y2(s []byte) {
  for i := 0; i < len(s) - 3; i += 4 {
    s2 := s[i:i+4] // Found IsInBounds
    s2 := s[3]
    s2 := s[2]
    s2 := s[1]
    s2 := s[0]
  }
}
```

```go
func f8y3(s []byte) {
  for i := 0; i < len(s) - 3; i += 4 {
    s2 := s[i+4:i+4] // Found IsInBounds
    s2 := s[3]
    s2 := s[2]
    s2 := s[1]
    s2 := s[0]
  }
}
```

在以下示例中，f9b 和 f9c 函数中没有边界检查，但在 f9a 函数中有。

```go
func f9a(n int) []int {
	buf := make([]int, n+1)
	k := 0
	for i := 0; i < n; i++ {
		buf[i] = k // Found IsInBounds
		k++
	}
	return buf
}
```

```go
func f9b(n int) []int {
	buf := make([]int, n+1)
	k := 0
	for i := 0; i < len(buf); i++ {
		buf[i] = k
		k++
	}
	return buf
}
```

```go
func f9c(n int) []int {
	buf := make([]int, n+1)
	k = 0
	for i := 0; i < n+1; i++ {
		buf[i] = k
		k++
	}
	return buf
}
```

在以下代码中，f0b 函数的性能远于 f0a。

```go
func f0a(x []byte) (r [4]byte) {
	for i := 0; i < 4; i++ {
		r[i] = x[i*4] // Found IsInBounds
		r[i] = x[i*4+1] // Found IsInBounds
		r[i] = x[i*4+2] // Found IsInBounds
		r[i] = x[i*4+3] // Found IsInBounds
	}
}
```

```go
func fB0(x []byte) (r [4]byte) {
	for i := 0; i < 4; i++ {
		r[i] = x[i*4:i+4][0] // Found IsInBounds
		r[i] = x[i*4:i+4][1]
		r[i] = x[i*4:i+4][2]
		r[i] = x[i*4:i+4][3]
	}
}
```

全局（包级）切片通常对 BCE 不友好，所以我们应该将它们赋值给局部切片。例如，在以下代码中，fa0 函数的边界检查比 fa1 和 fa2 多，函数 fa1() 和 fa2(s) 的性能都比 fa0() 好。

```go
var s = make([]int, 5)

func fa0() {
	for i := range s {
		s[i] = i // Found IsInBounds
	}
}
```

```go
func fa1() {
	s := s
	for i := range s {
		s[i] = i
	}
}
```

```go
func fa2(x []int) {
	for i := range x {
		x[i] = 1
	}
}
```

数组通常是更符合 BCE 的切片。在以下代码中，数组函数 (fb2 和 fc2) 不需要边界检查。

```go
var s = make([]int, 256)
var a = [256]int

func fb1() int {
	return s[100] // Found IsInBounds
}
```

```go
func fb2() int {
	return a[100]
}
```

```go
func fc1(n byte) int {
	return s[n] // Found IsInBounds
}
```

```go
func fc2(n byte) int {
	return a[n]
}
```

请注意，未来的 Go 标准编译器版本将变得更加智能，因此某些 BCE 不友好的代码可能会变为 BCE 友好。

# 10.7 当前官方 Go 编译器未能消除不必要的边界检查

截至 Go 工具链 v1.21.n，Go 标准编译器没有消除以下不必要的边界检查。

```go
func fb(s, x []byte) {
	n := copy(s, x)
	copy(s, y) // FoundSliceInBounds
	_ = s[n:] // FoundSliceInBounds
}
```

```go
func fc(s []byte) {
	const N = 6
	for i := 0; i < len(s)-(N-1); i += N {
		s[i+N-1] // FoundSliceInBounds
	}
}
```

```go
func fd(data []int, check func(int) bool) int {
	var k = 0
	for _, v := range data {
		if check(v) {
			data[k] = v // FoundInBounds
			k++
		}
	}
	return data[k] // FoundSliceInBounds
}
```

```go
func fe(s []int) {
	middle := len(s) / 2
	_ = s[middle] // FoundSliceInBounds
	_ = s[middle:] // FoundSliceInBounds
}
```




# 11.2 aMap[key]++ 比 aMap[key] = aMap[key] + 1 效率高

在语句 `aMap[key] = aMap[key] + 1` 中，key 被哈希了两次，但在语句 `aMap[key]++` 中，它只被哈希了一次。

同样地，`aMap[key] += value` 比 `aMap[key] = aMap[key] + value` 更高效。

可以通过以下基准测试代码证明这一点：

```go
package maps

import "testing"

var m = map[int]int()

func Benchmark_increment(b *testing.B) {
    for i := 0; i < b.N; i++ {
        m[99]++
    }
}

func Benchmark_plusone(b *testing.B) {
    for i := 0; i < b.N; i++ {
        m[99] += 1
    }
}

func Benchmark_addition(b *testing.B) {
    for i := 0; i < b.N; i++ {
        m[99] = m[99] + 1
    }
}
```

基准测试结果：

| Benchmark | Result |
| :--- | :--- |
| Benchmark_increment-4 | 11.31 ns/op |
| Benchmark_plusone-4 | 11.21 ns/op |
| Benchmark_addition-4 | 16.10 ns/op |

## 11.3 map 中的指针

如果 map 的 key 和元素类型不包含指针，那么在 GC 周期的扫描阶段，垃圾回收器将不会扫描 map 的项。这可以节省大量时间。这个提示也适用于 Go 中其他类型的容器，如切片（slices）、数组和通道（channels）。

## 11.4 使用字节数组代替短字符串作为 key

在内部，每个字符串都包含一个指针，该指针指向字符串的底层字节。因此，如果 map 的 key 或元素类型是字符串，那么在 GC 周期中需要扫描 map 的所有条目。

如果我们能让 map 条目使用的字符串值具有一个最大长度，且该最大长度较小，那么我们可以使用数组 `[N] byte` 来代替字符串类型（其中 N 是最大长度）。如果 map 中的条目数量很大，这样做将节省大量的垃圾回收扫描时间。

例如，在下面的代码中，`mapB` 的条目不包含指针，而 `map` 的（字符串）key 包含指针。垃圾回收器将在 GC 周期的扫描阶段跳过 `mapB`。

```go
var mapA = make(map[string]int, 1 << 16)
var mapB = make(map[[32]byte]int, 1 << 16)
```

请注意，官方标准编译器对 key 大为 4 或 8 字节进行了特殊优化。从节省 CPU 的角度，使用 `map[8]byte` 代替 `map[5]byte` 更好，使用 `map[32]byte` 代替 `map[16]byte` 更好。

## 11.5 降低 map 元素修改性能

在之前的“字符串和切片”章节中提到，出现在 map 元素检索表达式索引中的字节切片到字符串的转换不会分配内存，但在左值（L-value）map 元素索引表达式中的此类转换将会分配。

有时，我们可以通过降低在左值 map 元素索引表达式中使用此类转换的频率来提高程序性能。

在下面的示例中，B 方式（指针元素方式）性能优于 A 方式。原因是 B 方式 map 元素修改需要值。B 中的元素是指针，一旦创建，它们永远不会改变。

```go
package maps

import "testing"

var counterA = make(map[string]int)
var counterB = make(map[string]*int)
var key = make([]byte, 64)

func IncA(w []byte) {
	counterA[string(w)]++
}

func IncB(w []byte) {
	p := counterB[string(w)]
	if p == nil {
		p = new(int)
		counterB[string(w)] = p
	}
	*p++
}

func Benchmark_A(b *testing.B) {
	for i := 0; i < b.N; i++ {
		IncA(key[:])
	}
}

func Benchmark_B(b *testing.B) {
	for i := 0; i < b.N; i++ {
		IncB(key[:])
	}
}
```

基准测试结果：

| Benchmark | ns/op | B/op | allocs/op |
| :--- | :--- | :--- | :--- |
| Benchmark_A-4 | 11600 ns/op | 2336 B/op | 62 allocs/op |
| Benchmark_B-4 | 1543 ns/op | 0 B/op | 0 allocs/op |

虽然 B（指针元素）消耗少的 CPU，但它创建了许多指针，增加了 GC 周期中扫描的负担。但 B 方式更高效。

我们可以使用额外的计数器（切片）并将索引映射到表，以避免许多分配和创建许多指针，如下代码所示：

```go
var wordIndexes = make(map[string]int)
var wordCounters []int

```



# 第 12 章

## 通道 (Channels)

## 12.1 使用 channel 编程很有趣，但在某些情况下 channel 不是性能最好的方式

使用 channel 可能很有趣，但在某些场景下，它并不是最高效。在当前的官方标准 Go 编译器实现中（版本 1.21），channel 的速度比其他同步方式慢。可以通过下面的基准测试代码证明这一点。

```go
package channels

import (
  "sync"
  "sync/atomic"
  "testing"
)

var g int32

func Benchmark_NoSync(b *testing.B) {
  for i := 0; i < b.N; i++ {
    g++
  }
}

func Benchmark_Atomic(b *testing.B) {
  for i := 0; i < b.N; i++ {
    atomic.AddInt32(&g, 1)
  }
}

var m sync.Mutex

func Benchmark_Mutex(b *testing.B) {
  for i := 0; i < b.N; i++ {
    m.Lock()
    g++
    m.Unlock()
  }
}

var ch = make(chan struct{}, 1)
func Benchmark_Channel(b *testing.B) {
    for i := 0; i < b.N; i++ {
        ch <- struct{}
        g++
        <-ch
    }
}
```

基准测试结果：

| Benchmark_NoSync-4 | 2.246 ns/op |
| Benchmark_Atomic-4 | 7.112 ns/op |
| Benchmark_Mutex-4 | 14.25 ns/op |
| Benchmark_Channel-4 | 61.44 ns/op |

从结果可以发现，使用 channel 并发增加一个值的速度比其他同步方式慢得多。原子操作（atomic）方式是最好的。

如果可能，我们应该尽量避免在多个 goroutine 之间共享值，这样我们就不需要对所有值进行同步。

## 12.2 使用一个 channel 代替多个 channel 以避免使用 select 块

对于 select 代码块，分支（case）越多，该代码块消耗的 CPU 就越多。这可以通过下面的基准测试代码证明。

```go
package channels

import "testing"

var ch1 = make(chan struct{}, 1)
var ch2 = make(chan struct{}, 1)

func Benchmark_Select_OneCase(b *testing.B) {
    for i := 0; i < b.N; i++ {
        select {
        case ch1 <- struct{}:
            <-ch1
        }
    }
}

func Benchmark_Select_TwoCases(b *testing.B) {
    for i := 0; i < b.N; i++ {
        select {
        case ch1 <- struct{}:
            <-ch1
        case ch2 <- struct{}:
            <-ch2
        }
    }
}
```

基准测试结果：

Benchmark_Select_OneCase-4 58.90 ns/op
Benchmark_Select_TwoCases-4 115.3 ns/op

所以我们应该尽量限制 select 代码块中 case分支的数量。

官方标准 Go 编译器将只有一个 case 分支（且没有 default ）的 select 代码块视为简单的通用通道。

在某些情况下，我们通过合并多个 channel 来避免在执行多分支 select 代码块时产生性能损失。我们可以使用 interface 类型或 struct 作为 channel 的元素类型来实现此目标。如果 channel 元素类型是 interface，那么我们可以使用类型切换（type switch）来区分消息类型。如果 channel 元素类型是 struct，那么可以通过检查哪个字段被设置来区分消息类型。下面的基准测试代码显示了这些方式之间的性能差异。

```go
package channels

import "testing"

var vx int
var vy string

func Benchmark_TwoChannels(b *testing.B) {
	var x = make(chan int)
	var y = make(chan string)
	go func() { for { x <- i } }()
	go func() { for { y <- "hello" } }
	b.ResetTimer()
	for i := 0; i < b.N; i++ {
		select {
		case vx = <-x:
		case vy = <-y:
		}
	}
}

func Benchmark_OneChannel_Interface(b *testing.B) {
	var x = make(chan interface{})
	go func() { for { x <- i } }()
	go func() { for { x <- "hello" } }
	b.ResetTimer()
	for i := 0; i < b.N; i++ {
		select {
		case v = <-x:
			switch v := v.(type) {
				case int: vx = v
				case string: vy = v
			}
		}
	}
}

func Benchmark_OneChannel_Struct(b *testing.B) {
	type T struct { x int; y string }
	var x = make(chan T)
	go func() { for { x <- T{x: i} } }()
	go func() { for { x <- T{y: "hello"} } }
	b.ResetTimer()
	for i := 0; i < b.N; i++ {
		select {
		case v := <-x:
			if v.y != "" {
				vy = v.y
			} else {
				vx = v.x
			}
		}
	}
}
```

*(注：原文代码 Benchmark_OneChannel_Struct 逻辑不完整，此处已根据逻辑补全翻译上下文)*

基准测试结果：

| Benchmark_TwoChannels-4 | 1295 ns/op |
| Benchmark_OneChannel_Interface-4 | 940 ns/op |
| Benchmark_OneChannel_Struct-4 | 851 ns/op |

从结果可以发现，合并多个 channel 的性能优于执行多分支 select 代码块。

# 第 13 章

## 函数

## 13.1 函数内联 (Inlining)

官方标准 Go 编译器会自动内联一些小函数以提高速度。请看这个例子：

```go
// inline.go
package inline

func bar(a int) int {
	return a + 1
}

func foo(x, y int) int {
	return bar(x) + y
}
```

使用 -m 选项编译它：

```bash
$ go build -gcflags="-m" inline.go
# command-line arguments
./inline.go:4:6: can inline bar
./inline.go:8:6: inlining call to bar
./inline.go:9:6: inlining call to bar
```

从输出中我们知道，编译器认为 bar 函数是可以内联的，foo 函数将被扁平为：

```go
func foo(x, y int) int {
	var a = x + 1
	var b = a + y
	return b
}
```

内联后，原本在调用 bar 函数时的某些栈操作被节省，从而提高了性能。内联会增大 Go 二进制文件的大小，所以编译器只内联小函数。

### 13.1.1 哪些函数是可以内联的？

函数需要多小？函数内的每条语句都有内联成本。如果函数内所有语句的总成本不超过编译器设置的阈值，那么编译器认为该函数可以内联。

我们可以使用 -m 选项显示为什么某些函数可以内联而另一些不能。仍然使用这个例子：

```bash
$ go build -gcflags="-m" inline.go
# command-line arguments
./inline.go:4:6: can inline bar with cost 14
./inline.go:8:6: cannot inline foo: cost 96 exceeds budget 80
```

从输出中我们可以得知，该函数无法内联，因为它的内联成本为 96，超过了阈值（未启用配置引导优化时为80）。递归函数永远不会内联。例如，下面的代码中的 sumSquares 函数是不可内联的：

```go
package main

func sumSquares(n uint) uint {
	if n == 0 {
		return 0
	}
	return sumSquares(n-1) + n*n
}

func main() {
	println(sumSquares(5))
}
```




```go
func g1(s []int) int {
    recover()
    return cap(s) - len(s)
}
```

```go
func f2(b bool) string {
    if b {
        return "y"
    }
    return "N"
}
```

```go
func f3(c chan int) int {
    return -c
}
```

```go
func f4(a, b int) int {
    return a - b*b
}
```

```go
func g4(a, b int) int {
    defer func() {}
    return a - b*b
}
```

```go
func f5(a, b int) int {
    return a - b*b
}
```

```go
func g5(a, b int) int {
    go func() {}
    return a - b*b
}
```

官方 Go 编译器可能会随版本更改内联策略、内联成本和语句成本。例如，在上面的示例中，*在 v1.16 之前*，编译器认为代码中的函数 g5 不可内联的（但从 v1.16 开始，它已经变得可内联了）。*在 v1.18 之前*，编译器认为代码中的函数 g7 不可内联的（但从 v1.18 开始，它已经变得可内联了）。*在 v1.19 之前*，编译器认为代码中的函数 g3 不可内联的（但从 v1.19 开始，它已经变得可内联了）。*在 v1.20 之前*，编译器认为代码中的函数 g2 不可内联的（但从 v1.20 开始，它已经可以内联了）。

```go
func g6(s []int) {
    for i := 0; i < len(s); i++ {
        s[i] = i
    }
}
```

```go
func g7(s []int) int {
    for i := range s {
        s[i] = i
    }
}
```

```go
func g3(c chan int) int {
	select {
	case r := <-c:
		return r
	}
}
```

```go
func g2(b bool) string {
	type struct {
		int int
	}
	if b {
		return "y"
	}
	return "N"
}
```

另一个例子是下面代码中的 `plusSquare` 函数自 Go v1.17 起是仅内联的。在 v1.17 之前，包含闭包的函数被认为是内联的。

package main

```go
func plusSquare(n int) int {
	f := func(x int) int { return x*x }
	return f(n) + 2*n + 1
}
```

## 13.1.2 如果值在编译时难以确定，则对值的调用不可内联

例如，在以下代码中，包级变量 `addFunc` 是不可内联的，编译器不会在编译时确认包级变量的值。然而，它会尝试在可能的情况下在编译时确认局部变量的值。对本地 `addFunc` 函数（变量）的调用将被内联。

package main

```go
func add(a, b int) int {
	return a + b
}
```

```go
var addFunc = add
func main() {
	println(addFunc(11, 22)) // not inlined
	var addFunc = add
	println(addFunc(11, 22)) // inlined
}
```

## 13.1.3 go:ninline 注释指令

有时，出于学习和测试目的，我们可能希望函数调用被内联，或者让函数的调用者变得可内联（见下示例），等。除了我们介绍的几种方法外，我们还可以使用 `go:ninline` 注释指令来实现这一目标。编译器不会内联以下代码中的 `add` 函数，即使 `add` 函数非常简单。

```go
package main
//go:ninline
func add(x, y int) int {
    return x + y
}

func main() {
    println(add(1, 2))
}
```

但是，请注意，这不是避免内联的正规方法。它主要用于标准包和 Go 工具链的开发。但我个人认为，这个指令会被长期支持。

## 13.1.4 以高内联成本的方式编写代码

通常，我们应该尝试让更多的函数成为可内联的，以获得更好的执行性能。

除了上述规则，我们应该知道不同的代码实现方式可能会有不同的内联成本，即使代码差异非常细微。我们可以利用这一事实尝试不同的实现方式，以找出哪种方式的内联成本最低。

让我们看看上面的第一个例子。

```go
//inline2.go
package inline

func bar(a, b int) int {
    return a*a - b*b + 2 * (a - b)
}

func foo(x, y int) int { // line 8
    var a = bar(x, y)
    var b = bar(y, x)
    var c = bar(a, b)
    var d = bar(b, c)
    return c + d
}

func foo2(x, y int) int { // line 16
    var a = x*x - 2 * (x - y)
    var b = y*y - 2 * (y - x)
    var c = a*a - 2 * (a - b)
    var d = b*b - 2 * (b - a)
    return c + d
}
```

使用 `-m` 选项编译：

```bash
$ go build -m inline2.go
./inline2.go:8:6: cannot inline foo: too complex: cost 96
./inline2.go:16:6: can inline foo2 with cost 76 as:
```

从输出得知 `foo` 函数不可内联，但它的手动版本（`foo2` 函数）是可以内联的，因为编译器计算 `foo2` 函数的成本为76，没有超过阈值（80）。是的，手动内联通常比自动内联成本低。

另一个例子：

```go
// sum.go
package inline

func sum(s []int) int { // line 4
	r := 0
	for i := 0; i < len(s); i++ {
		r += s[i]
	}
	return r
}

func sum2(s []int) int { // line 12
	r := 0
	for i := range s {
		r += s[i]
	}
	return r
}

func sum3(s []int) int { // line 19
	r := 0
	for _, v := range s {
		r += v
	}
	return r
}
```
（注：`sum` 函数的 OCR 损坏了，根据常见的 Go 模式）编译器（v1.21）认为 `sum` 函数的内联成本是不同的，可以通过以下输出验证：

```bash
$ go build -gcflags="-m" sum.go
# command-line-arguments
./sum.go:4:6: can inline sum with cost 25 as: ...
./sum.go:12:6: can inline sum2 with cost 20 as: ...
./sum.go:19:6: can inline sum3 with cost 19 as: ...
```

从上面的例子可以看出：
- 局部变量会导致内联成本。
- 裸返回语句（bare return statements）比非裸返回语句成本低。

（请注意，内联成本并不意味着代码执行成本。事实上，官方编译器为上述 `sum` 函数生成了相同的汇编指令。）

从 v1.18 开始，官方 Go 编译器认为 `for range` 循环的内联成本小于 `for` 循环。例如，编译器认为 `sum4` 函数的内联成本为 11，远小于裸循环（bare loops）。

```go
func sum4(s []int) (r int) {
    for i := range s {
        r += s[i]
    }
    return r
}
```

第三个例子：

```go
// branches.go
package inline

func foo(a, b, c, d bool) int { // line 4
    if a { return 0 }
    if b { return 0 }
    if c { return 0 }
    if d { return 0 }
    return 1
}

func foo2(a, b, c, d bool) (r int) { // line 12
    if a { return 0 }
    if b { return 0 }
    if c { return 0 }
    if d { return 0 }
    return 1
}

func bar(a, b, c, d bool) int { // line 20
    if a || b || c || d {
        return 0
    }
    return 1
}

func bar2(a, b, c, d bool) (r int) { // line 27
    if a || b || c || d {
        return 0
    }
    return 1
}
```

以下输出显示较少的分会导致更低的内联成本。

```bash
$ go build -gcflags="-m -m" branches.go
# command-line-arguments
./branches.go:4:6: can inline foo with cost 18 as: ...
./branches.go:12:6: can inline foo2 with cost 14 as: ...
./branches.go:20:6: can inline bar with cost 12 as: ...
./branches.go:27:6: can inline bar2 with cost 11 as: ...
```

第四个例子：

```go
// funcvalue.go
package inline

func add(x, y int) int {
    return x+y
}

func sub(x, y int) int {
    return x-y
}

func op1(op string, a, b int) int { // line 12
    switch op {
        default: panic("unknown op " + op)
        case "+": return add(a, b)
        case "-": return sub(a, b)
    }
}

func op2(op string, a, b int) int { // line 20
    var f func(int, int) int
    switch op {
        default: panic("unknown op " + op)
        case "+": f = add
        case "-": f = sub
    }
    return f(a, b)
}
```

以下输出显示 `op2` 函数的行成本远高于 `op1` 函数：

```bash
$ go build -gcflags="-m -m" funcvalue.go
...
./aaa.go:12:6: can inline op1 with cost 30 as: ...
./aaa.go:20:6: cannot inline op2: ... cost 84 exceeds budget
...
```

标准 Go 编译器在未来的版本中可能会改进，以便本节所示示例中计算出的成本更加一致。

## 13.1.5 让热路径可内联

如果一个函数不可内联但包含一个起始热路径，为了让该热路径可内联，我们可以将冷路径部分封装到另一个函数中。


例如，以下代码中的 `concat` 函数是不可内联的，因为它的内联成本为 85（大于阈值 80）。

```go
func concat(bss ...byte) byte {
    n := len(bss)
    if n == 0 {
        return nil
    } else if n == 1 {
        return bss[0]
    } else if n == 2 {
        return append(bss[0], bss[1]...)
    }

    var m = 0
    for i := 0; i < len(bss); i++ {
        m += len(bss[i])
    }

    var r = make([]byte, 0, m)
    for i := 0; i < len(bss); i++ {
        r = append(r, bss[i]...)
    }
    return r
}
```

如果在实践中，绝大多数情况都是拼接两个字节，那么我们可以将上面的代码重写如下所示。`concat` 函数的内联成本变为 74，因此现在它是可内联的。这意味着热路径将被内联。

```go
func concat(bss ...byte) byte {
    if len(bss) == 2 {
        return append(bss[0], bss[1]...)
    }

    return concatSlow(bss...)
}
```

```go
//go:noinline
func concatSlow(bss ...byte) byte {
    if len(bss) == 0 {
        return nil
    } else if len(bss) == 1 {
        return bss[0]
    }

    var m = 0
    for i := 0; i < len(bss); i++ {
        m += len(bss[i])
    }

    var r = make([]byte, 0, m)
    for i := 0; i < len(bss); i++ {
        r = append(r, bss[i]...)
    }
    return r
}
```

如果封装代码部分的函数内联成本没有超过内联阈值，那么我们应该使用上述引入的避免内联的方法来防止函数变为可内联。否则，重写后的 `concat` 函数仍然不可内联，因为封装部分在重写后的 `concatSlow` 函数之前会被自动展平。这就是为什么使用 `go:noninline` 注释指令的原因。

请注意，目前（Go 工具链 v1.21.n），非内联函数调用的内联成本为 59。这意味着如果函数包含 2 个及以上的非内联调用，该函数是不可内联的。

另外请注意，自 Go 工具链 v1.11b 起，如果我们将原始 `concat` 函数中的两个 `for` 循环替换为两个 `range` 循环，那么原始函数将准备好可以内联。在这里，为了演示，我们使用了两个 `for` 循环。

## 13.1.6 手动内联性能通常优于自动内联

一个示例：

```go
package functions

import "testing"

const N = 100

// 此函数是可内联的。
func Slice2Array(b []byte) [N]byte {
	return *(*[N]byte)(b)
}

//==================================
```

```go
var buf = make([]byte, 8192)
var r [128]byte

func Benchmark_ManualInline(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r[i&127] = *(*[N]byte)(buf)
	}
}

func Benchmark_AutoInline(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r[i&127] = Slice2Array(buf) // inlined
	}
}
```

基测试结果：
Benchmark_ManualInline-4 5.134 ns/op
Benchmark_AutoInline-4 11.49 ns/op

从结果可以发现，手动内联的性能优于自动内联，至少在这个特定情况下如此。

官方标准 Go 编译器将在未来的版本中得到改进，使自动内联变得更加智能。

## 13.1.7 内联可能对性能产生负面影响

由于某些编译器实现缺陷，有时内联调用的性能可能不如非内联调用。这里有一个示例：

```go
package functions

import "testing"

type T [8]byte

var r, s T

//noinline
func not_inline_able(x1, y1 *T) {
	x, y := x1[:], y1[:]
	for k := 0; k < len(T); k++ {
		x[k] = y[k]
	}
}

func inline_able(x1, y1 *T) {
	x, y := x1[:], y1[:]
	for k := 0; k < len(T); k++ {
		x[k] = y[k]
	}
}

func Benchmark_not_inlined(b *testing.B) {
	for i := 0; i < b.N; i++ {
		not_inline_able(&r, &s)
	}
}

func Benchmark_auto_inlined(b *testing.B) {
	for i := 0; i < b.N; i++ {
		inline_able(&r, &s)
	}
}

func Benchmark_manual_inlined(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r[i&127] = *(*[N]byte)(buf)
	}
}
// (注：此处原文逻辑似乎有些错乱，已根据上下文调整翻译)
// 修正翻译逻辑：
// 如果封装代码部分的函数内联成本未超过内联阈值，则我们应该使用上述引入的避免内联的方法来防止函数变为可内联。否则，重写的 concat 函数仍然不可内联，因为封装部分在重写后的 concatSlow 函数之前会被自动展平。这就是为什么使用 go:noninline 注释指令的原因。

// 请注意，目前（Go 工具链 v1.21.n），非内联函数调用的内联成本为 59。这意味着如果函数包含 2 个及以上的非内联调用，该函数是不可内联的。

// 另外请注意，自 Go 工具链 v1.11b 起，如果我们将原始 concat 函数中的两个 for 循环替换为两个 range 循环，那么原始函数将准备好可以内联。在这里，为了演示，我们使用了两个 for 循环。

## 13.1.6 手动内联性能通常优于自动内联

// 一个示例：

```go
package functions

import "testing"

const N = 100

// 此函数是可内联的。
func Slice2Array(b []byte) [N]byte {
	return *(*[N]byte)(b)
}

//==================================
```

```go
var buf = make([]byte, 8192)
var r [128]byte

func Benchmark_ManualInline(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r[i&127] = *(*[N]byte)(buf)
	}
}

func Benchmark_AutoInline(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r[i&127] = Slice2Array(buf) // inlined
	}
}
```

基测试结果：
Benchmark_ManualInline-4 5.134 ns/op
Benchmark_AutoInline-4 11.49 ns/op

从结果可以发现，手动内联的性能优于自动内联，至少在这个特定情况下如此。

官方标准 Go 编译器将在未来的版本中得到改进，使自动内联变得更加智能。

## 13.1.7 内联可能对性能产生负面影响

由于某些编译器实现缺陷，有时内联调用的性能可能不如非内联调用。这里有一个示例：

```go
package functions

import "testing"

type T [8]byte

var r, s T

//noinline
func not_inline_able(x1, y1 *T) {
	x, y := x1[:], y1[:]
	for k := 0; k < len(T); k++ {
		x[k] = y[k]
	}
}

func inline_able(x1, y1 *T) {
	x, y := x1[:], y1[:]
	for k := 0; k < len(T); k++ {
		x[k] = y[k]
	}
}

func Benchmark_not_inlined(b *testing.B) {
	for i := 0; i < b.N; i++ {
		not_inline_able(&r, &s)
	}
}

func Benchmark_auto_inlined(b *testing.B) {
	for i := 0; i < b.N; i++ {
		inline_able(&r, &s)
	}
}

// (由于原文提供的文本片段存在大量重复和混乱，翻译已根据语意进行对齐处理)




## 13.4 尝试将中间计算结果存储在局部变量中

使用局部变量存储中间计算结果可以让编译器有机会进行更好的优化，从而获得更好的性能。例如下：

```go
package functions

import "testing"

var sum int

func f(s []int) {
    for _, v := range s {
        sum += v
    }
}

func g(s []int) {
    var n = 0
    for _, v := range s {
        n += v
    }
    sum = n
}

var s = make([]int, 1024)

func Benchmark_f(b *testing.B) {
    for i := 0; i < b.N; i++ {
        f(s)
    }
}
func Benchmark_g(b *testing.B) {
    for i := 0; i < b.N; i++ {
        g(s)
    }
}
```

基准测试结果：

```
Benchmark_f-4 3293 ns/op
Benchmark_g-4 654.1 ns/op
```

## 13.5 避免在循环中使用 defer 调用

从 v1.14 开始，Go 官方编译器已经专门优化了开放延迟调用（即不在循环内的延迟调用）。但循环内延迟调用的代价仍然很高。可以通过以下示例证明：

```go
package functions

import "testing"

var n int
func inc() {
  n++
}

func f(n int) {
  for i := 0; i < n; i++ {
    defer inc()
    inc()
  }
}

func g(n int) {
  for i := 0; i < n; i++ {
    func() {
      defer inc()
      inc()
    }()
  }
}

func Benchmark_f(b *testing.B) {
  n = 0
  for i := 0; i < b.N; i++ {
    f(100)
  }
}

func Benchmark_g(b *testing.B) {
  n = 0
  for i := 0; i < b.N; i++ {
    g(100)
  }
}
```

基准测试结果：

| Benchmark_f-4 | 33232 ns/op 2 B/op 0 allocs/op |
| Benchmark_g-4 | 5237 ns/op 0 B/op 0 allocs/op |

函数 g 性能远高于函数 f 的原因是，不直接在循环中的延迟调用被 Go 官方标准编译器进行了专门优化。函数 g 将循环中的代码封装在一个匿名函数中，使得延迟调用没有直接包含在循环内。

请注意，这两个函数在逻辑上是不等价。如果这是一个问题，则不应该使用匿名函数技巧。

## 13.6 如果追求极高性能，请避免使用 defer 调用

即使 Go 官方标准编译器已经专门优化了开放延迟调用，与非延迟调用相比，这种延迟调用仍有额外的额外开销。如上所述，目前（Go 工具链 v1.21n），包含延迟调用的函数是不可内联。因此，如果某段代码需要极高的性能，请尝试避免在该段代码中使用 defer 调用。

## 13.7 函数调的参数在调用时始终会被求值

例如，以下程序打印 1，这意味着即使参数 `s` 在运行时没有在 `debugPrint` 函数中使用，字符串拼接表达式 `+ w` 仍然被求值。

```go
package main

import (
    "log"
    "testing"
)

var debugOn = false

func debugPrint(s string) {
    if debugOn {
        log.Println(s)
    }
}

func main() {
    stat := func(f func()) int {
        allocs := testing.AllocsPerRun(10, f)
        return int(allocs)
    }

    var h, w = "hello ", "world!"

    var n = stat(func() {
        debugPrint(h + w)
    })

    println(n) // 0
}
```

避免不参数的方法是将 `debugOn` 改为常量。但某些程序可能需要动态更改值，所以这种方法不可行。我们可以让 `debugPrint` 函数返回 bool 并在布尔运算中调用该函数，如下代码所示：

```go
package main

import (
  "log"
  "testing"
)

var debugOn = false

func debugPrint(s string) bool {
    if debugOn {
        log.Println(s)
        return true
    }
    return false
}

func main() {
    stat := func(f func()) int {
        // ...
    }
    // ...
}
```

在上面的代码中，分析显示通过利用栈和逃逸分析引入的技巧，我们可以将函数 `f` 重写如下所示，以防止参数 `x` 逃逸到堆。

```go
package main

import (
    "strconv"
    "testing"
)

var sink interface{}

//go:noinline
func escape(x interface{}) {
    sink = x
}

func main() {
    var a = f(10)
    println(a)
}

func f(x int) string {
    return strconv.Itoa(x)
}

func g(x int) string {
    return strconv.Itoa(x)
}
```

## 13.8 接口装箱与逃逸

## 14: 接口

接口值可以被视为对非接口值的装箱。nil 接口值不任何内容。相反，当非接口值赋值给接口值时，通常该非接口值会被装箱，其地址存储在接口值中。在 Go 官方实现中，通常装箱一个值的代价与值的大小成正比。

```go
package interfaces

import "testing"

var r interface{}

var n16 int16 = 12345
func Benchmark_BoxInt16(b *testing.B) {
	for i := 0; i < b.N; i++ { r = n16 }
}

var n32 int32 = 12345
func Benchmark_BoxInt32(b *testing.B) {
	for i := 0; i < b.N; i++ { r = n32 }
}

var n64 int64 = 12345
func Benchmark_BoxInt64(b *testing.B) {
	for i := 0; i < b.N; i++ { r = n64 }
}

var f64 float64 = 1.2345
func Benchmark_BoxFloat64(b *testing.B) {
	for i := 0; i < b.N; i++ { r = f64 }
}

var s = "Go"
func Benchmark_BoxString(b *testing.B) {
	for i := 0; i < b.N; i++ { r = s }
}

var x = []int{1, 2, 3}
func Benchmark_BoxSlice(b *testing.B) {
	for i := 0; i < b.N; i++ { r = x }
}

var a = [100]int{}
func Benchmark_BoxArray(b *testing.B) {
	for i := 0; i < b.N; i++ { r = a }
}
```

基准测试结果：

| Benchmark_BoxInt16-4 | 16.62 ns/op 2 B/op 1 alloc/op |
| Benchmark_BoxInt32-4 | 16.36 ns/op 4 B/op 1 alloc/op |
| Benchmark_BoxInt64-4 | 19.51 ns/op 8 B/op 1 alloc/op |
| Benchmark_BoxFloat64-4 | 20.05 ns/op 8 B/op 1 alloc/op |
| Benchmark_BoxString-4 | 56.57 ns/op 16 B/op 1 alloc/op |
| Benchmark_BoxSlice-4 | 45.5 ns/op 24 B/op 1 alloc/op |
| Benchmark_BoxArray-4 | 247.2 ns/op 196 B/op 1 alloc/op |




Benchmark_BoxFunction-4 1.126 ns/op 0 B/op 0 allocs/op

从上述结果，我们得到指针值的装箱（boxing）非常快，且不会产生内存分配。这解释了为什么如果我们让方法实现接口方法，为 *T* 声明方法通常比为 T 更高效。

通过使用这种优化，在某些情况下，我们使用查表来将小集合中的某些非指针值转换为指针值。例如，在下面的代码中，我们使用数组将 `uint16` 值转换为指针，以获得得低的装箱成本。

```go
package interfaces
```

```go
var values [65536]uint16

func init() {
    for i := range values {
        values[i] = uint16(i)
    }
}
```

```go
func Benchmark_Box_Normal(b *testing.B) {
    for i := 0; i < b.N; i++ {
        r = uint16(i)
    }
}
```

```go
func Benchmark_Box_Lookup(b *testing.B) {
    for i := 0; i < b.N; i++ {
        r = &values[uint16(i)]
    }
}
```

```go
var x interface{uint16(10000)}byte
var n uint16
```

```go
func Benchmark_Unbox_Normal(b *testing.B) {
    for i := 0; i < b.N; i++ {
        n = x.(uint16)
    }
}
```

```go
func Benchmark_Unbox_Lookup(b *testing.B) {
    for i := 0; i < b.N; i++ {
        n = +y.(*uint16)
    }
}
```

基准测试结果：

Benchmark_Box_Normal-4 22.69 ns/op 0 B/op 0 allocs/op
Benchmark_Box_Lookup-4 1.137 ns/op 0 B/op 0 allocs/op
Benchmark_Unbox_Normal-4 0.7535 ns/op 0 B/op 0 allocs/op
Benchmark_Unbox_Lookup-4 0.7510 ns/op 0 B/op 0 allocs/op

（请注意，结果显示 Box_Normal 函数测量为零分配，这并不是事实。该值为 0.99，被截断为零。原因是位于 [0, 255] 范围内的值进行装箱不会分配，这一点在下文中提到。）

该优化也应用于常量值的装箱：

```go
package interfaces

import "testing"

var r interface()

const N int64 = 12345
func Benchmark_BoxInt64(b *testing.B) {
    for i := 0; i < b.N; i++ { r = N }
}
```

```go
const F float64 = 1.2345
func Benchmark_BoxFloat64(b *testing.B) {
    for i := 0; i < b.N; i++ { r = F }
}
```

```go
const S = "Go"
func Benchmark_BoxConstString(b *testing.B) {
    for i := 0; i < b.N; i++ { r = S }
}
```

基准测试结果：

Benchmark_BoxInt64-4 1.136 ns/op 0 B/op 0 allocs/op
Benchmark_BoxFloat64-4 1.196 ns/op 0 B/op 0 allocs/op
Benchmark_BoxConstString-4 1.211 ns/op 0 B/op 0 allocs/op

事实上，Go 官方编译器也对值的装箱做了类似的优化：

- 任意整数类型的非常量小整数值（范围在 [0, 255] 之间），8 位整数除外（8 位已在上面提到的第一个优化中涵盖）。
- 浮点类型/切片类型的非常量零值。

装箱非常量小整数值：

```go
package interfaces

import "testing"

var r interface()

func Benchmark_BoxSmallInt16(b *testing.B) {
    for i := 0; i < b.N; i++ { r = int16(i&255) }
}
```

```go
func Benchmark_BoxSmallInt32(b *testing.B) {
  for i := 0; i < b.N; i++ { r = int32(i&255) }
}

func Benchmark_BoxSmallInt64(b *testing.B) {
  for i := 0; i < b.N; i++ { r = int64(i&255) }
}
```

基准测试结果：

| Benchmark_BoxSmallInt16-4 | 3.409 ns/op | 0 B/op | 0 allocs/op |
| Benchmark_BoxSmallInt32-4 | 3.379 ns/op | 0 B/op | 0 allocs/op |
| Benchmark_BoxSmallInt64-4 | 3.404 ns/op | 0 B/op | 0 allocs/op |

装箱零指针、字符串和切片值：

```go
package interfaces

import "testing"

var r interface{}

var f32 float32 = 0
func Benchmark_BoxZeroFloat32(b *testing.B) {
	for i := 0; i < b.N; i++ { r = f32 }
}

var f64 float64 = 0
func Benchmark_BoxZeroFloat64(b *testing.B) {
	for i := 0; i < b.N; i++ { r = f64 }
}

var str = ""
func Benchmark_BoxBlankString(b *testing.B) {
	for i := 0; i < b.N; i++ { r = str }
}

var slc []int
func Benchmark_BoxNilSlice(b *testing.B) {
	for i := 0; i < b.N; i++ { r = slc }
}
```

基准测试结果：

| Benchmark_BoxZeroFloat32-4 | 3.386 ns/op | 0 B/op | 0 allocs/op |
| Benchmark_BoxZeroFloat64-4 | 3.385 ns/op | 0 B/op | 0 allocs/op |
| Benchmark_BoxBlankString-4 | 3.427 ns/op | 0 B/op | 0 allocs/op |
| Benchmark_BoxNilSlice-4 | 3.930 ns/op | 0 B/op | 0 allocs/op |

装箱只有一个字段（元素）的结构体（数组）值，如果该字段是小整数或零布尔/数值/字符串/切片/指针值，其成本与装箱该字段（元素）相同（在 v1.19 版本之前，8 位整数除外）。

```go
package interfaces

import "testing"

var r interface{}

func Benchmark_SmallInt32Field(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r = struct{n int32}{255}
	}
}

func Benchmark_ZeroFloatElement(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r = [1]float64{0}
	}
}

func Benchmark_BlankStringField(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r = struct{n string}{""}
	}
}

func Benchmark_NilSliceField(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r = struct{n []int}{nil}
	}
}

func Benchmark_NilFunctionElement(b *testing.B) {
	for i := 0; i < b.N; i++ {
		r = [1]func(){}{}
	}
}
```

基准测试结果：

| Benchmark | ns/op | B/op | allocs/op |
|---|---|---|---|
| Benchmark_SmallInt32Field-4 | 3.387 ns/op | 0 B/op | 0 allocs/op |
| Benchmark_ZeroFloat64Element-4 | 3.584 ns/op | 0 B/op | 0 allocs/op |
| Benchmark_BlankStringField-4 | 3.528 ns/op | 0 B/op | 0 allocs/op |
| Benchmark_NilSliceField-4 | 3.931 ns/op | 0 B/op | 0 allocs/op |
| Benchmark_NilFunctionElement-4 | 1.134 ns/op | 0 B/op | 0 allocs/op |

基于基准测试结果的总结（截至 Go v1.21）：

- 指针值的装箱比非指针值的装箱快得多。
- map、通道和函数的装箱与指针值一样快。
- 常量值的装箱与指针值一样快。
- 固定大小值的装箱与指针值一样快。
- 任意整数类型（8 位除外）的非常量小值（[0, 255] 之间）装箱比指针值慢约 3 倍。
- 浮点/字符串/切片零值的装箱比指针值慢约 3 倍。

- 非常量小整数值（超出 [0, 255] 范围）或非零浮点值的装箱比指针值慢约 20 倍或更多。
- 非空切片或非空非常量字符串值的装箱比指针值慢约 50 倍或更多。
- 只有一个字段（元素）的结构体（数组）的小整数或零布尔/数值/字符串/切片/指针值与装箱该字段（元素）一样快。

因此，如果在代码执行的热点路径上进行了值装箱分配，建议装箱成本较小的值。

## 14.2 尝试通过将接口赋值给接口来消除内存分配

有时，我们需要在接口值中装箱非接口值。有两种方法实现此目标：

1. 在第一个接口值中装箱非接口值，然后在第二个中装箱非接口值。
2. 在第一个接口值中装箱非接口值，然后将第一个赋值给第二个。

如果装箱值需要分配，哪种性能更优？毫无疑问，可以通过下面的基准测试代码证明。

```go
package main

import "testing"

var v = 9999999
var x, y interface{}

func Benchmark_Box(b *testing.B) {
	for i := 0; i < b.N; i++ {
		x = v // 需要一次分配
		y = v // 需要一次分配
	}
}

func Benchmark_BoxAssign(b *testing.B) {
	for i := 0; i < b.N; i++ {
		x = v // 需要一次分配
		y = v // 无分配
	}
}
```

基准测试结果：

| Benchmark_Box-4 130.5 ns/op 16 B/op 2 allocs/op |
| Benchmark_BoxAssign-4 68.31 ns/op 8 B/op 1 allocs/op |

第二种方法节省了一次分配，因此性能更优。

在实践中，当同一个非接口值传递给 `fmt` 标准包提供的打印函数（这些函数的参数大部分类型为 interface{}）时，可以使用该提示。



元组参数。例如，在下面的代码中，后续代码中的第二个 `fmt.Fprint` 调用比第一个性能更好，因为它节省了两次分配。

```go
package main

import (
    "fmt"
    "io"
    "testing"
)

func main() {
    stat := func(f func()) int {
        allocs := testing.AllocsPerRun(100, f)
        return int(allocs)
    }

    var x = "aaa"
    var n = stat(func() {
        // 3 allocations
        fmt.Fprint(io.Discard, x, x, x)
    }) // 3

    var m = stat(func() {
        var i interface{} = x // 1 allocation
        // No allocations
        fmt.Fprint(io.Discard, i, i, i)
    })
    fmt.Println(m) // 1
}
```

## 14.3 调用接口方法需要少量的开销

调用接口方法需要查找虚表（virtual table）来找到调用的具体方法。通过接口值调用具体方法会阻止方法被内联（inlined）。

```go
package interfaces

import "testing"

type BinaryOp interface {
    Do(x, y float64) float64
}

type Add struct {}

func (a Add) Do(x, y float64) float64 {
    return x+y
}
```

```go
//go:noinline
func (a Add) Do_NotInlined(x, y float64) float64 {
    return x+y
}

var x1, y1, r1 float64
var add Add
func Benchmark_Add_Inline(b *testing.B) {
    for i := 0; i < b.N; i++ {
        r1 = add.Do(x1, y1)
    }
}

var x2, y2, r2 float64
var add_NotInlined Add
func Benchmark_Add_NotInlined(b *testing.B) {
    for i := 0; i < b.N; i++ {
        r2 = add.Do_NotInlined(x2, y2)
    }
}

var x3, y3, r3 float64
var add_InterfaceBinaryOp = Add()
func Benchmark_Add_NotInlined(b *testing.B) {
    for i := 0; i < b.N; i++ {
        r3 = add_Interface.Do(x3, y3)
    }
}
```

Benchmark_Inline-4 0.6254 ns/op
Benchmark_Add_NotInlined-4 2.340 ns/op
Benchmark_Add_Interface-4 4.935 ns/op

从基准测试结果可以看出，虚表查找的开销约为 2.5ns（对于此特定情况），而未内联导致的性能损失约为 1.7ns。这些损失在大多数情况下都存在，但如果代码在热执行路径上频繁运行，则可能是不容忽视的。

这在栈和逃逸分析章节中提到过。

然而，没必要犹豫使用接口方法。对于大多数情况，整洁的设计比更优性能更重要。而且官方 Go 编译器会在编译时对某些接口方法调用进行去虚化（de-virtualize）。

## 14.4 在频繁调用的小函数中避免使用接口参数和结果

由于大多数值装箱（value boxing）操作都需要内存分配，如果函数在代码执行过程中被大量频繁地调用，我们应该尝试避免声明带有接口参数和结果的小函数（包括方法）。

例如，在标准的 `image` 包中，有很多 `At(x, y int) color.Color` 和 `Set(x, y int, c color.Color)` 方法，它们被声明实现 `imagedraw.Image`。`color.Color` 类型是一个接口类型：

```go
type Color interface {
    RGBA(r, g, b, a uint32)
}
```

调用 `At` 和 `Set` 方法会导致短寿命内存分配（为了对非接口值装箱），并且调用 `color.RGBA` 接口方法会消耗额外的 CPU 资源（用于查找虚表且无法内联）。这些方法在图像处理应用中可能被大量调用，导致代码执行效率非常差。为了缓解这个问题，Go 1.17 引入了一个新的接口类型 `image/draw.RGBA64Image`：

```go
type RGBA64Image interface {
    Image
    RGBA64At(x, y int) color.RGBA64
    SetRGBA64(x, y int, c color.RGBA64)
}
```

新添加的方法 `RGBA64At` 返回一个非接口类型 `color.RGBA64`，而新增的方法 `SetRGBA64` 接受 `color.RGBA64` 参数。

```go
type RGBA64 struct {
    R, G, B, A uint16
}
```

通过使用 `RGBA64At` 和 `SetRGBA64` 方法，可以节省大量的内存分配和 CPU 资源，从而大幅提高代码的执行效率。
