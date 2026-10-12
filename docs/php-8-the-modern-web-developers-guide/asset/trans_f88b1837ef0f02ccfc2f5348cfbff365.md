
在这种情况下，`str_starts_with()` 返回 true，因为字符串 ‘Hello, world!’ 以前缀 ‘Hello.’ 开头。

### 6.3.3. `str_ends_with()`

`str_ends_with()` 函数检查字符串是否以指定的后缀结尾。如果字符串以该后缀结尾则返回 true，否则返回 false。

```
$text = 'This is the end.';
$suffix = 'end.';

if (str_ends_with($text, $suffix)) {
    echo 'String ends with the suffix!';
} else {
    echo 'String does not end with the suffix.';
}
```

在此示例中，`str_ends_with()` 返回 true，因为字符串 ‘This is the end.’ 以后缀 ‘end.’ 结尾。

这些字符串函数对于简化条件检查和提高代码可读性非常有用。在 PHP 应用程序中处理各种字符串操作时，它们特别有用。

---

## 6.4. 理解并使用 Unicode 和多字节字符串

在现代 Web 开发中，处理各种字符和语言至关重要，这些字符和语言通常包含非 ASCII 字符。PHP 8 为 Unicode 和多字节字符串提供了增强的支持，确保您的应用程序能够有效地处理各种字符编码和语言。

### 6.4.1. 多字节字符串函数

PHP 提供了一组多字节字符串函数（以 `mb_` 为前缀），允许您处理除默认 ISO-8859-1 (Latin-1) 以外的字符编码。这些函数对于处理使用多字节字符的语言（如中文、日文或阿拉伯文）至关重要。

下面是一个使用 `mb_strlen()` 函数计算多字节字符串长度的示例：

```
$text = 'こんにちは、世界！'; // 日语问候语
$length = mb_strlen($text, 'UTF-8'); // 指定字符编码 (UTF-8)
echo "The string length is: $length characters.";
```

在此示例中，`mb_strlen()` 与字符编码 ‘UTF-8’ 一起使用，以正确确定日语问候语字符串的长度。

### 6.4.2. 多字节字符串操作

`mb_substr()` 函数允许您提取多字节字符串的部分内容，而不会破坏字符。这对于使用多字节编码的语言中的子字符串操作至关重要。

```
$text = '你好，世界！'; // 中文问候语
$substring = mb_substr($text, 0, 2, 'UTF-8'); // 提取前两个字符
echo "The substring is: $substring";
```

在这种情况下，`mb_substr()` 确保提取的子字符串由完整的字符组成，即使是在多字节编码中。

### 6.4.3. 字符编码转换

PHP 8 提供了诸如 `mb_convert_encoding()` 之类的函数，用于在不同字符编码之间进行转换。当您需要处理以各种编码形式传入的数据时，这非常有用。

```
$text = 'Привет, мир!'; // 俄语问候语
$utf8Text = mb_convert_encoding($text, 'UTF-8', 'Windows-1251'); // 从 Windows-1251 转换为 UTF-8
echo "UTF-8 encoded text: $utf8Text";
```

在此示例中，`mb_convert_encoding()` 用于将字符串从 Windows-1251 编码转换为 UTF-8。

### 6.4.4. Unicode 规范化

在处理同一字符的不同表示形式时，Unicode 规范化至关重要。PHP 8 提供了诸如 `mb_normalize()` 之类的函数来规范化 Unicode 字符串，确保一致性。

```
$text1 = 'Café'; // 带锐音符 (é)
$text2 = 'Café'; // 带组合锐音符 (é)

$normalized1 = mb_normalize('NFC', $text1); // 规范化为 NFC (组合形式)
$normalized2 = mb_normalize('NFC', $text2);

echo "Are they equivalent? " . ($normalized1 === $normalized2 ? 'Yes' : 'No');
```

在此示例中，`mb_normalize()` 用于将单词 ‘Café’ 的两个版本规范化为 NFC (组合形式)，使它们等效。

### 6.4.5. 文件操作中的 Unicode 字符处理

当处理包含 Unicode 字符的文件时，指定适当的字符编码至关重要。您可以使用 `mb_` 函数正确处理具有多字节字符编码的文件读取和写入操作。

```
$filename = 'unicode.txt';
$content = file_get_contents($filename); // 读取包含多字节字符的文件
$decodedContent = mb_convert_encoding($content, 'UTF-8', 'ISO-8859-1'); // 转换为 UTF-8
echo $decodedContent;
```

在此代码中，`file_get_contents()` 读取包含多字节字符的文件，然后 `mb_convert_encoding()` 将内容转换为 UTF-8 以便正确处理。

总之，PHP 8 对 Unicode 和多字节字符串的支持对于构建能够与各种字符编码和语言无缝协作的应用程序至关重要。`mb_` 函数和相关特性确保您的 PHP 应用程序能够处理现代国际化和本地化需求的复杂性。

---

## 6.5. 结合命名参数的数组解包

PHP 8 引入了命名参数的概念，它提供了一种更灵活的方式将参数传递给函数和方法。此特性通过允许您按名称而非位置指定参数，提高了代码的可读性和可维护性。结合命名参数，您还可以使用数组解包将数组作为命名参数传递给函数。

### 6.5.1. 命名参数回顾

在深入探讨数组解包之前，让我们简要回顾一下命名参数。在 PHP 8 中，您可以按名称指定函数和方法参数，如下所示：

```
function sendMessage($to, $message, $from) {
    // 函数逻辑
}

// 使用命名参数
sendMessage(from: 'Alice', message: 'Hello, Bob!', to: 'Bob');
```

命名参数通过显式指定参数名称提供了清晰度，使函数调用更易于理解。

### 6.5.2. 结合命名参数的数组解包

数组解包允许您将关联数组的键值对作为命名参数传递给函数或方法。当您有一个值数组想要传递给接受命名参数的函数时，这特别有用。

请看下面的示例：

```
function createPerson($name, $age, $city) {
    // 函数逻辑
}

$personData = [
    'name' => 'Alice',
    'age' => 30,
    'city' => 'Wonderland',
];

// 使用数组解包传递命名参数
createPerson(...$personData);
```

在此示例中，`createPerson()` 函数接受三个命名参数。`...$personData` 语法解包关联数组，将其键映射到函数的参数名称。

### 6.5.3. 默认值与数组解包

您还可以将数组解包与命名参数的默认值结合使用。如果关联数组缺少与具有默认值的命名参数对应的键，则将使用默认值。

```
function createPerson($name = 'Unknown', $age = 0, $city = 'Unknown') {
    // 函数逻辑
}

$personData = [
    'name' => 'Alice',
    'age' => 30,
];

// 使用数组解包传递带默认值的命名参数
createPerson(...$personData);
```

在这种情况下，由于关联数组中不存在 ‘city’ 参数，因此它将默认为 ‘Unknown’。

### 6.5.4. 数组解包与可变参数函数

可变参数函数（接受可变数量参数的函数）也可以从结合命名参数的数组解包中受益。您可以将数组解包与可变参数函数结合使用，以处理动态数量的参数。

```
function logMessages(...$messages) {
    // 函数逻辑
}

$logData = [
    'messages' => ['Error: Something went wrong', 'Info: Task completed'],
];

// 使用数组解包将命名参数传递给可变参数函数
logMessages(...$logData['messages']);
```

在此示例中，`logMessages()` 函数是可变参数函数，`...$logData['messages']` 语法将消息数组作为命名参数解包。

PHP 8 结合命名参数的数组解包提供了一种强大且灵活的方式将数据传递给函数和方法，提高了代码可读性并简化了将关联数组作为函数参数的处理。

---

# 7.1. 类构造函数增强
