

## PHP 引用规则

引用可以使用赋值运算符 `=` 赋给另一个变量。例如，`$subject = &$title` 将变量 `$title` 的引用赋给变量 `$subject`。

持有引用的变量是原始变量的别名，其行为方式与原始变量完全相同。例如，`$subject = &$title; var_dump($subject);` 会打印出赋给变量 `$title` 的数据的信息。

如果原始变量被赋予新数据，引用变量会自动被赋予该新数据。例如，`$subject = &$title; $title = "New String";` 将 "New String" 同时赋给 `$subject` 和 `$title`。

如果引用变量被赋予新数据，原始变量会自动被赋予该新数据。例如，`$subject = &$title; $subject = "New Text";` 将 "New Text" 同时赋给 `$subject` 和 `$title`。

可以通过将引用赋给多个变量来创建多个引用变量。例如，`$subject = &$title; $topic = &$title;` 将 `$title` 的引用同时赋给 `$subject` 和 `$topic`。

实际上，原始变量及其引用变量都可以被视为指向它们共享的同一数据的引用。例如，`$subject = &$title; $topic = &$title; $topic = "New Message";` 创建了 3 个指向同一数据 "New Message" 的变量。

要移除变量与其赋值数据之间的引用链接，需要使用 `unset($var)` 函数。例如，`$title = "New String"; unset($title);` 移除 `$title` 与 "New String" 之间的引用链接。此时 `$title` 处于“未设置”状态。

如果多个变量引用同一数据，移除其中一个变量的引用链接不会影响其他变量。例如，`$subject = &$title; $topic = &$title; $topic = "New Message"; unset($topic);` 移除了 `$topic` 上的引用链接，但 `$subject` 和 `$title` 仍引用 "New Message"。

如果多个变量引用同一数据，将其中一个变量赋予指向新数据的新引用不会影响其他变量。例如，`$subject = &$title; $topic = &$title; $topic = "New Message"; $topic = &$name;` 将 `$name` 的引用赋给 `$topic`，但 `$subject` 和 `$title` 仍引用 "New Message"。

### ReferenceTest.php 示例

为了演示上述提到的一些引用规则，我编写了以下 PHP 脚本 `ReferenceTest.php`：

```php
<?php
#  ReferenceTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $title;
   print "\n \$title is not assigned to anything:\n";
   print "    \$title: "; var_dump($title);

   $subject = &$title;
   print "\n \$subject is an alias of $title:\n";
   print "    \$subject: "; var_dump($subject);
   print "    \$title: "; var_dump($title);

   $subject = "Herong's PHP Book";
   print "\n \$subject is assigned with a string:\n";
   print "    \$title: "; var_dump($title);
   print "    \$subject: "; var_dump($subject);

   $title = "Herong's Programming Book";
   print "\n \$title is reassigned with a new string:\n";
   print "    \$title: "; var_dump($title);
   print "    \$subject: "; var_dump($subject);

   $topic = &$subject;
   print "\n \$topic is added as the third reference variable:\n";
   print "    \$title: "; var_dump($title);
   print "    \$subject: "; var_dump($subject);
   print "    \$topic: "; var_dump($topic);

   unset($subject);
   print "\n \$subject's reference link is removed:\n";
   print "    \$title: "; var_dump($title);
   print "    \$subject: "; var_dump($subject);
   print "    \$topic: "; var_dump($topic);


   $name = "Herong's Tutorial Book";
   $title = &$name;
   print "\n \$title is assigned to a new reference:\n";
   print "    \$title: "; var_dump($title);
   print "    \$subject: "; var_dump($subject);
   print "    \$topic: "; var_dump($topic);
   print "    \$name: "; var_dump($name);
?>
```

如果你在 PHP 7 及更高版本中运行此示例脚本，输出中应包含一些 "Notice"（通知）消息。这是因为现在默认消息级别设置为 `E_NOTICE`。你可以更改设置或修改代码，以确保在使用变量前所有变量均已定义。

```
herong> \php-7.3\php ReferenceTest.php

 $title is not assigned to anything:
    $title: PHP Notice:  Undefined variable: title in
       C:\herong\ReferenceTest.php on line 7

Notice: Undefined variable: title in
   C:\herong\ReferenceTest.php on line 7
NULL

 $subject is an alias of :
    $subject: NULL
    $title: NULL

 $subject is assigned with a string:
    $title: string(17) "Herong's PHP Book"
    $subject: string(17) "Herong's PHP Book"

 $title is reassigned with a new string:
    $title: string(25) "Herong's Programming Book"
    $subject: string(25) "Herong's Programming Book"

 $topic is added as the third reference variable:
    $title: string(25) "Herong's Programming Book"
    $subject: string(25) "Herong's Programming Book"
    $topic: string(25) "Herong's Programming Book"

 $subject's reference link is removed:
    $title: string(25) "Herong's Programming Book"
    $subject: PHP Notice:  Undefined variable: subject in
       C:\herong\ReferenceTest.php on line 33

Notice: Undefined variable: subject in
   C:\herong\ReferenceTest.php on line 33
NULL
    $topic: string(25) "Herong's Programming Book"

 $title is assigned to a new reference:
    $title: string(22) "Herong's Tutorial Book"
    $subject: PHP Notice:  Undefined variable: subject in
       C:\herong\ReferenceTest.php on line 41

Notice: Undefined variable: subject in
   C:\herong\ReferenceTest.php on line 41
NULL
    $topic: string(25) "Herong's Programming Book"
    $name: string(22) "Herong's Tutorial Book"
```

如果你在 PHP 5 及更低版本中运行此示例脚本，输出中不应包含任何 "Notice" 消息：

```
herong> \php-5.6\php ReferenceTest.php

 $title is not assigned to anything:
    $title: NULL

 $subject is an alias of :
    $subject: NULL
    $title: NULL

 $subject is assigned with a string:
    $title: string(17) "Herong's PHP Book"
    $subject: string(17) "Herong's PHP Book"

 $title is reassigned with a new string:
    $title: string(25) "Herong's Programming Book"
    $subject: string(25) "Herong's Programming Book"

 $topic is added as the third reference variable:
    $title: string(25) "Herong's Programming Book"
    $subject: string(25) "Herong's Programming Book"
    $topic: string(25) "Herong's Programming Book"

 $subject's reference link is removed:
    $title: string(25) "Herong's Programming Book"
    $subject: NULL
    $topic: string(25) "Herong's Programming Book"

 $title is assigned to a new reference:
    $title: string(22) "Herong's Tutorial Book"
    $subject: NULL
    $topic: string(25) "Herong's Programming Book"
    $name: string(22) "Herong's Tutorial Book"
```

[PHP 教程 - Herong 的教程示例](#part0001.xhtml)

∟ [变量、引用和常量](#part0022.xhtml)

∟ 变量变量名 - 使用表达式命名变量

### 变量变量名

本节介绍什么是变量变量名，将变量名存储在另一个变量中，使用表达式命名变量，以及使用任意表达式作为变量名。

**什么是变量变量名：** 变量变量名是指存储在另一个变量内部的变量名。通常，变量名是一个静态字符串。但有时，你希望将变量名存储在另一个变量中，以便能够参与运算。PHP 通过以下基本规则支持变量变量名：

1. 如果原始变量的名称存储在另一个不同的变量中，你可以在 PHP 源代码中使用 `$$var` 符号来标识原始变量。例如，`$variableName = "title"; $$variableName` 代表变量 `$title`。

