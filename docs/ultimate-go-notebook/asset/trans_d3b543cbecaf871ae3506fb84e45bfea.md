

Listing 4.34

```go
type user struct {
    name string
    email string
}

type admin struct {
    person user // 未嵌入
    level string
}
```

这是嵌入。

Listing 4.35

```go
type user struct {
    name string
    email string
}

type admin struct {
    user // 值语义嵌入
    level string
}
```

`person` 字段被删除了，只下了类型名。我也可以使用指针语义嵌入一个类型。

Listing 4.36

```go
type user struct {
    name string
    email string
}

type admin struct {
    *user // 指针语义嵌入
    level string
}
```

在这种情况下，嵌入的是该类型的指针。无论哪种情况，访问嵌入的值都是通过使用类型的名称完成的。

理解嵌入的最佳方式是将 `user` 类型视为内部类型，将 `admin` 视为外部类型。正是这种内部/外部类型关系是神奇的，因为通过嵌入，与内部类型相关的所有内容（字段和方法）都可以提升到外部类型。

# Listing 4.37

```go
type user struct {
    name string
    email string
}

func (u *user) notify() {
    fmt.Printf("Sending user email To %s<%s\n",
    u.name,
    u.email)
}

type admin struct {
    *user
    level string
}

func main() {
    ad := &admin{
        user: &user{
            name: "john smith",
            email: "john@yahoo.com",
        },
        level: "super",
    }

    ad.user.notify()
    ad.notify() // 外部类型提升
}
```

输出：
Sending user email To smith<john@yahoo.com>
Sending user email To john smith<john@yahoo.com>

一旦我为 `user` 类型添加了一个名为 `notify` 的方法并编写了一个小的 `main` 函数，我就可以看到无论直接通过内部指针值调用 `notify` 方法，还是通过外部类型值调用，输出都是相同的。为 `user` 类型声明的 `notify` 方法可以直接被 `admin` 类型值访问。

尽管这看起来像继承，但我必须小心。这并不是关于状态重用，而是关于行为提升。

# Listing 4.38

```go
type notifier interface {
    notify()
}

func sendNotification(n notifier) {
    n.notify()
}
```

现在我添加了一个接口和一个多态函数，该函数接受任何实现了 `notifier` 接口定义的完整行为集的具体类型。这只是一个名为 `notify` 的方法。

由于嵌入和提升，`admin` 类型的值现在实现了 `notifier` 接口。

# Listing 4.39

```go
func main() {
    ad := admin{
        user: &user{
            name: "john smith",
            email: "john@yahoo.com",
        },
        level: "super",
    }
    sendNotification(&ad)
}
```

输出：
Sending user email To john smith<john@yahoo.com>
```

我可以将 `admin` 值的地址发送到多态函数，因为嵌入将 `notify` 行为提升到了 `admin` 类型。

# Listing 4.40

```go
type admin struct {
    *user // 指针语义嵌入
    level string
}

func (a *admin) notify() {
    fmt.Printf("Sending admin Email To %s<%s\n",
        a.name,
        a.email)
}
```

当外部类型实现了一个内部类型已经实现的方法时，提升就不会发生。

# Listing 4.41

```go
func main() {
    ad := admin{
        user: &user{
            name: "john smith",
            email: "john@yahoo.com",
        },
        level: "super",
    }
    sendNotification(&ad)
}
```

输出：
Sending admin email To john smith<john@yahoo.com>
```

我看到外部类型的方法现在正在执行。

## 4.14 导出 (Exporting)

导出提供了一种能力，允许声明标识符在声明所在包之外的代码中可访问。包是 Go 中编译代码的基本单位。它代表一个物理的编译代码单元，通常作为宿主机操作系统上的编译库。导出决定了跨包边界的标识符访问权限。

Listing 4.42

```go
package counters
type AlertCounter int
```

在这种情况下，由于使用了大写字母来命名类型 `AlertCounter`，该类型是导出的，并且可以被 `counters` 包之外的代码直接引用。

Listing 4.43

```go
package counters
type alertCounter int
```

现在我将类型名称更改为小写字母开头，该类型是未导出的。这意味着只有 `counters` 包内部的代码可以直接引用此类型。

Listing 4.44

```go
package counters
type alertCounter int
func New(value int) alertCounter {
  return alertCounter(value)
}
```

尽管上面的代码是合法的语法并且可以通过编译，但它没有意义。返回一个未导出类型的值是有误的，因为调用者（可能存在另一个包中）无法直接引用类型名称。

# Listing 4.45

```go
package main

import (
    "fmt"
    "github.com/ardanlabs/example/exporting"
)

func main() {
    counter := counters.New(10)
    fmt.Printf("Counter: %d\n", counter)
}
```
*（注：4.45 的 OCR 严重乱码；我根据前几页的上下文重构了逻辑代码）*

# Listing 4.46

```go
package users

type User struct {
    Name string
    ID int

    password string
}

type Manager struct {
    Title string
    user
}
```

在这种情况下，`users` 包之外的代码可以构造一个 `Manager`，但由于嵌入类型是未导出的，该类型的字段是可访问的。否则，序列化器（Marshallers）将无法工作。

