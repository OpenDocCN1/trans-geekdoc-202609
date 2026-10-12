
没有指针引用由 `new` 创建的变量，因此垃圾收集器有权在该语句完成后回收其存储空间，此后 `pT` 包含的是变量曾经所在的地址，但变量已不复存在。

目前没有 Go 实现使用移动式垃圾收集器（尽管未来的实现可能会），但这不是掉以轻心的理由：当前版本的 Go 确实会移动 **某些** 变量。回顾 5.2 节，goroutine 栈会按需增长。发生这种情况时，旧栈上的所有变量可能被重定位到一个新的、更大的栈上，所以我们不能依赖变量地址的数值在其生命周期内保持不变。

撰写本书时，关于 Go 程序员在 `unsafe.Pointer` 转 `uintptr` 后可以依赖什么，几乎没有明确的指导（参见 Go issue 7192），因此我们强烈建议你假设最低限度的保证。将所有 `uintptr` 值视为包含变量的 *旧* 地址，并将 `unsafe.Pointer` 转换为 `uintptr` 与使用该 `uintptr` 之间的操作数量降到最低。在上面的第一个示例中，三个操作——转换为 `uintptr`、加上字段偏移量、转换回指针——都出现在单个表达式中。

当调用返回 `uintptr` 的库函数时，例如 `reflect` 包中的以下函数，结果应立即转换为 `unsafe.Pointer`，以确保它继续指向同一个变量。

```go
package reflect

func (Value) Pointer() uintptr

func (Value) UnsafeAddr() uintptr

func (Value) InterfaceData() [2]uintptr // (索引 1)
```

## 13.3 示例：深度相等

`reflect` 包中的 `DeepEqual` 函数用于报告两个值是否“深度”相等。`DeepEqual` 使用内置的 `==` 运算符比较基本值；对于复合值，它会递归遍历它们，比较对应的元素。因为它适用于任意一对值，甚至包括那些无法用 `==` 比较的值，所以它在测试中被广泛使用。以下测试使用 `DeepEqual` 来比较两个 `[]string` 值：

```go
func TestSplit(t *testing.T) {
    got := strings.Split("a:b:c", ":")
    want := []string{"a", "b", "c"}
    if !reflect.DeepEqual(got, want) { /* ... */ }
}
```

虽然 `DeepEqual` 很方便，但它的区分标准可能显得武断。例如，它不认为 nil map 等于非 nil 的空 map，也不认为 nil slice 等于非 nil 的空 slice：

```go
var a, b []string = nil, []string{}
fmt.Println(reflect.DeepEqual(a, b)) // "false"

var c, d map[string]int = nil, make(map[string]int)
fmt.Println(reflect.DeepEqual(c, d)) // "false"
```

在本节中，我们将定义一个函数 `Equal` 来比较任意值。与 `DeepEqual` 一样，它基于元素比较 slice 和 map，但与 `DeepEqual` 不同，它认为 nil slice（或 map）等于非 nil 的空 slice（或 map）。对参数的基本递归可以通过反射完成，使用类似于我们在 12.3 节 中看到的 `Display` 程序的方法。像往常一样，我们定义一个未导出的函数 `equal` 用于递归。暂时不用担心 `seen` 参数。对于要比较的每一对值 `x` 和 `y`，`equal` 检查两者是否都有效（或都无效），并检查它们是否具有相同的类型。函数的结果定义为一组 switch case，用于比较两个相同类型的值。由于篇幅限制，我们省略了几个 case，因为到现在为止这种模式应该已经很熟悉了。

```go
// gopl.io/ch13/equal
func equal(x, y reflect.Value, seen map[comparison]bool) bool {
    if !x.IsValid() || !y.IsValid() {
        return x.IsValid() == y.IsValid()
    }
    if x.Type() != y.Type() {
        return false
    }
    // ...循环检查省略（稍后展示)...
    switch x.Kind() {
    case reflect.Bool:
        return x.Bool() == y.Bool()
    case reflect.String:
        return x.String() == y.String()
    // ...为简洁起见省略了数值 case...
    case reflect.Chan, reflect.UnsafePointer, reflect.Func:
        return x.Pointer() == y.Pointer()
    case reflect.Ptr, reflect.Interface:
        return equal(x.Elem(), y.Elem(), seen)
    case reflect.Array, reflect.Slice:
        if x.Len() != y.Len() {
            return false
        }
        for i := 0; i < x.Len(); i++ {
            if !equal(x.Index(i), y.Index(i), seen) {
                return false
            }
        }
        return true
    // ...为简洁起见省略了 struct 和 map case...
    }
    panic("unreachable")
}
```

像往常一样，我们不在 API 中暴露反射的使用，因此导出函数 `Equal` 必须对其参数调用 `reflect.ValueOf`：

```go
// Equal 报告 x 和 y 是否深度相等。
func Equal(x, y interface{}) bool {
    seen := make(map[comparison]bool)
    return equal(reflect.ValueOf(x), reflect.ValueOf(y), seen)
}

type comparison struct {
    x, y unsafe.Pointer
    t    reflect.Type
}
```

为了确保算法即使对于循环数据结构也能终止，它必须记录已经比较过哪些变量对，并避免第二次比较它们。`Equal` 分配一组 `comparison` 结构体，每个结构体保存两个变量的地址（表示为 `unsafe.Pointer` 值）和比较的类型。我们除了地址之外还需要记录类型，因为不同的变量可能具有相同的地址。例如，如果 `x` 和 `y` 都是数组，`x` 和 `x[0]` 具有相同的地址，`y` 和 `y[0]` 也是如此，区分我们是比较了 `x` 和 `y` 还是 `x[0]` 和 `y[0]` 非常重要。

一旦 `equal` 确定其参数具有相同类型，并在执行 switch 之前，它会检查是否在比较两个已经见过的变量，如果是，则终止递归。

```go
// 循环检查
if x.CanAddr() && y.CanAddr() {
    xptr := unsafe.Pointer(x.UnsafeAddr())
    yptr := unsafe.Pointer(y.UnsafeAddr())
    if xptr == yptr {
        return true // 相同引用
    }
    c := comparison{xptr, yptr, x.Type()}
    if seen[c] {
        return true // 已见过
    }
    seen[c] = true
}
```

这是我们的 `Equal` 函数的实际运行效果：

```go
fmt.Println(Equal([]int{1, 2, 3}, []int{1, 2, 3}))        // "true"
fmt.Println(Equal([]string{"foo"}, []string{"bar"}))      // "false"
fmt.Println(Equal([]string(nil), []string{}))             // "true"
fmt.Println(Equal(map[string]int(nil), map[string]int{})) // "true"
```

它甚至适用于类似于导致 12.3 节 中的 `Display` 函数陷入循环的循环输入：

```go
// 循环链表 a -> b -> a 和 c -> c。
type link struct {
    value string
    tail  *link
}

a, b, c := &link{value: "a"}, &link{value: "b"}, &link{value: "c"}
a.tail, b.tail, c.tail = b, a, c

fmt.Println(Equal(a, a)) // "true"
fmt.Println(Equal(b, b)) // "true"
fmt.Println(Equal(c, c)) // "true"
fmt.Println(Equal(a, b)) // "false"
fmt.Println(Equal(a, c)) // "false"
```

**练习 13.1：** 定义一个深度比较函数，如果两个数字（任意类型）的差异小于十亿分之一，则认为它们相等。

**练习 13.2：** 编写一个函数，报告其参数是否为循环数据结构。

## 13.4 使用 `cgo` 调用 C 代码

Go 程序可能需要使用 C 实现的硬件驱动程序、查询 C++ 实现的嵌入式数据库，或使用 Fortran 实现的某些线性代数例程。C 长期以来一直是编程领域的通用语言，因此许多旨在广泛使用的包都会导出兼容 C 的 API，无论其实现语言是什么。

在本节中，我们将构建一个简单的数据压缩程序，它使用 `cgo`，这是一个为 C 函数创建 Go 绑定的工具。此类工具称为*外部函数接口*（FFI），`cgo` 并不是 Go 程序唯一的此类工具。SWIG (`swig.org`) 是另一个；它提供了与 C++ 类集成的更复杂功能，但我们这里不演示它。

标准库的 `compress/...` 子树为流行的压缩算法提供了压缩器和解压缩器，包括 LZW（Unix `compress` 命令使用）和 DEFLATE（GNU `gzip` 命令使用）。这些包的 API 在细节上略有不同，但它们都为 `io.Writer` 提供了一个压缩写入数据的包装器，并为 `io.Reader` 提供了一个解压缩读取数据的包装器。例如：

```go
package gzip // compress/gzip

func NewWriter(w io.Writer) io.WriteCloser
func NewReader(r io.Reader) (io.ReadCloser, error)
```

### bzip2 算法与 cgo 集成

bzip2 算法基于优雅的 Burrows-Wheeler 变换，其运行速度比 gzip 慢，但能产生显著更好的压缩率。`compress/bzip2` 包提供了 bzip2 的解压器，但目前该包不提供压缩器。从头构建一个是一项重大的工程，但有一个文档完善且高性能的开源 C 语言实现，即来自 `bzip.org` 的 `libbzip2` 包。

如果 C 库很小，我们只需将其移植为纯 Go 代码；如果其性能对我们的目的而言并不关键，我们最好使用 `os/exec` 包调用 C 程序作为辅助子进程。只有当你需要使用一个具有狭窄 C API 的复杂、性能关键型库时，使用 `cgo` 进行封装才说得通。在本章的其余部分，我们将通过一个示例来演示。

从 `libbzip2` C 包中，我们需要 `bz_stream` 结构体类型，它保存输入和输出缓冲区，以及三个 C 函数：`BZ2_bzCompressInit`，用于分配流的缓冲区；`BZ2_bzCompress`，将数据从输入缓冲区压缩到输出缓冲区；以及 `BZ2_bzCompressEnd`，用于释放缓冲区。（不必担心 `libbzip2` 包的内部机制；此示例的目的是展示各部分如何组合在一起。）

我们将直接从 Go 调用 `BZ2_bzCompressInit` 和 `BZ2_bzCompressEnd` C 函数，但对于 `BZ2_bzCompress`，我们将在 C 中定义一个封装函数，以展示如何操作。下面的 C 源文件与我们包中的 Go 代码共存：

```c
/* This file is gopl.io/ch13/bzip/bzip2.c,         */
/* a simple wrapper for libbzip2 suitable for cgo. */
#include <bzlib.h>

int bz2compress(bz_stream *s, int action,
                char *in, unsigned *inlen, char *out, unsigned *outlen) {
  s->next_in = in;
  s->avail_in = *inlen;
  s->next_out = out;
  s->avail_out = *outlen;
  int r = BZ2_bzCompress(s, action);
  *inlen -= s->avail_in;
  *outlen -= s->avail_out;
  return r;
}
```

现在让我们转向 Go 代码，其第一部分如下所示。`import "C"` 声明是特殊的。不存在名为 `C` 的包，但此导入会导致 `go build` 在 Go 编译器看到文件之前，使用 `cgo` 工具对文件进行预处理。

```go
// Package bzip provides a writer that uses bzip2 compression (bzip.org).
package bzip

/*
#cgo CFLAGS: -I/usr/include
#cgo LDFLAGS: -L/usr/lib -lbz2
#include <bzlib.h>

int bz2compress(bz_stream *s, int action,
                char *in, unsigned *inlen, char *out, unsigned *outlen);
*/
import "C"

import (
    "io"
    "unsafe"
)

type writer struct {
    w      io.Writer // underlying output stream
    stream *C.bz_stream
    outbuf [64 * 1024]byte
}

// NewWriter returns a writer for bzip2-compressed streams.
func NewWriter(out io.Writer) io.WriteCloser {
    const (
        blockSize  = 9
        verbosity  = 0
        workFactor = 30
    )
    w := &writer{w: out, stream: new(C.bz_stream)}
    C.BZ2_bzCompressInit(w.stream, blockSize, verbosity, workFactor)
    return w
}
```
