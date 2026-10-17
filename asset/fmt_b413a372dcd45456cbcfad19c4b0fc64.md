
### `read` 函数

```go
v.SetInt(int64(i))

lex.next()

return

case '(':

    lex.next()

    readList(lex, v)

    lex.next() // 消费 ')'

    return

}

panic(fmt.Sprintf("unexpected token %q", lex.text()))

}
```

我们的 S-表达式将标识符用于两个不同的目的：结构体字段名和指针的 `nil` 值。`read` 函数仅处理后一种情况。当它遇到 `scanner.Ident` `"nil"` 时，它使用 `reflect.Zero` 函数将 `v` 设置为其类型的零值。对于任何其他标识符，它会报告错误。稍后我们将看到的 `readList` 函数处理用作结构体字段名的标识符。

`'('` 标记表示列表的开始。第二个函数 `readList` 将列表解码为复合类型的变量——映射、结构体、切片或数组——具体取决于我们当前正在填充哪种 Go 变量。在每种情况下，循环都会持续解析项目，直到遇到匹配的右括号 `')'`，这由 `endList` 函数检测。

有趣的部分在于递归。最简单的情况是数组。在看到右括号 `')'` 之前，我们使用 `Index` 获取每个数组元素的变量，并进行递归调用 `read` 来填充它。与许多其他错误情况一样，如果输入数据导致解码器索引超出数组末尾，解码器会 panic。切片采用类似的方法，不同之处在于我们必须为每个元素创建一个新变量，填充它，然后将其追加到切片中。

结构体和映射的循环必须在每次迭代中解析一个 `(key value)` 子列表。对于结构体，键是标识字段的符号。类似于数组的情况，我们使用 `FieldByName` 获取结构体字段的现有变量，并进行递归调用来填充它。对于映射，键可以是任意类型，类似于切片的情况，我们创建一个新变量，递归填充它，最后将新的键/值对插入映射中。

### `readList` 和 `endList` 函数

```go
func readList(lex *lexer, v reflect.Value) {

    switch v.Kind() {

    case reflect.Array: // (item ...)

        for i := 0; !endList(lex); i++ {

            read(lex, v.Index(i))

        }

    case reflect.Slice: // (item ...)

        for !endList(lex) {

            item := reflect.New(v.Type().Elem()).Elem()

            read(lex, item)

            v.Set(reflect.Append(v, item))

        }

    case reflect.Struct: // ((name value) ...)

        for !endList(lex) {

            lex.consume('(')

            if lex.token != scanner.Ident {

                panic(fmt.Sprintf("got token %q, want field name", lex.text()))

            }

            name := lex.text()

            lex.next()

            read(lex, v.FieldByName(name))

            lex.consume(')')

        }

    case reflect.Map: // ((key value) ...)

        v.Set(reflect.MakeMap(v.Type()))

        for !endList(lex) {

            lex.consume('(')

            key := reflect.New(v.Type().Key()).Elem()

            read(lex, key)

            value := reflect.New(v.Type().Elem()).Elem()

            read(lex, value)

            v.SetMapIndex(key, value)

            lex.consume(')')

        }

    default:

        panic(fmt.Sprintf("cannot decode list into %v", v.Type()))

    }

}

func endList(lex *lexer) bool {

    switch lex.token {

    case scanner.EOF:

        panic("end of file")

    case ')':

        return true

    }

    return false

}
```

### `Unmarshal` 函数

最后，我们将解析器封装在一个导出函数 `Unmarshal` 中，如下所示，它隐藏了实现的一些粗糙边缘。解析过程中遇到的错误会导致 panic，因此 `Unmarshal` 使用延迟调用来从 panic 中恢复（§5.10）并返回错误信息。

```go
// Unmarshal 解析 S-表达式数据并填充非空指针 out 指向的变量。

func Unmarshal(data []byte, out interface{}) (err error) {

    lex := &lexer{scan: scanner.Scanner{Mode: scanner.GoTokens}}

    lex.scan.Init(bytes.NewReader(data))

    lex.next() // 获取第一个 token

    defer func() {

        // 注意：这不是理想错误处理的示例。

        if x := recover(); x != nil {

            err = fmt.Errorf("error at %s: %v", lex.scan.Position, x)

        }

    }()

    read(lex, reflect.ValueOf(out).Elem())

    return nil

}
```

生产级的实现永远不应该对任何输入 panic，并且应该为每个意外情况报告信息丰富的错误，也许还带有行号或偏移量。尽管如此，我们希望这个例子能传达一些关于 `encoding/json` 等包在底层发生了什么的概念，以及如何使用反射来填充数据结构。

### 练习

**练习 12.8：** `sexpr.Unmarshal` 函数与 `json.Marshal` 一样，在开始解码之前需要完整的输入字节切片。定义一个 `sexpr.Decoder` 类型，像 `json.Decoder` 一样，允许从 `io.Reader` 解码一系列值。更改 `sexpr.Unmarshal` 以使用这个新类型。

**练习 12.9：** 为解码 S-表达式编写一个基于 token 的 API，遵循 `xml.Decoder` 的风格（§7.14）。你需要五种类型的 token：`Symbol`、`String`、`Int`、`StartList` 和 `EndList`。

**练习 12.10：** 扩展 `sexpr.Unmarshal` 以处理你在练习 12.3 的解决方案中编码的布尔值、浮点数和接口。（提示：要解码接口，你需要一个从每个支持类型的名称到其 `reflect.Type` 的映射。）

## 12.7 访问结构体字段标签

在第 4.5 节中，我们使用结构体*字段标签*来修改 Go 结构体值的 JSON 编码。`json` 字段标签让我们可以选择替代的字段名并抑制空字段的输出。在本节中，我们将看到如何使用反射来访问字段标签。

在 Web 服务器中，大多数 HTTP 处理函数做的第一件事是将请求参数提取到局部变量中。我们将定义一个工具函数 `params.Unpack`，它使用结构体字段标签使编写 HTTP 处理器（§7.7）更加方便。

首先，我们将展示它是如何使用的。下面的 `search` 函数是一个 HTTP 处理器。它定义了一个名为 `data` 的匿名结构体类型变量，其字段对应 HTTP 请求参数。结构体的字段标签指定了参数名，这些参数名通常简短且晦涩，因为 URL 中空间宝贵。`Unpack` 函数从请求中填充结构体，以便可以方便地并以适当的类型访问参数。

```go
import "gopl.io/ch12/params"

// search 实现 /search URL 端点。

func search(resp http.ResponseWriter, req *http.Request) {

    var data struct {

        Labels     []string `http:"l"`

        MaxResults int      `http:"max"`

        Exact      bool     `http:"x"`

    }

    data.MaxResults = 10 // 设置默认值

    if err := params.Unpack(req, &data); err != nil {

        http.Error(resp, err.Error(), http.StatusBadRequest) // 400

        return

    }

    // ...处理器的其余部分...

    fmt.Fprintf(resp, "Search: %+v\n", data)

}
```

下面的 `Unpack` 函数执行三项任务。首先，它调用 `req.ParseForm()` 来解析请求。此后，`req.Form` 包含所有参数，无论 HTTP 客户端使用的是 GET 还是 POST 请求方法。

接下来，`Unpack` 会建立一个映射，从每个字段的*有效*名称到该字段对应的变量。如果字段带有标签，有效名称可能与实际名称不同。`reflect.Type` 的 `Field` 方法返回一个 `reflect.StructField`，它提供了关于每个字段类型的信息，如名称、类型和可选标签。`Tag` 字段是一个 `reflect.StructTag`，这是一个字符串类型，提供了一个 `Get` 方法来解析并提取特定键的子串，本例中即为 `http:"..."`。

```go
func Unpack(req *http.Request, ptr interface{}) error {

    if err := req.ParseForm(); err != nil {

        return err

    }

    // Build map of fields keyed by effective name.

    fields := make(map[string]reflect.Value)

    v := reflect.ValueOf(ptr).Elem() // the struct variable

    for i := 0; i < v.NumField(); i++ {

        fieldInfo := v.Type().Field(i) // a reflect.StructField

        tag := fieldInfo.Tag           // a reflect.StructTag

        name := tag.Get("http")

        if name == "" {

            name = strings.ToLower(fieldInfo.Name)

        }

        fields[name] = v.Field(i)

    }

    // Update struct field for each parameter in the request.

    for name, values := range req.Form {

        f := fields[name]

        if !f.IsValid() {

            continue // ignore unrecognized HTTP parameters

        }

        for _, value := range values {

            if f.Kind() == reflect.Slice {

                elem := reflect.New(f.Type().Elem()).Elem()

                if err := populate(elem, value); err != nil {

                    return fmt.Errorf("%s: %v", name, err)

                }

                f.Set(reflect.Append(f, elem))

            } else {

                if err := populate(f, value); err != nil {

                    return fmt.Errorf("%s: %v", name, err)

                }

            }

        }

    }

    return nil

}
```

最后，`Unpack` 遍历 HTTP 参数的名称/值对，并更新相应的结构体字段。请记住，同一个参数名可能出现多次。如果发生这种情况，且该字段是一个切片，则该参数的所有值都会累积到该切片中。否则，该字段会被反复覆写，以至于只有最后一个值生效。

`populate` 函数负责根据参数值设置单个字段 `v`（或切片字段的单个元素）。目前，它仅支持字符串、有符号整数和布尔值。支持其他类型留作练习。

```go
func populate(v reflect.Value, value string) error {

    switch v.Kind() {

    case reflect.String:

        v.SetString(value)

    case reflect.Int:

        i, err := strconv.ParseInt(value, 10, 64)

        if err != nil {

            return err

        }

        v.SetInt(i)

    case reflect.Bool:

        b, err := strconv.ParseBool(value)

        if err != nil {

            return err

        }

        v.SetBool(b)

    default:

        return fmt.Errorf("unsupported kind %s", v.Type())

    }

    return nil

}
```

如果我们将 `server` 处理器添加到 Web 服务器中，这可能是一个典型的会话：

```
$ go build gopl.io/ch12/search

$ ./search &

$ ./fetch 'http://localhost:12345/search'

Search: {Labels:[] MaxResults:10 Exact:false}

$ ./fetch 'http://localhost:12345/search?l=golang&l=programming'

Search: {Labels:[golang programming] MaxResults:10 Exact:false}

$ ./fetch 'http://localhost:12345/search?l=golang&l=programming&max=100'

Search: {Labels:[golang programming] MaxResults:100 Exact:false}

$ ./fetch 'http://localhost:12345/search?x=true&l=golang&l=programming'

Search: {Labels:[golang programming] MaxResults:10 Exact:true}

$ ./fetch 'http://localhost:12345/search?q=hello&x=123'

x: strconv.ParseBool: parsing "123": invalid syntax

$ ./fetch 'http://localhost:12345/search?q=hello&max=lots'

max: strconv.ParseInt: parsing "lots": invalid syntax
```
