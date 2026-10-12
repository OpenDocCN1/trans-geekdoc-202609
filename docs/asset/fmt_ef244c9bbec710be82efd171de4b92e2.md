
但指针类型绝非满足接口的唯一类型，甚至带有修改方法的接口也可能由 Go 的其他引用类型满足。我们已经见过带有方法的切片类型（`geometry.Path`，§6.1）和带有方法的映射类型（`url.Values`，§6.2.1），稍后我们将看到带有方法的函数类型（`http.HandlerFunc`，§7.7）。甚至基本类型也可能满足接口；正如我们在第 7.4 节中看到的，`time.Duration` 满足 `fmt.Stringer`。

一个具体类型可能满足许多不相关的接口。考虑一个组织或销售数字化文化产品（如音乐、电影和书籍）的程序。它可能定义以下具体类型集合：

```
Album
Book
Movie
Magazine
Podcast
TVEpisode
Track
```

我们可以将每个感兴趣的抽象表示为一个接口。某些属性是所有产品共有的，例如标题、创建日期和创作者列表（作者或艺术家）。

```
type Artifact interface {
    Title() string
    Creators() []string
    Created() time.Time
}
```

其他属性仅限于特定类型的产品。印刷文字的属性仅与书籍和杂志相关，而只有电影和电视剧集具有屏幕分辨率。

点击此处查看代码图像

```
type Text interface {
    Pages() int
    Words() int
    PageSize() int
}

type Audio interface {
    Stream() (io.ReadCloser, error)
    RunningTime() time.Duration
    Format() string // 例如 "MP3", "WAV"
}

type Video interface {
    Stream() (io.ReadCloser, error)
    RunningTime() time.Duration
    Format() string // 例如 "MP4", "WMV"
    Resolution() (x, y int)
}
```

这些接口只是将相关的具体类型分组并表达它们共享的侧面的一种有用方式。我们稍后可能会发现其他的分组。例如，如果我们发现需要以相同的方式处理 `Audio` 和 `Video` 项目，我们可以定义一个 `Streamer` 接口来表示它们的共同方面，而无需更改任何现有的类型声明。

```
type Streamer interface {
    Stream() (io.ReadCloser, error)
    RunningTime() time.Duration
    Format() string
}
```

基于共享行为的每个具体类型分组都可以表示为一个接口类型。与基于类的语言不同，在基于类的语言中，类满足的接口集合是显式的，在 Go 中，我们可以在需要时定义新的抽象或感兴趣的分组，而无需修改具体类型的声明。当具体类型来自不同作者编写的包时，这特别有用。当然，具体类型之间确实需要有底层的共性。

## 7.4 使用 `flag.Value` 解析标志

在本节中，我们将看到另一个标准接口 `flag.Value` 如何帮助我们为命令行标志定义新的表示法。考虑下面的程序，它休眠一段指定的时间。

点击此处查看代码图像

gopl.io/ch7/sleep

```
var period = flag.Duration("period", 1*time.Second, "sleep period")

func main() {
    flag.Parse()
    fmt.Printf("Sleeping for %v...", *period)
    time.Sleep(*period)
    fmt.Println()
}
```

在进入休眠前，它会打印时间段。`fmt` 包调用 `time.Duration` 的 `String` 方法来打印该时间段，不是以纳秒数的形式，而是以用户友好的表示法：

```
$ go build gopl.io/ch7/sleep
$ ./sleep
Sleeping for 1s...
```

默认情况下，休眠时长为一秒，但可以通过 `-period` 命令行标志进行控制。`flag.Duration` 函数创建一个类型为 `time.Duration` 的标志变量，并允许用户以多种用户友好的格式指定时长，包括 `String` 方法打印的相同表示法。这种设计的对称性造就了良好的用户界面。

点击此处查看代码图像

```
$ ./sleep -period 50ms
Sleeping for 50ms...
$ ./sleep -period 2m30s
Sleeping for 2m30s...
$ ./sleep -period 1.5h
Sleeping for 1h30m0s...
$ ./sleep -period "1 day"
invalid value "1 day" for flag -period: time: invalid duration 1 day
```

由于带时长值的标志非常有用，该功能被内置在 `flag` 包中，但为我们自己的数据类型定义新的标志表示法也很容易。我们只需定义一个满足 `flag.Value` 接口的类型，其声明如下：

点击此处查看代码图像

```
package flag

// Value 是标志中存储的值的接口。
type Value interface {
    String() string
    Set(string) error
}
```

`String` 方法格式化标志的值以用于命令行帮助信息；因此每个 `flag.Value` 同时也是一个 `fmt.Stringer`。`Set` 方法解析其字符串参数并更新标志值。实际上，`Set` 方法是 `String` 方法的逆操作，最好让它们使用相同的表示法。

让我们定义一个 `celsiusFlag` 类型，允许以摄氏度指定温度，或以华氏度指定并进行适当转换。注意 `celsiusFlag` 嵌入了 `Celsius`（§2.5），从而免费获得了一个 `String` 方法。要满足 `flag.Value`，我们只需声明 `Set` 方法：

点击此处查看代码图像

`gopl.io/ch7/tempconv`

```
// *celsiusFlag 满足 flag.Value 接口。
type celsiusFlag struct{ Celsius }

func (f *celsiusFlag) Set(s string) error {
    var unit string
    var value float64
    fmt.Sscanf(s, "%f%s", &value, &unit) // 无需错误检查
    switch unit {
    case "C", "°C":
        f.Celsius = Celsius(value)
        return nil
    case "F", "°F":
        f.Celsius = FToC(Fahrenheit(value))
        return nil
    }
    return fmt.Errorf("invalid temperature %q", s)
}
```

对 `fmt.Sscanf` 的调用从输入 `s` 中解析出一个浮点数（`value`）和一个字符串（`unit`）。虽然通常必须检查 `Sscanf` 的错误结果，但在这种情况下不需要，因为如果出现问题，没有任何 switch case 会匹配。

下面的 `CelsiusFlag` 函数将一切封装起来。对调用者而言，它返回嵌入在 `celsiusFlag` 变量 `f` 中的 `Celsius` 字段的指针。`Celsius` 字段是在标志处理期间将被 `Set` 方法更新的变量。对 `Var` 的调用将该标志添加到应用程序的命令行标志集合中，即全局变量 `flag.CommandLine`。具有异常复杂命令行界面的程序可能有多个此类变量。对 `Var` 的调用将 `*celsiusFlag` 参数赋值给 `flag.Value` 参数，导致编译器检查 `*celsiusFlag` 是否具有必要的方法。

点击此处查看代码图像

```
// CelsiusFlag 使用指定的名称、默认值和用法定义一个 Celsius 标志，
// 并返回标志变量的地址。
// 标志参数必须包含数量和单位，例如 "100C"。
func CelsiusFlag(name string, value Celsius, usage string) *Celsius {
    f := celsiusFlag{value}
    flag.CommandLine.Var(&f, name, usage)
    return &f.Celsius
}
```

现在我们可以在程序中开始使用这个新标志了：

点击此处查看代码图像

`gopl.io/ch7/tempflag`

```
var temp = tempconv.CelsiusFlag("temp", 20.0, "the temperature")

func main() {
    flag.Parse()
    fmt.Println(*temp)
}
```

以下是一个典型的会话：

点击此处查看代码图像

```
$ go build gopl.io/ch7/tempflag
$ ./tempflag
20°C
$ ./tempflag -temp -18C
-18°C
$ ./tempflag -temp 212°F
100°C
$ ./tempflag -temp 273.15K
invalid value "273.15K" for flag -temp: invalid temperature "273.15K"
Usage of ./tempflag:
  -temp value
        the temperature (default 20°C)
$ ./tempflag -help
Usage of ./tempflag:
  -temp value
        the temperature (default 20°C)
```

**练习 7.6：** 为 `tempflag` 添加对开尔文温度的支持。

**练习 7.7：** 解释为什么帮助信息包含 `°C`，而默认值 `20.0` 却不包含。

## 7.5 接口值

概念上，接口类型的值，或称*接口值*，有两个组成部分：一个具体类型和该类型的一个值。它们被称为接口的*动态类型*和*动态值*。

对于像 Go 这样静态类型的语言，类型是编译时的概念，因此类型不是值。在我们的概念模型中，一组称为*类型描述符*的值提供了关于每种类型的信息，如其名称和方法。在接口值中，类型组成部分由相应的类型描述符表示。

在下面的四条语句中，变量 `w` 取了三个不同的值。（初始值和最终值相同。）

```
var w io.Writer
w = os.Stdout
w = new(bytes.Buffer)
w = nil
```

让我们仔细看看每条语句执行后 `w` 的值和动态行为。第一条语句声明 `w`：

```
var w io.Writer
```

在 Go 中，变量总是被初始化为一个明确定义的值，接口也不例外。接口的零值将其类型和值组成部分都设为 `nil`（图 7.1）。

![一个 nil 接口值。](img/iface1.png)

**图 7.1。** 一个 nil 接口值。

根据其动态类型，接口值被描述为 nil 或非 nil，所以这是一个 nil 接口值。你可以使用 `w == nil` 或 `w != nil` 来测试接口值是否为 nil。调用 nil 接口值的任何方法都会导致 panic：

点击此处查看代码图像

```
w.Write([]byte("hello")) // panic: nil pointer dereference
```

第二条语句将一个 `*os.File` 类型的值赋给 `w`：

```
w = os.Stdout
```

此赋值涉及从具体类型到接口类型的隐式转换，等同于显式转换 `io.Writer(os.Stdout)`。这种转换无论显式还是隐式，都会捕获其操作数的类型和值。接口值的动态类型被设为指针类型 `*os.File` 的类型描述符，其动态值持有 `os.Stdout` 的副本，这是一个指针，指向代表进程标准输出的 `os.File` 变量（图 7.2）。

![一个包含 *os.File 指针的接口值。](img/iface2.png)

**图 7.2。** 一个包含 `*os.File` 指针的接口值。

在包含 `*os.File` 指针的接口值上调用 `Write` 方法会导致调用 `(*os.File).Write` 方法。该调用打印 `"hello"`。

点击此处查看代码图像

```
w.Write([]byte("hello")) // "hello"
```

通常情况下，我们无法在编译时知道接口值的动态类型是什么，因此通过接口进行的调用必须使用*动态分发*。编译器不是生成直接调用的代码，而是必须生成代码从类型描述符中获取名为 `Write` 的方法的地址，然后对该地址进行间接调用。该调用的接收者参数是接口动态值 `os.Stdout` 的副本。其效果就如同我们直接进行了如下调用：

点击此处查看代码图像

```
os.Stdout.Write([]byte("hello")) // "hello"
```

第三条语句将一个 `*bytes.Buffer` 类型的值赋给接口值：

```
w = new(bytes.Buffer)
```

现在动态类型是 `*bytes.Buffer`，动态值是指向新分配缓冲区的指针（图 7.3）。

![包含 *bytes.Buffer 指针的接口值。](img/iface3.png)

**图 7.3。** 包含 `*bytes.Buffer` 指针的接口值。

对 `Write` 方法的调用使用与之前相同的机制：

点击此处查看代码图像

```
w.Write([]byte("hello")) // 将 "hello" 写入 bytes.Buffer
```

这一次，类型描述符是 `*bytes.Buffer`，因此调用了 `(*bytes.Buffer).Write` 方法，并将缓冲区的地址作为接收者参数的值。该调用将 `"hello"` 追加到缓冲区中。

最后，第四条语句将 `nil` 赋给接口值：

```
w = nil
```

这将其两个组成部分都重置为 `nil`，使 `w` 恢复到声明时的相同状态，这在图 7.1 中已展示。

接口值可以容纳任意大小的动态值。例如，表示时间点的 `time.Time` 类型是一个包含若干未导出字段的结构体类型。如果我们从它创建一个接口值，

```
var x interface{} = time.Now()
```

结果可能如图 7.4 所示。从概念上讲，动态值总是能放入接口值中，无论其类型有多大。（这只是一个概念模型；实际的实现截然不同。）

![包含 time.Time 结构体的接口值。](img/iface-time.png)

**图 7.4。** 包含 `time.Time` 结构体的接口值。

接口值可以使用 `==` 和 `!=` 进行比较。如果两个接口值都为 nil，或者它们的动态类型相同且动态值根据该类型 `==` 的常规行为相等，则这两个接口值相等。因为接口值是可比较的，所以它们可以用作 map 的键或 switch 语句的操作数。

然而，如果比较的两个接口值具有相同的动态类型，但该类型不可比较（例如切片），则比较会引发 panic：

点击此处查看代码图像

```
var x interface{} = []int{1, 2, 3}
fmt.Println(x == x) // panic: comparing uncomparable type []int
```

在这方面，接口类型比较特殊。其他类型要么是安全可比较的（如基本类型和指针），要么完全不可比较（如切片、map 和函数），但在比较接口值或包含接口值的聚合类型时，我们必须意识到可能会发生 panic。将接口用作 map 键或 switch 操作数时也存在类似的风险。只有当你确定接口值包含的动态值类型是可比较时，才去比较它们。

在处理错误或调试时，报告接口值的动态类型通常很有帮助。为此，我们使用 `fmt` 包的 `%T` 动词：

点击此处查看代码图像

```
var w io.Writer
fmt.Printf("%T\n", w) // "<nil>"

w = os.Stdout
fmt.Printf("%T\n", w) // "*os.File"

w = new(bytes.Buffer)
fmt.Printf("%T\n", w) // "*bytes.Buffer"
```

在内部，`fmt` 使用反射来获取接口动态类型的名称。我们将在第 12 章中探讨反射。

### 7.5.1 警示：包含空指针的接口非空

一个不包含任何值的 nil 接口值，与一个恰好包含 nil 指针的接口值是不一样的。这个微妙的区别制造了一个陷阱，每个 Go 程序员都曾踩过坑。

请看下面的程序。将 `debug` 设为 `true` 时，main 函数会在 `bytes.Buffer` 中收集函数 `f` 的输出。

点击此处查看代码图像

```
const debug = true

func main() {
    var buf *bytes.Buffer
    if debug {
        buf = new(bytes.Buffer) // 启用输出收集
    }
    f(buf) // 注意：微妙的错误！
    if debug {
        // ...使用 buf...
    }
}

// 如果 out 非空，则向其写入输出。
func f(out io.Writer) {
    // ...做些事情...
    if out != nil {
        out.Write([]byte("done!\n"))
    }
}
```
