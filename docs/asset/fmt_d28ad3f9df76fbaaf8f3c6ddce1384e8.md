
```go
package main

import (
    "fmt"
    "regexp"
)

func main() {
    data := `# host.domain.tld #`

    pattern := regexp.MustCompile(
        `\(\\w+).(\\w+).(\\w+)`)

    groups := pattern.FindAllStringSubmatch(
        data, -1)

    fmt.Printf("\n%q\n", groups)
    fmt.Printf("groups[0][0]: %s\n", groups[0][0])
    fmt.Printf("groups[0][1]: %s\n", groups[0][1])
    fmt.Printf("groups[0][2]: %s\n", groups[0][2])
    fmt.Printf("groups[0][3]: %s\n", groups[0][3])
}
```

下方的输出首先展示了整个匹配，随后展示了各个独立组。

```
[["host.domain.tld" "host" "domain" "tld"]]
groups[0][0]: host.domain.tld
groups[0][1]: host
groups[0][2]: domain
groups[0][3]: tld
```

# 第 8.3 章：命名捕获组

当正则表达式变得复杂时，通过名称记录和引用每个捕获组的用途是非常有帮助的。由于组名和位置是固定的，可以使用 `regexp.Regexp.SubexpNames()` 方法引用它们。切片中的组索引与 `regexp.Regexp.FindStringSubmatch()` 方法返回的切片中的相应索引匹配，然后用于构建映射，如下面的示例所示。

此示例首先识别数据集，然后使用 `regexp.MustCompile()` 函数定义模式。该模式使用 `\w+` 语法来匹配点号两侧的一个或多个单词字符。由于使用了命名捕获组，每个模式都用 `(?P<name>re)` 语法定义，其中 `name` 是捕获组名称。然后，使用数据集作为输入，调用 `regexp.Regexp.FindStringSubmatch()` 方法以返回一个切片，其中第一个切片值是最左侧的匹配。接下来，创建一个映射来保存结果，然后遍历由 `regexp.Regexp.SubexpNames()` 方法返回的切片，该方法返回每个括号子表达式的名称。在遍历每个名称时，检查子表达式名称以确保其不为空。如果名称有效，则使用该名称作为键，对应的子匹配索引值作为值来创建映射条目，最后打印出新的映射。

```go
package main

import (
  "fmt"
  "regexp"
)

func main() {
  dat := `# host.domain.tld #`
  pat := regexp.MustCompile(
	`(?P<third>\w+).(?P<sec>\w+).(?P<first>\w+)`)

  mch := pat.FindStringSubmatch(dat)

  res := make(map[string]string)

  for i, name := range pat.SubexpNames() {
	if i != 0 && name != "" {
			res[name] = mch[i]
	}
  }

  ff := fmt.Printf
  ff("\n%\n", res)
  ff("res[\"first\"]: %s\n", res["first"])
  ff("res[\"sec\"]: %s\n", res["sec"])
  ff("res[\"third\"]: %s\n", res["third"])
}
```

下方的输出首先展示了整个匹配，随后展示了在结果映射中通过命名匹配键引用的每个值。

```
map["third":"host" "sec":"domain" "first":"tld"]
result["first"]: tld
result["sec"]: domain
result["third"]: host
```

# 第 8.4 章：模板展开

模板展开捕获正则表达式模式匹配并将其展开为字符串模板。此示例演示了通过 `regexp.Regexp.ExpandString()` 方法使用模板展开，该方法将正则表达式的一组匹配展开到模板中。

示例开始后，识别数据集作为源，然后使用 `regexp.MustCompile()` 函数定义模式。该模式使用 `\w+` 语法来匹配点号两侧的一个或多个单词字符。接下来，定义字符串模板。它通过添加美元符号前缀将命名匹配作为变量。然后，遍历由 `regexp.Regexp.FindAllStringSubmatchIndex()` 方法返回的每个匹配行。每个匹配随后使用 `regexp.Regexp.ExpandString()` 方法展开到模板中以产生输出。

```go
package main

import (
    "fmt"
    "regexp"
)

func main() {
    src := `
host1.domain.tld some text
host2.domain.tld more text
`

    re := regexp.MustCompile(
        `(?m)(?P<thir>\w+).(?P<sec>\w+).(?P<fir>\w+)\s(?P<text>.*?)$`)

    tpl := "$thir.$sec.$fir.\tIN\tTXT\t\"$text\"\n"
```

# 第 8.5 章：多行分隔符拆分

多行分隔符拆分对于提取由特定模式分隔的文本行非常有用，例如配置文件中的各个部分。它可以用于实现清单管理、审计或配置管理。多行 `m` 标志使得 `^` 和 `$` 正则表达式语法能够额外匹配每一行的开头和结尾。

本示例将定义好的配置拆分为一个二维切片，其中由 `!` 字符分隔的每个配置部分都由其自己的切片表示。随后，配置中的每一行将作为各自配置部分切片中的一个字符串表示。

首先，定义配置，然后使用 `regexp.MustCompile()` 函数中的模式作为参数，返回一个 `regexp.Regexp` 对象。接着，对该对象调用 `regexp.Regexp.Split()` 方法，使用配置和 `-1` 来处理无限次匹配。该方法将配置拆分为一个单一切片，其中每个值是模式匹配之间剩余的内容。

在初始化二维切片后，迭代遍历从拆分配置中返回的值。最后，在循环内，使用 `strings.TrimSuffix()` 函数修剪末尾的换行符，然后按换行符分割每个字符串，返回并追加一个新切片，其中包含由分割每一行产生的值。

```go
package main

import (
    "fmt"
    "regexp"
    "strings"
)

func main() {
    config := `int Vlan1
        desc v1
! int Vlan2
    desc v2
`
    a := regexp.MustCompile("(?m)\n^!\$\n")
    m := a.Split(config, -1)

    arr := [][]string{}

    for _, s := range m {
        s := strings.TrimSuffix(s, "\n")
        m := strings.Split(s, "\n")

        arr = append(arr, m)
    }

    fmt.Printf("%q\n", arr)
}
```

输出使用双引号和括号来展示结果。

```
[["int Vlan1\n    desc v1"] ["int Vlan2\n    desc v2"]]
```

# 第 9 章：外部命令

执行外部命令利用了 `exec` 包来封装 `os.StartProcess` 函数，这使得重新映射终端的 `stdout` 和 `stderr` 管道变得更加容易。虽然 `exec.Command()` 函数用于外部命令时很直接，但必须小心处理终端重定向。

本章通过示例展示如何合并 `stderr` 和 `stdout`，以及如何将两者分开。能够原生处理重定向选择有助于提高代码的简洁性和可读性。

本章将涵盖以下外部命令主题：

- 合并 Stdout/Stderr
- 分离 Stdout/Stderr

## 第 9.1 章：合并 Stdout/Stderr

`exec` 包支持在命令执行后合并终端的标准输出和标准错误。这种合并的输出可以简化输出处理并节省几个步骤。

将设置一个场景来演示，创建两个文件；一个是可写的，另一个则移除了写权限。使用 `cat` 命令，我们将读取每个文件，并期望看到来自可读文件 `r.txt` 的标准输出和来自不可读文件 `w.txt` 的标准错误。

```
$ touch r.txt w.txt
$ echo hi from r.txt > r.txt
$ chmod a-r w.txt
```

首先，命令和参数作为单独的字符串参数输入到 `exec.Command()` 函数中，该函数返回一个 `exec.Cmd` 对象。接着，调用 `exec.Cmd.CombinedOutput()` 方法来执行命令并返回合并的标准输出和错误。最后，打印返回的字节切片。

```go
package main

import (
    "fmt"
    "os/exec"
)

func main() {
    cmd := exec.Command("cat", "r.txt", "w.txt")
    data, _ := cmd.CombinedOutput()

    fmt.Printf("%s", data)
}
```

请注意，输出首先显示来自可读文件 `r.txt` 的标准输出文本，然后是来自不可读文件 `w.txt` 的错误文本。

```
hi from r.txt
cat: w.txt: Permission denied
```

## 第 9.2 章：分离 Stdout/Stderr

本示例将展示如何执行命令并将标准终端输出和错误分开。`exec` 包轻松地执行外部命令，并通过其原生函数区分标准输出和标准错误。

与上一节类似，将设置一个场景进行演示。创建两个文件；一个是可写的，另一个则移除了写权限。使用 `cat` 命令，我们将读取每个文件，并期望看到来自可读文件 `r.txt` 的标准输出和来自不可读文件 `w.txt` 的标准错误。

```
$ touch r.txt w.txt
$ echo hi from r.txt > r.txt
$ chmod a-r w.txt
```

首先，命令和参数作为单独的字符串参数输入到 `exec.Command()` 函数中，该函数返回一个 `exec.Cmd` 对象。接着，分配将在命令启动时连接到终端标准输出和错误的管道。然后，使用 `exec.Cmd.Start()` 方法启动命令，并调用 `ioutil.ReadAll()` 函数读取管道返回的 `io.ReadCloser` 对象，之后打印输出。最后，使用 `exec.Cmd.Wait()` 方法在看到命令退出后关闭管道。

```go
package main

import (
    "fmt"
    "io/ioutil"
    "os/exec"
)

func main() {

    cmd := exec.Command("cat", "r.txt", "w.txt")

    stdoutpipe, _ := cmd.StdoutPipe()
    stderrpipe, _ := cmd.StderrPipe()

    _ = cmd.Start()

    stdout, _ := ioutil.ReadAll(stdoutpipe)
    stderr, _ := ioutil.ReadAll(stderrpipe)

    fmt.Printf("stdout: %s\nstderr: %s\n", stdout, stderr)

    _ = cmd.Wait()
}
```

输出首先显示来自可读文件 `r.txt` 的标准输出文本，然后是来自不可读文件 `w.txt` 的错误文本。

```
stdout: hi from r.txt
stderr: cat: w.txt: Permission denied
```

# 第 10 章：CLI 应用程序助手

CLI 应用程序助手在命令行应用程序中用作构建模块。它们有助于快速轻松地构建交互式程序。

本章将介绍读取数据的三种不同方法。演示了敏感和非敏感数据的用户输入提示，接着是用于内联参数的命令行参数和标志。最后，检查列格式化的输出，以展示一种呈现数据的有效模式。

本章将涵盖以下 CLI 应用程序助手主题：

- 用户输入
- 命令行参数
- 命令行标志
- 列格式化

## 第 10.1 章：用户输入

从终端读取用户输入通常需要读取敏感和非敏感数据。本示例接受用户名和密码来演示这两种情况。为了简洁，将使用 `terminal.ReadPassword()` 函数从终端读取敏感的密码文本，而不进行本地回显。对于非敏感输入，将使用 `bufio.Reader.ReadString()` 方法。

本示例通过用 `bufio.NewReader()` 函数封装 `os.Stdin` 返回一个带缓冲的 `bufio.Reader` 对象，从而开始读取非敏感的用户名输入。然后，打印提示，并调用 `bufio.Reader.ReadString()` 方法，同时使用换行符作为参数。这将返回换行符之前的输入字符串。接下来，打印敏感密码提示，并使用 `syscall.Stdin` 作为参数调用 `terminal.ReadPassword()` 函数，以禁用本地回显并获取密码。最后，打印用户名和密码作为验证。

```go
package main

import (
    "bufio"
    "fmt"
    "golang.org/x/crypto/ssh/terminal"
    "os"
    "syscall"
)

func main() {

    reader := bufio.NewReader(os.Stdin)

    fmt.Print("Enter username: ")
    user,_ := reader.ReadString('\n')
    
    // 注意：原文 OCR 文本在此处结束，但通常后续会有：
    // user = strings.TrimRight(user, "\n")
    // fmt.Print("Enter password: ")
    // password, _ := terminal.ReadPassword(int(syscall.Stdin))
    // fmt.Println("Username:", user)
    // fmt.Println("Password:", string(password))
}
```

```go
fmt.Print("Enter password: ")

pass, _ := terminal.ReadPassword(
    int(syscall.Stdin))

fmt.Printf("\n\nUsername: %sPassword: %s\n", user, string(pass))

}
```

输出结果会显示用户名和密码的提示符，然后展示如下结果的输出。为了避免他人窥视，用户输入密码时不会显示该密码。

Enter username: John Doe

Enter password:

Username: John Doe

Password: $ecret

## 第 10.2 章：命令行参数

命令行参数是为程序执行添加参数的一种常见方法。本示例利用了 `os.Args` 切片，其中包含每个命令行参数，第一个值是正在执行的程序名称，其余为参数。

在示例程序中，只允许两种用户操作：添加或删除。因此，只接受三个参数：（1）程序本身，（2）关键字“add”或“del”，（3）被操作的项目。

首先，通过检查长度是否不等于 3 来验证命令行参数的总数，如果不符合，则打印帮助对话框并退出程序。接下来，由于“add”或“del”关键字是第二参数中仅有的两个可接受值，因此使用 switch 和 case 语句对第二参数进行判断，执行相应的操作，否则显示帮助对话框并退出。

```go
package main
import (
    "fmt"
    "os"
)

func main() {
    if len(os.Args) != 3 {
        fmt.Printf(
            "usage: %s add|del \n", os.Args[0])
        os.Exit(1)
    }
    switch os.Args[1] {
    case "add":
        fmt.Println("adding item")
    case "del":
        fmt.Println("deleting item")
    default:
        fmt.Printf(
            "usage: %s add|del \n", os.Args[0])
        os.Exit(1)
    }
}
```

## 第 10.3 章：命令行标志

命令行标志是指定命令行程序选项的另一种常见方法。本示例使用 `flag` 包来演示参数解析，并解析 int、bool 和 string 类型。默认情况下，`flag` 包会接受 "-h" 或 "--help" 标志以显示帮助对话框。如果未输入标志值，则默认值（定义为标志的第二个参数）将被分配。
