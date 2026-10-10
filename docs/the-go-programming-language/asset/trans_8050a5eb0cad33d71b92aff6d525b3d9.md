
每当我们通过指针间接访问时，都会获得一个可寻址的 `reflect.Value`，即使我们是从一个不可寻址的 `Value` 开始的。所有关于可寻址性的常规规则在反射中都有对应的类比。例如，由于切片索引表达式 `e[i]` 隐式地遵循了一个指针，因此它是可寻址的，即使表达式 `e` 本身不是。类比而言，`reflect.ValueOf(e).Index(i)` 指向一个变量，因此它是可寻址的，即使 `reflect.ValueOf(e)` 不是。

从一个可寻址的 `reflect.Value` 恢复变量需要三个步骤。首先，我们调用 `Addr()`，它返回一个持有指向该变量指针的 `Value`。接着，我们在这个 `Value` 上调用 `Interface()`，它返回一个包含该指针的 `interface{}` 值。最后，如果我们知道变量的类型，我们可以使用类型断言将接口的内容作为普通指针取出。然后我们可以通过该指针更新变量：

[点击此处查看代码图片](#ch12_images.html#id342pro03_r)

```
x := 2
d := reflect.ValueOf(&x).Elem()     // d 指向变量 x
px := d.Addr().Interface().(*int)   // px := &x
*px = 3                             // x = 3
fmt.Println(x)                      // "3"
```

或者，我们可以直接更新可寻址 `reflect.Value` 所指向的变量，而不使用指针，方法是调用 `reflect.Value.Set` 方法：

```
d.Set(reflect.ValueOf(4))
fmt.Println(x) // "4"
```

编译器通常执行的赋值兼容性检查，在运行时由 `Set` 方法执行。上面的例子中，变量和值都是 `int` 类型，但如果变量是 `int64` 类型，程序就会 panic，因此确保值可赋值给变量的类型至关重要：

[点击此处查看代码图片](#ch12_images.html#id343pro01_r)

```
d.Set(reflect.ValueOf(int64(5))) // panic: int64 is not assignable to int
```

当然，在不可寻址的 `reflect.Value` 上调用 `Set` 也会 panic：

[点击此处查看代码图片](#ch12_images.html#id343pro01_01_r)

```
x := 2
b := reflect.ValueOf(x)
b.Set(reflect.ValueOf(3)) // panic: Set using unaddressable value
```

针对某些基本类型组，存在 `Set` 的变体：`SetInt`、`SetUint`、`SetString`、`SetFloat` 等：

[点击此处查看代码图片](#ch12_images.html#id343pro02_r)

```
d := reflect.ValueOf(&x).Elem()
d.SetInt(3)
fmt.Println(x) // "3"
```

在某些方面，这些方法更宽容。例如，只要变量的类型是某种有符号整数，甚至是底层类型为有符号整数的命名类型，`SetInt` 就会成功；如果值太大，它会被悄悄截断以适应。但要小心：在指向 `interface{}` 变量的 `reflect.Value` 上调用 `SetInt` 会 panic，尽管 `Set` 会成功。

[点击此处查看代码图片](#ch12_images.html#id343pro03_r)

```
x := 1
rx := reflect.ValueOf(&x).Elem()
rx.SetInt(2)                     // OK, x = 2
rx.Set(reflect.ValueOf(3))       // OK, x = 3
rx.SetString("hello")            // panic: string is not assignable to int
rx.Set(reflect.ValueOf("hello")) // panic: string is not assignable to int

var y interface{}
ry := reflect.ValueOf(&y).Elem()
ry.SetInt(2)                     // panic: SetInt called on interface Value
ry.Set(reflect.ValueOf(3))       // OK, y = int(3)
ry.SetString("hello")            // panic: SetString called on interface Value
ry.Set(reflect.ValueOf("hello")) // OK, y = "hello"
```

当我们对 `os.Stdout` 应用 `Display` 时，我们发现反射可以读取根据语言常规规则不可访问的未导出结构体字段的值，例如类 Unix 平台上 `os.File` 结构体的 `fd int` 字段。然而，反射无法更新这些值：

[点击此处查看代码图片](#ch12_images.html#id343pro04_r)

```
stdout := reflect.ValueOf(os.Stdout).Elem() // *os.Stdout, 一个 os.File 变量
fmt.Println(stdout.Type())                  // "os.File"
fd := stdout.FieldByName("fd")
fmt.Println(fd.Int()) // "1"
fd.SetInt(2)          // panic: unexported field
```

可寻址的 `reflect.Value` 记录了它是否通过遍历未导出结构体字段获得，如果是，则禁止修改。因此，`CanAddr` 通常不是在设置变量前使用的正确检查。相关方法 `CanSet` 报告 `reflect.Value` 是否**既可寻址又可设置**：

[点击此处查看代码图片](#ch12_images.html#id343pro05_r)

```
fmt.Println(fd.CanAddr(), fd.CanSet()) // "true false"
```

## 12.6 示例：解码 S-表达式

对于标准库 `encoding/...` 包提供的每个 `Marshal` 函数，都有一个对应的 `Unmarshal` 函数用于解码。例如，正如我们在 [4.5 节](#ebook_split_039.html#id-json) 所见，给定一个包含我们 `Movie` 类型（[§12.3](#ebook_split_113.html#id-movie)）JSON 编码数据的字节切片，我们可以这样解码它：

[点击此处查看代码图片](#ch12_images.html#id344pro01_r)

```
data := []byte{/* ... */}
var movie Movie
err := json.Unmarshal(data, &movie)
```

`Unmarshal` 函数使用反射来修改现有 `movie` 变量的字段，根据类型 `Movie` 和传入数据的内容创建新的 map、结构体和切片。

现在让我们为 S-表达式实现一个简单的 `Unmarshal` 函数，类似于上面使用的标准 `json.Unmarshal` 函数，它是我们之前 `sexpr.Marshal` 的逆操作。我们必须提醒您，一个健壮且通用的实现需要大量代码，远超本示例舒适容纳的范围（本示例已经很长了），所以我们走了许多捷径。我们仅支持 S-表达式的一个有限子集，且不优雅地处理错误。该代码旨在演示反射，而非解析。

词法分析器使用 `text/scanner` 包中的 `Scanner` 类型将输入流分解为一系列标记，如注释、标识符、字符串字面量和数字字面量。扫描器的 `Scan` 方法推进扫描器并返回下一个标记的类型，其类型为 `rune`。大多数标记（如 `'('`）由单个 rune 组成，但 `text/scanner` 包使用 `rune` 类型的小负值来表示多字符标记 `Ident`、`String` 和 `Int` 的类型。在返回这些类型标记之一的 `Scan` 调用之后，扫描器的 `TokenText` 方法返回该标记的文本。

由于典型的解析器可能需要多次检查当前标记，但 `Scan` 方法会推进扫描器，我们将扫描器包装在一个名为 `lexer` 的辅助类型中，它记录 `Scan` 最近返回的标记。

[点击此处查看代码图片](#ch12_images.html#id344pro02_r)

gopl.io/ch12/sexpr

```
type lexer struct {
    scan  scanner.Scanner
    token rune // 当前标记
}

func (lex *lexer) next()        { lex.token = lex.scan.Scan() }
func (lex *lexer) text() string { return lex.scan.TokenText() }

func (lex *lexer) consume(want rune) {
    if lex.token != want { // 注意：这不是良好错误处理的示例。
        panic(fmt.Sprintf("got %q, want %q", lex.text(), want))
    }
    lex.next()
}
```

现在让我们转向解析器。它由两个主要函数组成。第一个函数 `read` 读取以当前标记开头的 S-表达式，并更新由可寻址 `reflect.Value` `v` 指向的变量。

[点击此处查看代码图片](#ch12_images.html#id345pro01_r)
