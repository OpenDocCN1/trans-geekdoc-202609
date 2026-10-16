
# 使用变量

使用变量，我们可以记住值，并通过命名引用来访问它们。使用变量会让我们的代码更易于阅读。

## 介绍

在本课中我们将学习：

*   Go 中变量的用法。

*   如何创建它们。

*   赋予不同类型和值。

## 声明变量

在 Go 中，声明变量有很多方法：

*   **定义名称和类型**。这里，你使用关键字 `var`，给变量命名，最后指定类型 `string`。下面是一个示例：

    ```
    1 var firstName string
    ```

*   **定义变量组**。你可以定义一组变量。使用这种声明方式，你只需要在 `var` 关键字后面使用一次。变量组使用括号 `()` 来定义：

    ```
    1 var (
    2   firstName = "Chris"
    3   age = 20
    4 )
    ```

    注意，每个变量都在新的一行上。

*   **定义并赋值**。在函数内部，你可以使用 `:=` 运算符，它同时声明并赋值。下面的代码展示了 `firstName` 变量的创建。数据类型会被自动推断为字符串：

    ```
    1 firstName := "Chris"
    ```

## 赋值变量

要向变量赋予新值，它首先必须存在。你使用赋值运算符 `=`。下面是一个示例：

```
1 firstName = "Mike"
```

## 数据类型

Go 中可以使用的数据类型很多，它们被分为不同的类别：

*   **基本类型**。在这一类中，我们可以看到整数、浮点数（带小数的数字）以及其他类型，如布尔值（用于 true/false）、字符串（用于文本）等。

*   **复合类型**。我们将在单独的文章中讨论复合类型，但它们更为复杂，例如数组、结构体和接口。

### 使用类型声明变量

你可以以两种方式声明变量并指定其类型：

*   **显式**，通过指定类型，例如：

    ```
    1 var name string
    ```

*   **隐式**，通过赋值并让类型被推断：

    ```
    1 name := "chris"
    ```

    在前面的代码中，数据类型是根据你给出的值推断出来的。这里，值 “chris” 使类型变为 `string`。

## 字符串插值

有时，你想在屏幕上写入内容，并混合不同的数据类型。例如，你可能想写：“客户：Adam，银行账户余额 20$”。

假设下面的变量代表了这些信息：

```
1 var (
2   customerName = "Adam"
3   accountBalance = 20
4 )
```

那么，如何打印出上面的文本呢？为此，你可以使用 `Printf()` 函数，它接受格式化符。格式化符是指示某种类型的指令。通过将这些信息提供给 `Printf()`，它就能正确打印出相应的类型。

下面是如何打印之前的示例字符串的方法：

```
1 fmt.Printf("Customer %s has %d$ on their bank account", customerName, accountBalance)
```

上面，`%s` 表示字符串，`%d` 表示数字。通过使用这些格式化符作为占位符，变量会被正确实现，输出结果为：

```
1 Customer Adam has 20$ on their bank account
```

## 练习 - 定义一些变量并打印它们

为德州扑克（Texas Holdem）纸牌游戏定义一些变量，并打印它们。

创建一个名为 *main.go* 的文件，并将其内容设置为：

```
1 package main
2 
3 import "fmt"
4 
5 func main () {
6  }
```

1. 在 import 部分之后，添加以下变量：

    ```
    1 var (
    2   players = 3
    3   replay = false
    4   namePlayerOne = "chris" 
    5 )
    ```

    现在你有：

    *   `players`，表示游戏中的玩家数量。

    *   `replay`，布尔值，表示在旧游戏结束后是否开始新的一局。

    *   `namePlayerOne`，字符串，表示第一位玩家的名字。

    这些变量都能帮助描述德州扑克游戏中的关键信息。

    接下来，让我们运行程序以确保它能正常工作。

2. 在 `main()` 函数中添加以下代码来打印这些变量：

    ```
    1 fmt.Println(players)
    2 fmt.Println(replay)
    3 fmt.Println(namePlayerOne)
    ```

3. 在终端运行 `go run main.go`：

    ```
    1 go run main.go
    ```

    你应该会看到以下输出：

    ```
    1  3
    2  false
    3  chris
    ```

    太好了，你现在有一个可以继续构建的应用的起点。

## 🚀 挑战

看看你能否想出更多变量来表示德州扑克卡牌游戏的状态，例如其他玩家、卡牌牌组等。你会为这些变量赋予什么数据类型？

## 复习与自学

查看 [官方变量教程](https://go.dev/tour/basics/8)，使用 Go 沙箱。

## 解答

```
 1 package main
 2 
 <unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1.  var
 2   firstName = "Chris"
 3 
 4 
 5 
3.  Add the following code to the main() function to print out the variables: 
4    
5     fmt.Println(players)
6   fmt.Println(replay)
16   fmt.Println(namePlayerOne)
16 
16 
16 
