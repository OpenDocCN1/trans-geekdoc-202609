

# 17. 编程示例

既然我们已经学习了 Go 编程的基础知识，现在让我们将这些概念付诸实践，尝试一些编程示例。

## 17.1 数字各位之和

下面是一个程序，它从用户处读取一个整数并计算其各位数字之和：

```go
/*各位数字之和*/
/*包声明*/
package main

/*导入语句 - 导入 fmt 包*/
import (
	"fmt"
)

/*强制性的 main 函数*/
func main() {
	var number int
	var sum int = 0
	fmt.Printf("\n请输入一个数字: ")
	fmt.Scanf("%d", &number)
	for number > 0 {
		/*将个位数字加到 sum 上*/
		sum = sum + (number % 10)
		/*丢弃个位数字*/
		number = number / 10
	}
	fmt.Printf("\n所有数字之和: %d\n", sum)
}
```

**输出：**
![](Image00084.jpg)

## 17.2 斐波那契数列

斐波那契数列以 0 和 1 作为前两项开始。下一项通过将前两项相加得出。由于前两项是 0 和 1，接下来的项将是 1、2、3、5、8，依此类推。以下是该程序：

```go
/*斐波那契数列*/
/*包声明*/
package main

/*导入语句 - 导入 fmt 包*/
import (
	"fmt"
)

/*强制性的 main 函数*/
func main() {
	var terms, next int
	var previous, current int = 0, 1
	fmt.Printf("\n请输入要生成的项数: ")
	fmt.Scanf("%d", &terms)
	if terms < 2 {
		fmt.Printf("\n斐波那契数列至少包含两项")
	} else {
		fmt.Printf("\n\n斐波那契数列:\n\n")
		for i := 0; i < terms; i++ {
			fmt.Printf("%d ", previous)
			next = previous + current
			previous = current
			current = next
		}
	}
	fmt.Printf("\n")
}
```

**输出：**
![](Image00085.jpg)

## 17.3 反转给定数字

下面是一个读取整数并将其反转的程序：

```go
/*反转数字*/
/*包声明*/
package main

/*导入语句 - 导入 fmt 包*/
import (
	"fmt"
)

/*强制性的 main 函数*/
func main() {
	var number int
	var rev int = 0
	fmt.Printf("\n请输入一个数字: ")
	fmt.Scanf("%d", &number)
	for number > 0 {
		rev = (rev * 10) + (number % 10)
		number = number / 10
	}
	fmt.Printf("\n反转结果: %d\n", rev)
}
```

**输出：**
![](Image00086.jpg)

## 17.4 字符串回文

如果一个字符串的反转与原字符串相同，则称该字符串为回文。例如，“book” 不是回文，而 “malayalam” 是回文。以下程序接收一个字符串作为输入并检查它是否为回文。请注意，未考虑大小写敏感性。

```go
/*回文*/
/*包声明*/
package main

/*导入语句 - 导入 fmt、bufio、os、strings 包*/
import (
	"fmt"
	"bufio"
	"os"
	"strings"
)

/*强制性的 main 函数*/
func main() {
	/*使用 stdin 创建一个类型为 NewReader 的输入读取器变量*/
	inputReader := bufio.NewReader(os.Stdin)
	/*提示用户输入内容*/
	fmt.Printf("\n请输入一个字符串: ")
	/*使用 ReadString 函数读取字符串*/
	str, _ := inputReader.ReadString('\n')
	/*去除 \n 和 \r 字符*/
	str = strings.Trim(str, "\n\r")
	str_length := len(str) - 1
	/*使用 rune 获取数组中的字符*/
	str_char := []rune(str)
	/*反转字符串*/
	for i := 0; i < str_length/2; i++ {
		temp := str_char[i]
		str_char[i] = str_char[str_length-i]
		str_char[str_length-i] = temp
	}
	/*使用 string 函数转回字符串*/
	rev_str := string(str_char)
	fmt.Printf("\n反转后的字符串: %s\n", rev_str)
	/*检查两个字符串是否相等*/
	result := strings.Compare(str, rev_str)
	if result == 0 {
		fmt.Printf("\n%s 是回文。\n", str)
	} else {
		fmt.Printf("\n%s 不是回文。\n", str)
	}
}
```

**输出：**
![](Image00087.jpg)

## 17.5 冒泡排序

冒泡排序是一种按升序或降序对数据结构进行排序的算法。在此算法中，以嵌套方式使用两个循环。内层循环确保将最大或最小元素放置在数据结构的开头或末尾。外层循环的迭代次数等于数据结构中的元素数量。我们将编写一个程序，从用户处读取 5 个整数，将它们放入数组，并使用冒泡排序按升序对数组进行排序。

```go
/*使用冒泡排序对数组排序*/
/*包声明*/
package main

/*导入语句 - 导入 fmt、strconv 包*/
import (
	"fmt"
	"strconv"
)

/*强制性的 main 函数*/
func main() {
	/*声明变量*/
	var arr [5]int
	/*声明两个循环计数器*/
	var i, j int
	/*声明一个变量临时存储作为字符串的数字*/
	var num_str string
	/*提示用户输入 5 个元素，使用 for 循环*/
	for i = 0; i < 5; i++ {
		fmt.Printf("\n请输入索引 %d 处的元素: ", i)
		fmt.Scanln(&num_str)
		/*将 num_str 转换为整数*/
		num, err := strconv.Atoi(num_str)
		/*将 num 赋值给 arr[i]*/
		arr[i] = num
		/*将 err 赋值给空标识符*/
		_ = err
	}
	fmt.Printf("\n原始数组: %d\n", arr)
	arr_length := len(arr)
	/*冒泡排序*/
	for i = 0; i < arr_length; i++ {
		for j = 0; j < i; j++ {
			if arr[j] > arr[j+1] {
				temp := arr[j]
				arr[j] = arr[j+1]
				arr[j+1] = temp
			}
		}
	}
	fmt.Printf("\n排序后的数组: %d\n", arr)
}
```

**输出：**
![](Image00088.jpg)

# 18. 结束语

Go 编程语言是一个相对较新的语言。第一个版本发布于 2012 年，因此在撰写本书时（2020 年），它大约只有 8 岁。凭借其提供的特性，这门语言拥有巨大的潜力。我编写本书的目的是让读者熟悉一门新的编程语言，它可能在不久的将来彻底改变软件开发。我已尽最大努力使书中的概念非常简单，以便您的基础变得非常扎实。在 Web 开发、云应用开发、中间件开发等方面，Go 语言已被证明是**游戏规则改变者**。如果您已经理解了本书中解释的基本概念，您绝对应该学习更多内容，并可能涉足一些高级概念，如面向对象编程、文件处理、错误处理等。如果您已经是一名 Web 开发人员，您应该尝试 Web 框架，如 `Gin`、`Web.Go`、`Martini`、`Revel` 等，以开发 Web 应用程序和服务。希望您从本书中学到了有价值的知识。请永远记住——学无止境！

如果您像我写作时一样喜欢这本书，您可以订阅*我的电子邮件列表，以获取独家内容和未来新书的抢先预览。请访问下面的链接：[http://eepurl.com/du_L4n](http://eepurl.com/du_L4n) 或使用二维码：![](Image00089.jpg)(*订阅者必须年满 13 周岁)

