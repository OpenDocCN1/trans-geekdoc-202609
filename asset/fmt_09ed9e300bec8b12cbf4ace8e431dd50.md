
```php
class Temperature_converter_test extends TestCase
{
    public function test_FtoC()
    {
        $obj = new Temperature_converter();
        $actual = $obj->FtoC(100);
        $expected = 37.0;
        $this->assertEquals($expected, $actual, '', 0.01);
    }
}
```

> 给 CodeIgniter 用户
> 在这种情况下，`ci-phpunit` 会自动加载 `Temperature_converter` 库，所以你不需要在 CodeIgniter 中调用 `$this->load->library()` 方法。

`$this->assertEquals()` 方法是 PHPUnit 的断言方法之一。它检查两个值是否相等。第三个参数允许我们提供错误信息，但我们将其设置为空字符串以使用默认消息。第四个参数是允许的差值 `delta`，即前两个值之间被认为是相等的差异。

## 浮点数的比较

使用 `$this->assertEquals()` 对浮点数进行比较时，应该作为第四个参数提供允许的差值。更多信息请参阅《每个计算机科学家应该知道的浮点算术》和 PHP 手册。

由于我们比较的是浮点数，我们必须设置第四个参数。在比较字符串或整数时我们不需要它，所以我们经常编写这样的代码：

```php
$this->assertEquals($expected, $actual);
```

尝试使用 `phpunit` 命令运行测试用例。

```bash
$ php phpunit.phar libraries/Temperature_converter_test.php
```

## 给 Composer 用户

`$ ./phpunit.sh libraries/Temperature_converter_test.php`

查看[如何创建 phpunit 快捷方式]。

* http://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html
* http://php.net/manual/en/language.types.float+language.types.float.comparison

## PHPUnit 基础

```bash
bash-3.2$ php phpunit.phar libraries/Temperature_converter_test.php
PHPUnit 4.8.6 by Sebastian Bergmann and contributors.
Time: 1.35 seconds, Memory: 14.50MB
There was 1 failure:
1) Temperature_converter_test::test_FtoC
Failed asserting that 37.9999999999999157829056959592651550292926875 matches
Expected 37.0.
/Users/kenji/CodeIgniter/application/tests/libraries/Temperature_converter_
test.php:10
/Users/kenji/CodeIgniter/application/tests/phpunit.phar:547
FAILURES:
Tests: 1, Assertures: 1.
Generating code coverage report in Clover XML format ... done
Generating code coverage report in HTML format ... done
bash-3.2$
```

运行 `phpunit` 命令

这次你应该能看到红色的失败了！事实上，你的第一个测试中存在一个 bug。100 华氏度不是 37.0 摄氏度，而是 37.8。

你应该检查你的代码。

## PHPUnit 基础

There was 1 failure:
1) Temperature_converter_test::test_FtoC
Failed asserting that 37.99999999999991578290569595926515502929268875 matches
Expected 37.0.
/Users/kenji/CodeIgniter/application/tests/libraries/Temperature_converter_
test.php:10
/Users/kenji/CodeIgniter/application/tests/phpunit.phar:547
FAILURES:
Tests: 1, Assertures: 1.
Generating code coverage report in Clover XML format ... done
Generating code coverage report in HTML format ... done

## 浮点数的比较

错误是因为浮点数并不总是以精确度表示的。在这种情况下，值 37.9999999999999157829056959592651550292926875 不等于 37.0。

为了修复这个问题，我们使用差值 `delta`。 0.01 的差值。

```php
$this->assertEquals($expected, $actual, '', 0.01);
```

## PHPUnit 基础

## Data Provider

我们在一个方法中有两个测试，但你应该继续添加测试。编程中有一句格言是“不要重复”`DRY`。以这种方式继续添加测试看起来有点麻烦。

## PHPUnit 基础

幸运的是，PHPUnit 包含了重复此类测试的功能。一种方法是使用数据提供者 `Data Provider`。通过这种方法，我们可以编写如下的测试：

# PHPUnit 基础

`test_FtoC()` 方法有两个参数 `($degree` 和 `$expected)`。数据提供者方法中的值会被传递给它们。第一个数组 `[-40, -40.0]` 被传递给方法，赋值为 `$degree = -40` 且 `$expected = -40.0`。

PHPUnit 会为数据提供者方法中的每个数组重复测试。

```php
$ phpunit.phar libraries/Temperature_converter_test.php
PHPUnit 4.8.10 by Sebastian Bergmann and contributors.
```
...
nTime: 1.15 seconds, Memory: 12.50Mb
OK (5 tests, 5 assertions)

在输出中，你应该看到五个点、5 个测试和5 个断言。如果你添加 `--debug` 选项，可以更清晰地看到发生了什么。

```php
$ phpunit.phar --debug libraries/Temperature_converter_test.php
PHPUnit 4.8.10 by Sebastian Bergmann and contributors.
```
Starting test 'Temperature_converter_test::test_FtoC with data set #0 (-40, -40.0)'.
Starting test 'Temperature_converter_test::test_FtoC with data set #1 (0, -17.80000000000007105427357601001858711242675781225)'.
Starting test 'Temperature_converter_test::test_FtoC with data set #2 (32, 0.0)'.
Starting test 'Temperature_converter_test::test_FtoC with data set #3 (100, 37.799999999999971578209560959952952651555029296875)'.
Starting test 'Temperature_converter_test::test_FtoC with data set #4 (212, 100.0)'.
Time: 1.46 seconds, Memory: 12.50Mb
OK (5 tests, 5 assertions)

## 测试技巧：来自另一个类的数据提供者

你可以通过在标签中指定类来使用另一个类的数据提供者：`@dataProvider Bar::provide_baz_data`。如果该类已定义 `或可加载` 且提供者方法存在，PHPUnit 将使用它。

## 不完全的测试

我们为 `FtoC()` 方法编写了测试代码，但类中还有另一个方法 `CtoF()`。因此，我们需要测试这个方法。

当我们需要写一个测试方法但尚未完成时，可以使用 PHPUnit 的 `$this->markTestIncomplete()` 方法。这是一个标记，用于指示测试尚未完成或目前尚未实现。

将以下方法添加到测试类的末尾：

`application/tests/libraries/Temperature_converter_test.php`

```php
public function test_CtoF() {
    $this->markTestIncomplete(
        'This test has not been implemented yet.'
    );
}
```

不完全的测试在 `phpunit.php` 的输出中用 `I` 表示，如果你的终端支持颜色，OK 行将呈现黄色而不是绿色。

```bash
$ php phpunit.phar libraries/Temperature_converter_test.php --no-coverage
PHPUnit 4.8.10 by Sebastian Bergmann and contributors.
```
```
...I
Time: 817 ms, Memory: 7.50Mb
```
OK, but incomplete, skipped, or risky tests!
Tests: 6, Assertions: 5, Incomplete: 1.

如果你放了一个既没有断言也没有使用 `$this->markTestIncomplete()` 的测试方法，你会看到绿色的 OK，且无法判断测试是实际上成功了还是尚未实现。

## 添加测试

为 `CtoF()` 方法添加测试代码很容易，因为 `CtoF()` 仅仅是 `FtoC()` 的反向。我们可以复用 `test_FtoC()` 方法的数据提供者。

## 练习

请在此停止并思考你将如何编写该测试方法。

更新 `test_FtoC()` 方法：

```php
application/tests/libraries/temperature_converter_test.php
/**
 * @dataProvider provide_temperature_data
 */
public function test_FtoC($expected, $degree) {
    $obj = new Temperature_converter();
    $actual = $obj->FtoC($degree);
    $this->assertEquals($expected, $actual, '', 0.01);
}
```

`test_FtoC()` 参数的顺序反过了。
这个测试类是可以的，但我们仍然可以通过 PHPUnit 的 `setUp()` 方法对其进行一些改进。

## 固定件 Fixtures

固定件是应用程序的一种状态。如果你运行测试，必须在运行测试之前将世界设置为已知状态，因为状态的任何差异可能会改变测试结果。
PHPUnit 有定义固定件的方法。在这个用例中，我们不需要做任何事情，因为目标类除了 PHP 内部函数 `round()` 之外没有依赖。`round()` 也没有依赖，它返回一个计算值。
然而，我们仍然可以通过设置环境来改进测试代码。

## setUp()

`setUp()` 是在每个测试方法之前调调的方法。换句话说，如果你使用它，可以在多个测试之间共享设置过程。

# PHPUnit 基础

```diff
--- a/application/tests/libraries/Temperature_converter_test.php
+++ b/application/tests/libraries/Temperature_converter_test.php
@@ -2,13 +2,17 @@
 class Temperature_converter_test extends TestCase
+{
+    public function setUp()
+    {
+      $obj = new Temperature_converter();
+    }
+
+/**
+ * @dataProvider provide_temperature_data
+ */
 public function test_FtoC($expected, $degree)
 {
-    $obj = new Temperature_converter();
     $actual = $obj->FtoC($degree);
     $this->assertEquals($expected, $actual, '', 0.01);
 }
@@ -29,8 +33,7 @@ class Temperature_converter_test extends TestCase
 {
-    $obj = new Temperature_converter();
-    $actual = $obj->FtoC($degree);
+    $this->assertEquals($expected, $actual, '', 0.01);
 }
```

上面的列表是统一 diff。它显示了两个文件之间的差异。

## 断言 Assertions

PHPUnit 有许多断言方法。以下是常用的断言列表：

- `assertEquals($expected, $actual)` 检查两个值是否相等
- `assertSame($expected, $actual)` 检查两个值是否且类型相同
- `assertTrue($condition)` 检查条件是否为真
- `assertFalse($condition)` 检查条件是否为假
- `assertNull($variable)` 检查变量是否为空
- `assertInstanceOf($expected, $actual)` 检查对象的类型
- `assertCount($expected, $haystack)` 检查 `$haystack` 中的元素数量是否匹配 `$expected`
- `assertRegExp($pattern, $string)` 检查 `$string` 是否匹配正则表达式
- `assertContains($needle, $haystack)` 检查 `$needle` 是否在 `$haystack` 中，此方法适用于字符串 `($needle` 是 haystack 的子字符串）、数组 `($needle` 是 haystack 的元素）或实现了 Iterator 的类 `可以使用 foreach() 调用`

你可以在 PHPUnit 手书中查看所有断言方法。

> 测试技巧：使用特定的断言方法
使用特定的断言方法是一种实践，因为它表达了你想测试的内容，并且你可以获得更有用的错误信息。

# 5. 测试一个简单的 MVC 应用

为了开始学习如何编写测试，我们将从一个简单但重要的 MVC 应用开始，这是 CodeIgniter 教程中包含的一个应用程序。

该应用程序根据 MIT 许可证许可。参见 [CodeIgniter 用户指南](https://www.codeigniter.com/userguide/3/index.html)

我稍微修改了应用程序的代码风格，并添加了以 `#` 开头的注释。

## 5.1 控制器的功能测试

由于 CodeIgniter 将模型视为可选，我们将从测试我们的控制器开始。

### 处理静态页面的控制器

你将看到的第一个是处理静态页面的控制器。

### Pages 控制器

`application/controllers/Pages.php`

```php
<?php
class Pages extends CI_Controller
{
    public function view($page = 'home')
    {
        if (file_exists(APPATH.'/views/$page.php')) {
            // 哎，我们没有那个页面！
            show_404();
        }
        $data['title'] = ucfirst($page); // 首字母大写
```

# 测试一个简单的 MVC 应用

```php
$this->load->view('templates/header', $data);
$this->load->view('pages/' . $data['page'], $data);
$this->load->view('templates/footer', $data);
```
