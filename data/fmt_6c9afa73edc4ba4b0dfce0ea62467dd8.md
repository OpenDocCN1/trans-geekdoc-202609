
我们创建了一个名为 `Bird` 的接口。`Bird` 接口有一个方法 `Fly()`。我们创建了三个结构体 `Eagle`、`Pigeon` 和 `Penguin`，它们都通过覆写 `Fly()` 方法实现了 `Bird` 接口。最重要的是，我们定义了一个函数 `flyNow(b Bird)`。`flyNow` 函数期望一个 `Bird` 作为参数，并在 `Bird` 类型的变量上调用 `Fly` 方法。`flyNow` 函数并不知道会传入哪一个 `Bird` 的实现；它只知道该实现会有一个 `Fly` 方法。我们可以传入任何实现了 `Bird` 接口的类型的对象。在 `main()` 函数中，我们调用了 `flyNow` 函数三次，并分别传入了 `Eagle{}`、`Pigeon{}` 和 `Penguin{}` 的值。当 `flyNow` 函数调用 `Fly` 方法时，实际调用会进入 `Eagle`、`Pigeon` 或 `Penguin` 的接收者。

### 9.3 空接口

到目前为止，我们已经看到，如果一个类型拥有某个接口的所有方法，那么它便满足该接口，并隐式地实现了该接口。但假如一个接口没有任何方法会怎样？在这种情况下，所有类型都满足该接口。没有任何方法的接口被称为空接口。

因为所有类型都满足空接口，所以我们可以将任意类型的值赋给该接口的变量。

**程序 9.6**

```go
package main

import "fmt"

type MyEmpty interface {
}

type Student struct {
	id   int
	name string
}

func main() {
	var empty MyEmpty
	empty = 10
	fmt.Println(empty)
	empty = "a"
	fmt.Println(empty)
	empty = 22.3
	fmt.Println(empty)
	empty = Student{101, "Shyam"}
	fmt.Println(empty)
}
```

上述程序的输出如下：

```
10
a
22.3
{101 Shyam}
```

我们创建了一个名为 `MyEmpty` 的空接口。接口 `MyEmpty` 没有任何方法。我们还创建了一个 `Student` 结构体，其字段为 `id` 和 `name`。在 `main` 函数中，我们创建了一个名为 `empty` 的 `MyEmpty` 接口变量。我们向该变量赋予了不同类型的值，如 `10`、`"a"`、`22.3` 和 `Student{101, "Shyam"}`，并打印了这些值。

但是空接口有什么好处呢？我们通过查看标准库代码来理解它的好处。我们经常使用 `fmt` 包在控制台打印输出。你是否曾尝试理解 `fmt.Println()` 函数是如何工作的？为什么它允许我们传入任意值？让我们先看一下这个函数的签名：

```go
func Println(a ...interface{}) (n int, err error) {
	return Fprintln(os.Stdout, a...)
}
```

请注意该函数的参数。它接受空接口的可变参数。也就是说，可变参数意味着你可以传入任意数量的参数，空接口则意味着你可以传入任意类型的值。

### 9.4 方法集

方法集是使类型隐式实现接口的方法集合。到目前为止，我们已经看到，当一个类型定义了某个接口的所有方法时，该类型就会隐式地实现该接口的所有方法。但我们还没有看到方法应该是指针接收者方法还是值接收者方法。接口方法并不指定实现类型应该使用指针接收者还是值接收者。

如果类型 `T` 具有（某个接口的）指针接收者方法，那么实现该接口的是 `*T`，而不是 `T`。我们可以将 `T` 的地址赋给接口变量。如果我们尝试将 `T` 的值赋给接口变量，就会得到一个编译错误。让我们通过下面的程序来理解这一点：

**程序 9.7**

```go
package main

import "fmt"

type ltr interface {
	m1()
	m2()
}

type St struct {
}
```

#### 程序 9.7

```go
package main

import "fmt"

type Itr interface {
    m1()
    m2()
}

type St struct {
}

func (s *St) m1() {
    fmt.Println("In m1 of St")
}

func (s *St) m2() {
    fmt.Println("In m2 of St")
}

func main() {
    var i Itr
    i = St{}
    i.m1()
    i.m2()
}
```

上述程序的错误如下：

#### 错误 9.3

```text
./main.go:20:4: cannot use St literal (type St) as type Itr in assignment:
St does not implement Itr (m1 method has pointer receiver)
```

在程序 9.7 中，我们定义了一个接口 `Itr`。该接口有两个方法：`m1` 和 `m2`。我们定义了一个结构体类型 `St`。类型 `St` 通过使用指针接收器定义 `m1` 和 `m2` 方法来实现 `Itr` 接口。在 `main` 函数中，我们使用 `var` 关键字声明了一个 `Itr` 的变量，并将 `St` 的值赋给它。然后，我们在接口变量上调用了 `m1` 和 `m2` 方法。但运行此代码时，我们会得到编译错误。错误提示 `St` 未实现 `Itr`。出现此错误的原因是 `*St` 实现 `Itr` 接口，而不是 `St`。

如果我们重新运行上述代码，将 `St` 的地址赋给变量 `i`，代码将正常工作。

当我们通过值接收器实现接口时，可以将该类型的值和地址都赋给接口。让我们在以下代码中查看这一点：

#### 程序 9.8

```go
package main

import "fmt"

type Itr interface {
    m1()
    m2()
}

type St struct {
}

func (s St) m1() {
    fmt.Println("In m1 of St")
}

func (s St) m2() {
    fmt.Println("In m2 of St")
}

func main() {
    var i Itr
    fmt.Println("Assigning value of St")
    i = St{}
    i.m1()
    i.m2()
    fmt.Println("Assigning Address of St")
    i = &St{}
    i.m1()
    i.m2()
}
```

上述程序的输出如下：

**分配 St 的值**  
**在 St 的 m1 中**  
**在 St 的 m2 中**  
**分配 St 的地址**  
**在 St 的 m1 中**  
**在 St 的 m2 中**

在上述代码中，我们通过使用值接收器定义 `m1` 和 `m2` 方法来实现 `Itr` 接口。在 `main` 函数中，我们尝试将 `St` 的值和地址都赋给一个接口变量，并且它工作正常。在此代码中我们不会得到编译错误。

### 方法集的结论

- 如果类型 `T` 通过定义指针接收器方法来实现接口 `I`，那么只有 `*T` 会实现接口 `I`，而 `T` 不会。因此，我们只能将 `T` 的地址赋给接口变量。
- 如果类型 `T` 通过定义值接收器来实现接口 `I`，那么 `T` 和 `*T` 都实现接口 `I`。因此，我们可以将 `T` 的值和地址都赋给接口变量。

### 9.5 经常使用的内置/stdlib 接口

标准库中有太多常用的接口。我们无法在此涵盖所有这些接口。我们将在本节中介绍 `Stringer` 接口，并在第 9.5.3 节中看到 error 接口的实现。

#### 9.5.1 Stringer 接口

`Stringer` 接口对于打印自定义输出非常有用。它只有一个名为 `String` 的方法，该方法返回一个字符串。当我们使用 `fmt.Println` 打印某个类型的值时，如果该类型重写了 `String()` 方法，则 `String()` 方法会在内部被调用。`fmt` 包会打印 `String()` 方法返回的内容。

#### 程序 9.9

```go
package main

import "fmt"

type Dollar float64

func (d Dollar) String() string {
    return fmt.Sprintf("$%f", d)
}

func main() {
    var d Dollar = 23.3
    fmt.Println(d)
}
```

上述程序的输出如下：

```text
$23.300000
```

#### 9.5.2 sort 包的 Interface 接口

Golang 标准库中有一个名为 `sort.Interface` 的接口。请注意，接口名称本身就是 `Interface`。该接口在 `sort` 包中定义，用于对用户定义类型的切片进行排序。该接口有三个方法：`Len`、`Less` 和 `Swap`。下面给出的代码片段是来自 `sort` 包的 `Interface` 接口的定义：

#### 程序 9.10

```go
package sort

type Interface interface {
    Len() int
    Less(i, j int) bool
    Swap(i, j int)
}
```

如果我们想对任何类型的切片进行排序，则需要调用 `sort` 包的 `Sort` 函数。`Sort` 函数期望 `Interface` 类型。因此，我们可以传递任何实现 `sort.Interface` 的类型。该类型可以通过实现全部三个方法来实现 `Interface` 接口：

#### 程序 9.11

```go
package main

import (
    "fmt"
    "sort"
)

type Student struct {
    Name  string
    Marks int
}

func (s Student) String() string {
    return fmt.Sprintf("%s: %d", s.Name, s.Marks)
}

type ByMarks []Student

func (a ByMarks) Len() int           { return len(a) }
func (a ByMarks) Swap(i, j int)      { a[i], a[j] = a[j], a[i] }
func (a ByMarks) Less(i, j int) bool { return a[i].Marks < a[j].Marks }

func main() {
    students := []Student{
        {"Bob", 31},
        {"John", 42},
        {"Michael", 17},
        {"Jenny", 26},
    }
    fmt.Println("Before sorting =", students)
    sort.Sort(ByMarks(students))
    fmt.Println("After sorting =", students)
}
```

上述程序的输出如下：

```text
Before sorting = [Bob: 31 John: 42 Michael: 17 Jenny: 26]
After sorting = [Michael: 17 Jenny: 26 Bob: 31 John: 42]
```

在程序 9.11 中，我们声明了一个名为 `Student` 的结构体。我们在 `Student` 中定义了 `String()` 方法，以便以美观的方式打印 `Student` 对象。然后，我们创建了一个新的 `Student` 切片类型，即 `ByMarks`，并按如下方式在 `ByMarks` 类型上定义了 `Interface` 的全部三个方法：

- `Len()` 返回切片的长度。
- `Swap()` 将第 i 个索引元素与第 j 个索引元素交换。
- `Less()` 具有判断第 i 个索引元素和第 j 个元素中哪个更小的逻辑。

在 `main` 函数中，我们有一个包含四个元素的 `Student` 切片。当我们打印 `students` 变量时，它按这些元素插入的顺序打印。在下一行，我们通过传递 `sort.Sort()` 函数对 `students` 变量进行排序。在将其传递给 `sort.Sort()` 函数之前，我们已将 `students` 强制转换为 `ByMarks` 类型。

上述方法对于排序来说不必要地复杂。`Len` 和 `Swap` 方法是不必要的，因为 `Sort` 函数应该具有内部逻辑来查找切片的长度并交换元素。`sort` 包有一个函数可以克服这种复杂性。我们可以使用 `sort` 包的 `Slice` 函数。我们不需要实现任何接口。`sort.Slice` 函数期望两个参数：

- 我们想要排序的元素切片。
- 用于排序逻辑的函数。

以下代码演示了 `Slice` 函数：

#### 程序 9.12

```go
package main

import (
    "fmt"
    "sort"
)

type Student struct {
    Name  string
    Marks int
}

func (s Student) String() string {
    return fmt.Sprintf("%s: %d", s.Name, s.Marks)
}

func main() {
    students := []Student{
        {"Bob", 31},
        {"John", 42},
        {"Michael", 17},
        {"Jenny", 26},
    }
    fmt.Println("Before sorting", students)
    sort.Slice(students, func(i, j int) bool {
        return students[i].Marks < students[j].Marks
    })
    fmt.Println("After sorting", students)
}
```

上述程序的输出如下：

```text
Before sorting [Bob: 31 John: 42 Michael: 17 Jenny: 26]
After sorting [Michael: 17 Jenny: 26 Bob: 31 John: 42]
```

在程序 9.12 中，`Student` 结构体未实现任何接口。此代码调用 `sort.Slice()` 方法。我们传递了一个学生切片和一个匿名函数。匿名函数具有按 Marks 升序对学生进行排序的逻辑。

### 9.6 结构体中的接口

接口可以在结构体体内使用。我们既可以将接口用作嵌入类型，也可以定义接口变量。我们不能在创建结构体值时传递接口的实际值，因为接口是抽象的。我们需要传递实际实现类型的值。因此，当我们在结构体上调用接口的方法时，调用将转到实际实现类型。

#### 9.6.1 接口变量作为结构体字段

接口变量可以用作结构体字段。当创建该结构体的对象时，我们需要按如下所示为接口传递实际实现值：

#### 程序 9.13

```go
package main

import "fmt"

type Executor interface {
    Execute()
}

type Thread struct {
}

func (t Thread) Execute() {
    fmt.Println("Executing thread")
}

type Process struct {
    exe Executor
}

func main() {
    p := Process{Thread{}}
    p.exe.Execute()
}
```

上述程序的输出如下：

```text
Executing thread
```

在程序 9.13 中，我们创建了一个名为 `Process` 的结构体，其中接口变量 `exe` 作为字段。`exe` 字段是 `Executor` 接口的变量。`Thread` 结构体实现了 `Executor` 接口。在 `main` 函数中，我们创建了一个 `Process` 的变量，并为 `Executor` 字段传递了 `Thread` 值。我们在 `p` 变量的 `exe` 字段上调用了 `Execute` 方法。

### 结论

- 接口中的方法没有主体。接口的所有方法都是纯抽象的。
- 接口的方法可以有参数和返回类型。
- 任何自定义类型都可以实现接口。
- 没有显式语法来实现接口。当任何类型定义了接口的所有方法时，该类型就会隐式实现接口。
- 实现接口的类型也可以有其他方法。
- 一个类型可以实现多个接口。
- 一个接口可以被许多类型实现。
- 当接口没有任何方法时，它被称为空接口。空接口默认由所有类型实现。
- 接口可以作为结构体字段使用。当使用时，我们需要在创建结构体对象时传递接口的实际实现。
- 在 Golang 中可以使用接口实现多态。

### 问题

以下程序的结果是什么？

```go
package main

import "fmt"

type I interface {
