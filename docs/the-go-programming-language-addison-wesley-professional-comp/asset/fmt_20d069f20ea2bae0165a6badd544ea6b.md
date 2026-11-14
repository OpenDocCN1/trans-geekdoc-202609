
## 12.7 结构体字段标签与 HTTP 参数

在 [4.5 节](#part0040.html#id-json) 中，我们使用结构体 *field tags* 来修改 Go 结构体值的 JSON 编码。`json` 字段标签允许我们选择替代字段名并抑制空字段的输出。在本节中，我们将看到如何使用反射访问字段标签。

在 Web 服务器中，大多数 HTTP 处理函数首先做的事情是将请求参数提取到局部变量中。我们将定义一个工具函数 `params.Unpack`，它利用结构体字段标签使编写 HTTP 处理器（[§7.7](#part0067.html#id-httphandler)）更加方便。

首先，我们展示如何使用它。下面的 `search` 函数是一个 HTTP 处理器。它定义了一个名为 `data` 的变量，类型是匿名结构体，其字段对应 HTTP 请求参数。结构体的字段标签指定了参数名，这些参数名通常简短且晦涩，因为 URL 中空间宝贵。`Unpack` 函数从请求中填充结构体，以便方便地以适当的类型访问参数。

`gopl.io/ch12/search`

```go
import "gopl.io/ch12/params"

// search implements the /search URL endpoint.
func search(resp http.ResponseWriter, req *http.Request) {
    var data struct {
        Labels     []string `http:"l"`
        MaxResults int      `http:"max"`
        Exact      bool     `http:"x"`
    }
    data.MaxResults = 10 // set default
    if err := params.Unpack(req, &data); err != nil {
        http.Error(resp, err.Error(), http.StatusBadRequest) // 400
        return
    }

    // ...rest of handler...
    fmt.Fprintf(resp, "Search: %+v\n", data)
}
```

下面的 `Unpack` 函数做三件事。首先，它调用 `req.ParseForm()` 解析请求。此后，`req.Form` 包含所有参数，无论 HTTP 客户端使用 GET 还是 POST 请求方法。

接下来，`Unpack` 从每个字段的 *有效* 名称建立到该字段变量的映射。如果字段有标签，有效名称可能与实际名称不同。`reflect.Type` 的 `Field` 方法返回一个 `reflect.StructField`，提供关于每个字段的信息，如名称、类型和可选标签。`Tag` 字段是一个 `reflect.StructTag`，它是一个字符串类型，提供 `Get` 方法来解析并提取特定键的子串，例如本例中的 `http:"..."`。

`gopl.io/ch12/params`

```go
// Unpack populates the fields of the struct pointed to by ptr
// from the HTTP request parameters in req.
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

最后，`Unpack` 遍历 HTTP 参数的名称/值对并更新相应的结构体字段。回想一下，同一个参数名可能出现多次。如果发生这种情况，且字段是切片，则该参数的所有值都会累积到切片中。否则，字段会被反复覆盖，只有最后一个值生效。

`populate` 函数负责从参数值设置单个字段 `v`（或切片字段的单个元素）。目前它仅支持字符串、有符号整数和布尔值。支持其他类型留作练习。

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

如果我们将 `server` 处理器添加到 Web 服务器，这可能是一个典型会话：

```bash
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

### 练习 12.11

编写相应的 `Pack` 函数。给定一个结构体值，`Pack` 应返回一个包含来自结构体的参数值的 URL。

### 练习 12.12

扩展字段标签表示法以表达参数有效性要求。例如，字符串可能需要是有效的电子邮件地址或信用卡号，整数可能需要是有效的美国邮政编码。修改 `Unpack` 以检查这些要求。

### 练习 12.13

修改 S 表达式编码器（[§12.4](#part0115.html#id-exampleencodingsexpressions)）和解码器（[§12.6](#part0117.html#id-exampledecodingsexpressions)），使它们以类似于 `encoding/json`（[§4.5](#part0040.html#id-json)）的方式遵守 `sexpr:"..."` 字段标签。

## 12.8 显示类型的方法集

我们最后一个反射示例使用 `reflect.Type` 打印任意值的类型并枚举其方法：

`gopl.io/ch12/methods`

```go
// Print prints the method set of the value x.
func Print(x interface{}) {
    v := reflect.ValueOf(x)
    t := v.Type()
    fmt.Printf("type %s\n", t)

    for i := 0; i < v.NumMethod(); i++ {
        methType := v.Method(i).Type()
        fmt.Printf("func (%s) %s%s\n", t, t.Method(i).Name,
            strings.TrimPrefix(methType.String(), "func"))
    }
}
```
