

# 第三部分：使用 PHP 练习

字段名和标签，以及显示在每个按钮后的脚本文本（“Male/男性”和“Female/女性”），以及“m”和“f”对应的值。然后将这两个按钮添加到一个数组中：

```php
$genderOptions = array();
$genderOptions[] = HTMLQuickForm::createElement("radio", null, null,
Male, "m");
$genderOptions[] = HTMLQuickForm::createElement("radio", null, null,
Female, "f");
```

然后使用此按钮数组创建一个名为“gender”且且标签为“Your gender”（您的性别）的元素。HTML_QuickForm 将每个数组按钮的字段设置为组名“gender”：

```php
$form->addGroup($genderOptions, "gender", "Your gender", " );
```

要创建 favoriteGenre（最喜爱的类型），请选择该字段，使用 `Member::Genre` 方法获取类型名称的关联数组并将其传递给 `addElement()`。脚本需要创建一个临时的 $member 对象来调用 `Member::getGenres($member)`，因为 `getGenres()` 不是一个静态方法：

```php
$member = new Member(array());
$form->addElement("select", "favoriteGenre", "What's favorite
genre?", $member->getGenres());
```

`addRule()` 函数使用 `addRule` 方法为表单字段添加验证规则。所有必填字段都会根据 `required` 规则进行检查，用户名和密码字段使用字母数字规则，以确保它们只包含字母和/或数字。此外，使用 `compare` 规则来检查两个密码字段是否包含相同的值：

```php
$form->addRule(array("password1", "password2", "Please make sure you
enter your password correctly in both password fields.", "compare");
```

邮箱字段当然也使用 `email` 规则进行检查。其余字段——firstName、lastName、genre、favoriteGenre 和 otherinterests——使用 `regex` 规则根据各种正则表达式进行检查。

对于兴趣（interest），我们创建了 favoriteGenre。这创建了一个临时的 $member 对象并调用其 `getGenres()` 方法来检索允许的类型的关联数组。然后，它使用 PHP 的 `array_keys()` 函数提取类型值（该函数返回一个包含给定数组中所有键的索引），并使用 `implode()` 函数将结果数组转换为由 `|` 分隔的字符串，以便插入正则表达式中：

```php
$member = new Member(array());
$form->addRule("favoriteGenre", "The Favorite Genre field can contain only
allowed genre values", "regex", . implode("|", array_keys($member->getGenres()) ) . \$/);
```

468

# 第15章：使用 PEAR 让你的工作更轻松

`implode()` 在第6章中已经解释过，你可以在第18章中找到更多关于正则表达式和替代方案的知识。

此外，注意 callback 规则类型的两种用法。用户名通过调用 `checkDuplicateUsername()` 函数（你可以在监控中获取它）进行验证；如果用户名是唯一的，该函数返回 true；如果用户名已存在于数据库中，则返回 false。emailAddress 字段也使用 `checkDuplicateEmailAddress()` 回调函数进行类似的检查：

```php
$form->addRule("username", "A member with that username already exists in the database. Please choose another.", "callback",
$form->addRule("emailAddress", "A member with that email already exists in the database. Please choose another email address, or contact the webmaster to retrieve your password.", "callback",
$checkDuplicateEmailAddress(");
```

接下来是刚才描述的两个函数。`checkDuplicateUsername()` 接收要检查的用户名。它调用 `Member::getUsername()` 尝试检索具有相同用户名的现有成员。返回值被转换为布尔值（Boolean）：如果返回了 Member 对象，则被转换为 true，否则结果值将为 false。然后使用 `!`（非）运算符获取该值，以从函数获取正确的值：

```php
return !((boolean) Member::getUsername($value));
```

`checkDuplicateEmailAddress()` 的工作相同，调用 `Member::getByEmailAddress()` 来查找具有相同邮箱地址的现有成员：

```php
return ((boolean) Member::getByEmailAddress($value);
```

`processForm()` 函数比第14章中对应的版本简单得多，因为检索和验证提交数据的所有困难工作已经由 HTML_QuickForm 完成了。该函数接收提交字段的关联数组（传递给 HTML_QuickForm 对象），添加一个带有 `password1` 值的新密码字段，并根据当前日期创建 `DateField`。这组完整的字段数组被传递给 Member 构造函数创建 Member 对象，然后通过调用 `insert()` 方法将其添加到数据库：

```php
function processForm($values) {
$values['password'] = $values['password1'];
$values['DateField'] = date("Y-m-d");
$member = new Member($values);
$member->insert();
}
```

多亏使用了 HTML_QuickForm 完成了大量大量工作（显示表单、收集和验证提交的数据以及报告错误），这个重写的 `register.php` 脚本既优雅又易读。更重要的是，它只有 96 行代码，而原始脚本有 127 行。这就是复用代码的力量！

# 总结

在本章中，你探索了 PEAR（PHP 扩展和应用程序库）：这是一个庞大的免费可重用代码集合，你可以将其整合到自己的 PHP 项目中。通过使用 PEAR 包，你正在基于预写的、经过同行评审和彻底测试的代码构建你的 Web 应用程序，这节省了你大量的调试时间。

在学习本章的过程中，你：

- 研究了 PEAR 包管理器
- 学了如何安装和删除 PEAR 包
- 使用 Net_Detect 包编写了检测浏览器的脚本
- 使用 HTML_Table 包生成了表格
- 学了如何使用 HTML_QuickForm 包生成、处理和验证表单
- 重写了注册脚本，使其更加简洁

本章让你体验了 PEAR 的强大和实用。尝试完成练习，并在 http://pear.php.net 查看其他包。这些练习的答案可以在附录 A。

在下一章中，你将探索 PHP 脚本与外部世界交互的方法，包括发送电子邮件。

# 练习

- 1. 下载并安装 Numbers_Roman 包，并使用它编写一个显示1到100的罗马数字的脚本。
- 2. 使用 Numbers_Roman 和 HTML_QuickForm 编写一个罗马数字转换器。用户可以以罗马或阿拉伯格式输入数字，然后点击转换按钮。脚本将以另一种格式显示该数字。

