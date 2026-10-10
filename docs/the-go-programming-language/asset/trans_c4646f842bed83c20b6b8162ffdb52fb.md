

## 考虑 `os` 包中文件操作返回的错误集合

I/O 可能因各种原因失败，但通常必须区别处理三种失败：文件已存在（针对创建操作）、文件未找到（针对读取操作）和权限被拒绝。`os` 包提供了三个辅助函数，用于对给定 `error` 值指示的失败进行分类：

[点击此处查看代码图片](#ch07_images.html#id207pro01_r)

```go
package os

func IsExist(err error) bool
func IsNotExist(err error) bool
func IsPermission(err error) bool
```

一个简单的实现可能会检查错误消息是否包含特定子串：

[点击此处查看代码图片](#ch07_images.html#id207pro02_r)

```go
func IsNotExist(err error) bool {
    // NOTE: not robust!
    return strings.Contains(err.Error(), "file does not exist")
}
```

但由于处理 I/O 错误的逻辑可能因平台而异，这种方法不够健壮，同一种失败可能会用各种不同的错误消息报告。检查错误消息的子串在测试期间可能有用，以确保函数按预期方式失败，但不适用于生产代码。

一种更可靠的方法是使用专用类型表示结构化错误值。`os` 包定义了一个名为 `PathError` 的类型，用于描述涉及文件路径操作（如 `Open` 或 `Delete`）的失败，以及一个名为 `LinkError` 的变体，用于描述涉及两个文件路径的操作（如 `Symlink` 和 `Rename`）的失败。以下是 `os.PathError`：

[点击此处查看代码图片](#ch07_images.html#id207pro03_r)

```go
package os

// PathError records an error and the operation and file path that caused it.
type PathError struct {
    Op   string
    Path string
    Err  error
}

func (e *PathError) Error() string {
    return e.Op + " " + e.Path + ": " + e.Err.Error()
}
```

大多数客户端不关心 `PathError`，而是通过调用其 `Error` 方法以统一方式处理所有错误。虽然 `PathError` 的 `Error` 方法通过简单拼接字段来形成消息，但 `PathError` 的结构保留了错误的底层组件。需要区分不同失败类型的客户端可以使用类型断言来检测错误的具体类型；具体类型提供的细节比简单字符串更多。

[点击此处查看代码图片](#ch07_images.html#id207pro04_r)

```go
_, err := os.Open("/no/such/file")
fmt.Println(err) // "open /no/such/file: No such file or directory"
fmt.Printf("%#v\n", err)
// Output:
// &os.PathError{Op:"open", Path:"/no/such/file", Err:0x2}
```

这正是这三个辅助函数的工作原理。例如，下面展示的 `IsNotExist` 报告错误是否等于 `syscall.ENOENT`（参见 [§7.8](#ebook_split_067.html#id-theerrorinterface)）或特定错误 `os.ErrNotExist`（参见 [§5.4.2](#ebook_split_045.html#id-endoffileeof) 中的 `io.EOF`），或者是一个其底层错误为上述两者之一的 `*PathError`。

[点击此处查看代码图片](#ch07_images.html#id208pro01_r)

```go
import (
    "errors"
    "syscall"
)

var ErrNotExist = errors.New("file does not exist")

// IsNotExist returns a boolean indicating whether the error is known to
// report that a file or directory does not exist. It is satisfied by
// ErrNotExist as well as some syscall errors.
func IsNotExist(err error) bool {
    if pe, ok := err.(*PathError); ok {
        err = pe.Err
    }
    return err == syscall.ENOENT || err == ErrNotExist
}
```

实际效果如下：

[点击此处查看代码图片](#ch07_images.html#id208pro02_r)

```go
_, err := os.Open("/no/such/file")
fmt.Println(os.IsNotExist(err)) // "true"
```

当然，如果错误消息被组合成更大的字符串（例如通过调用 `fmt.Errorf`），`PathError` 的结构就会丢失。错误判别通常必须在失败操作后立即进行，在错误传播给调用者之前。

## 7.12 使用接口类型断言查询行为

下面的逻辑类似于 `net/http` Web 服务器中负责写入 HTTP 头字段（如 `"Content-type: text/html"`）的部分。`io.Writer` `w` 代表 HTTP 响应；写入其中的字节最终会发送到某人的 Web 浏览器。

[点击此处查看代码图片](#ch07_images.html#id208pro03_r)

```go
func writeHeader(w io.Writer, contentType string) error {
    if _, err := w.Write([]byte("Content-Type: ")); err != nil {
        return err
    }
    if _, err := w.Write([]byte(contentType)); err != nil {
        return err
    }
    // ...
}
```

因为 `Write` 方法需要字节切片，而我们想写入的是字符串，所以需要 `[]byte(...)` 转换。这种转换会分配内存并进行复制，但复制品几乎在转换后立即被丢弃。假设这是 Web 服务器的核心部分，且性能分析显示这种内存分配拖慢了速度。我们能否避免在此处分配内存？

`io.Writer` 接口仅告诉我们关于 `w` 所持有的具体类型的一个事实：可以向其写入字节。如果我们查看 `net/http` 包的内部实现，会发现 `w` 在此程序中持有的动态类型还有一个 `WriteString` 方法，允许高效地写入字符串，避免了分配临时副本的需要。（这看似是碰运气，但许多满足 `io.Writer` 的重要类型也有 `WriteString` 方法，包括 `*bytes.Buffer`、`*os.File` 和 `*bufio.Writer`。）

我们不能假设任意 `io.Writer` `w` 也有 `WriteString` 方法。但我们可以定义一个仅包含此方法的新接口，并使用类型断言来测试 `w` 的动态类型是否满足这个新接口。

[点击此处查看代码图片](#ch07_images.html#id209pro01_r)

```go
// writeString writes s to w.
// If w has a WriteString method, it is invoked instead of w.Write.
func writeString(w io.Writer, s string) (n int, err error) {
    type stringWriter interface {
        WriteString(string) (n int, err error)
    }
    if sw, ok := w.(stringWriter); ok {
        return sw.WriteString(s) // avoid a copy
    }
    return w.Write([]byte(s)) // allocate temporary copy
}

func writeHeader(w io.Writer, contentType string) error {
    if _, err := writeString(w, "Content-Type: "); err != nil {
        return err
    }
    if _, err := writeString(w, contentType); err != nil {
        return err
    }
    // ...
}
```

为了避免重复代码，我们将检查移到了工具函数 `writeString` 中，但它非常有用，以至于标准库将其作为 `io.WriteString` 提供。这是向 `io.Writer` 写入字符串的推荐方式。

这个例子有趣的是，没有标准接口定义 `WriteString` 方法并指定其所需行为。此外，具体类型是否满足 `stringWriter` 接口仅由其方法决定，而不由它与接口类型之间的任何声明关系决定。这意味着上述技术依赖于这样一个假设：*如果*一个类型满足下面的接口，*那么* `WriteString(s)` 必须与 `Write([]byte(s))` 具有相同的效果。

[点击此处查看代码图片](#ch07_images.html#id210pro01_r)

```go
interface {
    io.Writer
    WriteString(s string) (n int, err error)
}
```

