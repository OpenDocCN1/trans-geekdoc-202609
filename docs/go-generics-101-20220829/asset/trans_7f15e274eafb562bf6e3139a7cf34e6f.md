

```go
type Getter[T any] interface {
    Get() T
}

type Age[T uint8 | int16] struct {
    n T
}

func (a Age[T]) Get() T {
    return a.n
}

func doSomething[T any](g Getter[T]) T {
    return g.Get()
}

// The two lines fail to compile.
var z = doSomething(Age[uint8]{255}) // error
var w = doSomething(Age[int16]{256}) // error

// The two lines compile okay.
var x = doSomething[uint8](Age[uint8]{255})
var y = doSomething[int16](Age[int16]{256})
```

## 6.4 将基本接口类型作为类型实参传递

上面提到，如果基本接口类型满足（实现）类型参数的约束，则可以作为类型实参传递给类型参数。下面的代码展示了这样的一个例子。

```go
package main

type Base[T any] []T

type _ Base[any]
type _ Base[error]

func Gf[T any](x T) {}

var _ = Gf[any]
var _ = Gf[error]

func main() {
    Gf[any](123)
    Gf[any](true)
    Gf[error](nil)
}
```

根据当前规范（Go 1.19），对于涉及类型参数的赋值：

- 如果目标类型是类型参数，且源值是一个未类型化的值，那么仅当该未类型化的值可赋值给目标类型参数类型集合中的每个类型时，赋值才有效。
- 如果目标类型是类型参数，但源类型是普通类型，那么仅当源普通类型是未命名的，且其值可赋值给目标类型参数类型集合中的每个类型时，赋值才有效。
- 如果源类型是类型参数，但目标类型是普通类型，那么仅当目标普通类型是未命名的，且源类型参数类型集合中的每个类型的值都可赋值给目标普通类型时，赋值才有效。
- 如果目标类型和源类型都是类型参数，那么赋值无效。

从这些规则中，我们可以得知，一个命名类型的值不能赋值给另一个命名类型。

在下面的代码片段中，有四个无效的赋值。

```go
func dat[T ~int | ~float64, S *int | []bool]() {
    var _ T = 123 // okay
    var _ S = nil // okay
}
```

```go
func zum[T []byte](x []byte) {
    var t T = x // okay
    type Bytes []byte
    var y Bytes = x // okay (both are ordinary types)
    x = t // okay
    x = y // okay

    // Both are named types.
    t = y // error
    y = t // error

    // To make the above two assignments valid,
    // the sources in them must be converted.
    t = T(y)     // okay
    y = Bytes(t) // okay
}
```

```go
func pet[A, B []byte](x A, y B) {
    // Both are type parameters.
    x = y // error: cannot use y as type A in assignment
    y = x // error: cannot use x as type B in assignment
}
```

目前尚不清楚未来 Go 版本是否会放宽这些赋值规则。看起来可能性很小。

```go
func MyNew[T any]() *T {
    var t T
    return &t
}
```

## 7.14 调用预声明的 make 函数要求其第一个参数（容器类型）具有核心类型

目前（Go 1.19），在下面的代码片段中，函数 `voc` 和 `ted` 都无法编译，而另外两个可以编译。原因是调用预声明的 `make` 函数的第一个参数必须具有核心类型。`voc` 和 `ted` 这两个函数都不满足此要求，而另外两个函数都满足此要求。

```go
func voc[T chan bool | chan int]() {
    _ = make(T) // error: invalid argument: no core type
}
```

```go
func ted[T chan<- int | <-chan int]() {
    _ = make(T) // error: invalid argument: no core type
}
```

```go
type Stream chan int
type Queue Stream
```

```go
func fat[T Stream | chan int | Queue | chan<- int]() {
    _ = make(T) // okay
}
```

```go
func nub[T Stream | chan int | Queue | <-chan int]() {
    _ = make(T) // okay
}
```

根据我的理解，这个要求是为了确保对制作出的容器（在上面的例子中是通道）进行的后续操作始终合法。例如，确保从制作出的通道接收到的值具有指定类型（无论是类型参数还是普通类型）。

就我个人而言，我认为这一要求过于严格。毕竟，在某些情况下，预想的后续操作并不会发生。

要在泛型函数中使用没有核心类型的类型参数的值，我们可以将这些值作为值实参传递给函数，如下面的代码所示。

```go
func doSomething(any) {}
```

```go
func voc2[T chan bool | chan int](x T) {
    doSomething(x)
}
```

```go
func ted2[T chan<- int | <-chan int](x T) {
    doSomething(x)
}
```

由于同样的要求，下面两个函数都无法编译。

```go
func zig[T ~[]int | map[int]int](c T) {
    _ = make(T) // error: invalid argument: no core type
}
```

```go
func rat[T ~[]int | ~[]bool](c T) {
    _ = make(T) // error: invalid argument: no core type
}
```

对预声明的 `new` 函数的调用没有此要求。

## 7.15 调用预声明的 delete 函数要求其第一个参数类型集合中的所有类型具有相同的键类型

请注意，这里的相同键类型可以是普通类型，也可以是类型参数类型。

以下两个函数都可以编译。

```go
func zuk[M ~map[int]string | ~map[int]bool](x M, k int) {
    delete(x, k)
}
```

```go
func pod[M map[K]int | map[K]bool, K ~int | ~string](x M, k K) {
    delete(x, k)
}
```

## 7.16 调用预声明的 close 函数要求其参数类型集合中的所有类型都是通道类型

以下函数可以编译。

```go
func dig[T ~chan int | ~chan bool | ~chan<- string](x T) {
    close(x)
}
```

请注意，当前 Go 规范要求调用预声明的 `close` 函数的参数必须具有核心类型。这与官方标准 Go 编译器的实现不一致。

## 7.17 调用预声明的 complex、real 和 imag 函数目前不接受类型参数

使用类型参数作为参数调用这三个函数可能会违反本章第一节提到的原则规则。

这是当前自定义泛型设计无法解决的问题。已经有一个相关的 issue。

## 7.18 关于空类型集合的约束

某些接口类型的类型集合可能为空。空类型集合的接口类型实现任何接口类型，包括其自身。

空类型集合的接口类型在实践中完全无用，但从理论角度看，它们可能会影响实现的完美性。

当前官方标准 Go 编译器（v1.19）的实现中确实存在几个不完美之处。

例如，下面的函数是否应该编译？在最新的官方标准 Go 编译器（v1.19）中，它可以编译。然而，前面的一节提到过，`make` 调用要求其参数具有核心类型。下面代码中声明的约束 `C` 的类型集合为空，因此它没有核心类型，那么 `foo` 函数内的 `make` 调用就不应该编译。

```go
// This is an empty-type-set interface type.
type C interface {
    map[int]int
    M()
}

func foo[T C]() {
    var _ = make(T)
}
```

下面是另一个例子，其中函数 `g` 中的所有函数调用都应该编译通过。然而，在最新的官方标准 Go 编译器（v1.19）中，其中两个调用无法编译。

```go
func f1[T any](x T) {}
func f2[T comparable](x T) {}
func f3[T []int](x T) {}
func f4[T int](x T) {}
```

```go
// This is an empty-type-set interface type.
type C interface {
    []int
    m()
}

func g[V C](v V) {
    f1(v) // okay
    f2(v) // error: V does not implement comparable
    f3(v) // okay
    f4(v) // error: V does not implement int
}
```

当前 Go 规范特别指出：

> 实现限制：如果操作数的类型是一个具有空类型集合的类型参数，编译器可以不报告错误。带有此类类型参数的函数无法被实例化；任何尝试都会在实例化点导致错误。

因此，上述展现出的不完美之处并非官方标准 Go 编译器的缺陷。

