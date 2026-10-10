

# bzip2 算法与 cgo 集成

bzip2 算法基于优雅的 Burrows-Wheeler 变换，其运行速度比 gzip 慢，但能产生显著更好的压缩率。`compress/bzip2` 包提供了 bzip2 的解压器，但目前该包不提供压缩器。从头构建一个是一项重大的工程，但有一个文档完善且高性能的开源 C 语言实现，即来自 `bzip.org` 的 `libbzip2` 包。

如果 C 库很小，我们只需将其移植为纯 Go 代码；如果其性能对我们的目的而言并不关键，我们最好使用 `os/exec` 包调用 C 程序作为辅助子进程。只有当你需要使用一个具有狭窄 C API 的复杂、性能关键型库时，使用 `cgo` 进行封装才说得通。在本章的其余部分，我们将通过一个示例来演示。

从 `libbzip2` C 包中，我们需要 `bz_stream` 结构体类型，它保存输入和输出缓冲区，以及三个 C 函数：`BZ2_bzCompressInit`，用于分配流的缓冲区；`BZ2_bzCompress`，将数据从输入缓冲区压缩到输出缓冲区；以及 `BZ2_bzCompressEnd`，用于释放缓冲区。（不必担心 `libbzip2` 包的内部机制；此示例的目的是展示各部分如何组合在一起。）

我们将直接从 Go 调用 `BZ2_bzCompressInit` 和 `BZ2_bzCompressEnd` C 函数，但对于 `BZ2_bzCompress`，我们将在 C 中定义一个封装函数，以展示如何操作。下面的 C 源文件与我们包中的 Go 代码共存：

[点击此处查看代码图像](#ch13_images.html#id362pro01_r)

gopl.io/ch13/bzip

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

[点击此处查看代码图像](#ch13_images.html#id362pro02_r)

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

在预处理期间，`cgo` 会生成一个临时包，其中包含与文件使用的所有 C 函数和类型对应的 Go 声明，例如 `C.bz_stream` 和 `C.BZ2_bzCompressInit`。`cgo` 工具通过以特殊方式调用 C 编译器处理 import 声明前的注释内容，来发现这些类型。

注释中还可能包含 `#cgo` 指令，用于指定传递给 C 工具链的额外选项。`CFLAGS` 和 `LDFLAGS` 的值为编译器和链接器命令提供额外参数，以便它们能找到 `bzlib.h` 头文件和 `libbz2.a` 归档库。示例假设这些文件安装在你系统的 `/usr` 目录下。你可能需要根据你的安装情况修改或删除这些标志。

`NewWriter` 通过调用 C 函数 `BZ2_bzCompressInit` 来初始化流的缓冲区。`writer` 类型包含另一个缓冲区，用于排空压缩器的输出缓冲区。

如下所示，`Write` 方法将未压缩的 `data` 送入压缩器，在循环中调用 `bz2compress` 函数，直到所有数据被消耗完毕。请注意，Go 程序可以通过 `C.x` 表示法访问 C 类型（如 `bz_stream`、`char` 和 `uint`）、C 函数（如 `bz2compress`），甚至类对象的 C 预处理器宏（如 `BZ_RUN`）。`C.uint` 类型不同于 Go 的 `uint` 类型，即使两者具有相同的宽度。

[点击此处查看代码图像](#ch13_images.html#id363pro01_r)

```go
func (w *writer) Write(data []byte) (int, error) {
    if w.stream == nil {
        panic("closed")
    }
    var total int // uncompressed bytes written

    for len(data) > 0 {
        inlen, outlen := C.uint(len(data)), C.uint(cap(w.outbuf))
        C.bz2compress(w.stream, C.BZ_RUN,
            (*C.char)(unsafe.Pointer(&data[0])), &inlen,
            (*C.char)(unsafe.Pointer(&w.outbuf)), &outlen)
        total += int(inlen)
        data = data[inlen:]
        if _, err := w.w.Write(w.outbuf[:outlen]); err != nil {
            return total, err
        }
    }
    return total, nil
}
```

循环的每次迭代将 `data` 剩余部分的地址和长度，以及 `w.outbuf` 的地址和容量传递给 `bz2compress`。这两个长度变量通过其地址而非值传递，以便 C 函数可以更新它们，指示消耗了多少未压缩数据以及产生了多少压缩数据。然后将每块压缩数据写入底层的 `io.Writer`。

`Close` 方法的结构与 `Write` 类似，使用循环将流输出缓冲区中剩余的任何压缩数据刷新出去。

[点击此处查看代码图像](#ch13_images.html#id364pro01_r)

```go
// Close flushes the compressed data and closes the stream.
// It does not close the underlying io.Writer.
func (w *writer) Close() error {
    if w.stream == nil {
        panic("closed")
    }
    defer func() {
        C.BZ2_bzCompressEnd(w.stream)
        w.stream = nil
    }()
    for {
        inlen, outlen := C.uint(0), C.uint(cap(w.outbuf))
        r := C.bz2compress(w.stream, C.BZ_FINISH, nil, &inlen,
            (*C.char)(unsafe.Pointer(&w.outbuf)), &outlen)
        if _, err := w.w.Write(w.outbuf[:outlen]); err != nil {
            return err
        }
        if r == C.BZ_STREAM_END {
            return nil
        }
    }
}
```

完成后，`Close` 调用 `C.BZ2_bzCompressEnd` 释放流缓冲区，使用 `defer` 确保在所有返回路径上都会发生此操作。此时 `w.stream` 指针不再安全解引用。为了防御性编程，我们将其设为 `nil`，并在每个方法中添加显式的 nil 检查，以便在用户错误地在 `Close` 后调用方法时程序会 panic。不仅 `writer` 不是并发安全的，而且对 `Close` 和 `Write` 的并发调用可能导致程序在 C 代码中崩溃。修复此问题请参见[练习 13.3](#ebook_split_124.html#id-bzipmutex)。

下面的程序 `bzipper` 是一个使用我们新包的 bzip2 压缩命令。其行为类似于许多 Unix 系统上存在的 `bzip2` 命令。

[点击此处查看代码图像](#ch13_images.html#id365pro01_r)

gopl.io/ch13/bzipper

```go
// Bzipper reads input, bzip2-compresses it, and writes it out.
package main

import (
    "io"
    "log"
    "os"

    "gopl.io/ch13/bzip"
)

func main() {
    w := bzip.NewWriter(os.Stdout)
    if _, err := io.Copy(w, os.Stdin); err != nil {
        log.Fatalf("bzipper: %v\n", err)
    }
    if err := w.Close(); err != nil {
        log.Fatalf("bzipper: close: %v\n", err)
    }
}
```

