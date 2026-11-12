
## 第 5 章：操作文件

### 本章内容

- 创建新文件并写入文件
- 打开文件并从文件读取
- 向现有文件追加内容
- 获取文件信息
- 管理文件和目录

如果你对打开和关闭文件、从文件读取和写入文件感兴趣，Tcl 都可以做到。本章主要介绍如何操作文件。我还会向你展示如何获取诸如文件是否存在、文件名是文件还是目录等信息，还有更多内容。

### 创建新文件并写入

要创建并打开一个用于写入的新文件，需使用 open 命令。你即将阅读的内容是 C 语言编程古老时代的遗留产物，如果我说了算，事情会有所不同。但事实并非如此，至少在 Tcl 中不是这样。因此，你必须使用一个本质上只是旧式 C 语言做法复制品的命令。

open 命令接受两个参数：文件名（也可以包含文件路径）和一个描述如何打开文件的晦涩字符串。假设你想要创建一个新文件以便写入；为此，你使用字母 w（代表写入）。命令如下：

```
open "/tmp/data.txt" "w"
```

该命令在 /tmp 目录中创建并打开名为 data.txt 的文件，并返回一个代表该文件的值。但你还需要将该值存储在变量中。因此，你通常将 open 命令放在方括号内并保存结果，如下所示：

```
set myfile [open "/tmp/data.txt" "w"]
```

这将 open 命令的结果保存到名为 myfile 的变量中，随后可在后续操作中使用，例如写入文件的命令和关闭文件的命令。下面是一个演示此过程的完整程序：

```
set myfile [open "/tmp/data.txt" "w"]
puts $myfile "Hello"
puts $myfile "Goodbye"
close $myfile
```

该程序创建并打开文件，然后向文件写入两行文本。close 命令关闭文件。

运行此程序后，文件内容如下：

Hello
Goodbye

我使用 puts 命令将这两行写入文件。但与 puts 命令的常规用法不同，我包含了 myfile 变量，如前所述，它是 open 命令的结果。

![](img/3f967ab8a8fddc723173059f56621648_303_0.png)

将 open 命令的结果保存到变量中，并在 puts 命令后放置该变量名。这样，puts 命令就知道要写入文件，而不是控制台。

### 打开文件并从中读取

如果你已有一个文件，可以在 Tcl 中使用 open 命令以读取方式打开文件。然后即可开始从文件读取数据。假设你在 /tmp 目录中有一个名为 data.txt 的文件，其中包含如下两行文本：

Hello
 Goodbye

（如果你阅读了上一节，这就是该节中创建的同一个文件。）要读取这些数据，请使用 open 命令，将第二个参数传递为字母 r（代表读取）。

下面是一个示例程序：

```
set myfile [open "/tmp/data.txt" "r"]
gets $myfile a
puts "The first line is: $a"
gets $myfile a
puts "The second line is: $a"
close $myfile
```

在本示例中，首先我调用 open 命令，传递要打开的文件名（包含目录）以及由字母 r 组成的字符串（表示读取）。我将 open 命令的结果保存到名为 myfile 的变量中，稍后将在后续文件命令中使用。下一行从文件中读取。具体做法如下：

```
gets $myfile a
```

gets 命令读取一个字符串，通常用于从控制台读取数据，如下所示：

```
gets stdin a
```

但这次，我没有为第二个参数使用 stdin，而是使用了 $myfile。gets 命令会读取一行，并将其作为字符串保存到指定的变量中，本例中是变量 a。程序的下一行会打印变量 a 的内容以及一条友好的提示信息。然后我针对文件中的另一行文本再次执行同样的两行代码。

最后，我关闭文件。输出如下：

```
The first line is: Hello
The second line is: Goodbye
```

通常，以读取方式打开文件时，你会希望先确保不会遇到任何错误，然后再贸然尝试从文件读取数据。例如，如果文件不存在，open 命令会失败并报错，如下所示：

![](img/3f967ab8a8fddc723173059f56621648_304_0.png)

```
couldn't open "/tmp/data.txt": no such file or directory
while executing
"open "/tmp/data.txt" "r""
invoked from within
"set myfile [open "/tmp/data.txt" "r"]"
(file "read.tcl" line 1)
```

因此，在打开文件之前，你应先检查文件是否存在。我将在本章后面的“获取文件信息”一节中介绍如何测试文件是否存在。以下是快速预览：

```
if {[file exists "/tmp/data.txt"]} {
set myfile [open "/tmp/data.txt" "r"]
gets $myfile a
puts "The first line is: $a"
gets $myfile a
puts "The second line is: $a"
close $myfile
} else {
puts "Sorry, the file doesn't exist."
}
```

### 向现有文件追加

你可能有一个已包含信息的文件，并希望将更多信息写入文件末尾。通常，如果在程序中输入以下行，将会覆盖文件中已有的任何数据：

```
open "/tmp/data.txt" "w"
```

如果要*追加*到文件，请将 *w* 替换为 *a*，如下所示：

```
open "/tmp/append.txt" "a"
```

接下来的 `puts` 命令将向文件追加内容（即追加到文件）。要查看此过程，请尝试以下简短程序：

```
set myfile [open "/tmp/append.txt" "a"]
puts $myfile [clock seconds]
close $myfile
```

将此程序保存为 append.tcl，并按如下方式运行：

```
$ tclsh append.tcl
```

然后等待片刻，再次输入：

```
$ tclsh append.tcl
```

这样做几次。文件内容应类似于：

```
more /tmp/append.txt
1062372095
1062372146
1062372226
1062372229
```

每次运行程序时，都会向文件追加一行，而不是覆盖现有文件。（顺便说一句，`clock seconds` 命令会获取当前系统时间（以秒为单位）。）

### 获取文件信息

Tcl 包含大量用于获取文件信息的命令。这些命令都作为 file 命令的子命令存在。要试用其中一些命令，我建议选择你确定在计算机上存在的文件。一种方法是在当前目录中创建一个文件。在 Linux 或 Windows 命令行 shell 中，可以输入以下行来创建一个简单文件：

```
echo hi > test.txt
```

然后可以打开 Tcl 命令行 shell，尝试其中一些命令。

![](img/3f967ab8a8fddc723173059f56621648_306_0.png)

我逐一列出所有可用命令未免太傻，因为你可以在在线帮助中自行查找。因此，我将重点介绍更实用的命令。你可以在 Tcl 在线帮助的 file 条目下找到其他命令，网址为：www.scriptics.com/man/tcl8.4/TclCmd/file.htm

下面是在 Linux 上的一次交互式会话，演示了其中一些命令（请先创建 test.txt 文件）：

```
% # This will show the time the file was 'last accessed:
% file atime test.txt
1062382720
% # Now format the time as a string
% clock format [file atime test.txt]
Sun Aug 31 19:18:40 PDT 2003
%
% # Here's the time the file was last modified:
% file mtime test.txt
1062382719
% # Format it:
% clock format [file mtime test.txt]
Sun Aug 31 19:18:39 PDT 2003
%
% # Get the file attributes
% file attribute test.txt
-group users -owner jeffcogs -permissions 00644
% # Find out if the file exists
% file exists test.txt
1
% # Is it a directory?
% file isdirectory test.txt
0
% # Nope, got back 0
%
% # Is it a file?
% file isfile test.txt
1
% # Yup, got back 1
%
% # How big is the file?
% file size test.txt
3
% # Only three bytes...
```

### 管理文件和目录

如果要删除文件、重命名文件、移动文件、创建目录或删除目录，可以使用 file 命令的子命令。这些操作很特殊，因为它们都不涉及打开和读取文件。它们直接作用于文件本身，而不是文件内容。

下面是你需要使用的命令摘要：

- copy：顾名思义，此命令用于复制文件。不过，如果要创建的文件已存在，除非包含名为 force 的选项，否则复制操作将失败。
- delete：此命令用于删除文件或目录。不过，有时文件或目录可能没有足够的权限来执行删除操作；如果包含名为 force 的选项，Tcl 会尝试覆盖该权限。
- mkdir：此命令用于创建目录。
- rename：此命令用于重命名文件或目录。如果文件权限不允许重命名，你可以包含 force 选项，Tcl 会尝试覆盖权限。

下面是 copy 命令的交互式会话示例；请记住，像我这样在命令前加上 file 命令：

```
% file copy myfile.txt myfile2.txt
% file copy myfile.txt myfile2.txt
error copying "myfile.txt" to "myfile2.txt": file already exists
% file copy -force myfile.txt myfile2.txt
```
