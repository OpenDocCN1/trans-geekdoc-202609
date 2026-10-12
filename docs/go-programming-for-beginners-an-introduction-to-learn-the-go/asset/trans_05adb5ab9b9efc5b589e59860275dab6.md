

# 14. 字符串

字符串是字符的序列。可以通过将一系列字符用双引号括起来来形成常量字符串。就像数组一样，可以通过指定索引，借助访问操作符（`[]`）来访问单个字符。字符串的索引从 0 开始，到比字符串大小小 1 的位置结束。字符串的长度可以使用 `len(<string>)` 函数来确定。使用访问操作符，只能读取单个字符，而不能设置。

下面是一个演示这些字符串基础知识的简单 Go 程序：

```go
/*String Demo 1*/
/*Package Declaration*/
package main

/*Import Statement - import fmt package*/
import (
	"fmt"
)

/*Mandatory main function*/
func main() {
	/*Declare and initialize a string*/
	var name string = "Monica"

	/*Fetch length of the string*/
	length := len(name)

	/*Display the string and its length*/
	fmt.Printf("\nname = %s, length = %d\n", name, length)

	/*Use for loop to print individual characters of the string*/
	for i := 0; i < length; i++ {
		fmt.Printf("\nCharacter at index %d ==> %c\n", i, name[i])
	}
}
```

输出：
![](Image00070.jpg)

可以使用 rune 函数将字符串的单个字符获取到字符数组中，如下所示：

```go
<character array var> = []rune(<String>)
```

示例：
```go
c_arr = []rune(str)
```

可以使用 `string` 函数将字符数组转换为字符串，如下所示：

```go
<string> = string(<character array variable>)
```

示例：
```go
str = string(char_array)
```

下面是一个演示该函数工作原理的程序：

```go
/*Rune demo*/
/*Package Declaration*/
package main

/*Import Statement - import fmt package*/
import (
	"fmt"
)

/*Mandatory main function*/
func main() {
	str := "Excelsior"

	str_length := len(str)

	/*Use rune to fetch characters in an array*/
	str_char := []rune(str)

	fmt.Printf("\nstr: %s, length: %d", str, str_length)

	fmt.Printf("\n\nCharacter array: %c\n", str_char)

	fmt.Printf("\nstr_char character array elements: \n")

	for i := 0; i < str_length; i++ {
		fmt.Printf("\nCharacter at index %d ==> %c\n", i, str_char[i])
	}
}
```

输出：
![](Image00071.jpg)

有一个名为 `strings` 的包，它包含许多有助于字符串操作的内置函数。让我们来看看其中几个重要的：

## 14.1 连接字符串

可以使用 `strings.Join` 函数连接两个或多个字符串。为此，待连接的字符串应放在一个字符串数组中。以下是通用语法：

```go
strings.Join(<string array>, <separator>)
```

示例：
```go
big_string := strings.Join(arr, " ")
```

还有一种连接两个或多个字符串的更简单方法——使用 `+` 运算符。通用语法：

```go
<concatenated string variable> = <string 1> + <string 2> + ... <string n>
```

示例：
```go
big_str := "hello" + " " + "world!"
```

让我们编写一个程序来演示这两种连接方法：

```go
/*String Demo 2 - Concatenation*/
/*Package Declaration*/
package main

/*Import Statement - import fmt, strings packages*/
import (
	"fmt"
	"strings"
)

/*Mandatory main function*/
func main() {
	/*Declare and initialize a string array*/
	var words = []string{"This", "is", "an", "array", "of", "7", "strings"}

	/*Display the string array*/
	fmt.Printf("\nwords array: %s\n", words)

	/*Concatenate using strings.Join*/
	words_str := strings.Join(words, " ")

	fmt.Printf("\nConcatenated string (using strings.Join): %s\n", words_str)

	/*Short declare some strings*/
	str1 := "Go"
	str2 := "Programming"
	str3 := "Language"

	/*Concatenate str1, str2 and str3*/
	str4 := str1 + " " + str2 + " " + str3

	fmt.Printf("\nstr1 = %s\nstr2 = %s\nstr3 = %s\n\nConcatenated string (using + operator)\n\nstr4 = %s\n", str1, str2, str3, str4)
}
```

输出：
![](Image00072.jpg)

## 14.2 比较字符串

`strings` 包中的 `Compare` 函数用于比较两个字符串。

语法：
```go
strings.Compare(<string1>, <string2>)
```

示例：
```go
result := strings.Compare(string1, string2)
```

如果两个字符串相同，该函数返回 0；如果 `string1` 在字典序上小于 `string2`，则返回 `-1`；如果 `string1` 在字典序上大于 `string2`，则返回 `1`。

让我们编写一个程序从用户处读取两个字符串并进行比较：

```go
/*Compare two strings*/
/*Package Declaration*/
package main

/*Import Statement - import fmt, bufio, os, strings package*/
import (
	"fmt"
	"bufio"
	"os"
	"strings"
)

/*Mandatory main function*/
func main() {
	/*Create an input reader variable of type NewReader using stdin*/
	inputReader := bufio.NewReader(os.Stdin)

	/*Prompt the user to enter something*/
	fmt.Printf("\nEnter a string: ")

	/*Read string using ReadString function*/
	str1, _ := inputReader.ReadString('\n')

	fmt.Printf("\nEnter another string: ")

	/*Read string using ReadString function*/
	str2, _ := inputReader.ReadString('\n')

	/*Compare str1 and str2 using strings.Compare*/
	result := strings.Compare(str1, str2)

	if result == 0 {
		fmt.Printf("\nBoth strings are the same.\n")
	} else if result > 0 {
		fmt.Printf("\nFirst string is lexicographically greater than the second string.\n")
	} else {
		fmt.Printf("\nSecond string is lexicographically greater than the first string.\n")
	}
}
```

输出：
![](Image00073.jpg)

## 14.3 在另一个字符串中搜索字符串

`strings` 包中的 `Contains` 函数用于检查一个字符串是否存在于另一个字符串中。如果字符串存在，该函数返回布尔值 `true`，如果不存在则返回 `false`。

语法：
```go
strings.Contains(<main string>, <string to be searched>)
```

示例：
```go
result := strings.Contains("Hello World", "World")
```

此外，可以使用 `strings` 包中的 `Index` 函数来确定给定字符串在主字符串中首次出现的位置。如果字符串不存在于主字符串中，该函数返回 `-1`。

下面是一个从用户处读取两个字符串并在主字符串中搜索第二个字符串的程序：

```go
/*Search for a string within another string*/
/*Package Declaration*/
package main

/*Import Statement - import fmt, bufio, os, strings package*/
import (
	"fmt"
	"bufio"
	"os"
	"strings"
)

/*Mandatory main function*/
func main() {
	/*Create an input reader variable of type NewReader using stdin*/
	inputReader := bufio.NewReader(os.Stdin)

	/*Prompt the user to enter something*/
	fmt.Printf("\nEnter the main string: ")

	/*Read string using ReadString function*/
	main_str, _ := inputReader.ReadString('\n')

	fmt.Printf("\nEnter the string to be searched inside the main string: ")

	/*Read string using ReadString function*/
	str, _ := inputReader.ReadString('\n')

	/*Use trim function to remove all \n and \r characters*/
	str = strings.Trim(str, "\n\r")

	result := strings.Contains(main_str, str)

	if result == true {
		fmt.Printf("\nThe given string is present in the main string.")

		/*Find the first occurrence*/
		first := strings.Index(main_str, str)

		/*Print first index*/
		fmt.Printf("\n\nFirst Occurrence: %d\n", first)
	} else {
		fmt.Printf("\nThe given string is not present in the main string.\n")
	}
}
```

输出：
![](Image00074.jpg)

## 14.4 修剪字符串

可能需要从字符串中移除不需要的字符。可以使用 `strings` 包中的 `Trim` 函数，如下所示：

```go
<trimmed_string> = strings.Trim(<string>, <character set to be trimmed>)
```

从用户处读取字符串时，`\n` 或 `\r` 或两者都有很大概率被追加到字符串中。可以使用 `Trim` 函数移除这些字符：

```go
new_str = strings.Trim(str, "\n\r")
```

实际上，让我们看看从用户处读取字符串时会发生什么——我们将字符串转换为字符数组来查看每个字符：

```go
/*Pre-trim demo*/
/*Package Declaration*/
package main

/*Import Statement - import fmt, bufio, os, strings package*/
import (
	"fmt"
	"bufio"
	"os"
)

/*Mandatory main function*/
func main() {
	/*Create an input reader variable of type NewReader using stdin*/
	inputReader := bufio.NewReader(os.Stdin)

	/*Prompt the user to enter something*/
	fmt.Printf("\nEnter a string: ")

	/*Read string using ReadString function*/
	str, _ := inputReader.ReadString('\n')

	str_length := len(str)

	fmt.Printf("\nLength: %d", str_length)

	/*Use rune to fetch characters in an array*/
	str_char := []rune(str)

	fmt.Printf("\n\nCharacter array: \n %c \n", str_char)

	for i := 0; i < str_length; i++ {
		fmt.Printf("\nCharacter at index %d ==> %c\n", i, str_char[i])
	}
}
```

输出：
![](Image00075.jpg)

我们输入了单词 Linux，它显然有 5 个字符。但长度显示为 7。此外，在打印字符时，我们在位置 5 和 7 看到了两个空字符。让我们稍微调查一下，看看发生了什么。我们将修改以下语句：

```go
fmt.Printf("\nCharacter at index %d ==> %c\n", i, str_char[i])
```

改为：

```go
fmt.Printf("\nCharacter at index %d ==> %X\n", i, str_char[i])
```

新语句将打印字符的十六进制代码。这是新的输出：
![](Image00076.jpg)

索引 5 处的字符是 D，即 `0x0D`，索引 6 处的字符是 A，即 `0x0A`。如果你在 ASCII 表中核对这些十六进制值，就会意识到这些字符分别是 `\r` 和 `\n`。

让我们使用 `Trim` 函数看看会发生什么。这是新程序：

```go
/*Trim demo*/
/*Package Declaration*/
package main

/*Import Statement - import fmt, bufio, os, strings package*/
import (
	"fmt"
	"bufio"
	"os"
	"strings"
)

/*Mandatory main function*/
func main() {
	/*Create an input reader variable of type NewReader using stdin*/
	inputReader := bufio.NewReader(os.Stdin)

	/*Prompt the user to enter something*/
	fmt.Printf("\nEnter a string: ")

	/*Read string using ReadString function*/
	str, _ := inputReader.ReadString('\n')

	/*Trim to remove unwanted characters*/
	str = strings.Trim(str, "\n\r")

	str_length := len(str)

	fmt.Printf("\nLength: %d", str_length)

	/*Use rune to fetch characters in an array*/
	str_char := []rune(str)

	fmt.Printf("\n\nCharacter array: \n %c \n", str_char)

	for i := 0; i < str_length; i++ {
		fmt.Printf("\nCharacter at index %d ==> %c\n", i, str_char[i])
	}
}
```

输出：
![](Image00077.jpg)

## 14.5 大小写转换

可以分别使用 `ToUpper` 和 `ToLower` 函数将字符串转换为大写和小写。

语法：
```go
<ustring> = strings.ToUpper(<string>)
<lstring> = strings.ToLower(<string>)
```

示例：
```go
str1 = strings.ToUpper(s)
str2 = strings.ToLower(s)
```

下面是一个演示大小写转换的程序：

```go
/*Case conversion demo*/
/*Package Declaration*/
package main

/*Import Statement - import fmt, bufio, os, strings package*/
import (
	"fmt"
	"bufio"
	"os"
	"strings"
)

/*Mandatory main function*/
func main() {
	/*Create an input reader variable of type NewReader using stdin*/
	inputReader := bufio.NewReader(os.Stdin)

	/*Prompt the user to enter something*/
	fmt.Printf("\nEnter a string: ")

	/*Read string using ReadString function*/
	str, _ := inputReader.ReadString('\n')

	/*Trim to remove unwanted characters*/
	str = strings.Trim(str, "\n\r")

	/*Convert to upper and lower case*/
	u_str := strings.ToUpper(str)
	l_str := strings.ToLower(str)

	fmt.Printf("\nOriginal string: %s\nUpper case string: %s\nLower case string: %s\n", str, u_str, l_str)
}
```

输出：
![](Image00078.jpg)

