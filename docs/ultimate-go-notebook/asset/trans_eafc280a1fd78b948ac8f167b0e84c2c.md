

# 列表 8.4

```go
var gs string

func BenchmarkSprint(b *testing.B) {
    var gs string

    for i := 0; i < b.N; i++ {
        s = fmt.Sprint("hello")
    }

    gs = s
}
```

每个基准测试的核心都是从 `i` 到 `b.N` 的循环。循环内部放置了要进行基测试的代码。为了理解这个循环，我需要了解一个名为 `-benchtime` 的设置。

`-benchtime` 代表在提供结果之前运行循环的总时间。这里变得有点意思了，因为我不能根据时间来运行循环，只能根据迭代次数来运行。需要确定为了匹配 `-benchtime` 所需的迭代次数。

匹配 `-benchtime` 的正确 `b.N` 是通过一些尝试错误完成的。在运行基准测试的最开始，工具会将 `b.N` 的值设置为 1 并运行循环。然后它会将 `b.N` 的值乘以 100，直到接近 `-benchtime`。然后，算法就可以固定一个可用的 `b.N`。

# 列表 8.5

```go
var gs string
var a []int

func BenchmarkSprint(b *testing.B) {
    var gs string

    a = append(a, b.N)
    for i := 0; i < b.N; i++ {
        s = fmt.Sprint("hello")
    }

    if len(a) > 4 {
        fmt.Println(a)
    }

    gs = s
}
```

我添加了在每次调用基准测试函数时捕获 `b.N` 值的。。已知在某些情况下需要 5 次调用才能找到正确的 `b.N`，这时我就输出切片的内容。

# 列表 8.6
BenchmarkSprint-16 [1 100 10000 1000000 54495168]

我看到工具在 5 次尝试后确定了一个 `b.N` 的值，在尝试百万次迭代后找到了正确的数字。

这是编译器基准测试的另一个重要方面。编译器会将此代码编译成二进制文件以运行基准测试。循环内部的代码与生产环境中的运行保持准确是非常重要的。任何微小的变化都可能改变编译器构建代码的方式，或者代码在运行时的行为。

回到 Sprint 基准测试的原始代码。

# 列表 8.7

```go
var gs string
func BenchmarkSprint(b *testing.B) {
  var s string
  for i := 0; i < b.N; i++ {
    s = fmt.Sprint("hello")
  }

  gs = s
}
```

这个基准测试衡量的是调用 `Sprint` 的性能。注意 `Sprint` 函数在调用后返回了一个新字符串。在运行基准测试时，捕获该返回值是非常重要的，因为这代表了生产代码中使用该函数的真实行为。

如果我不捕获 `Sprint` 调用的返回值，编译器可能会将函数调用从编译后的二进制文件中剔除。如果不捕获返回值，该函数就是无用的，因为单代码的行为本身不会改变程序的行为。如果编译器选择丢弃对 `Sprint` 的调用，基准测试将只是运行一个空循环，提供不准确的结果。

当我运行基准测试时，我在命令行上使用以下调用。

# 列表 8.8

```
$ go test -bench . -benchtime 3s -benchmem
```

将此拆解，我要求 go 运行它在当前目录下找到的所有基准测试函数（`-bench .`），将运行循环的时间增加到三秒（`-benchtime 3s`），并显示内存分配（`-benchmem`）。

# 列表 8.9

| BenchmarkSprint-16 | 56956252 | 55.48 ns | 5 B/op | 1 allocs/op |
| Benchmarkf-16 | 80984947 | 42.46 ns | 5 B/op | 1 allocs/op |

BenchmarkSprint-16 基准测试函数的名称以及线程数，这里是 16。

56956252 执行的循环迭代次数，为 56,956,252 次。

55.48 ns/op 循环内部代码执行的时间，为 55.48 纳秒。

5 B/op 循环内部代码分配的内存量，为 5 字节。

1 allocs/op 循环内部代码分配的值数量，为 1 个。

最后，对于字符串 "hello"，使用 `Sprintf` 比 `Sprint` 更快，尽管它们在堆上分配了相同数量的值和总内存。

## 8.2 基础子基准测试

有时我可能想将一组基准测试整合在一个基准测试函数下。我可能有一个数据表，我想在命令行上控制哪些数据正在被基准测试。如果我遇到其中任何情况，Go 的子基准测试支持就是我需要的。

# 列表 8.10

```go
package basic

import (
	"fmt"
	"testing"
)

var gs string

func BenchmarkSprint(b *testing.B) {
	b.Run("Sprint", func(b *testing.B) {
		for i := 0; i < b.N; i++ {
			fmt.Sprint("hello")
		}
	})
	b.Run("Sprintf", func(b *testing.B) {
		for i := 0; i < b.N; i++ {
			fmt.Sprintf("%s", "hello")
		}
	})
}
```
*注：列表 8.10 的 OCR 识别在源文件中已损坏；我根据文中描述的标准 Go 子基准测试模式对其进行了重构。）*

## 8.2 子基准测试

有时我可能想将一组基准测试整合在一个基准测试函数下。我可能有一个数据表，我想在命令行上控制哪些数据正在被基准测试。如果我遇到其中任何情况，Go 的子基准测试支持就是我需要的。

## 8.3 验证基准测试

有时我可能想将一组基准测试整合在一个基准测试函数下。我可能有一个数据表，我想在命令行上控制哪些数据正在被基准测试。如果我遇到其中任何情况，Go 的子基准测试支持就是我需要的。

这里我如何使用子基准测试。

# 列表 8.11

```go
func BenchmarkSplit(b *testing.B) {
	cases := []struct {
		name  string
		input string
	}{
		{"short", "hello"},
		{"long", "world"},
	}
	for _, c := range cases {
		b.Run(c.name, func(b *testing.B) {
			for i := 0; i < b.N; i++ {
				fmt.Sprint(c.input)
			}
		})
	}
}
```

# 列表 8.12

```go
func merge(a, b []int) []int {
	ret := make([]int, 0, len(a)+len(b))
	i, j := 0, 0
	for i < len(a) && j < len(b) {
		if a[i] < b[j] {
			ret = append(ret, a[i])
			i++
		} else {
			ret = append(ret, b[j])
			j++
		}
	}
	ret = append(ret, a[i:]...)
	ret = append(ret, b[j:]...)
	return ret
}
```

# 列表 8.13

```go
func BenchmarkSprint(b *testing.B) {
	var gs string
	b.Run("Sprint", func(b *testing.B) {
		var s string
		for i := 0; i < b.N; i++ {
			s = fmt.Sprint("hello")
		}
		gs = s
	})
}
```

# 列表 8.14

```go
func unlimited(n []int) []int {
	if len(n) <= 1 {
		return n
	}
	mid := len(n) / 2
	var wg sync.WaitGroup
	wg.Add(2)
	var left, right []int
	go func() {
		defer wg.Done()
		left = unlimited(n[:mid])
	}()
	go func() {
		defer wg.Done()
		right = unlimited(n[mid:])
	}()
	wg.Wait()
	return merge(left, right)
}
```

# 列表 8.15

```go
func numCPU(n []int) []int {
    // ...
}
```

