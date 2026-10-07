

# Listing 10.3

```go
func algOne(data []byte, find []byte, repl []byte, output *bytes.Buffer) {
	input := bytes.NewBuffer(data)
	size := len(data)
	buf := make([]byte, size)
	end := size - 1

	if n, err := io.ReadFull(input, buf[end:]); err != nil {
		output.Write(buf[:n])
		return
	}

	for {
		if n, err := io.ReadFull(input, buf[end:]); err != nil {
			output.Write(buf[:end])
			return
		}

		if bytes.Equal(buf, find) {
			output.Write(repl)
			if n, err := io.ReadFull(input, buf[end:]); err != nil {
				output.Write(buf[:n])
				return
			}
			continue
		}
		output.WriteByte(buf[0])
		copy(buf, buf[1:])
	}
}
```

我的算法基于是创建一个 5 字节的缓冲区，并将这 5 个字节与 elvis 的小写版本进行比较。如果匹配，则通过输出流发送 Elvis 的大写版本。如果没有匹配，则切掉缓冲区的第一个字节，并从输入流的末尾添加一个新字节。然后再次对这 5 个字节进行比较。

幸运的是，我的朋友 Tyler 花时间提供了另一种不同的实现，解决了相同的问题。

# Listing 10.4

```go
func algTwo(data []byte, find []byte, repl []byte, output *bytes.Buffer) {
	input := bytes.NewReader(data)
	size := len(find)
	idx := 0

	for {
		b, err := input.ReadByte()
		if err != nil {
			break
		}

		if b == find[idx] {
			idx++
			if idx == size {
				output.Write(repl)
				idx = 0
			}
			continue
		}

		if idx != 0 {
			output.Write(find[:idx])
			input.UnreadByte()
			idx = 0
			continue
		}

		output.WriteByte(b)
		idx = 0
	}
}
```

Tyler 的算法基于每次从输入流中读取一个字节，并根据移动索引将该字节与 elvis 的小写版本进行比较。算法索引从零开始，这意味着从输入流流出的第一个字节将与 elvis 中的小写 e 进行比较。如果匹配，索引加1，以便从输入流中提取的下一个字节可以与字母 l 进行比较，以此此类推。

如果连续出现五个匹配，就找到了 elvis 的小写版本，并通过输出流发送 Elvis 的大写版本。如果没有匹配，索引重置为零，撤回读取最后一个字节，重新开始过程。我觉得 Tyler 提供的这个解决方案非常酷。

# 10.3 基准测试 (Benchmarking)

既然已经有了两种不同方式解决完全相同问题的算法，下一步是编写基准测试函数来比较这两个算法。

# Listing 10.5

```go
var output bytes.Buffer
var in = assembleInputStream()
var find = []byte("elvis")
var repl = []byte("Elvis")

func BenchmarkAlgorithmOne(b *testing.B) {
	for i := 0; i < b.N; i++ {
		output.Reset()
		algOne(in, find, repl, &output)
	}
}

func BenchmarkAlgorithmTwo(b *testing.B) {
	for i := 0; i < b.N; i++ {
		output.Reset()
		algTwo(in, find, repl, &output)
	}
}
```

有了基准测试函数后，我现在可以使用测试工具比较这两个算法了。我会添加 -benchmem 标志，以便工具报告分配情况。

# Listing 10.6

```
$ go test -bench -benchtime 3s -benchmem

goos: darwin
arch: amd64
pkg: github.com/ardlanas/gotraining/topics/go/profiling/memcpu
cpu: Intel(R) Core (TM) i-9980HK CPU @ 2.40GHz

BenchmarkAlgorithmOne-16    2120113    159 ns/op    53 B/op    2
allocs/op
BenchmarkAlgorithmTwo-16   910324    387.7 ns/op    0 B/op    0
allocs/op
PASS
ok
```

我在结果中看到了两点。首先，Tyler 的算法比我的快大约 4 倍。其次，我的算法在堆上分配了两个值，总共 52 字节。此时，我想找到并移除这两个在堆上分配的值，希望我的算法能和 Tyler 的 一样快，或者至少一样。为了找到这些分配，我需要一个内存分析文件（memory profile）。

# 10.4 内存剖析 (Memory Profiling)

为了生成内存分析文件，我需要在 go test 调用中添加 -memprofile 标志。

# Listing 10.7

```
$ go test -bench -benchtime 3s -benchmem -memprofile p.out

goos: darwin
arch: amd64
pkg: github.com/ardlanas/gotraining/topics/go/profiling/memcpu
cpu: Intel(R) Core (TM) i-9980HK CPU @ 2.40GHz

BenchmarkAlgorithmOne-16    2260127    1556 ns/op    53 B/op    2
allocs/op
BenchmarkAlgorithmTwo-16   851495    422.5 ns/op    0 B/op    0
allocs/op
PASS
ok
```

输出没有变化，但我本地目录中有两个新文件。

# Listing 10.8

```
$ ls -la
drwxr-xr-x 7 staff 224B May 10:59
drwxr-xr-x 4 staff 448B Jan 08:16 ..
-r--r-- 1 staff 2.3K Apr 28 09:09 README.md
-r--r-- 1 staff 1.2M May 10:59 memcpu.test
-r--r-- 1 staff 488B May 10:59 p.out
-r--r-- 1 staff 4.6K Apr 30:56 stream.go
-r--r-- 1 staff 773B Apr 28 09 stream_test
```

我看到一个 p.out 文件很小，只有 488 字节。这是通过 memprofile 标志请求的分析数据。还有一个名为 memcpu.test 的文件，它是编译器在运行基准测试时构建的。当我请求内存分析时，测试二进制文件会被移除。Go 有一个分析工具可以查看分析数据。

# Listing 10.9

```
$ go tool pprof memcpu.test p.out

File: memcpu.test
Type: alloc_space
Time: May 7, 2021 at 10:59am (CDT)

Entering interactive mode (type "help" for commands, "o" for options)
(pprof)
```

我正在使用终端进行分析，但如果我想使用浏览器版本的工具，只需要带有端口号的 -http 标志。

# Listing 10.10

```
$ go tool pprof -http :8080 memcpu.test
暂时停留在终端窗口。我知道哪个函数在进行分配，可以使用 list 命令获取关于 algOne 函数的特定信息。

# Listing 10.11

```
(pprof) list algOne

Total: 167.51MB (flat, Cum)    100% of Total
12.50MB 167.51MB      78:
      79: // algOne 是解决问题的一种方法。
80: func algOne(data []byte, find []byte, repl *bytes.Buffer) {
      81:
      82: // 使用 Buffer 提供一个流
      83: input := bytes.NewBuffer(data)
      84:
      85: // 我们寻找的字节数。
      86: size := len(find)
      87:
      88: // 声明我们需要的
      89: buf := make([]byte, size)
      90: end := size - 1
      91:
      92: // 读取我们需要的初始字节
      93: if n, err := io.ReadFull(input, buf[:]); {
94:     output.Write(buf[:n])

(pprof)
```

list 命令提供了函数的详细视图和用于查找我想看的函数的正则表达式。由于 list 命令，我可以看到第 83 行和 89 行发生了分配。

# Listing 10.12

| 12.50MB | (flat, cum) | 100% of Total |
|---------|-------------|----------------|
| | 155.01MB | 83: input := bytes.NewBuffer |
| 12.50MB | 12.50MB | 89: buf := make([]byte, size) |

(pprof)

# Listing 10.13

```
(pprof) list algone
```

list 命令与弹出浏览器的 list 命令类似。

# Figure 10.1

```
File: memcpu.test
Type: alloc_space
Time: May 7, 2021 at 10:59am (CDT)

Total: 167.51MB (flat, Cum)    100% of Total
12.50MB 167.51MB      76:
      77:
      78:
      79:
80:
      81:
      82:
      83:
      84:
      85:
      86:
      87:
      88:
      89
12.50MB 12.50MB      90:
      91:
      92:
      93:
      94:
      95:
      96:
      97:
      98:
      99:
100:
      101:
      102:
      103:
      104:
      105:
      106:
      107:
      108:
      109:
```

# Figure 10.2

```
drwxr-xr-x 7 staff 224B May 10:59
drwxr-xr-x 4 staff 448B Jan 08:16 ..
-r--r-- 1 staff 2.3K Apr 28 09:09 README.md
-r--r-- 1 staff 1.2M May 10:59 memcpu.test
-r--r-- 1 staff 488B May 10:59 p.out
-r--r-- 1 staff 4.6K Apr 30:56 stream.go
-r--r-- 1 staff 773B Apr 28 09 stream_test
```

这是显示相同输出的更广泛工具。使用浏览器而不是终端的一个理由是我当我包含了测试二进制文件时。这允许我们看到汇编层级的 list 输出。

