

# 图 10.3

```
82      155.01MB  155.01MB
83              // 使用一个 bytes.Buffer 来提供
84              input := bytes.Buffer(data)
```

看第一列是如何显示与第二列相同的分配次数的。这引发了一个问题：分配是扁平的（flat），意味着 `input` 变量是在堆上构建的，还是累积的（cumulative），意味着分配来自 `bytes.ByteBuffer` 内部？

在我看来，浏览器的视图（browser view）更准确，因为它考虑了代码在执行时发生的一项重要的编译器优化，称为**内联**（inlining）。

## 10.5 内联 (Inlining)

内联是一种优化手段，它会移除函数调用并将其替换为目标函数内部代码的副本。由于某种原因，终端视图关闭了内联。

我该如何让终端在关闭内联的情况下显示 `list` 命令的结果呢？

## 列表 10.14

```
$ go tool pprof --noinlines memcpu.test p.out
```

我需要在调用 `go tool pprof` 时添加 `--noinlines` 标志，这本应该是关闭内联的，但在终端视图中它反而开启了。

## 列表 10.15 list algOne

```pprof
Total: 167.51MB
  167.51MB      167.51MB       100% of Total
      78:
        79:// algOne 是解决问题的方法之一。
        80:func algOne(data []byte, find []byte, repl
        81:
        82: // 使用 Buffer 提供一个流
  155.01MB      155.01MB      83: input := bytes.NewBuffer(data)
        84:
        85: // 我们寻找的字节数。
        86: size := len(find)
        87:
        88: // 定义我们需要处理的缓冲区
  12.500MB      12.500MB      89: buf := make([]byte, size)
        90: end := size - 1
        91:
        92: // 读取我们需要的初始字节
        93: if n, err := io.ReadFull(input, buf[:end]);
        94: output.Write(buf[:n])
```

终端视图显示 81 字节为扁平分配。内联实际上是如何工作的？从 `bytes.NewBuffer` 函数开始，我们知道它正被内联了。

## 列表 10.16

```go
func NewBuffer(buf []byte) *Buffer {
    return &Buffer{buf: buf}
}
```

我可以看到这是一个使用指针语义的工厂函数。调用者可以获取正在构建的 `Buffer` 值的访问权限。如果函数被调用，那么 `Buffer` 必须在堆上构建。这是因为所有权规则。

任何构建值的函数都是该值的所有者。如果该值在所有者函数返回后仍存在，那么该值必须在堆上构建。

如果函数可以被内联，那么构建的所有权就会移动到调用者函数。这意味着 `algOne` 函数拥有 `Buffer` 的构建所有权。

## 列表 10.17

```go
func algOne() {
    // 内联之前
    input := bytes.NewBuffer(data)    <-- 原始调用
    // 内联之后
    input := &bytes.Buffer{buf: data}    <-- 内联优化后
}
```

我看到在内联优化之后，`algOne` 函数成为了 `Buffer` 值构建的所有者，而不是 `NewBuffer` 函数。因此，除非该值在 `algOne` 函数返回后仍需存在，否则该值不需要逃逸到堆上。

值得注意的是，Tyler 的算法之所以是零分配算法，在某种程度上归功于同一种内联优化。

## 列表 10.18

```go
func algOne() {
    // 内联之前
    input := bytes.NewReader(data)    <-- 原始调用
    // 内联之后
    input := &bytes.Reader{buf: data}    <-- 内联优化后
}
```

由于 `NewReader` 函数被内联了，`Reader` 值的构建由 Tyler 的算法拥有。以某种方式，Tyler 在 `algTwo` 中似乎没有做任何会导致 `Reader` 值逃逸的操作，而我在 `algOne` 中对 `Buffer` 值做了某些处理。

## 10.6 逃逸分析 (Escape Analysis)

我如何知道内联绝对发生了？而我仍然不知道为什么 `algOne` 会导致分配而 `algTwo` 是零分配的？只有一个工具可以告诉我原因，那就是编译器。编译器正在使用逃逸分析算法做出决策。

幸运的是，编译器在运行任何内容之前会构建测试二进制文件，因此我可以要求编译器在运行基准测试之前生成逃逸分析报告。

## 列表 10.19

```
$ go test -bench . -bench 3s -benchmem -memprofile .out -gcflags -m=2
```

我在调用 `go test` 时添加了 `-gcflags -m=2` 标志。这在运行基准测试之前产生了一份逃逸分析报告。

## 列表 10.20

```
./stream.go:83:26 inlining call to bytes.NewBuffer()([]byte)
*Buffer { return &bytes.Buffer{...}}
./stream.go:83:26 &bytes.Buffer{...}
./stream.go:83:26 &bytes.Buffer{...}
./stream.go:83:26 input = &bytes.Buffer{...}
./stream.go:83:26 input = &bytes.Buffer{...}
./stream.go:83:26 input = &bytes.Buffer{...}
./stream.go:83:26 input = (interface-converted)
./stream.go:83:26 input = &bytes.Buffer{...}
./stream.go:83:26 input = &bytes.Buffer{...}
./stream.go:83:26 input = &bytes.Buffer{...}
./stream.go:83:26 input = &bytes.Buffer{...}
./stream.go:83:26 input = &bytes.Buffer{...}
./stream.go:83:26 input = &bytes.Buffer{...}
./stream.go:83:26 input = (interface-converted)
```

`streamstream.go:83:26 ` bytes.NewBuffer()` 的内联调用。
`*Buffer { return &bytes.Buffer{...}}`
`stream.go:83:26 ` &bytes.Buffer{...}
`stream.go:83:26 ` &bytes.Buffer{...}
`stream.go:83:26 ` &bytes.Buffer{...}
`stream.go:83:26 ` input = &bytes.Buffer{...}
`stream.go:83:26 ` input = &bytes.Buffer{...}
`stream.go:83:26 ` input = &bytes.Buffer{...}
`stream.go:83:26 ` input = (interface-converted)
`stream.go:83:26 ` input = &bytes.Buffer{...}
`stream.go:83:26 ` input = &bytes.Buffer{...}
`stream.go:83:26 ` input = &bytes.Buffer{...}
`stream.go:83:26 ` input = &bytes.Buffer{...}
`stream.go:83:26 ` input = &bytes.Buffer{...}
`stream.go:83:26 ` input = (interface-converted)
（注：此处原文内容似乎存在大量重复或乱码，已根据逻辑保留核心含义）

*更正：重新审视原文内容：*
```
./stream.go:83:26 inlining call to bytes.NewBuffer()([]byte)
*Buffer { return &bytes.Buffer{...}}
./stream.go:83:26 &bytes.Buffer{...}
```
（由于提供的文本中存在大量重复，以下为核心逻辑翻译）

`stream.go:83:26` 逃逸到堆。
`stream.go:83:26` 逃逸到堆。
`stream.go:83:26` 这种显示内联是必需的。
`stream.go:83:26 &bytes.Buffer{...}` 逃逸到堆。
`stream.go:83:26 &bytes.Buffer{...}` 逃逸到堆。
`stream.go:83:26 &bytes.Buffer{...}` 逃逸到堆。
`stream.go:83:26 input = &bytes.Buffer{...}`
`stream.go:83:26 input = &bytes.Buffer{...}`
`stream.go:83:26 input = &bytes.Buffer{...}`
`stream.go:83:26 input = (interface-converted)`
`stream.go:83:26 input = &bytes.Buffer{...}`
`stream.go:83:26 input = &bytes.Buffer{...}`
`stream.go:83:26 input = &bytes.Buffer{...}`

`stream.go:83:26` 的内联调用 `bytes.NewBuffer()`。
`*Buffer { return &bytes.Buffer{...}}`。
`stream.go:83:26` `&bytes.Buffer{...}`。

终端视图显示 81 字节为扁平分配。内联实际上是如何工作的？从 `bytes.NewBuffer` 函数开始，我们知道它正被内联了。

## 列表 10.16

```go
func NewBuffer(buf []byte) *Buffer {
    return &Buffer{buf: buf}
}
```

我可以看到这是一个使用指针语义的工厂函数。调用者可以获取正在构建的 `Buffer` 值的访问权限。如果函数被调用，那么 `Buffer` 必须在堆上构建。这是因为所有权规则。

任何构建值的函数都是该值的所有者。如果该值在所有者函数返回后仍存在，那么该值必须在堆上构建。

如果函数可以被内联，那么构建的所有权就会移动到调用者函数。这意味着 `algOne` 函数拥有 `Buffer` 的构建所有权。

## 列表 10.17

```go
func algOne() {
    // 内联之前
    input := bytes.NewBuffer(data)    <-- 原始调用
    // 内联之后
    input := &bytes.Buffer{buf: data}    <-- 内联优化后
}
```

我看到在内联优化之后，`algOne` 函数成为了 `Buffer` 值构建的所有者，而不是 `NewBuffer` 函数。因此，除非该值在 `algOne` 函数返回后仍需存在，否则该值不需要逃逸到堆上。

值得注意的是，Tyler 的算法之所以是零分配算法，在某种程度上归功于同一种内联优化。

## 列表 10.18

```go
func algOne() {
    // 内联之前
    input := bytes.NewReader(data)    <-- 原始调用
    // 内联之后
    input := &bytes.Reader{buf: data}    <-- 内联优化后
}
```

由于 `NewReader` 函数被内联了，`Reader` 值的构建由 Tyler 的算法拥有。以某种方式，Tyler 在 `algTwo` 中似乎没有做任何会导致 `Reader` 值逃逸的操作，而我在 `algOne` 中对 `Buffer` 值做了某些处理。

## 10.6 逃逸分析 (Escape Analysis)

我如何知道内联绝对发生了？而我仍然不知道为什么 `algOne` 会导致分配而 `algTwo` 是零分配的？只有一个工具可以告诉我原因，那就是编译器。编译器正在使用逃逸分析算法做出决策。

幸运的是，编译器在运行任何内容之前会构建测试二进制文件，因此我可以要求编译器在运行基准测试之前生成逃逸分析报告。

## 列表 10.19

```
$ go test -bench . -bench 3s -benchmem -memprofile .out -gcflags -m=2
```

我在调用 `go test` 时添加了 `-gcflags -m=2` 标志。这在运行基准测试之前产生了一份逃逸分析报告。

## 列表 10.20

```
./stream.go:83:26 inlining call to bytes.NewBuffer()([]byte)
*Buffer { return &bytes.Buffer{...}}
```
（注：原文列表 10.20 包含大量重复行，此处翻译了其核心分析含义）

`stream.go:83:26` `bytes.NewBuffer()` 的内联调用。
`*Buffer { return &bytes.Buffer{...}}`。
`stream.go:83:26` `&bytes.Buffer{...}` 逃逸到堆。
`stream.go:83:26` `input = &bytes.Buffer{...}`。
`stream.go:83:26` `input = (interface-converted)`。

终端视图显示 81 字节为扁平分配。内联实际上是如何工作的？从 `bytes.NewBuffer` 函数开始，我们知道它正被内联了。

