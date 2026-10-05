
# 模型的单元测试

```
>>> $mock->FtoC(100)
=> 99.9
>>> $mock->FtoC(50)
=> 99.9
>>> $mock->FtoC(0)
=> 99.9
```

所有的返回值都是 99.9，因为这是我们告诉 mock 返回的唯一值。

```php
$mock = $this->getMockBuilder('Temperature_converter')
    ->getMock();
$mock->method('FtoC')->willReturn(99.9);
```

这段代码的最后一行显示 mock 有一个名为 FtoC 的方法，它将返回值 99.9。

运行另一个方法会怎样？

```
>>> $mock->CtoF(0)
=> null
```

我们在创建 mock 时没有指定的方法将返回 `null`。这是 PHPUnit 在我们显式定义方法时提供的默认行为。

![](img/ce0568211401542acf89e27068fbf651_92_0.png)

Psy Shell

同时按下 [control] 键和 [c] 键来终止 PHPUnit 进程。

# 模型的单元测试

# 部分 Mock (Partial Mocks)

接下来，定义 mock 的另一种方法如何？我们在定义这个 mock 时只需添加 `setMethods(['FtoC'])` 即可。

```diff
--- a/CodeIgniter/application/tests/models/Play_with_mocks_test.php
+++ b/CodeIgniter/application/tests/models/Play_with_mocks_test.php
@@ -8,6 +8,11 @@ class Play_with_mocks_test extends TestCase
-- ->getMock();
-$ $method('FtoC')->willReturn(99.9);
+
+$mock2 = $this->getMockBuilder('Temperature_converter')
+    ->setMethods(['FtoC'])
+    ->getMock();
+$mock2->method('FtoC')->willReturn(99.9);
+
+eval(\PhpShell($mock));
+var_dump($mock, $mock->FtoC(100), $mock->CtoF(0)); execute;
```

上面的列表是统一 diff 格式。它显示了两个文件之间的差异。简单来说，添加以 `+` 开头的绿色行即可获取新文件。详情请参见“此中使用的约定”。

运行 phpunit 命令并检查结果。

```
$ php phpunit.phar models/Play_with_mocks_test.php
#/usr/bin/env php
PHPUnit 4.8.10 by Sebastian Bergmann and contributors.
```

```
Psy Shell v0.6.0-dev (PHP 5.5.26 - cli) by Justin Hileman
$mock2->FtoC(100)
=> 99.9
$mock2->FtoC(50)
=> 99.9
$mock2->FtoC(0)
=> 99.9
$mock2->CtoF(0)
=> 32.0
$mock2->CtoF(50)
=> 122.0
```

# 为 CtoF 进行单元测试

```
$mock2->CtoF(100)
=> 212.0
```

这一次，我们在创建 mock 时没有指定的方法返回了真实值，而不是 `null`。这样的 mock 被称为**部分 Mock (Partial Mocks)**。当我们使用 `setMethods()` 时，我们告诉 PHPUnit 模拟数组中包含的方法，但其他方法将调用原始类，并且无法通过你的 $mock2 对象进行配置。

# 验证期望 (Verifying Expectations)

我们在上面定义并了 mock 的输出。我们也可以检查 mock 的输入。在下面的代码中，mock 期望 FtoC() 方法被调用一次并向参数传递值 0。

application/tests/models/Play_with_mocks_test.php

```php
public function test_mock_expectations() {
    $mock = $this->getMockBuilder('Temperature-converter')
        ->getMock();
    $mock->expects($this->once())
        ->method('FtoC')
        ->with(0);
    $mock->FtoC(0);
}
```

测试方法中没有断言，但这是一个真实的测试。如果你更改或删除了 `$mock->FtoC(0);`，测试将失败。
除了 `$this->once()` 之外，PHPUnit 使用其他方法来验证调用次数：

- `$this->any()` ... 任意次数，包括 0
- `$this->once()` ... 仅一次
- `$this->exactly($count)` ... 恰好 $count 次
- `$this->at($index)` ... 参见下文示例
- `$this->never()` ... 永远不被调用
- `$this->atLeastOnce()` ... 至少一次

以下是一个使用 `$this->at()` 方法通过测试的示例。

# 模型的单元测试

application/tests/models/Play_with_mocks_test.php

```php
public function test_mock_at_method()
{
    $mock = $this->getMockBuilder('Temperature-converter')
        ->getMock();
    $mock->expects($this->at(0))
        ->method('FtoC')
        ->with(0);
    $mock->expects($this->at(1))
        ->method('CtoF')
        ->with(100);

    $mock->FtoC(0);
    $mock->CtoF(100);
}
```

`$this->at()` 方法的参数指的是给定 mock 对象所有方法调用的从零开始的索引。因此，`$mock->expects($this->at(0))->method('FtoC')->with(0);` 配置 mock 期望第一次方法调用为 FtoC(0)，而 `$mock->expects($this->at(1))->method('CtoF')->with(100);` 配置 mock 期望第二次方法调用为 CtoF(100)。如果我们更改了传递给 `at()` 的索引，或者更改了 FtoC() 和 CtoF() 方法被调用的顺序，测试将会失败。

# 6.3 测试不带数据库的模型

在上一章中，我们为一个使用数据库的模型编写了测试代码（参见第 5 章，新闻模型案例）。在功能测试中，我们需要数据库。

# 测试不带数据库的模型

（注：原文后续部分存在大量重复的 OCR 错误文本，已根据要求按核心逻辑进行处理。）
