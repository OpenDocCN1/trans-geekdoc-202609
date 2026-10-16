
# 测试你的 Go 代码

## 介绍

本章节将涵盖：

*   为何你应该测试你的代码。

*   Go 中的测试库。

*   编写和运行测试。

*   控制如何运行你的测试。

*   生成覆盖率报告。

## 为何我们进行测试

测试你的代码可以确保它按预期工作。本章节我们专注于单元测试。

## Go 提供的内容

Go 有一个 `testing` 包，为我们提供了以下两点：

*   测试的参数。`testing` 库暴露了一个 `t *testing.T` 参数。通过将其作为函数的参数，该函数即成为测试。

    ```
    1  func TestAdd(t *testing.T) {}
    ```

*   断言结果的方法。`testing` 还暴露了 `t.Errorf()`。通过以字符串形式调用它，测试即视为失败。要通过测试，你什么都不需要做：

    ```
    1  t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
    ```

下面是一个测试函数的示例：

```
1 func TestAdd(t *testing.T) {
2   total := Add(2, 2)
3   if total != 4 {
4    t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
5  }
6  t.Log("running TestAdd")
7 }
```

*   首先，调用要测试的代码：

    ```
    1  total := Add(2, 2)
    ```

*   其次，进行断言，以查看是否成功或失败：

    ```
    1  if total != 4 {
    2    t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
    3  }
    ```

    如果结果不是预期的，则调用 `t.Errorf()` 来指出出错的地方。

## 你的第一个测试

确保你已创建了一个使用 `go mod init` 的项目，然后创建类似下面的文件结构：

```
1 main.go
2 math/
3   math.go
4   math_test.go
```

接下来要做的是创建测试文件。你希望将测试文件尽可能贴近你要测试的代码。因为你要测试 *math.go*，所以在 math/ 目录下创建 `math_test.go` 文件，如下所示：

```
1 main.go
2 math/
3   math.go
4   math_test.go
```

### 编写并运行你的第一个测试

现在你已经拥有上述文件结构，确保 *math_test.go* 文件包含以下内容：

```
 1 package math
 2 
 3 import (
 4   "testing"
 5 )
 6 
 7 func TestAdd(t *testing.T) {
 8   total := Add(2, 2)
 9   if total != 4 {
10     t.Errorf("Sum was incorrect, Actual: %d, Expected: %d", total, 4)
11   }
12   t.Log("running TestAdd")
13 }
```

运行测试时，你需要调用 `go test` 命令。以下是不同运行测试的方式：

*   `go test`，运行当前工作目录中的测试。示例输出：

    ```
    1  ok      test-example/math       0.258s
    ```

*   `go test -v`，运行详细版本。可能的输出如下：

    ```
    1  === RUN   TestAdd
    2   math_test.go:12: running TestAdd
    3 
    4  --- PASS: TestAdd (0.00s)
    5  PASS
    6  ok      test-example/math       0.422s
    ```

    在详细版本中，你可以看到测试的名称以及是否失败。

*   `go test ./..`，递归运行。如果你以此方式运行命令，它会运行子文件夹中的所有测试。

## 控制测试运行

有几种方式可以控制测试的运行数量。以下是一些方法：

- **通过模式运行测试**。你可以提供一个模式，让 Go 运行部分测试，该模式通过子串匹配或甚至在特定深度进行匹配。例如：

    ```
    1     go test -run <pattern>
    ```

- **跳过测试**。在测试中调用 `t.Skip()`，该测试将被跳过。

*   **运行单个测试**。你可以通过运行指定包和测试名称的模式来运行单个测试，例如：

    ```
    1     go test -run TestAdd
    ```
