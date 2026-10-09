# 网络运维 Go 编程：Golang 网络自动化手册

# 用于网络运维的 Go 编程

## Golang 网络自动化指南

### Tom McAllen, CCIE 26867

## 关于作者

**Tom McAllen** 是一位拥有超过二十年编程和网络运维经验的开发人员和网络专家。他的职业生涯始于 Linux 系统管理员和 Web 应用开发人员，在 Merit Network 和北美网络运营人员组（NANOG）实习后，他完成了计算机科学学士学位和技术管理硕士学位。Tom 还持有十多项活跃的技术认证，包括思科认证互联网专家（CCIE）和认证信息系统安全专家（CISSP）。目前，他在德克萨斯州奥斯汀的一家财富全球 500 强企业担任高级首席网络工程师。

## 前言

Go 是近几十年出现的最令人兴奋的新主流编程语言。与现代网络运维一样，Go 瞄准了 21 世纪的基础设施，特别是在云计算领域。本书展示了如何将 Go 编程应用于网络运维。书中通过旨在充当指南和参考的示例，涵盖了常见用例。

假设读者已经对 Go 编程有了基本了解；然而，示例仍提供了额外的澄清说明。重点在于使用 Go 进行网络运维，而非语言本身。本书的方法注重实用；鼓励读者尝试示例并自行组合程序以获得实践经验。

本书中的示例是为电子书格式设计的。它们简短而简洁，同时保留了足够的内容来运行并说明要点。虽然为了简洁起见省略了错误处理，但在开发生产代码时，始终建议包含它以及其他最佳实践。

## 为什么选择 Go 进行网络运维？

Go 编程语言是由 Google 内部团队于 2009 年发布的现代语言。作为一种工程化设计的语言（而非随时间演变的语言），Go 具有几个关键优势。它使用了简洁且易于理解的语法，避免了像 C++ 等其他语言的复杂性。它是静态类型的，但通过支持简短变量声明、接口和结构类型，既高效又灵活。

另一个关键优势是内置于语言核心的并发特性。Go 的并发模型通过利用 goroutine 和 channel 简单而有效，而非使用效率较低的线程。并发是语言原生支持的，并随着 CPU 核心数量的增加而高效扩展。

Go 轻量且快速。它直接编译为二进制文件，而不依赖于解释器。这释放了直接在底层硬件上运行的性能，同时通过其固有的垃圾回收机制减少了开销。编译速度快；因此，在通常使用解释型语言的情况下使用它是可行的。它方便地编译为单个二进制文件，并可以交叉编译到多种操作系统和架构，包括 MacOS、Linux、Windows 和 BSD。

Go 的流行度和采用率的上升清楚地展示了其在现实 IT 世界中的益处。从一开始就工程化集成到语言中的下一代功能，可以增加依赖其进行生产使用的信心。随着网络继续演变，公司越来越多地关注可编程性和自动化以应对新挑战，网络运维必须使用现代工具集保持敏捷。

## 第 1 章：文件和目录基础

文件和目录是大多数操作系统的基本功能。能够操作和解释它们是必备技能。本章专注于几个演示基本文件和目录操作的示例。

首先，本节查看打开和关闭以及添加和删除文件的基础知识。然后，它介绍获取文件的属性，如大小、权限、所有权和修改日期。最后，最后两节演示列出文件和目录，包括在同一目录中以及递归地列出。

本章将涵盖以下文件和目录主题：

- 打开和关闭
- 添加和删除
- 获取信息
- 列出目录内容
- 遍历文件和目录树

## 第 1.1 章：打开/关闭

打开文件主要有两个选项：`os.Open()` 函数，它只接受文件名并提供一个只读文件；以及一个更增强的选项 `os.OpenFile()` 函数，该函数通过实现下表所示的标志提供了更多控制。这些标志可以通过使用逻辑 OR 管道运算符分隔来组合使用。

| 标志 | 描述 |
|---|---|
| O_RDONLY | 以只读方式打开文件。 |
| O_WRONLY | 以只写方式打开文件。 |
| O_RDWR | 以读写方式打开文件。 |
| O_APPEND | 写入时向文件追加数据。 |
| O_CREATE | 如果文件不存在，则创建新文件。 |
| O_EXCL | 与 O_CREATE 一起使用。文件必须不存在。 |
| O_SYNC | 以同步 I/O 方式打开。 |
| O_TRUNC | 如果可能，打开时截断文件。 |

下面的示例通过使用 `os.OpenFile()` 函数返回一个 `os.File` 类型值的指针，演示了更增强的选项。该标志组合在没有文件时创建一个只写文件，否则向文件追加内容。然后，在 `os.File` 对象上调用 `os.File.Write()` 方法以向文件追加一个字节切片。最后，在 `os.File` 对象上调用 `os.File.Close()` 方法以使 I/O 无法使用。

```go
package main

import "os"

func main() {
    file,_ := os.OpenFile("file.txt",
    os.O_APPEND|os.O_CREATE|os.O_WRONLY, 0644)
}
```





```
file.Write([]byte("append data\n"))

file.Close()
}
```

## 1.2 章：添加/删除

下一个示例演示了如何添加一个目录和文件，然后删除它们。示例首先声明了一个目录路径和文件名。然后，利用该目录路径并设置权限位，使用 os.MkdirAll() 函数创建名为 path 的目录。一旦目录创建完成，通过调用 filepath.Join() 函数并结合路径名，构建完整的目录路径。然后，将该完整路径作为参数传递给 os.Create() 函数，以创建文件并返回一个 os.File 对象。此时，调用 os.File.Close() 方法关闭文件，并使用 os.Remove() 函数将其删除。最后，使用 os.RemoveAll() 函数删除该目录，该函数会移除路径及其所有依赖的子项。

```
package main

import (
    "os"
    "path/filepath"
)

func main() {
    dpath := "/dir"
    fname := "file.txt"

    _ = os.MkdirAll(dpath, 0777)

    fpath := filepath.Join(dpath, fname)

    file, _ := os.Create(fpath)

    file.Close()

    _ = os.Remove(fpath)

    _ = os.RemoveAll(dpath)
}
```

## 1.3 章：获取信息

使用 os 包从文件和目录中获取信息非常简单。此示例利用 os.Stat() 函数返回一个 os.FileInfo 对象，然后使用它来读取各种属性，包括文件名、大小、权限、最后修改时间戳以及是否为目录。os.FileInfo 对象随后用于调用相应的方法来检索文件和目录的元数据。

```
package main

import (
    "fmt"
    "os"
)

func main() {
    file, _ := os.Stat("main.go")

    fl := fmt.Println
    fl("File name: ", file.Name())
    fl("Size in bytes: ", file.Size())
    fl("Last modified: ", file.ModTime())
    fl("Is a directory: ", file.IsDir())

    ff := fmt.Printf
    ff("Permission 9-bit: %s\n", file.Mode())
    ff("Permission 3-digit: %6o\n", file.Mode())
    ff("Permission 4-digit: %04o\n",file.Mode())
}
```

在下面的输出中，有三种不同的权限表示形式，它们采用标准的 Unix 9 位格式、3 位八进制和 4 位八进制格式。这些权限位是使用 fmt 包的字符串和基数整数动词格式化而成。此外，请注意 os.FileInfo.ModTime() 方法返回一个 time.Time 对象，这非常适合进一步的解析和格式化。

```
File name: main.go
Size in bytes: 0
Last modified: 2018-10-20 10:51:12.305 -0500 EDT
Is a directory: false
Permission bits: -rwxr--r--
Permission 3-digit octal: 744
Permission 4-digit octal: 0744
```

## 1.4 章：列出目录内容

使用 ioutil 包中的任一 I/O 实用函数可以实现列出特定目录内的目录内容。通过在 ioutil.ReadDir() 函数中指定目录名称，它方便地返回一个 os.FileInfo 对象列表，如前一节所示。

在此示例中，使用句点符号来表示当前工作目录，作为 ioutil.ReadDir() 函数的输入。然后，对一个返回 os.FileInfo 对象列表的切片进行循环。最后，循环遍历并利用每个 os.FileInfo.Name() 和 os.FileInfo.ModTime() 方法打印名称和最后修改时间戳。

```
package main

import (
    "fmt"
    "io/ioutil"
)

func main() {
    files, _ := ioutil.ReadDir(".")

    for _, file := range files {
        fmt.Println(file.Name(), file.ModTime())
    }
}
```

请注意，下方的输出是故意按文件名排序的。这是 ioutil.ReadDir() 函数的固有特性。

```
file1.txt 2018-10-20 14:21:11.1 -0500 EDT
file2.txt 2018-10-20 14:22:22.1 -0500 EDT
```

## 1.5 章：遍历文件树

从指定的起始点递归地遍历文件树，可用于在目录结构中查找和收集数据或修改特定文件。来自 filepath 包的 filepath.Walk() 函数启用了此功能。它接受一个根目录和一个用于处理文件和目录的函数；符号链接不会被跟踪。

为了演示文件树遍历，下面的示例首先通过设置一个函数作为值开始。然后，它使用 os.FileInfo 对象调用 os.FileInfo.IsDir() 方法来确定该条目是否为目录，并打印结果以及相应的路径。最后，该函数与根目录一起作为参数设置到 filepath.Walk() 函数中。在执行过程中，初始扫描函数会被 filepath.Walk() 函数访问的每个文件或目录调用。

```
package main

import (
	"fmt"
	"os"
	"path/filepath"
)

func main() {
	scan := func(
		path string, i os.FileInfo, _ error) error {
		fmt.Println(i.IsDir(), path)
		return nil
	}

	_ = filepath.Walk("", scan)
}
```

下方的输出是故意按字典顺序列出的。这种排序是 filepath.Walk() 函数的固有特性。

```
false main.go
true dir1
false dir1/file1.txt
false dir1/file2.txt
```

# 第 2 章：读写文件类型

读写不同的文件类型是许多程序中的关键要素。本章将讲解读取和写大多数环境中常见文件类型的示例；这些包括纯文本、CSV、YAML、JSON 和 XML。

几个示例将利用缓冲区来优化读取或写入操作，并最小化昂贵的系统调用。缓冲区将用于存储数据，直到达到一定大小后才进行写入，并在读取时通过单次操作检索更多数据。

本章将涵盖以下主题：

- 纯文本
- CSV
- YAML
- JSON
- XML

## 2.1 章：纯文本

读写纯文本通常是逐行或逐词进行的。以下子章节中的示例将演示如何使用原生缓冲区逐行读写文本。

在处理大文件时，利用缓冲区会很有帮助，因为它在将数据提交给 IO 之前会存储数据直到达到一定大小；这减少了昂贵的系统调用次数以及其他相关机制的开销。

本子章节将涵盖以下主题：

- 读取纯文本文件
- 写入纯文本文件

### 2.1.1 章：读取纯文本

bufio 包的 Scanner 是一个方便的接口，用于从文件中逐行或逐词读取文本。原生缓冲区通过单次操作检索更多数据来优化读取操作。此示例演示了如何从下面的纯文本文件中逐行读取文本。

```
RTR1 1.1.1.1
RTR2 2.2.2.2
RTR3 3.3.3.3
```

首先，使用 os.Open() 函数以只读模式打开上述纯文本文件，然后返回一个指向 os.File 类型值的指针。接下来，调用 bufio.NewScanner() 函数，以 os.File 对象作为参数，返回一个用于调用 bufio.Scanner.Split() 方法的 bufio.Scanner 对象。

由于目标是读取每一行文本，bufio.ScanLines 被用作 bufio.Scanner.Split() 方法的输入，然后使用 bufio.Scanner.Scan() 方法将扫描器推进到每一新行。每当推进到新的一行时，每次迭代都会通过 bufio.Scanner.Text() 方法访问，然后追加到切片中并在最后打印。最后，在 os.File 对象上调用 os.File.Close() 方法以关闭文件，然后一个循环遍历并打印切片中的每个值。

```
package main

import (
    "bufio"
    "fmt"
    "os"
)

func main() {
    file, _ := os.Open("./file.txt")

    scanner := bufio.NewScanner(file)

    scanner.Split(bufio.ScanLines)

    var lines []string

    for scanner.Scan() {
        lines = append(lines, scanner.Text())
    }

    file.Close()

    for _, line := range lines {
        fmt.Println(line)
    }
}
```

输出将逐行显示，正如从文件中读取的那样。

```
RTR1 1.1.1.1
RTR2 2.2.2.2
RTR3 3.3.3.3
```





## 2.1.2 章：编写纯文本

`bufio` 包提供了一个高效的缓冲写入器（Writer），可用于将数据写入文件。缓冲写入器会累积字节，直到达到阈值，然后完成写入操作以最小化资源消耗。本示例将通过逐步讲解，演示如何将字符串切片逐行写入纯文本文件。

以下示例首先定义了一个表示为字符串切片的示例数据。示例数据中的每个值都将写入文件中的一新行。首先，使用标志组合调用 `os.OpenFile()` 函数，如果文件不存在则创建一个仅可写文件，并在写入时向文件追加内容。将 `os.OpenFile()` 函数返回的 `os.File` 对象作为 `bufio.NewWriter()` 函数的输入，即可获得一个新的 `bufio.Writer` 对象。接着，遍历该切片，使用 `bufio.Writer.WriteString()` 方法将每个值写入文件，并添加每一新行。最后，使用 `bufio.Writer.Flush()` 方法将剩余的缓冲数据写入文件，并使用 `os.File.Close()` 方法关闭文件。

```go
package main

import (
	"bufio"
	"os"
)

func main() {
	lines := []string{"RTR1 1.1.1.1",
		"RTR2 2.2.2.2",
		"RTR3 3.3.3.3"}

	file, _ := os.OpenFile("./file.txt",
		os.O_APPEND|os.O_CREATE|os.O_WRONLY, 0644)

	writer := bufio.NewWriter(file)
	for _, line := range lines {
		_, _ = writer.WriteString(line + "\n")
	}

	writer.Flush()

	file.Close()
}
```

## 2.2 章：CSV

逗号分隔值（CSV）是一种常用于导入、导出和存储数据的格式。它也常用于在不兼容的格式之间移动表格数据。

`csv` 包支持 RFC 4180 中描述的标准格式。每个 CSV 文件包含零行或多行，每行包含一个或多个字段，且遵循以下识别出的约束：

- 空行将被忽略。
- 空白字符被视为字段的一部分。
- 每一行由换行符分隔。
- 换行符前的回车符会被移除。
- 引号内的字段中可以包含换行符、空格和逗号。
- 引号内的引号本身如果不被引号包围，则不包含在字段中。

本小节将涵盖以下主题：

- 读取 CSV 文件
- 编写 CSV 文件

### 2.2.1 章：读取 CSV

`csv` 包包含一个 `NewReader()` 函数，该函数返回一个用于处理 CSV 记录的 Reader 对象。`csv.Reader` 会将输入中的所有 '\n' 序列转换为仅为 \n，包括多行字段值。

下面的 CSV 文件包含三列，一个带有标签的标题行，以及两行数据。本示例将演示如何读取 CSV 文件并打印每个对应的单元格值。

以下是以表格形式查看的 CSV 文件。

| 主机 | IP 地址 | 位置 |
| :--- | :--- | :--- |
| RTR1 | 1.1.1.1 | 西雅图, 华盛顿 |
| RTR2 | 2.2.2.2 | 内华达, 内华达州 |

以下是在文本编辑器中以纯文本形式查看的上述相同 CSV 文件。

```text
HOST,IP ADDR,LOCATION
RTR1,1.1.1.1,"Seattle, WA"
RTR2,2.2.2.2,"Nevada, NV"
```

在本示例中，使用 `os.Open()` 函数以只读模式打开文件，该函数返回一个 `os.File` 实例。接着，将 `os.File` 对象作为参数传递给 `csv.NewReader()` 函数，该函数返回一个缓冲的 `csv.Reader` 对象。然后，使用 `csv.Reader.Read()` 方法将每个文件记录解码到结构体中，并将它们存储在一个切片中，直到返回 `io.EOF`，表明已达到文件末尾。最后，切片遍历每个值。

```go
package main

import (
	"encoding/csv"
	"fmt"
	"io"
	"os"
)

type Row struct {
	ColA, ColB, ColC string
}

func main() {
	file, _ := os.Open("file.csv")

	reader := csv.NewReader(file)

	rows := []Row{}

	for {
		row, err := reader.Read()
		if err == io.EOF {
			break
		}

		rows = append(rows, Row{
			ColA: row[0], ColB: row[1], ColC: row[2],
		})
	}
	for _, row := range rows {
		fmt.Printf("%s -- %s -- %s\n",
			row.ColA, row.ColB, row.ColC)
	}
}
```

### 2.2.2 章：编写 CSV

`csv` 包包含一个 `NewWriter()` 函数，该函数返回一个用于写入 CSV 记录的 Writer 对象。`csv.Writer` 写入以换行符结尾的记录，并使用逗号作为字段分隔符。本示例演示如何将数据写入 CSV 文件。

以下示例首先将示例数据格式化为二维切片。然后，使用 `os.Create()` 函数创建文件，如果文件已存在则将其截断，并返回一个 `os.File` 对象实例。接着，将 `os.File` 实例作为参数传递给 `csv.NewWriter()` 函数，以获得一个缓冲的 `csv.Writer` 对象。然后，调用 `csv.Writer.Write()` 方法将每个字符串切片作为 CSV 记录写入文件。最后，使用 `csv.Writer.Flush()` 方法将剩余的缓冲数据刷新到潜在的 `csv.Writer` 中，并使用 `os.File.Close()` 方法关闭文件。

```go
package main

import (
	"encoding/csv"
	"os"
)

func main() {
	rows := [][]string{
		{"HOST", "IP ADDR", "LOCATION"},
		{"RTR1", "1.1.1.1", "Seattle, WA"},
		{"RTR2", "2.2.2.2", "Nevada, NV"}
	}

	file, _ := os.Create("file.csv")

	writer := csv.NewWriter(file)

	for _, row := range rows {
		_ = writer.Write(row)
	}

	writer.Flush()

	file.Close()
}
```

以下是以表格形式查看生成的文件。

| 主机 | IP 地址 | 位置 |
| :--- | :--- | :--- |
| RTR1 | 1.1.1.1 | 西雅图, 华盛顿 |
| RTR2 | 2.2.2.2 | 内华达, 内华达州 |

以下是以纯文本形式在文本编辑器中查看的相同文件。

```text
HOST,IP ADDR,LOCATION
RTR1,1.1.1.1,"Seattle, WA"
RTR2,2.2.2.2,"Nevada, NV"
```

## 2.3 章：YAML

YAML Ain't Markup Language（YAML）是一种流行的格式，通常用于读取和写入配置文件。它也可以用于转换数据并支持兼容性。

YAML 具有人类友好的布局，并支持易于遵循的语法。通常，冒号用于键值对，缩进用于嵌套，连字符用于列表成员。

`yaml.v2` 包与大多数 YAML 1.1 和 1.2 兼容。它通常被用作解析和生成 YAML 格式数据的快速且可靠的首选包。

本小节将涵盖以下主题：

- 读取 YAML 文件
- 编写 YAML 文件

### 2.3.1 章：读取 YAML

`yaml.v2` 包支持一个 `Unmarshal()` 函数，该函数将数据从字节切片解码为值。如果解码的值被赋值给结构体字段，则字段名必须是导出的，因此首字母必须大写；使用 "yaml" 结构体字段标签定义自定义键。

在这个简单示例中，使用 `yaml.Unmarshal()` 函数将以下 YAML 文件中的数据解码到结构体中。

```yaml
host: localhost
ports:
 - 80
 - 443
```

首先，定义一个结构体，首字母大写，并使用 "yaml" 字段标签来识别键。然后，使用 `ioutil.ReadFile()` 函数读取文件，该函数返回一个字节切片，并使用 `yaml.Unmarshal()` 函数将数据解码到结构体实例中。最后，打印结构体实例的成员值，以展示解码后的 YAML 文件。

```go
package main

import (
	"fmt"
	"gopkg.in/yaml.v2"
	"io/ioutil"
)

type Config struct {
	Host  string `yaml:"host"`
	Ports []int  `yaml:"ports"`
}

func main() {
	data, _ := ioutil.ReadFile("file.yaml")
	conf := Config{}
	_ = yaml.Unmarshal(data, &conf)
	fmt.Printf("%s:%d\n", conf.Host, conf.Ports)
}
```

以下输出显示每个值在冒号的两侧格式化。

```text
localhost:[80,443]
```

### 2.3.2 章：编写 YAML

`yaml.v2` 包支持一个 `Marshal()` 函数，该函数用于将值序列化为 YAML 格式。虽然通常使用结构体来支持这些值，但也接受映射和指针。只有当结构体字段是导出的（即首字母大写）时才会被序列化。使用 "yaml" 结构体字段标签定义自定义键。

在本示例中，使用 `yaml.Marshal()` 函数将结构体中的数据序列化并写入到 YAML 格式的文件中。首先，定义一个结构体，首字母大写，并使用 "yaml" 字段标签来识别文件中的键。接着，用值初始化结构体，并使用 `yaml.Marshal()` 函数进行序列化。最后，接收序列化后的 YAML 格式字节切片，并使用 `ioutil.WriteFile()` 函数将其写入文件。

```go
package main

import (
	"gopkg.in/yaml.v2"
	"io/ioutil"
)

type Config struct {
	Host  string `yaml:"host"`
	Ports []int  `yaml:"ports"`
}

func main() {
	conf := Config{
		Host:  "localhost",
		Ports: []int{80, 443},
	}

	data, _ := yaml.Marshal(&conf)
}
```





_ = ioutil.WriteFile("file.yaml", data, 0644)
}

以下输出展示了示例中创建的文件，其中包含以 YAML 格式写入的各个值。

```
host: localhost
ports:
 - 80
 - 443
```

## 第 2.4 章：JSON

JavaScript 对象表示法（JSON）是一种数据交换格式，通常用于 Web 前端与后端服务器以及移动应用之间。大多数现代网络设备支持交换 JSON 编码数据的 REST 接口。

json 包支持读取和写入 RFC 7159 中定义的 JSON 格式。必须遵守一些特定的 Go 语言规则：

- 导出的结构体字段必须以大写字母开头。
- JSON 对象仅支持字符串作为键。
- 函数、通道和复数类型不会被编码。
- 不支持循环数据结构。
- 指针在编码前会被解引用。

本章将涵盖以下主题：

- 读取 JSON 文件
- 写入 JSON 文件

### 第 2.4.1 节：读取 JSON

json 包包含一个 Unmarshal() 函数，支持将字节切片中的数据解码为值。如果解码后的值被赋值给结构体字段，则字段名必须是导出的，因此首字母必须大写；使用 "json" 结构体字段标签可以自定义键。

在这个示例中，使用 json.Unmarshal() 函数将以下 JSON 格式文件中的值解码到结构体中。

```json
{
  "total": 3,
  "devices": [
    "SW1",
    "SW2",
    "SW3"
  ]
}
```

首先，定义一个与 JSON 文件中的数据对应的结构体。然后，使用 "json" 字段标签来标识各个键。接下来，使用 ioutil.ReadFile() 函数读取文件，该函数返回一个字节切片，该切片通过 json.Unmarshal() 函数解码到结构体实例中。最后，打印结构体实例的成员值，以演示 JSON 文件已被解码。

```go
package main

import (
  "encoding/json"
  "fmt"
  "io/ioutil"
)

type Inventory struct {
Total int `json:"total"`
Devices []string `json:"devices"`
}

func main() {
    data, _ := ioutil.ReadFile("file.json")

    inv := Inventory{}

    _ = json.Unmarshal([]byte(data), &inv)

    fmt.Printf("Total: %d\nDevices: %q\n",
               inv.Total, inv.Devices)
}
```

输出显示冒号右侧的每个值，旁边是对应的标签。为清晰起见，设备保持字符串切片格式。

Total: 3
Devices: ["SW1" "SW2" "SW3"]

### 第 2.4.2 节：写入 JSON

json 包支持 Marshal() 函数，用于将值序列化为 JSON 格式。虽然通常使用结构体来分组值，但也接受 maps。只有导出的结构体字段（因此首字母为大写）才会被序列化。使用 "json" 结构体字段标签可以自定义键。

在这个示例中，使用 json.Marshal() 函数将结构体中的值序列化并写入 JSON 格式的文件。首先，定义一个首字母大写并带有 "json" 字段标签的结构体，以标识文件中的键。初始化结构体值，然后使用 json.Marshal() 函数进行序列化。最后，接收序列化后的 JSON 格式字节切片，并将其写入文件，使用 ioutil.WriteFile() 函数。

```go
package main

import (
	"encoding/json"
	"fmt"
)

type Inventory struct {
	Total int `json:"total"`
	Devices []string `json:"devices"`
}

func main() {
	data := &Inventory{
		Total: 3,
		Devices: []string{"SW1", "SW2", "SW3"},
	}

	inv, _ := json.MarshalIndent(data, "", "  ")

fmt.Println(string(inv))
}
```

输出显示一个文件，其中每个值均以 JSON 格式呈现。虽然此处将 JSON 格式数据写入文件以展示其功能，但将 JSON 格式数据写入 REST API 也很常见，如第 4.2 章稍后所示。

```json
{
"total": 3,
"devices": [
"SW1",
"SW2",
"SW3"
]
}
```

## 第 2.5 章：XML

可扩展标记语言（XML）是一种标记语言，通常用作 Web 服务中的数据通信格式。由于其紧凑的结构，这种简化格式通常比 JSON 更受欢迎。

xml 包支持读取和写入 XML 1.0。由于 XML 形成树状数据结构，可以使用 Go 中的结构体以类似的层级结构进行定义。后续小节中的示例将利用结构体来编码和解码 XML。

本章将涵盖以下主题：

- 读取 XML 文件
- 写入 XML 文件

### 第 2.5.1 节：读取 XML

xml 包包含一个 Unmarshal() 函数，支持将字节切片中的数据解码为值。如果解码后的值被赋值给结构体字段，则字段名必须是导出的，因此首字母必须大写；使用 "xml" 结构体字段标签可以自定义键。

在这个示例中，使用 xml.Unmarshal() 函数将以下 XML 格式文件中的值解码到结构体中。

```xml
<campus name="campus1">
    <!-- building-comment -->
    <building name="bldg1">
        <!-- device-comment -->
        <device type="router" name="rtr1"></device>
    </building>
</campus>
```

首先，定义一个结构体，并使用 "xml" 字段标签来标识文件中的键。接下来，使用 ioutil.ReadFile() 函数读取文件并返回一个字节切片，然后使用 xml.Unmarshal() 函数将其解码到结构体实例中。最后，打印结构体实例的成员值，以演示解码后的数据。

```go
package main

import (
    "encoding/xml"
    "fmt"
    "io/ioutil"
)

type Campus struct {
    XMLName xml.Name `xml:"campus"`
    Name     string   `xml:"name,attr"`
    Comment string `xml:",comment"`
    Building Building
}
type Building struct {
    XMLName xml.Name `xml:"building"`
    Name string `xml:"name,attr"`
    Comment string `xml:",comment"`
    Device Device
}
type Device struct {
    XMLName xml.Name `xml:"device"`
    Name string `xml:"name,attr"`
    Type string `xml:"type,attr"`
}

func main() {
    data, _ := ioutil.ReadFile("file.xml")

    camp := &Campus{}

    _ = xml.Unmarshal([]byte(data), &camp)

    fl := fmt.Println
    fl("Campus Name: ", camp.Name)
    fl("Building Name: ", camp.Building.Name)
    fl("Building Comment:", camp.Comment)
    fl("Device Comment: ", camp.Building.Comment)
    fl("Device Name: ", camp.Building.Device.Name)
    fl("Device Type: ", camp.Building.Device.Type)
}
```

输出显示每个值及其相应的字段名。

- Campus Name: campus1
- Building Name: bldg1
- Building Comment: building-comment
- Device Comment: device-comment
- Device Name: rtr1
- Device Type: router

### 第 2.5.2 节：写入 XML

xml 包支持 Marshal() 函数，用于将值序列化为 XML 格式。虽然通常使用结构体来分组值，但也接受 maps。只有导出的结构体字段（因此首字母为大写）才会被序列化。使用 "xml" 结构体字段标签可以自定义键。

在这个示例中，使用 xml.Marshal() 函数将结构体中的值序列化并写入 XML 格式的文件。首先，定义一个首字母大写并使用 "xml" 字段标签标识键的结构体。初始化结构体值，然后使用 xml.Marshal() 函数进行序列化。最后，接收序列化后的 XML 格式字节切片，并使用 ioutil.WriteFile() 函数将其写入文件。

```go
package main

import (
    "encoding/xml"
    "io/ioutil"
)

type Campus struct {
    XMLName xml.Name `xml:"campus"`
    Name string `xml:"name,attr"`
    Comment string `xml:",comment"`
    Building Building
}
type Building struct {
    XMLName xml.Name `xml:"building"`
    Name string `xml:"name,attr"`
    Comment string `xml:",comment"`
    Device Device
}
type Device struct {
    XMLName xml.Name `xml:"device"`
    Name string `xml:"name,attr"`
    Type string `xml:"type,attr"`
}
```





```go
XMLName xml.Name `xml:"device"`
    Name string `xml:"name,attr"`
    Type string `xml:"type,attr"`
}

func main() {
    camp := &Campus {Name: "campus1",
                     Comment: "building-comment",
                     Building: Building{Name: "bldg1",
                          Comment: "device-comment",
                          Device: Device{Name: "rtr1",
                              Type: "router"}}}

    indt, _ := xml.MarshalIndent(camp, "", "  ")

    _ = ioutil.WriteFile("file.xml", indt, 0644)
}
```

输出显示了以 XML 格式呈现每个值的文件。虽然为了演示过程，XML 被写入到文件中，但将 XML 写入 REST API 也很常见。

```xml
<campus name="campus1">
    <!-- building-comment -->
    <building name="bldg1">
        <!-- device-comment -->
        <device type="router" name="rtr1"></device>
    </building>
</campus>
```

## 第 3 章：文本模板

文本模板常用于网络运维中，生成大量遵循标准模板的配置。它们能够实现一致的准确性，并允许版本控制。

模板包通过解析文本并评估动态元素来处理模板。本章将探讨常见的模板操作，然后介绍一个基本模板，再深入讲解模板继承。

本章将涵盖以下主题：

- 定义模板元素
- 创建基本模板
- 实现模板继承

### 第 3.1 节：模板元素

模板的基本构建块是其元素。元素由双花括号包围的参数和操作组成。参数包括值和操作，而操作由语句组成，例如 if-else、range 或 with。

| 元素 | 描述 |
| :--- | :--- |
| `{{.}}` | 根元素 |
| `{{.Var}}` | 变量 |
| `{{- .Var -}}` | 移除两侧的空白 |
| `{{ $version := "0.1" }} {{ $version }}` | 内部变量赋值 |
| `{{/* comment here */}}` | 注释 |
| `Name: {{if .Name }} {{ .Name }} {{ else }} anonymous {{end}} .` | If-else 条件判断 |
| `{{with .Var}} {{end}}` | With 语句 |
| `{{range .Array}} {{end}}` | 遍历切片、映射或通道 |
| `{{ lt 3 4 }}` | 小于（其他布尔运算符：eq, ne, lt, le, gt, ge） |

### 第 3.2 节：基本模板

基本模板由数据源和单个模板组成。模板继承（将在下一节中涵盖）用于组装嵌套模板。

在这个示例中，使用了三个文件：一个 CSV 数据文件、一个模板文件和一个 Go 文件。下面的 CSV 数据文件表示一个 VLAN 列表，每行一个，第一列是数字，第二列是名称。模板文件将表示配置每个 VLAN 的格式。它将遍历数据文件的每一行，并按照各自的布局格式化来自这两列的数据。Go 文件将用于将 CSV 文件和模板文件合并，然后生成输出。

CSV 数据文件：

```csv
1,ONE
2,TWO
3,THREE
```

既然上面已经定义了 CSV 数据文件，模板文件用于定位数据。下面定义的模板文件使用 range 元素封装了中间两行。它遍历代表 CSV 数据文件中行的根元素切片结构体。在循环内，普通文本后面跟着一个用于应用结构体成员的变量。请注意下面模板文件中用于修剪名称后空格的破折号元素。

```go
{{range .}}
  vlan {{.Id}}
  name {{.Name -}}
{{end}}
```

遍历下面的 Go 文件，CSV 数据文件使用 os.Open() 函数以只读模式打开，返回 os.File 的实例。接下来，os.File 实例作为参数传递给 csv.NewReader() 函数，以接收一个带缓冲的 csv.Reader 对象。然后，创建 V lans 结构体的切片实例，用于存储 CSV 文件每行中的值。使用 csv.Reader.Read() 方法逐行解码文件到结构体字段中。然后，将它们存储在一个切片中，直到返回预期的 io.EOF 错误，表示已达到文件末尾。最后，使用 template.ParseFiles() 函数解析模板文件，然后调用 tmpl.Execute() 函数与模板文件合并，将结果发送到终端标准输出。

```go
package main

import (
    "encoding/csv"
    "io"
    "os"
    "text/template"
)

type V lans struct {
    Id, Name string
}

func main() {
    data, _ := os.Open("file.csv")

    reader := csv.NewReader(data)

    vlans := []V lans{}

    for {
        row, err := reader.Read()
        if err == io.EOF {
            break
        }

        vlans = append(vlans, V lans{
            Id: row[0],
            Name: row[1],
        })
    }

    tmpl, _ := template.ParseFiles("file.tpl")
    _ = tmpl.Execute(os.Stdout, vlans)
}
```

输出展示了基本模板数据：

```text
vlan 1
    name ONE
vlan 2
    name TWO
vlan 3
    name THREE
```

### 第 3.3 节：模板继承

模板继承用于处理嵌套模板，通过构建包含子模板的基本骨架来实现。这使得能够跨多个基本模板重用子模板。想象一下多种类型的路由器模板，它们都共享相同的公共子 BGP 或 NTP 模板。

在这个示例中，使用模板继承来组装一个由基本配置数据和多个代表路由器 BGP 和 NTP 配置的子组件组成的路由器配置。数据源将设置在下面的 YAML 文件中，以便轻松解析用户输入。

```yaml
base:
  hostname: router1

bgp:
  as: 1234
  id: 4.4.4.4
  neighbors:
    - ip: 1.1.1.1
      as: 1
    - ip: 2.2.2.2
      as: 2

ntp:
  source: Loopback0
  primary: 11.11.11.11
  secondary: 22.22.22.22
```

总共将使用三个模板文件：一个基本模板和两个嵌套模板。在每个文件中，在顶部利用注释元素来标识文件名，同时使用 define 元素来分配模板名称。由于这是模板继承，子模板通过在各自的位置引用子模板名称以及模板元素来与基本模板关联。

```go
{{/* base.tpl */}}

{{define "base"}}
hostname {{.Base.Hostname}}
{{template "bgp" .}}
{{template "ntp" .}}
{{end}}

{{/* bgp.tmpl */}}

{{ define "bgp" }}
router {{.Bgp.As }}
router-id {{.Bgp.Id -}}
{{range .Bgp.Neighbors}}
neighbor {{.Ip}} remote-as {{.As -}}
{{end}}
{{ end }}

{{/* ntp.tmpl */}}

{{ define "ntp" }}
ntp source-interface {{.Ntp.Source}}
ntp server {{.Ntp.Primary}} prefer
ntp server {{.Ntp.Secondary}}
{{ end }}
```

在下面的 Go 文件中，使用 ioutil.ReadFile() 函数将 YAML 文件读取到一个字节切片中。然后，使用 yaml.Unmarshal() 函数将字节切片解析为结构体实例。接下来，通过解析基本模板和子模板创建模板映射。最后，使用 template.Template.ExecuteTemplate() 方法将数据与模板映射合并，将数据发送到终端标准输出。

```go
package main

import (
    "text/template"
    "os"
    "gopkg.in/yaml.v2"
    "io/ioutil"
)

type Config struct {
    Base Base `yaml:"base"`
    Bgp Bgp `yaml:"bgp"`
    Ntp Ntp `yaml:"ntp"`
}
type Base struct {
    Hostname string `yaml:"hostname"`
}
type Bgp struct {
    As string `yaml:"as"`
    Id string `yaml:"id"`
    Neighbors []Neighbors `yaml:"neighbors"`
}
type Neighbors struct {
    Ip string `yaml:"ip"`
    As string `yaml:"as"`
}
type Ntp struct {
    Source string `yaml:"source"`
    Primary string `yaml:"primary"`
    Secondary string `yaml:"secondary"`
}

func main() {
    config := Config{}

    data, _ := ioutil.ReadFile("file.yaml")

    _ = yaml.Unmarshal(data, &config)

    tmpl := make(map[string]*template.Template)

    files, _ := template.ParseFiles("base.tpl", "bgp.tmpl", "ntp.tmpl")
    
    // 注意：原文在此处截断。根据上下文，接下来的行通常会是：
    // baseTmpl, _ := tmpl.ParseFiles("base.tpl") ... 或类似的解析逻辑以填充映射。
    // 然而，严格遵循“不要添加内容”的原则，我将在源文本停止的地方停止。
}
```




```
"bgp.tmpl", "ntp.tmpl")
tmpl["base.tmpl"] = template.Must(files, nil)
_ = tmpl["base.tmpl"].ExecuteTemplate(
  os.Stdout, "base", config)
}
```

下方的输出显示了合并后的数据和模板。

```
hostname router1

router 1234
  router-id 4.4.4.4
  neighbor 1.1.1.1 remote-as 1
  neighbor 2.2.2.2 remote-as 2

ntp source-interface Loopback0
ntp server 11.11.11.11 prefer
ntp server 22.22.22.22
```

## 第 4 章：HTTP 客户端

超文本传输协议（HTTP）客户端用于建立连接并向 HTTP 服务器请求数据。最常用的方法是 GET 和 POST。http 包支持 RFC 2616 中定义的属性，如超时、重定向和 Cookie。虽然该包提供了更基本的方法，如 `http.Client.Get()` 和 `http.Client.Post()` 方法，但为了应用自定义请求头，可以将 `http.NewRequest()` 函数与 `http.Client.Do()` 方法结合使用。本章将通过使用更常见的功能（如客户端超时、Cookie 和自定义请求头）示例，演示 GET 和 POST 请求。

本章将涵盖以下 HTTP 客户端主题：

-   GET 请求
-   POST 请求

### 4.1：GET

http 包支持 RFC 7231 第 4.3.1 节中定义的 GET 方法。简单的 GET 请求可以使用 `http.Client.Get()` 方法完成；如果需要自定义请求头，则可以使用 `http.NewRequest()` 函数和 `http.Client.Do()` 方法的组合。

在本示例中，使用 `http.NewRequest()` 函数设置方法、URL 和请求体，以接收一个 `http.Request` 对象。然后，使用标准的键值对作为输入，通过 `http.Request.Header.Set()` 方法设置一个请求头。接下来，在 `http.Client` 结构体中初始化 Timeout 字段，返回一个新的 `http.Client` 对象。现在，GET 请求已根据 URL 构建，客户端请求头也已定义，将它们与自定义超时一起使用，通过 `http.Client.Do()` 方法发送和接收 HTTP 请求。最后，从 `http.Client.Do()` 方法接收 Response 对象，并在打印响应之前关闭请求体。

```go
package main

import (
	"fmt"
	"io/ioutil"
	"net/http"
	"time"
)

func main() {
	req, _ := http.NewRequest("GET",
		"http://example.com", nil)
	
	req.Header.Set("Cache-Control", "no-cache")
	
	client := &http.Client{Timeout: time.Second * 10}
	
	resp, _ := client.Do(req)
	body, _ := ioutil.ReadAll(resp.Body)
	resp.Body.Close()
	
	fmt.Printf("%s\n", body)
}
```

### 4.2：POST

http 包支持 RFC 7231 第 4.3.3 节中定义的 POST 方法。简单的 POST 请求可以使用 `http.Client.Post()` 方法完成。如果需要自定义请求头，可以使用 `http.NewRequest()` 函数和 `http.Client.Do()` 方法的组合。

在本示例中，使用 `http.NewRequest()` 函数定义方法、URL 和请求体，以接收一个 `http.Request` 对象。然后，使用标准的键值对作为输入，通过 `http.Request.Header.Set()` 方法设置请求头。接下来，在 `http.Cookie` 结构体中定义 Cookie 的 Name 和 Value 字段，返回一个新的 Cookie 对象，并通过 `http.Request.AddCookie()` 方法将其添加到请求中。然后，在 `http.Client` 结构体中设置 Timeout 字段，并返回一个新的 `http.Client` 对象。现在，POST 请求已构建，请求头已设置，将它们与新的客户端一起使用，在 `http.Client.Do()` 方法中发送和接收 HTTP 请求。最后，从 `http.Client.Do()` 方法返回 Response 对象，并在打印响应之前关闭请求体。

```go
package main

import (
	"bytes"
	"fmt"
	"io/ioutil"
	"net/http"
	"time"
)

func main() {
	url := "http://example.com"

	data := []byte(`{"hello":"world"}`)

	req, _ := http.NewRequest("POST",
		url, bytes.NewBuffer(data))
	req.Header.Set(
		"Content-Type", "application/json")

	cookie := http.Cookie{
		Name:  "cookie name",
		Value: "cookievalue",
	}
	req.AddCookie(&cookie)

	client := &http.Client{Timeout: time.Second * 10}

	resp, _ := client.Do(req)

	body, _ := ioutil.ReadAll(resp.Body)
	resp.Body.Close()

	fmt.Printf("%s\n", body)
}
```

## 第 5 章：SSH 客户端

安全外壳协议（SSH）常用于在远程服务器上执行命令。它也可以用于通过安全文件传输协议（SFTP）传输文件。虽然 ssh 包不是 Go 标准库的一部分，但它是由 Go 团队编写和支持的官方 SSH 包。ssh 包支持多种认证方法，例如使用密码或私钥。本章将通过演示执行命令和传输文件的示例，涵盖这两种认证形式。

本章将涵盖以下 SSH 客户端主题：

-   使用私钥认证的单个命令
-   使用密码认证的多个命令
-   使用密码认证的 SFTP 文件复制

### 5.1：使用私钥认证的单个命令

ssh 包支持私钥认证。这种认证形式比简单密码更安全，因为它难以被暴力破解，并且无需记住或写下密码。

为了准备这个示例，使用 `ssh-keygen` 工具在本地机器上生成公钥和私钥。`ssh-keygen` 在大多数 Linux 或 Mac 安装中可用。该工具创建公钥（`id_rsa.pub`）和私钥文件（`id_rsa`），如下所示。

```bash
$ ssh-keygen -b 4096
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/username/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/username/.ssh/id_rsa.
Your public key has been saved in /Users/username/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:2Bx44V(8c61...BeawULC+z919UW5F username@mycomputer.local
The key's randomart image is:
+----[RSA 4096]----+
| o.@=...ooo |
| o.*+@+ oO |
| ..=.*= oB |
| .o+=.o& Eo |
| + To.+., |
| o .o |
| , |
| |
+----[SHA256]-----+
```

接下来，使用 `ssh-copy-id` 工具将公钥（`id_rsa.pub`）复制到远程主机。它将放置在该主机的 `~/.ssh/authorized_keys` 文件中。

```bash
$ ssh-copy-id remotehost

/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed:
"/Users/username/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys

Password:

Number of key(s) added: 1
```

现在尝试登录该机器，使用：`"ssh 'remotehost'"`
并检查是否只添加了您想要的密钥。

现在，公钥已在远程主机上，私钥已在本地就位，两个密钥均已正确准备用于私钥认证。

接下来，为了准备验证远程主机的身份，使用 `ssh-keyscan` 工具将远程主机公钥获取为 `known_hosts` 文件格式的指纹。如果本地机器之前通过 SSH 连接过该主机，指纹可能已经存在于本地 `~/.ssh/known_hosts` 文件中。

```bash
$ ssh-keyscan remotehost
# remotehost:22 SSH-2.0-OpenSSH_7.6
remotehost ecdsa-sha2-nistp256 AAAAE...jJHN
```

本示例开始于将远程主机公钥复制到一个变量中，该变量将用于在客户端配置中验证远程主机并防止欺骗。使用 `ssh.ParseKnownHosts()` 函数，以 `known_hosts` 文件格式解析公钥。出于简化的目的，密钥是硬编码的；然而，在实际应用中，它可能从文件或数据库中解析。

接下来，使用 `ioutil.ReadFile()` 函数读取私钥文件，并以字节切片形式返回。然后，它与密码一起在 `ssh.ParsePrivateKeyWithPassphrase()` 函数中使用，以获取一个 Signer 实例。然后，通过添加用户名，然后将 Signer 签名添加到 `ssh.PublicKeys()` 函数中进行认证，构建 `ssh.ClientConfig` 结构体。接下来，使用 `ssh.FixedHostKey()` 函数定义 `HostKeyCallback` 以进行授权。最后，设置建立 TCP 连接的最大时间作为 Timeout 值，其中零表示无超时。

请注意，通过将 `ssh.FixedHostKey()` 函数替换为 `ssh.InsecureIgnoreHostKey()` 函数，可以选择绕过远程主机授权，但此不安全函数仅建议在非生产实验室环境中使用。

虽然本示例未涵盖，但可以在 `ssh.ClientConfig` 结构体中可选地定义可接受的密钥类型和加密列表，以及优先级顺序。由 `KeyAlgoXxxx` 常量标识的密钥类型将定义为 `HostKeyAlgorithms` 切片中的值。可接受的加密列表将在嵌入在 `ssh.ClientConfig` 结构体中的 `ssh.Config` 结构体的 `Cipher` 字段中定义。此外，还可以添加传统的 CBC 模式加密算法。

现在，`ssh.ClientConfig` 结构体已构建，它与远程主机一起使用，通过 `ssh.Dial()` 函数启动 SSH 连接，返回一个 `ssh.Client` 实例。接下来，使用 `ssh.Client.NewSession()` 方法创建一个新的会话，然后将其映射到终端的本地标准输出和错误，以便进行演示。最后，使用 `ssh.Session.Run()` 函数在远程主机上运行命令，然后调用 `ssh.Session.Close()` 方法终止连接。

```go
package main

import (
	"golang.org/x/crypto/ssh"
	"io/ioutil"
	"os"
	"time"
)
```




```go
func main() {
    user := "username"
    pass := []byte("password")
    remotehost := "remotehost:22"
    cmd := "hostname"
    privkeyfile := "/Users/username/.ssh/id_rsa"
    knownhost := []byte(
        "remotehost ecdsa-sha2-nistp256 AAE...jZHN")

    _, _, hostkey, _, _ := ssh.ParseKnownHosts(
        knownhost)

    privkeydata, _ := ioutil.ReadFile(privkeyfile)

    parsekey := ssh.ParsePrivateKeyWithPassphrase
    privkey, _ := parsekey(privkeydata, pass)

    config := &ssh.ClientConfig{
        User: user,
        Auth: []ssh.AuthMethod{
            ssh.PublicKeys(privkey),
        },
        HostKeyCallback: ssh.FixedHostKey(hostkey),
        Timeout: 5 * time.Second,
    }
    conn, _ := ssh.Dial("tcp", remotehost, config)

    sess, _ := conn.NewSession()

    sess.Stdout = os.Stdout
    sess.Stderr = os.Stderr

    _ = sess.Run(cmd)

    sess.Close()
}
```

## 第 5.2 章：使用密码认证执行多个命令

接下来的示例首先收集用于验证远程主机身份并构建客户端配置的远程主机公钥。

与前面的示例一样，远程主机公钥是以 `known_hosts` 文件格式的指纹形式获取的，使用 `ssh-keyscan` 实用工具。同样，如果本机之前通过 SSH 连接过该主机，它也可能存在于本地的 `~/.ssh/known_hosts` 文件中。

```bash
$ ssh-keyscan remotehost
# remotehost:22 SSH-2.0-OpenSSH_7.6
remotehost ecdsa-sha2-nistp256 AAE...jZHN
```

接下来，远程主机公钥被复制到客户端配置中用于防止欺骗的变量中。然后，使用 `ssh.ParseKnownHosts()` 函数以 `known_hosts` 文件格式解析该公钥。为了简化起见，密钥是硬编码的，但在实际操作中，可以从文件或数据库中解析。同样，虽然本例中用户名的密码是硬编码的，但在生产环境中应使用更安全、更便捷的方式获取。接下来，通过添加用户名，然后将密码加入 `ssh.Password()` 函数进行身份验证，构建 `ssh.ClientConfig` 结构体。通过定义带有 `ssh.FixedHostKey()` 函数的 `HostKeyCallback` 来启用授权。最后，设置 TCP 连接建立的最大时间作为 `Timeout` 值，其中零表示无超时。

请注意，可以通过将 `ssh.FixedHostKey()` 函数替换为 `ssh.InsecureIgnoreHostKey()` 函数来选择绕过远程主机授权，但是，这种不安全的函数仅建议在非生产实验室环境中使用。

虽然本示例未涵盖，但可以选择在 `ssh.ClientConfig` 结构体中定义可接受的密钥类型和加密算法列表以及偏好顺序。由 KeyAlgoXxxx 常量识别的密钥类型将作为 `HostKeyAlgorithms` 切片中的值进行定义。可接受的加密算法列表将在嵌入到 `ssh.ClientConfig` 结构体中的 `ssh.Config` 结构体的 `Cipher` 字段中定义。此外，还可以添加传统的 CBC 模式加密算法。

现在 `ssh.ClientConfig` 结构体已构建完成，它与远程主机一起使用，通过调用 `ssh.Dial()` 函数返回 `ssh.Client` 实例来启动 SSH 连接。接下来，使用 `ssh.Client.NewSession()` 方法创建新会话，然后将其映射到终端的本地标准错误和标准输出，以便演示。然后，使用 `ssh.Session.Shell()` 方法在远程主机上启动 shell 以运行命令。最后，执行命令，并使用 `ssh.Session.Wait()` 方法等待命令执行完毕，然后调用 `ssh.Session.Close()` 方法关闭会话并终止连接。

```go
package main

import (
    "fmt"
    "golang.org/x/crypto/ssh"
    "os"
    "time"
)

func main() {
    user := "username"
    pass := "password"
    remotehost := "remotehost:22"
    knowhost := []byte(
        "remotehost ecdsa-sha2-nistp256 AAE...jZHN")

    _, _, hostkey, _, _ := ssh.ParseKnownHosts(
        knowhost)

    config := &ssh.ClientConfig{
        User: user,
        Auth: []ssh.AuthMethod{
            ssh.Password(pass),
        },
        HostKeyCallback: ssh.FixedHostKey(hostkey),
        Timeout: 5 * time.Second,
    }
    conn, _ := ssh.Dial("tcp", remotehost, config)

    sess, _ := conn.NewSession()

    stdin, _ := sess.StdinPipe()

    sess.Stdout = os.Stdout
    sess.Stderr = os.Stderr

    _ = sess.Shell()

    fmt.Fprintf(
        stdin, "%s\n%s\n%s\n", "pwd", "ls", "exit")

    _ = sess.Wait()

    sess.Close()
}
```

## 第 5.3 章：使用密码认证的 SFTP 文件复制

在这个 SFTP 示例中，检索远程主机公钥以验证远程主机的身份。它将用于构建客户端配置。

首先，使用 `ssh-keyscan` 实用工具以 `known_hosts` 文件格式收集远程主机公钥作为指纹。同样，如果本机之前通过 SSH 连接过该主机，它也可见于本地的 `~/.ssh/known_hosts` 文件中。

```bash
$ ssh-keyscan remotehost
# remotehost:22 SSH-2.0-OpenSSH_7.6
remotehost ecdsa-sha2-nistp256 AAE...jZHN
```

接下来，远程主机公钥被复制到客户端配置中用于防止欺骗的变量中。然后，使用 `ssh.ParseKnownHosts()` 函数从 `known_hosts` 格式的条目中解析公钥。为了简化起见，密钥是硬编码的；然而，在实际操作中，可以从文件或数据库中解析。接下来，通过将用户名和密码加入 `ssh.Password()` 函数进行身份验证，构建 `ssh.ClientConfig` 结构体。然后，使用 `ssh.FixedHostKey()` 函数定义 `HostKeyCallback` 以进行授权。最后，在 `Timeout` 中设置 TCP 连接建立的最大时间，其中值为零表示无超时。

请注意，可以通过将 `ssh.FixedHostKey()` 函数替换为 `ssh.InsecureIgnoreHostKey()` 函数来绕过远程主机授权，但是，这种不安全的函数仅建议在非生产实验室环境中使用。

虽然本示例未涵盖，但可以选择在 `ssh.ClientConfig` 结构体中定义可接受的密钥类型和加密算法列表以及偏好顺序。由 KeyAlgoXxxx 常量识别的密钥类型将作为 `HostKeyAlgorithms` 切片中的值进行定义。可接受的加密算法列表将在嵌入到 `ssh.ClientConfig` 结构体中的 `ssh.Config` 结构体的 `Cipher` 字段中定义。此外，还可以添加传统的 CBC 模式加密算法。

现在 `ssh.ClientConfig` 结构体已构建完成，它与远程主机一起使用，通过调用 `ssh.Dial()` 函数返回 `ssh.Client` 实例来启动 SSH 连接。

接下来，通过调用 `sftp.NewClient()` 函数并使用 `ssh.Client` 会话对象作为参数，创建一个新的 SFTP 客户端。这使得 `sftp.Client.MkdirAll()` 方法可以创建包含路径中所有父级的目录，`sftp.Client.Create()` 方法可以创建将要复制到的目标文件。现在目标目录和文件已创建，使用 `os.Open()` 函数打开源文件，并使用 `io.Copy()` 函数复制内容，直到源文件达到 EOF。然后，在目标文件上调用 `sftp.File.Close()` 方法，并使用 `sftp.Client.Close()` 方法关闭 SFTP 会话。最后，使用 `ssh.Client.Close()` 方法关闭 SSH 会话。

```go
package main

import (
    "github.com/pkg/sftp"
    "golang.org/x/crypto/ssh"
    "io"
    "os"
    "time"
)

func main() {
    user := "username"
    pass := "password"
    remotehost := "remotehost:22"
    knowhost := []byte(
        "remotehost ecdsa-sha2-nistp256 AAE...jZHN")

    _, _, hostkey, _, _ := ssh.ParseKnownHosts(
        knowhost)

    config := &ssh.ClientConfig{
        User: user,
        Auth: []ssh.AuthMethod{
            ssh.Password(pass),
        },
        HostKeyCallback: ssh.FixedHostKey(hostkey),
        Timeout: 5 * time.Second,
    }
    conn, _ := ssh.Dial("tcp", remotehost, config)

    client, _ := sftp.NewClient(conn)

    _ = client.MkdirAll("/dir")

    dstfile, _ := client.Create("/dir/dest.txt")

    srcfile, _ := os.Open("/src.txt")

    _, _ = io.Copy(dstfile, srcfile)

    dstfile.Close()
    client.Close()
    conn.Close()
}
```




## 第 6 章：IP 地址操作

IP 地址操作用于高效地解析和处理 IP 地址及其各自的网络掩码。net 包提供了用于处理符合 RFC 4632 和 RFC 4291 标准的 IP 地址和 CIDR 表示法的方法。本章将介绍与 IP 地址操作相关的常见任务，例如列出网络内的所有 IP、判断 IP 是否包含在某个网络中，以及将掩码在 CIDR 表示法和点分十进制表示法之间进行转换。

本章将涵盖以下主题：

- 判断网络是否包含某个 IP
- 列出网络内的所有 IP
- 在不同网络掩码格式之间进行转换

### 第 6.1 章：网络包含 IP

本示例将定义一个包含两个 IP 地址的 CIDR 网络和切片，其中一个 IP 在 CIDR 网络内，另一个在外部。它将遍历切片中的每个 IP，以确定其是否包含在该网络中。

该示例首先使用 `net.ParseCIDR()` 函数对字符串格式的 CIDR 网络地址进行处理，以返回一个 `net.IPNet` 对象。接着，使用 `net.ParseIP()` 函数从字符串地址返回一个 `net.IP` 对象。最后，将 `net.IP` 对象用作 CIDR 网络上 `net.IPNet.Contains()` 方法的参数，以获取并打印结果。

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	netw := "1.1.1.0/24"
	ips := []string{"1.1.1.1", "2.2.2.2"}

	for _, ip := range ips {
		_, cidrnet, _ := net.ParseCIDR(netw)

		addr := net.ParseIP(ip)

		result := cidrnet.Contains(addr)

		fmt.Printf("%s contains %s: %t\n",
			cidrnet, addr, result)
	}
}
```

下方输出显示了 IP 是否包含在 CIDR 网络中。

```
1.1.1.0/24 contains 1.1.1.1: true
1.1.1.0/24 contains 2.2.2.2: false
```

### 第 6.2 章：列出网络 IP

本示例演示了如何列出网络内的所有 IP 地址，包括网络地址和广播地址。首先，使用 `net.ParseCIDR()` 函数处理字符串格式的 CIDR 地址，以返回 `net.IP` 和 `net.IPNet` 对象。接下来，定义一个函数作为值，稍后将在循环语句中用于自增。该函数接受一个 `net.IP` 字节切片参数，用于初始化循环的起始值，并最终增加相应的八位组值。

接下来，定义一个最终的循环来遍历网络 IP。首先，使用 `net.IP.Mask()` 方法获取起始网络地址，以此初始化 `net.IP` 值。然后，将 `net.IPNet.Contains()` 方法设置为终止条件以结束循环。最后，使用自增函数来遍历相应的网络。

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	netw := "1.1.1.1/30"
	ip, ipnet, _ := net.ParseCIDR(netw)

	inc := func(ip net.IP) {
		for i := len(ip) - 1; i >= 0; i-- {
			ip[i]++
			if ip[i] >= 1 {
				break
			}
		}
	}

	ipmask := ip.Mask(ipnet.Mask)

	for ip := ipmask; ipnet.Contains(ip); inc(ip) {
		fmt.Println(ip)
	}
}
```

下方输出列出了 CIDR 网络内的所有 IP 地址，包括网络地址和广播地址。

```
1.1.1.0
1.1.1.1
1.1.1.2
1.1.1.3
```

### 第 6.3 章：掩码转换

本示例将把 IPv4 掩码从斜杠表示法转换为点分十进制表示法，然后再从点分十进制表示法转回 IPv4 斜杠表示法。

首先，使用 `net.ParseCIDR()` 函数处理字符串格式的 CIDR 地址，以返回 `net.IP` 和 `net.IPNet` 对象。然后，为了转换掩码，将 `net.IPNet.Mask` 字节切片赋值给一个变量，并将每个索引格式化为点分十进制掩码字符串并打印。

接下来，为了将掩码转回斜杠表示法，将点分十进制掩码传入 `net.ParseIP()` 函数，以返回一个 `net.IP` 对象。在 `net.IP` 对象上调用 `net.IP.To4()` 方法，将 IP 转换回 4 字节表示。该 `net.IP` 对象被包裹在 `net.IPMask()` 函数中，以返回一个 `net.IPMask` 对象。最后，使用 `net.IPMask.Size()` 方法返回掩码长度，即掩码中前导 1 的数量。

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	netw := "1.1.1.1/27"
	ipv4IP, ipv4Net, _ := net.ParseCIDR(netw)

	m := ipv4Net.Mask

	dotmask := fmt.Sprintf("%d.%d.%d.%d", m[0], m[1], m[2], m[3])

	fmt.Printf("Dot-decimal notation: %s %s\n", ipv4IP, dotmask)

	cidrMask := net.IPMask(
		net.ParseIP(dotmask).To4())

	length, _ := cidrMask.Size()

	slash := fmt.Sprintf("%s/%d", ipv4IP, length)

	fmt.Println("\nCIDR notation: ", slash)
}
```

下方输出显示了带有 点分十进制 掩码的 IP，随后是 CIDR 掩码表示法。

```
Dot-decimal notation: 1.1.1.1 255.255.255.224
CIDR notation: 1.1.1.1/27
```

## 第 7 章：DNS 记录查询

DNS 记录查询通过域名解析实现。net 包包含用于查询更常见的 DNS 记录的方法。本章介绍了这些方法以及如何用来查询包括正向、反向、CNAME、MX、NS、SRV 和 TXT 在内的记录。

本章将涵盖以下 DNS 记录查询：

- 正向 (A)
- 反向 (PTR)
- 规范名称 (CNAME)
- 邮件交换器 (MX)
- 名称服务器 (NS)
- 服务 (SRV)
- 文本 (TXT)

### 第 7.1 章：正向 (A)

`net.LookupIP()` 函数接受一个字符串，并返回一个包含表示该主机的 IPv4 和/或 IPv6 地址的 `net.IP` 对象切片。

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	ips, _ := net.LookupIP("google.com")

	for _, ip := range ips {
		fmt.Println(ip.String())
	}
}
```

下方输出列出了以 IPv4 和 IPv6 格式返回的 google.com 的 A 记录。

```
172.217.1.238
2607:f8b0:4000:80e::200e
```

### 第 7.2 章：反向 (PTR)

`net.LookupAddr()` 函数执行地址的反向查询，并返回映射到该地址的名称列表。请注意，宿主机的 C 库解析器只会返回一个结果。为了绕过主机解析器，必须使用自定义解析器。

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	names, _ := net.LookupAddr("8.8.8.8")

	for _, name := range names {
		fmt.Println(name)
	}
}
```

下方显示了针对该地址返回的单个反向记录，包括末尾的句点符号。

```
google-public-dns-a.google.com.
```

### 第 7.3 章：规范名称 (CNAME)

`net.LookupCNAME()` 函数接受主机名作为字符串，并返回所提供主机的单个规范名称。

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	cname, _ := net.LookupCNAME(
		"research.swtch.com")

	fmt.Println(cname)
}
```

下方显示了针对 research.swtch.com 域名返回的 CNAME 记录，包括末尾的句点符号。

```
ghs.google.com.
```

### 第 7.4 章：邮件交换器 (MX)

`net.LookupMX()` 函数接受域名作为字符串，并返回按优先级排序的 MX 结构体切片。MX 结构体由 Host（字符串）和 Pref（uint16）组成。

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	mxs, _ := net.LookupMX("google.com")

	for _, mx := range mxs {
		fmt.Println(mx.Host, mx.Pref)
	}
}
```

输出列出了该域名的每个 MX 记录，随后是各自的优先级。

```
aspmx.l.google.com. 10
alt1.aspmx.l.google.com. 20
alt2.aspmx.l.google.com. 30
alt3.aspmx.l.google.com. 40
alt4.aspmx.l.google.com. 50
```

### 第 7.5 章：名称服务器 (NS)

`net.LookupNS()` 函数接受域名作为字符串，并以 NS 结构体切片的形式返回 DNS NS 记录。NS 结构体由 Host（字符串）组成。

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	nss, _ := net.LookupNS("gmail.com")

	for _, ns := range nss {
		fmt.Println(ns.Host)
	}
}
```

下方显示了支持该域名的 NS 记录，包括末尾的句点符号。

```
ns1.google.com.
ns4.google.com.
ns3.google.com.
ns2.google.com.
```




## 第 7.6 章：SRV 记录

`net.LookupSRV()` 函数接受服务、协议和域名作为字符串输入。它返回一个规范名称字符串以及一个 SRV 结构体切片。SRV 结构体支持将 Target（目标）作为字符串，以及将 Port（端口）、Priority（优先级）和 Weight（权重）作为 uint16 类型。`net.LookupSRV()` 函数尝试解析该服务、协议和域名的 SRV 查询，并按优先级排序，在同一优先级内按权重进行随机化。

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	cname, srvs, _ := net.LookupSRV(
		"xmpp-server", "tcp", "google.com")

	fmt.Printf("\ncname: %s \n\n", cname)

	for _, srv := range srvs {
		fmt.Printf("%v:%v:%v:%d:%d\n",
			srv.Target, srv.Port,
			srv.Priority, srv.Weight)
	}
}
```

下方的输出展示了 CNAME 的返回结果，随后是相应的 SRV 记录的目标、端口、优先级和权重，它们之间由冒号分隔。

```
cname: _xmpp-server._tcp.google.com.

xmpp-server.l.google.com.:5269:5:0
alt2.xmpp-server.l.google.com:5269:20:0
alt1.xmpp-server.l.google.com:5269:20:0
alt3.xmpp-server.l.google.com:5269:20:0
alt4.xmpp-server.l.google.com:5269:20:0
```

## 第 7.7 章：TXT 记录

`net.LookupTXT()` 函数接受一个域名作为字符串，并返回一个包含 DNS TXT 记录列表的字符串切片。

```go
package main

import (
	"fmt"
	"net"
)

func main() {
	txts, _ := net.LookupTXT("gmail.com")

	for _, txt := range txts {
		fmt.Println(txt)
	}
}
```

下面展示了 gmail.com 的单条 TXT 记录。

```
v=spf1 redirect=_spf.google.com
```

## 第 8 章：正则表达式模式匹配

正则表达式模式匹配用于匹配由搜索模式定义的一系列字符。`regexp` 包利用了快速且线程安全的 RE2 正则表达式引擎。虽然它不支持回溯，但它保证了线性时间的执行效率。本章涵盖了简单匹配、匹配组、命名匹配、模板展开以及多行分割。

本章将涵盖以下正则表达式模式主题：

- 简单匹配
- 匹配组
- 命名捕获组
- 模板展开
- 多行分隔符分割

## 第 8.1 章：简单匹配

简单模式匹配涵盖了对数据集应用正则表达式模式并返回结果的基本概念。在此示例中，首先识别数据集，然后使用 `regexp.MustCompile()` 函数定义模式。该模式利用 `\w+` 语法来匹配点号两侧的一个或多个单词字符。然后，使用数据集作为输入，在模式上调用 `regexp.Regexp.FindString()` 方法以返回结果。如果需要从模式中获得多个字符串匹配，则应使用 `regexp.Regexp.FindAllString()` 方法，该方法将返回一个切片。

```go
package main

import (
	"fmt"
	"regexp"
)

func main() {
	data := `# host.domain.tld #`
	pattern := regexp.MustCompile(`\w+\.\w+\.\w+`)
	result := pattern.FindString(data)

	fmt.Println(result)
}
```

下方展示了使用 `\w+.\w+.\w+` 模式对数据集进行简单匹配的结果。

```
host.domain.tld
```

## 第 8.2 章：匹配组

在搜索模式中使用括号可以识别各个匹配组。子模式放置在括号内，以识别数据集中的每个独立匹配组。在此示例中，通过匹配域名的每一部分到其独立的组中来演示匹配组。

首先，识别数据集，然后使用 `regexp.MustCompile()` 函数定义模式。该模式使用 `\w+` 语法来匹配点号两侧的一个或多个单词字符。然后，使用数据集作为输入，调用 `regexp.Regexp.FindAllStringSubmatch()` 方法以返回一个二维切片，其中第一个切片值是整个匹配集合，而随后的每个值分别是相应的匹配组。向 `regexp.Regexp.FindAllStringSubmatch()` 方法传入 -1 表示不限制匹配数量；否则，可以设置一个正数来限制结果。

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

## 第 8.3 章：命名捕获组

当正则表达式变得复杂时，通过名称记录和引用每个捕获组的用途是非常有帮助的。由于组名和位置是固定的，可以使用 `regexp.Regexp.SubexpNames()` 方法引用它们。切片中的组索引与 `regexp.Regexp.FindStringSubmatch()` 方法返回的切片中的相应索引匹配，然后用于构建映射，如下面的示例所示。

此示例首先识别数据集，然后使用 `regexp.MustCompile()` 函数定义模式。该模式使用 `\w+` 语法来匹配点号两侧的一个或多个单词字符。由于使用了命名捕获组，每个模式都用 `(?P<name>re)` 语法定义，其中 name 是捕获组名称。然后，使用数据集作为输入，调用 `regexp.Regexp.FindStringSubmatch()` 方法以返回一个切片，其中第一个切片值是最左侧的匹配。接下来，创建一个映射来保存结果，然后遍历由 `regexp.Regexp.SubexpNames()` 方法返回的切片，该方法返回每个括号子表达式的名称。在遍历每个名称时，检查子表达式名称以确保其不为空。如果名称有效，则使用该名称作为键，对应的子匹配索引值作为值来创建映射条目，最后打印出新的映射。

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

## 第 8.4 章：模板展开

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

首先，定义配置，然后使用 `regexp.MustCompile()` 函数中的模式作为参数，返回一个 `regexp.Regexp` 对象。接着，对该对象调用 `regexp.Regex.Split()` 方法，使用配置和 `-1` 来处理无限次匹配。该方法将配置拆分为一个单一切片，其中每个值是模式匹配之间剩余的内容。

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

-   合并 Stdout/Stderr
-   分离 Stdout/Stderr

## 第 9.1 章：合并 Stdout/Stderr

`exec` 包支持在命令执行后合并终端的标准输出和标准错误。这种合并的输出可以简化输出处理并节省几个步骤。

将设置一个场景来演示，创建两个文件；一个是可写的，另一个则移除了写权限。使用 `cat` 命令，我们将读取每个文件，并期望看到来自可读文件（`r.txt`）的标准输出和来自不可读文件（`w.txt`）的标准错误。

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

请注意，输出首先显示来自可读文件（`r.txt`）的标准输出文本，然后是来自不可读文件（`w.txt`）的错误文本。

```
hi from r.txt
cat: w.txt: Permission denied
```

## 第 9.2 章：分离 Stdout/Stderr

本示例将展示如何执行命令并将标准终端输出和错误分开。`exec` 包轻松地执行外部命令，并通过其原生函数区分标准输出和标准错误。

与上一节类似，将设置一个场景进行演示。创建两个文件；一个是可写的，另一个则移除了写权限。使用 `cat` 命令，我们将读取每个文件，并期望看到来自可读文件（`r.txt`）的标准输出和来自不可读文件（`w.txt`）的标准错误。

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

输出首先显示来自可读文件（`r.txt`）的标准输出文本，然后是来自不可读文件（`w.txt`）的错误文本。

```
stdout: hi from r.txt
stderr: cat: w.txt: Permission denied
```

# 第 10 章：CLI 应用程序助手

CLI 应用程序助手在命令行应用程序中用作构建模块。它们有助于快速轻松地构建交互式程序。

本章将介绍读取数据的三种不同方法。演示了敏感和非敏感数据的用户输入提示，接着是用于内联参数的命令行参数和标志。最后，检查列格式化的输出，以展示一种呈现数据的有效模式。

本章将涵盖以下 CLI 应用程序助手主题：

-   用户输入
-   命令行参数
-   命令行标志
-   列格式化

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

在示例的第一部分，根据类型使用相应的 `flag` 函数声明标志。接下来，指定标志名称、默认值和使用说明字符串。然后，在所有标志定义完成后，调用 `flag.Parse()` 函数将命令行用户输入解析到定义的标志中。最后，通过指针访问标志值。

```go
package main

import (
    "flag"
    "fmt"
)

func main() {

    port := flag.Int("p", 8000,
        "specify port. default is 8000.")

    enable := flag.Bool("e", false,
        "specify enable. default is false.")

    name := flag.String("n", "blank",
        "specify name. default is blank.")

    flag.Parse()

    fmt.Println("port = ", *port)
    fmt.Println("enable = ", *enable)
    fmt.Println("name = ", *name)
}
```

程序从本地目录运行，并使用标志作为输入。输出结果将显示标志值。

```
$ ./program -p 80 -e true -n test
port = 80
enable = true
name = test
```

## 第 10.4 章：列格式设置

命令行应用程序的输出通常以列格式显示，以便关联各项内容。`tabwriter` 包允许使用制表符结尾的单元格在连续行中轻松格式化列。

示例首先分配并初始化一个新的 `tabwriter.Writer` 对象。参数从左到右分别用于输出、最小宽度、制表宽度、填充、填充字符和自定义标志（例如右对齐）。接下来，使用 `fmt.Fprintf` 函数格式化列并写入 `tabwriter.Writer` 对象。最后，在最后一次调用后使用 `tabwriter.Writer.Flush()` 方法，以确保任何缓冲数据都被写入输出。

```go
package main

import (
    "fmt"
    "os"
    "text/tabwriter"
)

func main() {
    w := tabwriter.NewWriter(
        os.Stdout, 8, 8, 0, '\t', 0
    )

    fmt.Fprintf(w, "\n %s\t%s\t%s\t",
        "Col1", "Col2", "Col3")

    fmt.Fprintf(w, "\n %s\t%s\t%s\t",
        "----", "----", "----")

    for i := 0; i < 5; i++ {
        fmt.Fprintf(
            w, "\n %0d\t%0d\t%0d\t", i, i+1, i+2)
    }
    w.Flush()
}
```

输出结果展示了左对齐的三列格式。

```
Col1 Col2 Col3
--- --- ---
0 1 2
1 2 3
2 3 4
3 4 5
4 5 6
```

