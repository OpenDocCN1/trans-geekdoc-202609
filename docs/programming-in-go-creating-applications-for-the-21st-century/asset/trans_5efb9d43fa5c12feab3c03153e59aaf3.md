
## 9.1. 自定义包

GOPATH/src/stacker/stacker.go

在这里，GOPATH 是一个目录（如果存在），或者是 GOPATH 环境变量中用冒号（Windows 上为分号）分隔的路径。我们在 stacker 目录下执行 `go build` 命令，将得到一个名为 `stacker` 的可执行文件（Windows 上为 `stacker.exe`）。然而，如果我们希望可执行文件位于 GOPATH 目录，或者希望其他程序可以使用 `stacker` 包，则必须使用 `go install`。

当执行 `go install stacker` 时，程序会创建两个目录（如果不存在）：GOPATH/bin 包含 `stacker` 可执行文件，以及 GOPATH/pkg/linux_64，后者包含包的二进制库文件。操作系统/架构目录将与所使用的机器匹配（例如，对于 32 位 Windows 为 `windows`）。

`stacker` 包通过 `import "stacker/"` 语句被程序导入，这是 Unix 风格的路径，它不包含 GOPATH/src 部分。事实上，GOPATH 中的任何程序或包都可以使用这种导入方式，因为 Go 不区分特定的包和共享包。

第 6 章中的 `omap` 包（第 6.5 节，在 `omap.go` 文件中）为了避免冲突，我们为想要共享的包创建了一个目录（或我们的 GOPATH 目录之一），并给它一个唯一的名称（在本例中为一个域名）。这里的目录结构如下：

GOPATH/src/qrac.eu/omap/omap.go

我们的任何程序（只要它们在 GOPATH 中）都可以通过 `import "qrac.eu/omap"` 访问 `omap` 包。如果我们有共享包，会将它们放在 GOPATH/src/qrac.eu 下，与 `omap` 包并列。

当执行 `go install omap` 时，它会创建 GOPATH/pkg/linux_64/qrac.eu 目录（如果不存在），包含 `omap` 包的二进制库文件，其操作系统/架构目录取决于机器。

如果我们想在自己的包内部创建包，可以这样做。我们创建一个包目录，例如 `GOPATH/src/my_package`。然后在下面创建一个子目录，例如 `GOPATH/src/my_package/pkg1` 和 `GOPATH/src/my_package/pkg2`，以及相应的文件 `GOPATH/src/my_package/pkg1/pkg1.go` 和 `GOPATH/src/my_package/pkg2/pkg2.go`。然后，为了导入 `pkg2`，我们将编写 `import "my_package/pkg2"`。Go 源码中的 `archive` 包就是这种方法的示例。也可以在包本身编写代码（在本例中，通过创建 `GOPATH/src/my_package/my_package.go`）。查看源码中的 `image` 包作为此类示例。

Go 包是从 GOROOT 下（特别是 `$GOROOT/pkg/${GOOS}_${GOARCH}`，例如 `/opt/go/pkg/linux_64`）以及 GOPATH 环境变量下的目录导入的。这意味着可能会命名冲突。避免命名冲突简单方法是确保 GOPATH 路径具有唯一的目录，例如我们在 `omap` 包中使用的域名。

Go 程序与标准库包以及 GOPATH 路径中的包无缝工作，还可以理解后续小节中讨论的特定平台源文件。

### 9.1.1. 平台特定代码

在某些情况下，我们需要不同平台不同的代码。例如，在 Unix 类系统上，shell 执行通配符扩展（展开的 globbing），命令行上的 `*` 可能会被程序接收为例如 `os.Args[1:]` 切片中的 `"README.txt"` 和 `"INSTALL.txt"`。但在 Windows 上，程序将只得到 `*`。我们可以使用 `filepath.Glob()` 让程序执行此类 globbing，当然，我们只在 Windows 上这样做。

一种解决方案是在运行时通过 `if runtime.GOOS == "windows" { }` 测试来决定是否使用 `filepath.Glob()`，这是书中大部分示例（例如 `cgrep1/cgrep.go`）的做法。另一种解决方案是将平台特定代码放入其 `.go` 文件或文件中。例如，`cgrep3` 程序由三个文件组成：`cgrep.go`、`util_linux.go` 和 `util_windows.go`。在 `util_linux.go` 中定义了一个单一函数。

```go
func commandLineFiles(files []string)string { return files }
```

显然，这个函数没有进行任何 globbing，因为在 Linux 上不需要。`util_windows.go` 文件定义了一个同名的不同函数。

```go
func commandLineFiles(files []string)string {
  args := make([]string, 0, len(files))
  for _, name := range files {
    if matches, err := filepath.Glob(name); err != nil {
      args = append(args, name) // 无效模式
    } else if matches != nil { // 至少有一个匹配
      args = append(args, matches...)
    }
  }
  return args
}
```

### 9.1.2. 包文档

什么是良好的文档是一个争议的问题，因此在这个小节中，我们纯关注 Go 包文档的机制。

默认情况下，导出的类型、常量和变量都会被 godoc 显示，因此所有这些都应该编写文档。文档直接写在源码中。

```go
// Package omap 实现 // 键值可以是任何类型，但所有键必须能够
// 使用传递给 omap.New() 函数的 less 函数进行比较，
// 或 omap.New* 构造函数提供的 less 函数。
package omap
```
