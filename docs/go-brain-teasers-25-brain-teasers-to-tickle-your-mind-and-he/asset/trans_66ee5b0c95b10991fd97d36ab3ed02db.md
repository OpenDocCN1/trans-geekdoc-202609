

Go 中还有其他“nil 安全”类型。例如，你可以查询 nil 切片的长度，从空 channel 接收一个值（不过你会永远阻塞），等等。

### 2.1. 延伸阅读

- Go 博客上的“Go maps in action”
- 《Effective Go》中的 Maps 章节

## 3. WHEN IN KRAKÓW

Listing 4. city.go

```
package main

import (
	"fmt"
)

func main() {
	city := "Kraków"
	fmt.Println(len(city))
}
```

在翻到下一页之前，试着猜猜输出会是什么。

如果你数一下 Kraków 中的字符数，结果是 6。那为什么是 7？原因是……历史。

起初，计算机是在英语国家（英国和美国）开发的。当早期开发者想要在只懂比特的计算机中对文本进行编码时，他们提出了以下方案：使用一个字节（8 位）[3] 来表示一个字符。例如，a 是 97（01100001），b 是 98，以此类推。一个字节足以表示包含 26 个小写字母、26 个大写字母和 10 个数字的英文字母表。甚至还有剩余空间用于其他特殊字符（例如，9 表示制表符）。这就是 ASCII 编码。

过了一段时间，其他国家开始使用计算机，并希望使用本国语言书写。ASCII 已不够用，一个字节不足以容纳表示不同语言字母所需的所有数字。这导致出现了多种不同的编码方案，最常见的是 UTF-8。Rob Pike 是 Go 的设计者之一，同时也是 UTF-8 的设计者之一。

Go 字符串采用 UTF-8 编码，这意味着一个字符（称为 rune）的长度可以是 1 到 4 个字节。当你在 Go 中查询字符串长度时，得到的是字节大小。在这个例子中，rune ó 占用 2 个字节，因此字符串的总长度是 7。

如果你想知道字符串中 rune 的数量，需要使用 unicode/utf8 包。

Listing 5. cityu.go

```
package main

import (
	"fmt"
	"unicode/utf8"
)

func main() {
	city := "Kraków"
	fmt.Println(utf8.RuneCountInString(city))
}
```

### 3.1. 延伸阅读

- Go 博客上的“Strings, bytes, runes and characters in Go”
- Unicode and You
- 维基百科上的 Unicode 条目

3 精确来说，ASCII 只使用 7 位，而 LATIN-1 将其扩展到 8 位。

## 4. I'VE GOT NOTHING

Listing 6. city.go

```
package main

import (
	"fmt"
)

func main() {
	n := nil
	fmt.Println(n)
}
```

在翻到下一页之前，试着猜猜输出会是什么。

这段代码无法编译。

nil 不是类型，而是一个保留字。初始化为 nil 的变量必须有一个类型。例如，如果你将赋值改为 var n *int = nil，代码将能够编译，因为现在 n 有了类型。

nil 的一些用法如下：

- map、slice 和 chan 的零值是 nil。
- 你不能使用 == 比较切片或映射，只能将它们与 nil 进行比较 [4]。
- 向 nil channel 发送或从中接收会永远阻塞。你可以利用这一点来避免忙等待。

### 4.1. 延伸阅读

- Dave Cheney 的 Practical Go 中的“理解 nil”
- justforfunc 的“为什么 Go 中有 nil channel？”
- Dave Cheney 的“Channel Axioms”

4 你可以使用 reflect.DeepEqual 来比较映射和切片。

## 5. A RAW DIET

Listing 7. raw.go

```
package main

import (
	"fmt"
)

func main() {
	s := `\a\tb`
	fmt.Println(s)
}
```

在翻到下一页之前，试着猜猜输出会是什么。

这段代码将输出：a\tb

Go 规范说明：

有两种形式：原始字符串字面量和解释字符串字面量。

原始字符串用反引号括起来（例如 `hello`），解释字符串用引号括起来（例如 "hello"）。在原始字符串中，\ 没有特殊含义，所以 `\t` 是两个字符——反斜杠和字母 t。如果是解释字符串，则 \t 会被解释为制表符字符。

除了常见的 \t（制表符）、\n（换行符）等之外，你还可以在解释字符串中使用 Unicode 码点。fmt.Println("\u2122") 将输出 ™。

原始字符串最常见的用途之一是创建多行字符串。

```
// An HTTP request
request := `GET / HTTP/1.1
Host: www.353solutions.com
Connection: Close
`
```

### 5.1. 延伸阅读

- Go 博客上的“Strings, bytes, runes and characters in Go”
- 字符串规范
- 维基百科上的 ASCII 控制字符

## 6. ARE WE THERE YET?

Listing 8. time.go

```
package main

import (
	"fmt"
	"time"
)

func main() {
	timeout := 3
	fmt.Printf("before ")
	time.Sleep(timeout * time.Millisecond)
	fmt.Println("after")
}
```

在翻到下一页之前，试着猜猜输出会是什么。

这段代码无法编译。

当你写 `timeout := 3` 时，Go 编译器会进行类型推断。
在这种情况下，它会推断 `timeout` 是 `int` 类型。然后在第 11 行，你将 `timeout`（int 类型）与 `time.Millisecond`（`time.Duration` 类型）相乘——这是不允许的。

你有几种方法来修复这个问题。

将 `timeout` 的类型更改为 `time.Duration`（第 9 行）：

```
var timeout time.Duration = 3
```

将 `timeout` 设为 const，那么它的类型将在使用上下文中解析（第 9 行）：

```
const timeout = 3
```

使用类型转换将 `timeout` 转换为 `time.Duration`（第 11 行）：

```
time.Sleep(time.Duration(timeout) * time.Millisecond)
```

### 6.1. 延伸阅读

- Go 之旅中的类型推断
- golang/example 中的 go/types：Go 类型检查器
- time.Duration 类型
- Go 规范中的类型转换

## 7. CAN NUMBERS LIE?

Listing 9. float.go

```
package main
import (
"fmt"
)
func main() {
n := 1.1
fmt.Println(n * n)
}
```

在翻到下一页之前，试着猜猜输出会是什么。

这段代码将输出：1.2100000000000002

你可能期望是 1.21，这是正确的数学答案。

一些新开发者在看到这种或类似输出时，会到论坛上说“我们在 Go 中发现了一个 Bug！”。通常的回答是 RTFM。[5]。

> 浮点数有点像量子物理：你越仔细看，它就越混乱。
> ~ Grant Edwards

这个问题背后的基本思想是，在浮点数中我们牺牲精度来换取速度（也就是说，作弊）。不要震惊，这在计算机科学中是我们经常进行的一种权衡。

你看到的结果符合浮点数规范。如果你在 Python、Java、C 等语言中运行相同的代码，会看到相同的输出。

如果你想了解浮点数的工作原理，请参阅下面的链接。你需要记住的主要观点是：它们不精确，而且数字越大，精度越差。

这意味着，在使用浮点数进行测试时，你需要检查“大约相等”，并决定什么是可接受的阈值。诸如 testify 之类的测试库提供了现成的函数（例如 InDelta）来检查两个浮点数是否近似相等。

浮点数还有几个其他古怪之处。例如，有一个特殊的 NaN 值（“not a number”的缩写）。NaN 不等于任何数字，包括它自身。下面的代码将输出 false。

```
fmt.Println(math.NaN() == math.NaN())
```

要检查是否得到了 NaN，你需要使用像 math.IsNaN 这样的特殊函数。

如果你需要更好的精度，可以查看 math/big 或 shopspring/decimal 之类的外部包。

### 7.1. 延伸阅读

- Julia Evans 的《浮点数小册子》
- 《每个计算机科学家都应该知道的关于浮点数算术的知识》

5 阅读精妙手册。

## 8. SLEEP SORT

Listing 10. sleep_sort.go

```
package main

import (
	"fmt"
	"sync"
	"time"
)

func main() {
	var wg sync.WaitGroup
	for _, n := range []int{3, 1, 2} {
		wg.Add(1)
		go func() {
			defer wg.Done()
			time.Sleep(time.Duration(n) * time.Millisecond)
			fmt.Printf("%d ", n)
		}()
	}
	wg.Wait()
	fmt.Println()
}
```

> 在翻到下一页之前，试着猜猜输出会是什么。

