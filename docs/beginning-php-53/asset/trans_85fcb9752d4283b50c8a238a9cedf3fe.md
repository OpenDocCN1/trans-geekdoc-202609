

```xml
<pubDate>Mon, 04 Aug 2008 14:32:11 GMT</pubDate>
</item>
<item>
<title>A Hard Day in the Armchair</title>
<link>http://kitty-news.example.com/a-hard-day-in-the-armchair</link>
<description><![CDATA[After yesterday's frenzy of activity, Lucky
took it easy today and spent the whole day in the armchair.]]></description>
<pubDate>Sun, 03 Aug 2008 17:59:42 GMT</pubDate>
</item>
<item>
<title>A Mouse for Breakfast</title>
<link>http://kitty-news.example.com/a-mouse-for-breakfast</link>
<description><![CDATA[Clever Lucky caught a big juicy mouse for
breakfast this morning. She looks very contented right now.]]></description>
<pubDate>Sat, 02 Aug 2008 11:01:08 GMT</pubDate>
</item>
</channel>
</rss>
```

## 编写高质量代码

如果你已经学完了本书至此部分的内容，那么你对编写复杂PHP Web应用程序所需的技术已有不错的基础。恭喜！但在结束本书之前，值得看看如何编写 *高质量* 的应用程序。“高质量”一词颇具主观性，但就本书而言，它是指具备以下特质的代码：

- 易于阅读、维护和扩展
- 安全——即受到攻击防护
- 以强健且优雅的方式处理错误条件和问题
- 经过了良好的测试

随着你的Web应用程序变得越来越庞大和复杂，代码质量变得越来越重要。如果不维护严格的质量标准，大型代码库很快就会变得容易出错且难以使用。在本章中，你将学习以下质量控制技术：

- 将代码拆分为可管理、可复用的代码块
- 使用一套编码标准，使你的代码易于阅读
- 编写文档，以便其他在你的代码上工作的程序员更易读
- 验证输入并对输出进行编码，以降低代码中出现安全漏洞的风险
- 处理错误条件——即在代码运行时处理异常情况
- 清晰地将应用程序的业务逻辑与其用户界面分离
- 使用自动化测试框架来提高代码质量

读完本章后，你将具备创建强健、安全且易于你和其他程序员使用的PHP应用程序的知识，无论你的应用程序有多大或多复杂。那么，让我们开始吧！

## 编写模块化代码

在第15章中，你已经探索了模块化代码的概念——即小块的代码，可以反复重复使用。PEAR包是个很好的示例。每个PEAR包都是一个自包含的代码集合，用于执行特定任务。全球开发者已经成千上万次地使用了许多PEAR包。

编写模块化代码有许多优势，包括：

- **代码复用：** 你只需编写一次代码，然后就可以在各种PHP应用程序中多次使用它
- **易于维护：** 与其在应用程序中保留十份相同代码的副本，不如将代码保存在一个位置。如果你需要为代码添加新功能或修复bug，只需修改一份代码副本
- **可读性：** 通过将代码拆分成块，你可以使应用程序代码更易于阅读和理解
- **效率：** 与其将整个应用程序放在一个巨大的文件中——PHP引擎随后需要为每个页面视图加载并解释它——不如仅加载处理每个请求所需的代码

PHP包含一些有助于你编写模块化代码的功能，包括：

- **函数：** 在第7章中，你学习了如何将一段代码封装在函数中，然后只需从应用程序代码的其他位置调用该函数即可重用该代码
- **类：** 这一概念将代码封装更进一步，让你能在单个类中存储功能和属性。你在第8章中了解了关于类和对象的所有内容
- **include() 和 require()：** 这两个PHP函数——以及相关函数 include_once() 和 require_once() —— 允许你将一个脚本文件中的代码包含在另一个脚本文件内
- **命名空间：** 这些对于大型应用程序和库很有用。它们有助于避免同一个类名、函数名或常量名意外在不同库或应用程序不同部分中被使用的冲突

函数和类在第7章和第8章中已详细介绍。在此，你将查看 include()、require()、include_once() 和 require_once()，并学习如何使用它们来创建模块化、可复用的代码文件。你还将简要了解命名空间，并了解它们如何对大型项目有所帮助。

## 包含文件

如果你完成了前几章中的“试一试”示例，那么你可能已经熟悉 `include()`、`require()`、`include_once()` 和 `require_once()`。基本上，它们允许你将库文件中包含的代码包含在脚本文件内，就像代码已被复制并粘贴到脚本文件中一样。

下面是一个简单示例。假设你创建了一个名为 `animalSpeak()` 的简单函数，用于返回猫、狗或老鼠发出的声音：

```
function animalSpeak( $animal ) {
    $sounds = array ( "cat" => "meow", "dog" => "woof", "mouse" => "squeak" );

    if ( array_key_exists( $animal, $sounds ) ) {
        return $sounds[$animal];
    } else {
        return false;
    }
}

echo animalSpeak( "mouse" ) . "<br />"; // Displays "squeak"
echo animalSpeak( "cat" ) . "<br />"; // Displays "meow"
```

此处，函数和使用它的代码都包含在同一脚本文件中。这固然很好，但如果你想从另一个脚本或应用程序中调用 `animalSpeak()`，该怎么办？你不得不将定义 `animalSpeak()` 函数的代码从一个脚本复制粘贴到另一个脚本——显然不是最佳方法，因为你最终会得到重复的 `animalSpeak()` 版本。

这时，`include()` 函数就派上用场了。通过将 `animalSpeak()` 函数定义存储在单独的文件中，你可以使用 `include()` 从任意多个其他脚本文件中包含该函数。例如，你可以将其存储在名为 `animal_functions.php` 的文件中：

```
<?php

function animalSpeak( $animal ) {
    $sounds = array ( "cat" => "meow", "dog" => "woof", "mouse" => "squeak" );

    if ( array_key_exists( $animal, $sounds ) ) {
        return $sounds[$animal];
    } else {
        return false;
    }
}

?>
```

请注意，你需要将 `<?php` 和 `?>` 标签放在包含文件中的任何PHP代码周围。如果不这样做，包含的文件将被视为HTML标记，并直接发送到浏览器。

你可以如下从同一文件夹中的 `mouse.php` 脚本文件内使用该函数：

```
<?php
include ( "animal_functions.php" );
echo animalSpeak( "mouse" ) . "<br />"; // Displays "squeak";
?>
```

然后你可以在 `cat.php` 脚本文件内使用相同的函数：

```
<?php
include ( "animal_functions.php" );
echo animalSpeak( "cat" ) . "<br />"; // Displays "meow";
?>
```

与 include() 关系密切的是 require()，它的作用大致相同：

```
<?php
require ( "animal_functions.php" );
echo animalSpeak( "cat" ) . "<br />"; // Displays "meow";
?>
```

唯一的区别是，如果要包含的文件找不到，include() 仅会引发PHP警告，而 require() 则会引发致命错误并停止运行脚本。如果要包含对应用程序运行至关重要的库文件，请使用 require()。

## 仅包含文件一次

使用 include() 或 require() 包含文件的文件本身可以被包含在另一个文件中——这一过程称为嵌套包含。例如，先前的 `mouse.php` 和 `cat.php` 文件（它们本身包含 animal_functions.php 文件）可能会被包含在更高级别的 `display_animal_sounds.php` 脚本中，如下所示：

```
<?php
require ( "mouse.php" );
require ( "cat.php" );
?>
```

不过，运行此脚本会生成以下致命错误：

```
Cannot redeclare animalspeak() (previously declared in animal_functions
.php:3) in animal_functions.php on line 11
```

是什么导致了这个错误？首先，`display_animal_sounds.php` 包含 `mouse.php`。该文件反过来包含 `animal_functions.php`，从而定义了 `animalSpeak()` 函数。接下来，`display_animal_sounds.php` 包含 `cat.php`。该文件也包含 `animal_functions.php`，再次尝试定义 `animalSpeak()`。因为一个函数只能定义一次，所以会触发错误。

当你开始构建具有大量嵌套包含的大型应用程序时，这是一种非常常见的情况。要解决这个问题，请使用 PHP 的 `include_once()` 和 `require_once()` 函数。它们与各自的 `include()` 和 `require()` 对照物的工作方式相同，只是仅包含指定的文件

