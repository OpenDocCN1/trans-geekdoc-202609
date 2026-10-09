

出于测试目的，我们将使用潜在客户表作为目标。不再从 `$_POST` 提供数据，而是构造一个包含**良好**数据和*不良*数据的数组：

|  | **字段名** | **类型** | **允许为空？** |
| :--- | :--- | :--- | :--- |
| ☐ | id | int(11) | 否 |
| ☐ | first_name | varchar(128) | 否 |
| ☐ | last_name | varchar(128) | 否 |
| ☐ | address | varchar(256) | 是 |
| ☐ | city | varchar(64) | 是 |
| ☐ | state_province | varchar(32) | 是 |
| ☐ | postal_code | char(16) | 否 |
| ☐ | phone | varchar(16) | 否 |
| ☐ | country | char(2) | 否 |
| ☐ | email | varchar(250) | 否 |
| ☐ | status | char(8) | 是 |
| ☐ | budget | decimal(10,2) | 是 |
| ☐ | last_updated | datetime | 是 |

现在，你可以创建一个 `chap_06_post_data_filtering.php` 脚本，该脚本设置自动加载，并包含消息和回调配置文件：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
include __DIR__ . '/chap_06_post_data_config_messages.php';
include __DIR__ . '/chap_06_post_data_config_callbacks.php';
```

接着，你需要定义*分配项*，它表示数据字段与过滤回调之间的映射。使用 `*` 键来定义应用于所有数据的**全局过滤器**：

```php
$assignments = [
    '*'       => [ ['key' => 'trim', 'params' => []],
                   ['key' => 'strip_tags', 'params' => [] ]],
    'first_name' => [ ['key' => 'length',
                      'params' => ['length' => 128]] ],
    'last_name'  => [ ['key' => 'length',
                      'params' => ['length' => 128]] ],
    'city'       => [ ['key' => 'length',
                      'params' => ['length' => 64]] ],
    'budget'     => [ ['key' => 'filter_float', 'params' => []] ],
];
```

接下来，定义良好的测试数据和不良的测试数据：

```php
$goodData = [
	'first_name'		=> 'Your Full',
	'last_name'			=> 'Name',
	'address'			=> '123 Main Street',
	'city'				=> 'San Francisco',
	'state_province'	=> 'California',
	'postal_code'		=> '94101',
	'phone'				=> '+1 415-555-1212',
	'country'			=> 'US',
	'email'				=> 'your@email.address.com',
	'budget'			=> '123.45',
];
$badData = [
	'first_name'		=> 'This+Name<script>bad tag</script>Valid!',
	'last_name'		=> 'ThisLastNameIsWayTooLong
	Abcdefghijklmnopqrstuvwxyz0123456789
	Abcdefghijklmnopqrstuvwxyz0123456789
	Abcdefghijklmnopqrstuvwxyz0123456789
	Abcdefghijklmnopqrstuvwxyz0123456789',
	// 'address'		=> '',		// 缺失
	'city'			=> '
	ThisCityNameIsTooLong0123456789012345678901234
	56789012345678901234567890123456789	',
	// 'state_province'=> '',		// 缺失
	'postal_code'		=> '!"#£$%^&*Non Alpha Chars',
	'phone'			=> ' 12345 ',
	'country'			=> 'XX',
	'email'			=> 'this.is.not@an.email',
	'budget'			=> 'XXX',
];
```

最后，你可以创建一个 `Application\Filter\Filter` 实例，并测试这些数据：

```php
$filter = new Application\Filter\Filter(
	$config['filters'], $assignments);
$filter->setSeparator(PHP_EOL);
$filter->process($goodData);
echo $filter->getMessageString();
var_dump($filter->getItemsAsArray());

$filter->process($badData);
echo $filter->getMessageString();
var_dump($filter->getItemsAsArray());
```

处理良好数据时，除了有一条消息指出浮点字段的值已从字符串转换为浮点数外，不会生成其他消息。另一方面，处理不良数据时，会产生以下输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_231_0.png)

你还会注意到，first_name 中的标签已被移除，且 last_name 和 city 均被截断。

## 更多相关内容…

filter_input_array() 函数接受两个参数：输入源（形式为用于指示 PHP 超全局变量之一的预定义常量，即 $_POST）以及一个以匹配的字段定义作为键、以过滤器或验证器作为值的数组。该函数不仅执行过滤操作，还执行验证操作。标记为 sanitize 的标志实际上是过滤器。

## 参见

filter_input_array() 的文档和示例可在 http://php.net/manual/en/function.filter-input-array.php 找到。你可能还会想查看 http://php.net/manual/en/filter.filters.php 上可用的不同类型的过滤器。

## 链接 $_POST 验证器

本食谱中的*主要工作*已在上一食谱中完成。核心功能由 `Application\Filter\AbstractFilter` 定义。实际验证是由一系列验证回调数组执行的。

### 执行方法...

1.  回顾上一食谱，*链接 $_POST 过滤器*。我们将使用此食谱中的所有类和配置文件，除非在此处另有说明。
2.  首先，我们定义一个验证回调的配置数组。与上一食谱一样，每个回调都应实现 `Application\Filter\CallbackInterface`，并应返回 `Application\Filter\Result` 的实例。验证器将采用这种通用形式：

```php
use Application\Filter\{ Result, Messages, CallbackInterface };
$config = [
// validator callbacks
'validators' => [
'key' => new class () implements CallbackInterface
{
public function __invoke($item, $params) : Result
{
// validation logic goes here
return new Result($valid, $error);
}
},
// etc.
]
];
```

3.  接下来，我们定义一个 `Application\Filter\Validator` 类，它遍历分配项数组，并使用分配的验证回调测试每个数据项。我们让此类继承 `AbstractFilter`，以便提供前面描述的核心功能：

```php
namespace Application\Filter;
class Validator extends AbstractFilter
{
// code
}
```

4.  在此类中，我们定义一个核心 `process()` 方法，该方法扫描数据数组并根据分配项数组应用验证器。如果此数据集没有分配的验证器，我们只需返回 `$valid` 的当前状态（即 `TRUE`）：

```php
public function process(array $data)
{
    $valid = TRUE;
    if (!isset($this->assignments)
        && count($this->assignments)) {
        return $valid;
    }
```

5.  否则，我们将 `$this->results` 初始化为一个由 `Result` 对象组成的数组，其中 `$item` 属性设置为 `TRUE`，且 `$messages` 属性为一个空数组：

```php
foreach ($data as $key => $value) {
    $this->results[$key] = new Result(TRUE, array());
}
```

6.  然后，我们复制一份 `$this->assignments` 并检查是否存在任何 `global` 过滤器（通过 `'*'` 键标识）。如果有，我们运行 `processGlobal()`，然后取消设置 `'*'` 键：

```php
$todo = $this->assignments;
if (isset($todo['*'])) {
    $this->processGlobalAssignment($todo['*'], $data);
    unset($todo['*']);
}
```

7.  最后，我们遍历剩余的分配项，调用 `processAssignment()`。这是检查分配项数组中存在的任何字段是否缺失于数据中的一个理想位置。请注意，如果任何验证回调返回 `FALSE`，我们将 `$valid` 设置为 `FALSE`：

```php
foreach ($todo as $key => $assignment) {
    if (!isset($data[$key])) {
        $this->results[$key] =
            new Result(FALSE, $this->missingMessage);
    } else {
        $this->processAssignment(
            $assignment, $key, $data[$key]);
    }
    if (!$this->results[$key]->item) $valid = FALSE;
}
return $valid;
```

8.  如你所回忆的，每个*分配项*都*键控*到数据字段，并且代表针对该字段的回调数组。因此，在 `processGlobalAssignment()` 中，我们需要遍历回调数组。然而，在这种情况下，因为这些*分配项*是**全局的**，我们还需要遍历**整个**数据集，并依次应用每个全局过滤器。

9.  与相应的 `Application\Filter\Filter::processGlobalAssignment()` 方法相比，我们需要调用 `mergeValidationResults()`。原因是如果 `$result->item` 的值已经是 `FALSE`，我们需要确保它随后不会被 `TRUE` 值覆盖。链中返回 `FALSE` 的任何验证器都必须覆盖其他任何验证结果：

```php
protected function processGlobalAssignment($assignment, $data)
{
    foreach ($assignment as $callback) {
        if ($callback === NULL) continue;
        foreach ($data as $k => $value) {
            $result = $this->callbacks[$callback['key']]
                     ($value, $callback['params']);
            $this->results[$k]->mergeValidationResults($result);
        }
    }
}
```

10. 当我们定义 `processAssignment()` 时，以类似于 `processGlobalAssignment()` 的方式，我们需要执行**每个剩余分配的回调**，针对每个数据键，再次调用 `mergeValidationResults()`： 

```php
protected function processAssignment($assignment, $key, $value)
{
    foreach ($assignment as $callback) {
        if ($callback === NULL) continue;
        $result = $this->callbacks[$callback['key']]
                  ($value, $callback['params']);
        $this->results[$key]->mergeValidationResults($result);
    }
}
```

### 工作原理...

与上一食谱一样，请确保定义以下类：

- `Application\Filter\Result`
- `Application\Filter\CallbackInterface`

