
*   `TrimRight()`。它只删除右侧的空白字符，同样可以指定特殊字符。

使用正则表达式来解析文本

在本章中，你将学习如何使用正则表达式（RegEx）来搜索和替换文本。

## 什么是 RegEx 以及用途

正则表达式（RegEx）也称为正则，用于查找和替换文本。技术上，RegEx 是一系列字符，表示搜索模式。

## 为什么使用 RegEx

RegEx 的主要用途是查找文本、替换文本以及提取文本。虽然存在一些字符串库可以实现部分 RegEx 功能，但在某些情况下，使用 RegEx 可能更为合适。不过，RegEx 很难掌握，建议多学习其工作原理，因为它功能强大。

## 使用场景

RegEx 在许多不同的场景中被使用：

*   **文本编辑器、任何带有搜索功能的程序**。例如，Visual Studio Code 允许你在文件和文件夹中使用 RegEx 进行搜索。
*   **代码**，许多编程语言和运行时环境都提供 RegEx 库以帮助你使用正则表达式。

## 你的第一个 RegEx

让我们构建一个简单的 RegEx 来感受它的用法。以下是示例：

```
1 an
```

如果将搜索模式 `an` 应用于以下文本：

```
1 highlands is a part of Scotland
```

它会匹配如下：

> highl**an**ds is a part of Scotl**an**d

对于简单的情况，即查找特定单词在句子中的一或多个位置，像上面的模式足够。

### RegEx 在 Go

在 Go 中使用 RegEx 的第一步是使用 `regexp` 包。有两种方法：

*   直接使用 `regexp`，示例如下：

    ```
    1  matched, err := regexp.FindString("an", "highlands is a part of Scotland")
    ```

    这里会返回一个布尔值，表示是否存在匹配。

*   **编译**，即先编译正则表达式，然后调用其方法，例如：

    ```
    1  r, _ := regexp.Compile("an")
    2  matches := r.FindAllString("highlands is a part of Scotland", -1)
    ```

    上述代码会返回一个字符串数组，包含所有匹配项，这里是 `["an", "an"]`。

    使用编译方式，你可以调用更多函数。

## 字符类

字符类能够区分不同类型的字符，例如换行符、数字、字母等。

以下是一些常见字符类及其描述：

| 类型 | 描述 |
| --- | --- |
| `.` | 匹配除换行符外的任意字符 |
| `\` | 转义后面的字符 |
| `\w` | 匹配拉丁字母表中的字符，包括下划线 `_` |
| `\d` | 匹配任何数字 |
| `D` | 与 `\d` 相反，匹配非数字字符 |
| `\s` | 匹配空白字符，如空格、制表符、换行符等 |

示例：

```
1 matched, err := regexp.FindString("\d", "abc123")
```

上述代码会因 `"123"` 而匹配成功，但对 `"abc"` 不会匹配，因为其中没有数字。

## 重复

如果想表达重复，有两个特殊字符：

*   `+`，匹配 1 到多个字符。

    ```
    1  \w+
    ```

    给定字符串 `"aaaa bab"`，它会匹配：

    **aaaaab** **bab**（匹配字符，不包括空格）

    ```
    1  r, _ := regexp.Compile("\\w+")
    2  matches := r.FindAllString("aaaa bab", -1)
    ```

    注意需要额外的 `\`，因为在构建正则表达式时需要转义。

*   `*`，匹配 0 到多个字符。例如，要匹配以 `"PA"` 开头，后面可包含 0 或多个数字的邮政地址，可以使用 `*` 如下：

```
1 package main

2

3 import (

4  "fmt"

5  "log"

6  "regexp"

7 )

8

9 func main() {

10  var url string

11  fmt.Println("Type URL: ")

12  fmt.Scan(&url)

13

14  r, err := regexp.Compile(`^(?P<protocol>\w+):\/\/(?P<domain>\w+\.\w+)\/(?P<route>\w+

15 +)\/?`)

16  if err != nil {

17   log.Fatal("Error compiling: ", err)

18  }

19  m := r.FindStringSubmatch(url)

20  if m == nil {

21   panic("mo match")

22  }

23  result := make(map[string]string)

24  for i, name := range r.SubexpNames() {

25   if i != 0 && name != "" {

26    result[name] = m[i]

27   }

28  }

29  fmt.Println("The URL consist of:")

30  fmt.Println(result["protocol"])

31  fmt.Println(result["domain"])

32  fmt.Println(result["route"])

33 }

```

4

-   [将 `books.xml` 文件中的 `author` 替换为 `name`](https://wiki.example.org/books_xml_author_replace) 和 [将 `cost` 替换为 `price`](https://wiki.example.org/books_xml_cost_replace)。

TIP: 你可能需要执行两次替换。

```
1 package main
2
3 import (
4  "fmt"
5  "regexp"
6 )
7
8 func main() {
9  file := `<books>
10     <book>
11       <author>Shakespeare</author>
12       <title>Romeo and Juliet</title>
13       <pages>400</pages>
14       <type>paperback</type>
15       <cost>17</cost>
16     </book>
17     <book>
18       <author>Shakespeare</author>
19       <title>Hamlet</title>
20       <pages>270</pages>
21       <type>paperback</type>
22       <cost>15</cost>
23     </book>
24 </books>`
25
26  r := regexp.MustCompile(`(\<\/?)(title)(\>)`)
27  s := r.ReplaceAllString(file, "${1}name${3}")
28  fmt.Println(s)
29
30  r = regexp.MustCompile(`(\<\/?)(cost)(\>)`)
31  s = r.ReplaceAllString(s, "${1}price${3}")
32  fmt.Println(s)
33 }
```

## Goroutines and channels

A goroutine is a lightweight thread managed by the Go runtime.

Channels is how you communicate between routines.

## Introduction

In this chapter you will:

*   Understand the difference between concurrency and parallelism
*   Use Goroutines to run your functions
*   Create and use channels to communicate between your Goroutines
*   Apply Goroutines to an app that searches files for faster execution.

## Concurrency, what’s the benefit

Concurrency is the task of running and managing the multiple computations at the same time. While *parallelism* is the task of running multiple computations simultaneously.

So what are some benefits:

*   **Faster processing**. The benefit is getting tasks done faster. Imagine that you are searching a computer for files, or processing data, if it’s possible to work on these workloads in parallel, you end up getting the response back faster.
*   **Responsive apps** Another benefit is getting more responsive apps. If you have an app with a UI, imagine it would be great if you can perform some background work without interrupting the responsiveness of the UI.

## Goroutines

A goroutine is a lightweight thread managed by the Go runtime. What you do is to add the keyword `go` in front of a function. Here’s an example:

```
1 go myFunction()
```

Imagine the following code running, what would happen?

```
1 package main
2
3 import "fmt"
4
5 func myFunction() {
6  for i := 0; i < 3; i++ {
7   fmt.Println("my function: ", i)
8  }
9 }
10 func anotherFunction() {
11  for i := 4; i <7; i++ {
12   fmt.Println("another function: ", i)
13  }
14 }
15
16 func main() {
17  go myFunction()
18  anotherFunction()
19 }
```

It would only print the result from `anotherFunction()` as it takes a short while for the go routine to start up. You can have the go routine execute as well by adding a little delay, like so:

```
1 func main() {
2  go myFunction()
3  anotherFunction()
4  time.Sleep(1 * time.Second)
5 }
```

The result is now the following:

```
1 another function:  4
2 another function:  5
3 another function:  6
4 my function:  0
5 my function:  1
6 my function:  2
```

The function with the go routine finishes last. Lets modify the code slightly and have the two functions use a delay, so we simulate workloads taking different time to finish:

```
1 func myFunction() {
2  time.Sleep(1500 * time.Millisecond)
3  for i := 0; i < 3; i++ {
4   fmt.Println("my function: ", i)
5  }
6 }
7 func anotherFunction() {
8  time.Sleep(500 * time.Millisecond)
9  for i := 4; i < 7; i++ {
10   fmt.Println("another function: ", i)
11  }
12 }
13
14 func main() {
15  go myFunction()
16  go anotherFunction()
17  time.Sleep(2 * time.Second)
18 }
```

at this point, `anotherFunction()` finishes first as it has the shortest delay, which is to be expected. Here’s what the output looks like now:

```
1 another function:  4
2 another function:  5
3 another function:  6
4 my function:  0
5 my function:  1
6 my function:  2
```

### Use case - a file search

Imagine you have case where you need to find a file on disk. If you write a function like so, it will search a directory and report back the result if the file is found:

```
1 func SearchFiles(dir string, lookFor string) string {
2  log.Println("[SEARCHING] ", dir)
3  files, err := ioutil.ReadDir(dir)
4  if err != nil {
5   log.Fatal(err)
6  }
7
8  for _, file := range files {
9   log.Println(dir+file.Name(), file.IsDir())
10   if file.Name() == lookFor {
11    return "[FOUND] " + filepath.Join(dir, file.Name())
12   }
13  }
14  return "[NOT FOUND] " + dir
15 }
```

Imagine you now run this code like so, to search many directories:

```
1 result := make([]string, 0)
2 append(result, SearchFile("./tmp", "myfile.txt"))
3 append(result, SearchFile("./tmp2", "myfile.txt"))
4 append(result, SearchFile("./tmp3", "myfile.txt"))
5 append(result, SearchFile("./tmp4", "myfile.txt"))
6
7 for i := 0 i< len(result); i++ {
8   fmt.Println(result[i])
9 }
```

If found, you will get an output similar to the below, depending on whether `myfile.txt` is found in any of the searched directories:

```
1 [FOUND] ./tmp/myfile.txt
2 [NOT FOUND] ./tmp2/myfile.txt
3 [NOT FOUND] ./tmp3/myfile.txt
4 [NOT FOUND] ./tmp4/myfile.txt
```

Now to speed up this process, it would be great if you are able to search many directories at once, so you could type something like so:
