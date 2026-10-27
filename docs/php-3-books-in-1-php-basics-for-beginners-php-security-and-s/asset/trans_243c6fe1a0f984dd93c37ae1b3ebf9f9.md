
开始之前，您必须删除 C:\Users\YOUR_USER_NAME\AppData\Local\Temp\ 中的所有内容。

- 1. 启动一个命令提示符选项卡。并以管理员身份运行。

- 2. 独立执行以下命令（一次一个，仅执行一次）：

```text
pear channel-discover pear.PHPUnit.de
pear channel-discover components.ez.no
pear channel-discover pear.symfony-project.com
pear clear-cache
```

- 3. 现在运行：

```text
pear install PHPUnit/PHPUnit
```

## 在 XAMPP 环境下在 Windows 上安装 PHPUnit

您必须在执行上述步骤之前将 Xampp 安装到 C:\xampp。

- 1. 启动 cmd.exe，然后导航到 C: 文件夹，现在打开 Xampp 文件夹，您会找到一个名为 PHP 的文件夹。打开它。

- 2. 独立执行以下命令（一次一个，仅执行一次）：

```text
pear update-channels
pear upgrade
pear channel-discover components.ez.no
pear channel-discover pear.symfony-project.com
pear channel-discover pear.PHPUnit.de
pear clear-cache
pear install --alldeps PHPUnit/PHPUnit
```

记住：每当您遇到内存问题时，您必须更改 PHP.ini 中的“memory limit”设置；只需将其更改为非常巨大的值，然后在完成后将其改回。

## 在 Macbook 上安装 PHPUnit

假设您已在上一章中按照 Mac OS 的 PEAR 安装程序进行操作，则在 Macbook 上安装 PHPUnit，只需在提示符中执行以下命令：

```text
$ sudo pear channel-discover pear.PHPUnit.de
```

之后，在提示符中执行此行：

```text
$ sudo pear install PHPUnit/PHPUnit
```

完成。 我们已安装 PHPUnit，您可以通过打开用户文件夹然后打开 local 来导航它，您会在其中找到 PEAR 文件夹。 在其中您会看到 PHPUnit。 现在您可以添加

```
public function Unit_Test_TestEqual() {
if ( ($this->m_x == $m_y) && ($this->m_x!= NULL) && ($this->m_y!= NULL) ) {
echo "$m_x is equal to $m_y";
}
}

public function Unit_Test_TestIdentical() {
if ( ($this->m_x === $m_y) && ($this->m_x!= NULL) && ($this->m_y!= NULL) ) {
echo "$m_x is identical to $m_y";
}
}

public function Unit_Test_TearDown() {
$this->m_x = "";
$this->m_y = "";
}
}
?>
```

Unit_Test_Setup() 和 Unit_Test_TearDown() 方法用于初始化和清理测试夹具。

## 断言方法

断言是用于测试您对某个系统功能假设的工具。 断言通常用于表示关于被测试代码语句或段落结果的测试。 如果测试结果与预期结果不同，则测试失败，并显示警告消息。 断言方法对于记录被测系统的预期行为也很有用。 让我们用断言方法替换上面的示例测试用例：

```php
<?PHP
class Unit_Test extends PHPUnit_Framework_TestCase {

private $m_x;
private $m_y;

public function Unit_Test_Setup()
{
$this->m_x = 2;
$this->m_y = '2';
}

public function Unit_Test_TestEqual() {
$this->assertTrue($this->m_x == $this->m_y);
}

public function Unit_Test_TestIdentical() {
$this->assertTrue($this->m_x === $this->m_y);
}
public function Unit_Test_TearDown() {
$m_x = "";
$m_y = "";
}
}
?>
```

所有断言方法都允许一个可选的描述作为最后一个参数。 这将用于标记显示的结果。 当省略此参数时，会发送默认消息代替，通常已足够。 如果您在字符串中放入“% s”，您仍可在自己的消息中包含此默认消息。 如果断言成功，它返回 true；否则返回 false。

让我们使用 assertEqual() 和 assertSame() 方法再次测试这些条件：

```php
<?PHP
class Unit_Test extends PHPUnit_Framework_TestCase {
private $m_x;
private $m_y;

public function Unit_Test_Setup()
{
$this->m_x = 2;
$this->m_y = '0';
}

public function Unit_Test_TestEqual() {
$this->assertEquals($this->m_x, $this->m_y, 'Failed!');
}

public function Unit_Test_TestIdentical() {
$this->assertSame($this->m_x, $this->m_y, 'Failed!');
}
public function Unit_Test_TearDown() {
$m_x = "";
$m_y = "";
}
}
?>
```

现在让我们将 $m_x 和 $m_y 设置为彼此相等但类型不同，并测试它们是否不相同：

```php
<?PHP
class Unit_Test extends PHPUnit_Framework_TestCase {
private $m_x;
private $m_y;

public function Unit_Test_Setup()
{
$this->m_x = 2;
$this->m_y = '2';
}

public function Unit_Test_TestEqual() {
$this->assertTrue($this->m_x == $this->m_y);
}

public function Unit_Test_testIdentical() {
$this->assertTrue($this->m_x === $this->m_y);
}

public function Unit_Test_TearDown() {
$m_x = "";
$m_y = "";
}
}
```

现在让我们最后再运行一次，将 $m_x = 2 和 $m_y = 2 设置为相等且类型相同：

```php
<?PHP
//test_assertion.PHP

class Unit_Test extends PHPUnit_Framework_TestCase {

private $m_x;
private $m_y;
public function Unit_Test_Setup()
{
$this->m_x = 5;
$this->m_y = 5;
}

public function Unit_Test_TestEqual() {
$this->assertTrue($this->m_x == $this->m_y);
}

public function Unit_Test_TestIdentical() {
$this->assertTrue($this->m_x === $this->m_y);
}

public function Unit_Test_Teardown() {
$m_x = "";
$m_y = "";
}
}
?>
```

## 以下是内置 PHPUnit 断言方法列表：

- `assertArrayHasKey()`
- `assertClassHasAttribute()`
- `assertClassHasStaticAttribute()`
- `assertContains()`
- `assertContainsOnly()`
- `assertContainsOnlyInstancesOf()`
- `assertCount()`
- `assertEmpty()`
- `assertEqualXMLStructure()`
- `assertEquals()`
- `assertFalse()`
- `assertFileEquals`
- `assertFileExists()`
- `assertGreaterThan()`

- `assertGreaterThanOrEqual()`
- `assertInstanceOf()`
- `assertInternalType()`
- `assertJsonFileEqualsJsonFile()`
- `assertJsonStringEqualsJsonFile()`
- `assertJsonStringEqualsJsonString()`
- `assertLessThan()`
- `assertLessThanOrEqual()`
- `assertNull()`
- `assertObjectHasAttribute()`
- `assertRegExp()`
- `assertStringMatchesFormat()`
- `assertStringMatchesFormatFile()`
- `assertSame()`
- `assertSelectCount()`
- `assertSelectEquals()`

| 方法 |
|---|
| assertSelectRegExp() |
| assertStringEndsWith() |
| assertStringEqualsFile() |
| assertStringStartsWith() |
| assertTag() |
| assertThat() |
| assertTrue() |
| assertXmlFileEqualsXmlFile() |
| assertXmlStringEqualsXmlString |

表 11-1. PHPUnit 断言方法

## 测试来自 HTML 表单提交的数据

我们使用了预定义的 $_POST 变量，它是一个从表单收集值的数组，来在我们的餐厅 carte 应用程序中创建表单以将 carte 产品数据加载到数据库中。

在 PHP 中开发时，您需要与表单交互。 因此，您需要测试表单提交，特别是用于从 $_GET 和 $_POST 数组发送数据的 GET 和 POST 方法。 考虑依赖注入的概念。 让代码获得所需的东西比期望它自行找到要好。 以下是区分两者的示例：

无依赖注入示例：

```php
function Add_Carte_Product1() {
foreach($_POST as $form_element => $v) {
// code to process $v
}
}

Add_Carte_Product_1();
```

有依赖注入示例：

```php
function Add_Carte_Product2(array &$formData) {
foreach($formData as $form_element => $v) {
// code to process $v
}
}

Add_Carte_Product2($_POST);
```

你明白我的意思吗？ 在您的 PHPUnit 测试中，您可以将您选择的关联数组传递给 AddCarteProduct2()；依赖项已被注入。 $_POST 与 addCarteProduct1() 一起使用。 因为 $_GET 和 $_POST 是关联数组，您可以在生产代码中使用它们，但在单元测试中必须硬编码某些预期值。

单元测试示例：

```php
function Test_Add_Carte_Product() {
$formData = array ('carteProductname'=>'Coffee', 'carteProductdescription'=>'black coffee',
'carteProductprice'=>'$2.55');
Test_Add_Carte_Product($formData);
// assert something...
}
```

## 测试套件

test-suite 是使用完全相同夹具的一组实验。 执行测试的顺序不应重要。 我们实际上在 test assertion.PHP 示例中运行了两个简单的测试，它们使用了相同的 setup() 夹具为 $x 和 $y 分配值。 一个基本的测试套件看起来像这样。

## 模拟和存根

用返回指定值的 testdouble 替换对象称为存根。

模拟是通过用测试双重对象替换对象来验证行为的过程。 模拟对象在单元测试中用于模拟测试用例中真实对象的行为。 当您使用它们时，很容易测试您正在构建的对象的功能。 模拟对象在以下情况下很有用：一个或多个对象的依赖项的真正实现仍在进行中，或者一个或多个对象的依赖项依赖于难以复制的方面。 这两种情况都通过测试应用程序与数据库之间的交互来说明。 通常，您会使用函数或其他数据访问对象，但如果数据库尚未创建怎么办？

如果没有可用数据，或者如果数据库查询代码尚未编写怎么办？ 模拟数据访问对象通过返回一些预定义值来模拟真实的数据访问对象。 这为您节省了设置数据库、加载测试数据以及编写查询数据库的代码的时间和精力。 模拟有助于验证请求，例如 SQL，是否由访问连接的对象在想象的上下文中适当创建
