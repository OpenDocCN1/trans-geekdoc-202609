
# S-表达式编码

正如我们在 [`第 4.5 节`](#part0040.html#id-json) 中所见，Go 标准库支持多种格式，包括 JSON、XML 和 ASN.1。另一种仍被广泛使用的表示法是 *S-表达式*，即 Lisp 的语法。与其他表示法不同，S-表达式不被 Go 标准库支持，这至少部分是因为尽管有过几次标准化尝试且存在许多实现，但它们没有被普遍接受的定义。

在本节中，我们将定义一个包，使用支持以下结构的 S-表达式表示法来编码任意 Go 对象：

[点击此处查看代码图像](#part0142_split_020.html#id338pro01_r)

```
42             整数
"hello"        字符串（采用 Go 风格引号）
foo            符号（一个未加引号的名称）
(1 2 3)        列表   （用括号括起的零个或多个项）
```

布尔值传统上使用符号 `t` 表示真，用空列表 `()` 或符号 `nil` 表示假，但为求简单，我们的实现将忽略它们。它也忽略通道和函数，因为它们的状态对反射不可见。并且它忽略实数和复数浮点数以及接口。为它们添加支持是 [`练习 12.3`](#part0115.html#id-encodecases)。

我们将使用 S-表达式按如下方式编码 Go 的类型。整数和字符串以显而易见的方式编码。空值编码为符号 `nil`。数组和切片使用列表表示法编码。

结构体编码为字段绑定的列表，每个字段绑定是一个双元素列表，其第一个元素（一个符号）是字段名，第二个元素是字段值。映射也编码为键值对的列表，每个键值对是一个映射条目的键和值。传统上，S-表达式使用单个 *cons* 单元 `(key . value)` 来表示每个键值对，而不是双元素列表，但为简化解码，我们将忽略点对列表表示法。

编码由单个递归函数 `encode` 完成，如下所示。其结构本质上与上一节中的 `Display` 相同：

[点击此处查看代码图像](#part0142_split_021.html#id339pro01_r)

`gopl.io/ch12/sexpr`

```
func encode(buf *bytes.Buffer, v reflect.Value) error {
    switch v.Kind() {
    case reflect.Invalid:
        buf.WriteString("nil")

    case reflect.Int, reflect.Int8, reflect.Int16,
        reflect.Int32, reflect.Int64:
        fmt.Fprintf(buf, "%d", v.Int())

    case reflect.Uint, reflect.Uint8, reflect.Uint16,
        reflect.Uint32, reflect.Uint64, reflect.Uintptr:
        fmt.Fprintf(buf, "%d", v.Uint())

    case reflect.String:
        fmt.Fprintf(buf, "%q", v.String())

    case reflect.Ptr:
        return encode(buf, v.Elem())

    case reflect.Array, reflect.Slice: // (value ...)
        buf.WriteByte('(')
        for i := 0; i < v.Len(); i++ {
            if i > 0 {
                buf.WriteByte(' ')
            }
            if err := encode(buf, v.Index(i)); err != nil {
                return err
            }
        }
        buf.WriteByte(')')

    case reflect.Struct: // ((name value) ...)
        buf.WriteByte('(')
        for i := 0; i < v.NumField(); i++ {
            if i > 0 {
                buf.WriteByte(' ')
            }
            fmt.Fprintf(buf, "(%s ", v.Type().Field(i).Name)
            if err := encode(buf, v.Field(i)); err != nil {
                return err
            }
            buf.WriteByte(')')
        }
        buf.WriteByte(')')

    case reflect.Map: // ((key value) ...)
        buf.WriteByte('(')
        for i, key := range v.MapKeys() {
            if i > 0 {
                buf.WriteByte(' ')
            }
            buf.WriteByte('(')
            if err := encode(buf, key); err != nil {
                return err
            }
            buf.WriteByte(' ')
            if err := encode(buf, v.MapIndex(key)); err != nil {
                return err
            }
            buf.WriteByte(')')
        }
        buf.WriteByte(')')

    default: // float, complex, bool, chan, func, interface
        return fmt.Errorf("unsupported type: %s", v.Type())
    }
    return nil
}
```

`Marshal` 函数将编码器封装在一个类似于其他 `encoding/...` 包的 API 中：

[点击此处查看代码图像](#part0142_split_022.html#id340pro01_r)

```
// Marshal 以 S-表达式形式编码 Go 值。
func Marshal(v interface{}) ([]byte, error) {
    var buf bytes.Buffer
    if err := encode(&buf, reflect.ValueOf(v)); err != nil {
        return nil, err
    }
    return buf.Bytes(), nil
}
```

下面是将 `Marshal` 应用于 [`第 12.3 节`](#part0114.html#id-display) 中 `strangelove` 变量的输出：

[点击此处查看代码图像](#part0142_split_023.html#id340pro02_r)

```
((Title "Dr. Strangelove") (Subtitle "How I Learned to Stop Worrying and Lo
ve the Bomb") (Year 1964) (Actor (("Grp. Capt. Lionel Mandrake" "Peter Sell
ers") ("Pres. Merkin Muffley" "Peter Sellers") ("Gen. Buck Turgidson" "Geor
ge C. Scott") ("Brig. Gen. Jack D. Ripper" "Sterling Hayden") ("Maj. T.J. \
"King\" Kong" "Slim Pickens") ("Dr. Strangelove" "Peter Sellers"))) (Oscars
("Best Actor (Nomin.)" "Best Adapted Screenplay (Nomin.)" "Best Director (N
omin.)" "Best Picture (Nomin.)")) (Sequel nil))
```

整个输出显示在一行上，空格极少，难以阅读。这是根据 S-表达式约定手动格式化后的相同输出。编写 S-表达式的美化打印器作为一个（有挑战性的）练习留给读者；`gopl.io` 的下载包含一个简单版本。

[点击此处查看代码图像](#part0142_split_024.html#id341pro01_r)

```
((Title "Dr. Strangelove")
 (Subtitle "How I Learned to Stop Worrying and Love the Bomb")
 (Year 1964)
 (Actor (("Grp. Capt. Lionel Mandrake" "Peter Sellers")
         ("Pres. Merkin Muffley" "Peter Sellers")
         ("Gen. Buck Turgidson" "George C. Scott")
         ("Brig. Gen. Jack D. Ripper" "Sterling Hayden")
         ("Maj. T.J. \"King\" Kong" "Slim Pickens")
         ("Dr. Strangelove" "Peter Sellers")))
 (Oscars ("Best Actor (Nomin.)"
          "Best Adapted Screenplay (Nomin.)"
          "Best Director (Nomin.)"
          "Best Picture (Nomin.)"))
 (Sequel nil))
```

与 `fmt.Print`、`json.Marshal` 和 `Display` 函数一样，如果用循环数据调用 `sexpr.Marshal`，它将永远循环下去。

在 [`第 12.6 节`](#part0117.html#id-exampledecodingsexpressions) 中，我们将概述相应的 S-表达式解码函数的实现，但在此之前，我们首先需要了解如何使用反射来更新程序变量。

## 练习

**练习 12.3：** 实现 `encode` 函数缺失的情况。将布尔值编码为 `t` 和 `nil`，使用 Go 的表示法编码浮点数，将像 `1+2*i` 这样的复数编码为 `#C(1.0 2.0)`。接口可以编码为类型名和值的对，例如 `("[]int" (1 2 3))`，但要注意这种表示法是有歧义的：`reflect.Type.String` 方法可能为不同的类型返回相同的字符串。

**练习 12.4：** 修改 `encode` 以按上述风格美化打印 S-表达式。

**练习 12.5：** 改造 `encode` 以发出 JSON 而不是 S-表达式。使用标准解码器 `json.Unmarshal` 测试你的编码器。

**练习 12.6：** 改造 `encode`，使其作为一种优化，不编码值为其类型零值的字段。

**练习 12.7：** 为 S-表达式解码器创建一个流式 API，遵循 `json.Decoder` 的风格 ([`第 4.5 节`](#part0040.html#id-json))。

## 12.5 使用 `reflect.Value` 设置变量

到目前为止，反射只是以各种方式*解读*我们程序中的值。然而，本节的重点是*修改*它们。

