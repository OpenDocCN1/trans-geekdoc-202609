

### Maps

`MapKeys` 方法返回一个 `reflect.Value` 切片，每个 map 键对应一个元素。和遍历 map 一样，顺序是未定义的。`MapIndex(key)` 返回与 `key` 对应的值。我们将下标表示法 `"[key]"` 追加到路径后面。（这里我们偷了个懒。map 键的类型不限于 `formatAtom` 最擅长处理的那些类型；数组、结构体和接口也可以是合法的 map 键。扩展此情况以完整打印键是[练习 12.1](#part0114.html#id-ex-printstruct)。）

### Pointers

`Elem` 方法返回指针指向的变量，同样作为 `reflect.Value`。即使指针值为 `nil`，此操作也是安全的，此时结果的 kind 为 `Invalid`，但我们使用 `IsNil` 显式检测空指针，以便打印更合适的消息。我们在路径前加上 `"*"` 并加上括号以避免歧义。

### Interfaces

同样，我们使用 `IsNil` 测试接口是否为 nil，如果不为 nil，则使用 `v.Elem()` 获取其动态值并打印其类型和值。

现在我们的 `Display` 函数已完成，让我们把它用起来。下面的 `Movie` 类型是 [4.5 节](#part0040.html#id-json) 中类型的一个小变体：

```
type Movie struct {
    Title, Subtitle string
    Year            int
    Color           bool
    Actor           map[string]string
    Oscars          []string
    Sequel          *string
}
```

让我们声明一个该类型的值，看看 `Display` 如何处理它：

```
strangelove := Movie{
    Title:    "Dr. Strangelove",
    Subtitle: "How I Learned to Stop Worrying and Love the Bomb",
    Year:     1964,
    Color:    false,
    Actor: map[string]string{
        "Dr. Strangelove":            "Peter Sellers",
        "Grp. Capt. Lionel Mandrake": "Peter Sellers",
        "Pres. Merkin Muffley":       "Peter Sellers",
        "Gen. Buck Turgidson":        "George C. Scott",
        "Brig. Gen. Jack D. Ripper":  "Sterling Hayden",
        `Maj. T.J. "King" Kong`:      "Slim Pickens",
    },

    Oscars: []string{
        "Best Actor (Nomin.)",
        "Best Adapted Screenplay (Nomin.)",
        "Best Director (Nomin.)",
        "Best Picture (Nomin.)",
    },
}
```

调用 `Display("strangelove", strangelove)` 打印：

```
Display strangelove (display.Movie):
strangelove.Title = "Dr. Strangelove"
strangelove.Subtitle = "How I Learned to Stop Worrying and Love the Bomb"
strangelove.Year = 1964
strangelove.Color = false
strangelove.Actor["Gen. Buck Turgidson"] = "George C. Scott"
strangelove.Actor["Brig. Gen. Jack D. Ripper"] = "Sterling Hayden"
strangelove.Actor["Maj. T.J. \"King\" Kong"] = "Slim Pickens"
strangelove.Actor["Dr. Strangelove"] = "Peter Sellers"
strangelove.Actor["Grp. Capt. Lionel Mandrake"] = "Peter Sellers"
strangelove.Actor["Pres. Merkin Muffley"] = "Peter Sellers"
strangelove.Oscars[0] = "Best Actor (Nomin.)"
strangelove.Oscars[1] = "Best Adapted Screenplay (Nomin.)"
strangelove.Oscars[2] = "Best Director (Nomin.)"
strangelove.Oscars[3] = "Best Picture (Nomin.)"
strangelove.Sequel = nil
```

我们可以用 `Display` 显示库类型的内部结构，例如 `*os.File`：

```
Display("os.Stderr", os.Stderr)
// Output:
// Display os.Stderr (*os.File):
// (*(*os.Stderr).file).fd = 2
// (*(*os.Stderr).file).name = "/dev/stderr"
// (*(*os.Stderr).file).nepipe = 0
```

请注意，即使是未导出字段对反射也是可见的。请当心，此示例的具体输出可能因平台而异，并可能随库的演进而变化。（这些字段之所以是私有的，是有原因的！）我们甚至可以将 `Display` 应用于 `reflect.Value`，观察它遍历 `*os.File` 类型描述符的内部表示。调用 `Display("rV", reflect.ValueOf(os.Stderr))` 的输出如下所示，当然您的实际结果可能会有所不同：

```
Display rV (reflect.Value):
(*rV.typ).size = 8
(*rV.typ).hash = 871609668
(*rV.typ).align = 8
(*rV.typ).fieldAlign = 8
(*rV.typ).kind = 22
(*(*rV.typ).string) = "*os.File"
```

```
(*(*(*rV.typ).uncommonType).methods[0].name) = "Chdir"
(*(*(*(*rV.typ).uncommonType).methods[0].mtyp).string) = "func() error"
(*(*(*(*rV.typ).uncommonType).methods[0].typ).string) = "func(*os.File) error"
...
```

观察这两个例子的区别：

```
var i interface{} = 3

Display("i", i)
// Output:
// Display i (int):
// i = 3

Display("&i", &i)
// Output:
// Display &i (*interface {}):
// (*&i).type = int
// (*&i).value = 3
```

在第一个例子中，`Display` 调用 `reflect.ValueOf(i)`，返回一个 kind 为 `Int` 的值。正如我们在 [12.2 节](#part0113.html#id-reflecttypeandreflectvalue) 中提到的，`reflect.ValueOf` 总是返回一个具体类型的 `Value`，因为它提取了接口值的内容。

在第二个例子中，`Display` 调用 `reflect.ValueOf(&i)`，返回一个指向 `i` 的指针，kind 为 `Ptr`。`Ptr` 的 switch case 对此值调用 `Elem`，返回一个代表变量 `i` 本身的 `Value`，kind 为 `Interface`。间接获得的 `Value`，像这样，可以代表任意值，包括接口。`display` 函数递归调用自己，这一次，它为接口的动态类型和值分别打印了组成部分。

按目前的实现，如果 `Display` 在对象图中遇到循环，将永远不会终止，例如这个吞食自己尾巴的链表：

```
// 一个指向自身的结构体
type Cycle struct{ Value int; Tail *Cycle }
var c Cycle
c = Cycle{42, &c}
Display("c", c)
```

`Display` 打印出这种不断增长的展开：

```
Display c (display.Cycle):
c.Value = 42
(*c.Tail).Value = 42
(*(*c.Tail).Tail).Value = 42
(*(*(*c.Tail).Tail).Tail).Value = 42
...ad infinitum...
```

许多 Go 程序至少包含一些循环数据。使 `Display` 对此类循环具有鲁棒性比较棘手，需要额外的记账来记录迄今为止已跟踪的引用集合；开销也很大。通用解决方案需要 `unsafe` 语言特性，正如我们将在 [13.3 节](#part0124.html#id-exampledeepequivalence) 中看到的。

对 `fmt.Sprint` 而言，循环不构成太大问题，因为它很少尝试打印完整结构。例如，遇到指针时，它通过打印指针的数值来中断递归。它可能会卡在试图打印包含自身作为元素的切片或 map 上，但这种罕见情况不值得花费巨大精力去处理循环。

### 练习 12.1

扩展 `Display`，使其能显示键为结构体或数组的 map。

### 练习 12.2

通过限制放弃递归前的步数，使 `display` 在循环数据结构上使用安全。（在 [13.3 节](#part0124.html#id-exampledeepequivalence) 中，我们将看到另一种检测循环的方法。）

## 12.4 示例：编码 S-Expressions

`Display` 是一个用于显示结构化数据的调试例程，但它离能够将任意 Go 对象编码或 `marshal` 为适合进程间通信的可移植表示法中的消息已不远了。

