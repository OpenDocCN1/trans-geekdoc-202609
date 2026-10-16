
信息关于第二个分隔符之后的数据块，以判断它是否也是一个完整的消息。如果你再读取 1KB 的数据并未发现分隔符，你可以得出结论：这整个数据块是上一次阅读的 1KB 中最后一个消息的延续。但如果你读取的 1KB 里全是分隔符呢？

如果这听起来有点复杂，那是因为你必须处理多次 Read 调用之间的数据，并妥善处理可能出现的错误。

**76** 第 4 章

任何当你想自己实现此类问题的解决方案时，请先检查标准库，看是否已有成熟的实现。此例中，bufio.Scanner 正好满足需求。

bufio.Scanner 是 Go 标准库中一个便利的代码片段，用于读取带分隔的数据。Scanner 接受 io.Reader 作为输入。由于 net.Conn 的 Read 方法实现了 io.Reader 接口，你可以轻松使用 Scanner 从网络连接中读取带分隔的数据。Listing 4-2 设置了一个监听器，用于提供后续由 bufio.Scanner 解析的带分隔数据。

package main

import (
	"bufio"
	"net"
	"reflect"
	"testing"
)

const payload = "The bigger the interface, the weaker the abstraction."

func TestScanner(t *testing.T) {
	listener, err := net.Listen("tcp", "127.0.0.1:")
	if err != nil {
		t.Fatal(err)
	}
	go func() {
		conn, err := listener.Accept()
		if err != nil {
			t.Error(err)
			return
		}
		defer conn.Close()
		_, err = conn.Write([]byte(payload))
		if err != nil {
			t.Error(err)
		}
	}()

	*--snip--*

Listing 4-2：创建测试以提供常量 payload（ scanner_test.go ） 此监听器在你已经熟悉。它的作用仅是提供 payload 1。Listing 4-3 使用 bufio.Scanner 从网络读取字符串，按空白字符分割每个片段。

conn, err := net.Dial("tcp", listener.Addr().String())
if err != nil {
	Sending TCP Data **77**
	t.Fatal(err)
}
defer conn.Close()
scanner := bufio.NewScanner(conn)
scanner.Split(bufio.ScanWords)
var words []string
for scanner.Scan() {
	words = append(words, scanner.Text())
}
err = scanner.Err()
if err != nil {
	t.Error(err)
}
expected := []string{"The", "bigger", "the", "interface,", "the", "weaker", "the", "abstraction."}
if !reflect.DeepEqual(words, expected) {
	t.Fatal("inaccurate scanned word list")
}
t.Logf("Scanned words: %#v", words)
}

Listing 4-3：使用 bufio.Scanner 从网络读取以空白字符分隔的文本（ scanner_test.go ）

由于你知道你要从服务器读取字符串，首先创建一个 bufio.Scanner 读取网络连接 1。默认情况下，Scanner 会在流中遇到换行字符 ( \n ) 时分割数据。相反，你可以通过 bufio.ScanWords 让 Scanner 在遇到单词边界（如空白或句末标点）时分割数据。

你会持续从 scanner 读取数据，只要它表明已读取到连接上的数据 2。每次调用 Scan 可能会多次调用网络连接的 Read 方法，直到 Scanner 找到分隔符或从连接读取错误为止。它隐藏了在多次网络读取之间查找分隔符的复杂性，并返回相应的消息。

调用 scanner 的 Text 方法会返回它刚从连接读取到的那段数据——一个单词及其紧随的标点，例如 3。代码会一直循环，直到 scanner 收到 io.EOF 或其他连接错误。若是后者，Scanner 的 Err 方法会返回非 nil 错误。你可以通过在 go test 命令后加 -v 标志来查看已扫描的单词 4。

**78** 第 4 章

 ***Dynamical y Al ocating the Buffer Size***

你可以在协商好协议的前提下，从网络连接读取长度不一的数据。

*type-length-value* (TLV) 编码方案是一个不错的选择。TLV 编码使用固定字节数表示数据类型，固定字节数表示值的大小，并使用可变字节数表示值本身。我们的实现使用 5 字节的报头：1 字节用于类型，4 字节用于长度。TLV 编码让你能够以字节序列的形式向远程节点发送类型，并在此字节序列上在远程节点上重新构造相同的类型。

Listing 4-4 定义了我们 TLV 编码协议将接受的类型。

package main

import (
	"bytes"
	"encoding/binary"
	"errors"
	"fmt"
	"io"
)

const (
	1 BinaryType uint8 = iota + 1
	2 StringType
	3 MaxPayloadSize uint32 = 10 << 20 // 10 MB
)

var ErrMaxPayloadSize = errors.New("maximum payload size exceeded")

type Payload interface {
	fmt.Stringer
	io.ReaderFrom
	io.WriterTo
	Bytes() []byte
}

Listing 4-4：消息结构体实现了简单协议（ types.go ）

你首先创建常量来表示你将要定义的每种类型。

在本例中，你会创建 BinaryType 1 和 StringType 2。在消化每种类型的实现细节后，你就能创建符合需求的类型。为了安全考虑（我们稍后会讨论），必须定义一个最大 payload 大小 3。

你还定义了一个名为 Payload 的 interface 4，描述每种类型必须实现的方法。每种类型都必须实现以下方法：

- Bytes
- String
- ReadFrom
- WriteTo

io.ReaderFrom 与 io.WriterTo 接口允许你的类型从读取器读取数据、向写入者写入数据。

你在此时有灵活性。你可以让 Payload 直接实现 encoding.BinaryMarshaler 接口来序列化为字节切片，或实现 encoding.BinaryUnmarshaler 接口来反序列化。但字节切片是相对于网络连接的一层 removed，所以我们保持 Payload 接口不变。此外，你将在下一章节使用二进制编码接口。

你现在已有构建 TLV‑based 类型的基础。Listing 4-5 详细说明了第一种类型——Binary。

*\--snip--*

type Binary []byte

func (m Binary) Bytes() []byte { return m }

func (m Binary) String() string { return string(m) }

func (m Binary) WriteTo(w io.Writer) (int64, error) {
	err := binary.Write(w, binary.BigEndian, BinaryType) // 1-byte type
	if err != nil {
		return 0, err
	}
	var n int64 = 1
	err = binary.Write(w, binary.BigEndian, uint32(len(m))) // 4-byte size
	if err != nil {
		return n, err
	}
	n += 4
	o, err := w.Write(m) // payload
	return n + int64(o), err
}

Listing 4-5：创建 Binary 类型（ types.go ）

Binary 类型 1 是字节切片；因此其 Bytes 方法 2 直接返回自身。其 String 方法 3 将自身转换为字符串后返回。

WriteTo 方法接受 io.Writer 并返回写入到 writer 的字节数以及错误 4。它首先写入 1 字节的类型到 writer 5，然后写入 4 字节的 Binary 长度到 writer 6，最后写入 Binary 本身 7。

Listing 4-6 为 Binary 类型补全其 ReadFrom 方法。

*\--snip--*

func (m *Binary) ReadFrom(r io.Reader) (int64, error) {
	var typ uint8
	err := binary.Read(r, binary.BigEndian, &typ) // 1-byte type
	if err != nil {
		return 0, err
	}
	var n int64 = 1
	if typ != 2BinaryType {
		**80** Chapter 4
		return n, errors.New("invalid Binary")
	}
	var size uint32
	err = binary.Read(r, binary.BigEndian, &size) // 4-byte size
	if err != nil {
		return n, err
	}
	n += 4
	if size > MaxPayloadSize {
		return n, ErrMaxPayloadSize
	}
	return n, nil
}

