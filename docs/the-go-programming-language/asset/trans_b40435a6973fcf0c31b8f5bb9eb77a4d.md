

# 仅访问或修改内部值的函数

仅访问或修改类型内部值的函数，例如下面 `log` 包中 `Logger` 类型的方法，被称为 *getters*（获取器）和 *setters*（设置器）。然而，在命名 getter 方法时，我们通常省略 `Get` 前缀。这种对简洁性的偏好适用于所有方法，而不仅仅是字段访问器，也适用于其他冗余前缀，如 `Fetch`、`Find` 和 `Lookup`。

[点击此处查看代码图片](#ch06_images.html#id170pro01_r)

```
package log

type Logger struct {
    flags  int
    prefix string
    // ...
}

func (l *Logger) Flags() int
func (l *Logger) SetFlags(flag int)
func (l *Logger) Prefix() string
func (l *Logger) SetPrefix(prefix string)
```

## Go 风格不禁止导出字段

Go 风格不禁止导出字段。当然，一旦导出，若不进行不兼容的 API 变更，字段就无法取消导出，因此初始选择应当审慎，并应考虑必须维护的不变量的复杂性、未来变更的可能性，以及会受变更影响的客户端代码量。

## 封装并非总是可取的

封装并非总是可取的。通过将其表示形式揭示为纳秒数的 `int64`，`time.Duration` 让我们能将所有常用的算术和比较操作用于时长，甚至可以定义该类型的常量：

[点击此处查看代码图片](#ch06_images.html#id170pro02_r)

```
const day = 24 * time.Hour
fmt.Println(day.Seconds()) // "86400"
```

## IntSet 与 geometry.Path

作为另一个例子，将 `IntSet` 与本章开头的 `geometry.Path` 类型进行对比。`Path` 被定义为切片类型，允许其客户端使用切片字面量语法构造实例，使用 range 循环遍历其点，等等，而这些操作对 `IntSet` 的客户端则是被禁止的。

这里是关键区别：`geometry.Path` 本质上就是一个点的序列，不多不少，我们预见不到会给它添加新字段，因此 `geometry` 包揭示 `Path` 是一个切片是合理的。相比之下，`IntSet` 只是恰好用 `[]uint64` 切片表示。它本可以用 `[]uint` 表示，或者对于稀疏或极小的集合用完全不同的表示，它或许还能从额外功能中受益，比如一个用于记录集合元素数量的额外字段。基于这些理由，让 `IntSet` 保持不透明是合理的。

## 小结

在本章中，我们学习了如何将方法与命名类型关联，以及如何调用这些方法。虽然方法对面向对象编程至关重要，但它们只是全貌的一半。为了完善它，我们需要 *interfaces*（接口），这是下一章的主题。

# 7. 接口

接口类型表达了对其他类型行为的泛化或抽象。通过泛化，接口让我们能编写更灵活、适应性更强的函数，因为它们不依赖于某一特定实现的细节。

许多面向对象语言都有接口的概念，但 Go 接口的独特之处在于它们是 *satisfied implicitly*（隐式满足）的。换句话说，无需声明某个具体类型满足了哪些接口；仅拥有必要的方法就足够了。这种设计让你能创建新接口，使现有的具体类型满足它们，而无需修改现有类型，这对于你无法控制的包中定义的类型特别有用。

在本章中，我们将首先了解接口类型及其值的基本机制。在此过程中，我们将研究标准库中的几个重要接口。许多 Go 程序对标准接口的使用程度不亚于它们自己的接口。最后，我们将探讨 *type assertions*（类型断言）（[§7.10](#ebook_split_069.html#id-typeassertions)）和 *type switches*（类型开关）（[§7.13](#ebook_split_072.html#id-typeswitches)），并了解它们如何实现另一种泛化。

## 7.1 接口即契约

我们迄今为止看到的所有类型都是 *concrete types*（具体类型）。具体类型指定了其值的确切表示形式，并暴露了该表示形式的内在操作，例如数字的算术运算，或切片的索引、`append` 和 `range`。具体类型还可以通过其方法提供额外的行为。当你拥有一个具体类型的值时，你确切地知道它 *是什么* 以及你能用它 *做什么*。

Go 中还有另一种类型，称为 *interface type*（接口类型）。接口是一种 *abstract type*（抽象类型）。它不暴露其值的表示形式或内部结构，也不暴露它们支持的基本操作集；它只揭示它们的某些方法。当你拥有一个接口类型的值时，你不知道它 *是什么*；你只知道它能 *做什么*，更准确地说，是其方法提供了哪些行为。

贯穿全书，我们一直在使用两个用于字符串格式化的相似函数：`fmt.Printf`，它将结果写入标准输出（一个文件）；以及 `fmt.Sprintf`，它将结果作为 `string` 返回。如果格式化结果这项艰苦工作，仅因结果用法上的这些表面差异就不得不重复编写，那将是不幸的。得益于接口，并非如此。这两个函数实际上都是第三个函数 `fmt.Fprintf` 的包装器，后者对如何处理其计算出的结果持不可知态度：

[点击此处查看代码图片](#ch07_images.html#id172pro01_r)

```
package fmt

func Fprintf(w io.Writer, format string, args ...interface{}) (int, error)

func Printf(format string, args ...interface{}) (int, error) {
    return Fprintf(os.Stdout, format, args...)
}

func Sprintf(format string, args ...interface{}) string {
    var buf bytes.Buffer
    Fprintf(&buf, format, args...)
    return buf.String()
}
```

`Fprintf` 的 `F` 前缀代表 *file*（文件），表明格式化输出应写入作为第一个参数提供的文件。在 `Printf` 的情况下，参数 `os.Stdout` 是一个 `*os.File`。然而在 `Sprintf` 的情况下，参数不是文件，尽管它表面上类似于文件：`&buf` 是一个指向内存缓冲区的指针，字节可被写入其中。

`Fprintf` 的第一个参数也不是文件。它是一个 `io.Writer`，这是一个具有以下声明的接口类型：

[点击此处查看代码图片](#ch07_images.html#id172pro02_r)

```
package io

// Writer is the interface that wraps the basic Write method.
type Writer interface {
    // Write writes len(p) bytes from p to the underlying data stream.
    // It returns the number of bytes written from p (0 <= n <= len(p))
    // and any error encountered that caused the write to stop early.
    // Write must return a non-nil error if it returns n < len(p).
    // Write must not modify the slice data, even temporarily.
    //
    // Implementations must not retain p.
    Write(p []byte) (n int, err error)
}
```

`io.Writer` 接口定义了 `Fprintf` 与其调用者之间的契约。一方面，契约要求调用者提供一个具体类型的值，如 `*os.File` 或 `*bytes.Buffer`，该类型拥有名为 `Write`、具有适当签名和行为的方法。另一方面，契约保证 `Fprintf` 在给定任何满足 `io.Writer` 接口的值时都能完成其工作。`Fprintf` 不能假设它在写入文件或内存，只能假设它可以调用 `Write`。

因为 `fmt.Fprintf` 对值的表示形式不做任何假设，仅依赖 `io.Writer` 契约保证的行为，我们可以安全地将任何满足 `io.Writer` 的具体类型的值作为第一个参数传递给 `fmt.Fprintf`。这种用满足同一接口的另一种类型替换一种类型的自由被称为 *substitutability*（可替换性），是面向对象编程的标志。

