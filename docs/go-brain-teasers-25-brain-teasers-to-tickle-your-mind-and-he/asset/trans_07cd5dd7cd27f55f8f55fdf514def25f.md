
### 24.1. 延伸阅读

- 《基于 Go 的代码库重构》（由 Russ Cox 撰写）解释了类型别名的原理
- Go 语言规范中的类型声明
- Go 语言规范中的类型断言
- 《Effective Go》中的类型开关与接口转换及类型断言

## 25. 你有我的许可

```
package main

import (
	"fmt"
)

const (
	Read = 1 << iota
	Write
	Execute
)

func main() {
	fmt.Println(Execute)
}
```

在进入下一页之前，先试着猜猜输出是什么。

*iota* 是 Go 语言版本的枚举类型。它可以用在 *const* 声明中。*iota* 在同一组中的每个常量上都会加 1。如果你对 *iota* 指定某个运算（例如加法），它会继续递增。

`<<` 是左移运算符，它会将数字中的位向左移动 n 位。

- 1 的二进制（8 位）是 00000001
- 1<<3 是 00001000，即 8

在本例中，我们从 *Read* = 1<<*iota* 开始，相当于 1<<0 -> 0001，即 1。接着隐式地有 1<<1 -> 0010 对应 *Write*，即 2；最后隐式地有 1<<2 -> 0100 对应 *Execute*，即 4。

你主要会用这些位运算来处理标志位。你可以使用 | [14]（称为"位掩码"）将 8 个标志打包进一个字节，并使用 & [15] 高效地检查某个标志是否被设置。

*清单 46. iota_check.go*

```
mask := Read | Execute

if mask&Execute == 0 {
    fmt.Println("can't execute")
} else {
    fmt.Println("can execute") // will be printed
}

if mask&Write == 0 {
    fmt.Println("can't write") // will be printed
} else {
    fmt.Println("can write")
}
```

iota 的值是数字，在某些情况下，你希望常量具有可读的表示形式。这可以通过给这些常量指定类型并为该类型实现 fmt.Stringer 接口来完成。

清单 47. iota_str.go

```
package main

import (
	"fmt"
)

type FilePerm uint16 // 16 flags are enough

const (
	Read FilePerm = 1 << iota
	Write
	Execute
)

// String implements fmt.Stringer interface
func (p FilePerm) String() string {
	switch p {
	case Read:
		return "read"
	case Write:
		return "write"
	case Execute:
		return "execute"
	}

	return fmt.Sprintf("unknown FilePerm: %d", p) // don't
	use %s here :)
}

func main() {
	fmt.Println(Execute) // execute
	fmt.Printf("%d\n", Execute) // 4
}
```

我将此作为练习留给你，实现一个支持位掩码的 String() string 方法。

### 25.1. 延伸阅读

- Go Wiki 上的 iota
- 《Effective Go》中的常量
- 维基百科上的位运算

- 14. 按位或。
- 15. 按位与。

## 致谢

我对每一份贡献都心存感激，无论是发现 Bug、修正语法，还是让我能安静地工作。

以下是提供帮助的人员名单，我向任何被我遗忘的人道歉。

- Adi Tebeka 负责校对和评论
- Dan Allen 在 asciidoctor 论坛提供了帮助。我正在使用出色的 asciidoctor 编写此书
- Dave Cheney 撰写了序言
- David Bordeynik 提供了评论
- Egon Elbre 绘制了所有这些可爱的地鼠（其中一幅用于封面），并将其置于 CC0 许可下
- Eliran Bivas 负责校对和评论
- Ran Tavory 提供了评论
- Yoni Davidson 提供了评论

我也感谢 Brad Fitzpatrick 及其他发布 Go"即时测验"的人，为这些脑筋急转弯提供了许多灵感。

## 尾声

希望你在猜谜的过程中感到有趣，并且在途中学到了一些东西。

> 调试就像在犯罪电影中扮演侦探，而你也是凶手。
> >
> > ~ 菲利普·福特斯

我发现，将出问题的事情视为待解决的谜题这种思维方式，能帮助我更好地理解事物。这也让我的工作更加愉快。当你试图解决自己犯下的当前"谋杀案"时，你可以随时把自己想象成南希·德鲁、福尔摩斯或其他任何你童年时期的侦探。

如果您想了解更多，欢迎发送电子邮件至 info@353solutions.com，我们将根据您的需求定制实操研讨会。

![](img/07a7b391d92ba53dcfe8da4b75a4aed7_122_0.png)

保持好奇，继续 hacking，
Miki Tebeka，2020 年 3 月

## 索引
