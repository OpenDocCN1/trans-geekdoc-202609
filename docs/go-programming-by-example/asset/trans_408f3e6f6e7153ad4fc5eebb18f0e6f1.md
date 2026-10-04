

```
package main

import (
    "fmt"
    "math/rand"
)

func main() {

    // define array
    fmt.Println("define map")
    products := make(map[string]int)
    customers := make(map[string]int)

    // insert data
    fmt.Println(">>>>>insert map data")
    products["product1"] = rand.Intn(100)
    products["product2"] = rand.Intn(100)

    customers["cust1"] = rand.Intn(100)
    customers["cust2"] = rand.Intn(100)


    // display data
    fmt.Println(">>>>>display map data")
    fmt.Println(products["product1"])
    fmt.Println(products["product2"])
    fmt.Println(customers["cust1"])
    fmt.Println(customers["cust2"])

}
```

保存此代码。

构建并运行此程序。

```
$ go build
$ go run main.go
```

程序输出的示例可在下图看到。

![ch3-3](Images/ch3-3.png)

# 4. 函数

本章介绍如何使用 Go 创建函数。

## 4.1 创建一个简单函数

在 Go 中声明函数的格式如下。

```
func function_name return_datatype {

    return foo
}
```

为了说明，我们可以创建一个名为 `arraydemo` 的新项目，通过创建一个名为 `arraydemo` 的文件夹。

```
$ mkdir arraydemo
$ cd arraydemo
```

创建文件 `main.go`。然后导入 Go 包。

```
package main

import (
    "fmt"
    "math"
)
```

要创建一个简单函数，你可以在 `main.go` 文件中编写此代码。

```
func main(){
    foo()

}


// a simple function
func foo() {
    fmt.Println("foo() was called")
}
```

## 4.2 带参数的函数

有时你想要创建一个带参数的函数。你可以按如下方式实现。

```
// a function with a parameter
func circle_area(r float64){
    area := math.Pi * math.Pow(r,2)
    fmt.Printf("Circle area (r=%.2f) = %.2f \n",r, area)
}
```

如果函数上有多个参数，我们可以按如下方式定义函数。

```
// a function with parameters
func calculate(a,b, c float64){
    result := a*b*c
    fmt.Printf("a=%.2f, b=%.2f, c=%.2f = %.2f \n",a, b, c, result)
}
```

## 4.3 带返回值的函数

你可能想要创建一个具有返回值的函数。参考此代码作为示例说明。

```
// a function with parameters and a return value
func advanced_calculate(a,b, c float64) float64 {
    result := a*b*c

    return result
}
```

## 4.4 带多个返回值的函数

Go 中的函数可以返回多个返回值。例如，我们在 Go 函数中返回三个值。示例代码可写成如下。

```
// a function with parameters and multiple return values
func compute(a,b, c float64, name string) (float64,float64,string) {
    result1 := a*b*c
    result2 := a + b + c
    result3 := result1 + result2
    newName := fmt.Sprintf("%s value = %.2f", name,result3)

    return result1, result2, newName
}
```

## 4.5 带多个参数和返回值的函数

你可能想要在函数上使用无限参数。在 Go 中实现它是可能的。我们可以使用 `...` 来在函数中定义多个参数。

```
// a function with zero or more parameters and a return value
func add(numbers ...int) int {
    result := 0
    for _, number := range numbers {
        result += number
    }
    return result
}
```

## 4.6 闭包函数

我们可以在函数中定义函数。它被称为闭包函数。我们可以在 Go 中按如下方式实现闭包函数。

```
// a closure function
func closure_func(name string){

    hoo := func(a,b int){
        result := a*b
        fmt.Printf("hoo() = %d \n",result)
    }
    joo := func(a,b int) int {
        return a*b + a
    }

    fmt.Printf("closure_func(%s) was called\n",name)
    hoo(2,3)
    val := joo(5,8)
    fmt.Printf("val from joo() = %d \n",val)
}
```

## 4.7 递归函数

递归函数是指一个函数，其问题的解决方案取决于同一问题的较小实例的解决方案（与迭代相反）。为了说明，我们可以使用 Go 实现斐波那契问题。

以下是 Go 中斐波那契解决方案的示例代码。

```
// a recursion function
func  fibonacci(n int) int {
    if n==0{
        return 0
    }else if n==1 {
        return 1
    }
    return (fibonacci(n-1) + fibonacci(n-2))
}
```

## 4.8 测试

我们可以重写第 4.1 到 4.7 节的代码并在主入口中使用它们。将此代码写入 `main.go` 文件。

```
package main

import (
    "fmt"
    "math"
)

func main(){
    foo()
    circle_area(2.56)
    calculate(2, 6.7, 5)

    val := advanced_calculate(2, 4.8, 7)
    fmt.Printf("advanced_calculate() = %.2f \n",val)

    val1,val2,val3 := compute(6, 2.7, 1.4, "energy")
    fmt.Printf("val1=%.2f, val2=%.2f, val3=\"%s\" \n", val1, val2, val3)

    result := add(1,2,3,4,5,6,7,8,9,10,11)
    fmt.Printf("add() = %d \n",result)

    closure_func("testing")

    ret := fibonacci(15)
    fmt.Printf("fibonacci() = %d \n",ret)
}

// a simple function
func foo() {
    fmt.Println("foo() was called")
}

// a function with a parameter
func circle_area(r float64){
    area := math.Pi * math.Pow(r,2)
    fmt.Printf("Circle area (r=%.2f) = %.2f \n",r, area)
}

// a function with parameters
func calculate(a,b, c float64){
    result := a*b*c
    fmt.Printf("a=%.2f, b=%.2f, c=%.2f = %.2f \n",a, b, c, result)
}

// a function with parameters and a return value
func advanced_calculate(a,b, c float64) float64 {
    result := a*b*c

    return result
}

// a function with parameters and multiple return values
func compute(a,b, c float64, name string) (float64,float64,string) {
    result1 := a*b*c
    result2 := a + b + c
    result3 := result1 + result2
    newName := fmt.Sprintf("%s value = %.2f", name,result3)

    return result1, result2, newName
}

// a function with zero or more parameters and a return value
func add(numbers ...int) int {
    result := 0
    for _, number := range numbers {
        result += number
    }
    return result
}

// a closure function
func closure_func(name string){

    hoo := func(a,b int){
        result := a*b
        fmt.Printf("hoo() = %d \n",result)
    }
    joo := func(a,b int) int {
        return a*b + a
    }

    fmt.Printf("closure_func(%s) was called\n",name)
    hoo(2,3)
    val := joo(5,8)
    fmt.Printf("val from joo() = %d \n",val)
}

// a recursion function
func  fibonacci(n int) int {
    if n==0{
        return 0
    }else if n==1 {
        return 1
    }
    return (fibonacci(n-1) + fibonacci(n-2))
}
```

保存此代码。

构建并运行此程序。

```
$ go build
$ go run main.go
```

程序输出的示例可在下图看到。

![ch4-1](Images/ch4-1.png)

# 5. 指针

本章我们探讨如何在 Go 中使用指针。

## 5.1 Go 中的指针

指针是一种编程语言对象，其值直接引用（或“指向”）计算机内存中其他位置存储的值，使用其地址，参考：[http://en.wikipedia.org/wiki/Pointer\_(computer\_programming)](http://en.wikipedia.org/wiki/Pointer_\(computer_programming\))。

当我们将 `x` 定义为 `int` 时，我们可以通过调用 `x = 1` 来 `x` 值。要了解 `x` 的内存地址，我们可以使用 `&x`。为了测试，我们构建一个新项目。创建一个名为 `pointers` 的文件夹。

```
$ mkdir pointers
$ cd pointers
```

创建文件 `main.go`，并编写此代码。

```
package main

import "fmt"

func main(){

    var x int

    x = 10
    fmt.Println(x)  // print a value of x
    fmt.Println(&x) // print address of x

}
```

保存此文件。

尝试构建并运行它。

```
$ go build
$ go run main.go
```

![ch5-1](Images/ch5-1.png)

你可以看到 `x` 的值为 10，其内存地址为 0xC082002238。内存地址可以使用 `&` 关键字检索。

在 Go 中，我们可以使用 `*` 定义数据类型为指针，例如 `var x *int`。我们可以使用 `*x = value` 设置指针变量。要在指针变量上设置内存地址，我们可以使用 `x = memory_address`。

为了测试，我们在 `main.go` 文件上添加以下代码。

