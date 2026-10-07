
```go
type Item struct {
    Id       string
    Price    float64
    Quantity int
    Note     string
}
```

```go
type XMLItem struct {
    XMLName xml.Name `xml:"ITEM"`
    Id       string `xml:",attr"`
    Price    float64 `xml:",attr"`
    Quantity int `xml:",attr"`
    Note     string `xml:"NOTE"`
}
```

`XMLItem` 的字段被标记为属性，但 `Note` 字段将成为一个嵌套的 `<NOTE>` 标签，且 `XMLName` 字段持有项目自身的 XML 标签名。

正如我们在处理 JSON 格式时所的那样，对于 XML，我们创建了一个空结构体，以便与 XML 特有的 `MarshalInvoices()` 和 `UnmarshalInvoices()` 方法相关联。

这实现了我们之前看到的通用 `InvoicesMarshaller` 和 `InvoicesUnmarshaler` 接口（365）。

```go
func (XMLMarshaller) MarshalInvoices(writer io.Writer, 
    invoices []*Invoice) error {
    if _, err := writer.Write([]byte(xml.Header)); err != nil {
        return err
    }
    xmlInvoices := XMLInvoicesForInvoices(invoices)
    encoder := xml.NewEncoder(writer)
    return encoder.Encode(xmlInvoices)
}
```

该方法接收一个 `io.Writer`（即任何满足 `io.Writer` 接口的对象，我们可以向其中写入打开的文件或压缩文件）。该方法开始写入标准的 XML 头部 `<?xml version="1.0"?>`（`xml.Header` 的内容也包含尾随换行符）。然后它将所有的 `Invoices` 及其项目转换为等效的 XML 结构。尽管这看起来会消耗与原始数据一样多的内存，但由于 Go 的字符串是不可变的，在底层只有原始字符串的引用会被复制到 XML 结构体中，因此开销并没看起来那么大。对于直接使用 XML 标签的应用程序，没有转换转换。

一旦我们填充了 `xmlInvoices`（类型为 `XMLInvoices`），我们就创建一个新的 `xml.Encoder`，并将其传递给我们想要写入的 `io.Writer`。然后我们将所有数据编码为 XML 并返回编码器的返回值——该值将是错误 `error` 或 `nil`。

```go
func XMLInvoicesForInvoices(invoices []*Invoice) *XMLInvoices {
    xmlInvoices := &XMLInvoices{
        Version: version,
        Invoice: make([]*XMLInvoice, 0, len(invoices)),
    }
    for _, invoice := range invoices {
        xmlInvoices.Invoice = append(xmlInvoices.Invoice, invoice)
    }
    return xmlInvoices
}
```

此函数接收一个 `[]*Invoice` 并返回等效的 `*XMLInvoice`。转换非常直接；我们简单地将 `Invoice` 值复制到相应的字段中。由于我们选择了自己处理 `Raised` 和 `Due` 日期（以便我们只存储值而不是时间），因此我们将它们转换为了字符串。对于 `Invoice.Items`，我们将每个项目作为 `XMLItem` 添加到 `XMLInvoice` 切片中。

```go
func XMLInvoiceForInvoice(invoice *Invoice) *XMLInvoice {
    xmlInvoice := &XMLInvoice{
        Id: invoice.Id,
        CustomerID: invoice.CustomerID,
        Raised: invoice.Raised.String(),
        Due: invoice.Due.String(),
        Paid: invoice.Paid,
        Note: invoice.Note,
        Items: make([]*XMLItem, 0, len(invoice.Items)),
    }
    for _, item := range invoice.Items {
        xmlItem := &XMLItem{
            Id: item.Id,
            Price: item.Price,
            Quantity: item.Quantity,
            Note: item.Note,
        }
        xmlInvoice.Items = append(xmlInvoice.Items, xmlItem)
    }
    return xmlInvoice
}
```

## 8.1.2. 读取 XML 文件

读取 XML 文件比写入稍微复杂一些，特别是当我们必须解析某些字段（如日期）时；但如果使用合适的 XML 标签结构体，这并不困难。

```go
func (XMLMarshaller) UnmarshalInvoices(reader io.Reader) ([]*Invoice,
error) {
    xmlInvoices := &XMLInvoices{}
    decoder := xml.NewDecoder(reader)
    if err := decoder.Decode(xmlInvoices); err != nil {
        return nil, err
    }
    if xmlInvoices.Version > fileVersion {
        return nil, fmt.Errorf("version %d is too new to read",
        xmlInvoices.Version)
    }
    return xmlInvoices, nil
}
```

该方法接收一个 `io.Reader`（即任何满足 `io.Reader` 接口的对象，例如打开的文件或压缩文件），从中读取 XML。该方法开始创建一个空 `XMLInvoices` 结构体的指针和一个用于读取 `io.Reader` 的 `xml.Decoder`。随后整个 XML 文件由 `xml.Decoder.Decode()` 方法解析，如果解析成功，则 `XMLInvoices` 结构体将被填充 XML 文件的数据。如果解析失败（例如，存在 XML 语法错误或文件不是发票），解码器将返回一个错误，我们将其将其传递给调用者。

# 第 8 章 文件处理

检查版本，如果它是我们可以转换的版本，我们就可以将所有的 XML 结构体转换回程序内部使用的结构体。自然地，如果我们使用了带有 XML 标签的结构体，这种转换将是不必要的。

```go
func (xmlInvoices *XMLInvoices) Invoices() ([]*Invoice,
    err error) {
    invoices := make([]*Invoice, len(xmlInvoices.Invoices))
    for _, xmlInvoices := range xmlInvoices.Invoices {
        invoice, err := xmlInvoices.Invoice()
        if err != nil {
            return nil, err
        }
        invoices = append(invoices, invoice)
    }
    return invoices, nil
}
```

`XMLInvoices.Invoices()` 方法将 *XMLInvoices* 转换为 *[]*Invoice*。它是 `XMLInvoicesForInvoices()` 函数 (374 ◄) 的逆操作，并将所有的转换工作交给了 `XMLInvoice.Invoice()` 方法。

```go
func (xmlInvoice *XMLInvoice) Invoice() (invoice *Invoice, err error) {
    invoice := &Invoice{
        Id: xmlInvoice.Id,
        CustomerId: xmlInvoice.CustomerId,
        Paid: xmlInvoice.Paid,
        Note: strings.TrimSpace(xmlInvoice.Note),
        Items: make([]*Item, 0, len(xmlInvoice.Item)),
    }
    if invoice.Raised, err = time.Parse(dateFormat, xmlInvoice.Raised); err != nil {
        return nil, err
    }
    if invoice.Due, err = time.Parse(dateFormat, xmlInvoice.Due); err != nil {
        return nil, err
    }
    for _, xmlItem := range xmlInvoice.Item {
        item := &Item{
            Id: xmlItem.Id,
            Price: xmlItem.Price,
            Quantity: xmlItem.Quantity,
            Note: strings.TrimSpace(xmlItem.Note),
        }
        invoice.Items = append(invoice.Items, item)
    }
    return invoice, nil
}
```

## 8.1. 自定义数据文件

此 `XMLInvoice.Invoice()` 方法用于返回一个与其调用的 *XMLInvoice* 等效的 *Invoice*。

该方法首先创建一个 `Invoice`，其大部分字段从 `XMLInvoice` 填充，`Items` 字段被设置为一个具有足够容量以容纳项目的空切片。

当手动填充包含两个日期/时间值的字段时，由于我们选择了自己处理这些内容。`time.Parse()` 函数接收一个日期/时间字符串（如前所述，必须基于精确的日期/时间 2006-01-02T15:04:05Z07:00）和一个要解析的字符串，并返回等效的 `time.Time` 和或 nil 错误。

接下来，通过遍历 `XMLInvoice` 中 `Item` 字段的 *XMLItems* 来填充发的 `Items` 字段，并创建相应的 *Items*。最后，返回 *Invoice*。

在编写 XML 时，我们不需要担心读取的任何 XML 的反转义——`xml.Decoder.Decode()` 函数可以自动处理这些。

`xml` 包支持比我们这里需要的更复杂的标签，带有嵌套功能。例如，标签名 `xml:content="Books>Author"` 将导致 XML `<Books><Author></Author></Books>`。此外，除了 `xml:attr` 之外，该包还支持 `xml:chardata` 和 `xml:` 将字段作为字符数据写入，`xml:innerxml` 将字段原文写入，以及 `xml:comment` 将字段作为 XML 注释写入。通过使用标记的结构体，我们可以充分利用方便的编码和解码函数，同时对 XML 的写入和读取实现相当大的控制。

### 8.1.3. 处理纯文本文件

对于纯文本文件，我们必须创建自定义格式，理想情况下是易于解析和扩展的。

以下是自定义文本格式中单张发票的数据。

```
INVOICE ID=5441 CUSTOMER=960 RAISED=2012-09-06 DUE=2012-10-06 PAID=true
ITEM ID=BE9066 PRICE=400.89 QUANTITY=7 Keep out of <direct> sunlight
ITEM ID=AM7240 PRICE=183.69 QUANTITY=2
ITEM ID=PT9110 PRICE=105.40 QUANTITY=3: Flammable
```

每张发票的格式是一个 `Invoice` 行，然后是一个或多个 `ITEM` 行，最后是一个分页符。每一行（无论是发票还是其项目）具有相同的本质结构：一个识别行类型的单词、一系列由空格分隔的键值对，以及可选的冒号加空格后跟注释文本。

### 8.1.3.1. 写入纯文本文件

得益于 Go 强大灵活的 `fmt` 包函数，写入纯文本是非常直接的。（这些是在之前创建的；$3.5, 93）。

```go
type TxtMarshaler struct{}{}

func (t *TxtMarshaler) MarshalInvoices(writer io.Writer,
    invoices []Invoice) err error {
    bufferedWriter := bufio.NewWriter(writer)
    defer bufferedWriter.Flush()
    var writeWriter writerFunc = func(format string,
        args ...interface{}) error {
        err := fmt.Fprintf(bufferedWriter, format, args...)
        return err
    }
    if err := writeWriter("%s\n", invoice); err != nil {
        return err
    }
    for _, invoice := range invoices {
        if err := writeWriter("INVOICE ID=%d CUSTOMER=%d RAISED=%s DUE=%s PAID=%t\n",
            invoice.Id, invoice.CustomerId, invoice.Raised, invoice.Due, invoice.Paid); err != nil {
            return err
        }
        if invoice.Items != nil {
            for _, item := range invoice.Items {
                note := ""
                if item.Note != "" {
                    note = " " + item.Note
                }
                if err := writeWriter("ITEM ID=%s PRICE=%.2f QUANTITY=%d%s\n",
                    item.Id, item.Price, item.Quantity, note); err != nil {
                    return err
                }
            }
        }
    }
    err = writer.WriteByte('\x0c')
    return err
}
```

## 8.1. 自定义数据文件

```go
err = nil              // io.EOF 并不是真正的错误
eof = true               // 这将在下次迭代时结束循环
} else if err != nil {
    return nil, err // 遇到真实错误时立即返回
}
if invoices, err = parseTxtLine(lino, line, invoices); err != nil {
    return nil, err
}
```

该方法为它传入的 `io.Reader` 创建了一个缓冲读取器，并将每一行依次传递给解析函数。按照处理文本文件的惯例，我们专门处理了 `io.EOF`，以确保无论最后一行是否以换行符结束，都能读取到最后一行。（当然，对于这种特定格式来说，这种处理相当宽松。）

文件按照惯例使用基于索引的行号逐行读取。首先检查第一行以确保其具有有效的文件类型，因此在处理实际发票数据时，行号（lino）从 2 开始。

由于我们是按行处理的，且每张发票由两行或多行组成（一个发票行或更多项目 ITEM 行），我们需要跟踪当前的发票，以便在读取每行时进行添加。这很容易实现，因为发票被追加到 `invoices` 切片中，所以当前发票始终位于 `invoices[len(invoices)-1]` 的位置。

当 `parseTxtLine()` 函数解析发票 LINE 时，它会创建一个新的发票值并将该值的指针添加到 `invoices` 切片中。

如果我们想在函数内部向切片追加内容，可以使用两种技术。第一种技术是传递切片的指针并对所指向的内容进行操作。第二种技术是传递切片的值并将（可能修改过的）切片返回给调用者，以便将其赋值给原始切片。`parseTxtLine()` 函数使用了第二种技术。（我们之前看过该函数的示例：$5.7, 244 ◀）

```go
func parseTxtLine(lino int, line string, invoices []*Invoice) ([]*Invoice, error) {
    var err error
    if strings.HasPrefix(line, "INVOICE") {
        var invoice *Invoice
        invoice, err = parseTxtInvoice(lino, line)
        invoices = append(invoices, invoice)
    } else if strings.HasPrefix(line, "ITEM") {
        if len(invoices) == 0 {
```

