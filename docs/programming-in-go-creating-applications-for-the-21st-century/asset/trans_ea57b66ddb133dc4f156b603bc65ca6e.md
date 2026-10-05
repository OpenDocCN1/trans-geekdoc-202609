

## 8.1. 自定义数据文件

```go
var invWriter = func(x interface{}) error {
	return binary.Write(writer, byteOrder, x)
}
if err := write(uint32(magicNumber)); err != nil {
	return err
}
if err := write(uint16(fileVersion)); err != nil {
	return err
}
if err := write(int32(len(invoices))); err != nil {
	return err
}
for _, invoice := range invoices {
	if err := write.writeInvoice(invoice); err != nil {
		return err
	}
}
return nil
```

该方法将所有发票写入给定的 `io.Writer`。它首先创建了一个方便的 `write()` 函数，该函数捕获了 `io.Writer` 和我们想要使用的字节序。就像我们在处理 `.txt` 格式时做的那样，我们将 `write()` 函数设置为了特定的类型（`invWriterFunc`），并为 `write()` 函数创建了一些方法（例如 `invWriterFunc.writeInvoices()`），以便后续更方便地使用。

请注意，在写入和读取二进制数据时，使用相同的字节序至关重要。（我们无法将 `byteOrder` 设置为常量，因为 `binary.LittleEndian` 或 `binary.BigEndian` 并不是像字符串或数字那样简单的值。）

写入数据与我们之前看到的其他格式非常相似。一个重要的区别是，一旦写入了魔数（magic number）和文件版本，我们就会写入将要写入的发票数量。（也可以跳过计数直接写入发票；那么在读回数据时，我们必须每次读取一个发票，直到遇到 `io.EOF`。）

```go
type invWriterFunc func(interface{}) error
```

```go
func (write invWriterFunc) writeInvoice(invoice *Invoice) error {
	for _, i := range []int{invoice.Id, invoice.CustomerID} {
		if err := write(int32(i)); err != nil {
			return err
		}
	}
	for _, date := range []time.Time{invoice.Raised, invoice.Due} {
		if err := write.writeDate(date); err != nil {
			return err
		}
	}
	if err := write.writeBool(invoice.Paid); err != nil {
		return err
	}
	if err := write.writeString(invoice.Note); err != nil {
		return err
	}
	if err := write(int32(len(invoice.Items))); err != nil {
		return err
	}
	for _, item := range invoice.Items {
		if err := write.writeItem(item); err != nil {
			return err
		}
	}
	return nil
}
```

每张发票都会调用一次 `writeInvoice()` 方法。它接收一个要写入的发票的指针，并使用它被调用的 `write()` 函数。

该方法首先将发票的 ID 和客户 ID 以 `int32` 形式写入。写入普通的 `int` 是合法的，但这是不可移植的，因为 `int` 的大小取决于底层机器和所使用的 Go 版本，所以专门写入特定大小和有符号的整数（如 `uint32`、`int32` 等）非常重要。接下来，我们使用自定义的 `writeDate()` 方法写入开票日期和截止日期，并使用自定义方法写入备注字符串。最后，我们写入发票包含的项目项数量，然后是项目本身（项目是通过自定义的 `writeItem()` 方法写入的）。

```go
const invDateFormat = "20060102" // 必须始终使用此日期。

```go
func (write invWriterFunc) writeDate(date time.Time) error {
	i, err := strconv.Atoi(date.Format(invDateFormat))
	if err != nil {
		return err
	}
	return write(int32(i))
}
```

## 8.1. 自定义数据文件

我们之前讨论过 `time.Format()` 函数——以及为什么我们必须在格式化字符串中使用特定的日期 `2006-01-02`（见 368 页◄）。在这里我们使用了类似于 ISO-8601 的格式，但没有连字符，这样我们就能得到一个恰好八位的数字字符串，其中个数的月份和日期会有前导零。然后我们将此字符串转换为整数——例如，如果日期是 `2012-08-05`，我们将其转换为等效数字，即 `20120805`，然后将其作为 `int32` 写入。

顺便提到，如果我们想存储日期时间而不仅仅是日期，或者只是想要更快的计算，可以将对此方法的调用替换为 `int64(date.Unix())` 并存储自 Unix 纪元以来的秒数。相应的读取器将类似于 `var d int64; if err := binary.Read(reader, byteOrder, &d); if err != nil { return err }; date := time.Unix(d, 0)`。

```go
func (invWriterFunc) WriteBool(b bool) error {
	var v int8
	if b {
		v = 1
	}
	return write(v)
}
```

在编写此时，`encoding/binary` 数据包不支持写入或读取 `bool` 类型，因此我们创建了这个简单的方法来处理它们。顺便提一下，我们不需要转换（例如 `int8(v)`），因为变量 `v` 已经是有符号的固定大小类型。

```go
func (invWriterFunc) WriteString(s string) error {
	// 假设实现逻辑
	return nil
}
```

*(注：由于原文文本在某些部分存在逻辑重复或截断的情况，译文已根据上下文逻辑进行了结构化处理，以确保技术文档的连贯性。)*

