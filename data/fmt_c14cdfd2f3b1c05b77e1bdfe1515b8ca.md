
```
(40.717, -74.000) "New York"
(39.283, -76.617) "Baltimore"
```

我们将 `Place` 放在包中并调用 `place.New()` 来创建 `*Place`。一旦有了 `*Place`，我们就可以像调用标准库的自定义类型一样调用它的方法。

## 6.3. 接口

在 go 中，接口是一种指定一个或多个方法签名的自定义类型。接口由于是抽象的，因此无法实例化接口。然而，可以创建一个类型接口的变量类型——并且它可以分配任何具有所需方法的类型的值。

`interface{}` 是指定空方法集的类型。任何值都满足 `interface{}`，无论该值是否有方法——毕竟，如果一个值有方法，它的方法集包含了作为方法的空方法集。这就是为什么 `interface{}` 可以用于任何值。因此，通常最好将值传递为它们的实际类型或具有我们想要使用的方法的接口。当然，如果我们对 `interface{}` 类型使用有方法的值，我们可以通过使用类型断言 (§5.2.1, 191 ►) 或类型切换 (§5.2.2.2, 197 ➤)，甚至通过使用内省 (§9.4.9, ➤427) 来访问方法。

这是一个非常简单的接口。

# 第 6 章 面向对象编程

```go
type Exchanger interface {
    Exchange()
}
```

`Exchanger` 接口定义了一个单一方法 `Exchange()`，它不接受任何参数也没有返回值。我们遵循了 Go 的接口命名规范，即它们应该以 `er` 结尾。只有一个方法的接口是常见的现象——例如，标准库中的 `io.Reader` 和 `io.Writer` 各自指定了一个方法。请注意，接口实际上是在定义一个 API（应用程序编程接口），即零或多个方法——尽管它并没有说明这些方法具体是做什么的。

一个非空接口本身通常没有用；为了让它变得有用，我们创建了一些实现了接口所需方法的自定义类型。这里有两种这样的类型。

```go
type StringPair struct{first, second string}
func (pair *StringPair) Exchange() {
    pair.first, pair.second = pair.second, pair.first
}
type Point [2]int
func (point *Point) Exchange() { point[0], point[1] = point[1], point[0] }
```

自定义的 `StringPair` 和 `Point` 类型完全不同，但由于它们都提供了 `Exchange()` 方法，因此都实现了 `Exchanger` 接口。这意味着我们可以创建 `StringPair` 和 `Point` 值，并将它们传递给接受 `Exchanger` 的函数。

请注意，尽管 `StringPair` 和 `Point` 类型都实现了 `Exchanger` 接口，但现在我们没有显式地说明这一点——没有“实现”（implements）或“继承”（inherits）语句。`StringPair` 和 `Point` 类型提供了接口指定的方法（在这种情况下只有一个方法），足以让 Go 知道它们实现了该接口。

方法的接收者被指定为其类型的指针，这样我们就可以更改调用方法所指向的值。虽然 Go 足够智能可以以合理的方式创建自定义类型，但我们通常更倾向于控制它们的表示。这可以通过添加一个实现 `Stringer` 接口的方法（即签名为 `String() string` 的方法）来轻松实现。如果我们正在编写一个框架，可能会创建接口但不创建实现它们的类型，并要求框架的用户创建此类类型以供使用。

## 6.3. 接口

```go
func (pair StringPair) String() string {
    return fmt.Sprintf("%q+%q", pair.first, pair.second)
}
```

该方法返回一个由双引号括起来字符串和中间的 `+` 号组成的字符串。定义了这个方法后，Go 的 `fmt` 包的打印方法将使用它来打印 `StringPair` 值——同时也包括 *StringPairs*，因为变量是作为值创建的，但 `Exchange()` 方法需要指针。这不是一个问题，正如我们之前提到的，当我们对值调用需要指针的方法时，Go 足够智能可以传递该值的地址——前提是该值是可寻址的。因此，在代码段中，`pair.Exchange()` 被自动处理为等于 `(&pair).Exchange()`，其他情况也是如此。

在对 `exchangeThese()` 函式进行调用时，我们必须显式地传递地址。例如，如果我们传递了类型为 `StringPair` 的值，Go 编译器会注意到 `StringPairs` 没有实现 `Exchanger` 接口——因为没有以 `StringPair` 为接收者的 `Exchange()` 方法——并将停止编译且报告错误。然而，如果我们传递一个 *StringPair*（例如 `&hyde`），编译将成功完成。这是因为存在一个接收 `*StringPair` 接收者的 `Exchange()` 方法，这意味着 *StringPairs* 实现了 `Exchanger` 接口。

这里是 `exchangeThese` 函式：

```go
func exchangeThese(exchangers ...Exchanger) {
	for _, exchanger := range exchangers {
		exchanger.Exchange()
	}
}
```

该函数不知道也不在乎传递给它的两个 *StringPairs* 和一个 *Point*；它唯一要求的是参数是 `Exchangers`——这一要求由编译器强制执行，这里使用的鸭子类型（duck typing）是类型安全的。

实现我们自定义的接口外，我们还可以实现标准库或其他我们需要的接口，正如我们在定义 `StringPair.String()` 方法来实现 `String` 接口时看到的那样。另一个例子是 `io.Reader` 接口，它指定了一个签名为 `Read([]byte) (int, error)` 的单一方法，该方法将调用值的数据写入给定的 `[]byte` 中。写入是破坏性的，也就是说，每个写入的字节都会从被调用的值中移除。

```go
func (pair *StringPair) Read(data []byte) (int, error) {
	if pair.first == "" && pair.second != "" {
		return 0, io.EOF
	}
	if pair.first != "" {
		n = copy(data, pair.first)
		pair.first = pair.first[:n]
	}
	if n < len(data) && pair.second != "" {
		m = copy(data[n:], pair.second)
		pair.second = pair.second[m:]
		n += m
	}
	return n, nil
}
```

通过实现这个方法，我们让 `String` 类型实现了 `io.Reader` 接口。所以现在 `StringPairs`（或者严格来说，是 *StringPairs*，因为某些方法需要指针接收者）都是 `Exchangers`、`fmt.Stringers` 和 `io.Readers`——无需说 *String* “实现”了 `Exchanger` 或任何其他接口。如果我们愿意，还可以添加更多方法并实现额外的接口。

该方法使用了内置的 `copy()` 函式 (§4.2.3)。该函数可以用于从另一个相同类型的切片拷贝到切片中——但在这里我们使用了它的另一种形式，从字符串拷贝到 `[]byte`。`copy()` 函数拷贝的字节数永远不会超过目标 `[]byte` 的空间，并返回拷贝的字节数。自定义的 `StringPair.Read()` 方法从第一个字符串写入字节（移除已写入的字节），对第二个字符串执行相同操作。如果两个字符串都为空，该方法返回计数零和 EOF。顺便提一下，如果删除第二个语句，该方法也能完美运行——但在效率上会有某种（可能微不足道）的代价。这里有一个代码段：

```go
const size = 16
robert := &StringPair("Robert L.", "Stevenson")
david := StringPair("David", "Balfour")
for _, reader := range io.Readers{robert, &david} {
	raw, err := ToBytes(reader, size)
	if err != nil {
		fmt.Println(err)
	}
	fmt.Printf("%q\n", raw)
}
```

- 之前："Henry"+"Edward"+"Hyde"

- 之后 #1："Jekyll"+"Henry"+"Edward"

- 之后 #2："Henry"+"Jekyll"+"Hyde"

## 第6 章 面向对象编程

```go
if err != nil {
    return data, err
}
return data[:], nil // 切片掉所有未使用的字节
```

就像我们之前看到的 `exchange` 函数一样，这个函数并不知道也不在乎传递的是什么特定类型的值——只要它是某种 `io.Reader` 即可。

如果读取成功，数据切片将被重新切片，以将其长度缩减为实际读取的字节数。如果我们不这样做，且大小太大，我们得到的是读取的数据后面跟着一串字节（每个值均为 0x0）。例如，如果不进行切片，david 将输出为 `DavidBalfour\x000\x000\x000`。

注意，我们并不需要在接口和满足该的任何类型之间建立自定义连接——类型可以“继承”或“扩展”一个接口；只需提供所需的方法就足够了。这使得 Go 变得极其灵活——我们可以随时添加新的接口、类型和方法，而不会破坏继承树。

### 6.3.1. 接口嵌入

Go 接口（以及结构体，正如我们在下一节中看到的）对嵌入提供了很好的支持。接口可以嵌入其他接口，其效果几乎等同于我们在嵌入接口中直接写了被嵌入接口的方法签名。让我们用一个简单的例子来说说明这一点。

```go
type LowerCase interface {
    LowerCase()
}

type UpperCase interface {
    UpperCase()
}

type LowerUpperCase interface {
    LowerCase // 相当于我们写了 LowerCase()
    UpperCase // 相当于我们写了 UpperCase()
}
```

`LowerUpperCase` 接口指定了一个单一方法 `LowerCase()`，它不接受参数也不返回任何内容。`UpperCase` 接口也类似。`LowerUpperCase` 嵌入了另外两个接口。这意味着一个具体类型要满足 `LowerUpperCase` 接口，必须拥有 `LowerCase()` 和 `UpperCase()` 方法。

## 6.3. 接口

在这个微小的例子中，嵌入看起来优势不大。然而，如果我们向前两个接口添加额外的方法（例如，`LowerCaseSpecial()` 和 `UpperCaseSpecial()`），`LowerUpperCase` 接口将自动包含它们，而我们无需修改它的代码。

```go
type FixCaser interface {
    FixCase()
}
type ChangeCaser interface {
    LowerUpperCase // 相当于我们写了 LowerCase(); UpperCase
    FixCaser // 相当于我们写了 FixCase()
}
```

我们又增加了两个接口，所以我们现在有了一种嵌入接口的层次结构，如图 6.2 所示。

| 抽象接口 | 具体类型 |

| --- | --- |

| ChangeCaser | *Part // 是一个 ChangeCaser |

| LowerUpperCaseaser | *Part // 是一个 fmt.Stringer |

| LowerCaser | *StringPair // 是一个 ChangeCaser |

| LowerCase() | *StringPair // 是一个 Exchanger |

| | *StringPair // 是一个 io.Reader |

| | *StringPair // 是一个 fmt.Stringer |

| UpperCaser | Values |

| UpperCase() | part := Part{1439, "File"} |

| FixCaser | pair := StringPair{"Murray", "Bookchin"} |

| FixCase() | |

图 6.2 Caser 接口、类型和示例值

当然，接口本身没有用；我们需要实现它们的具体类型才能它们发挥作用。

```go
func (part *Part) FixCase() {
    part.Name = fixCase(part.Name)
}
```

我们之前见过自定义的 `Part` 类型（260）。在这里，我们添加了一个额外方法 `FixCase()`，它作用于 Part 的 `Name` 字段，就像我们之前看到的 `LowerCase()` 和 `UpperCase()` 方法一样。所有更改大小写的方法都使用指针接收者，因为它们修改了被调用的值。

`LowerCase()` 和 `UpperCase()` 方法使用标准库函数实现，而 `FixCase()` 方法依赖于自定义的 `fixCase()` 函数——这种依赖函数执行工作的微小方法模式在 Go 中非常常见。

`Part.String()` 方法（260）实现了标准库的 `fmt.Stringer` 接口，这意味着任何 `Part`（或 `*Part`）都将使用该方法返回的字符串进行打印。

```go
func fixCase(s string) string {
    var chars []rune
    upper := true
    for _, char := range s {
        if upper {
            char = unicode.ToUpper(char)
        } else {
            char = unicode.ToLower(char)
        }
        chars = append(chars, char)
        upper = unicode.IsSpace(char) || unicode.Is(unicode.Hyphen, char)
    }
    return string(chars)
}
```

这个简单的函数返回它接收到的字符串的副本，其中每个字符都已转小写，除了第一个字符以及每个空白字符或连字符后的第一个字符（这些字符是大大写的）。例如，给定字符串 "lobster sackville-baggings"，函数将返回 "Lobelia Sackville-Baggins"。

自然，我们可以让任何自定义类型满足一个或所有 caser 接口。

```go
func (pair *StringPair) UpperCase() {
    pair.first = strings.ToUpper(pair.first)
    pair.second = strings.ToUpper(pair.second)
}
func (pair *StringPair) LowerCase() {
    pair.first = strings.ToLower(pair.first)
    pair.second = strings.ToLower(pair.second)
}
```

## 6.4. 结构体 (Structs)

Go 中简单的类型是基于 Go 的内置类型——例如，`type Integer` 创建了一个自定义的 `Integer` 类型，我们可以为其添加自己的方法。自定义类型也可以基于结构体，结构体用于将值聚合并嵌入在一起。当值（在结构体的语文中称为字段）的类型不同且无法存储在切片（slice）中（除非我们使用 `[]interface{}`）时，这种方法特别有用。Go 的结构体比 C++ 的结构体更接近 C（例如，它们不是类），而且因为对嵌入（embedding） Excellent支持，使用起来更加方便。

我们在前面的章节和本章中已经看到了许多结构体的示例，在书的其余部分还将看到更多。尽管如此，还有一些我们尚未看到的结构体特性，因此我们将通过说明性示例来展示它们。

```go
points := []int{{4, 6}, {}, {-7, 11}, {15, 17}, {14, -8}}
for _, point := range points {
  fmt.Printf("%d, %d\n", point[0], point[1])
}
```

代码片段中的 `points` 变量是一个 `[]int` 数组切片，因此我们必须使用 `[]` 索引运算符来获取每个坐标。（顺带一提，`{}` 项等同于 `{0, 0}`，这归于 Go 的自动零值初始化）。对于简单数据的小样本，这种方法可行，但使用匿名结构体有更好的方法。

```go
points := []struct{x, y int}{{4, 6}, {}, {-7, 11}, {15, 17}, {14, -8}}
for _, point := range points {
  fmt.Printf("%d, %d\n", point.x, point.y)
}
```

在这里，代码片段中的 `points` 变量是 `struct{x, y int}` 的切片。虽然结构体本身没有命名，但我们可以通过其命名字段访问其数据，这比使用数组索引更容易且更安全。
