

## 工作原理……

您可以先按照上文描述对 `Application\Form\Factory` 进行修改。作为测试目标，您可以使用*工作原理...*章节中*链接 $...POST 过滤器*配方里展示的 `prospects` 数据库表。各种列设置应该能让您了解需要定义哪些表单元素、过滤器和验证器。

例如，您可以定义一个 `chap_06_tying_filters_to_form_definitions.php` 文件，其中将包含表单包装器、元素和过滤器分配的代码定义。以下是一些示例：

```php
<?php
use Application\Form\Generic;

define('VALIDATE_SUCCESS', 'SUCCESS: form submitted ok!');
define('VALIDATE_FAILURE', 'ERROR: validation errors detected');

$wrappers = [
    Generic::INPUT    => ['type' => 'td', 'class' => 'content'],
    Generic::LABEL    => ['type' => 'th', 'class' => 'label'],
    Generic::ERRORS   => ['type' => 'td', 'class' => 'error']
];

$elements = [
    'first_name' => [
        'class'    => 'Application\Form\Generic',
        'type'     => Generic::TYPE_TEXT,
        'label'    => 'First Name',
        'wrappers' => $wrappers,
        'attributes'=> ['maxLength'=>128,'required'=>'']
    ],
    'last_name'  => [
        'class'    => 'Application\Form\Generic',
        'type'     => Generic::TYPE_TEXT,
        'label'    => 'Last Name',
        'wrappers' => $wrappers,
        'attributes'=> ['maxLength'=>128,'required'=>'']
    ],
    // etc.
];

// overall form config
$formConfig = [
    'name'        => 'prospectsForm',
    'attributes'  => [
        'method'=>'post',
        'action'=>'chap_06_typing_filters_to_form.php'
    ],
    'row_wrapper' => ['type' => 'tr', 'class' => 'row'],
    'form_wrapper' => [
        'type'=>'table',
        'class'=>'table',
        'id'=>'prospectsTable',
        'class'=>'display','cellspacing'=>'0'
    ],
    'form_tag_inside_wrapper' => FALSE,
];

$assignments = [
    'first_name' => [ ['key' => 'length',
        'params' => ['min' => 1, 'max' => 128]],
        ['key' => 'alnum',
        'params' => ['allowWhiteSpace' => TRUE]],
        ['key' => 'required','params' => []] ],
    'last_name' => [ ['key' => 'length',
        'params' => ['min' => 1, 'max' => 128]],
        ['key' => 'alnum',
        'params' => ['allowWhiteSpace' => TRUE]],
        ['key' => 'required','params' => [] ] ],
    'address' => [ ['key' => 'length',
        'params' => ['max' => 256]] ],
    'city' => [ ['key' => 'length',
        'params' => ['min' => 1, 'max' => 64]] ],
    'state_province'=> [ ['key' => 'length',
        'params' => ['min' => 1, 'max' => 32]] ],
    'postal_code' => [ ['key' => 'length',
        'params' => ['min' => 1, 'max' => 16] ],
        ['key' => 'alnum',
        'params' => ['allowWhiteSpace' => TRUE]],
        ['key' => 'required','params' => []] ],
    'phone' => [ ['key' => 'phone', 'params' => []] ],
    'country' => [ ['key' => 'in_array',
        'params' => $countries ],
        ['key' => 'required','params' => []] ],
    'email' => [ ['key' => 'email', 'params' => [] ],
        ['key' => 'length',
        'params' => ['max' => 250] ],
        ['key' => 'required','params' => []] ],
    'budget' => [ ['key' => 'float', 'params' => [] ]
];
```

您可以使用之前配方中描述的已存在的 `chap_06_post_data_config_callbacks.php` 和 `chap_06_post_data_config_messages.php` 文件。最后，定义一个 `chap_06_tying_filters_to_form.php` 文件，该文件设置自动加载并包含这三个配置文件：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../..');
include __DIR__ . '/chap_06_post_data_config_messages.php';
include __DIR__ . '/chap_06_post_data_config_callbacks.php';
include __DIR__ . '/chap_06_tying_filters_to_form_definitions.php';
?>
```

接下来，您可以创建表单工厂、过滤器和验证器类的实例：

```php
use Application\Form\Factory;
use Application\Filter\{ Validator, Filter };
$form = Factory::generate($elements);
$form->setFilter(new Filter($Callbacks['filters'],
    $Assignments['filters']));
$form->setValidator(new Validator($Callbacks['validators'],
    $Assignments['validators']));
```

然后，您可以检查是否存在 `$_POST` 数据。如果存在，则执行验证和过滤：

```php
$message = '';
if (isset($_POST['submit'])) {
    $form->setData($_POST);
    if ($form->validate()) {
        $message = VALIDATE_SUCCESS;
    } else {
        $message = VALIDATE_FAILURE;
    }
    $form->filter();
}
?>
```

视图逻辑非常简单：只需渲染表单即可。验证消息以及各个元素的值将作为验证和过滤过程的一部分被分配：

```php
<?= $form->render($form, $formConfig); ?>
```

以下是使用错误表单数据的示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_243_0.png)

请注意过滤和验证消息。还要注意错误标签：

![](img/39390f6d56c5a83b28db083a8bd5185c_243_1.png)

# 7
# 访问 Web 服务

在本章中，我们将涵盖以下主题：

- 在 PHP 和 XML 之间进行转换
- 创建简单的 REST 客户端
- 创建简单的 REST 服务器
- 创建简单的 SOAP 客户端
- 创建简单的 SOAP 服务器

## 引言

向外部 Web 服务发起后台查询已成为任何 PHP Web 实践中日益重要的部分。提供适当、及时且丰富的数据能力意味着为您开发的客户和网站带来更多业务机会。我们首先介绍几个旨在实现**可扩展标记语言 (XML)** 与原生 PHP 之间数据转换的配方。接着，我们将展示如何实现简单的**表示状态转移 (REST)** 客户端和服务器。之后，我们将关注 **SOAP** 客户端和服务器。

## 在 PHP 和 XML 之间进行转换

在考虑 PHP 原生数据类型与 XML 之间的转换时，我们通常会将数组作为主要目标。基于这一点，从 PHP 数组转换为 XML 的过程与反向转换所需的策略截然不同。

> 也可以考虑对象转换；然而，在 XML 中渲染对象方法是困难的。不过，可以使用 `get_object_vars()` 函数将对象属性读取到数组中，从而表示属性。

### 实现方法...

1. 首先，我们定义一个 `Application\Parse\ConvertXml` 类。该类将持有用于从 XML 转换为 PHP 数组及反向转换的方法。我们需要 SPL 中的 `SimpleXMLElement` 和 `SimpleXMLIterator` 类：

    ```php
    namespace Application\Parse;

    use SimpleXMLIterator;
    use SimpleXMLElement;

    class ConvertXml
    {
    }
    ```

2. 接下来，我们定义一个 `xmlToArray()` 方法，该方法接受一个 `SimpleXMLIterator` 实例作为参数。它将被递归调用，并从 XML 文档生成 PHP 数组。我们利用 `SimpleXMLIterator` 遍历 XML 文档的能力，使用 `key()`、`current()`、`next()` 和 `rewind()` 方法进行导航：

    ```php
    public function xmlToArray(SimpleXMLIterator $xml) : array
    {
        $a = array();

        for( $xml->rewind(); $xml->valid(); $xml->next() ) {
            if(!array_key_exists($xml->key(), $a)) {
                $a[$xml->key()] = array();
            }

            if ($xml->hasChildren()) {
                $a[$xml->key() ][] = $this->xmlToArray($xml->current());
            }
            else{
                $a[$xml->key() ] = (array) $xml->current()->attributes();
                $a[$xml->key()][ 'value'] = strval($xml->current());
            }
        }
        return $a;
    }
    ```

3. 对于反向过程（同样递归调用），我们定义两个方法。第一个方法 `arrayToXml()` 设置初始的 `SimpleXMLElement` 实例，然后调用第二个方法 `phpToXml()`：

    ```php
    public function arrayToXml(array $a)
    {
        $xml = new SimpleXMLElement('<?xml version="1.0" standalone="yes"?><root></root>');
        $this->phpToXml($a, $xml);
        return $xml->asXML();
    }
    ```

4. 请注意，在第二个方法中，我们使用 `get_object_vars()` 以防数组元素之一是对象。您还会注意到，单独的数字不能作为 XML 标签，这意味着需要在数字前添加一些文本：

    ```php
    protected function phpToXml($value, &$xml)
    {
        $node = $value;
        if (is_object($node)) {
            $node = get_object_vars($node);
        }
        if (is_array($node)) {
            foreach ($node as $k => $v) {
                if (is_numeric($k)) {
                    $k = 'number' . $k;
                }
                if (is_array($v)) {
                    $newNode = $xml->addChild($k);
                    $this->phpToXml($v, $newNode);
                } elseif (is_object($v)) {
                    $newNode = $xml->addChild($k);
                    $this->phpToXml($v, $newNode);
                } else {
                    $xml->addChild($k, $v);
                }
            }
        } else {
            $xml->addChild(self::UNKNOWN_KEY, $node);
        }
    }
    ```

