
# 列表 9.5

```go
func main() {
    fmt.Print("vector[int] : ")
    vGenInt := vector(10, -1)
    i, err := vGenInt.last()
    if i < 0 {
        fmt.Print("negative integer: ")
    }
    fmt.Printf("value: %d error: %v\n", i, err)

    fmt.Print("vector[string] : ")
    vGenStr := vector("A", "B", string([]byte(0xff)))
    s, err := vGenStr.last()
    if !utf8.ValidString(s) {
        fmt.Print("non-valid string: ")
    }
    fmt.Printf("value: %q error: %v\n", s, err)
}
```

```
输出:
vector[int] : negative integer: -1 error: <nil>
vector[string] : non-valid string: value: "\xff" error: <nil>
```

```，这就是当我在构造时设置切中的值时，如何构造一个底层类型为 int 的泛型值。这段代码的一个重要方面是构造调用。

# 列表 9.6

```go
// 零值构造
var vGenInt vector[int]
var vGenStr vector[string]

// 非零值构造
vGenInt := vector(10, -1)
vGenStr := vector("A", "B", string([]byte(0xff)))
```

当将这些泛型构造为零值时，编译器无法推断类型。然而，在构造期间有初始化的情况下，编译器可以推断类型。

规范中有一个方面关注将泛型构造为零值状态。

# 列表 9.7

```go
type vector[T any] []T

func (v vector[T]) last() (T, error) {
    var zero T
    if len(v) == 0 {
        return zero, errors.New("empty")
    }
    return v[len(v)-1], nil
}
```

我需要关注 `last` 方法的声明以及该方法如何返回泛型 T 的值。在第一个返回处，我需要返回类型 T 的零值。当前草稿提供了两种编写此代码的方案。我已经看到了第一个方案：一个名为 `zero` 的变量被构造为类型 T 的零值，然后使用该变量返回。

另一个选项是使用内置函数 `new` 并在返回语句中解引用指针。

# 列表 9.8

```go
type vector[T any] []T

func (v vector[T]) last() (T, error) {
  if len(v) == 0 {
    return new(T), errors.New("empty")
  }
  return v[len(v)-1], nil
}
```

这个版本的 `last` 方法使用了内置函数 `new` 进行零值构造。

注意：我可能会想为什么不使用 `T{}` 来执行零值构造？这种语法适用于所有类型（如 `int`、`string`, `bool`）。

# 9.3 结构体类型

如果我想使用 `struct` 来声明我自己的泛型类型呢？

# 列表 9.9

```go
type node[T any] struct {
  Data T
  next *node[T]
  prev *node[T]
}
```

这个结构体类型被声明用于表示链表。每个节点包含一个存储并由列表管理的个体数据。使用方括号 `[]` 定义了在编译时确定的泛型类型。`any` 约束描述了类型 T 可以变成什么。

# 列表 9.10

```go
type list[T any] struct {
    first *node[T]
    last  *node[T]
}
```

第二个结构体类型名为 `list`，通过指向 `first` 和 `last` 来表示节点集合。这些字段分别指向链表中的节点，就像节点中的 `next` 和 `prev` 字段一样。

# 列表 9.11

```go
func (l *list[T]) add(data T) *node[T] {
    n := &node[T]{
        data: data,
        prev: l.last,
    }
    if l.first == nil {
        l.first = &n
        l.last = &n
        return &n
    }
    l.last.next = &n
    l.last = &n
}
```
