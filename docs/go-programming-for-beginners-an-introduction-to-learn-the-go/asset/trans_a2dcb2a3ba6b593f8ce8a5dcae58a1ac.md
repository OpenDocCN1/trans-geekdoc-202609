

# 10. 用户交互

到目前为止，我们已经看了几个编程示例。所有这些程序都使用了硬编码的值。没有任何程序给用户提供手动输入值的机会。在本节中，我们将学习如何接受用户的输入。与用户交互的方式有很多。我们将学习 `fmt` 包中用于读取用户输入的两个简单函数——`Scanln` 和 `Scanf`。

## 10.1 Scanln 函数

以下是使用 `Scanln` 函数的方法：

```go
fmt.Scanln(&<字符串变量>)
```

**示例：**

```go
var str string
fmt.Scanln(&str)
```

`Scanln` 函数需要指定一个字符串变量来存储用户的输入（在上述代码片段中用 `<字符串变量>` 标记）。该函数实现了**阻塞 I/O 操作**。也就是说，当执行控制到达 `Scanln` 语句时，程序的执行将暂停，给用户一个通过键盘输入内容（并按回车键）的机会。一旦用户输入内容并按下回车，用户通过键盘输入的任何内容都将被获取并存储在指定的字符串变量中。变量前的 `&` 符号用于获取变量的内存地址，以便 `Scanln` 函数可以直接设置指定变量的内容。这一概念将在指针章节中更清晰地说明。

让我们编写一个简单的 Go 程序，提示用户输入内容并将其显示回来：

```go
/* 用户交互演示 1 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
	"fmt"
)

/* 强制性的 main 函数 */
func main() {
	/* 创建一个变量来存储输入 */
	var str string

	/* 提示用户输入内容 */
	fmt.Printf("\n请输入内容: ")

	/* 使用 Scanln 函数读取用户输入 */
	fmt.Scanln(&str)

	/* 显示读取的内容 */
	fmt.Printf("\n您输入了: %s \n", str)
}
```

**输出：**
![](Image00033.jpg)

`Scanln` 函数有其自身的局限性。首先，它只能以字符串格式读取输入。这意味着，即使您输入一个数字，它也会被视为字符串。其次，它将输入作为以空格分隔的标记化字符串读取。也就是说，如果您输入一个句子，每个单词将被视为一个标记，并且需要相应数量的变量来存储输入。如果您只指定一个变量却输入一个句子，则只会读取第一个单词。

让我们运行相同的程序并尝试输入一个句子：
![](Image00034.jpg)

如所见，只读取了第一个单词。上面的输入有四个单词，因此 `Scanln` 语句应该指定 4 个变量来存储这 4 个单词，如下所示：

```go
fmt.Scanln(&str1, &str2, &str3, &str4)
```

同样，`Printf` 语句应如下所示：

```go
fmt.Printf("\n您输入了: %s %s %s %s\n ", str1, str2, str3, str4)
```

这是完整的程序：

```go
/* 用户交互演示 2 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
	"fmt"
)

/* 强制性的 main 函数 */
func main() {
	/* 创建变量来存储输入 */
	var str1, str2, str3, str4 string

	/* 提示用户输入内容 */
	fmt.Printf("\n请输入内容: ")

	/* 使用 Scanln 函数读取用户输入 */
	fmt.Scanln(&str1, &str2, &str3, &str4)

	/* 显示读取的内容 */
	fmt.Printf("\n您输入了: %s %s %s %s\n ", str1, str2, str3, str4)
}
```

**输出：**
![](Image00035.jpg)

虽然程序现在可以正确运行，但这不是读取句子的最佳方式，因为我们不知道用户会输入多长的句子。存储一个单词需要一个变量。这完全不切实际。稍后在本章中讨论的 `bufio` 包提供了一种读取句子的更好方法。我们将仅在想要一次读取一个单词或一个数字时使用 `Scanln` 函数。

如果用户输入一个数字，而您尝试使用 `Scanln` 读取它，它将以字符串格式存在。为了将字符串格式的数字转换为适当的数值格式，我们将使用 `strconv` 包中的函数。您要做的第一件事是在程序中导入此包并使用以下转换函数：

**将字符串格式的数字转换为整数：**

```go
<数字变量>, <错误变量> = strconv.Atoi(<字符串格式的数字>)
```

**示例：**

```go
num, err := strconv.Atoi("55")
```

在上面的示例中，字符串格式的 `"55"` 将被转换为整数格式的 `55` 并存储在变量 `num` 中（此处使用短变量声明）。同时，`err` 也被短声明，用于存储可能发生的转换错误。

**将字符串格式的数字转换为浮点数：**

```go
<变量> = strconv.ParseFloat(<字符串格式的数字>, <位数>)
```

**示例：**

```go
numS := "-46.2343"
numF, err := strconv.ParseFloat(numS, 64)
```

在上面的示例中，`ParseFloat` 函数将字符串格式的 `"-46.2343"` 转换为 64 位浮点格式的 `-46.2343` 并返回给 `numF` 变量存储。

让我们编写一个 Go 程序，从用户那里接受 4 个数字——两个整数和两个浮点数。我们将使用 `Scanln` 函数读取这些输入，因此所有 4 个数字都将以字符串格式存储。我们将把这些数字转换为适当的格式并执行加、减、乘、除运算：

```go
/* 用户交互演示 3 - 处理数字 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 和 strconv 包 */
import (
	"fmt"
	"strconv"
)

/* 强制性的 main 函数 */
func main() {
	/* 声明变量来存储输入 */
	var num1_str, num2_str, num3_str, num4_str string

	/* 声明变量来存储 int 和 float64 等价值 */
	var num1, num2, sum, diff int
	var num3, num4, prod, quo float64

	/* 提示用户输入两个整数 */
	fmt.Printf("\n请输入两个整数: ")

	/* 使用 Scanln 函数读取用户输入 */
	fmt.Scanln(&num1_str, &num2_str)

	/* 提示用户输入两个浮点数 */
	fmt.Printf("\n请输入两个浮点数: ")

	/* 使用 Scanln 函数读取用户输入 */
	fmt.Scanln(&num3_str, &num4_str)

	/* 将 num1_str 和 num2_str 转换为整数 */
	num1, err1 := strconv.Atoi(num1_str)
	num2, err2 := strconv.Atoi(num2_str)

	/* 将 num3_str 和 num4_str 转换为 float64 */
	num3, err3 := strconv.ParseFloat(num3_str, 64)
	num4, err4 := strconv.ParseFloat(num4_str, 64)

	/* 将错误赋值给空标识符 */
	_ = err1
	_ = err2
	_ = err3
	_ = err4

	/* 执行算术运算 */
	sum = num1 + num2
	diff = num1 - num2
	prod = num3 * num4
	quo = num3 / num4

	/* 打印所有内容 */
	fmt.Printf("\nnum1 + num2 = %d", sum)
	fmt.Printf("\nnum1 - num2 = %d", diff)
	fmt.Printf("\nnum3 * num4 = %f", prod)
	fmt.Printf("\nnum3 / num4 = %f \n", quo)
}
```

**注意：** 我们为 4 次不同的转换使用了 4 个不同的错误变量——`err1`、`err2`、`err3` 和 `err4`。实际上没有必要使用它们。但是，如果您不使用它们，编译器将返回“声明但未使用”错误，程序将无法构建。为了规避这个问题，可以将每个错误变量赋值给空标识符 `_`。

**输出：**
![](Image00036.jpg)

## 10.2 Scanf 函数

`Scanf` 函数与 C 语言中使用的函数非常相似。该函数使用动词（类似于 C 语言中的格式说明符）来读取特定类型的数据。例如，如果您想从用户那里读取一个整数，可以使用动词 `%d`。这消除了 `Scanln` 中使用的数据转换的额外步骤。第 8 章讨论的相同动词将被使用。

以下是通用语法：

```go
fmt.Scanf("<带有动词的格式化字符串>", &<用逗号分隔的变量>)
fmt.Scanf("%<动词 1> %<动词 2>, ...", &<变量 1>, &<变量 2>, ...)
```

**示例：**

```go
fmt.Scanf("%s %d %f", &name, &age, &weight)
```

`Scanf` 函数使用由动词组成的格式化字符串来解析用户的输入。对于使用的每个动词，都有一个对应的变量（变量名前缀为 `&` 符号）。该函数也实现了**阻塞 I/O 操作**。当用户通过键盘输入内容时，它将根据格式化字符串中指定的格式进行解析。

例如，如果格式化字符串如下——`"%s %d %f"`，用户应该输入三个用空格分隔的值，其中第一个值是字符串，第二个值是整数，第三个值是浮点数。只有在输入所有值后才应按回车键。如果用户在输入第一个值后按下回车，则将跳过剩余的两个输入，相应的变量将获得零值。

让我们再举一个格式化字符串的例子。如果格式化字符串如下——`"%d\n%f\n%d\n%s"`，该函数将期望用户输入 4 个值。动词之间的 `"\n"` 字符序列表示用户应该在输入每个值后按回车键。如果这让您感到困惑，您可以始终为每个输入使用一条 `Scanf` 语句。

让我们编写一个程序，从用户那里读取 3 个输入并将用户输入的内容打印回来：

```go
/* Scanf 演示 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
	"fmt"
)

/* 强制性的 main 函数 */
func main() {
	/* 声明变量 */
	var name string
	var age int
	var weight float32

	/* 提示用户输入 3 个值 */
	fmt.Printf("\n请输入姓名、年龄和体重: ")

	/* 读取 3 个值 */
	fmt.Scanf("%s %d %f", &name, &age, &weight)

	/* 显示所有内容 */
	fmt.Printf("\n\n姓名: %s, 年龄: %d, 体重: %f \n", name, age, weight)
}
```

**输出：**
![](Image00037.jpg)

在上面的示例中，`"Liev"` 被读作字符串，`18` 被读作 int，`152` 被读作 float32。输入分配给变量的过程如下：
![](Image00038.jpg)

如前所述，输入是根据动词指定的数据类型读取的，因此不需要将输入从一种形式转换为另一种形式。让我们通过编写一个程序来添加两个数字来验证这一点。这次，我们将在两个动词之间插入 `\n`，因此用户在输入每个数字后必须按回车键：

```go
/* Scanf 两数相加演示 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt 包 */
import (
	"fmt"
)

/* 强制性的 main 函数 */
func main() {
	/* 声明变量 */
	var num1, num2, sum int

	/* 提示用户输入 2 个数字 */
	fmt.Printf("\n请输入两个数字: ")

	/* 读取 2 个数字 */
	fmt.Scanf("%d\n%d", &num1, &num2)

	/* 计算总和 */
	sum = num1 + num2

	/* 显示所有内容 */
	fmt.Printf("\n总和 = %d\n", sum)
}
```

**输出：**
![](Image00039.jpg)

## 10.3 读取句子

`Scanf` 和 `Scanln` 函数都无法读取句子，即包含单词的字符串。`bufio` 包中有一个名为 `ReadString` 的函数。因此，如果您打算使用 `ReadString` 函数，需要导入 `bufio` 包。除了 `bufio`，还应导入 `os`，因为我们需要访问 `os.Stdin`（标准输入/输出）。不用担心技术细节，这是一个高级主题。如果您想读取一个句子，只需记住几行代码即可。

以下是通用语法：

```go
<读取器变量> := bufio.NewReader(os.Stdin)
<字符串变量>, _ := <读取器变量>.ReadString('\n')
```

**示例：**

```go
r := bufio.NewReader(os.Stdin)
msg, _ := r.ReadString('\n')
```

这是一个提示用户输入内容并读取完整句子的程序：

```go
/* 读取句子 */
/* 包声明 */
package main

/* 导入语句 - 导入 fmt、bufio、os 包 */
import (
	"fmt"
	"bufio"
	"os"
)

/* 强制性的 main 函数 */
func main() {
	/* 使用 stdin 创建一个 NewReader 类型的输入读取器变量 */
	inputReader := bufio.NewReader(os.Stdin)

	/* 提示用户输入内容 */
	fmt.Printf("\n请输入一个句子: ")

	/* 使用 ReadString 函数读取 */
	text, _ := inputReader.ReadString('\n')

	/* 打印读取的内容 */
	fmt.Printf("\n您输入了: \n%s", text)
}
```

**输出：**
![](Image00040.jpg)

