

## 第 5 章 过程化编程

```go
fmt.Println(jsonObjectAsString(jsonObject))
{
  "senators": ["John Kerry", "Scott Brown"], "name": "Massachusetts",
  "water": 25.700000,"area": 2736.000000
}
```

如果在反序列化时没有发生错误，类型为 `interface{}` 的对象值将引用类型为 `map[string]interface{}` 的变量，其键为 JSON 对象的字段名。`jsonObjectAsString()` 函数接收此类类型的 map 并返回相应的 JSON 字符串。我们使用未检查的断言（199 ≺）将类型为 `interface{}` 的缓冲区转换为类型为 `map[string]interface{}` 的 `jsonObject` 变量。（注意，这里显示的输出为了适应书本的页宽被拆分成了两行）

```go
func jsonObjectAsString(jsonObject map[string]interface{}) string {
  var buffer bytes.Buffer
  buffer.WriteString("")
  comma := ""
  for key, value := range jsonObject {
    buffer.WriteString(comma)
    switch value := value.(type) { // 变量 ①
    case nil: ②
      fmt.Fprintf(&buffer, "%q: null", key)
    case bool:
      fmt.Fprintf(&buffer, "%q: %t", key, value)
    case float64:
      fmt.Fprintf(&buffer, "%q: %f", key, value)
    case string:
      fmt.Fprintf(&buffer, "%q: %q", key, value)
    case []interface{}:
      fmt.Fprintf(&buffer, "%q: [", key)
      innerComma := ""
      for s, ok := range value.([]string) { // 变量 ③
        fmt.Fprintf(&buffer, "%s%q", innerComma, s)
        innerComma = ","
      }
      buffer.WriteString("]")
    }
    comma = ","
  }
  buffer.WriteString("")
  return buffer.String()
}
```

### 5.2. 分支

此函数将表示 JSON 对象的 map 转换，并返回 JSON 格式的对象数据的关联字符串。表示 JSON 对象的 map 内部的 JSON 数组本身由 `[]interface{}` 类型表示。该函数对 JSON 数组做了一个简化假设：假设它们只包含字符串。

为了访问我们用于... 的数据，我们对 map 的键使用 `range` 循环（$5.3, ➤ 203），并使用类型切换（type switch）来访问和处理每个不同的值类型。`switch` 的类型守卫（200, ➤）将值（类型为 `interface()`）赋值给名为 `value` 的新变量，其类型与匹配的 `case` 一致。在这种情况下，对变量进行遮蔽是有意义的（尽管如果我们愿意，也可以创建一个新变量）。因此，如果 `interface()` 的值是 `bool`，则内部值将是 `bool` 并匹配第二个 `case`，其他情况亦是然。

为了将值写入缓冲区，我们使用了 `fmt.Fprintf()` 函数，因为这比写入例如 `buffer.WriteString(fmt.Sprintf(...))` 更方便（200, ➤）。`fmt.Fprint()` 函数将内容写入作为第一个参数的 `io.Writer`。`Buffer` 不是 `io.Writer`——但 *bytes.Buffer* 是，这就是为什么我们传递缓冲区的地址。这个问题在第 6 章会有详细介绍，但简而言之，`io.Writer` 是一个接口，由任何提供 `Write()` 方法的值实现（即 **bytes.Buffer.Write()* 接收的是指针接收者，而不是字节），因此只有 *bytes.Buffer* 实现了该接口，这意味着我们必须将缓冲区的地址传递给 `fmt.Fprintf()` 函数，而不是缓冲区的值。

如果 JSON 对象包含 JSON 数组，我们使用内部的 `for ... range` 循环来遍历每一个数组，并使用检查的类型断言（200, ➤），仅当项为字符串时才将它们添加到我们的输出中。我们再次使用了遮蔽变量（这次类型为 `string`），因为我们需要的不是 `interface{}`，而是它所引的值。（类型断言在之前介绍过：$5.1.2, 191 ➤）

当然，如果我们知道原始 JSON 对象的结构，我们会使用 `struct` 来存储数据，并编写一个方法以字符串形式输出它。以下是在各种情况下进行反序列化和打印的代码。

```go
var state State
if err := json.Unmarshal(data, &state); err != nil {
    fmt.Println(err)
}
fmt.Println(state)

{"name": "Massachusetts", "area": 27336, "water": 25.700000,
"senators": ["John Kerry", "Scott Brown"]}
```

这段代码与我们之前的代码非常相似。然而，不需要 `jsonAsString()` 函数；相反，我们需要定义一个 `State` 类型和相应的 `State.String()` 方法。（再次，我们必须将其拆分为两行以适应书本的页宽。）

```go
type State struct {
  Name string
  Senators []string
  Water float64
  Area int
}
```

该结构体与我们之前看到的相似。但注意，每个字段必须以大写字母开头以使其导出（公有），因为 `json.Unmarshal()` 函数只能填充导出字段。此外，Go 的 `encoding/json` 包不区分不同的数值类型——它将所有 JSON 数字处理为 `float64`——`json.Unmarshal()` 函数足够智能，可以根据需要填充其他数值类型的字段。此方法以 JSON 字符串的形式返回 `State` 值。

大多数程序不需要类型断言和类型切换；即使需要，它们的使用也应该是相当少见的。一个用例是我们传递了满足一个接口的值，并希望同时也满足另一个接口。（该主题在第 6 章介绍；例如 6.5.）另一个用例是当来自外部源的数据必须转换为 Go 类型时。为了维护，最好将此类代码与程序的其余部分隔离。这允许程序完全以 Go 类型的方式运行，并意味着由于外部源格式变化而需要的任何维护都可以局部化。

### 5.3. 使用 For 语句进行循环

Go 使用两种 `for` 语句进行循环：普通的 `for` 语句和 `for ... range` 语句。它们的语法如下：

```go
for { 无限循环
	block
}
```

```go
for booleanExpression { // While 循环
	block
}
```

```go
for optionalPreStatement, booleanExpression, optionalPostStatement { 
	block
}
```

```go
for index, char := range aString // 字符串逐字符迭代
	block
}
```

```go
for index, char := range aString // 字符串逐字符迭代
	block
}

```go
for index, char := range utf8.DecodeRune(aString) // 字符串逐字符迭代
	block
}
```

```go
for index, item := range arraySlice // 数组切片迭代
	block
}
```

```go
for index := range arraySlice // 数组切片迭代
	block
}
```

```go
for key, value := range aMap // Map 迭代
	block
}
```

```go
for key := range aMap // Map 迭代
	block
}
```

```go
for item := range aChannel // 通道迭代
	block
}
```

大括号是强制性的，如果使用了可选的置语句或后语句，则需要分号；`for` 语句中的布尔表达式必须是 `bool` 类型。`range` 子句在 `for` 语句结束处提供了索引。（（布尔运算符见表 2。）

第二个 `for ... range` 字符串语法（203, ➤）提供了字节索引。对于 7-bit ASCII 字符串值 "Xaby"，它产生索引 0, 1, 2。对于 UTF-8 字符串值 "QYZ"，它产生索引 0, 1, 3, 4, 5。第一个 `for ... range` 字符串语法（203, ➌）几乎比第二个（203, ➤）更方便。

第二个 `for ... range` 数组切片语法（203, ➤）产生从 0 到 `len(slice)-1` 的项（对于空切片或数组）。这和第一个 `for ... range` 数组切片语法（203, ➤）通常很有用。这些语法特别解释了为什么 Go 程序需要循环（203, ➊）。

遍历 键值对（203, ⬙）以及 Map 键（203, ➤），如果需要排序，则使用第二个语法（203, ➤）并填充 `for` 语句后的语句，或者——如果使用 `break` 语句——我们在上一章中展示了它的示例（$4.3.4, 170.$）。另一种解决方案是使用有序数据结构。我们将在下一章看到它的示例（$6.5.3. ⬓。）

如果任何语法（203, ⬙）用于空字符串、数组、切片或 map，循环将什么都不做，控制流继续执行后续语句。

`for` 循环可以使用 `break` 语句随时退出，控制流传递到 `for` 循环后的语句，或者——带有指定标签的最内 `for`、`switch` 或 `select` 语句。还可以通过 `continue` 语句使控制流返回循环条件或 `range` 子句以强制执行下一次迭代（或循环）。

