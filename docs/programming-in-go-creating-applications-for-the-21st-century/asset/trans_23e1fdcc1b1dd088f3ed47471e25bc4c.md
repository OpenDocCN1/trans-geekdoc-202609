

# 426

# 第 9 章 包

exec 包用于运行外部程序。这也可以通过 `os.StartProcess()` 函数实现，但 `exec.Cmd` 类型使用起来要方便得多。

flag 包提供了一个命令行解析器。它接受 X11 风格的选项（例如 `--width`）和 GNU 风格（例如 `-w` 和 `--width`）。该包会生成非常基本的用法信息，并且除了值的类型之外不提供任何验证。（因此，该包可以用于指定一个选项，但不能指定哪些值是可以接受的。）Dashboard (godashboard.appspot.com/project) 提供了几种替代方案。

log 包提供了日志信息输出（默认输出到 stdout，并在发生任何错误时终止程序或触发 panic）。`log` 包的输出目标可以使用 `log.SetOutput()` 函数更改为任何 `io.Writer`；消息输出格式为时间戳后接消息；在第一次调用 log 函数之前调用 `log.SetFlags(0)` 可以消除时间戳。还可以使用 `log.New()` 创建自定义的日志器。

math/rand 包提供了许多实用的伪随机数生成器函数，包括返回随机整数的 `rand.Int()` 和返回范围在 `[0, n)` 内随机整数的 `rand.Intn()`。crypto/rand 包有一个产生加密安全随机数的函数。

regex 包提供了一个非常快速且强大的正则表达式引擎，支持 RE2 引擎语法。我们在书的几个示例中使用了它，尽管我们刻意使用了简单的正则表达式，而没有发挥该包的全部威力，以防偏离主题。该包在更早版本中已引入（$3.6.5, 120 ◄）。

sort 包提供了对 int、float64 和 string 切片进行排序的便利函数，以及对切片执行快速（二分拷贝）搜索的函数。它还提供了 `generic.Sort()` 和 `sort.Search()` 函数，可用于自定义数据。（例如，参见 §4.2.4, 160 ◄ 表 4.2, 161 以及 §5.6.7, 228 ◄）

time 包具有用于测量时间、解析和格式化日期/时间以及值的函数。`time.After()` 函数可以在指定的纳秒通过后向其返回的 channel 发送当前时间，正如我们在之前的示例中所看到的（332 ◄）。`time.Tick()` 和 `time.Ticker()` 函数可以提供一个在指定间隔内重复发送“tick”的 channel。`time.Time` 拥有提供当前时间、将日期/时间格式化为字符串以及解析日期/时间的方法。（我们在第 8 章中看到过 `time.Time` 的示例，例如 375 ◄）

## 9.4. Go 标准库简述

### 9.4.8. 网络包

Go 标准库有许多支持网络和编程的包。net 包提供了用于通过 Unix 域套接字、网络套接字、TCP/IP 和 UDP 通信的函数和类型。该包还提供了域名解析的函数。

net/http 包使用了 net 包的许多功能，并提供了解析 HTTP 请求和响应的功能，以及一个基本的 HTTP 客户端。net/http 包还包含一个易于扩展的 HTTP 服务器，正如我们在第 2 章 ($24.4, 72 ➤）和第 3 章的练习中所看到的。net/url 包提供了 URL 解析和查询转义。

标准库中还包含其他一些高级网络相关的包。其中一个是 net/rpc（远程过程调用），它允许服务器提供对象，客户端可以调用对象的导出方法。另一个是 net/smtp（简单邮件传输协议）包，可发送电子邮件。

### 9.4.9. reflect 包

reflect 包提供了运行时反射（也称为内省），即在运行时访问和交互任意类型值的能力。

该包还提供了一些实用函数，例如 `reflect.DeepEqual()`，它可以比较任何两个值——例如切片（slices），切片无法使用 `==` 和 `!=` 运算符无法比较的。

Go 中的每个值都有两个属性：它的实际值和它的类型。`reflect.TypeOf()` 函数可以告诉我们任何值的类型。

```
x := 8.6
y := float32(2.5)
fmt.Printf("var x %v = %v\n", reflect.TypeOf(x), x)
fmt.Printf("var y %v = %v\n", reflect.TypeOf(y), y)
```

```
var x float64 = 8.6
var y float32 = 2.5
```

在这里，我们使用反射输出了两个浮点变量及其作为 Go 声明的类型。

当对值调用 `reflect.ValueOf()` 函数时，它返回一个 `reflect.Value`，它持有该值但并不使用值本身。如果我们想访问所持有的值，必须使用一个 `reflect.Value` 方法。

```
word := "Chameleon"
value := reflect.ValueOf(word)
```

```
text := value.String()
fmt.Println(text)
Chameleon
```

`reflect.Value` 类型有许多方法用于提取底层类型，包括 `reflect.Value.Bool()`、`reflect.Value.Complex()`、`reflect.Value.Float()`、`reflect.Value.Int()` 和 `reflect.Value.String()`。

reflect 包还可以处理切片和映射等集合类型，以及结构体（structs）；它甚至可以访问结构体的标签（tag）文本。（这种能力被 json 和 xml 编码器和解码器使用，正如我们在第 8 章看到的。）

```go
type Contact struct {
  Name string "check:len(3,40)"
  Id int "check:range(1,999999)"
}
person := Contact("Bjork", 0xDEEED)
personType := reflect.TypeOf(person)
if nameField, ok := personType.FieldName("Name"); ok {
  fmt.Printf("%q %q\n", nameField.Type, nameField.Tag)
}
```

```
"string" "Name" "check:len(3,40)" 
```

`reflect.Value` 持有的底层值是可以更改的，如果它是“setable”。设置性可以通过调用 `reflect.Value.CanSet()` 来检查。

```go
presidents := []string{"Obama", "Bush", "Clinton"}
sliceValue := reflect.ValueOf(presidents)
value := sliceValue.Index(1)
value.SetString("Bush")
fmt.Println(presidents)
```

```
Obama Bush Clinton
```

尽管字符串是不可变的，但 []string 中的任何项都可以被另一个字符串替换，这就是我们所做的。我们无法设置不可变的值，但可以使用 `reflect.Value.Elem()` 方法获取一个指向的 `reflect.Value`，通过它我们可以设置。

```
count := 1
value = reflect.ValueOf(&count)
if value.CanSet() {
  pointee := value.Elem()
  pointee.SetInt(2)
}
fmt.Println(count)
```

```
3
```

这段代码的输出显示，如果条件为假，循环体就不会执行。虽然我们无法设置不可变的值，但可以使用 `reflect.Value.Elem()` 方法获取一个指向的 `reflect.Value`，我们在代码结尾处这样做。

也可以使用反射调用任意函数和方法。这里有一个示例调用了两次自定义的 `TitleCase()` 函数（未显示），一次常规调用，一次使用反射。

```go
caption := "greg egan's dark integers"
title := TitleCase(caption)
fmt.Println(title)

titleFuncValue := reflect.ValueOf(TitleCase)
values := titleFuncValue.Call([]reflect.Value{reflect.ValueOf(caption)})
title = values[0].String()
fmt.Println(title)
```

```
Greg Egan's Dark Integers
Greg Egan's Dark Integers
```

`reflect.Value.Call()` 方法接收并返回一个 `[]reflect.Value` 切片。在这种情况下，我们传入单个值（即长度为 1 的切片），并检索单个结果值。

我们可以以类似的方式调用方法——事实上，我们可以查询方法是否存在并在仅在存在时进行调用。

```
a := list.New() // a.Len() == 0
b := list.New()
b.PushFront(1) // b.Len() == 1
c := stack.Stack()
c.Push(0.5)
c.Push(1.5) // c.Len() == 2
d := map[string]int{"A": 1, "B": 2, "C": 3} // len(d) == 3
```

