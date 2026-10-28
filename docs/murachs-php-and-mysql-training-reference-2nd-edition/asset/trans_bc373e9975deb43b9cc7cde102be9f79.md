

## Field 和 Fields 类（model/fields.php）

```php
<?php
class Field {
    private $name;
    private $message = '';
    private $hasError = false;

    public function __construct($name, $message = '') {
        $this->name = $name;
        $this->message = $message;
    }
    public function getName()    { return $this->name; }
    public function getMessage() { return $this->message; }
    public function hasError()   { return $this->hasError; }

    public function setErrorMessage($message) {
        $this->message = $message;
        $this->hasError = true;
    }
    public function clearErrorMessage() {
        $this->message = '';
        $this->hasError = false;
    }

    public function getHTML() {
        $message = htmlspecialchars($this->message);
        if ($this->hasError()) {
            return '<span class="error">' . $message . '</span>';
        } else {
            return '<span>' . $message . '</span>';
        }
    }
}

class Fields {
    private $fields = array();

    public function addField($name, $message = '') {
        $field = new Field($name, $message);
        $this->fields[$field->getName()] = $field;
    }

    public function getField($name) {
        return $this->fields[$name];
    }

    public function hasErrors() {
        foreach ($this->fields as $field) {
            if ($field->hasError()) { return true; }
        }
        return false;
    }
}
?>
```

图 15-11  Registration 应用（共 7 部分中的第 2 部分）

## Validate 类（model/validate.php）

```php
<?php
class Validate {
    private $fields;

    public function __construct() {
        $this->fields = new Fields();
    }

    public function getFields() {
        return $this->fields;
    }

    // Validate a generic text field
    public function text($name, $value,
            $required = true, $min = 1, $max = 255) {

        // Get Field object
        $field = $this->fields->getField($name);

        // If field is not required and empty, remove error and exit
        if (!$required && empty($value)) {
            $field->clearErrorMessage();
            return;
        }

        // Check field and set or clear error message
        if ($required && empty($value)) {
            $field->setErrorMessage('Required.');
        } else if (strlen($value) < $min) {
            $field->setErrorMessage('Too short.');
        } else if (strlen($value) > $max) {
            $field->setErrorMessage('Too long.');
        } else {
            $field->clearErrorMessage();
        }
    }

    // Validate a field with a generic pattern
    public function pattern($name, $value, $pattern, $message,
            $required = true) {

        // Get field object
        $field = $this->fields->getField($name);

        // If field is not required and empty, remove errors and exit
        if (!$required && empty($value)) {
            $field->clearErrorMessage();
            return;
        }

        // Check field and set or clear error message
        $match = preg_match($pattern, $value);
        if ($match === false) {
            $field->setErrorMessage('Error testing field.');
        } else if ( $match != 1 ) {
            $field->setErrorMessage($message);
        } else {
            $field->clearErrorMessage();
        }
    }

    public function phone($name, $value, $required = false) {
        $field = $this->fields->getField($name);

        // Call the text method and exit if it yields an error
        $this->text($name, $value, $required);
        if ($field->hasError()) { return; }

        // Call the pattern method to validate a phone number
        $pattern = '/^[[:digit:]]{3}-[[:digit:]]{3}-[[:digit:]]{4}$/';
        $message = 'Invalid phone number.';
        $this->pattern($name, $value, $pattern, $message, $required);
    }

    public function email($name, $value, $required = true) {
        $field = $this->fields->getField($name);

        // If field is not required and empty, remove errors and exit
        if (!$required && empty($value)) {
            $field->clearErrorMessage();
            return;
        }

        // Call the text method and exit if it yields an error
        $this->text($name, $value, $required);
        if ($field->hasError()) { return; }
```

在完成初步字段检查后，这段代码将电子邮件地址拆分为*本地部分*（local）和*域部分*（domain）。如果两部分不存在或其中任一部分过长，它会在 Field 对象中设置相应的错误消息。否则，它会使用正则表达式来测试每个部分的有效性。

根据 SMTP 规范，电子邮件地址的本地部分可以采用两种格式之一：*地址格式*（address format）或*带引号的文本格式*（quoted text format）。在这两种格式中，地址格式是几乎总被使用的格式。尽管带引号的文本格式很少被使用（如果曾使用过的话），但它仍然是潜在有效的。因此，你应该对其进行验证，否则就有阻止有效电子邮件地址的风险。

地址格式以一个*原子*（atom）开头，原子可以是字母、数字或 19 个符号（!#$%&'*+-/=?^_\`{|}~）之一。之后，一个原子后面可以跟其他原子。或者，一个原子后面可以跟零个或多个前面带点号的原子。换句话说，地址格式可以包含字母、数字和一些符号。但是，它不能以点号开头或结尾，也不能包含两个连续的点号。例如，“ray.harris”是有效的，但“ray..harris”或“ray.”是无效的。

带引号的文本格式包含用双引号括起来的文本。文本可以包含任何字符，但双引号和反斜杠前面必须有反斜杠。例如，“Ray Harris”和“Ray\\Harris”是有效的，但“Ray\Harris”是无效的。在这段代码中，`$char` 模式匹配任何不是反斜杠或双引号的字符，`$esc` 模式匹配 `\\` 或 `\"` 转义字符。因此，`$text` 模式匹配任何字符或转义的反斜杠/双引号，而 `$quoted` 模式就是被双引号包围的 `$text` 模式。

本地部分的最终模式是地址格式或带引号的文本格式中的一种。接下来，这段代码使用 pattern 方法根据该模式验证电子邮件地址的本地部分。如果本地部分无效，它会在 Field 对象中设置相应的错误消息并退出该方法。

域部分由一个或多个*主机名*（host names）后跟一个*顶级域名*（top level domain）组成。主机名最多可以有 64 个字母、数字或连字符，但不能以连字符开头或结尾。`$hostname` 模式匹配一个开头的字母数字字符，后跟一个可选的子模式，该子模式由最多 62 个连字符和字母数字字符组成，并以字母数字字符结尾。这样总长度范围可以是 1 到 64 个字符。

当电子邮件地址有多个主机名时，它们必须用点号分隔。这就是 `$hostnames` 模式匹配一个 `$hostname` 模式后跟零个或多个前面带点号的主机名的原因。最后，顶级域名可以有 2 到 6 个字母或数字，并且前面必须带点号。

域部分的最终模式是一个或多个主机名后跟一个顶级域名。接下来，这段代码使用 pattern 方法验证电子邮件地址的域部分。如果域部分无效，pattern 方法会在 Field 对象中设置相应的错误消息。但是，如果域部分有效，pattern 方法会清除 Field 对象中的错误消息。因此，该字段的电子邮件地址是有效的。

## 控制器

第 6 部分介绍了存储在 index.php 文件中的 Registration 应用的控制器。这段代码检查在注册页面上输入的所有数据，看它们是否有效。

控制器的代码首先加载包含这些类的 fields.php 和 validate.php 文件。然后，它创建一个新的 Validate 对象并将其存储在 $validate 变量中。接下来，它将 Fields 对象的引用存储在 $fields 变量中。

从 Validate 对象获取 Fields 对象后，这段代码使用 addField 方法为表单中的每个字段添加一个字段。这段代码为电话和电子邮件字段提供了默认消息。因此，当浏览器首次加载表单时，这些消息会显示给用户。

设置好字段后，代码检查全局 $_POST 数组中是否存在名为 action 的字段。如果不存在，它将 $action 变量设置为默认值“reset”。否则，这段代码将 action 复制到一个名为 $action 的局部变量中。但首先，它使用 strtolower 函数将 action 字符串转换为所有小写字母。

获取 action 后，这段代码使用 switch 语句根据当前 action 执行相应的代码。如果 action 是 reset，这段代码会重置变量的值，并使用字段的默认值显示注册页面。

如果 action 是 register，代码使用 trim 函数将表单字段的数据复制到局部变量中，以去除任何前导或尾随空格。然后，它使用 Validate 对象的 text、phone 和 email 方法来验证每个表单字段。

验证之后，这段代码使用 Validate 对象的 hasErrors 方法检查是否有任何字段存在错误。如果有，它会再次显示注册页面。否则，它会显示一个页面，表明数据已成功输入。

请注意，对 text、email 和 phone 方法的调用没有为可选的第三个参数（用于指定字段是否必填）提供值。因此，这些字段使用方法提供的默认值。这意味着电话号码字段不是必填的，但其他三个字段是必填的。当然，如果你想更改默认值，可以指定第三个参数。例如，要强制要求电话号码字段，你可以这样指定第三个参数：

```php
$validate->phone('phone', $phone, true);  // require phone field
```

