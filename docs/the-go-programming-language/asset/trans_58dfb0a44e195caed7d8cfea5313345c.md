

// String 将集合以 "{1 2 3}" 的形式返回为字符串。
func (s *IntSet) String() string {
    var buf bytes.Buffer
    buf.WriteByte('{')
    for i, word := range s.words {
        if word == 0 {
            continue
        }
        for j := 0; j < 64; j++ {
            if word&(1<<uint(j)) != 0 {
                if buf.Len() > len("{") {
                    buf.WriteByte(' ')
                }
                fmt.Fprintf(&buf, "%d", 64*i+j)
            }
        }
    }
    buf.WriteByte('}')
    return buf.String()
}

请注意上述 `String` 方法与 [3.5.4 节](#ebook_split_032.html#id-stringsandbyteslices) 中 `intsToString` 的相似之处；`bytes.Buffer` 在 `String` 方法中常以这种方式使用。`fmt` 包会特殊对待拥有 `String` 方法的类型，以便复杂类型的值能以用户友好的方式显示自身。`fmt` 不会打印值的原始表示（本例中为结构体），而是调用 `String` 方法。该机制依赖于接口和类型断言，我们将在 [第 7 章](#ebook_split_059.html#id-interfaces) 中解释。

现在我们可以演示 `IntSet` 的实际运行效果：

[点击此处查看代码图像](#ch06_images.html#id167pro01_r)

```
var x, y IntSet
x.Add(1)
x.Add(144)
x.Add(9)
fmt.Println(x.String()) // "{1 9 144}"

y.Add(9)
y.Add(42)
fmt.Println(y.String()) // "{9 42}"

x.UnionWith(&y)
fmt.Println(x.String()) // "{1 9 42 144}"

fmt.Println(x.Has(9), x.Has(123)) // "true false"
```

**注意**：我们将 `String` 和 `Has` 声明为指针类型 `*IntSet` 的方法，并非出于必要性，而是为了与其他两个方法保持一致，因为那两个方法需要指针接收者，因为它们要对 `s.words` 进行赋值。因此，`IntSet` *值* 没有 `String` 方法，这偶尔会导致如下意外情况：

[点击此处查看代码图像](#ch06_images.html#id167pro02_r)

```
fmt.Println(&x)         // "{1 9 42 144}"
fmt.Println(x.String()) // "{1 9 42 144}"
fmt.Println(x)          // "{[4398046511618 0 65536]}"
```

在第一种情况下，我们打印一个 `*IntSet` 指针，它确实拥有 `String` 方法。在第二种情况下，我们在 `IntSet` 变量上调用 `String()`；编译器会插入隐式的 `&` 操作，给我们一个指针，该指针拥有 `String` 方法。但在第三种情况下，因为 `IntSet` 值没有 `String` 方法，`fmt.Println` 会打印结构体的表示形式。切记不要忘记 `&` 操作符。将 `String` 定义为 `IntSet` 的方法而非 `*IntSet` 的方法可能是个好主意，但这需要根据具体情况判断。

### 练习 6.1

实现以下附加方法：

[点击此处查看代码图像](#ch06_images.html#id167pro03_r)

```
func (*IntSet) Len() int      // 返回元素数量
func (*IntSet) Remove(x int)  // 从集合中移除 x
func (*IntSet) Clear()        // 从集合中移除所有元素
func (*IntSet) Copy() *IntSet // 返回集合的副本
```

### 练习 6.2

定义一个可变参数方法 `(*IntSet).AddAll(...int)`，允许添加一组值，例如 `s.AddAll(1, 2, 3)`。

### 练习 6.3

`(*IntSet).UnionWith` 使用 `|`（按字并行的按位或运算符）计算两个集合的并集。为对应的集合运算实现 `IntersectWith`、`DifferenceWith` 和 `SymmetricDifference` 方法。（两个集合的对称差集包含仅存在于其中一个集合而不同时存在于两个集合中的元素。）

### 练习 6.4

添加一个 `Elems` 方法，返回一个包含集合元素的切片，适合使用 `range` 循环进行迭代。

### 练习 6.5

`IntSet` 使用的每个字的类型是 `uint64`，但在 32 位平台上 64 位运算可能效率低下。修改程序以使用 `uint` 类型，这是平台上最高效的无符号整数类型。不再除以 64，而是定义一个常量来保存 `uint` 的有效位大小（32 或 64）。你可以使用这个或许过于聪明的表达式 `32 << (^uint(0) >> 63)` 来达到此目的。

## 6.6 封装

如果对象的变量或方法对该对象的客户端代码不可见，则称该变量或方法被*封装*。封装有时称为*信息隐藏*，是面向对象编程的关键方面。

Go 只有一种机制来控制名称的可见性：大写字母开头的标识符会从定义它们的包中导出，小写字母开头的名称则不会。限制包成员访问的同一机制也限制了对结构体字段或类型方法的访问。因此，要封装一个对象，我们必须将其定义为结构体类型。

这就是上一节中 `IntSet` 类型被声明为结构体类型的原因，尽管它只有一个字段：

```
type IntSet struct {
    words []uint64
}
```

我们本可以将 `IntSet` 定义为切片类型，如下所示，尽管当然我们必须在其方法中将每处 `s.words` 替换为 `*s`：

```
type IntSet []uint64
```

虽然这种版本的 `IntSet` 本质上是等价的，但它会允许其他包的客户端代码直接读取和修改切片。换句话说，表达式 `*s` 可在任何包中使用，而 `s.words` 只能出现在定义 `IntSet` 的包中。

这种基于名称的机制的另一个后果是，封装的单元是包，而不是像许多其他语言那样是类型。结构体类型的字段对同一个包内的所有代码可见。代码出现在函数中还是方法中并无区别。

封装提供了三个好处。首先，因为客户端代码无法直接修改对象的变量，所以只需检查更少的语句即可了解这些变量的可能值。

其次，隐藏实现细节可以防止客户端代码依赖可能会改变的事物，这使设计者拥有更大的自由来演进实现，而无需破坏 API 兼容性。

作为一个例子，考虑 `bytes.Buffer` 类型。它经常用于累加非常短的字符串，因此在对象中预留一点额外空间以避免这种常见情况下的内存分配是一项有利的优化。由于 `Buffer` 是结构体类型，这部分空间表现为一个类型为 `[64]byte` 且名称小写的额外字段。当添加此字段时，因为它未被导出，`bytes` 包外部的 `Buffer` 客户端代码除了性能提升外，不会察觉到任何变化。下面展示了简化后的 `Buffer` 及其 `Grow` 方法：

[点击此处查看代码图像](#ch06_images.html#id169pro01_r)

```
type Buffer struct {
    buf     []byte
    initial [64]byte
    /* ... */
}

// Grow 在必要时扩展缓冲区容量，
// 以保证有空间容纳另外 n 个字节。[...]
func (b *Buffer) Grow(n int) {
    if b.buf == nil {
        b.buf = b.initial[:0] // 最初使用预分配的空间
    }
    if len(b.buf)+n > cap(b.buf) {
        buf := make([]byte, b.Len(), 2*cap(b.buf) + n)
        copy(buf, b.buf)
        b.buf = buf
    }
}
```

封装的第三个好处，在许多情况下也是最重要的，是它防止客户端代码随意设置对象的变量。因为对象的变量只能由同一个包中的函数设置，该包的作者可以确保所有这些函数都维护对象的内部不变量。例如，下面的 `Counter` 类型允许客户端代码增加计数器或将其重置为零，但不允许将其设置为任意值：

[点击此处查看代码图像](#ch06_images.html#id169pro02_r)

```
type Counter struct { n int }

func (c *Counter) N() int     { return c.n }
func (c *Counter) Increment() { c.n++ }
func (c *Counter) Reset()     { c.n = 0 }
```

