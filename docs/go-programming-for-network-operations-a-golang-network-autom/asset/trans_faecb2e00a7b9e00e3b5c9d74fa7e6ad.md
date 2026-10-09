

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

