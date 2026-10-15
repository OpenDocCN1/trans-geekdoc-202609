# PHP 常用语手册：必备代码和命令








![](img/1e6d362f187af50011d2666ddaa68739_0_0.png)

![](img/1e6d362f187af50011d2666ddaa68739_1_0.png)







































## 关于作者

克里斯蒂安·文茨（Christian Wenz）是一位专业的短语专家、作者、培训师和顾问，专注于 Web 技术。他撰写或合著了四十多本书。他经常为知名 IT 杂志撰稿，并在全球各地的会议上发表演讲。克里斯蒂安为 PEAR 仓库中的多个 PHP 包做出了贡献，还维护着一个 Perl CPAN 模块。他拥有慕尼黑工业大学（Technical University of Munich）的计算机科学学位（“Diploma”），在德国慕尼黑生活和工作。他还是德国首位 Zend 认证专家，并且是 PHP 安全联盟（PHP Security Consortium）的创始负责人。

## 期待您的反馈！

作为本书的读者，*您*是我们最重要的评论者和意见提供者。我们重视您的意见，想知道我们哪些方面做得好，哪些地方可以做得更好，您希望我们在哪些领域出版书籍，以及您愿意分享的任何其他真知灼见。

您可以直接给我发电子邮件或写信，让我知道您对这本书喜欢或不喜欢的方面，以及我们能做些什么让我们的书更出色。

*请注意，我无法帮助您解决与本书主题相关的技术问题，而且由于我收到的邮件数量很多，我可能无法回复每一条消息。*

写信时，请务必包含本书的书名和作者，以及您的姓名和电话或电子邮件地址。我会仔细审阅您的评论，并与参与本书工作的作者和编辑分享。

电子邮件：opensource@samspublishing.com
邮寄地址：马克·泰伯（Mark Taber）
协理出版人
Sams Publishing
800 East 96th Street
Indianapolis, IN 46240 USA

## 读者服务

要了解本书或 Sams 其他图书的更多信息，请访问我们的网站 www.samspublishing.com。在“搜索”字段中输入 ISBN（不含连字符）或书名，即可找到您要找的页面。

## 引言

不久前，我最喜欢的策划编辑达蒙·乔丹（Damon Jordan）给我发了一封电子邮件，结尾写道：“Ich möchte eine Föhnwelle”——“我想要一个吹风波浪。”遗憾的是，我不知道 Föhnwelle 或 blow wave 是什么，所以我婉拒了。他随后告诉我，这句话出自他最近买的一本德语常用语手册。

我产生了兴趣，于是翻阅了一些德语常用语手册。我认为它们是出国旅行时很有用的工具，尽管我个人觉得其中有些短语毫无意义。例如，在一本常用语手册中，我看到一系列搭讪语，包括那句精妙的“你拥有美丽的个性”——这句话无论用英语、德语还是任何其他语言，对我来说都不管用！有些性爱指导还可能带来其他问题——你要么在关键时刻记住该说的所有话，要么只能用空着的那只手拿着常用语手册。最后，再用一个短语：“吹风波浪已经像宠物石一样过时了。”

总之，我们聊了一会儿常用语手册，达蒙说他打算做一个关于常用语手册的系列丛书。他还提到想和他（也是我）最爱的选题编辑雪莉·约翰斯顿（Shelley Johnston）合作，于是我也加入了。

在构思这个概念的过程中，我们发现语言常用语手册和 IT 常用语手册之间存在一些差异。例如，语言常用语手册只是将同一句话在两种语言中对照呈现。

但这并不总是有用。如果你想稍微改动一下这个短语呢？比如，你想要的是一款时髦的“吹风波浪”（有人可能会说，这本身就是一个矛盾修饰法）。

因此，我们试图创建一个包含大量短语的概念，但每个短语都配有详尽的解释，以便读者轻松修改代码并使其适应自己的需求。当然，这会使得短语的“外语”部分比短语本身稍长一些，但我们认为在使用这本书时，这确实很有帮助。

我还记得一出著名的蒙提·派森（Monty Python）小品，里面有个人用了一本被动过手脚的词典，结果问路时反而挨了一顿揍。因此，真正理解短语背后的含义至关重要。

随后，我写了一个系列构想和一个样章。现在，仅仅几个月后，您手上拿着的正是这本常用语手册的第一本，希望这是一个系列的开端。

在阅读计算机书籍时，我非常讨厌的一种情况是，代码示例被草草塞进文字处理器，却从未经过测试。为了避免这种情况，书中每个代码清单都可以在 http://php.phrasebook.org/ 下载，而且对于超过几行的短语，文件名会包含在清单的标题中。因此，每一段代码都确实以文件形式存在，并且经过了实际测试，不像某些其他书籍。当然，说这本书 100% 无错误是一种幻想，尽管我们采取了多项措施来非常接近这一目标。任何已知的勘误也会发布在该网站上。

我对某些书的另一个非常不满的地方是，它们往往严重依赖特定操作系统，而这对于 PHP 来说是完全不必要的。有些书显然只在 Windows 下测试过，另一些则只在 Linux 下测试过，但完全可以让代码相对独立于平台。我们投入了大量精力在众多服务器平台上测试本书中的代码，包括 Linux、Windows、Mac OS X 和 Solaris。因此，本书的截图也来自这些平台，所以您会看到各种系统（和浏览器）的良好组合。意识形态可以用许多短语来表达，但在这本书中您不会找到任何这类内容。不过，如果某些内容确实只适用于特定平台（或 PHP 版本），文本中会加以说明。我保证，您在这本书中不会找到任何看起来像 foo、bar、baz 或任何其他想象力匮乏证明的东西。

当然，在这本书中很容易找到遗漏的短语——PHP 提供了如此丰富的功能，不可能涵盖所有方面。因此，我们不得不挑选一些感兴趣的主题——即与 PHP 程序员日常工作中相关的内容。然而，如果您认为有些内容确实被忽视了，请告诉我——但同时也请提名一个应当从本书后续版本中删掉的条目，以便为新的短语腾出空间。我期待听到您的反馈。

现在，让我再一次引用常用语手册中的一句话：“Bist du soweit? Da boxt der Papst”——“你准备好了吗？一切都将在那里发生”（但直译是：教皇在那里打拳）。

您专属的短语专家，
克里斯蒂安·文茨

## 操作字符串

在 PHP 支持的所有数据类型中，字符串可能是最常用的。原因之一是，在向客户端发送某些内容时，总是需要将某些内容表示为字符串。

PHP 提供了大量适用于字符串的函数，将近 100 个。此外，当需要在字符串中查找特定模式时，正则表达式也非常有用。然而，在实际生活中，这些函数中只有一小部分被真正使用。大多数函数都拥有自己忠实的粉丝群；但有些被低估的函数应该得到更多关注。本章中的代码短语很好地兼顾了这两个方面：既有标准应用，也有相当不寻常但非常实用的字符串处理方法。

### 比较字符串

```
strcmp($a, $b)
strcasecmp($a, $b)
```

比较字符串看起来是一项简单的任务——使用 == 运算符进行隐式类型转换（所以 '1' == 1 返回 true），或者使用 === 运算符进行类型检查（所以 '1' === 1 返回 false）。然而，第一种方法存在相当大的缺陷，因为类型转换并不总是会转为字符串。例如，1 == '1twothree' 也返回 true——这两个值都被转换为整数。因此，使用 === 才是正确的方式。

然而，PHP 还提供了一些函数，它们不仅仅是比较字符串并返回 true 或 false。实际上，当第一个参数传入的字符串大于第二个参数时，strcmp() 返回一个正值；当它小于第二个参数时，返回一个负值。如果两个字符串相等，strcmp() 返回 0。如果不需要区分大小写，可以使用 strcasecmp()。它的工作方式与 strcmp() 相同；但不会区分大写和小写字母。

```
<?php
$a = 'PHP';
$b = 'php';
echo 'strcmp(): ' . strcmp($a, $b) . '<br />';
echo 'strcasecmp(): ' . strcasecmp($a, $b);
?>
```

输出结果：

```
strcmp(): -1
strcasecmp(): 0
```

*比较字符串（compare.php）*




这两个函数可用于排序数组。有关自定义数组排序的更多信息，请参阅第 2 章“使用数组”。

### 检查用户名和密码

当验证用户名和密码时（例如，在支持 HTML 登录表单的脚本中），网络上似乎形成了事实上的标准：

- 密码始终区分大小写。必须以设置时完全相同的方式提供。
- 然而，用户名不区分大小写。

因此，用户名必须在不考虑大小写的情况下进行比较。这可以通过使用 strcasecmp()——参见上一段——或先将提供的用户名和真实用户名都转换为小写字母（或大写字母）来实现。这由函数 strtolower() 或 strtoupper() 完成。之前的代码展示了一个示例，使用 strcmp()/strcasecmp() 以及比较运算符 ===。

```php
<?php
$user = (isset($_GET['user'])) ? $_GET['user'] : '';
$pass = (isset($_GET['pass'])) ? $_GET['pass'] : '';

if (
    (strtolower($user) === 'damon' && $pass === 'secret') ||
    (strtoupper($user) === 'SHELLEY' && $pass === 'verysecret') ||
    (strcasecmp($user, 'Christian') == 0 &&
        strcmp($pass, 'topsecret') == 0)
) {
    echo 'Login successful.';
} else {
    echo 'Login failed.';
}
?>
```

*通过比较字符串验证登录 (comparelogin.php)*

根据对脚本调用的统一资源定位符（URL）中提供的数据，登录可能会失败或成功。例如，以下 URL 成功登录用户（你需要更改服务器名称部分）：

`http://servername/comparelogin.php?user=cHRISTIAN&pass=topsecret`

另一方面，以下登录则会失败：

`http://servername/comparelogin.php?user=Christian&pass=TopSecret`

> **NOTE**
> 当然，通过 GET 提供用户名和密码是非常糟糕的做法；建议使用 POST（有关表单数据的更多详细信息，请参阅第 4 章“与 Web 表单交互”）。然而，出于测试目的，本章的代码使用 GET。

### 将字符串转换为超文本标记语言（HTML）

```
htmlspecialchars($input)
htmlentities($input)
```

一种常用的网络攻击称为跨站脚本（XSS）。例如，用户在网页表单中输入一些恶意数据，例如 JavaScript 代码；网页随后在某处原样输出此信息，而未进行适当的转义。此类标准的示例是网络留言簿或讨论表单。人们输入文本供他人查看。

```php
<?php
    $input = '<script>alert("I have a bad Föhnwelle, ' .
        'therefore I crack websites.");</script>';

echo htmlspecialchars($input) . '<br />';
echo htmlentities($input);
?>
```

*转义字符串以用于 HTML (htmlescape.php)*

这里，重要的是要删除某些 HTML 标记。简单来说：几乎不可能真正捕获所有将 JavaScript 注入数据的尝试。它不仅总是使用 `<script>` 标签完成，还使用其他 HTML 元素，例如 `<img onerror="badCode()" />`。因此，在大多数情况下，必须删除所有 HTML。

最简单的方法是调用 `htmlspecialchars()`；这会将字符串转换为 HTML，包括将所有 `<` 和 `>` 字符替换为 `&lt;` 和 `&gt;`。另一个选项是调用 `htmlentities()`。这会为字符使用 HTML 实体（如果可用）。之前的代码展示了这两种方法之间的差异。德语 ö（o 分音符）不会被 `htmlspecialchars()` 转换；然而，`htmlentities()` 会将其替换为其实体 `&ouml;`。

使用 `htmlspecialchars()` 和 `htmlentities()` 只是在浏览器中输出用户输入的内容。因此，如果用户输入了 HTML 标记，则该标记本身会被显示。因此 `htmlspecialchars()` 和 `htmlentities()` 会让浏览器满意，但可能不会让用户满意。

> **NOTE**
> 然而，如果你想准备要在 URL 中使用的字符串，则必须使用 `urlencode()` 来正确编码特殊字符，例如可在 URL 中使用的空格字符。

然而，函数 `strip_tags()` 会完全去掉所有 HTML 元素。如果只想保留某些元素（例如，使用 `<b>`、`<i>` 和 `<br />` 标签的一些有限格式功能），则在 `strip_tags()` 的第二个参数中提供允许值的列表。以下脚本展示了这一点；图 1.1 描述了其输出。正如你所见，所有不需要的 HTML 标签已被删除；然而，其内容仍然存在。

![](img/1e6d362f187af50011d2666ddaa68739_22_0.png)

*图 1.1 一些 HTML 标签已被剥离，但并非全部。*

```php
<?php
$input = 'My parents <i>hate</i> me, <br />' .
    'therefore I <b>crack</b> websites. ' .
    '<script>alert("Nice try!");</script>' .
    '<img src="explicit.jpg" />';

echo strip_tags($input, '<b><br><i>');
?>
```

*删除所有 HTML 标签 (strip_tags.php)*

### 使用换行

在 HTML 中如何使用换行？很简单：使用 `<br />` HTML 元素。然而，如果数据中包含 `\n` 或 `\r\n` 换行符怎么办？可能会想到搜索和替换；然而，使用内置的 PHP 函数 `nl2br()` 要容易得多。这会解析字符串并将所有换行符转换为 `<br />` 元素，如前面的脚本所示。

```php
<?php
    $input = "One\nTwo\r\nThree";
    echo nl2br($input);
?>
```

输出 HTML：

```html
One<br />
Two<br />
Three
```

*在每个换行处添加 `<br />` 元素 (nl2br.php)*

正如你所见，换行符仍然存在，但 `<br />` 元素已被添加。

### 加密字符串

```
$encpass = '$1$FK3.qn2.$Si5KhnprsRb.N.SEF4GMW0'
```

密码绝不应以明文形式存储在数据库中，而应以加密方式存储。一些数据库内部提供加密；对于其他所有数据库，PHP 都可以提供帮助。`crypt()` 函数使用数据加密标准（DES）加密字符串。这是一种单向加密，因此无法回溯。此外，对 `crypt()` 的后续调用会产生不同的结果。

```php
<?php
    $pass = (isset($_GET['pass'])) ? $_GET['pass'] : '';
    $encpass = '$1$FK3.qn2.$Si5KhnprsRb.N.SEF4GMW0';
    if (crypt($pass, $encpass) === $encpass) {
        echo 'Login successful.';
    } else {
        echo 'Login failed.';
    }
?>
```

*使用加密密码检查登录 (crypt.php)*

例如，字符串 `TopSecret` 被加密为 `$1$FK3.qn2.$Si5KhnprsRb.N.SEF4GMW0`（也可能是 `$1$m61.1i2.$0p1J3EHwkIxycnyePp1Fz0` 和 `$1$9S3.c/3.$5101Bm4v3cnBN0b1AECi1..`，但本示例坚持使用第一个）。检查某个值是否对应于调用 `crypt()` 的结果可以通过再次调用 `crypt()` 来完成：`crypt($value, $encryptedValue)` 必须返回 `$encryptedValue`。

前面的脚本检查通过 URL 提供的密码是否与 `crypt()` 的先前结果匹配。使用 GET 参数 `pass=TopSecret` 调用此脚本会成功登录；所有其他密码都会失败。

> **NOTE**
>
> 为了提供更多详细信息：`crypt()` 的第二个参数是用于加密数据的盐（初始化值）。你也可以在加密原始密码时使用盐。然而，你必须确保盐值是唯一的——否则，加密就不安全。因此，不要使用自定义盐值，让 PHP 来完成工作。
>
> 同时请注意，DES 加密大约可以在 24 小时内被破解，因此它不再是万无一失的。更现代的替代方案是高级加密标准（AES）。

### 字符串校验和

```
md5()
sha1()
```

使用 `crypt()` 处理字符串类似于为某物创建校验和：可以很容易地确定字符串是否与校验和匹配；然而，从校验和重新创建原始字符串是不可能的（或不容易）。

```php
<?php
    $pass = (isset($_GET['pass'])) ? $_GET['pass'] :
        '';

    $md5pass = '6958b43cb096e036f872d65d6a4dc01b';
    $sha1pass = '61c2feed11e0e53eb8e295ab8da78150be12f301';

    if (sha1($pass) === $sha1pass) {
        echo 'Login successful.';
    } else {
        echo 'Login failed.';
    }

    // Alternatively, using MD5:
    // if (md5($pass) === $md5pass) {
    //     echo 'Login successful.';
    // } else {
    //     echo 'Login failed.';
    // }
?>
```

*使用 SHA1 和 MD5 哈希检查登录 (checksum.php)*

两个专门用于执行此校验和的算法是安全哈希算法 1（SHA1）

以及消息摘要算法5（MD5）。它们会生成这样的校验和，即哈希。这两种算法与DES/crypt()所用算法的主要区别在于：字符串的SHA1或MD5校验和始终是相同的，因此验证数据非常容易。如图1.2所示，就连PHP发行版也在网站上提供了MD5校验和，用于验证下载文件。

![](img/1e6d362f187af50011d2666ddaa68739_26_0.png)

图1.2 PHP下载页面显示了PHP发行版的MD5哈希值。

在这里，目标仍然是验证用户通过GET提供的密码。正确的密码依旧是'TopSecret'，其哈希值如下：

- 6958b43cb096e036f872d65d6a4dc01b 是 MD5 哈希值
- 61c2feed11e0e53eb8e295ab8da78150be12f301 是 SHA1 哈希值

### 计算字符串校验和

> 在计算文件的MD5或SHA1哈希值时，无需调用 file_get_contents() 或其他文件函数；PHP提供了两个函数来计算文件的哈希值（并负责打开和读取文件数据）：
> 
> - md5_file()
> - sha1_file()

### 提取子字符串

substr() 函数返回字符串的一部分。你需要提供一个字符串以及要提取的第一个字符的位置（请记住，第一个字符的索引为0）。从该字符开始，将返回字符串的其余部分。如果只想返回其中一部分，可在第三个参数中指定长度。前面的代码演示了 substr() 的用法，从 PHP: Hypertext Preprocessor 中提取出 Prep。

```php
<?php
$php = "PHP: Hypertext Preprocessor";
echo substr($php, 15, 4); //returns "Prep"
?>
```

*使用 substr() 提取子字符串（substr.php；节选）*

> 提示
> 
> 如果想从字符串末尾开始计数，可以将 substr() 的第二个参数设置为负值：
> 
> echo substr($php, -12, 4);
> 
> 如果为 substr() 的第三个参数提供负值，例如 -n，则最后 n 个字符不包含在子字符串中。
> 
> echo substr($php, -12, -8);
> 
> 所有这些 substr() 调用都返回 Prep，并包含在完整代码中。

### 使用ASCII码保护电子邮件地址

### protectMail('email@address.xy')

在浏览器中，你只会看到一个电子邮件链接；但其底层的HTML标记是难以解读的：

```
<a href="&#109;&#97;&#105;&#108;&#116;&#111;&#58;&#101;&#109;&#97;&#105;&#108;&#64;&#97;&#100;&#100;&#114;&#101;&#115;&#115;&#46;&#120;&#121;">Send mail</a>
```

```php
<?php
function protectMail($s) {
  $result = '';
  $s = 'mailto:' . $s;
  for ($i = 0; $i < strlen($s); $i++) {
    $result .= '&#' . ord(substr($s, $i, 1)) . ';';
  }
  return $result;
}
```

### 使用ASCII码保护电子邮件地址

```
echo '<a href="' .
    protectMail('email@address.xy') .
    '">Send mail</a>';
?>
```

*保护电子邮件地址（protectMail.php）*

然而，请看图1.3：网络浏览器正确解码了电子邮件地址，从状态栏中可以看到。

![](img/1e6d362f187af50011d2666ddaa68739_29_0.png)

图1.3 机器胜过人类（在解密电子邮件地址时）。

有些特殊字符很难用在字符串中，因为用键盘很难输入。但是，它们都有对应的ASCII值。PHP提供了两个函数来处理这种情况：

- `chr()` 将ASCII码转换为相应的字符
- `ord()` 返回一个字符的ASCII码

### 使用ASCII码保护电子邮件地址

例如，这可用于保护电子邮件地址。由于垃圾邮件发送者会编写软件来搜索网页上的特定模式（电子邮件地址），这样做可能有助于减少垃圾邮件。诀窍是为电子邮件地址使用HTML字符代码，使垃圾邮件机器人更难以找到电子邮件数据。

前面的代码将一个电子邮件地址（格式为 email@address.xy）作为参数，返回 mailto:email@address.xy —— 但会转换为HTML实体。例如，mailto: 中的 m 的ASCII码是109，因此 &#109; 表示 m。为此，需要使用 for 循环遍历字符串中的所有字符。要这样做，必须先确定字符串的长度，这可以使用 strlen() 完成。然后，调用 ord() 计算每个字符的ASCII码，并将其用于生成的HTML。

当然，这并不能提供万无一失的保护；你可以考虑使用其他方式来隐藏电子邮件地址，例如使用 email at address dot xy 这样的语法。

### 同时打印字符串、变量和表达式

使用双引号，可以轻松打印字符串和变量的混合内容。但是，当还想使用函数调用等表达式时，标准做法是使用大量的字符串连接：

```
echo 'The length of the string is ' . strlen($s) . '!' ;
```

当涉及多个表达式时，这显然会变得相当复杂。

下面展示了 printf() 如何使代码更易读一些：

```php
<?php
$a = 'PHP';
$b = 'php';
printf('strcmp(): %d<br />strcasecmp(): %d',
    strcmp($a, $b), strcasecmp($a, $b));
?>
```

PHP还支持几个与 printf() 相关的函数：

- sprintf() 的工作方式与 printf() 类似，但会返回字符串，而不是打印它。
- vprintf() 的工作方式与 printf() 类似，但期望字符串中占位符的值以数组形式提供。
- vsprintf() 是 sprintf() 和 vprintf() 的混合体：占位符值以数组形式提供，函数返回字符串但不打印。

### 扫描格式化字符串

```
sscanf($date, '%d/%d/%d')
```

另一个与 printf() 相关的函数是 sscanf()。它会解析一个字符串，并尝试将其与包含占位符的模式进行匹配。$input 字符串包含一个日期，并使用包含多个占位符的字符串 '%d-%d-%d' 进行扫描，如前面的代码所示。该函数返回一个数组，其中包含所有匹配的占位符的值。然后将该数组传递给 vprintf() 进行打印。

### 扫描格式化字符串

```php
<?php
$date = '02/01/06';
$values = sscanf($date, '%d/%d/%d');
vprintf('Month: %d; Day: %d; Year: %d.', $values);
?>
```

*扫描格式化字符串（sscanf.php）*

或者，你可以向 sscanf() 提供一系列变量名作为附加参数。然后，该函数会将与占位符匹配的子字符串写入这些变量。下面的代码演示了这一点：

```php
<?php
$date = '02/01/06';
$values = sscanf($date, '%d/%d/%d', $m, $d, $y);
echo "Month: $m; Day: $d; Year: $y.";
?>
```

*扫描格式化字符串（sscanf-alternative.php）*

### 获取关于变量的详细信息

```
var_dump(false);
```

变量的值可以使用 print() 或 echo() 发送到客户端；但有时这样做会有问题。以布尔值为例，echo(true) 会打印 1，而 echo(false) 不打印任何内容。更好的方法是使用 var_dump()，这个函数还会打印变量的类型。因此，上述代码返回字符串 bool(false)。

这对于对象和数组也同样适用，因此 var_dump() 是喜欢在没有调试器的情况下进行调试的开发人员的必备选择。

### 注意

一个与 var_dump() 相关的函数是 var_export()。它的工作方式类似，但有两个不同点：

- var_export() 的返回值是 PHP 代码；例如，var_export(false) 返回 false。
- 如果提供给 var_export() 的第二个参数为布尔值 true，则该函数不会打印任何内容，而是返回一个字符串。

### 在字符串中搜索

```php
if (strpos($string, $substring) === false) {
    echo 'No match found.';
} else {
    echo 'Match found.';
}
```

在字符串中查找子字符串时，会使用 strpos()（以及对应的 strrpos()，它从字符串末尾开始搜索）。这个函数的棘手之处在于，它返回子字符串第一次出现的索引，否则返回 false。这意味着前面的代码片段是不正确的。

前面的代码片段不正确，因为如果 $string 恰好以 $substring 开头，strpos() 会返回 0，而 0 被判定为 false。因此，必须使用 === 或 !== 进行比较来获取数据

请考虑。 这句话开头的代码展示了如何正确使用 `strpos()`。

### 理解正则表达式

正则表达式简单来说，是可以与字符串匹配的模式。PHP 中有两种正则表达式——POSIX 正则表达式和 PCRE 正则表达式。前者可以在使用开关 `--with-regex` 配置 PHP 时安装。Windows 用户无需这样做；POSIX Regex 的支持默认已启用。

另一种选择是 Perl 兼容正则表达式（PCRE）。PCRE 通常被认为更快，并且提供更多功能。此功能在 PHP 中默认启用；但是，如果你自行编译 PHP，可以使用开关 `--without-pcre-regex` 禁用 PCRE。

正则表达式中的模式包含可在较大字符串中搜索的字符串。然而，这也可以（更快地）使用 `strpos()` 来完成。正则表达式的优点是提供了一些特殊功能，例如通配符。表 1.2 显示了一些特殊字符及其含义。

表 1.2 正则表达式中的特殊字符

| 特殊字符 | 描述 | 示例 |
|---|---|---|
| ^ | 字符串开头 | ^a 表示以 a 开头的字符串 |

### 表 1.2 继续

| 特殊字符 | 描述 | 示例 |
|---|---|---|
| $ | 字符串结尾 | a$ 表示以 a 结尾的字符串 |
| ? | 0 或 1 次（指前一个字符或表达式） | ab? 表示 a 或 ab |
| * | 0 或多次（指前一个字符或表达式） | ab* 表示 a 或 ab 或 abb 或 ... |
| + | 1 或多次（指前一个字符或表达式） | ab+ 表示 ab 或 abb 或 abbb 或 ... |
| [...] | 替代字符 | PHP[45] 表示 PHP4 或 PHP5 |
| - (用于方括号内) | 值序列 | PHP[3-5] 表示 PHP3 或 PHP4 或 PHP5 |
| ^ (用于方括号内) | 匹配除以下字符外的任何内容 | [^A-C] 表示 D 或 E 或 F 或 ... |
| \| | 替代模式 | PHP4|PHP5 表示 PHP4 或 PHP5 |
| (...) | 定义子模式 | (a)(b) 表示 ab，但包含两个子模式（a 和 b） |

### 在字符串中搜索

表 1.2 继续

| 特殊字符 | 描述 | 示例 |
|---|---|---|
| . | 任意字符 | . 表示 a、b、c、0、1、2、$、^、... |
| {min, max} | 最小和最大出现次数；如果省略 min 或 max，则表示 0 或无限 | a{1,3} 表示 a、aa 或 aaa。 a{,3} 表示空字符串、a、aa 或 aaa。 a{1,} 表示 a、aaa、aaa、... |
| \ | 转义下一个字符 | \. 代表 . |

> **TIP**
>
> 正则表达式的事实标准参考是 Jeffrey E. F. Friedl 所著的 *Mastering Regular Expressions*。有点过时，但读起来很有趣。

其他特殊字符和表达式也可用，例如指代数字的字符。然而，这在 POSIX 和 PCRE 之间有所不同，它们在示例中分别使用 [:digit:] 和 \d。

### 使用 POSIX 正则表达式

使用 POSIX 正则表达式搜索匹配是通过 ereg() 函数完成的。你提供一个模式、要搜索的字符串，以及一个变量名，该

### 验证电子邮件地址

检查字符串是否包含有效的电子邮件地址同时具有两个特点：非常常见且非常复杂。前述关于正则表达式的书籍用了几页篇幅来创建一套正则表达式来执行此任务。如果你对此感兴趣，请查看 http://examples.oreilly.com/regex/readme.html。

```
function checkEmail($s) {
  $lastDot = strrpos($s, '.');
  $ampersand = strrpos($s, '@');
  $length = strlen($s);
  return !(
    $lastDot === false ||
    $ampersand === false ||
    $length === false ||
    $lastDot - $ampersand < 3 ||
    $length - $lastDot < 3
  );
}
```

*验证电子邮件地址 (check.inc.php; 摘录)*

验证电子邮件地址很困难，因为不同国家对有效域名名的规则差异很大。例如，bn.com 是有效的，而 bn.de 不是（但 db.de 是）。此外，你知道 username@[127.0.0.1] 是一个有效的电子邮件地址吗（如果 127.0.0.1 是邮件服务器的 IP 地址）？

因此，建议仅检查电子邮件地址的主要元素：有效字符（@ 字符）以及其后某处的点。检查电子邮件地址不可能 100% 确定——如果测试过于严格，用户只需提供一个虚构的电子邮件地址。电子邮件检查的唯一目的是在发生（非故意）拼写错误时提供帮助。

当然，这也可以使用正则表达式完成，但可能只是更慢。你还应该注意，前述代码无法检测到所有不正确的电子邮件地址。还要注意包含特殊字符（如 ä 或 é）的新国际域名。大多数正则表达式省略了这些，因此使用前述代码要好得多。

### 搜索和替换

```
POSIX:
  ereg_replace()
PCRE:
  preg_replace()
```

在字符串中搜索是一回事；用其他内容替换所有出现的内容则完全不同。使用正则表达式，这相对容易；你只需要知道相应的函数名称：

- 对于 POSIX，使用 `ereg_replace()` 和 `eregi_replace()`
- 对于 PCRE，使用 `preg_replace()`

```
POSIX:
<?php
$string = '02/01/06';
echo ereg_replace(
'([0-9][0-9]?)/([0-9][0-9]?)/([0-9][0-9]?)',
'\\2/\\1/\\3',
$string
);
?>
```

```
PCRE:
<?php
    $string = '02/01/06';
    echo preg_replace(
        '#(\d{1,2})/(\d{1,2})/(\d{1,2})#',
        '$2/$1/$3',
        $string
    );
?>
```

*使用 POSIX (ereg_replace.php) 和 PCRE (preg_replace.php) 替换匹配项*

在替换项的正则表达式中，你可以使用对子模式的引用。完整匹配在 POSIX 中用 \0 表示，在 PCRE 中用 $0 表示。然后从内到外、从左到右计数括号：第一个括号的内容由 \1 或 $1 引用，第二个括号的内容使用 \2 或 $2 访问，以此类推。

考虑到这一点，可以进行替换。在示例中，美国日期（月/日/年）被转换为英国日期（日/月/年）。

**TIP**
前述代码中的正则表达式未使用 / 作为正则表达式的分隔符，因为正则表达式本身包含斜杠，这些斜杠随后需要转义。然而，通过选择另一个分隔符（例如：#），可以避免转义斜杠。

如果你有一个静态模式，没有任何量词或特殊字符，使用 str_replace() 几乎总是更快。其参数顺序为：首先是要搜索的字符串（或字符串）；然后是替换内容（或内容）；最后是执行搜索和替换的字符串。
你可以在前两个参数中提供字符串或字符串数组。以下代码从文本中删除所有标点符号。

```
<?php
$string = 'To be, or not to be; that\'s the question?!';
echo str_replace(
    array('.', ',', ':', ';', '!', '?'),
    '',
    $string
);
?>
```

*不使用正则表达式进行替换 (str_replace.php)*

### 使用数组

当简单变量不够好时，数组就派上用场了（或对象，但那是另一个话题）。PHP 手册中可用的数组部分，网址为 http://php.net/array，列出了大约 80 个有用的函数。因此，这本书仅用与数组相关的短语就可以填满。然而，并非所有这些函数都经常使用。因此，本章介绍了在使用数组时你需要解决的最重要问题——当然，还有这些问题的解决方案。

有两种类型的数组。它们的名称有时不同，但通常数组分为数值数组和关联数组。第一类数组使用数值键，而后一类数组也可以使用字符串作为键。

创建数组可以通过以下两种方式之一完成：

- 使用 array() 函数

```
$a = array('I', 'II', 'III', 'IV');
```



### 使用数组
- 连续使用变量名和方括号向数组添加值

```
$a[] = 'I';
$a[] = 'II';
$a[] = 'III';
$a[] = 'IV';
```

使用关联数组时，同样可以使用这两种方法；不过这次必须提供键和值：

```
$a1 = array('one' => 'I', 'two' => 'II', 'three' =>
    'III', 'four' => 'IV');
$a2['one'] = 'I';
$a2['two'] = 'II';
$a2['three'] = 'III';
$a2['four'] = 'IV';
```

数组也可以嵌套，当数组元素本身就是一个数组时：

```
$a = array(
    'Roman' =>
        array('one' => 'I', 'two' => 'II', 'three' =>
            'III', 'four' => 'IV'),
    'Arabic' =>
        array('one' => '1', 'two' => '2', 'three' =>
            '3', 'four' => '4')
);
```

现在，可以使用 $a['Arabic']['four'] 访问数字四的阿拉伯语表示。

当然，数组不仅可以在脚本中创建，还可以来自其他来源，包括来自 HTML 表单（参见第 4 章，“与 Web 表单交互”）以及 cookie 和会话（参见第 5 章，“记住用户（Cookie 和会话）”）。但如果数组已经存在，下一步是什么？以下内容提供了一些提示。

### 访问数值数组的所有元素

```
array('I', 'II', 'III', 'IV');
```

使用 foreach 遍历数值数组是最简单的方法，因为在循环的每次迭代中，数组中的当前元素会自动写入一个变量。

```
<?php
$a = array('I', 'II', 'III', 'IV');
foreach ($a as $element) {
    echo htmlspecialchars($element) . '<br />';
}
?>
```

*使用 foreach 遍历数组 (foreach-n.php)*

另外，也可以使用 for 循环。第一个数组元素的索引为 0；可以使用 count() 函数获取数组索引的数量。

```
<?php
$a = array('I', 'II', 'III', 'IV');
for ($i = 0; $i < count($a); $i++) {
    echo htmlspecialchars($a[$i]) . '<br />';
}
?>
```

*使用 for 遍历数组 (for-n.php)*

两种方法都同样好（或不好）；不过，通常使用 foreach 要方便得多。然而还有第三种可能性：PHP 函数

each() 返回数组中的当前元素。each() 的返回值是一个数组，其中可以使用数值索引 1 或字符串索引 'value' 访问值。使用 while 循环，可以遍历整个数组。以下代码再次打印数组中的所有元素，这次使用 each()。

```
<?php
$a = array('I', 'II', 'III', 'IV');
while ($element = each($a)) {
    echo htmlspecialchars($element['value']) .
        '<br />'; //or: $element[1]
}
?>
```

*使用 each() 遍历数组 (each-n.php)*

当然，这三个列表的输出始终相同。

### 访问关联数组的所有元素

```
foreach ($array as $key => $value) {
```

使用关联数组并希望访问其中的所有数据时，键也很重要。为此，foreach 循环必须为元素的键提供变量名，而不仅仅是其值。

```
<?php
$array = array('one' => 'I', 'two' => 'II', 'three' => 'III', 'four' => 'IV');
foreach ($array as $key => $value) {
```

```
<?php
foreach ($array as $key => $value) {
    echo htmlspecialchars("$key: $value") . '<br />';
}
?>
```

*使用 foreach 遍历关联数组 (foreach-a.php)*

使用 count() 是可行的：count() 返回数组中值的数量，而不是元素的数量。使用 for 遍历所有数组元素是不可行的。然而，可以使用 each() 和 while 的组合，如以下代码所示。重要的是，键名可以使用索引 0 或字符串索引 'key' 获取。

```
<?php
$a = array('one' => 'I', 'two' => 'II', 'three' =>
    'III', 'four' => 'IV');
while ($element = each($a)) {
    echo htmlspecialchars($element['key'] . ': ' .
        $element['value']) . '<br />';
    //or: $element[0] / $element[1]
}
?>
```

*使用 each() 遍历数组 (each-a.php)*

### 访问嵌套数组中的所有数组元素

```
<?php
print_r($a);
?>
```

使用 print_r() 可以非常轻松地打印嵌套数组。查看图 2.1 中列表的输出。

```
<pre>
<?php
$a = array(
    'Roman' =>
        array('one' => 'I', 'two' => 'II', 'three' =>
            'III', 'four' => 'IV'),
    'Arabic' =>
        array('one' => '1', 'two' => '2', 'three' =>
            '3', 'four' => '4')
);
print_r($a);
?>
</pre>
```

使用 print_r() 打印嵌套数组 (print_r.php)

![](img/1e6d362f187af50011d2666ddaa68739_47_0.png)

图 2.1 使用 print_r() 打印数组内容。

### 提示
如果将 print_r() 的第二个参数设置为 true，数组的内容不会发送给客户端，而是从函数返回，这样你就可以将此信息保存到变量中并进一步处理。

然而，前述代码的输出几乎只能用于调试目的（参见图 2.1）。因此，必须找到一种巧妙的方式来访问所有数据。递归函数是一种合理的方法来实现这一点。在此，所有数组元素都会被打印出来；整个输出使用 HTML 元素 <blockquote> 进行缩进。然而，如果数组元素的值本身就是一个数组，函数会递归调用自身，从而导致额外的缩进级别。是否是一个数组可以使用 PHP 函数 is_array() 来确定。利用这一点，可以组装以下代码。结果请参见图 2.2。

```
<?php
function printNestedArray($a) {
    echo '<blockquote>';
    foreach ($a as $key => $value) {
        echo htmlspecialchars("$key: ");
        if (is_array($value)) {
            printNestedArray($value);
        } else {
            echo htmlspecialchars($value) . '<br />';
        }
    }
    echo '</blockquote>';
}
```

```
$arr = array(
    'Roman' =>
        array('one' => 'I', 'two' => 'II', 'three' =>
        'III', 'four' => 'IV'),
    'Arabic' =>
        array('one' => '1', 'two' => '2', 'three' =>
        '3', 'four' => '4')
);

printNestedArray($arr);
?>
```

使用递归函数打印嵌套数组
(printNestedArray.php)

![](img/1e6d362f187af50011d2666ddaa68739_49_0.png)

图 2.2 使用递归函数打印数组内容。

### 将数组转换为变量

```
while (list($key, $value) = each($a))
```

每当使用 each() 时，使用 list() 是一个好主意。在 list() 中，你为 each() 返回的数组中所有具有数值索引的值提供变量名。这使得 while/each() 循环更容易使用，正如代码所示。在括号内提供变量名。

```
<?php
$a = array('one' => 'I', 'two' => 'II', 'three' =>
    'III', 'four' => 'IV');
while (list($key, $value) = each($a)) {
    echo htmlspecialchars("$key: $value") . '<br />';
}
?>
```

*使用 list() 和 each() 遍历数组 (each-list.php)*

### 提示
如果你只对数组的键或值感兴趣，可以删除其中一个变量；只要确保保留逗号。

```
while (list(, $value) = each($a)) {
    echo htmlspecialchars("$value") .
        '<br />';
}
```

### 将字符串转换为数组

```
$a = explode(',', $csvdata);
```

有时，并不使用数组来存储信息；而是使用字符串。单个值都包含在字符串中，但由特殊字符分隔。逗号分隔值（CSV）格式就是一个例子。

```
<?php
  $csvdata = 'Sams Publishing,800 East 96th Street,Indianapolis,Indiana,46240';
  $a = explode(',', $csvdata);
  $info = print_r($a, true);
  echo "<pre>$info</pre>";
?>
```

*将字符串转换为数组 (explode.php)*

PHP 函数 explode() 从这些值创建数组；你只需要提供字符串需要拆分的字符。浏览器然后显示此输出：

```
Array
(
    [0] => Sams Publishing
    [1] => 800 East 96th Street
    [2] => Indianapolis
    [3] => Indiana
    [4] => 46240
)
```

### 将数组转换为字符串

```
$address = implode('<br />', $data);
```

回去的方式（即从数组中的元素制作字符串表示）可以使用 implode() 完成。同样需要两个参数：分隔元素，然后是数组。顺序相当不寻常，但很重要。

因此，PHP 使用 <br /> HTML 元素连接数组的元素。因此，在浏览器中，每个数组的元素保持在自己的行上。



```php
<?php
$data = array(
    'Sams Publishing',
    '800 East 96th Street',
    'Indianapolis',
    'Indiana',
    '46240'
);
$address = implode('<br />', $data);
echo $address;
?>
```

*将数组转换为字符串 (implode.php)*

### 按字母顺序对数组进行排序

```php
sort($a, SORT_NUMERIC);
sort($a, SORT_STRING);
```

数值数组可以使用 `sort()` 相对容易地进行排序。然而，如果数组同时包含数值和字符串值（例如，"2" > "10" 但 2 < 10）就会出现问题。因此，可以调整排序方式，以便在排序时使用特殊的数据类型来比较元素：

- `SORT_NUMERIC` 将元素作为数字排序
- `SORT_REGULAR` 根据数据类型对元素进行排序（标准行为）
- `SORT_STRING` 将元素作为字符串排序

```php
<pre>
<?php
$a = array('4', 31, '222', 1345);
sort($a, SORT_NUMERIC);
print_r($a);
sort($a, SORT_STRING);
print_r($a);
?>
</pre>
```

### 对数组进行排序 (sort.php)

前述列表的输出如下：

```
Array
(
    [0] => 4
    [1] => 31
    [2] => 222
    [3] => 1345
)
Array
(
    [0] => 1345
    [1] => 222
    [2] => 31
    [3] => 4
)
```

**注意**
如果你想按相反顺序对数组元素进行排序，请使用 rsort()（r 代表 reverse，反向）。可以使用与 sort() 相同的可选第二个参数。

### 按字母顺序对关联数组进行排序

```php
ksort($a);
asort($a);
```

对关联数组的排序可以有几种方式进行：

- 按键排序，保持键值关联不变：使用 ksort()。
- 按键逆序排序，保持键值关联不变：使用 krsort()。
- 按值排序，保持键值关联不变：使用 asort()。
- 按值逆序排序，保持键值关联不变：使用 arsort()。

```php
<pre>
<?php
$a = array('one' => 'I', 'two' => 'II', 'three' =>
    'III', 'four' => 'IV');
ksort($a);
print_r($a);
asort($a);
print_r($a);
?>
</pre>
```

*对关联数组进行排序 (sort_a.php)*

前述代码展示了这些函数的使用情况；图 2.3 显示了结果。

### 对嵌套数组进行排序

![](img/1e6d362f187af50011d2666ddaa68739_55_0.png)

Figure 2.3 对关联数组进行排序。

> 注意
> 尝试使用 sort() 或 rsort() 对关联数组进行操作是可行的——但键将会全部丢失。

### 对嵌套数组进行排序

```php
function sortNestedArray(&$a) {
    sort($a);
    for ($i = 0; $i < count($a); $i++) {
        if (is_array($a[$i])) {
            sortNestedArray($a[$i]);
        }
    }
}
```

PHP 的标准排序函数在处理嵌套数组时会失效。然而，如果使用递归函数，你可以用几行代码实现这一点。

目标是对嵌套数组进行排序，但它仅由数值子数组组成，因此只使用数值（因此无用）的键。

![](img/1e6d362f187af50011d2666ddaa68739_57_0.png)

Figure 2.4 对嵌套数组进行排序。

### 对嵌套关联数组进行排序

```php
foreach ($a as $key => $value) {
    if (is_array($value)) {
        sortNestedArrayAssoc($value);
    }
}
```

如果要对关联嵌套数组进行排序，与之前对数值（但嵌套）数组进行排序的段落相比，必须改变两点。首先，数组必须使用 ksort() 而不是 sort() 进行排序。此外，递归排序必须应用于正确的变量，即本身是数组的数组元素。确保它通过引用传递，以便更改能反映回值。

### 对嵌套关联数组进行排序

```php
<pre>
<?php
    function sortNestedArrayAssoc($a) {
        ksort($a);
        foreach ($a as $key => $value) {
            if (is_array($value)) {
                sortNestedArrayAssoc($value);
            }
        }
    }

$arr = array(
    'Roman' =>
        array('one' => 'I', 'two' => 'II', 'three' =>
            'III', 'four' => 'IV'),
    'Arabic' =>
        array('one' => '1', 'two' => '2', 'three' =>
            '3', 'four' => '4')
);
    sortNestedArrayAssoc(&$arr);
    print_r($arr);
?>
</pre>
```

使用递归函数对嵌套关联数组进行排序 (sortNestedArrayAssoc.php)

图 2.5 显示了本段开头代码的结果。

### 按人类方式对 IP 地址进行排序

![](img/1e6d362f187af50011d2666ddaa68739_59_0.png)

Figure 2.5 对嵌套关联数组进行排序。

### 按人类方式对 IP 地址进行排序

```php
natsort($a);
```

使用 sort() 对 IP 地址进行排序并不真正有效，因为如果按字符串排序，'100.200.300.400' 小于 '50.60.70.80'（而且这甚至不是一个有效的 IP 地址，但这不是重点）。此外，字符串中不仅仅包含数字，因此数值排序也不起作用。

```php
<?php
$a = array('100.200.300.400', '100.50.60.70',
    '100.8.9.0');
natsort($a);
echo implode(' < ', $a);
?>
```

*使用自然顺序字符串比较对 IP 地址进行排序 (natsort.php)*

在这种情况下需要的是所谓的自然排序，这是由 Martin Pool 的 Natural Order String Comparison 项目在 http://sourcefrog.net/projects/natsort/ 实现的。在 PHP 的 natcasesort() 函数中使用了该算法。根据描述，它按“人类方式”排序。当区分大小写时，可以使用 natsort()。前述代码展示了后者函数。

注意
内部，natsort() 使用 strnatcmp()（而 natcasesort() 使用 strnatcasecmp()），它对两个字符串进行“自然”比较。通过多次调用此函数，数组元素会被排列到正确顺序。

### 对任何内容进行排序

```php
function compare($a, $b) {
    return $a - $b;
}

$a = array(4, 1345, 31, 222);
usort($a, 'compare');
echo implode(' < ', $a);
```

### 对任何内容进行排序

如果你不想局限于 PHP 提供的标准排序功能，你可以编写自己的排序算法。内部，PHP 使用 Quicksort 算法对数组中的值进行排序。为此，PHP 必须知道两个值是否相等；在后一种情况下，PHP 需要找出哪个值更大。因此，要实现自定义排序，只需要一个接受两个参数并返回的函数：

- 如果第一个参数小于第二个参数，则返回负值
- 如果两个参数相等，则返回 0
- 如果第二个参数小于第一个参数，则返回正值

此函数的名称必须作为字符串传递给 usort()！其余工作由 PHP 完成，如代码所示。那里使用的比较函数是一种非常简单的数值排序方法。通过减去两个值，函数返回所需的值：如果第一个参数大于第二个参数，则返回正数，如果两个参数相等则返回 0，否则返回负数。

> **注意**
> Quicksort 算法是排序元素最快的算法之一。对 n 个元素进行排序时，最多使用 n² 次比较；然而，平均只需要 n log n 次比较，使其非常快速。Quicksort 使用分而治之的策略：它将问题拆分为几个较小的子问题，可以递归解决。有关该算法的更多信息可在 http://en.wikipedia.org/wiki/Quicksort 找到。

### 使用外语进行排序

对于这种特殊情况，PHP 没有特殊的排序方法；然而，你可以使用 strnatcmp() 来模拟此行为。其思想是为某些特殊字符定义新的顺序；在比较函数中，你然后使用它来确定哪个字符“更大”，哪个字符“更小”。

你首先需要一个可以对单个字符进行排序的函数：

```php
function compareChar($a, $b) {
    $characters = 'AAÀÁÄBCÇDEÉÈFGHIÌÍJKLMNOÒÖÓPQRSTUÙÜÚVWXYZ';
    $characters .= 'aaàáäbcçdeèéfghiìíjklmnoòöópqrstuùüúvwxyz';
    $pos_a = strpos($characters, $a);
    $pos_b = strpos($characters, $b);
    if ($pos_a === false) {
        if ($pos_b === false) {
            return 0;
        } else {
            return 1;
        }
    } elseif ($pos_b === false) {
        return -1;
    } else {
        return $pos_a - $pos_b;
    }
}
```

然后，主排序函数逐字符调用 compareChar()，直到找到差异为止。如果没有找到差异，则较长的字符串被认为是“更大”的一个。如果两个字符串完全相同，则返回 0。本段开头的代码展示了 compare 函数。该代码的结果如预期，Frans < Frédéric < Froni。




### 将效果应用于所有数组元素

```
$a = array_map('sanitize', $a);
```

有时，数组中的数据在使用前必须进行预处理。在第4章中，你将看到如何对通过HTML表单来自用户的数据在使用前进行净化。为此，必须处理每个数组元素。

```php
<?php
function sanitize($s) {
    return htmlspecialchars($s);
}

$a = array('harmless', '<bad>', '>>click here!<<');
$a = array_map('sanitize', $a);
echo implode(' ', $a);
?>
```

*将htmlspecialchars()应用于数组的所有元素（array_map.php）*

然而，你并不需要编写繁琐的for/foreach/while循环；PHP为此提供了内置功能。第一种可能是使用array_map()。它接受一个数组（第二个参数），并将该数组中的每个元素提交给一个回调函数（第一个参数，以字符串形式传递）。最后返回数组，所有元素都被回调函数的相关返回值替换。

在前面的列表中，数组中的所有值都使用htmlspecialchars()转换为HTML。

但是，如果数组是嵌套的，策略就必须稍作改变。这时可以使用递归函数。如果数组元素是字符串，则进行HTML编码。如果是数组，则递归函数对该数组调用自身。以下代码实现了这一点，图2.6显示了结果。

```php
<?php
function sanitize_recursive($s) {
	if (is_array($s)) {
		return(array_map('sanitize_recursive', $s));
	} else {
		return htmlspecialchars($s);
	}
}

$a = array(
	'harmless' =>
		array('no', 'problem'),
	'harmful' =>
		array('<bad>', '--> <worse> <--')
	);

$a = sanitize_recursive($a);

echo '<pre>' . print_r($a, true) . '</pre>';
?>
```

递归地将htmlspecialchars()应用于嵌套数组的所有元素（array_map_recursive.php）

![](img/1e6d362f187af50011d2666ddaa68739_66_0.png)

图2.6 嵌套数组已经被HTML编码。

另一个行为类似的函数是array_walk()。它也将一个函数应用于数组的每个元素；不过，它还允许你为此函数调用提供一个参数。在以下代码中，这被用来打印出数组的所有元素。传递了一个参数——一个计数器。因为它通过引用传递，在函数内将此计数器加1会产生一个数字序列。

```php
<?php
    function printElement($s, &$i) {
        printf('%d: %s<br />', $i,
            htmlspecialchars($s));
        $i++;
    }
    $i = 1;
    $a = array('one', 'two', 'three', 'four');
    $a = array_walk($a, 'printElement', $i);
?>
```

使用array_walk()和通过引用传递的计数器打印数组元素（array_walk.php）

运行上述代码显示以下结果：

```
0: one
1: two
2: three
3: four
```

### 过滤数组

```
array_filter($values, 'checkMail')
```

假设你获得了一堆值——来自HTML表单、文件或数据库——并希望选择其中哪些值实际可用，哪些不可用。你可以再次调用for、foreach或while来找出感兴趣的内容，或者你可以让PHP完成大部分工作。在后一种情况下，你需要熟悉函数`array_filter()`。它接受两个参数——第一个是要过滤的数组，第二个是函数名（以字符串形式），用于检查数组元素是否合格。这个验证函数在成功时返回`true`，否则返回`false`。下面是一个非常简单的电子邮件地址验证函数（有关此主题的讨论，请参阅第1章“操作字符串”）。

```php
<?php
function checkMail($s) {
    $ampersand = strpos($s, '@');
    $lastDot = strrpos($s, '.');
    return ($ampersand !== false &&
            $lastDot !== false &&
            $lastDot - $ampersand >= 3);
}
?>
```

```php
$values = array(
    'valid@email.tld',
    'invalid@email',
    'also@i.nvalid',
    'also@val.id'
);
echo implode(', ', array_filter($values,
    'checkMail'));
?>
```

*过滤有效的电子邮件地址（array_filter.php）*

现在，本节开头的代码调用array_filter()，因此只留下（语法上）有效的电子邮件地址。

正如你所期望的，该代码只打印出两个有效的电子邮件地址。

### 从数组中获取随机元素

```
array_rand($numbers, 6)
```

使用array_rand()，可以随机确定数组中的一个或多个随机元素。例如，这可以用来抽取一些幸运数字。例如，德国彩票从49个数字中抽取6个。前面的代码使用PHP和array_rand()实现了这一抽取：见图2.7的输出。此函数的第一个参数是数组；第二个（可选）参数是要返回的元素数量。

```php
<?php
for ($i = 1; $i <= 49; $i++) {
    $numbers[] = $i;
}

echo implode(' ', array_rand($numbers, 6));
?>
```

从数组中挑选随机元素（array_rand.php）

> **注意**
> 
> 如果你不想挑选随机元素，而是想随机化数组中元素的顺序（例如，洗牌时），请使用shuffle()函数。

![](img/1e6d362f187af50011d2666ddaa68739_69_0.png)

图2.7 使用PHP生成幸运数字。

## 日期和时间

大多数时候，PHP 5的日期和时间功能用于打印当前日期和时间——以表明网页是最新的（你会惊讶于有多少大型网站实际使用这一点）。但除此之外，在PHP中处理日期和时间还提供了许多其他可能性，其中大部分你将在本章中找到。

首先，看一下PHP中最可能用于处理日期的函数——date()似乎是合适的。这个函数可以获取当前日期（或任意日期）并提取关于它的一些信息，例如，今天是几号，是上午还是下午，以及根据那个相当失败的市场营销噱头“Swatch Internet Time”现在是什么时间。为此，你调用date()并提供一个字符串作为第一个参数。这个字符串可以包含一系列格式化符号，如表3.1所示（PHP手册在http://php.net/date处带有更多示例的列表）。每个符号都被相应的日期/时间值替换。

### 表3.1 date()的格式化符号

| 符号 | 描述 |
|--------|-------------|
| a | am或pm |
| A | AM或PM |
| B | Swatch Internet Time（介于000和999之间） |
| c | ISO 8601格式的日期 |
| d | 月份中的日期（从01到31） |
| D | 星期几（从Mon到Sun） |
| F | 月份（从January到December） |
| g | 小时（从1到12） |
| G | 小时（从0到23） |
| h | 小时（从01到12） |
| H | 小时（从00到23） |
| i | 分钟（从00到59） |
| I | 日期是否在夏令时（1）或不是（0） |
| j | 月份中的日期（介于1和31之间） |
| l | 星期几（从Sunday到Saturday） |
| L | 日期是否在闰年（1）或不是（0） |
| m | 月份（从01到12） |
| M | 月份（从Jan到Dec） |
| n | 月份（从1到12） |
| O | 与GMT的差异（例如，+0100表示提前一小时） |
| r | RFC 2822格式的日期 |
| s | 秒（从00到59） |
| S | 月份中日期的序数后缀（st、nd、rd、th） |
| t | 所给月份的天数（从28到31） |
| T | 服务器的时区（例如，CET） |

### 表3.1 续表

| 符号 | 描述 |
| --- | --- |
| U | 纪元值（自1970年1月1日格林尼治标准时间午夜以来的秒数） |
| w | 星期几（从0——星期日，到6——星期六） |
| W | 周数（根据ISO 8601，从1到53） |
| y | 年份（两位数字） |
| Y | 年份（四位数字） |
| z | 一年中的第几天（从0到365） |
| Z | 与UTC的时区差（以秒为单位） |

**注意**
表3.1中显示的几乎所有格式化符号自PHP 3以来都可用。只有两个例外：使用W来确定日期所在的周数是在PHP 4.1.0中添加的，而使用c来获取日期的ISO 8601表示（例如，2006-06-30T12:34:56+01:00）是在PHP 5中出现的。

函数date()非常强大，提供了广泛的使用方式。然而，特别是如果你有本地化内容，你需要一些好的短语。在本章中，你将找到许多这样的短语。

PHP的日期和时间函数在PHP手册中有自己的一节。你可以在http://php.net/datetime找到关于date()及其相关函数的更多信息。




### 在 date() 中使用文本

```
date('\To\d\a\y \i\s \t\he jS \d\a\y of F')
```

想象你想要输出当前日期（或特定日期）并在其中使用自定义字符串。如果像这样尝试，代码可能会显得很混乱：

```
<?php
echo 'Today is the ' . date('jS') . ' day of the month ' . date('F');
?>
```

```
<?php
echo date('\To\d\a\y \i\s \t\he jS \d\a\y of F');
?>
```

*在 date() 中使用普通字符 (date.php)*

此脚本的输出如下所示，具体取决于当前日期：

今天是五月的第 3 天

date() 的行为如下：第一个参数中具有特殊含义的所有字符（例如，格式化符号）都会被适当的值替换。然而，其他字符保持不变。如果使用反斜杠字符（\）转义一个字符，则会原样返回。因此，本段开头的代码显示了仅使用一次 date() 调用的新版本代码。

> NOTE
> 如果你使用双引号而不是单引号，在 date() 中转义某些字符时可能会遇到麻烦。在前面的示例中，转义 n 会使用 \n，而在双引号内它会被替换为换行字符。

### 自动本地化日期

```
setlocale(LC_TIME, 'en_US');
echo strftime('In (American) English: %c<br />');
```

PHP 函数 strftime() 根据系统的区域设置格式化日期/时间值，例如 Web 服务器的本地设置。一般来说，系统的语言会自动使用。然而，这可以使用 setlocale() 来覆盖。

```
<?php
setlocale(LC_TIME, 'en_US');
echo strftime('In (American) English: %c<br />');
setlocale(LC_TIME, 'en_gb');
echo strftime('In (British) English: %c<br />');
setlocale(LC_TIME, 'de_DE');
echo strftime('Auf Deutsch: %c<br />');
setlocale(LC_TIME, 'fr_FR');
echo strftime('En Français: %c');
?>
```

*使用 strftime() 本地化日期 (strftime.php)*

函数 strftime() 接受一个格式字符串（date() 也是如此），其中接受大量特殊符号。表 3.2 包含完整列表。

### 自动本地化日期

表 3.2 — `strftime()` 的格式化符号

| Symbol | Description |
|---|---|
| `%a` | 星期几（缩写） |
| `%A` | 星期几 |
| `%b` or `%h` | 月份（缩写） |
| `%B` | 月份 |
| `%c` | 标准格式的日期和时间 |
| `%C` | 世纪 |
| `%d` | 月中的日（从 01 到 31） |
| `%D` | 日期缩写格式（mm/dd/yy） |
| `%e` | 月中的日作为两字符字符串（从‘ 1’到‘31’） |
| `%g` | 按周数计的年份，两位数 |
| `%G` | 按周数计的年份，四位数 |
| `%H` | 小时（从 00 到 23） |
| `%I` | 小时（从 01 到 12） |
| `%j` | 一年中的日（从 001 到 366） |
| `%m` | 月份（从 01 到 12） |
| `%M` | 分钟（从 00 到 59） |
| `%n` | 换行（`\n`） |
| `%p` | 上午或下午（或本地等价） |
| `%r` | 使用上午/下午标记的时间 |
| `%R` | 使用 24 小时标记的时间 |
| `%S` | 秒（从 00 到 59） |
| `%t` | 制表符（`\t`） |
| `%T` | 时间格式为 hh:ss:mm |
| `%u` | 星期几（从 1—星期一—到 7—星期日） |

表 3.2 继续

| Symbol | Description |
|---|---|
| %U | 周数（规则：第一个星期日是第一周的第一天。） |
| %V | 周数（规则：一年中至少有四天的第一周计为周数 1。） |
| %w | 星期几（从 0—星期日 到 6—星期六） |
| %W | 周数（规则：第一个星期一是第一周的第一天。） |
| %x | 标准格式的日期（不含时间） |
| %X | 标准格式的时间（不含日期） |
| %y | 年份（两位） |
| %Y | 年份（四位） |
| %z or %Z | 时区 |

每当表 3.2 中提到 *标准格式* 时，格式化符号会根据本地设置被替换为关联的值。前面的代码使用 `setlocale()` 多次更改区域设置，然后调用 `strftime()`。可以在图 3.1 中看到差异。还请看图 3.2，其中相同的脚本在 Windows 机器上执行。根据文档，大多数 `strftime()` 也在 Windows 上工作，但在某些配置中更改区域设置似乎不起作用。因此，非常重要的是先测试系统是否支持本地化日期。

### 自动本地化日期

![](img/1e6d362f187af50011d2666ddaa68739_77_0.png)

图 3.1  不同区域设置下的当前日期。

![](img/1e6d362f187af50011d2666ddaa68739_77_1.png)

图 3.2  此特定系统似乎不支持区域设置。

### 手动本地化日期

如果你不能依赖 setlocale()，但仍想使用本地化日期和时间值，你必须自己进行翻译并将结果存储在数组中。然后，你可以使用 date() 检索有关日期的信息。这可作为你数组的索引。

```
<?php
    $weekdays = array(
        'domingo', 'lunes', 'martes', 'miércoles',
        'jueves', 'viernes', 'sábado'
    );
    $months = array(
        'enero', 'febrero', 'marzo', 'abril',
        'mayo', 'junio', 'julio', 'agosto',
        'septiembre', 'octubre', 'noviembre',
        'diciembre'
    );
    $weekday = date('w');
    $month = date('n');
    echo $weekdays[$weekday] . date(', j ') .
        $months[$month - 1] . date(' Y');
?>
```

*手动本地化日期 (localdate.php)*

前面的代码对月份中的日期和月份本身都执行了此操作。一个数组包含西班牙语的星期几；另一个数组包含月份名称。

请注意，月份的值减少了 1，因为数组 $months 在位置 0 没有虚拟元素；因此，月份编号为一（1 月）的索引为 0。

### 按美国/英国/欧洲方式使用当前日期

```
<?php
    echo 'US format: ' . date('m/d/Y<br />');
    echo 'UK format: ' . date('d/m/Y<br />');
    echo 'German format: ' . date('d.m.Y<br />');
    echo 'International format: ' . date('Y-m-d');
?>
```

### 按美国/英国/欧洲方式使用当前日期

为了给你一个简短方便的参考，前面的代码包含了一些常用的日期格式。根据你的所在位置，日、月、年的顺序可能会有所不同：

- 在美国，主要是月份、日和年份
- 在英国和欧洲其他地区，主要是日、月份和年份
- 国际标准日期表示法以年份开头，然后是月份和日期

> **NOTE**
> 前面的代码使用了四位数的年份表示，因为这是无歧义的。在实践中，两位数的年份也很常见。

### 格式化特定日期

```
echo 'Time stamp: ' . mktime(12, 0, 0, 1, 1, 2001);
```

本章前面的所有段落都使用了当前日期和时间。然而，也可以使用任何其他任意日期和时间值。为此，相关函数（尤其是 date() 和 strftime()）接受第二个参数——要分析的日期的时间戳。此时间戳是一个整数值，即所谓的 epoch 格式的日期和时间。这是自 1970 年 1 月 1 日格林威治标准时间午夜以来经过的秒数——UNIX 纪元的开始。当前时刻的时间戳/epoch 值可以使用 time() 或通过调用 date('U') 检索（参见表 3.1）。

### 格式化特定日期

如果你想使用另一个日期，mktime() 就派上用场了。此函数将按年份、月份、日期、小时、分钟和秒提供的日期转换为 epoch 值。关于此函数最奇怪的事情可能是这些参数传递的顺序：

- 1. 小时
- 2. 分钟
- 3. 秒
- 4. 月份
- 5. 日期
- 6. 年份

你还可以提供一个可选的第七参数，无论是否使用夏令时（DST）。这在夏令时变更前后很相关，因为世界各地并不在同一时间发生。

前面的代码计算了本千年第一天的中午时间戳。由于没有公元 0 年，这就是 2001 年 1 月 1 日。

> 如果你喜欢收集无用的事实：在 2001 年 9 月 9 日凌晨 3:46:40  precisely，时间戳为 1,000,000,000。因此，mktime(3, 46, 40, 9, 9, 2001) 返回 1000000000（如果你的时区是中欧）。



### 提示

为什么 2000 年是闰年，但 2100 年不是？定义是：如果一年能被 4 整除，并且要么不能被 100 整除，要么能被 400 整除，则为闰年，二月有 29 天（这是因为地球绕太阳公转大约需要 365.25 天）。如果您想确定给定的年份是否为闰年，这个函数会很有用：

```
function isLeapYear($year) {
    return ($year % 4 == 0 &&
        ($year % 100 != 0 || $year % 400 == 0));
}
```

有时，您需要计算相对于当前日期的日期，例如“30 天后”。当然，您可以真正投入工作来实际计算这个值，考虑到是哪一天、是否为闰年以及是否与夏令时相关。

更简单的方法是使用纪元时间戳。例如，前面提到的找到未来 30 天的日期的任务。一天有 24 小时，一小时有 60 分钟，一分钟有 60 秒。因此，要获取当前时间戳（使用 time() 或 date('U')），您只需加上 30 * 24 * 60 * 60，就得到了所需日期的时间戳。然后可以使用此时间戳来设置 cookie 的过期日期或仅打印有关此日期的一些信息。

### 创建可排序的时间戳

```
function timestamp($t = null) {
    if ($t == null) {
        $t = time();
    }
    return date('YmdHis', $t);
}
```

有时，在数据库中使用日期值并不是一个明智的做法。数据库的不同语言版本、其驱动程序或底层操作系统在区域日期格式不匹配时可能会引起一些问题。

```
<?php
function timestamp($t = null) {
    if ($t == null) {
        $t = time();
    }
    return date('YmdHis', $t);
}

echo 'Time stamp: ' . timestamp(time());
?>
```

*将日期转换为（可排序的）时间戳 (timestamp.php)*

一种潜在的替代方案是使用时间戳。有几种不同的格式可用，但大多数格式的结构如下：年-月-日-小时-分钟-秒。使用这种值顺序，日期的字符串表示可以轻松排序，从而允许在数据库中使用。

要创建这样的时间戳，只需对 date() 进行特殊调用即可。在前面的代码中，这被封装在一个函数中以便重复使用。

### 提示
此格式也由 MySQL 用于表示其 TIMESTAMP 数据类型。

### 将字符串转换为日期

```
'Yesterday: ' . date('r', strtotime('Yesterday'))
```

之前，您看到的是日期的数字表示——要么是日、月、年的三元组，要么是时间戳值。这次，您可以反过来，将日期/时间值的字符串表示转换为纪元值或 PHP 及其日期/时间函数中可用的其他内容。

```
<?php
    echo 'Yesterday: ' . date('r',
        strtotime('Yesterday')) . '<br />';
    echo 'Today: ' . date('r', strtotime('Today')) .
        '<br />';
    echo 'Tomorrow: ' . date('r',
        strtotime('Tomorrow')) . '<br />';
    echo 'In one week: ' . date('r', strtotime('+1 week')) . '<br />';
    echo 'One month before: ' . date('r', strtotime('-1 month')) . '<br />';
    echo 'Last Sunday: ' . date('r', strtotime('Last Sunday')) . '<br />';
    echo 'Next fantasy day: ' .
        var_export(@date('r', strtotime('Next fantasy day')), true);
?>
```

将字符串转换为日期 (strtotime.php)

### 将字符串转换为日期

所有魔力都放在 PHP 函数 strtotime() 中。根据文档，它“解析几乎任何英语文本日期/时间描述为 UNIX 时间戳”。听起来很惊人，而且确实惊人。其基础是 GNU date 语法；本段开头的代码显示了一些 strtotime() 的示例。

> 注意
> 在撰写本文时，strtotime() 在计算相对日期且即将发生夏令时变更或结束时表现出一些奇怪的行为。同样在撰写本文时，PHP 的日期/时间函数即将被重写和修改。

### 确定日出和日落

```
date_sunrise(time(), SUNFUNCS_RET_STRING, 48, 11.5, 90, 1);
date_sunset(time(), SUNFUNCS_RET_STRING, 48, 11.5, 90, 1);
```

根据当前位置和日期，日出和日落时间可能有很大差异。然而，存在根据纬度和经度确定此值的公式，并且 PHP 从 PHP 5 开始已将此功能集成到其核心中。您需要做的就是调用 date_sunrise() 和 date_sunset()。这两个函数都期望多个参数：

- 用于确定日出/日落的日期的时间戳（纪元值）

### 确定日出和日落

- 返回值的期望格式：
  - SUNFUNCS_RET_DOUBLE returns the time as a float value (between 0 and 23.99), SUNFUNCS_RET_STRING returns it as a string (between 00:00 and 23:59), and SUNFUNCS_RET_TIMESTAMP returns an epoch value
- 纬度（北纬；南纬使用负值）
- 经度（东经；西经使用负值）
- 日出的天顶（以度为单位）
- 相对于格林威治标准时间（GMT）的偏移量（以小时为单位）

因此，前面的代码（在 sun.php 中）计算了德国慕尼黑当前日的 sunrise 和 sunset，该地位于约 48° 北纬、11° 30' 东经。我检查过：它有效！

### 使用日期和时间进行基准测试

```
$start = microtimestamp();
$end = microtimestamp();
($end-$start)
```

到目前为止，所有日期/时间函数产生的精度都不超过秒级；没有微秒可用。当您使用函数 gettimeofday() 时情况会改变。它返回一个值数组。键 'sec' 返回相关联的纪元值；然而，'usec' 返回

### 使用日期和时间进行基准测试

额外的微秒。有了它，可以为需要精确测量的操作使用非常精确的值，例如基准测试。

```
<?php
// ...

$start = microtimestamp();
$s = '';
for ($i=0; $i < 100000; $i++) {
  $s .= "$i";
}
$end = microtimestamp();
echo 'Using double quotes: ' . ($end-$start) .
  '<br />';

$start = microtimestamp();
$s = '';
for ($i=0; $i < 100000; $i++) {
  $s .= $i;
}
$end = microtimestamp();
echo 'Using no quotes: ' . ($end-$start) . '<br />';
?>
```

*使用 microtimestamp() 进行基准测试代码 (benchmark.php; excerpt)*

本段开头的代码包含一个返回精确时间戳的函数 microtimestamp()。该函数被调用两次；中间进行一个或多或少的复杂计算。其结果是一个基准测试，可能有助于决定哪种编码技术更优越。

### 使用表单字段进行日期选择

```php
function microtimestamp() {
	$timeofday = gettimeofday();
	return $timeofday['sec'] + $timeofday['usec'] / 1000000;
}
```

图 3.3 显示了结果。效果因人而异，但您会发现使用双引号只是浪费时间。（在另一个实验中，您可能会发现使用单引号还是双引号几乎没有区别——尽管流传着相反的说法。）

![](img/1e6d362f187af50011d2666ddaa68739_88_0.png)

图 3.3 第二段代码更快。

### 使用表单字段进行日期选择

```php
<select name="month"><?php
for ($i = 1; $i <= 12; $i++) {
	$monthname = date('F', mktime(12, 0, 0, $i, 1, 2005));
	echo "<option value=\"\$i\">$monthname</option>";
}
?></select>
```

### 使用表单字段进行日期选择

如果您想提供一个 HTML 表单来选择日期，就像许多酒店和航班预订服务提供的那样，您可以使用 date() 的各种参数；遍历一年的所有月份；因此创建日、月、年的选择列表。前面的代码包含此代码；请参阅图 3.4 查看结果。

```
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
<select name="day"><?php
    for ($i = 1; $i <= 31; $i++) {
        echo "<option value=\"$i\">$i</option>\n";
    }
?></select>
<select name="month"><?php
    for ($i = 1; $i <= 12; $i++) {
        $monthname = date('F', mktime(12, 0, 0, $i, 1, 2005));
        echo "<option value=\"$i\">$monthname</option>";
    }
?></select>
<select name="year"><?php
    for ($i = 2005; $i <= 2010; $i++) {
        echo "<option value=\"$i\">$i</option>";
    }
?></select>
</form>
```

*使用 HTML 表单选择日期 (dateselection.php; excerpt)*



> 提示
> 你可以用以下代码替换 microtimestamp() 函数：
> 
> ```
> function microtimestamp() {
>     return microtime(true);
> }
> ```
> 
> microtime() 函数在提供参数 true 时（这是在 PHP 5 中添加的）会返回当前微时间的浮点值。然而，据说它比使用 gettimeofday() 慢，后者只是执行底层的 gettimeofday 系统调用。

### 为日期选择创建自更新表单字段

下一节中的代码有一个小缺陷：每月的天数始终从 1 到 31，即使在天数较少的月份也是如此。使用 JavaScript，可以编写一个花哨的脚本来计算当前月份有多少天，然后更新选择列表。

```php
<?php
if (isset($_POST['month']) && is_numeric($_POST['month']) &&
    ((int)$_POST['month'] >= 1 &&
(int)$_POST['month'] <= 12)) {
    $month = (int)$_POST['month'];
} else {
    $month = date('n');
}
if (isset($_POST['year']) && is_numeric($_POST['year']) &&
    ((int)$_POST['year'] >= 2005 &&
(int)$_POST['year'] <= 2010)) {
    $year = (int)$_POST['year'];
} else {
    $year = date('Y');
}
?>
<form method="post" action="<?php echo
    htmlspecialchars($_SERVER['PHP_SELF']); ?>">
    <select name="day"><?php
    $maxdays = date('t', mktime(12, 0, 0, $month, 1,
        $year));
    for ($i = 1; $i <= $maxdays; $i++) {
        if (isset($_POST['day']) && $_POST['day'] ==
            $i) {
            $sel = ' selected';
        } elseif ($i == date('j')) {
            $sel = ' selected';
        } else {
            $sel = '';
        }
        echo "<option value=\"$i\"$sel>$i</option>\n";
    }
?></select>
    // ...
</form>
```

日期选择会自动更新
(dateselection-js.php; 摘录)

![](img/1e6d362f187af50011d2666ddaa68739_92_0.png)

图 3.4 月份名称是自动生成的。

然而，使用 JavaScript 和 PHP 的组合会更方便。使用 JavaScript，你可以自动提交表单。使用 PHP，你可以预先填充表单字段（有关更多信息，请参阅第 4 章“与 Web 表单交互”），更重要的是，找出相关年份有多少天。

JavaScript 代码被限制到最小：选择另一个月份会提交 HTML 表单（选择另一个年份也会提交表单，因为闰年会使二月变长）：

```html
<select name="month" onchange="this.form.submit();">
...
<select name="year" onchange="this.form.submit();">
```

每月的天数可以使用 date('t') 找到。本节开头处的列表包含了此功能的完整代码，包括对传输信息的某些合理性检查。此外，代码会自动预选当前日期，除非用户选择其他日期。图 3.5 包含完整代码的输出。

### 计算两个日期之间的差异

```
$century = mktime(12, 0, 0, 1, 1, 2001);
$today = time();
$difference = $today - $century;
```

可以由 time() 和其他 PHP 函数确定的纪元值可用于轻松计算两个日期之间的差异。诀窍是将日期转换为时间戳（如果尚未以此格式提供）。然后计算这两个时间戳之间的差异。结果是秒为单位的时间差。然后此值可用于找出它对应多少分钟、小时和天：

- 将结果除以 60 得到分钟数
- 将结果除以 60 * 60 = 3600 得到小时数
- 将结果除以 60 * 60 * 24 = 86400 得到天数

```php
<?php
$century = mktime(12, 0, 0, 1, 1, 2001);
$today = time();
$difference = $today - $century;
echo 'This century started ';
echo floor($difference / 86400);
$difference -= 86400 * floor($difference / 86400);
echo ' days, ';
echo floor($difference / 3600);
$difference -= 3600 * floor($difference / 3600);
echo ' hours, ';
echo floor($difference / 60);
$difference -= 60 * floor($difference / 60);
echo " minutes, and $difference seconds ago.";
?>
```

两个日期之间的差异 (timediff.php)

![](img/1e6d362f187af50011d2666ddaa68739_94_0.png)

图 3.5 PHP 代码用适当的天数填充了月份选择列表。

如果你从天数开始，将每个结果向下取整并从结果中减去它；你也可以将差异拆分为天、小时和分钟。

### 使用 GMT 日期/时间信息

通常，PHP 使用时间的本地设置。然而在某些特殊情况下，必须使用 GMT 时间格式。为此，PHP 提供了一些日期/时间函数的“GMT 启用”版本：

- `gmdate()` 的工作方式与 `date()` 相同并格式化日期/时间值；然而，返回值使用 GMT 格式
- `gmmktime()` 创建的时间戳与 `mktime()` 类似；然而，它使用 GMT
- `gmstrftime()` 的格式化方式与 `strftime()` 相同；然而，它使用 GMT

GMT 在设置页面在 HTTP 头中的过期日期或手动设置 cookie 的过期日期（也在 HTTP 头中）时很重要。

### PEAR 提供了什么？

以下 PEAR 包提供了有助于处理任何类型表单数据的功能：

- `Date` 包含一组用于处理各种日期/时间值的函数，包括时区之间以及各种日期/时间表示之间的转换
- `Date_Holidays` 计算特殊假期的名称和日期

## 与 Web 表单交互

HTML 表单是任何动态网站的关键要素之一，因为它们可以让网站用户与其交互。否则，网站或多或少是静态的：它们可能由数据库驱动，因此会定期更改，但对每个访客看起来都一样。HTML 表单可以改变这一点；因此，从 PHP 中使用表单数据非常重要。

读取信息是一项非常简单的任务：对于通过 GET 提交的表单数据（即在请求的页面的统一资源标识符 [URI] 中），数据可以在 $_GET[<表单字段 name 属性的值>] 中找到。然而，这只是开始。假设用户填写表单但忘记了一个字段。与其显示错误消息并要求用户点击浏览器的后退按钮，用户可以期望一个表单，其中所有字段都已填入他之前提供的值。许多书籍忽略了这一点；更糟的是，有些书籍只是做错了。你必须不要忘记表单字段值的特殊编码；否则，表单会受到跨站脚本 (XSS) 攻击，或至少看起来会很丑陋。

图 4.1 演示了这一点：你看到两个按钮的标题相同；然而，只有第一个按钮的标题在 HTML 代码中被正确编码。

![](img/1e6d362f187af50011d2666ddaa68739_97_0.png)

图 4.1 正确编码特殊字符是强制性的。

其他重要主题包括超文本传输协议 (HTTP) 文件上传以及应对 php.ini 或其他地方可能抵制开发人员良好意图的各种设置。

### 将表单数据发送回当前脚本

```
<form action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
</form>
```

所有相关浏览器如果在 <form> 元素中未提供 action 属性，就会将表单数据发送回当前页面。然而，HTML 和可扩展超文本标记语言 (XHTML) 规范都指出 action 是一个必需属性（在文档类型定义 [DTDs] 中标记为 #REQUIRED）。用户代理的行为是未定义的，正如 http://w3.org/TR/html4/interact/forms.html#def-action 处的 HTML 规范所解释的那样。因此，最好明确提供当前脚本的统一资源定位符 (URL) 作为表单的 action。上面的代码就是这样做的，并且还出于安全原因转义了 $_SERVER['PHP_SELF'] 中的特殊字符。

### 读取表单数据

起初，读取表单数据非常容易：如果表单字段具有 name 属性 "whatever" 或在 HTML/XHTML 的较新版本中具有 id 属性 "whatever"，PHP 会在全局范围内创建一个变量 $whatever。这非常方便，但从架构角度来看是个坏主意。因此，从 PHP 4.2 版本开始，默认情况下使用以下 php.ini 指令禁用了它：

```
register_globals = Off
```

自 PHP 3 以来，以下全局数组用于表单数据：

- $HTTP_GET_VARS—使用 GET 提供的所有数据
- $HTTP_POST_VARS—使用 POST 提供的所有数据
- $HTTP_REQUEST_VARS—使用 GET 或 POST 提供的数据，或通过 cookie 提供的数据（不推荐使用）

这些数组是全局的；因此，如果你在函数中使用它们，你必须使用 global 关键字将它们提升到全局范围：

### 读取表单数据

```
function processData() {
    global $HTTP_POST_VARS;
    // now you may access $HTTP_POST_VARS
}
```

然而，这些数组也可以被停用（PHP 5 起），使用此 php.ini 指令：
`register_long_arrays = Off`

因此，以下是今天在 PHP 中访问表单数据的唯一推荐方法：

- $_GET 用于 GET 数据
- $_POST 用于 POST 数据
- $_REQUEST 用于 POST、GET 和 cookie（不推荐）

这些数组的键是表单值的名称。$_* 数组是所谓的超全局数组——也就是说，你不需要使用 global 关键字将它们带入全局作用域；它们在函数内部已经可用。

当你决定使用哪个超全局数组（取决于表单的 method）后，访问表单数据很容易：$_GET[<formfieldname>] 或 $_POST[<formfieldname>] 会检索表单元素中的值。表 4.1 显示了针对每种表单字段类型返回的数据。

### 表 4.1 $_GET/$_POST 中表单字段类型及返回的数据

| 表单字段类型 | 返回的数据 |
|---|---|
| 文本字段 | 字段中的文本 |
| 密码字段 | 字段中的文本（明文，未加密） |
| 多行文本字段 | 字段中的文本 |
| 隐藏字段 | 字段的 value 属性 |
| 单选按钮 | 已选单选按钮的 value 属性 |
| 复选框 | 若选中则为复选框的 value 属性（若未设置 value 则为 "on"） |
| 选择列表 | 已选列表元素的 value 属性（若未设置 value 则为已选列表元素的标题） |
| 多选列表 | 已选列表元素的 value 属性组成的数组（若未设置 value 则为已选列表元素的标题组成的数组） |
| 提交按钮 | 若使用此按钮发送表单，则为提交按钮的 value 属性（如果有多个提交按钮则很重要） |

提示
另外两种表单字段类型，图形化提交按钮和文件上传，将在本书后面专门介绍。

### 处理 "Magic Quotes"

```
if (get_magic_quotes_gpc()) {
  $_GET = stripFormSlashes($_GET);
  $_POST = stripFormSlashes($_POST);
}
```

如果配置设置 magic_quotes 设置为 "On"，所有来自外部源的数据，包括表单数据和 cookie，都会得到特殊处理。所有引号字符，" 和 '，都使用反斜杠字符（\）进行转义。因此，如果用户在文本字段中输入 It's my life，则 $_GET 或 $_POST 中找到的值为 It\'s my life。这最初是为了避免结构化查询语言（SQL）注入（有关更多详细信息，请参阅第 8 章“使用 XML”），但对于经验丰富的程序员来说非常令人厌烦。唯一更令人厌烦的事情是手动为每个表单字段删除这些引号。

```php
<?php
    function stripFormSlashes($arr) {
        if (!is_array($arr)) {
            return stripslashes($arr);
        } else {
            return array_map('stripFormSlashes', $arr);
        }
    }

    if (get_magic_quotes_gpc()) {
        $_GET  = stripFormSlashes($_GET);
        $_POST = stripFormSlashes($_POST);
    }
?>
```

*如果由 "Magic Quotes" 添加了反斜杠，则去除反斜杠（stripFormSlashes.inc.php）*

PHP 函数 stripslashes() 从字符串中删除转义反斜杠。然而，此函数只能在应用了“magic quotes”时调用；否则，它会破坏有意添加的反斜杠。你可以通过调用布尔函数 get_magic_quotes_gpc() 来确定“magic quotes”是否处于活动状态。如果返回 true，则可以删除所有斜杠。为了使其尽可能方便，

### 检查表单是否已提交

你可以采用几种不同的方法来完成此任务；一种总是有效的方法是为提交按钮分配一个名称，然后测试在表单提交时此名称是否存在。

> 提示
> 如果你的表单有多个提交按钮，请为每个按钮分配一个独特的名称；然后，你可以专门检查该名称，从而确定使用了哪个提交按钮。

### 将表单数据保存到 Cookie 中

```php
setcookie('formdata', serialize($formdata), time()+30*24*60*60);
```

表单提交后，数据必须去往某处，可能存入数据库（参见第 8 章），写入文件，或通过电子邮件发送。当网站包含多个相似的表单（例如，所有表单都要求用户提供姓名和联系信息）时，在用户填写后保存数据是个好主意。由于 HTTP 是无状态协议，你必须使用 cookie（参见第 6 章“在服务器文件系统上使用文件”）——会话是无用的，因为它们在用户关闭浏览器时过期。

```php
function setCookieData($arr) {
    $formdata = getCookieData();
    if ($formdata == null) {
        $formdata = array();
    }
    foreach ($arr as $name => $value) {
        $formdata[$name] = $value;
    }
    setcookie('formdata', serialize($formdata),
        time()+30*24*60*60);
}
```

*将数据保存到 Cookie 中（getFormData.inc.php；摘录）*

由于用户代理每个域名只需保存 20 个 cookie，因此将表单信息存储在一个 cookie 中作为数组是个好主意。然而，cookie 中只允许字符串值；这就是为什么你必须序列化数组。列表开头显示的函数将作为参数提供的数组的内容写入 cookie。

函数 getCookieData() 返回 cookie 中现有的（如果可用）数据并将其反序列化为数组。你将在后面的章节看到代码。

剩下的唯一工作就是将所需的表单数据写入此数组。你可以专门提交某些值，或完整提交数组 $_GET 或 $_POST，如以下代码所示。

```php
<?php
    require_once 'stripFormSlashes.inc.php';
    require_once 'getFormData.inc.php';
    if (isset($_POST['Submit'])) {
        setCookieData($_POST);
    }
?>
...
<?php
    if (isset($_POST['Submit'])) {
        echo '<h1>Thank you for filling out this form!</h1>';
    } else {
?>
    <form method="post" action="<?php echo
        htmlspecialchars($_SERVER['PHP_SELF']); ?>">
    ...
    </form>
<?php
    }
?>
```

*在 Cookie 中保存表单数据（save-cookie.php；摘录）*

图 4.2 显示了 resulting cookie。

![](img/1e6d362f187af50011d2666ddaa68739_105_0.png)

图 4.2 序列化的表单数据保存在 cookie 中。

注意
请注意，你必须在任何 HTML 输出之前保存表单数据。由于 cookie 作为 HTTP 头的一部分发送，它们必须在 HTML 开始之前声明（因此 HTTP 头结束）。有关 cookie 时间的更多信息，请参阅第 6 章。

### 预填充文本字段和密码字段

```
<input type="text" name="textfieldname"
value="<?php
echo (isset($_POST['textfieldname'])) ?
htmlspecialchars($_POST['textfieldname']) : '';
?>" />
```

文本字段（以及密码字段和隐藏字段）中的值由其 value 属性提供。然而，那里的数据必须使用 htmlspecialchars() 正确编码，以去掉危险字符，如 ' 或 < 或 >。前面的代码片段期望表单提交回自身；因此，它从 $_POST 中提取文本字段的当前值（使用 $_GET 也会类似地工作）。

```
<?php
require_once 'stripFormSlashes.inc.php';
?>
...
<input type="text" name="textfieldname"
value="<?php
echo (isset($_POST['textfieldname'])) ?
htmlspecialchars($_POST['textfieldname']) : '';
?>" />
```

*预填充文本字段（text.php；摘录）*

提示
这也适用于密码字段和隐藏字段。

如果你想为此表单元素使用默认值，只需在 PHP 代码中用此默认值代替空字符串即可：


### 预填充文本字段和密码字段

```
<input type="text" name="textfieldname"
    value="<?php
    echo (isset($_POST['textfieldname'])) ?
        htmlspecialchars($_POST['textfieldname']) :
        'default value';
?>" />
```

另一种可能性是从 cookie 中预填充表单值。当用户多次将数据输入表单时，这非常有用。这样，当他们几天后再次访问站点上的表单时，可以从 cookie 中检索旧数据。是的，只需要一个 cookie，因为每个域只允许 20 个 cookie。当然，我们使用数组来实现这一点。但是，cookie 值只允许使用字符串，因此需要使用 serialize() 和 unserialize()。

下面的函数从包含表单数据的 cookie 中检索值。优先级顺序如下：如果 $_GET 或 $_POST 中包含该字段的当前值，则使用该值（由于通常一次只使用这两种方法中的一种，因此存在专门针对 $_GET 和 $_POST 的函数版本）。否则，脚本会在 $_COOKIE 中查找关联值。如果找不到任何内容，则返回空字符串。

```
function getCookieData() {
    if (isset($_COOKIE['formdata'])) {
        $formdata = $_COOKIE['formdata'];
        if ($formdata != '') {
            if (get_magic_quotes_gpc()) {
                $formdata = stripslashes($formdata);
            }
            return unserialize($formdata);
        } else {
            return array();
        }
    } else {
        return null;
    }
}

function getFormDataPOST($name) {
    if (isset($_POST[$name])) {
        return $_POST[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null &&
            isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
    }
    return '';
}
function getFormDataGET($name) {
    if (isset($_GET[$name])) {
        return $_GET[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null &&
            isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
    }
    return '';
}
```

*从 Cookie 中检索表单数据（getFormData.inc.php；节选）*

现在，预填充表单值就很简单了：由于 getFormDataGET() 和 getFormDataPOST() 总是返回一个值——即使是空字符串——因此返回值可以直接用于文本字段的 value 属性。

### 预填充文本字段和密码字段

```
<?php
    require_once 'stripFormSlashes.inc.php';
    require_once 'getFormData.inc.php';
?>
...
<input type="text" name="textfieldname"
    value="<?php
        echo
    htmlspecialchars(getFormDataPOST('textfieldname'));
    ?>" />
```

*预填充文本字段（text-cookie.php；节选）*

### 预填充多行文本字段

```
<textarea cols="40" rows="5"
name="areafieldname"><?php
    echo (isset($_POST['areafieldname'])) ?
    htmlspecialchars($_POST['areafieldname']) : '';
?></textarea>
```

对于多行文本字段，可以使用与单行文本字段和密码字段几乎相同的方法。唯一的区别在于预填充值的位置：它应位于 <textarea> 和 </textarea> 之间，如代码所示。

```
<?php
    require_once 'stripFormSlashes.inc.php';
?>
...
<textarea cols="40" rows="5"
name="areafieldname"><?php
    echo (isset($_POST['areafieldname'])) ?
    htmlspecialchars($_POST['areafieldname']) : '';
?></textarea>
```

### 注意

如果你想在多行文本字段中提供默认值（例如“在此处输入数据……”），应在 PHP 代码中提供该值，而不是空字符串。请记住，换行也是可以的：

```
<?php
  echo (isset($_POST['areafieldname'])) ?
  htmlspecialchars($_POST['areafieldname']) :
  "default\nvalue";
?>
```

使用 cookie/GET 或 cookie/POST 组合方法，代码会稍微简化。

```
<?php
  require_once 'stripFormSlashes.inc.php';
  require_once 'getFormData.inc.php';
?>
...
<textarea cols="40" rows="5"
name="areafieldname"><?php
  echo htmlspecialchars(getFormDataPOST
    ('areafieldname'));
?></textarea>
```

*预填充多行文本字段（textarea-cookie.php；节选）*

### 预选单选按钮

```
if (isset($_POST['groupname']) &&
  $_POST['groupname'] == 'php5') {
  echo 'checked="checked" ';
}
```

一组单选按钮通过共同的 name 属性来标识。在一组按钮中，只能有

### 预选单选按钮

一个被选中（或一个都不选）。当向服务器提交表单时，所选单选按钮的 value 属性会被传送到服务器。因此，预填充一组单选按钮虽然有些繁琐，但相当简单：只需将 $_GET/$_POST 中的值与关联值进行比较。如果匹配，就输出 checked——这个 HTML 属性用于预选单选按钮，如代码所示。

```
<input type="radio" name="groupname" value="php3"
<?php
    if (isset($_POST['groupname']) && $_POST['groupname'] == 'php3') {
        echo 'checked="checked" ';
    }
?>/>PHP 3
<input type="radio" name="groupname" value="php4"
    <?php
    if (isset($_POST['groupname']) &&
    $_POST['groupname'] == 'php4') {
        echo 'checked="checked" ';
    }
?>/>PHP 4
<input type="radio" name="groupname" value="php5"
<?php
    if (isset($_POST['groupname']) &&
    $_POST['groupname'] == 'php5') {
        echo 'checked="checked" ';
    }
?>/>PHP 5
```

*预填充单选按钮（radio.php；节选）*

这段代码可以扩展，当用户之前已将选择保存在 cookie 中时，使用包含文件 getFormData.inc.php 来预选单选按钮，如下面的代码所示。

```
<?php
    require_once 'getFormData.inc.php';
?>
...
<input type="radio" name="groupname" value="php3"
    <?php
    if (getFormDataPOST('groupname') == 'php3') {
        echo 'checked="checked" ';
    }
?>/>PHP 3
<input type="radio" name="groupname" value="php4"
    <?php
    if (getFormDataPOST('groupname') == 'php4') {
        echo 'checked="checked" ';
    }
?>/>PHP 4
<input type="radio" name="groupname" value="php5"
<?php
    if (getFormDataPOST('groupname') == 'php5') {
        echo 'checked="checked" ';
    }
?>/>PHP 5
```

预填充单选按钮（radio-cookie.php；节选）

### 预选复选框

```
if (isset($_POST['boxname']) && $_POST['boxname']
== 'yes') {
    echo 'checked="checked" ';
}
```

尽管有些网站试图像单选按钮一样对复选框进行分组，但从技术上讲这并不正确。每个复选框都是独立的；因此，它们都应该有不同的名称（给

### 预选复选框

它们相同的名称没有意义）。这样每个复选框都可以单独处理：检查关联的 value 属性，如果匹配，就输出 checked HTML 属性。

```
<?php
<input type="checkbox" name="boxname" value="yes" />
<?php
if (isset($_POST['boxname']) && $_POST['boxname'] == 'yes') {
	echo 'checked="checked" ';
}
?>
I agree.
```
```

*预填充复选框（checkbox.php；节选）*

当使用 cookie 数据（如果可用）时，代码会略有变化。

```
<?php
require_once 'getFormData.inc.php';
?>
...
<input type="checkbox" name="boxname" value="yes" />
<?php
if (getFormDataPOST('boxname') == 'yes') {
	echo 'checked="checked" ';
}
?>
I agree.
```
```

*预填充复选框（cookie.php；节选）*

### 预选选择列表

对于单个选择列表，提交表单时，所选 <option> 元素的 value 会被传送到服务器。然后可以手动

检查该值，使用 selected HTML 属性来预填充表单，如代码所示。

```
<select name="listname">
  <option value="php3"><?php
  if (isset($_POST['listname'])
      && $_POST['listname'] == 'php3') {
      echo ' selected="selected"';
  }
  ?>PHP 3</option>
  <option value="php4"><?php
  if (isset($_POST['listname'])
      && $_POST['listname'] == 'php4') {
      echo ' selected="selected"';
  }
  ?>PHP 4</option>
  <option value="php5"><?php
  if (isset($_POST['listname'])
      && $_POST['listname'] == 'php5') {
      echo ' selected="selected"';
  }
  ?>PHP 5</option>
</select>
```

*预填充选择列表（select.php；节选）*

使用 getFormData.inc.php 可以实现相同的效果；如果有可用的 cookie，则会使用站点 cookie 中的数据。

```
<?php
  require_once 'getFormData.inc.php';
?>
...
<select name="listname">
  <option value="php3"><?php
```




```
if (getFormDataPOST('listname') == 'php3') {
    echo ' selected="selected"';
}
?>PHP 3</option>
<option value="php4"><?php
if (getFormDataPOST('listname') == 'php4') {
    echo ' selected="selected"';
}
?>PHP 4</option>
<option value="php5"><?php
if (getFormDataPOST('listname') == 'php5') {
    echo ' selected="selected"';
}
?>PHP 5</option>
</select>
```

*预填充选择列表 (select-cookie.php; 摘录)*

### 预选多个选择列表

```
if (isset($_POST['multilistname']) &&
in_array('php4', $_POST['multilistname'])) {
    echo ' selected="selected"';
}
```

在预填充表单元素时，多选列表是最难实现的部分。这是因为在 $_GET 或 $_POST 中，你拥有一个已选选项的数组；因此不能简单地比较字符串，而必须在数组中查找指定的值。幸运的是，PHP 以 in_array() 函数的形式提供了合适的解决方案。因此所需的工作量与其它表单元素相比并没有多很多：如果当前值在 $_GET/$_POST 中，则输出 selected 属性。

### 预选多个选择列表

```
<select name="multilistname[]" multiple="multiple"
    size="3">
<option value="php3"><?php
if (isset($_POST['multilistname']) &&
    in_array('php3', $_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>PHP 3</option>
<option value="php4"><?php
if (isset($_POST['multilistname']) &&
    in_array('php4', $_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>PHP 4</option>
<option value="php5"><?php
if (isset($_POST['multilistname']) &&
    in_array('php5', $_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>PHP 5</option>
</select>
```

*预填充多选列表 (select-multiple.php; 摘录)*

然而，HTML 表单必须特别准备，以便 PHP 能访问多选列表的数据：name 属性的值必须以 [] 结尾，提示 PHP 应期望一个值数组，而不仅仅是一个字符串值。然而，访问列表数据仍然可以使用 $_GET['listname'] / $_POST['listname'] 来完成，而不是 $_GET['listname[]'] / $_POST['listname[]']，如前面的代码所示。

如果你想用 cookie 中的数据预填充列表，只需使用前面章节中熟知的 getFormData.inc.php 文件即可。

### 预选多个选择列表

它包含两个额外的函数，它们返回数组而不是字符串。

```php
function getFormDataArrayGET($name) {
    if (isset($_GET[$name])) {
        return $_GET[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null &&
            isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
    }
    return array();
}
function getFormDataArrayPOST($name) {
    if (isset($_POST[$name])) {
        return $_POST[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null &&
            isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
    }
    return array();
}
```

*从 Cookie 中检索表单数据 (getFormData.inc.php: 摘录)*

这些函数为多选列表返回一个数组，你可以像在 `select-multiple.php` 中那样使用它。

```php
<?php
    require_once 'getFormData.inc.php';
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
<head>
<title>Forms</title>
</head>
<body>
<form method="post" action="
<?php echo htmlspecialchars($_SERVER['PHP_SELF']);
?>">
<select name="multilistname[]"
multiple="multiple" size="3">
<option value="php3"><?php
if (in_array('php3', getFormDataArrayPOST
('multilistname'))) {
echo ' selected="selected"';
}
?>PHP 3</option>
<option value="php4"><?php
if (in_array('php4', getFormDataArrayPOST
('multilistname'))) {
echo ' selected="selected"';
}
?>PHP 4</option>
<option value="php5"><?php
if (in_array('php5', getFormDataArrayPOST
('multilistname'))) {
echo ' selected="selected"';
}
?>PHP 5</option>
</select><br />
<input type="submit" />
</form>
</body>
</html>
```

预填充多选列表 (select-multiple-cookie.php; 摘录)

### 处理图形提交按钮

```
if (isset($_POST['Submit_x']) && isset($_POST['Submit_y']))
```

图形提交按钮（<input type="image" />）不仅是美化表单布局的好方法，还提供了一个不错的功能：浏览器在点击按钮时会提交鼠标指针的 x 和 y 坐标。在 PHP 中，这是通过在按钮的 name 属性后附加 _x 和 _y 并将其写入 $_GET 或 $_POST 来实现的。 前面的代码评估了这些信息。

```
<?php
if (isset($_POST['Submit_x']) && isset($_POST['Submit_y'])) {
    printf('<h1>You clicked at the following coordinates: x-%s, y-%s</h1>',
    htmlspecialchars($_POST['Submit_x']),
    htmlspecialchars($_POST['Submit_y'])
    );
} else {
?>
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
<input type="image" name="Submit" src="sams.gif" />
</form>
<?php
}
?>
```

注意
使用键盘提交表单时（例如使用 Enter 键），两个坐标都为 0。

### 检查必填字段

```
if (isset($_POST['Submit']) &&
    isset($_POST['textfieldname']) &&
    trim($_POST['textfieldname']) != '')
```

在验证表单时，大多数情况下重点在于必填字段。你可以通过两种方式检查它们是否包含值：

- 检查字段是否存在于 $_GET/$_POST 中
  ```
  if (!isset($_GET['fieldname'])) {
    // Error!
  }
  ```
- 检查 $_GET/$_POST 中的值是否包含除空白之外的信息
  ```
  if (trim($_GET['fieldname']) == '') {
    // Error!
  }
  ```

非常重要的一点是，你必须结合使用这两种技术。你始终必须使用 isset() 检查字段是否存在，以避免在尝试访问不存在的数组值时出现错误消息。但你始终必须检查字段中除空白之外是否还有内容，因为文本字段总是会被提交。此外，当为空时，isset() 始终返回 true，与字段的值无关。

### 检查必填字段

```
<?php
    if (isset($_POST['Submit']) &&
        isset($_POST['textfieldname']) &&
        trim($_POST['textfieldname']) != '') {
    echo '<h1>Thank you for filling out this
        form!</h1>';
    } else {
?>
    <form method="post" action="
<?php echo htmlspecialchars($_SERVER['PHP_SELF']);
    ?>">
        <input type="text" name="textfieldname"
            value="<?php
echo (isset($_POST['textfieldname'])) ?
    htmlspecialchars($_POST['textfieldname']) : '';
?>">
        <input type="submit" name="Submit" />
    </form>
<?php
    }
?>
```

*验证必填字段 (mandatory.php; 摘录)*

提示

该方法也适用于所有其他文本表单元素、单选按钮和复选框。它可以很容易地扩展以检查某些模式，包括有效的电子邮件地址。请参阅第 2 章“使用数组”，以获取在此处可能有帮助的短语。

注意

表单元素的预填充代码已被保留 intact，以便此代码片段可以与其他代码片段合并。因此，如果表单仅部分填写，则正确的表单字段会被预填充。

### 检查选择列表

```
isset($_POST['listname']) &&
$_POST['listname'] != ''
```

在验证选择列表时，方法取决于列表的类型：

- 如果是只能选择一个元素的列表，则在以下情况下被认为填写不正确
  - 列表中没有选项被选中
  - 选中的选项的值为空字符串
- 如果是可选择多个元素的列表，则在以下情况下被认为填写不正确
  - 列表中没有选项被选中
  - 所有选中的选项的值都为空字符串

如果列表包含无功能的占位条目，其标题例如为“Please choose from list”，则会出现值为空字符串的选项。这些列表选项必须不接收除 "" 之外的其他值，以便验证算法能够将这些条目与合理的条目区分开来。

本短语开头的列表验证单个选择列表——再次包含用于预填充列表的 PHP 代码。

```
<?php
if (isset($_POST['Submit']) &&
    isset($_POST['listname']) &&
    $_POST['listname'] != '') {
echo '<h1>Thank you for filling out this
```



### 检查选择列表

```php
form!</h1>';
} else {
?>
<form method="post" action="<?php echo
    htmlspecialchars($_SERVER['PHP_SELF']); ?>">
  <select name="listname">
    <option value="">Please select from
      list</option>
    <option value="php3"><?php
if (isset($_POST['listname'])
&& $_POST['listname'] == 'php3') {
  echo ' selected="selected"';
}
?>>PHP 3</option>
    <option value="php4"><?php
if (isset($_POST['listname'])
&& $_POST['listname'] == 'php4') {
  echo ' selected="selected"';
}
?>>PHP 4</option>
    <option value="php5"><?php
if (isset($_POST['listname'])
&& $_POST['listname'] == 'php5') {
  echo ' selected="selected"';
}
?>>PHP 5</option>
  </select><br />
  <input type="submit" name="Submit" />
</form>
<?php
}
?>
```

*验证列表 (mandatory-list.php; 摘录)*

使用多个列表时，需要做更多的工作，如以下代码所示。如果表单已被提交，则会搜索所选列表元素的数组。如果找到一个非空元素，则过程完成，可以祝贺用户成功完成表单。否则，表单会再次显示。

```php
<?php
$ok = false;
if (isset($_POST['Submit']) &&
    isset($_POST['multilistname'])) {
    if (is_array($_POST['multilistname'])) {
        for ($i=0; $i <
            count($_POST['multilistname']); $i++) {
            if ($_POST['multilistname'][$i] != '') {
                $ok = true;
                break;
            }
        }
    }
}

if ($ok) {
    echo '<h1>Thank you for filling out this
        form!</h1>';
} else {
?>
<form method="post" action="
<?php echo htmlspecialchars($_SERVER['PHP_SELF']);
?>">
    <select name="multilistname[]"
        multiple="multiple" size="5">
    </select>
<br />
    <input type="submit" name="Submit" />
</form>
<?php
}
?>
```

### 将所有表单数据写入文件

```php
$data[] = $_POST;
file_put_contents('formdata.txt',
serialize($data));
```

用户正确填写表单后，你会如何处理表单数据？一种非常直观且不需要在服务器上做太多设置的方法是将数据写入服务器上的文件。

```php
<?php
    require_once 'stripFormSlashes.inc.php';
?>
...
<?php
    if (isset($_POST['Submit']) &&
        isset($_POST['fieldname']) &&
        trim($_POST['fieldname']) != '') {
    echo '<h1>Thank you for filling out this form!</h1>';
    $data = '';
    $data = @file_get_contents('formdata.txt');
    if ($data != '') {
        $data = unserialize($data);
    }
    $data[] = $_POST;
    file_put_contents('formdata.txt',
        serialize($data));
} else {
?>
    <form method="post" action="<?php echo
        htmlspecialchars($_SERVER['PHP_SELF']); ?>">
    ...
    </form>
<?php
    }
?>
```

### 通过电子邮件发送所有表单数据

前面的代码包含一种非常天真的做法：所有数据都存储在服务器上的文件中。当表单提交时，文件会被读入并反序列化为数组。然后，表单数据会被追加到数组中。最后，数组再次被序列化并写回文件。

图 4.3 在文本编辑器中显示了此文件。

> **NOTE**
>
> 当然，可能会发生竞争条件，文件可能被两个进程同时读取，这会导致两个进程中只有一个出现在文件中。为避免这种情况，你必须实现文件锁定，如第 7 章“使数据动态化”中所示。

![](img/1e6d362f187af50011d2666ddaa68739_126_0.png)

*图 4.3 写入文件的数据（稍后可以反序列化）。*

```php
mail('recipient@domain.tld', 'Form data', $text);
```

可以通过通过电子邮件发送表单数据来实现有人填写表单的更及时通知。当然，你可以为每个表单编写自定义邮件脚本；然而，前面的代码展示了如何通用地完成此操作。通过 foreach，所有表单数据被合并成一个字符串。特别注意表单值为数组的情况——这可能发生在多个选择列表中。然后表单数据会被发送邮件给网站管理员——只要别忘了更改电子邮件地址。

```php
<?php
    require_once 'stripFormSlashes.inc.php';
?>
...
<?php
    if (isset($_POST['Submit']) &&
        isset($_POST['fieldname']) &&
        trim($_POST['fieldname']) != '' &&
        $_POST['groupname'] != '') {
    echo '<h1>Thank you for filling out this
        form!</h1>';
    $text = '';
    foreach ($_POST as $name => $value) {
        if (is_array($value)) {
            $text .= sprintf("%s: %s\n", $name, join('
            ', $value));
        } else {
            $text .= sprintf("%s: %s\n", $name, $value);
        }
    }
    mail('recipient@domain.tld', 'Form data',
        $text);
    } else {
?>
<form method="post" action="<?php echo
    htmlspecialchars($_SERVER['PHP_SELF']); ?>">
...
</form>
<?php
    }
?>
```

*发送表单数据通过电子邮件 (form-mail.php; 摘录)*

### 获取有关文件上传的信息

```php
printf('<p>Error: %s<br />
    Original name: %s<br />
    File size: %s<br />
    Temporary name: %s<br />
    MIME type: %s</p>',
$_FILES['File']['error'],
$_FILES['File']['name'],
$_FILES['File']['size'],
$_FILES['File']['tmp_name'],
$_FILES['File']['type'])
```

使用 `<input type="file" />` 将文件上传到 Web 服务器时，HTML 表单必须满足两个要求：

- `enctype` 属性必须设置为 `"multipart/form-data"`
- `method` 属性必须设置为 `"post"`

没有这些设置，文件上传将无法工作。如果 `php.ini` 中缺少以下信息，也无法工作：

```
file_uploads = On
```

但如果设置正确，获取有关文件的信息就很容易：在（超全局）数组 `$_FILES` 中，你可以在其名称下找到文件上传表单字段。然后，以下子键提供了有关上传文件的更多信息：

- `$_FILES["File"]["error"]`—错误代码（成功时为 0）
- `$_FILES["File"]["name"]`—原始文件名
- `$_FILES["File"]["size"]`—文件大小
- `$_FILES["File"]["tmp_name"]`—PHP 保存文件的临时文件名
- `$_FILES["File"]["type"]`—客户端发送的文件 MIME 类型，不可靠

```php
<?php
    if (isset($_POST['Submit']) && isset($_FILES
    ['File'])) {
        printf('<p>Error: %s<br />
            Original name: %s<br />
            File size: %s<br />
            Temporary name: %s<br />
            MIME type: %s</p>',
            $_FILES['File']['error'],
            $_FILES['File']['name'],
            $_FILES['File']['size'],
            $_FILES['File']['tmp_name'],
            $_FILES['File']['type']
        );
    } else {
?>
<form action="<?php echo
    htmlspecialchars($_SERVER['PHP_SELF']); ?>"
    method="post" enctype="multipart/form-data">
    <input type="file" name="File" />
    <input type="submit" name="Submit" value="Submit
        form" />
</form>
<?php
    }
?>
```

前面的代码输出了可用的文件信息（见图 4.4）。

![](img/1e6d362f187af50011d2666ddaa68739_130_0.png)

> **NOTE**
>
> 在处理表单字段时有一些注意事项。你可以在隐藏表单字段中提供上传文件的最大文件长度；然而，此检查随后在服务器端执行，因此最好在自己的脚本中使用 `"size"` 数组子元素自行完成。
>
> 此外，不要依赖 `"name"` 数组子元素，因为此信息（原始文件名）可能被伪造。更糟糕的是，一些浏览器并不总是发送原始文件名，而是发送其完整路径。因此，始终调用 `basename()` 仅提取文件名。

### 将上传的文件移动到安全位置

```php
move_uploaded_file(
    $_FILES['File']['tmp_name'],
    '/tmp/' . basename($_FILES['File']['name'])
)
```

当用户使用 `<input type="file" />` HTML 元素向 PHP 脚本上传文件时，PHP 会将文件存储在临时位置（在 `php.ini` 指令 `upload_tmp_dir` 中设置）并在脚本执行完成后删除它。因此，你必须在脚本内访问上传的文件。为此，PHP 包含 `move_uploaded_file()` 函数，该函数将文件从一个位置移动到另一个位置。`move_uploaded_file()` 的优点是该函数首先进行健全性检查，检查你提供的文件名是否确实是上传的文件，还是恶意用户试图诱骗你将 `/etc/passwd` 或 `C:\boot.ini` 移动到其他位置。

```php
<?php
if (isset($_POST['Submit']) && isset($_FILES['File'])) {
    $move = move_uploaded_file(
        $_FILES['File']['tmp_name'],
        '/tmp/' . basename($_FILES['File']['name'])
    );
    echo '<h1>';
    echo ($move) ? 'Moved' : 'Did not move';
    echo ' the file!</h1>';
} else {
?>
<form action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>" method="post" enctype="multipart/form-data">
```



### 将上传文件移动到安全位置

```
<input type="file" name="File" />
<input type="submit" name="Submit" value="Submit form" />
</form>
<?php
}
?>
```

*将上传文件移动至新位置（upload-move.php；摘录）*

假设路径 /tmp 存在，并且 Web 服务器和 PHP 进程对其具有写权限。那么，前面的代码会将上传的文件移动到该目录，并使用其原始文件名（并且你不用担心该文件名是否已存在）。

### PEAR 提供了什么？

以下 PEAR 包提供了有助于处理任何类型表单数据的功能：

- HTML_QuickForm 是一个使用 OOP（面向对象编程）语法创建表单的非常便捷的包，并且包含非常强大的验证和处理功能
- HTTP_Upload 有助于管理文件上传，并提供高级功能，例如为上传提供有效的扩展名

## 记住用户（Cookie 与会话）

超文本传输协议（HTTP）是一种无状态协议。简单来说：客户端（Web 浏览器）连接到 Web 服务器，发送请求，得到响应。然后连接关闭。结果是，同一客户端下一次向同一 Web 服务器发送请求时，这是一个新请求，因此 Web 服务器无法识别调用者。当然，对于必须维护状态的应用来说，这是一个问题，例如带有购物车功能的电子商务应用。

不过，你可以通过多种方式克服这一限制。基本思想是在 HTTP 响应中发送一些信息；为了做到这一点，这些信息会在之后对该服务器的所有请求中一并发送回来。存在以下可能性：

- 每次都通过 POST（即表单）发送数据
- 通过 GET（即把信息附加到请求的统一资源定位符 [URL]）发送数据
- 作为 HTTP 头的一部分（以 Cookie 的形式）发送数据

在实际项目中，会使用两种方法之一：会话（通过 GET 或 Cookie）和 Cookie。

### 理解 Cookie

Cookie 作为 HTTP 头的一部分发送，本质上是一个名值对。它们的主要缺点是可以在 Web 浏览器中停用 Cookie（也可以在代理服务器中将其过滤掉）。有些人认为 Cookie 会带来隐私问题。这部分可能是因为 John Udell 在 1997 年 3 月撰写的一篇文章，他在文章中写道，每个 Web 服务器都可以读取每个 Cookie，因此没有隐私可言。这引起了不小的轰动，但不幸的是，两个月后的更正却并没有得到那么多的关注。

事实上，Cookie 有一些限制：

- Cookie 与域名绑定，通常与发送 Cookie 的域名绑定。
- Cookie 可以与 Web 服务器上的路径绑定。
- Cookie 只包含文本信息，最多 4096 字节（包括 Cookie 名称以及名称和值之间的 = 字符）。
- 浏览器每个域名最多只能接受 20 个 Cookie，总共 300 个 Cookie（尽管有些浏览器接受更多）。

> **注意**
> （非官方的）Cookie 规范可以追溯到 Netscape，并且仍然可以在 http://wp.netscape.com/newsref/std/cookie_spec.html 获取。人们曾尝试为下一代 Cookie 创建专门的请求评论（RFC），但还没有得到任何主流浏览器的合理支持。

Cookie 作为 HTTP 头的一部分发送。如果设置了 Cookie，就会创建 HTTP 头条目 Set-Cookie。随后是 Cookie 的名称和值（两者都是字符串），以及可选的其他信息，例如过期日期、域和 Cookie 路径。例如，访问 http://www.php.net/ 时，PHP 网站会发送这个头条目（具体内容可能有所不同，尤其是在使用的语言和 IP 地址方面）：

```
Set-Cookie: COUNTRY=DEU%2C84.154.17.84; expires=Thu, 19-May-05 15:23:29 GMT; path=/; domain=.php.net
```

当浏览器（或用户）接受 Cookie 后，它会通过 HTTP 头 Cookie 发送回服务器：

```
Cookie: COUNTRY=DEU%2C84.154.17.84
```

Cookie 可以有过期日期。如果设置了过期日期，Cookie 最多存活到该日期，即所谓的持久 Cookie。之后，浏览器会自动删除该 Cookie——但也可能更早发生，例如当浏览器中的 Cookie 数量达到上限时，最旧的 Cookie 会被清除。然而，如果没有设置 Cookie 过期日期，则创建了所谓的会话 Cookie 或临时 Cookie。它在 Web 浏览器运行期间一直存在。当浏览器关闭时，该 Cookie 会被删除。

> **提示**
> 要实际查看 HTTP 头，可以使用标准 Web 浏览器的特殊扩展。对于 Mozilla 浏览器（包括 Firefox），http://livehttpheaders.mozdev.org/ 上提供的 LiveHTTPHeaders 扩展可以节省大量时间。Microsoft Internet Explorer 的用户可能对安装 ieHTTPHeaders 感兴趣，这是一个来自 http://www.blunck.info/iehttpheaders.html 的 Explorer 栏。图 5.1 显示了 Firefox 扩展在访问 PHP 主页时显示的部分输出。

![](img/1e6d362f187af50011d2666ddaa68739_137_0.png)

图 5.1 Cookie 作为 HTTP 头的一部分进行设置。

### 创建 Cookie

```
<?php
    setcookie('version', phpversion());
?>
Tried to send cookie.
```

要创建 Cookie，可以使用 PHP 函数 setcookie()。它需要以下参数；但只有第一个是必需的：

- 1. Cookie 的名称
- 2. Cookie 的值
- 3. 过期日期（UNIX 纪元格式）
- 4. 可以从 Web 服务器访问 Cookie 的路径
- 5. 可以从哪个域访问 Cookie
- 6. Cookie 是否只能通过安全（HTTP Secure [HTTPS]/Secure Sockets Layer [SSL]）连接发送

前面的代码设置了一个简单的会话 Cookie，其值为当前 PHP 版本。

图 5.2 显示了 Firefox 浏览器中的 Cookie 警告。你可以清楚地看到 Cookie 名称和脚本。

### 读取 Cookie

服务器可以访问的所有 Cookie（不是浏览器中存储的所有 Cookie！）都可以在超全局数组 $_COOKIE 中获取。foreach 循环读取所有 Cookie，并将它们以 HTML 表格形式发送给客户端。

```
<table>
<?php
  foreach ($_COOKIE as $name => $value) {
    printf('<tr><td>%s</td><td>%s</td></tr>',
      htmlspecialchars($name),
      htmlspecialchars($value));
  }
?>
</table>
```

*读取 Cookie（getcookie.php）*

![](img/1e6d362f187af50011d2666ddaa68739_139_0.png)

图 5.2 Firefox 接收 Cookie 并询问用户要做什么。

**警告**
因为 Cookie 作为 HTTP 头的一部分发送，所以必须在发送任何超文本标记语言（HTML）内容之前创建它们（除非你使用输出缓冲）。否则，你会收到类似图 5.3 所示的错误消息。

![](img/1e6d362f187af50011d2666ddaa68739_140_0.png)

图 5.3 Cookie 必须先于任何 HTML 内容发送。

注意
通常，PHP 会负责对 Cookie 值中的特殊字符进行转义（采用 URL 格式）。但是，从 PHP 5 开始，可以通过发送原始 Cookie 数据来手动完成这件事。为此，函数 setrawcookie() 接受与 setcookie() 相同的参数，但不会对 Cookie 的值进行编码。你必须使用函数 urlencode() 手动进行编码。

### 摆脱 Cookie 中的“魔法引号”

魔法引号——上一章中也曾介绍过并遭到厌恶——同样适用于 Cookie，因为它们是来自客户端的数据。因此，如果 magic_quotes 开启，单引号和双引号会被反斜杠字符转义。为了去除这些转义，可以使用这段代码。上一章中也使用了类似的代码来从表单数据（GET 和 POST 数据）中移除这些转义字符。



### 去除 Cookie 中的“魔术引号”

如果启用了 magic_quotes，则 stripslashes() 会递归应用于 $_COOKIE 中的所有数据。

```php
<?php
function stripCookieSlashes($arr) {
    if (!is_array($arr)) {
        return stripslashes($arr);
    } else {
        return array_map('stripCookieSlashes', $arr);
    }
}

if (get_magic_quotes_gpc()) {
    $_COOKIE = stripCookieSlashes($_COOKIE);
}
?>
```

*从 Cookie 中移除“魔术引号”（stripCookieSlashes.inc.php）*

此文件随后应包含在读取 cookie 的所有 PHP 脚本中，使用以下语句：

```
require_once 'stripCookieSlashes.inc.php';
```

### 设置（合理的）过期日期

Cookie 的过期日期是 setcookie() 的第三个参数。它是一个整数值；因此必须使用时间戳的 epoch 值。第 3 章“日期和时间”包含有关如何处理此类信息的大量信息。

```php
<?php
    setcookie('version', phpversion(), time() +
        21*24*60*60);
?>
```
尝试发送 cookie。

*使用相对过期日期设置 Cookie（setcookie-expiry.php）*

通常，为 cookie 设置相对过期日期（“三周后”）是一个好主意，而不是绝对日期（“2006 年 5 月底”）。如果使用绝对日期，你可能需要定期更改脚本，因为绝对过期日期可能很快到来。将过期日期设置为遥远的未来，例如 2030 年，也被认为是非常不专业的。接收此 cookie 的客户端到那时很可能早已被淘汰。

因此，使用相对日期。PHP 函数 time() 获取当前 epoch 值；然后加上你希望 cookie 存活的秒数。本段开头的代码设置了一个将存在三周的 cookie。

### 设置客户端特定的过期日期

```
setcookie('version', phpversion(),
    $_GET['time'] + 21*24*60*60);
```

请记住，cookie 何时过期的决定是在客户端做出的，使用客户端的时间设置。因此，如果客户端的日期错误（这是服务器端无法控制的）。

你的 cookie 可能比你预期的更早过期。因此，不要尝试设置仅存活一小时左右的 cookie；像夏令时（DST）这样的小事就可能破坏你的计划。

```php
<?php
if (isset($_GET['time']) && is_int($_GET['time']))
{
    setcookie('version', phpversion(),
        $_GET['time'] + 21*24*60*60);
} else {
    setcookie('version', phpversion(),
        time() + 21*24*60*60);
}
?>
```
尝试发送 cookie。

*使用特定过期日期设置 Cookie（setcookie-specific.php）*

然而，通过一点 JavaScript，可以避免这个陷阱。以下列表中的代码是客户端 JavaScript 代码，它以 epoch 值确定当前时间（客户端！）并将其发送到服务器端脚本 setcookie-specific.php。PHP 的 time() 函数与 JavaScript 的 getTime() 方法之间的主要区别在于，后者返回自 1970 年 1 月 1 日以来的毫秒数，而前者仅使用秒数。因此，JavaScript 值首先必须除以 1,000 并向下取整。

本段开头的代码可以查看此文件：传输的值被用作计算相对 cookie 过期日期的基础。

```html
<script language="JavaScript"
    type="text/javascript"><!--
    var epoche = (new Date()).getTime();
    epoche = Math.floor(epoche / 1000);
    location.replace("setcookie-specific.php?time=" +
        epoche);
//--></script>
```

### 删除 Cookie

```
setcookie('version', '', time() - 10*365*24*60*60);
```

直观地删除 cookie 的方法是将其值设置为空字符串。然而，cookie 仍然存在，只是没有值。更好的方法是再次发送一个同名的 cookie，但提供一个在过去的过期日期。同样，必须考虑不正确的本地时间设置，因此使用一个非常小的过期日期，例如今天之前 10 年。此列表实现了这一点并删除了之前列表中发送的 version cookie。在这里，两种方法结合使用：cookie 值被设置为空字符串，并且过期日期在过去。图 5.4 显示了结果：浏览器尝试通过将过期日期设置为期望时间（该时间在过去，因此 cookie 已消失）来删除 cookie。

```php
<?php
    setcookie('version', '', time() -
        10*365*24*60*60);
?>
```
尝试删除 cookie。

删除 Cookie（deletecookie.php）

![](img/1e6d362f187af50011d2666ddaa68739_145_0.png)

图 5.4 cookie 将被删除（如果用户接受）。

警告
如果尝试将过期日期设置为 0，PHP 只是跳过此参数，因此不起作用。你必须提供一个正参数，即使是 1。

### 使 Cookie 可供多个域访问

```
setcookie('version', phpversion(), 0, '.example.com');
```

服务器发送的 Set-Cookie 头的一部分是有权访问此 cookie 的域。如果未明确发送，此值默认为发送 cookie 的域。将此域设置为完全不同的值，例如广告服务器的域（所谓的第三方 cookie；用于尝试生成用户画像），并不总是有效，因为许多浏览器允许专门禁用该功能。（参见图 5.5，了解旧版 Netscape 4.x 浏览器的示例，该浏览器已具备此功能。）

```php
<?php
    setcookie('version', phpversion(), 0,
        '.example.com');
?>
```
尝试发送 cookie。

*为 Cookie 设置域（setcookie-domain.php）*

![](img/1e6d362f187af50011d2666ddaa68739_146_0.png)

图 5.5  即使是 Netscape 4.x 也允许你阻止不使用源域的 cookie。

然而，在某些情况下，要求 cookie 在多个三级域或子域上工作，例如 www.example.com、store.example.com 和 ssl.example.com。这方面的例子是拥有许多子域的大型网站，如 Amazon 和 eBay。它们要求支持所有顶级域（TLD）。为此，必须设置 cookie 的域——setcookie() 的第四个参数。这里有一个技巧：

只要包含两个点，所有域名都是有效的。因此，如果将域设置为“.example.com”，example.com 的所有三级域都可以访问此 cookie。这里有一个“但是”：http://example.com/ 上的页面无法访问此 cookie。因此，你可能想尝试将域设置为“example.com”；然而，这不符合规范，并且可能不被所有浏览器支持。

### 检查客户端是否支持 Cookie

```php
$test_temp = isset($_COOKIE['test_temp']) ?
'supports' : 'does not support';
$test_persist = isset($_COOKIE['test_persist']) ?
'supports' : 'does not support';
```

请记住 cookie 的发送方式：首先，服务器作为 HTTP 响应的<|message|>一部分将 cookie 发送给客户端。在下一个请求中，如果接受，客户端会将 cookie 发送回。因此，调用 setcookie() 然后检查 $_COOKIE 的内容是无效的。你必须等待下一个 HTTP 请求。

```php
if (isset($_GET['step']) && $_GET['step'] == '2')
{
$test_temp = isset($_COOKIE['test_temp']) ?
'supports' : 'does not support';
$test_persist = isset($_COOKIE['test_persist']) ?
'supports' : 'does not support';
setcookie('test_temp', '', time() - 365*24*60*60);
setcookie('test_persist', '', time() - 365*24*60*60);
echo "Browser $test_temp temporary cookies.<br />";
echo "Browser $test_persist persistent cookies.";
} else {
setcookie('test_temp', 'ok');
setcookie('test_persist', 'ok', time() +
14*24*60*60);
header("Location: ".$_SERVER['PHP_SELF']."?step=2");
}
?>
```

*测试浏览器 Cookie 配置（cookietest.php）*

然而，你可以使用 header() 强制客户端创建第二个请求。在第一个请求中，你设置 cookie；在第二个请求中，你检查是否成功。

在之前的代码中，设置了两个 cookie，一个临时 cookie 和一个持久 cookie——因为可以配置某些浏览器以接受一种 cookie 而不接受另一种。然后，使用 header() 和 Location: HTTP 头进行重定向，并检查 cookie(s) 的存在。

当然，你应该配置浏览器在 cookie 到达时显示消息窗口；这使得调试变得容易得多。



### 在单个 Cookie 中保存多个数据

```
setcookie('cookiedata', serialize($cookiedata))
```

通常，一个 cookie 只有一个值：一个字符串。因此，要在 cookie 中存储多个数据，就必须使用多个 cookie。然而，这可能会带来一些问题，例如每个域名只能有 20 个 cookie 的限制。因此，尝试在单个 cookie 中保存多个数据是有意义的。为此，自然会想到使用数组。

然而，cookie 的值只允许是字符串。因此，必须使用 serialize() 将数组转换为字符串，然后可以使用 unserialize() 将其转换回数组。

```
<?php
    require_once 'stripCookieSlashes.inc.php';

    function setCookieData($arr) {
        $cookiedata = getAllCookieData();
        if ($cookiedata == null) {
            $cookiedata = array();
        }
        foreach ($arr as $name => $value) {
            $cookiedata[$name] = $value;
        }
        setcookie('cookiedata',
            serialize($cookiedata),
            time() + 30*24*60*60);
    }

    function getAllCookieData() {
        if (isset($_COOKIE['cookiedata'])) {
            $formdata = $_COOKIE['cookiedata'];
            if ($formdata != '') {
                return unserialize($formdata);
            } else {
                return array();
            }
        } else {
            return null;
        }
    }

    function getCookieData($name) {
        $cookiedata = getAllCookieData();
        if ($cookiedata != null &&
            isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
        return '';
    }
?>
```

*用于将多个值保存到一个 Cookie 中的辅助库（getCookieData.inc.php）*

为此，你可以编写一个库，它与上一章中用于将表单数据保存到 cookie 中的库非常相似。一个名为 cookiedata 的 cookie 以关联数组的形式包含所有值。函数 getCookieData() 返回一个特定的值，而 setCookieData() 接受一个数组并将其内容写入 cookie。前面的清单显示了这个库的完整代码。

下面的清单使用这个库来实现之前章节中的 cookie 测试。

```
<?php
    require_once 'getCookieData.inc.php';

    if (isset($_GET['step']) && $_GET['step'] == '2')
    {
        $test = (getCookieData('test') == 'ok') ?
            'supports' : 'does not support';
        echo "Browser $test cookies.";
    } else {
        setCookieData(array('test' => 'ok'));
        header("Location: ".$_SERVER['PHP_SELF']."?step=2");
    }
?>
```

### 保存用户的语言偏好

```
setcookie('Lang', $_SERVER['PHP_SELF'], time() + 30*24*60*60, '/')
```

许多网页都是多语言的。此外，它们通常被组织为每个本地化部分都位于自己的目录中，类似于下面这种方法：

- 英语版本位于 en 目录中。
- 西班牙语版本位于 es 目录中。
- 法语版本位于 fr 目录中。

你可以通过几种不同的方式检测用户的语言：

- 尝试将客户端的 IP 地址关联到地理区域
- 通过读取 Accept-Language HTTP 头来确定用户偏好的语言
- 直接询问用户

尽管所有这些方法在某种程度上都可行，但最后一种（或几种方法的组合）被认为是最用户友好的。因此，你确实需要一个提供指向所有三个版本链接的首页。这就是简单的 HTML，如下所示：

```
<a href="en/index.php">English version</a><br />
<a href="es/index.php">Versión español</a><br />
<a href="fr/index.php">Version française</a>
```

*链接到各种语言版本的首页（multilingual.php；节选）*

现在，每个语言目录都有一个特定语言的 index.php 文件。该文件包含了本部分开头清单中的代码。这段代码会检查是否已经存在语言 cookie。如果不存在，它会尝试使用当前路径（从 $_SERVER['PHP_SELF'] 获取）设置一个 cookie。

```
<?php
  if (!isset($_COOKIE['lang']) ||
      $_COOKIE['lang'] != $_SERVER['PHP_SELF']) {
    setcookie('lang', $_SERVER['PHP_SELF'],
      time() + 30*24*60*60, '/');
  }
?>
```

*将当前路径保存到 Cookie 中（saveLanguage.inc.php）*

> 注意
> 将 cookie 的路径设置为 Web 服务器的根目录非常重要。否则，路径默认为当前路径，cookie 将自动仅在当前目录及其子目录中可读，而在首页上不可读。

最后，你必须在首页上检查 cookie 是否存在，如果存在，则将用户重定向到相应的页面。为此，必须将以下代码添加到 multilingual.php 页面的顶部。

```
<?php
    if (isset($_COOKIE['lang']) && $_COOKIE['lang'] != '' ) {
        header("Location: ".$_COOKIE['lang']);
    }
?>
```

### 理解会话

最初，会话是指用户对网站的一次访问。用户点击一些链接，浏览几个页面，然后离开。这就定义了一个会话。或者换句话说：如果用户在一段时间内（例如 20 分钟）没有向网站请求任何数据，会话就会结束。

HTTP 没有任何会话机制；该协议是无状态的。不过，PHP 内置了会话支持，使得使用会话变得相当容易。

创建会话后，PHP 会生成一个会话 ID，即一个标识该会话的长字符串。然后，PHP 会为这个会话创建一个文件或数据库条目。接着，PHP 应用程序可以将数据存储在此会话中。这些数据随后会被写入会话文件或数据库（共享内存是另一种选择，但很少使用）。

因此，客户端和服务器之间必须传输的只有会话 ID。与会话相关的所有其他数据都驻留在服务器端。这样，敏感数据就不会被不必要地在网络上多次传输。

PHP 会话机制的配置完全在 php.ini 配置文件的 [session] 部分进行。默认设置可能不适用于所有应用程序，因此接下来的几个部分将介绍一些可能的配置。

### 在何处存储会话

通常，会话数据存储在文件中。这些文件的位置由 php.ini 指令 session.save_path 设置。当然，该路径必须 (a) 存在，并且 (b) 对 PHP 进程（通常是 Web 服务器进程）可读可写。否则，会话信息将无法存储。

然而，当你有大量用户和因此产生的大量会话时，PHP 不应将所有会话文件放在一个目录中，因为这可能会导致严重的性能问题。以下语法允许 PHP 将会话数据移动到多个子目录中：

```
session.save_path = "n;/tmp"
```

这会在 /tmp 目录内创建深度不超过 n 级的子目录。但是，这些子目录必须存在，PHP 的会话机制才能写入其中；为此，在 ext/session 目录中有一个 shell 脚本 mod_files.sh。

当然，只有 Web 服务器应被允许读取此目录；否则，系统中的其他用户可能能够读取可能包含敏感数据的会话信息。

### 如何维持会话状态

会话 ID 必须在每个响应中发送到浏览器，而且——更重要的是——必须在每个请求中发送回服务器。

最简单的方法是使用 cookie。然后，PHP 会向客户端发送一个名为 PHPSESSID 的 cookie（可以通过 session.name 指令更改）。然而，要实现这一点，必须设置以下 php.ini 指令：

```
session.use_cookies = 1
```

然而，如果客户端不支持 cookie 该怎么办？这时，第二种机制就会发挥作用，即以下指令：

```
session.use_trans_sid = 0
```

然后，PHP 会自动回退到一种模式，在该模式下，会话 ID 会自动附加到所有 URL。这可能会带来一些潜在的安全风险（例如会话固定和会话劫持），但也非常实用。所有相关的电子商务网站都使用这种机制，例如亚马逊。如果


你访问他们的网站并加载一个页面，会话 ID 会自动附加到 URL 的末尾。

要使用 `session.use_trans_sid`，PHP 必须使用开关 `--enable-trans-sid` 编译，这对于 Windows 和 Mac OS X 二进制文件是自动完成的。

另一个选项是只允许在 URL 中使用 cookie，而不是会话 ID。为此，你可以使用以下 php.ini 指令：

```
session.use_only_cookies = 1
```

> **注意**
> URL 中的会话 ID 通常是不好的；因为人们可能会书签保存这些信息，一些搜索引擎将不会索引你的网站，等等。然而，每个电子商务网站（以及大多数其他网站）都必须考虑到一些访客（潜在客户！）只是不喜欢或不支持 cookie。在这里，会话提供了一种方便的方式来克服这一限制。

### 激活会话

### session_start()

使用会话管理始终需要资源，因此会消耗性能。因此，会话必须被激活。因为 cookie 可能是其中的一部分，所以必须在任何 HTML 内容发送到客户端之前完成。这可以通过两种方式实现：

- 使用 php.ini 指令 `session.auto_start = 1` 全局激活会话。

- 使用函数 `session_start()` 按脚本激活会话。

从性能角度来看，后者是最佳选择。

```
<?php
session_start();
echo 'Sessions activated.';
?>
```

激活会话 (session_start.php)

### 读取和写入会话

```
<?php
session_start();
echo 'Sessions activated.<br />';
$_SESSION['version'] = phpversion();
echo 'Session data written.<br />';
echo "Session data read: {$_SESSION['version']}.";
?>
```

所有会话数据都可以通过 `$_SESSION` 数组从 PHP 脚本访问。因为数据本身存储在服务器端，你可以写入会话数据并在下一个 PHP 语句中读取，而不需要像 cookie 那样进行服务器往返。只需记住先调用 `session_start()` 然后访问 `$_SESSION`。前面的列表创建了一个会话文件，如图 5.6 所示。

![](img/1e6d362f187af50011d2666ddaa68739_158_0.png)

图 5.6 由列表 5.16 创建的会话文件的内容。

### 关闭会话

### session_destroy()

在某些情况下，例如用户注销时，所有会话数据都应被删除，并且会话必须关闭。当然，可以使用 `foreach` 遍历 `$_SESSION` 然后将每个值设置为空字符串或 null，但有更快的方法：调用 `session_destroy()`。之后，当前会话中的所有数据将被销毁，正如函数名所暗示的那样。

```
<?php
    session_start();
    echo 'Before: <pre>';
    print_r($_SESSION);
    echo '</pre>After: <pre> ';
    session_destroy();
    print_r($_SESSION);
    echo '</pre>';
?>
```

删除所有会话数据 (session_destroy.php)

### 更改会话 ID

### session_regenerate_id()

针对使用会话保护的网站的一种常见攻击是用户的会话 ID 以某种方式被窃取（例如，通过分析 HTTP 请求中的 HTTP_REFERER 条目），然后被用来冒充该特定用户。这很难防范，但一种方便的方法是每当发生“重要”事件时更改会话 ID，例如用户登录时。例如，亚马逊要求已通过 cookie 身份验证的用户在下单时再次登录。

```
<?php
ob_start();
session_start();
echo 'Old: ' . session_id();
session_regenerate_id();
echo '<br />New: ' . session_id();
ob_end_flush();
?>
```

*更改会话 ID (session_regenerate_id.php)*

在这种情况下，函数 `session_regenerate_id()` 只是更改当前会话 ID，但保留所有数据不变。这在前面的代码中显示，其中使用 `session_id()` 函数检索当前会话 ID（新旧皆是）。图 5.7 显示了此脚本的可能输出。

> 此代码使用输出缓冲——`ob_start()` 和 `ob_end_flush()`——因为 `session_regenerate_id()` 也必须在任何 HTML 输出发送到客户端之前调用。

![](img/1e6d362f187af50011d2666ddaa68739_160_0.png)

图 5.7 两个会话 ID，一个是旧的，一个是新的。

### 创建动态、会话感知的链接

```
$sname = urlencode(session_name());
$id = urlencode(session_id());
echo "<a href=\"page.php?$sname=$id\">dynamic link</a>";
```

使用 `session.use_trans_sid` 自动更新所有链接以包含会话 ID（如果需要）是件好事；然而，如果这些链接是由 PHP 动态生成的，则不起作用。然而，PHP 提供了两个函数，提供所需的所有信息：

- `session_name()` 返回会话的名称。
- `session_id()` 返回当前会话的 ID。

因此，前面的代码创建了一个包含此信息的动态链接，使程序员能够使动态链接具有会话感知能力。

此代码的一种潜在输出如下：

```
<a href="page.php?PHPSESSID=5b25b64843fad0d1afb4286cfe0ed448">dynamic link</a>
```

> **提示**
>
> 当你使用 HTML 表单时，PHP 会自动将会话 ID 附加到表单的 `action` 属性。然而，如果你想使用动态表单，可以向表单添加一个隐藏表单字段，包含会话信息：

```
<?php
$name = htmlspecialchars(session_name());
$id = htmlspecialchars(session_id());
echo "<input type=\"hidden\" name=\"$name\" value=\"$id\" />";
?>
```

### 实现自定义会话管理

```
session_set_save_handler(
'sess_open', 'sess_close', 'sess_read',
'sess_write', 'sess_destroy', 'sess_gc');
```

不将会话数据存储在文件中有一些很好的理由。性能可能是一个问题，安全性是另一个问题。存储会话信息的一种替代方法是使用数据库。为此，你只需要一个名为 `sessiondata` 的数据库表，包含三列（名称可能有所不同，但必须在即将到来的列表中使用）：

- 列 `id`（主键）类型为 `VARCHAR(32)`，包含会话 ID。
- 列 `data` 类型为 `TEXT`，包含会话数据。
- 列 `access` 类型为 `VARCHAR(14)`，包含对会话信息最近访问的时间戳。

使用哪种数据库并不重要。本书使用 MySQL 和 PHP 5 的新 `mysqli` 扩展；然而，将代码更改为适用于其他数据库也很简单（请参阅第 7 章，“Making Data Dynamic”，了解有关使用 PHP 使用许多相关数据库的信息）。

PHP 函数 `session_set_save_handler()` 可用于为 PHP 内部使用的所有相关六个会话操作提供自定义函数：

- 打开会话
- 关闭会话
- 读取会话变量
- 写入会话变量
- 销毁会话
- 清理（垃圾回收，例如从数据存储中删除旧会话数据）

对于这六个操作，以下列表包含从 MySQL 数据源读取和写入会话数据的代码。你只需要 PHP 5 并适当设置连接参数（服务器、用户名、密码）。然后，使用 `require_once` 包含此列表中的代码，然后像往常一样使用会话。在后台，PHP 然后将所有会话信息保存在数据库中，而不是文件系统中。

```
<?php
$GLOBALS['sess_server'] = 'localhost';
$GLOBALS['sess_db'] = 'sessions';
$GLOBALS['sess_username'] = 'user';
$GLOBALS['sess_password'] = 'pass';

function sess_open() {
    $GLOBALS['sess_mysqli'] = mysqli_connect(
        $GLOBALS['sess_server'],
        $GLOBALS['sess_username'],
        $GLOBALS['sess_password']
    );
```

### 实现自定义会话管理

```php
mysqli_select_db($GLOBALS['sess_mysqli'],
    $GLOBALS['sess_db']);
}

function sess_close() {
    mysqli_close($GLOBALS['sess_mysqli']);
}

function sess_read($id) {
    $result = mysqli_query(
        $GLOBALS['sess_mysqli'],
        sprintf('SELECT data FROM sessiondata WHERE id = \'%s\'',
            mysqli_real_escape_string($GLOBALS['sess_mysqli'],
            $id))
    );
    if ($row = mysqli_fetch_object($result)) {
        $ret = $row->data;
        mysqli_query(
            $GLOBALS['sess_mysqli'],
            sprintf('UPDATE sessiondata SET access=\'%s\' WHERE id=\'%s\'',
                date('YmdHis'),
                mysqli_real_escape_string($GLOBALS['sess_mysqli'],
                $id))
        );
    } else {
        $ret = '';
    }
    return $ret;
}

function sess_write($id, $data) {
    mysqli_query(
        $GLOBALS['sess_mysqli'],
        sprintf('UPDATE sessiondata SET data=\'%s\', access=\'%s\' WHERE id=\'%s\'',
            mysqli_real_escape_string($GLOBALS['sess_mysqli'], $data),
            date('YmdHis'),
            mysqli_real_escape_string($GLOBALS['sess_mysqli'], $id))
    );
    if (mysqli_affected_rows($GLOBALS['sess_mysqli']) < 1) {
        mysqli_query(
            $GLOBALS['sess_mysqli'],
            sprintf('INSERT INTO sessiondata (data, access, id) VALUES (\'%s\', \'%s\', \'%s\')',
                mysqli_real_escape_string($GLOBALS['sess_mysqli'], $data),
                date('YmdHis'),
                mysqli_real_escape_string($GLOBALS['sess_mysqli'], $id))
        );
    }
    return true;
}

function sess_destroy($id) {
    mysqli_query(
        $GLOBALS['sess_mysqli'],
        sprintf('DELETE FROM sessiondata WHERE id=\'%s\'',
            mysqli_real_escape_string($GLOBALS['sess_mysqli'], $id))
    );
    return true;
}

function sess_gc($timeout) {
    $timestamp = date('YmdHis', time() - $timeout);
    mysqli_query(
        $GLOBALS['sess_mysqli'],
        sprintf('DELETE FROM sessiondata WHERE access < \'%s\'',
            $timestamp)
    );
}

session_set_save_handler(
    'sess_open', 'sess_close', 'sess_read',
    'sess_write', 'sess_destroy', 'sess_gc');
?>
```

**提示**：下载存档中的 `session.sql` 文件包含一个用于在 MySQL 中创建数据库表的 SQL 文件。`session_mysqli_readwrite.php` 文件使用了前面代码列表中的代码，并在会话中保存了一些数据。

图 5.8 显示了数据写入后会话表中的内容。

![](img/1e6d362f187af50011d2666ddaa68739_167_0.png)

图 5.8 会话数据现在存储在数据库中。

### 使用会话创建安全区域

```php
session_start();
if (!(isset($_SESSION['authorized']) && $_SESSION['authorized'] != '')) {
    header("Location: login.php?url=".nl2br($_SERVER['PHP_SELF']));
}
```

会话可以成为保护网站某些部分的好方法。其方法很简单：在用户通过身份验证后，将此信息写入会话变量。在所有受保护的页面上，检查此会话变量是否存在。

首先，你可以检查该会话变量。本节开头的代码必须（使用 `require_once`）包含在所有只有授权用户才能访问的页面中。

前面代码将用户重定向到的 `login.php` 脚本包含一个 HTML 表单（另见图 5.9），并检查所提供的数据是否正确（你可能需要添加自己的用户和密码）。你可能已经注意到，之前的 URL 是作为 GET 参数提供的，因此，如果可用，登录代码会将用户重定向回其来源页面：

```php
<?php
    if (isset($_POST['user']) && $_POST['user'] == 'Damon' &&
        isset($_POST['pass']) && $_POST['pass'] == 'secret') {
        session_start();
        $_SESSION['authorized'] = 'ok';
        $url = (isset($_GET['url'])) ? nl2br($_GET['url']) : 'index.php';
        header("Location: $url");
    }
?>
```

*检查用户凭据（login.php；节选）*

就是这样！下载存档中的 `secret.php` 脚本包含一些相当机密的信息，并受前面代码列表中的代码保护。

![](img/1e6d362f187af50011d2666ddaa68739_169_0.png)

图 5.9 登录表单——注意 URL 中的来源页面。

### 不使用会话创建安全区域

```php
$_SERVER['PHP_AUTH_USER'] == 'Shelley' && $_SERVER['PHP_AUTH_PW'] == 'TopSecret'
```

如果使用 PHP 的会话管理进行身份验证似乎开销过大，你还有另外两种选择。首先，配置 Web 服务器，使得只有授权用户才能访问某些文件或目录。例如，Apache 用户可以使用 `.htaccess` 文件；`http://apache-server.com/tutorials/ATusing-htaccess.html` 包含了一些有关这方面的有用信息。Microsoft IIS 提供了访问权限的图形用户界面（GUI）管理，因此也可以这样做。

```php
<?php
if (!(isset($_SERVER['PHP_AUTH_USER']) &&
    isset($_SERVER['PHP_AUTH_PW']) &&
    $_SERVER['PHP_AUTH_USER'] == 'Shelley' &&
    $_SERVER['PHP_AUTH_PW'] == 'TopSecret')) {
    header('WWW-Authenticate: Basic realm="Secured area"');
    header('Status: 401 Unauthorized');
} else {
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
...
<?php
}
?>
```

*使用 HTTP 保护 PHP 页面（http_authentication.php；节选）*

不过，一种或多或少与平台无关的方式是通过 HTTP 进行身份验证。如果你发送 HTTP 状态码 401（未授权），浏览器会提示客户端输入用户名和密码。然后可以通过 `$_SERVER['PHP_AUTH_USER']` 和 `$_SERVER['PHP_AUTH_PW']` 获取这些信息——但前提是你将 PHP 作为服务器模块运行，而不是以通用网关接口（CGI）模式运行。

然后你可以检查这些信息，并决定是再次发送 401 头，还是显示页面的实际内容。前面的代码列表展示了该实现。图 5.10 显示了提示输入用户名和密码的界面。

![](img/1e6d362f187af50011d2666ddaa68739_171_0.png)

图 5.10 浏览器提示输入用户名和密码。

### PEAR 提供了什么？

以下 PEAR 包提供了与会话和 HTTP 身份验证相关的功能：

- Auth 实现了多种用户身份验证方式，从而保护 PHP 页面。
- HTTP_Session 基于 PHP 的会话机制，但提供了面向对象的会话信息访问方式。

## 使用服务器文件系统上的文件

尽管数据库非常普遍，但使用文件系统存储数据也是一种真正可行的替代方案。通常，以这种方式实现更容易。有时它更快，更重要的是，所有托管提供商都启用了文件访问，而数据库支持可能需要额外付费。

PHP 通过一组特定函数支持文件处理。使用包装器，同样的技术也可以用于通过超文本传输协议（HTTP）或文件传输协议（FTP）等协议访问远程数据，但这将在第 9 章“与他人通信”中更详细地介绍。

本章涵盖读取和写入文件等标准任务，以及以 ZIP 或 BZ2 格式归档文件等高级任务。其中许多任务可以用不同但同样可用的方式解决，因此你真正拥有选择的自由。

### 打开和关闭文件

```php
if ($fp = @fopen('file.txt', 'at')) {
    fclose($fp);
}
```

对于大多数文件系统函数，必须首先打开文件。`fopen()` 函数正是执行此操作，并返回所谓的文件句柄，即指向文件的指针。然后，该文件句柄可以在后续函数中使用，例如从文件中读取信息或向其写入信息。

`fopen()` 至少需要两个参数：

- 文件名
- 访问文件时使用的文件模式

```php
<?php
    if ($fp = @fopen('file.txt', 'at')) {
        echo 'File opened.';
        fclose($fp);
        echo '<br />File closed.';
    } else {
        echo 'Error opening file.';
    }
?>
```

*打开（和关闭）文件（fopen.php）*

文件模式参数非常值得关注。这是一个由一个或多个字符组成的字符串。第一个字符是 `a`、`r`、`w` 或 `x` 之一；之后可以使用一个或多个特殊修饰符。表 6.1 显示了所有模式。




### 表 6.1 PHP 文件函数的文件模式

| 模式 | 描述 |
|------|-------------|
| a | 打开文件以追加（写入）数据；如果不存在则创建 |
| a+ | 与模式 a 相同，但额外具有对文件的读取权限 |
| r | 打开文件以读取数据 |
| r+ | 与模式 r 相同，但额外具有写入权限 |
| w | 打开文件以写入数据，擦除其内容；如果不存在则创建 |
| w+ | 与模式 w 相同，但额外具有读取权限 |
| x | 创建文件以写入数据；如果已存在则发送 E_WARNING |
| x+ | 与模式 x 相同，但额外具有读取权限 |

因此修饰符 + 总是为文件模式添加缺少的读取或写入访问权限。还有其他修饰符。自 PHP 4.3.2 起，PHP 在判断文件是文本文件还是二进制文件方面做得非常好，并能适当转换奇怪的字符。如果你要在文件模式后追加 b，你将强制 PHP 以二进制文件方式打开文件；例如，文件模式 rb 以二进制模式打开文件进行读取。

还有一个特殊的修饰符可能对 Windows 用户有用：t。如果将其追加到文件模式，所有 \n 换行符将被转换为 \r\n，正如 Windows 应用程序所期望的那样。

### 打开和关闭文件

fopen() 返回文件句柄，如果打开文件失败则返回 false。然而，你应该使用 @ 字符抑制任何潜在的错误信息，或在 PHP 5 中使用 try-catch 块。

一旦文件不再使用，就应该关闭它。PHP 在脚本终止时会自动关闭所有打开的文件；然而，为了尽可能高效地使用系统资源，应尽早关闭文件以释放内存并加快系统速度。为此，使用 fclose() 并提供文件句柄作为参数。

本段开头的代码同时使用了 fopen() 和 fclose()。

运行脚本后，会创建一个名为 file.txt 的文件。

> **注意**
> 
> 为了使本章（以及本章中的其他示例）正常工作，你必须确保 PHP 脚本具有访问文件的适当权限。通常，Apache 在特殊用户 ID 0（UNIX/Linux）下运行，或在普通用户账户（Windows）下运行。使用 chmod 相应地设置访问权限。
> 
> Microsoft IIS（Internet Information Services）在名为 IUSR_<name of machine> 的特殊访客账户下运行 PHP 脚本。你可以使用图 6.1 所示的图形用户界面来调整文件或目录的访问设置。

### 提示

为了避免在尝试访问不存在的文件时出现任何错误，你可以使用 file_exists() 函数，该函数会返回给定文件名是否存在。

```
if (file_exists('file.txt')) {
  // ...
}
```

![](img/1e6d362f187af50011d2666ddaa68739_178_0.png)

图 6.1 允许 IIS 用户访问文件或目录。

### 从文件读取

```
echo file_get_contents('file.txt');
```

要从文件读取数据，PHP 提供了几种可能性。最简单的方法可能是将数据一次性全部读入然后输出给用户。

自 PHP 4.3.0 起可用的 file_get_contents() 函数以字符串形式返回文件（或流）的内容，以便进一步处理。前面的代码读取名为 file.txt 的文件并打印其内容。该函数是二进制安全的，因此不需要（或不能）使用文件模式。

file() 函数的工作方式与 file_get_contents() 相同，但以数组形式返回文件内容：每个元素是文件中的一行（包括换行符）。以下代码将此数组转换为字符串并发送到浏览器。implode() 函数将数组元素粘合在一起（参见第 2 章“使用数组”）。

```
<?php
    echo implode('', file('file.txt'));
?>
```

更简短的方法是使用 readfile()，它会直接将文件内容发送到浏览器。为了在发送前处理数据，必须使用输出缓冲。以下列表将特殊超文本标记语言（HTML）字符转换并在换行处使用 <br> 元素，以便在浏览器中显示文件的原始内容。

```php
<?php
ob_start();
readfile('text.txt');
$data = ob_get_contents();
ob_end_flush();
echo nl2br(htmlspecialchars($data));
?>
```

*使用输出缓冲将文件内容发送到浏览器（readfile.php）*

为了获得最大灵活性，可以使用手动方式；然而，对于文本文件，这通常不是必需的。使用 fopen() 打开文件，然后只要返回数据就调用 fgets()（这里使用 while 循环很方便）并输出数据。fgets() 返回其第二个参数提供的字符数，但最多为当前行末尾的所有字符。

```php
<?php
$fp = fopen('file.txt', 'r');
while (!feof($fp)) {
    $line = fgets($fp, 4096);
    echo $line;
}
fclose($fp);
?>
```

*逐行将文件内容发送到浏览器（readfile-linebyline.php）*

### 写入文件

```php
file_put_contents('file.txt',
    "-> This text file contains\nsome random text.
<-");
```

写入文件与从文件中读取一样简单——如果你使用的是 PHP 5 或更高版本。然后，file_put_contents() 函数直接将数据写入文件，并且是二进制安全的。调用函数后，文件将被关闭。代码将数据写入文件。

```
<?php
    file_put_contents('file.txt',
        "-> This text file contains\nsome random text.
        <-");
    echo 'File written.';
?>
```

将数据写入文件（file_put_contents.php）

然而，前面的代码会覆盖现有文件。如果你想追加数据（因此模拟文件模式 a），你首先必须读取文件的数据。

```
<?php
    function file_append_contents($filename, $data) {
        $olddata = @file_get_contents($filename);
        return file_put_contents($filename, 
            "$olddata$data");
    }

    file_append_contents('file.txt',
        "\n-> This text file contains\neven more random text. <-");
    echo 'Data appended to file';
?>
```

向文件追加数据（file_append_contents.php）

### 提示

提供第三个参数给 file_put_contents() 以追加数据而不是覆盖文件甚至更简单：

```
file_put_contents($filename, $data, FILE_APPEND);
```

然而，当使用低于 5.0.0 的 PHP 版本时，所有这些都会失败，因为 file_put_contents() 函数在早期版本中不存在。然而，可以为旧版 PHP 模拟 file_put_contents() 的行为。这与使用 fopen()、fgets() 和 fclose() 从文件读取的方式类似。对于写入，只需要一个额外的函数：fwrite() 将数据写入文件句柄。以下代码实现了这种方法。使用 function_exists()，你可以检查 file_put_contents() 函数是否已存在。如果不存在，你可以编写它。

```
<?php
if (!function_exists('file_put_contents')) {
    function file_put_contents($filename, $content)
    {
        if ($fp = @fopen($filename, 'w')) {
            $result = fwrite($fp, $content);
            fclose($fp);
            return $result;
        } else {
            return false;
        }
    }
}
```

```
file_put_contents('file.txt',
    "\n-> This text file contains\nsome random text. <-" );
echo 'Data written to file.';
?>
```

*使用 file_put_contents() 兼容所有相关 PHP 版本（file_put_contents_compatible.php）*

### 锁定文件

```
flock($fp, LOCK_UN);
```

在读取和写入文件时，你必须考虑并发。如果两个进程同时尝试访问文件怎么办？为了避免一个进程写入而另一个进程读取时出现问题，你必须锁定文件。这是通过 PHP 函数 flock() 完成的。

```
<?php
    if (!function_exists('file_put_contents')) {
        function file_put_contents($filename, $content)
        {
            if ($fp = @fopen($filename, 'w') && flock($fp, LOCK_EX)) {
                $result = fwrite($fp, $content);
                flock($fp, LOCK_UN);
                fclose($fp);
                return $result;
            } else {
                return false;
            }
        }
    }
?>
```



第一个参数是文件句柄；第二个参数是要使用的锁定类型。以下是可用的选项：

- LOCK_EX—用于写入的独占锁
- LOCK_NB—非阻塞锁
- LOCK_SH—用于读取的共享锁
- LOCK_UN—释放锁

前面的代码包含来自上一节的自定义 file_put_contents() 函数的更新版本，这次使用了独占锁。

### 使用相对路径进行文件访问

```php
dirname(__FILE__);
basename(__FILE__);
```

通常，文件是相对于文档路径打开（或搜索）的。如果您在 Windows 下将 PHP 用作 ISAPI 模块，则 php4ts.dll 或 php5ts.dll 的位置可能相关。为了确保您搜索的是当前脚本的路径，可以使用两步方法：

- 常量 __FILE__ 包含当前脚本的完整路径
- 函数 dirname() 确定路径的目录名称部分

```php
<?php
$directory = dirname(__FILE__);
$filename = basename(__FILE__);
print "This script is called $filename and resides in $directory.";
?>
```

### 确定目录名称和文件名 (pathinfos.php)

要使用相对路径，您现在可以调用 dirname(__FILE__) 然后附加相对路径，同时考虑目录分隔符字符，在 UNIX/Linux 上是 `/`，在 Windows 上是 `\`，在 Mac OS X 上是 `:`。通常，`/` 在大多数系统上都能正常工作，但您应注意要托管网站的系统的要求。

dirname() 的姊妹函数是 basename()；它确定路径的文件名部分。

本节开头的列表使用 basename() 和 dirname() 以及 __FILE__ 来确定当前路径的信息：目录和文件名。图 6.2 显示了脚本的输出。

![](img/1e6d362f187af50011d2666ddaa68739_185_0.png)

图 6.2 检测脚本的名称及其目录。

### 避免文件访问中的安全陷阱

一点非常重要：如果您在 PHP 中使用文件，请避免从外部来源（如用户输入或 cookie）检索文件名。这可能会允许用户在您的网站中注入危险代码或强制您加载您不想打开的文件。一些所谓的 安全专家 有一个自编程的内容管理系统，它创建了如下的统一资源定位符（URL）：`index.php?page=subpage.html`。这只是将页面 `subpage.html` 加载到某种页面模板中并发送到浏览器。但如果调用以下 URL 怎么办：`index.php?page=../../../etc/passwd`？运气好的话（或运气不好，取决于您的观点），文件 `/etc/passwd` 的内容会在浏览器中打印出来。这种攻击——所谓的目录遍历攻击——在网络上相当常见。然而，您可以通过以下几种方式避免成为受害者：

- 如果可能，不要在文件名中使用动态数据。
- 如果您必须在文件名中使用动态数据，请使用 `basename()` 来确定文件的实际名称，省略路径信息。
- 设置 `php.ini` 指令 `open_basedir`。它期望一个 PHP 可以访问文件的目录列表。PHP 在每次打开文件时都会检查 basedir 规则，如果不在适当路径中，则拒绝操作。
- 将 `include_path` 设置为存放所有待使用文件的目录，并将 `fopen()` 的第三个参数设置为 true，使用 `include_path`。

### 处理 CSV 数据

```php
fgetcsv($handle, 4096);
```

CSV 是一种文件格式，全称为逗号分隔值。许多电子表格应用程序可以将数据导出为 CSV 文件。似乎使用 explode() 将 CSV 值转换为数组很容易；然而，这实际上非常复杂。如果值中包含逗号怎么办？那么内容会被双引号包围，这使得使用 explode() 变得困难。

```php
<table>
<?php
  $fp = fopen('file.csv', 'r');
  while (!feof($fp)) {
      $line = fgetcsv($fp, 4096);
      echo '<tr><td>';
      echo implode('</td><td>', $line);
      echo '</td></tr>';
  }
  fclose($fp);
?>
</table>
```

### 读取 CSV 信息 (fgetcsv.php)

和（几乎）总是一样，PHP 项目已经完成了大部分工作并提供了 fgetcsv()。此函数的工作方式与 fgets() 相同；然而，它将行转换为数组，以逗号（或第三个参数中提供的任何其他字符）分隔内容。

fgetcsv() 的第二个参数是 CSV 文件中行的最大长度。在 PHP 5.0.0 及更高版本中这是可选的，但在之前必须设置。因此您需要检查 CSV 文件中最长行的长度；否则数据将被截断。

本节开头的代码读取 CSV 文件并将其作为 HTML 表格输出。这是通过循环中使用以下代码完成的：

```php
$line = fgetcsv($fp, 4096);
echo '<tr><td>';
echo implode('</td><td>', $line);
echo '</td></tr>';
```

这在 HTML 表格中创建一行：`<tr><td>...</td></tr>`。

图 6.3 显示了原始电子表格文件（在 OpenOffice.org 中）和浏览器中的结果。

![](img/1e6d362f187af50011d2666ddaa68739_188_0.png)

图 6.3 OpenOffice.org 中的 CSV 电子表格和浏览器中的结果（fgetcsv.php；摘录）。

> **注意**
>
> 在本节开头的代码中，输出未使用 htmlspecialchars() 进行清理——在这种情况下是为了使代码简短。然而，根据您的数据，您应考虑对 fgetcsv() 返回的数组的所有元素运行 htmlspecialchars()。

对于写入 CSV 文件，PHP 提供了一个姊妹函数 fputcsv()。您提供一个文件指针和一个值数组，PHP 会完成其余工作，包括转义特殊字符。不幸的是，该函数目前仅存在于 PHP 的 CVS 中，因此在撰写本文时，您必须手动模拟此行为。基本上，您只需用逗号连接所有数组元素。您还必须处理元素内的逗号，因此用双引号包围所有值。如果元素包含双引号，则必须转义它们。然而，这不是使用反斜杠完成的，而是通过重复引号。以下是有效 CSV 数据行的示例：

```
Quote,"And she said: ""No."" ...",Unknown
```

以下是 fputcsv() 的代码：

```php
if (!function_exists('fputcsv')) {
    function fputcsv($fp, $line, $separator = ',') {
        for ($i=0; $i < count($line); $i++) {
            if (false !== strpos($line[$i], '"')) {
                $line[$i] = ereg_replace('"', '""', $line[$i]);
            }
            if (false !== strpos($line[$i], $separator) ||
                false !== strpos($line[$i], '"')) {
                $line[$i] = '"' . $line[$i] . '"';
            }
        }
        fwrite($fp, implode($separator, $line) . "\r\n");
    }
}
```

以下代码使用我们自制的 fputcsv() 手动创建之前使用过的 CSV 文件。

```php
<?php
// ...

$data = array(
    array('April 2005', '19,720,597', '1,310,181'),
    array('January 2005', '18,455,683',
        '1,317,871'),
    array('December 2004', '17,826,404',
        '1,318,739')
);

if ($fp = @fopen('usage.csv', 'w')) {
    foreach ($data as $line) {
        fputcsv($fp, $line);
    }
    fclose($fp);
    echo 'CSV written.';
} else {
    echo 'Cannot open file.';
}
?>
```

### 写入 CSV 信息 (fputcsv.php；摘录)

此代码创建文件 usage.csv，其内容如下：

```
April 2005,"19,720,597","1,310,181"
January 2005,"18,455,683","1,317,871"
December 2004,"17,826,404","1,318,739"
```

### 解析 INI 文件

```php
parse_ini_file('php.ini', true)
```

另一种非常知名的文件格式是 INI 文件格式——它在 Windows 世界中被广泛使用，但今天也驱动着像 PHP 这样复杂软件产品的配置。例如，看看 php.ini。以下是默认 php.ini 的（修改过）摘录，很好地展示了 INI 文件的结构：

```
[mail function]
; For Win32 only.
; SMTP = localhost
; For Unix only. You may supply arguments as well
    (default: "sendmail -t -i").
sendmail_path =
```

因此，有以方括号中的节标题开头的节，以分号开头的注释，以及格式为 name=value 的设置。PHP 函数 parse_ini_file() 现在读取此类 PHP 文件并将其创建为数组：每个节都是一个子数组，在这些子数组中您可以找到 INI 文件中指令的名称和值。本节开头的代码执行此操作（如果适当，请更改 php.ini 的路径），图 6.4 显示了输出。

```php
<?php
    echo '<xmp>' .
        print_r(parse_ini_file('php.ini', true), true) .
        '</xmp>';
?>
```

提示

如果您想避免 INI 文件中的按节分组，只需省略第二个参数 parse_ini_file()；然后，您可以一次性获取所有设置。

parse_ini_file('php.ini');

![](img/1e6d362f187af50011d2666ddaa68739_192_0.png)

图 6.4 php.ini 的内容作为多维数组 (parse_ini_file.php; 摘录).

### 检索文件信息

```
$filename = __FILE__;
```

使用 PHP 访问目录和文件信息相当不寻常——至少在绝大多数 PHP 脚本通过 HTTP 在 Web 服务器上运行而不是使用命令行界面 (CLI) 或 PHP 的情况下如此。

以下列表显示了在这方面最相关的辅助函数：

- `fileatime($filename)`—最后一次访问文件
- `filegroup($filename)`—拥有文件的组
- `filemtime($filename)`—文件最后一次更改
- `fileowner($filename)`—文件所有者
- `filesize($filename)`—文件大小

另一组辅助函数也接受文件名，因此在使用这些函数之前无需打开文件：

- `is_dir($path)`—路径是否为目录
- `is_executable($filename)`—文件名是否可执行
- `is_file($path)`—路径是否为（常规）文件
- `is_link($filename)`—文件名是否为符号链接
- `is_readable($filename)`—文件是否可读
- `is_uploaded_file($path)`—路径是否是通过 HTTP 上传的文件（参见第 5 章，“记住用户（Cookies 和 Sessions）”）
- `is_writable($filename)`—文件是否可写

图 6.5 包含本节开头代码的结果。

![](img/1e6d362f187af50011d2666ddaa68739_195_0.png)

图 6.5 当前脚本的信息 (fileinfos.php).

### 复制、移动和删除文件

```php
copy($filename, $tempname1);
rename($tempname1, $tempname2);
unlink($tempname2);
```

PHP 中提供了许多操作系统的许多其他标准命令行函数。这不仅包括 chmod() 和 chgrp()，还包括以下文件系统操作：

- copy()—复制文件
- rename()—移动文件
- unlink()—删除文件

前面的代码复制当前文件，移动它（或重命名它），最后删除生成的文件。

```php
<?php
    $filename = 'php.ini';
    $tempname1 = $filename . rand();
    $tempname2 = $filename . rand();
    copy($filename, $tempname1);
    echo "Copied to $tempname1<br />";
    rename($tempname1, $tempname2);
    echo "Moved to $tempname2<br />";
    unlink($tempname2);
    echo "File deleted.";
?>
```

*复制、移动和删除文件 (copymovedelete.php)*

### 浏览文件系统

```
$d = dir('.');
while (false !== ($file = $d->read()));
```

自 PHP 3 起，PHP 就带有一个内置类。这听起来很奇怪，因为面向对象编程 (OOP) 在 PHP 5 之前并未在 PHP 中成为“主流”；然而，这个特殊类提供了几种访问文件系统的方法。可以获取目录中所有条目的列表。

```php
<?php
    $d = dir('.');
    while (false !== ($file = $d->read())) {
        echo htmlspecialchars($file) . '<br />';
    }
    $d->close();
?>
```

*使用 PHP 的 dir 类读取目录内容 (dir.php)*

您无需使用 new 关键字实例化该类，只需将所需路径作为参数提供即可。然后方法 read() 会遍历条目列表。前面的代码正是这样做的，并打印出当前目录的内容。

请注意，两个目录条目 .（当前目录）和 ..（父目录，如果您不在根目录）会被打印出来。

### 使用 PHP 流

在 PHP 中引入了 PHP 流的概念。从那时起，所有类型资源都有一个共同点：文件、HTTP 和 FTP 数据，甚至归档文件格式。有关此网络方面的更多信息可在第 9 章“与他人通信”中更详细地找到；本章仅挑选出一些特定于文件的功能：压缩流。

```php
<?php
$filename = __FILE__;
$zipfile = "$filename.zip";

$data = file_get_contents(__FILE__);
echo 'Loaded file (size: ' . strlen($data) . ').<br />';

file_put_contents("compress.zlib://$zipfile",
    $data);
echo 'Zipped file (new size: ' . filesize
    ($zipfile) . ').<br />';

$data = file_get_contents("compress.zlib://
    $zipfile");
echo 'Original file size: ' . strlen($data) .
    '.';
?>
```

*压缩和解压缩文件 (zip.php; 摘录)*

其中之一可用于使用 ZIP 文件。伪协议 compress.zlib:// 可用于像访问常规文件一样访问 ZIP 文件。为此，您需要在 UNIX/Linux 下使用配置开关 --with-gzip；Windows 系统已包含所需的库。然后，您可以使用例如 file_get_contents() 和 file_put_contents() 使用文件。

前面的代码加载当前文件（使用 file_get_contents()），对其进行压缩，并将其写入硬盘（使用 file_put_contents()）。然后，它读取压缩文件（使用 file_get_contents()）并比较文件大小。

在测试时，代码成功将文件从 729 压缩到 336 字节。

另外，您可以使用 PHP 的内置 ZIP 函数，这些函数由 http://zziplib.sourceforge.net/ 上的 ZZ IPlib 库的包装器实现。不幸的是，它只能从 ZIP 文件读取数据，但也支持归档中的多个文件（使用流包装器 compress.zlib:// 时，您首先必须将数据打包为 tar 以支持多个文件）。

要安装，在 Windows 下在 php.ini 中使用 extension=php_zip.dll，或使用 --with-zip 配置 PHP，提供 ZZ IPlib 的路径。使用此扩展必须执行以下步骤：

- 使用 zip_open() 打开归档
- 使用 `zip_read()` 遍历归档的条目
- 使用 `zip_entry_open()` 和 `zip_entry_read()` 读取特定文件

以下代码显示 ZIP 归档的内容并确定所有条目的名称和文件大小。

```php
<?php
    $zipfile = dirname(__FILE__) . '/archive.zip';
    if ($zip = zip_open($zipfile)) {
        while ($file = zip_read($zip)) {
            printf('%s (%d)<br />',
                zip_entry_name($file),
                zip_entry_filesize($file)
            );
        }
        zip_close($zip);
    }
?>
```

*使用 ZZIPLib 解压缩文件 (zziplib.php)*

### 使用 Bzip2 归档

```
file_put_contents('compress.bzip2://$bzip2file', $data);
```

另一个并非所有操作系统都附带但提供出色压缩率的文件格式是 Bzip2。在这里，PHP 也有一个内置流包装器：`compress.bzip2://`。要使用它，您必须从 http://sources.redhat.com/bzip2/ 加载 Bzip2 库。然后使用配置开关 `--with-bzip2`（UNIX/Linux），或在 `php.ini` 配置文件（Windows）中写入 `extension=php_bzip2.dll`。然后您就可以开始压缩或解压缩文件，

正如前面的代码所示，它使用 file_get_contents() 和 file_put_contents()。

```php
<?php
$filename = __FILE__;
$bzip2file = "$filename.bz2";

$data = file_get_contents(__FILE__);
echo 'Loaded file (size: ' . strlen($data) . ').<br />';

file_put_contents("compress.bzip2://$bzip2file", $data);
echo 'Bzipped file (new size: ' . filesize($bzip2file) . ').<br />';

$data = file_get_contents("compress.bzip2://$bzip2file");
echo 'Original file size: ' . strlen($data) . '.';
?>
```

*使用 Bzip2 压缩和解压缩文件 (bzip2.php; 摘录)*

另外，您可以使用 PHP 的特殊 Bzip2 函数。它们的工作方式与 PHP 的文件函数非常相似。然而，对于写入，您必须使用 bzopen()、bzwrite() 和 bzclose() 代替 fopen()、fwrite() 和 fclose()，如下面的代码所示，它创建了一个函数 file_put_bzip2_contents()。

```php
<?php
function file_put_bzip2_contents($filename, $content) {
    if ($fp = @bzopen($filename, 'wb')) {
        $result = bzwrite($fp, $content);
        bzclose($fp);
        return $result;
```



```
} else {
    return false;
}
}

file_put_bzip2_contents('file.txt.bz2',
    "\n-> This text file contains\nsome random text.
    <-" );
echo 'Data written to file.';
?>
```

### *使用 BZip2 压缩文件 (bzip2write.php)*

另一个方向（从 BZip2 归档中读取文件）与读取普通文件类似。不是使用 fopen()、fread() 和 fclose()，而是使用 bzopen()、bzread() 和 bzclose()，如下面的代码所示，该代码编写了函数 file_get_bzip2_contents()。

```
<?php
function file_get_bzip2_contents($filename) {
    $result = '';
    if ($fp = @bzopen($filename, 'wb')) {
        while ($data = bzread($fp, 4096)) {
            $result .= $data;
        }
        bzclose($fp);
        return $result;
    } else {
        return false;
    }
}

echo nl2br(htmlspecialchars(
    file_get_bzip2_contents('file.txt.bz2')
));
?>
```

### 使用 HTTP 请求返回文件

```
$filename = 'httpfile.zip';
header("Content-Disposition: attachment; filename = $filename");
```

当 PHP 脚本需要返回（可下载的）文件而不是 HTML 时，必须发送正确的 HTTP 头：

- Content-Disposition 用于文件的（建议）名称
- Content-Length 用于文件大小
- Content-Type 用于文件的 MIME 类型

前面的代码读取 ZIP 文件并将其发送给客户端；图 6.6 显示了其在浏览器中的结果。

```
<?php
$filename = 'httpfile.zip';
$mimetype = 'application/zip';
$data = file_get_contents($filename);
$size = strlen($data);
header("Content-Disposition: attachment; filename = $filename");
header("Content-Length: $size");
header("Content-Type: $mimetype");
echo $data;
?>
```

使用 HTTP 发送文件 (httpfile.php)

### 使用 HTTP 请求返回文件

![](img/1e6d362f187af50011d2666ddaa68739_203_0.png)

图 6.6  浏览器想要保存文件。

### PEAR 提供了什么？

以下 PEAR 包提供了可用于处理文件和流的功能：

- File 提供了一些用于文件访问的辅助函数，部分功能在较新的 PHP 版本中已从已弃用到新的功能
- File_Find 在路径中搜索特定文件或模式
- File_SearchReplace 在文件中执行搜索和替换
- Stream_Var 允许您将变量保存到流中，以便您可以像访问文件或流一样访问它们

## 使数据动态化

PHP 的主要优势之一是对大量数据库的支持。非常经常，PHP 和 MySQL 被视为一个整体。然而，其他数据库也有其优势——例如，MySQL 花了很长时间才支持在其他系统中被视为标准的功能；然而，MySQL 以速度很快而闻名。

本章涉及相当多的数据库并展示了与它们的基本操作：连接、发送 SQL 语句以及评估返回值。无论您的数据库驱动 Web 应用程序必须做什么，它总是必须执行这些步骤。

为了拥有一些测试数据，我们在关系数据库管理系统（RDBMS）中创建了一个名为 phrasebook 的数据库，并在其中放置了一个名为 quotes 的表。该表由四个字段组成：

- id—一个整数值，每向数据库输入一条新记录就会增加 1。根据数据库系统，数据类型称为 IDENTITY、auto_increment 或类似名称。
- quote—引语，类型为 VARCHAR(255)；此长度适用于所有系统。
- author—产生引语的人，类型为 VARCHAR(50)。
- year—引语产生的年份（有时这高度推测性），类型为 INT。

每个数据库系统都附带管理工具或可用的第三方产品。例如，图 7.1 所示的基于 PHP 的 phpMyAdmin (http://www.phpmyadmin.net/) 为 MySQL 安装提供了非常好的访问。

![](img/1e6d362f187af50011d2666ddaa68739_205_0.png)

图 7.1 使用 phpMyAdmin 管理 MySQL 安装。

### 连接到 MySQL

```
@mysql_connect('localhost', 'user', 'password')
```

PHP 可用两种 MySQL 扩展。较旧的 ext/mysql 用于 PHP 4 及更早版本；较新的 ext/mysqli（i 官方代表 improved，unofficially 代表 incompatible——但这是愤世嫉俗的）随 PHP 5 提供，但需要 MySQL 4.1 或更高版本。然而，PHP 5 也支持旧扩展。本章涵盖了这两种扩展。

```
<?php
if ($db = @mysql_connect('localhost', 'user', 'password')) {
    mysql_select_db('phrasebook', $db);
    echo 'Connected to the database.';
    mysql_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

*连接到 MySQL (mysql_connect.php)*

要使用这些扩展，您可能需要启用它们。在 PHP 4 下，ext/mysql 自动激活。在 PHP 5 下，您必须使用 extension=php_mysql.dll 并将 libmysql.dll 复制到 PHP 可以找到的位置。如果您自行编译 PHP，请对旧版 MySQL 和 ext/mysql 使用开关 --with-mysql=/path/to/mysql。

现在连接到数据库很容易：只需调用 mysql_connect()，提供服务器、用户名和

密码。然后您将获得一个句柄，可用于 mysql_select_db() 或在服务器上选择数据库。最后，mysql_close() 关闭与数据源的连接。

### 连接到 MySQLi

```
@mysqli_connect('localhost', 'user', 'password')
```

如果您想使用 ext/mysqli，-with-mysql 的开关必须指向 /path/to/mysql_config。Windows 用户必须使用文件 php_mysqli.dll 和 libmysqli.dll，其余之前的安装说明保持不变。

```
<?php
if ($db = @mysqli_connect('localhost', 'user', 'password')) {
    mysqli_select_db($db, 'phrasebook');
    echo 'Connected to the database.';
    mysqli_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

*连接到 MySQLi (mysqli_connect.php)*

使用 ext/mysqli 连接到 MySQL 与使用 ext/mysql 完全一样，只是函数名后面加上了 i。

请记住，mysql(i)_select_db() 的不同变量顺序是两种扩展之间最显著的差异之一。较新的扩展希望数据库句柄排在第一位。另一个区别

在这两种扩展之间是，每当使用时，数据库句柄都是强制参数。使用 ext/mysql 时，mysql_connect() 创建的最后一个句柄是页面的当前默认句柄。另一个区别：mysqli_connect() 接受数据库名称作为可选的第四个参数，因此您可以避免使用 mysqli_select_db()。

> **注意**
> 
> 另外，mysqli 扩展还提供了一种面向对象的语法来访问数据源。虽然本章使用函数式方法使从 ext/mysql 到 ext/mysqli 的过渡尽可能无痛，但下面展示了面向对象方法是什么样的：

```
<?php
$db = new mysqli('localhost', 'user',
    'password');
$db->select_db('phrasebook');
$db->close();
?>
```

### 向 MySQL 发送 SQL

### mysqli_query()

函数 mysql_query() 和 mysqli_query() 将 SQL 发送到由句柄标识的数据库——mysql_query() 的第二个参数，mysqli_query() 的第一个参数。然而，为了避免一种称为“SQL 注入”的攻击（使用 GET 或 POST 数据注入 SQL 语句的方法），您绝对 **必须** 使用 mysql_real_escape_string() 或 mysqli_real_escape_string() 来转义任何危险字符，例如单引号。请参阅前面的和下面的

列表以了解实现。那些列表中缺少的代码（但当然包含在代码下载中）基本上是一个 HTML 表单，接受引语、作者和年份。图 7.2 显示了引语收集的 HTML 输入表单。

```
<?php
    if ($db = @mysqli_connect('localhost', 'user',
        'password')) {
        require_once 'stripFormSlashes.inc.php';
        mysqli_select_db($db, 'phrasebook');
        mysqli_query($db, sprintf(
            'INSERT INTO quotes (quote, author, year)
            VALUES (\'%s\', \'%s\', \'%s\')',
            mysqli_real_escape_string($db, $_POST
            ['quote']),
            mysqli_real_escape_string($db, $_POST
            ['author']),
            intval($_POST['year'])));
        echo 'Quote saved.';
        mysqli_close($db);
    } else {
        echo 'Connection failed.';
    }
?>
```

*向 MySQLi 发送 SQL (mysqli_query.php; 摘录)*

```
<?php
    if ($db = @mysql_connect('localhost', 'user',
        'password')) {
        require_once 'stripFormSlashes.inc.php';
        mysql_select_db('phrasebook', $db);
        mysql_query(sprintf(
            'INSERT INTO quotes (quote, author, year)
            VALUES (\'%s\', \'%s\', \'%s\')',
```



### 向 MySQL 发送 SQL

```php
mysql_real_escape_string($_POST['quote'], $db),
 mysql_real_escape_string($_POST['author'], $db),
 intval($_POST['year'])), $db);
 echo 'Quote saved.';
 mysql_close($db);
 } else {
 echo 'Connection failed.';
 }
 ?>
```

*发送 SQL 到 MySQL (mysql_query.php; 摘录)*

![](img/1e6d362f187af50011d2666ddaa68739_210_0.png)

**图 7.2** 用于清单 7.3 和 7.4 的 HTML 输入表单。

### 使用 MySQL 的预处理语句

```php
$stmt = mysqli_prepare();
mysqli_stmt_execute($stmt);
```

新的 MySQL 扩展提供了一种既避免 SQL 注入又加快 SQL 语句速度的方法：所谓的预处理语句。在其中，你为 SQL 代码中使用的任何动态数据提供占位符。然后你为这些占位符分配值。MySQL 扩展随后会处理其余所有内容，包括特殊字符的转义。

```php
<?php
if ($db = @mysqli_connect('localhost', 'user', 'password')) {
    require_once 'stripFormSlashes.inc.php';
    mysqli_select_db($db, 'phrasebook');
    $stmt = mysqli_prepare($db, 'INSERT INTO quotes (quote, author, year) VALUES (?, ?, ?)');
    $quote = mysqli_real_escape_string($db, $_POST['quote']);
    $author = mysqli_real_escape_string($db, $_POST['author']);
    $year = intval($_POST['year']);
    mysqli_stmt_bind_param($stmt, 'ssi', $quote, $author, $year);
    if (mysqli_stmt_execute($stmt)) {
        echo 'Quote saved. ';
    } else {
        echo 'Error writing quote.';
    }
    mysqli_close($db);
} else {
    echo 'Connection failed. ';
}
?>
```

首先，你使用 `mysqli_prepare()` 准备一条 SQL 语句；作为占位符字符，你使用问号：

```php
$stmt = mysqli_prepare($db, 'INSERT INTO quotes
    (quote, author, year) VALUES (?, ?, ?)');
```

然后，你将值绑定到每个参数。首先，提供 `mysqli_prepare()` 返回的语句，然后提供所有参数值的单字符代码（s 表示字符串，i 表示整数，d 表示双精度）。最后，提供一个值列表。因为这些值是通过引用使用的，所以你必须提供变量，而不是原始值。

```php
mysqli_stmt_bind_param($stmt, 'ssi', $quote,
    $author, $year);
```

最后，`mysqli_stmt_execute()` 执行预处理语句。

### 注意

ext/mysqli 扩展支持最近 MySQL 版本的一些新功能，包括事务。为此，可用以下函数：

- `mysqli_autocommit($db, false)` 禁用自动提交
- `mysqli_rollback($db)` 回滚所有待处理的事务
- `mysqli_commit($db)` 提交所有待处理的事务

> **提示**
> 使用 auto_increment 值时，函数 `mysql_insert_id()` 和 `mysqli_insert_id()` 返回上一个 INSERT SQL 语句创建的 auto_increment 字段的值。

### 检索 MySQL 查询的结果

```php
$result = mysqli_query(query);
mysql_fetch_object($result);
```

`mysql_query()` 或 `mysqli_query()` 的返回值是指向实际结果集的指针。它可用于遍历 SELECT 语句返回的完整条目列表。为此，以下函数很有用：

- `mysql_fetch_assoc()` 和 `mysqli_fetch_assoc()` 将结果集中的当前行作为关联数组返回（字段名变为键），并移动到下一行。
- `mysql_fetch_object()` 和 `mysqli_fetch_object()` 将结果集中的当前行作为对象返回（字段名变为属性），并移动到下一行。
- `mysql_fetch_row()` 和 `mysqli_fetch_row()` 将结果集中的当前行作为数字数组返回，并移动到下一行。

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
    if ($db = @mysqli_connect('localhost', 'user', 'password')) {
        mysqli_select_db($db, 'phrasebook');
        $result = mysqli_query($db, 'SELECT * FROM quotes');
        while ($row = mysqli_fetch_object($result)) {
            printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
                htmlspecialchars($row->id),
                htmlspecialchars($row->quote),
                htmlspecialchars($row->author),
                htmlspecialchars($row->year)
            );
        }
        mysqli_close($db);
    } else {
        echo '<tr><td colspan="4">Connection failed.</td></tr>';
    }
?>
</table>
```

*从 MySQL 检索数据 (mysqli_fetch.php; 摘录)*

还有其他函数；然而，这三个是最常用的。以下代码使用 `mysql_fetch_assoc()`，而前面的清单使用 `mysqli_fetch_object()` 打印出数据库表的内容。主要思路是使用 while 循环——所有 `mysql_fetch_*`/`mysqli_fetch_*` 函数在结果集中没有剩余数据时会返回 false。

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
    if ($db = @mysql_connect('localhost', 'user',
        'password')) {
    mysql_select_db('phrasebook', $db);
    $result = mysql_query('SELECT * FROM quotes',
        $db);
    while ($row = mysql_fetch_assoc($result)) {
        printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
            htmlspecialchars($row['id']),
            htmlspecialchars($row['quote']),
            htmlspecialchars($row['author']),
            htmlspecialchars($row['year'])
        );
    }
    mysql_close($db);
} else {
    echo '<tr><td colspan="4">Connection failed.</td></tr>';
}
?>
</table>
```

*从 MySQL 检索数据 (mysql_fetch.php; 摘录)*

图 7.3 显示了一些（政治）引语填入后数据库的内容。抱歉，我来自国外——我取了找到的第一批。

![](img/1e6d362f187af50011d2666ddaa68739_216_0.png)

**图 7.3** 数据库的内容。

### 连接到 SQLite

```php
@sqlite_open('quotes.db', 0666, $error)
```

从 PHP 5 开始，SQLite 已捆绑在脚本语言中。这是一个轻量级的文件型数据库。这允许非常快速的读取（在许多情况下，甚至比使用“真实”数据库更快），但写入有时可能比其他系统更慢，因为文件锁定是一个问题。然而，PHP 4 用户也可以使用 SQLite，因为在 http://pecl.php.net/ 上有一个 PECL（PHP 扩展社区库）模块可用。

```php
<?php
if ($db = @sqlite_open('quotes.db', 0666, $error))
{
echo 'Connected to the database.';
sqlite_close($db);
} else {
echo 'Connection failed: ' . htmlspecialchars
    ($error);
}
?>
```

*连接到 SQLite (sqlite_open.php)*

如果使用 PHP 5，SQLite 支持已包含在内；使用 PHP 4 时，使用 `pear install SQLite`，或当 Windows 是你选择的系统时，从 http://snaps.php.net/win32/PECL_STABLE/php_sqlite.dll 加载当前的 SQLite 二进制扩展，将其复制到 PHP 的扩展文件夹，然后在 `php.ini` 中使用 `extension=php_sqlite.dll` 加载它。

然后，你可以使用 `sqlite_open()` 连接到 SQLite 数据源。作为第一个参数，你提供数据库文件名（如果尚不存在则会创建）。为此，PHP 进程需要对文件具有读写权限。第二个参数是文件打开模式（建议使用 0666）；然而，截至本文撰写时，该参数被忽略。第三个参数是一个包含任何错误消息的变量（如权限不足）。

### 注意

就像 ext/mysqli 一样，PHP 5 下的 SQLite 扩展也可以使用面向对象编程（OOP）方法访问：

```php
<?php
$db = new SQLiteDatabase('quotes.db');
echo 'Connected to the database.';
$db->close();
?>
```

为了向后兼容，本章在后续示例中使用函数式方法。

### 向 SQLite 发送 SQL

### sqlite_exec()

PHP 函数 `sqlite_exec()` 将 SQL 语句发送到数据库。作为第一个参数，使用由 `sqlite_open()` 返回的数据库句柄；第二个参数是 SQL 字符串。为了避免 SQL 注入，PHP 函数 `sqlite_escape_string()` 对动态数据中的危险字符进行转义。以下代码对此进行了实现，示例表 quotes 也在 MySQL 示例中使用过。

```php
<?php
if ($db = @sqlite_open('quotes.db', 0666, $error))
{
require_once 'stripFormSlashes.inc.php';
sqlite_exec($db, sprintf(
'INSERT INTO quotes (quote, author, year)
VALUES (\'%s\', \'%s\', \'%s\')',
sqlite_escape_string($_POST['quote']),
sqlite_escape_string($_POST['author']),
intval($_POST['year'])));
echo 'Quote saved.';
sqlite_close($db);
} else {
echo 'Connection failed: ' . htmlspecialchars
($error);
}
?>
```

*向 SQLite 发送 SQL (sqlite_exec.php; 摘录)*




> 提示
> 如果表包含标识列（使用 SQLite 时数据类型为 `INTEGER PRIMARY KEY`），在发送 SQL 语句后调用 `sqlite_last_insert_rowid()` 会返回该列在数据库中新条目的值。

### 检索 SQLite 查询结果

```
$result = sqlite_query($db, 'SELECT * FROM quotes');
sqlite_fetch_array($result);
```

前面提到的 `sqlite_exec()` 函数执行速度非常快；但是，无法访问通过它发送的 SQL 语句的返回值。为此，必须使用 `sqlite_query()`。该函数返回查询结果集的一个句柄。然后可以使用以下函数遍历结果集：

- `sqlite_fetch_array()` 将结果集中的当前行作为关联数组返回（字段名成为键），并继续移动到下一行。
- `sqlite_fetch_object()` 将结果集中的当前行作为对象返回（字段名成为属性），并继续移动到下一行。
- `sqlite_fetch_all()` 将整个结果集作为关联数组的数组返回。

```
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
  if ($db = @sqlite_open('quotes.db', 0666, $error))
  {
    $result = sqlite_query($db, 'SELECT * FROM
      quotes');
    while ($row = sqlite_fetch_array($result)) {
      printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
        htmlspecialchars($row['id']),
        htmlspecialchars($row['quote']),
        htmlspecialchars($row['author']),
        htmlspecialchars($row['year'])
      );
    }
    sqlite_close($db);
  } else {
    printf('<tr><td colspan="4">Connection failed:
      %s</td></tr>',
      htmlspecialchars($error));
  }
?>
</table>
```

*从 SQLite 检索数据（sqlite_fetch.php；摘录）*

前面的代码展示了如何使用 sqlite_fetch_array() 访问结果集中的所有数据。只要该函数返回的不是 false（意味着没有剩余数据），while 循环就会持续调用它。

> 提示
> 
> 使用 sqlite_fetch_all() 会一次性将整个结果集读入内存。因此，如果数据量不大，这是性能最好的方法。如果数据较多，使用 sqlite_fetch_array() 和 sqlite_fetch_object() 的迭代方法可能更好。

### 连接到 PostgreSQL

### @pg_connect()

PostgreSQL 拥有越来越多的爱好者。有些人甚至说这是因为新版本 8.0 终于推出了原生 Windows 版本。不过，大多数使用 PostgreSQL 的生产系统仍然托管在 Linux 或 UNIX 上。

安装数据库后，可以使用基于 Web 的管理软件（如 phpPgAdmin（http://sourceforge.net/projects/phppgadmin））或其他工具（如图形用户界面（GUI）应用程序 pgAdmin（http://www.pgadmin.org/））来管理数据库。或者，也可以使用命令行工具。要让 PHP 访问 PostgreSQL 安装，Windows 用户必须在 php.ini 中使用条目 `extension=php_pgsql.dll` 加载扩展；UNIX/Linux 用户使用开关 `--with-pgsql=/path/to/pgsql` 配置 PHP。

然后，pg_connect() 连接到数据源。你必须提供一个连接字符串，其中包含所有重要数据，包括主机、端口、数据库名称和用户凭据。

### 向 PostgreSQL 发送 SQL

```
 intval($_POST['year']));
    echo 'Quote saved.';
    pg_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

*向 PostgreSQL 发送 SQL（pg_query.php；摘录）*

> 注意
> 在最后一条 INSERT 语句之后检索标识列的值有点棘手。PostgreSQL 中这种数据类型的术语是 SERIAL，它会自动创建一个序列。要获取该序列的值，可以使用 pg_last_oid() 检索该值的 oid（对象 id）。然后，执行 `SELECT id FROM quotes WHERE oid=<oid>`，其中 `<oid>` 是你刚刚检索到的 oid。这将最终返回所需的值。

### 更新 PostgreSQL 中的数据

### pg_insert()

在 PostgreSQL 中插入或更新数据的另一种方式是使用 pg_insert() 和 pg_update() 函数。第一个参数必须是数据库句柄，第二个参数是要插入/更新的表，第三个参数以关联数组的形式包含一些数据（列名为键）。如果是 UPDATE SQL 语句，更新条件也必须以数组形式作为函数的第四个参数提交。前面的代码展示了如何插入数据。

```
<?php
if ($db = @pg_connect('host=localhost port=5432
dbname=phrasebook user=postgres
password=abc123')) {
require_once 'stripFormSlashes.inc.php';
$data = array(
'quote' => pg_escape_string($_POST['quote']),
'author' => pg_escape_string($_POST
['author']),
'year' => intval($_POST['year'])
);
pg_insert($db, 'quotes', $data);
echo 'Quote saved.';
pg_close($db);
} else {
echo 'Connection failed.';
}
?>
```

*向 PostgreSQL 发送 SQL（pg_insert.php；摘录）*

### 检索 PostgreSQL 查询结果

```
$result = pg_query();
pg_fetch_row($result);
```

调用 pg_query() 的返回值是指向结果集的指针，可以与以下函数一起使用：

- pg_fetch_assoc() 将结果集中的当前行作为关联数组返回
- pg_fetch_object() 将结果集中的当前行作为对象返回
- pg_fetch_row() 将结果集中的当前行作为数字数组返回
- pg_fetch_all() 将整个结果集作为关联数组的数组返回

```
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
    if ($db = @pg_connect('host=localhost port=5432
    dbname=phrasebook user=postgres
    password=abc123')) {
    $result = pg_query($db, 'SELECT * FROM quotes');
    while ($row = pg_fetch_row($result)) {
        vprintf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
            $row
        );
    }
    pg_close($db);
    } else {
    echo '<tr><td colspan="4">Connection
failed.</td></tr>';
    }
?>
</table>
```

*从 PostgreSQL 检索数据（pg_fetch.php；摘录）*

代码使用 pg_fetch_row() 读取 quotes 表中的所有数据。

另外，pg_select() 的工作方式与 pg_insert() 和 pg_update() 类似。只需提供数据库句柄、表名，以及可能是数组形式的 WHERE 子句，就可以得到以（关联）数组数组形式呈现的完整结果集。

```
$data = pg_select($db, 'quotes');
```

### 连接到 Oracle

### @oci_connect()

有两个 PHP 扩展可用于 Oracle，但只有一个在积极维护，并且也适用于更新版本的 RDBMS。要安装它，请使用开关 `--with-oci8` 配置 PHP。必须设置环境变量 `ORACLE_HOME`，以便 PHP 能够找到客户端库。Windows 用户需要 php.ini 指令 `extension=php_oci8.dll`。此外，PHP 需要对客户端库的读取权限。然后，oci_connect() 尝试与服务器建立连接。参数的顺序有点奇怪：先是用户名和密码，然后是服务名称（该服务已使用配置助手配置，或者是 tnsnames.ora 文件的一部分）。返回值是连接的句柄，数据库中的进一步操作需要它。

```
<?php
if ($db = @oci_connect('scott', 'tiger', 'orcl'))
{
 echo 'Connected to the database.';
 oci_close($db);
} else {
 echo 'Connection failed.';
}
?>
```

连接到 Oracle（oci_connect.php）

> 警告
> 
> 在 PHP 4 中，oci_connect() 尚不存在，因此对于该版本，必须使用 oci_logon()。然而，这被视为在 PHP 5 中已弃用。因此，本章中的所有 Oracle 示例都使用 PHP 5 语法；但是，下载仓库中包含了扩展名为 .php4 的文件，这些文件适用于较旧的 PHP 版本。

### 向 Oracle 发送 SQL

### oci_execute()

本节再次使用 quotes 表，该表也包含一个标识列；然而，在 Oracle 中实现这一点要复杂一些。有关更多信息，请参阅下载存档中的脚本 quotes.oracle.sql。

```
<?php
if ($db = @oci_connect('scott', 'tiger', 'orcl'))
{
require_once 'stripFormSlashes.inc.php';
$sql = 'INSERT INTO quotes (quote, author, year)
    VALUES (:quote, :author, :year)';
$stmt = oci_parse($db, $sql);
oci_bind_by_name($stmt, ':quote',
    $_POST['quote']);
oci_bind_by_name($stmt, ':author',
    $_POST['author']);
oci_bind_by_name($stmt, ':year',
    intval($_POST['year']));
oci_execute($stmt, OCI_COMMIT_ON_SUCCESS);
echo 'Quote saved.';
oci_close($db);
}
```




```php
} else {
    echo 'Connection failed.';
}
?>
```

向 Oracle 发送 SQL（oci_execute.php；节选）

要向 Oracle 发送 SQL，需要两个步骤。首先，调用 oci_parse() 解析 SQL 字符串，并返回一个资源，然后可以使用 oci_execute() 执行该资源。oci_execute() 的第二个参数非常重要。虽然允许使用几个常量，但大多数时候会使用 OCI_DEFAULT。尽管名称如此，但它并不是默认值，而是表示“不自动提交”。另一方面，OCI_COMMIT_ON_SUCCESS 会在未发生错误时提交挂起的事务。而且，这确实就是默认值。

遗憾的是，并没有类似 oci_escape_string() 的函数来转义 SQL 语句中的特殊字符。因此，预处理语句是必须的——但也非常容易实现。为此，SQL 语句必须包含以冒号开头的占位符：

```php
$sql = 'INSERT INTO quotes (quote, author, year)
    VALUES (:quote, :author, :year)';
```

然后，需要用值来填充这些占位符。为此，必须使用 oci_bind_by_name()：

```php
oci_bind_by_name($stmt, ':quote', $_POST['quote']);
```

上面的代码将一些表单数据发送到数据库。无需担心特殊字符，因为 oci_bind_by_name() 会处理这些问题。

### 向 Oracle 发送 SQL

> 当你使用 OCI_DEFAULT 作为提交模式时，必须使用 oci_commit($db) 将更改写入数据库；oci_rollback($db) 则执行回滚。

> 顺便说一下，如果你想获取最近一次 INSERT 操作的自增值，必须在事务内执行 SELECT quotes_id.CURRVAL AS id FROM DUAL，其中 quotes_id 是你所使用的序列的名称。

### 检索 Oracle 查询结果

```php
oci_fetch_object($stmt)
```

你有多种方式访问 SQL 查询的返回值，但在实践中，以下函数最常用：

- oci_fetch_assoc() 返回结果集中的当前行作为关联数组。
- oci_fetch_object() 返回结果集中的当前行作为对象。
- oci_fetch_row() 返回结果集中的当前行作为数字数组。
- oci_fetch_all() 将完整的结果集作为关联数组的数组返回。不过，它需要五个参数：来自 oci_parse() 的语句对象、用于返回数据的数组、要跳过的行数、要返回的最大行数（-1 表示无限），以及是否返回数字数组（OCI_NUM）或关联数组（OCI_ASSOC）。

本段中的代码清单使用 while 循环和 oci_fetch_object() 来检索表中的所有数据。

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
    if ($db = @oci_connect('scott', 'tiger', 'orcl'))
    {
        $stmt = oci_parse($db, 'SELECT * FROM quotes');
        oci_execute($stmt, OCI_COMMIT_ON_SUCCESS);
        while ($row = oci_fetch_object($stmt)) {
            printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
                htmlspecialchars($row->ID),
                htmlspecialchars($row->QUOTE),
                htmlspecialchars($row->AUTHOR),
                htmlspecialchars($row->YEAR)
            );
        }
        oci_close($db);
    } else {
        echo '<tr><td colspan="4">Connection failed.</td></tr>';
    }
?>
</table>
```

*从 Oracle 检索数据（oci_fetch.php；节选）*

> 注意
> Oracle 总是以大写形式返回列名。
> 因此，在访问 SQL 查询的返回值时，必须使用大写形式的对象属性或大写形式的关联数组键。

### 连接 MSSQL

```php
@mssql_connect()
```

Microsoft SQL 引擎有两种版本：功能完备（且价格不菲）的 Microsoft SQL Server（简称 MSSQL），以及免费版 Microsoft SQL Server Desktop Engine（简称 MSDE），可免费从 http://www.asp.net/msde/ 获取。PHP 支持这两个版本，因为它们彼此兼容。要使其正常工作，你需要 php.ini 中的 `extension=php_mssql.dll` 配置行。此外，PHP 还需要访问 MSSQL/MSDE 的客户端库文件 `ntwdbllib.dll`。在 PHP 5 中，该文件位于 PHP 目录中，因此 PHP 进程只需对其具有读取权限。在 PHP 4 中，你可能需要将该文件（位于 dll 子目录中）复制到其他地方，例如 Windows 的 system32 文件夹中。

不过，UNIX/Linux 系统也可以连接到异构网络中的 MSSQL/MSDE 安装，这种组合为一些高流量网站提供了动力。要实现这一点，你必须从 http://www.freetds.org/ 下载 FreeTDS 库，解压发行版后使用以下命令安装：

```
./configure --prefix=/usr/local/tds --with-tdsver=4.2
make
sudo make install
```

然后，使用开关 --with-sybase=/usr/local/freetds 重新配置 PHP。

最后，如前面的代码清单所示，你可以使用 mssql_connect() 连接到服务器，并使用 mssql_select_db() 选择要使用的数据库。

```php
<?php
    if ($db = @mssql_connect('localhost', 'user',
        'password')) {
        mssql_select_db('phrasebook');
        echo 'Connected to the database.';
        mssql_close($db);
    } else {
        echo 'Connection failed.';
    }
?>
```

*连接 MSSDE/MSDE（mssql_connect.php）*

MSSQL/MSDE 支持两种用户认证模式：SQL 认证和 Windows 认证。后者会检查当前 Windows 用户是否拥有足够的权限来访问数据库。在受控环境中，这可能比使用用户名和密码更好。不过，你首先必须弄清楚使用了哪个用户。例如，Microsoft IIS Web 服务器软件使用 Internet 来宾帐户，即 IUSR_<machinename>。因此，该用户需要在数据库中拥有权限。

要使用 Windows 认证——有时也称为受信任连接——你需要以下 php.ini 指令：

```
mssql.secure_connection = On
```

### 向 MSSQL 发送 SQL

### mssql_query()

mssql_query() 函数会将 SQL 语句发送到 MSSQL/MSDE 安装。同样，参数顺序有点奇怪：首先是 SQL 命令，然后是数据库句柄。然而，正如你在前面调用 mssql_select_db() 时所看到的那样，这些信息也可以省略——此时会自动使用最后建立的连接。

另一个重要问题是特殊字符的转义。在 MSSQL/MSDE 中，不能使用反斜杠来转义单引号，而应该将单引号双写：

```
INSERT INTO quotes (quote, author, year) VALUES ('Ain''t Misbehavin''', 'Louis Armstrong', 1929)
```

要实现这一点，可以使用 addslashes() ——不过，首先必须将其配置为返回与 MSSQL/MSDE 兼容的字符串：

```
ini_set('magic_quotes_sybase', 'On');
$author = addslashes($_POST['author']);
```

```php
<?php
if ($db = @mssql_connect('localhost', 'user', 'password')) {
    require_once 'stripFormSlashes.inc.php';
    mssql_select_db('phrasebook', $db);
    ini_set('magic_quotes_sybase', 'On');
    mssql_query(sprintf(
        'INSERT INTO quotes (quote, author, year)
        VALUES (\'%s\', \'%s\', \'%s\')',
        addslashes($_POST['quote']),
        addslashes($_POST['author']),
        intval($_POST['year']), $db);
    echo 'Quote saved.';
    mssql_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

*向 MSSQL/MSDE 发送 SQL（mssql_execute.php；节选）*

本段开头的代码清单会对一些表单数据进行清理，并将其写入到现在已经众所周知的示例数据库。

### 检索 MSSQL 查询结果

```php
$result = mssql_query();
mssql_fetch_assoc($result);
```

当然，最后还有一种方法可以检索结果集中的所有数据。这时可以使用 while 循环，并使用以下函数之一：

- mssql_fetch_assoc() 返回结果集中的当前行作为关联数组
- mssql_fetch_object() 返回结果集中的当前行作为对象
- mssql_fetch_row() 返回结果集中的当前行作为数字数组




### 检索对 MSSQL 的查询结果

```
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
    if ($db = @mssql_connect('localhost', 'user',
        'password')) {
        mssql_select_db('phrasebook', $db);
        $result = mssql_query('SELECT * FROM quotes',
            $db);
        while ($row = mssql_fetch_assoc($result)) {
            printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
                htmlspecialchars($row['id']),
                htmlspecialchars($row['quote']),
                htmlspecialchars($row['author']),
                htmlspecialchars($row['year'])
            );
        }
        mssql_close($db);
    } else {
        echo '<tr><td colspan="4">Connection
            failed.</td></tr>';
    }
?>
</table>
```

*从 MSSQL/MSDE 检索数据（mssql_fetch.php；节选）*

### 连接 Firebird

### ibase_connect()

Firebird 数据库目前更像是一种内行推荐，而非广泛使用的数据库，但它正在获得更多用户，并可能成为既有关系型数据库管理系统（RDBMS）的替代品。该数据库起源于 Borland 的 InterBase 产品。因此，该扩展被称为 ibase 或 interbase。所以，Windows 用户需要在 php.ini 中设置 extension=php_interbase.dll，而“自行编译者”必须使用 --with-interbase=/path/to/firebird 参数来配置 PHP。此外，Firebird 支持两种模式：一种是与 SQLite 类似的文件模式，另一种是服务器模式。为了互操作性以及易于部署，本节使用文件模式。

```
<?php
    if ($db =
ibase_connect('localhost:/tmp/quotes.gdb', 'user',
    'password')) {
        echo 'Connected to the database.';
        ibase_close($db);
    } else {
        echo 'Connection failed.';
    }
?>
```

*连接 InterBase/Firebird（ibase_connect.php）*

本节同样使用与 Firebird 和 InterBase 都兼容的 .gdb 文件；新的 Firebird 格式扩展名为 .fdb。创建该文件后，ibase_connect() 会连接到此文件或数据库。例如

```
} else {
    echo 'Connection failed.';
}
?>
```

*将 SQL 发送到 InterBase/Firebird（ibase_execute.php；节选）*

**注意**  
前面的代码包含 Firebird 的两个特性。首先，标识列由数据库中的生成器（generator）驱动；插入新字段时，对 GEN_ID(quotes_gen, 1) 的调用会在此列中填入下一个可用值。另外，year 一词在 Firebird 中是保留字，因此该列的名称是 qyear。

### 检索对 Firebird 的查询结果

```
$result = ibase_query();
$row = ibase_fetch_object($result);
```

无论你是使用 ibase_query 还是 ibase_execute()，最终都会获得一个结果集句柄。你可以使用 ibase_fetch_assoc()（返回关联数组）或 ibase_fetch_object()（返回对象）来遍历该结果集。此代码使用后一种方法。

请记住，Firebird 和 InterBase 以大写形式返回列名，因此对象属性（以及关联数组中的键）也都是大写的。

### 检索对 Firebird 的查询结果

```
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
if ($db = ibase_connect('//CHRISTIAN2003/tmp/quotes.gdb', 'user', 'password')) {
$result = ibase_query($db, 'SELECT * FROM quotes');
while ($row = ibase_fetch_object($result)) {
printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
htmlspecialchars($row->ID),
htmlspecialchars($row->QUOTE),
htmlspecialchars($row->AUTHOR),
htmlspecialchars($row->QYEAR)
);
}
ibase_close($db);
} else {
echo '<tr><td colspan="4">Connection failed.</td></tr>';
}
?>
</table>
```

*从 InterBase/Firebird 检索数据（ibase_fetch.php；节选）*

### 通过 PDO 连接

```
try {
$db = new PDO('sqlite:PDOquotes.db');
}
```

最后，PDO（PHP Data Objects 的缩写）是一些核心 PHP 开发者带来的新成果，也是 PHP 5.1 的关键特性之一。PHP 中有多个抽象类，但 PDO 将成为官方的抽象层。

PDO 已在 PEAR 中提供，见 http://pecl.php.net/package/PDO。UNIX/Linux 用户可以使用 pear install PDO 安装，也可以手动编译；Windows 用户则需要参考 http://pecl4win.php.net/list.php/5_0（PHP 5.0.x）和 http://pecl4win.php.net/list.php/5_1（PHP 5.1）。然后，在 php.ini 中设置 extension=php_pdo.dll（在其他系统中为 extension=pdo.so）即可。

```php
<?php
try {
    $db = new PDO('sqlite:PDOquotes.db');
    echo 'Connected to the database.';
} catch (PDOException $ex) {
    echo 'Connection failed: ' .
htmlspecialchars($ex->getMessage());
}
?>
```

*通过 PDO 连接（pdo_connect.php）*

安装 PDO 后，还必须加载所用数据库的驱动程序。截至撰写本文时，可用的驱动程序如下：

- PDO_FIREBIRD：用于 InterBase/Firebird
- PDO_MYSQL：用于 MySQL 3.x 和 4.0
- PDO_OCI：用于 Oracle
- PDO_ODBC：用于 ODBC 和 IBM 的 DB2
- PDO_PGSQL：用于 PostgreSQL
- PDO_SQLITE：用于 SQLite

### 通过 PDO 连接

为了尽可能使其可移植且易于部署，以下示例使用 SQLite 驱动；不过，其他驱动和数据库系统也同样适用。请注意，该驱动使用 SQLite 3，而不是 PHP 5 所捆绑的 SQLite 2（这就是该驱动的二进制发行版超过 200KB 的原因）。无论你选择哪种系统，请下载并安装相应驱动，并在 php.ini 中将其放在 PDO 之后加载。

由于 PDO 仅适用于 PHP 5 及更高版本，因此你可以使用面向对象的方法。你只需要一个合适的数据源名称（DSN）、用户名和密码（可能还需要其他选项）。前面的代码会连接/创建一个 SQLite 文件。

### 通过 PDO 发送 SQL

```
$stmt = $db->prepare($sql);
$stmt->execute();
```

要通过 PDO 发送 SQL，必须使用 query() 方法执行语句。与往常一样，你需要一种转义特殊字符的方法。这同样可以通过预处理语句来完成。首先，可以使用名为 prepare() 的方法解析 SQL 查询，其中的占位符以冒号开头。然后，bindParam() 方法将值绑定到占位符名称。最后，execute() 方法将语句发送到数据库。

```php
<?php
try {
    $db = new PDO('sqlite:PDOquotes.db');
    require_once 'stripFormSlashes.inc.php';
    $sql = 'INSERT INTO quotes (quote, author, year)
VALUES (:quote, :author, :year)';
$stmt = $db->prepare($sql);
$stmt->bindParam(':quote', $_POST['quote']);
$stmt->bindParam(':author', $_POST['author']);
$stmt->bindParam(':year',
    intval($_POST['year']));
$stmt->execute();
echo 'Quote saved.';
} catch (PDOException $ex) {
echo 'Connection failed: ' . htmlspecialchars
    ($ex->getMessage());
}
?>
```

通过 PDO 发送 SQL（pdo_execute.php；节选）

### 通过 PDO 检索查询结果

```
$result = $db->query();
$result->fetch(PDO::FETCH_ASSOC);
```

最后，使用 PDO 从 SQL 查询中读取结果采用标准方法：将 SELECT 查询发送到服务器，然后使用 while 循环遍历结果。这里，使用 fetch() 方法进行遍历。作为参数，你可以提供诸如 PDO::FETCH_ASSOC（返回关联数组）或 PDO::FETCH_OBJ（返回对象）之类的常量。或者，你可以使用 fetchAll() 方法获得一个数组的数组，从而一次性取得所有数据。

此代码使用 fetch() 和 PDO::FETCH_ASSOC 从数据源读取所有数据。

### 通过 PDO 检索查询结果

```
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
  try {
    $db = new PDO('sqlite:PDOquotes.db');
    $result = $db->query('SELECT * FROM quotes');
    while ($row = $result->fetch(PDO::FETCH_ASSOC)) {
      printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
        htmlspecialchars($row['id']),
        htmlspecialchars($row['quote']),
        htmlspecialchars($row['author']),
        htmlspecialchars($row['year'])
      );
    }
  } catch (PDOException $ex) {
    echo 'Connection failed: ' . htmlspecialchars
      ($ex->getMessage());
  }
?>
</table>
```

通过 PDO 检索数据（pdo_fetch.php；节选）

注意  
截至撰写本文时，PDO 尚不能被视为稳定；因此，PDO 的应用程序编程接口（API）或行为未来可能会发生变化。此外，如果你尝试使用 PDO，请记住它尚未被证明像 PHP 本身一样可靠。




### 通过 PDO 检索查询结果

### PEAR 提供了什么？

以下是 PEAR 包（其中之一）提供数据库抽象层和其他数据库访问便利功能：

- DB 是 PEAR 中最知名的数据库抽象层
- DB_DataObject 可以从对象创建 SQL
- DB_QueryTool 在构建 SQL 查询时提供一些帮助
- MDB 和 MDB2 也是功能丰富的数据库抽象层

## 使用 XML

在炒作之后，可扩展标记语言（XML）现在几乎在任何地方都被真正使用。一个备受关注的应用是 Web Services，这项技术在第 9 章“与他人通信”中有详细介绍。然而，XML 也可以在其他地方使用。它是存储任何类型数据的良好格式。

使用 XML 背后的任务始终相同：从 XML 读取数据并向其中写入数据。因此，本章重点介绍这些任务并展示如何实现它们。

不幸的是，PHP 4 的 XML 支持有限。一些扩展证明并不十分稳定。随着 PHP 5 和重新设计的 XML 支持，这一情况发生了巨大变化。因此，本章的重点主要放在 PHP 4 上。在 PHP 5.1 中，将添加一些新功能，这些功能已在本章中介绍。

作为本章中的示例 XML 文件和格式，以下代码中的 XML 重用了上一章中的 quotes 数据库示例。如你所见，<quotes> 是根元素，每个引语（包括其作者和短语诞生的年份）都包含在 <quote> 元素中。

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<quotes>
  <quote year="1991">
    <phrase>Hasta la vista, baby!</phrase>
    <author>Arnold Schwarzenegger</author>
  </quote>
</quotes>
```

### 示例 XML 文件（quotes.xml；摘录）

### 使用 SAX 解析 XML

```
$sax = xml_parser_create();
```

SAX 是一种解析 XML 文档的方法，但不用于验证。好处是，你可以在 PHP 4 和 PHP 5 中使用它而无需更改。在 PHP 4 中，SAX 解析已在所有平台上可用，因此无需单独安装。

```
<?php
// ...
$sax = xml_parser_create();
xml_parser_set_option($sax, XML_OPTION_CASE_FOLDING, false);
xml_parser_set_option($sax, XML_OPTION_SKIP_WHITE, true);
xml_set_element_handler($sax, 'sax_start', 'sax_end');
xml_set_character_data_handler($sax, 'sax_cdata');
xml_parse($sax, file_get_contents('quotes.xml'), true);
xml_parser_free($sax);
?>
```

你使用 xml_parser_create() 创建一个 SAX（XML 简单 API）解析器。该解析器可以查看 XML 文件并对各种事件做出反应。以下三个事件是最重要的：

- 元素的开始
- 元素的结束
- CDATA 块

然后你可以为这些元素定义处理函数，并使用它们将 XML 转换为其他内容，例如超文本标记语言（HTML）。列表 8.1 展示了这一点，并将 XML 文件的内容输出为项目符号 HTML 列表，如图 8.1 所示。函数 xml_set_element_handler() 设置元素的开始和结束处理程序，而 xml_set_character_data_handler() 设置 CDATA 块的处理程序。使用 xml_parser_set_option()，你可以配置处理程序，例如忽略空白并将标签名作为区分大小写处理（然后标签名不会自动转换为大写字母）。以下代码包含处理函数代码：

```
function sax_start($sax, $tag, $attr) {
    if ($tag == 'quotes') {
        echo '<ul>';
    } elseif ($tag == 'quote') {
        echo '<li>' . htmlspecialchars($attr['year']) .
            ': ';
    } elseif ($tag == 'phrase') {
        echo '"';
    } elseif ($tag == 'author') {
        echo ' (';
    }
}
function sax_end($sax, $tag) {
    if ($tag == 'quotes') {
        echo '</ul>';
    } elseif ($tag == 'quote') {
        echo '</li>';
    } elseif ($tag == 'phrase') {
        echo '"';
    } elseif ($tag == 'author') {
        echo ') ';
    }
}
function sax_cdata($sax, $data) {
    echo htmlspecialchars($data);
}
```

![](img/1e6d362f187af50011d2666ddaa68739_249_0.png)

图 8.1 从 XML 创建的 HTML。

注意

PHP 5.1 默认包含 XMLReader。它是对 libxml2 的包装，并模仿用于读取 XML 的 .NET 组件 XmlTextReader 的应用程序编程接口（API）。它比 SAX 快得多，而且更容易使用。截至本文撰写时，它还不是很稳定，但看起来很有前景。不是 PHP 5.1 标准发行版的一部分，但在 PECL 中可用的是关联模块 XMLWriter，它允许对 XML 进行写访问。有关这两个模块的更多信息可在其作者的演示文稿中找到，网址为 http://php5.bitflux.org/xmloncrack/。

### 在 PHP 4 中使用 DOM 读取 XML

```
domxml_open_mem(file_get_contents('quotes.xml'))
```

W3C 的文档对象模型（DOM）定义了访问 XML 结构中元素的一种统一方式。因此，使用 JavaScript 的 DOM 访问访问 HTML 页面中的元素和使用 PHP 的 DOM 访问访问 XML 文件中的元素非常相似。

```
<?php
$dom =
domxml_open_mem(file_get_contents('quotes.xml'));
echo '<ul>';
foreach ($dom->get_elements_by_tagname('quote') as
    $element) {
    $attr = $element->attributes();
    $year = htmlspecialchars($attr[0]->value);
    foreach ($element->child_nodes() as $e) {
        if (isset($e->tagname)) {
            if ($e->tagname == 'phrase') {
                $node = $e->first_child();
                $phrase = htmlspecialchars
                    ($node->node_value());
            } elseif ($e->tagname == 'author') {
                $node = $e->first_child();
                $author =
                    htmlspecialchars($node->node_value());
            }
        }
    }
    echo "<li>$author: \"$phrase\" ($year)</li>";
}
echo '</ul>';
?>
```

不幸的是，如果你使用 PHP 4，请注意 DOM 访问在版本之间发生了变化，并且在某些系统上并不稳定。Windows 用户必须在 php.ini 中使用 extension=php_domxml.dll，并且可能需要将 iconv.dll 复制到 Windows system32 文件夹中。其他系统必须使用 --with-dom=/path/to/libxml 重新配置 PHP。然后 domxml_open_file() 打开文件——使用绝对路径！更可移植的方法是使用读取字符串的 domxml_open_mem。这两个函数的返回值提供了对两个方法 get_elements_by_tagname() 和 get_element_by_id() 的访问，它们返回具有特定标签名的所有节点或由其 ID 标识的特定元素。然后每个节点公开一些方法，如下所示：

- `first_child()`—第一个子节点
- `last_child()`—最后一个子节点
- `next_sibling()`—下一个节点
- `previous_sibling()`—上一个节点
- `node_value()`—节点的值

前面的代码使用 DOM 访问 XML 文件中的所有引语并输出它们。

### 在 PHP 5 中使用 DOM 读取 XML

如果你使用 PHP 5，主要优势是使用了 libxml2，这是一个比 libxml 好得多的库。它捆绑在 PHP 中，因此无需安装。然而，API 已发生巨大变化。首先，你实例化一个 DOMDocument 对象，然后 load() 一个文件或 loadXML() 一个字符串。所有方法名都已更改为驼峰式大小写，并且所有属性都是真正的属性，而不是像 PHP 4 中的方法。前面的代码与前一个示例中的代码做同样的事情，但可在 PHP 5 下运行。

```
<?php
$dom = new DOMDocument();
$dom->load('quotes.xml');
echo '<ul>';
foreach ($dom->getElementsByTagname('quote') as
    $element) {
    $year = $element->getAttribute('year');
    foreach (($element->childNodes) as $e) {
        if (is_a($e, 'DOMElement')) {
            if ($e->tagName == 'phrase') {
                $phrase = htmlspecialchars($e->textContent);
            } elseif ($e->tagName == 'author') {
                $author = htmlspecialchars($e->textContent);
            }
        }
    }
    echo "<li>$author: \"$phrase\" ($year)</li>";
}
echo '</ul>';
?>
```

*使用 DOM 解析 XML（dom-read5.php）*

请注意，列表中使用 is_a()，以便仅在类型为 DOMElement 的节点中评估标签名。这是因为空白被视为一个 DOM 节点（不过类型为 DOMText）。



```php
<?php
require_once 'stripFormSlashes.inc.php';
$dom = domxml_open_mem(file_get_contents
    ('quotes.xml'));
$quote = $dom->create_element('quote');
$quote->set_attribute('year', $_POST['year']);
$phrase = $dom->create_element('phrase');
$phrase->set_content($_POST['quote']);
$author = $dom->create_element('author');
$author->set_content($_POST['author']);
$quote->append_child($phrase);
$quote->append_child($author);
$root = $dom->document_element();
$root->append_child($quote);
file_put_contents('quotes.xml', $dom->dump_mem());
echo 'Quote saved.';
?>
```

使用 DOM 创建 XML (dom-write4.php; 摘录)

前面的代码将作者、引语和年份保存到 XML 文档中，并追加到已有的数据中。

### 在 PHP 5 中使用 DOM 编写 XML

```php
$dom = new DOMDocument();
```

使用 PHP 5 时，代码会略有变化，但大部分变化是改为驼峰式大小写。

```php
<?php
require_once 'stripFormSlashes.inc.php';
$dom = new DOMDocument();
$dom->load('quotes.xml');
```

```php
$quote = $dom->createElement('quote');
$quote->setAttribute('year', $_POST['year']);
$phrase = $dom->createElement('phrase');
$phraseText = $dom->
createTextNode($_POST['quote']);
$phrase->appendChild($phraseText);
$author = $dom->createElement('author');
$authorText = $dom->
createTextNode($_POST['author']);
$author->appendChild($authorText);
$quote->appendChild($phrase);
$quote->appendChild($author);
$dom->documentElement->appendChild($quote);
$dom->save('quotes.xml');
echo 'Quote saved.';
?>
```

使用 DOM 创建 XML (dom-write5.php; 摘录)

> **注意**
> 
> PHP 5 的 DOM 扩展不提供类似 PHP 4 的 `set_content()` 的功能，因此你必须使用 `createTextNode()` 方法来定义节点的文本值，如前面的代码所示。

### 使用 SimpleXML

```php
$xml = simplexml_load_file('quotes.xml');
```

PHP 5.1 中最伟大的新特性之一是 SimpleXML 扩展，其灵感源自 CPAN 中的一个 Perl 模块。这种方法简单而巧妙。访问 XML 最直观的方式可能是通过面向对象编程（OOP）方法：子节点是其父节点/对象的属性，XML 属性则转换为对象属性。这使得访问 XML 变得非常容易，包括完整的迭代器支持，因此可以使用 foreach。

```php
<?php
$xml = simplexml_load_file('quotes.xml');
echo '<ul>';
foreach ($xml->quote as $quote) {
    $year = htmlspecialchars($quote['year']);
    $phrase = htmlspecialchars($quote->phrase);
    $author = htmlspecialchars($quote->author);
    echo "<li>$author: \"$phrase\" ($year)</li>";
}
echo '</ul>';
?>
```

*使用 SimpleXML 解析 XML (simplexml-read.php)*

此代码使用 simplexml_load_file() 加载文件——对于字符串也可以使用 simplexml_load_string()——然后读取其中的所有信息。

将其与 DOM 方法进行比较。SimpleXML 在某些情况下可能比 DOM 慢，但编码速度要快得多。

注意
写入也很容易完成。然而，不可能在没有外部帮助的情况下追加元素，例如使用 DOM 并通过 simplexml_import_dom() 将此 DOM 加载到 SimpleXML 中。

### 使用 XSL 和 PHP 4 转换 XML

```php
$result = $xslt->process($dom);
echo $xslt->result_dump_mem($result);
```

要在 PHP 中使用 XSL 转换（XSLT），你首先必须决定使用哪个 PHP 版本。如果是 PHP 4，你必须在 php.ini（Windows）中使用 extension=php_xslt.dll，或从 http://www.gingerall.com/ 安装 Sablotron 并使用配置开关 -enable-xslt -with-xslt-sablot（适用于其他系统）。

```php
<?php
    $dom =
    domxml_open_mem(file_get_contents('quotes.xml'));
    $xslt = domxml_xslt_stylesheet(
    file_get_contents('quotes.xsl'));
    $result = $xslt->process($dom);
    echo $xslt->result_dump_mem($result);
?>
```

使用 PHP 4 的 XSLT (xslt4.php)

执行转换分为四个简单的步骤：加载 XML；加载 XSLT；执行转换；最后保存结果。前一段包含这些步骤的代码；下载库中的文件 quotes.xsl 包含将引语 XML 转换为众所周知的 HTML 项目符号列表的标记。

### 使用 XSL 和 PHP 5 转换 XML

```php
$result = $xslt->transformToDoc($xml);
echo $result->saveXML();
```

在 PHP 5 中，XSLT 由 libxslt 实现，可在 Windows 上使用 php_xsl.dll（在 php.ini 中）启用，在其他平台上使用开关 -with-xsl。方法略有不同：将 XML 和 XSLT（它也是一个 XML 文档）都加载到 DOM 对象中，然后实例化一个 XsltProcessor 对象。调用 importStylesheet() 然后调用 transformToDoc()。

```php
<?php
  $xml = new DOMDocument();
  $xml->load('quotes.xml');
  $xsl = new DOMDocument();
  $xsl->load('quotes.xsl');
  $xslt = new XsltProcessor();
  $xslt->importStylesheet($xsl);
  $result = $xslt->transformToDoc($xml);
  echo $result->saveXML();
?>
```

*使用 PHP 5 的 XSLT (xslt5.php)*

提示
再次，有一个脚本可以使两个不兼容的 XSLT 实现相互兼容。你可以在 http://alexandre.alapetite.net/doc-alex/xslt-php4-php5/ 找到它。

### 验证 XML

```php
$dom->relaxNGValidate('quotes.rng')
```

PHP 5 可以根据三种类型的文件验证 XML：文档类型定义（DTDs）、模式（.xsd）和 relaxNG。对于后两种，DOM 对象存在以下四种方法：

- `schemaValidate('file.xsd')`—针对 Schema 文件进行验证
- `schemaValidateSource('...')`—针对 Schema 字符串进行验证
- `relaxNGValidate('file.rng')`—针对 relaxNG 文件进行验证
- `relaxNGValidateSource('...')`—针对 relaxNG 字符串进行验证

前面的代码使用 relaxNGValidate() 将（格式良好的）XML 文件与不匹配的 relaxNG 文件进行验证。如果你在文件 quotes.rng 中将 <element name="person"> 改为 <element name="author">，验证就会成功。

```php
<?php
$dom = new DOMDocument;
$dom->load('quotes.xml');
echo 'Validation ';
(($dom->relaxNGValidate('quotes.rng')) ?
'succeeded.' : 'failed.');
?>
```

使用 relaxNG 验证 XML (validate-rng.php)

> 提示
> 
> 创建 relaxNG 文件可能相当困难；Java 工具 Trang，可在 http://thaiopensource.com/relaxng/trang.html 获取，可以读取 XML 文件并从中创建 relaxNG、Schema 或 DTD 文件。

验证 Schema 类似，并在下载库中的文件 validate-xsd.php 中展示。当验证 DTD 时，你必须稍微修改 XML。DTD 文件必须包含在文件中或像这样引用：

```
<!DOCTYPE note SYSTEM "quotes.dtd">
```

然后，只需将 XML 文档加载到 DOM 对象中并调用 validate()。下面包含适当的代码；代码库中引用的文件在 DTD 中包含一个有意的错误（month 而不是 year）。

```php
<?php
$dom = new DOMDocument();
$dom->load('quotes-dtd.xml');
echo 'Validation ' .
    (($dom->validate()) ? 'succeeded.' : 'failed.');
?>
```

*使用 DTD 验证 XML (validate-dtd.php)*

### 验证 XML

### PEAR 提供了什么？

截至本文撰写时，PEAR 的 XML 部分包含 28 个包，太多无法一一列举。以下是其中一些：

- XML_Beautifier 格式化 XML 文档，使其更美观
- XML_DTD 允许解析 DTD，即使在 PHP 4 中也行
- XML_Serializer 将 XML 文件转换为数据结构，反之亦然
- XML_Util 包含用于处理 XML 的大量辅助函数

## 与他人通信

前面的大部分短语都在所使用的 PHP 脚本和 Web 服务器的生态系统中工作。然而，由于某些短语也可以被他人理解，本章涵盖了一些此类示例。你可以通过多种方式连接到远程服务器。

### 连接 HTTP 服务器

```php
<xmp>
<?php
echo file_get_contents('http://www.php.net/');
?>
</xmp>
```

超文本传输协议（HTTP）可能是从 PHP 连接到其他系统（除各种数据库协议外）最常用的协议。从 PHP 4.3 开始，连接此类数据变得非常容易



### 连接 HTTP 服务器

原因在于 PHP 的流支持在该版本中得到了极大改进（当然，以这种方式使用 HTTP 在更早的 PHP 版本中已经可能）。思路是当你使用文件操作时，你访问的是一个数据流。实际上，无论是本地系统上的文件、网络共享上的文件，还是通过 HTTP、文件传输协议（FTP）或其他受支持协议连接的远程服务器上的文件，都无关紧要。只需提供适当的文件名，PHP 就会处理其余部分。前面的代码展示了这一点：它打开 PHP 主页并在浏览器中打印其超文本标记语言（HTML）代码。只用一行代码，就不能更简单了。图 9.1 包含输出。

![](img/1e6d362f187af50011d2666ddaa68739_263_0.png)

图 9.1 一行代码打印 PHP 主页的 HTML 标记。

出于安全原因，此行为可在 php.ini 中通过将 allow_url_fopen 设置为 Off 来关闭，因此您无法在无法控制的 Web 服务器上依赖它——例如大型互联网服务提供商（ISP）的共享托管。

如果您想自行控制 HTTP 请求，可以使用套接字。首先，使用 fsockopen() 向 Web 服务器打开一个套接字，如果成功，则发送格式良好的 HTTP 请求。以下代码再次实现了此功能，用于查询 PHP 主页。

```
<?php
$fp = @fsockopen('www.php.net', 80, $errno,
$errstr, 30);
if ($fp) {
echo '<xmp>';
$request = "GET / HTTP/1.0\r\n";
$request .= "Host: www.php.net\r\n";
$request .= "Connection: Close\r\n\r\n";
fwrite($fp, $request);
while (!feof($fp)) {
	echo fgets($fp, 1024);
}
fclose($fp);
echo '</xmp>';
} else {
echo "Error: $errstr (#$errno)";
}
?>
```

使用套接字读取 HTTP 资源（http-socket.php）

输出相同，只有一个区别：套接字方法还会返回服务器发送的所有 HTTP 标头，而流包装器则省略了它们。

### 注意

当需要处理 HTTP 安全（HTTPS）资源（使用 SSL——安全套接字层 保护的网站）时，这两种方法仍然有效，只是需要稍作修改：

- 使用 file functions such as file_get_contents() 等文件函数时，只需提供一个 https:// 统一资源定位符（URL）。
- 使用套接字时，使用 ssl:// URL。

### 连接 FTP 服务器

访问 FTP 服务器时，PHP 的流包装器也很方便。您只有读取权限，但访问仍然是二进制安全的。此代码展示了如何使用 file_get_contents() 从 FTP 服务器下载 Apache 的当前 README 文件并将其保存到本地硬盘。写入也是可能的；只需使用 file_put_contents() 或 fopen() 的正确文件模式即可。注意，虽然同时进行读写尚未得到支持。

```
file_get_contents('ftp://ftp.leo.org/.mnt/0/
mirrors/apache/httpd/README.html')
```

```
<?php
$data =
file_get_contents('ftp://ftp.leo.org/.mnt/0/
mirrors/apache/httpd/README.html');
file_put_contents('Apache-README.html', $data);
echo 'File written.';
?>
```

读取 FTP 文件（ftp-file.php；摘录）

### 提示

如果您不提供任何凭据，PHP 会尝试使用大多数公共 FTP 服务器提供的访客账户登录到 FTP 服务器。您也可以自行提供凭据：

```
$data = file_get_contents
('ftp://USER:PASSWORD@ftp.example.com/');
```

这也适用于 HTTP 资源（见前文）！

PHP 还内置了对 FTP 的支持，并有一组特殊函数实现了相关请求评论（RFC）中定义的完整 FTP 功能。在 Windows 发行版中，这默认启用，而在其他系统上，PHP 必须使用 --enable-ftp 开关进行配置。然后，使用 FTP 服务器通常包括以下步骤：

- 使用 ftp_connect() 连接到服务器
- 使用 ftp_login() 登录
- 使用 ftp_chdir() 进入目标目录
- 从 FTP 服务器读取文件——ftp_get()——或向 FTP 服务器写入文件——ftp_put()——
- 使用 ftp_close() 关闭连接

由于读取可能比写入更常见，下面展示了前者的执行。再次从 FTP 服务器获取 Apache README。

```
<?php
$ftp = @ftp_connect('ftp.leo.org');
$login = @ftp_login($ftp, 'anonymous',
    'email@example.com');
if ($ftp && $login) {
    ftp_chdir($ftp, './mnt/0/mirrors/apache/httpd/');
    ftp_get($ftp, 'Apache-README-ftp.html',
        'README.html', FTP_ASCII);
    echo 'File written.';
    ftp_close($ftp);
} else {
    echo 'Error!';
}
?>
```

*使用内置函数读取 FTP 文件（ftp-functions.php）*

请注意 ftp_get() 的语法有点奇怪。在 FTP 资源之后，您必须先提供本地文件名，然后再提供远程文件名（直观上您会期望顺序相反）。最后一个参数是传输模式：文本文件使用 FTP_ASCII，所有其他数据使用 FTP_BINARY。

### 检查服务器是否仍在响应

假设您有一个 Web 服务器，并且想要定期检查它是否再次崩溃。那么使用 PHP 脚本执行此任务是个好主意。只需向服务器打开一个套接字并等待（fsockopen() 的最后一个参数是超时值）。在此时间过去后，您就知道服务器是否在线或离线。

```
<?php
$server = 'localhost';
$port = '80';
$status = 'unavailable';
$fp = @fsockopen($server, $port, $errno, $errstr, 10);
if ($fp) {
    $status = 'alive, but not responding';
    fwrite($fp, "HEAD / HTTP/1.0\r\n");
    fwrite($fp, "Host: $server:$port\r\n\r\n");
    if (strlen(@fread($fp, 1024)) > 0) {
        $status = 'alive and kicking';
    }
    fclose($fp);
}
echo "The server is $status.";
?>
```

*检查服务器状态（serverstatus.php）*

### 提示

如果只需要检查一个服务器的状态，这效果很好。如果有多个服务器，这种方法有一些缺点。fsockopen() 的调用可能需要长达超时值的时间才会执行下一个命令。
因此，所有服务器都是按顺序同步检查的。对于多个服务器来说，这花费的时间太长了。
然而，使用 PHP 5 和流套接字，这可以异步完成。代码有点复杂，但 Wez Furlong 在 http://netevil.org/node.php?nid=280 详细解释了这种方法。

### 理解 Web 服务

有些人说 Web 服务只是旧酒装新瓶，因为其背后的想法并不新鲜。基本原理是：两台机器相互通信。例如，一台机器包含一些业务逻辑或更一般地包含一些信息，而另一台机器请求这些信息（或想要使用业务逻辑）。

这已经做了很多年，但仅在几年前，主要参与者才坐在一起开始着手制定协议，将整个通信建立在标准之上。其中一些标准现在由万维网联盟（W3C）监管，而其他标准则由结构化信息标准推进组织（OASIS）联盟管理。

有大量关于 Web 服务的书籍，页数相当多。然而，根据本短语手册的概念，本章内容简单但仍提供您所需了解的一切。有一种协议用于传输对 Web 服务的请求及其响应。有几种可能性，但以下两种最常见：

- XML-RPC 代表远程过程调用，使用非常简单的 XML 方言传输函数调用、参数和返回值。这种方法有时称为 REST，即表征状态。关于哪种协议更好——这种协议还是下一个——存在一些激烈的争论。简单而粗糙地说：两者都有优点（和缺点）。
- SOAP 一度代表简单对象访问协议，但由于它既不简单也不太与对象访问有关，今天 SOAP 就只是代表……SOAP。它是一个相当复杂的协议，但克服了 XML-RPC 的许多限制（顺便说一下，XML-RPC 是由一些也参与 SOAP 工作的人员创建的）。

大多数情况下，XML-RPC 或 SOAP 调用通过 HTTP 作为承载协议传输。然而，其他协议也是可能的，包括简单邮件传输协议（SMTP）甚至用户数据报协议（UDP）。

使用 SOAP 时还有一个更重要的方面。当您确切知道 Web 服务是如何实现的时，您也知道如何调用（访问或使用）它。然而，很多时候这些信息不可用，因此必须有一种 Web 服务的自描述，其中包含所有相关信息，例如暴露了哪些方法和函数，它们期望哪些参数和数据类型，以及它们返回什么。这也可以使用专门制作的 XML 文件来完成。其背后的标准是 Web 服务描述语言

### 检查服务器是否仍在响应

今天，WSDL 已被所有相关的 Web 服务使用，因为这样使用它们就相当简单。大多数服务器端技术都提供一种（或多种）方式来读取 WSDL，然后像访问本地可用的类一样访问 Web 服务。

生成所有这些 XML 相当复杂。并不是说 PHP 没有良好的 XML 支持，而是语法可能相当困难。幸运的是，一些扩展和外部包使得使用 Web 服务变得容易得多。以下各节都实现了一个仅将两个数字相加的 Web 服务。基于这些信息，你肯定会更有创意并创建一些实际的 Web 服务。

### 使用 PEAR::XML-RPC 创建 Web 服务

有多种 XML-RPC 实现，但使用最广泛且也在积极开发中的是 PEAR::XML-RPC，可在 http://pear.php.net/package/XML_RPC/ 获取。它是另一款 XML-RPC 库的 PEAR 移植版，并添加了一些在原始发行版中未包含的修复。你可以使用 pear upgrade XML_RPC 安装它，以获取最新最好的版本。

要提供这样的 Web 服务，你必须实例化 XML_RPC_Server 类并提供有关服务的一些信息：使用哪个函数、其描述，以及当然签名（传递哪些参数类型、返回哪种数据类型）。前面的代码包含了简单“加两个数字”Web 服务的这些信息。

```php
<?php
    require_once 'XML/RPC/Server.php';

    $description = 'adds two numbers';
    $signature = array(
        array('int', 'int', 'int')
    );

    $xmlrpc = new XML_RPC_Server(
        array('phrasebook.php.add' =>
            array(
                'function' => 'add',
                'docstring' => $description,
                'signature' => $signature
            )
        )
    );
?>
```

*有关 XML-RPC Web 服务的信息
(xmlrpc-pear-server.php；摘录)*

请注意，签名包含所有输入参数的数据类型加上返回值的类型；这就是为什么 'int' 出现了三次而不是两次。

现在唯一缺少的就是实际的业务逻辑，即 add 函数。这有点棘手：首先，getParam() 方法返回提供给函数的所有参数；然后，scalarval() 检索此类参数的实际值。然后，可以通过返回合适的 XML_RPC_Response 对象来完成数字的相加。例如：

```php
function add($params) {
    $a = $params->getParam(0);
    $b = $params->getParam(1);
    if (isset($a) && isset($b)) {
        if ($a->scalartyp() == 'int' && $b->scalartyp() == 'int') {
            $a = $a->scalarval();
            $b = $b->scalarval();
            $c = new XML_RPC_Value($a + $b, 'int');
            return new XML_RPC_Response($c);
        } else {
            global $XML_RPC_erruser;
            return new XML_RPC_Response(0,
                $XML_RPC_erruser,
                'wrong parameters');
        }
    }
}
```

### 使用 PEAR::XML-RPC 消费 Web 服务

查询 Web 服务相当容易。只需实例化 XML_RPC_Client 类（提供服务的名称、服务器和端口），然后制作包含所有参数的消息，最后将该消息发送到服务器。你会收到 Web 服务调用的结果——或错误消息。该代码调用上一节中的 Web 服务，假设它可通过端口 80 上的 http://localhost/xmlrpc-pear-server.php 访问。

```php
<?php
require_once 'XML/RPC.php';

$a = 47;
$b = 11;

$xmlrpc = new XML_RPC_Client(
'/xmlrpc-pear-server.php',
'localhost',
80
);

$msg = new XML_RPC_Message(
  'phrasebook.php.add',
  array(
    new XML_RPC_Value($a, 'int'),
    new XML_RPC_Value($b, 'int')
  )
);

$response = $xmlrpc->send($msg);
$result = $response->value();
if (!$response->faultCode()) {
  echo "$a + $b = " . $result->scalarval();
} else {
  echo 'Error #' . $response->faultCode() . ': ' .
    $response->faultString();
}
?>
```

调用 XML-RPC Web 服务 (xmlrpc-pear-client.php)

TIP
当你调用 $xmlrpc->setDebug(1) 时，调试消息会被打开，使你更容易找出问题所在。

NOTE
仅适用于 PHP 5，有一个名为 XMLRPCi 的新扩展（i 代表 improved，即改进版），它使用 libxml2 进行 XML-RPC 调用。然而，目前仅发布过一次，且文档非常有限，因此几乎没有被使用。

### 使用 NuSOAP 创建 Web 服务

在 http://dietrich.ganx4.com/nusoap/ 和 http://sourceforge.net/projects/nusoap/ 上，你可以找到 NuSOAP，这是 PHP 中最知名的 SOAP 类之一。有些人甚至可能知道它的前身 SOAPx4。一段时间以来，发布并不频繁，但现在该项目再次活跃起来。尽管如此，你最好还是检查 Concurrent Versions System (CVS) 系统以获取最新代码。即使你在那里找到多个文件，nusoap.php 才是你需要的那个。

```php
<?php
    require_once 'nusoap.php';

    $soap = new soap_server;
    $soap->register('add');
    $soap->service($HTTP_RAW_POST_DATA);

    function add($a, $b) {
        return $a + $b;
    }
?>
```

*使用 NuSOAP 创建 Web 服务 (nusoap-server.php)*

NOTE
截至本文撰写时，NuSOAP 仅在 PHP 4 下工作，但据传 PHP 5 的移植正在进行中。

使用 NuSOAP 创建 Web 服务非常简单，因为该模块处理了所有繁琐的事情，包括 SOAP。只需按照以下步骤操作：

- 1. 编写你想要作为 Web 方法公开的函数
- 2. 实例化 soap_server 类
- 3. 将你的函数注册到 SOAP 服务器
- 4. 调用 service() 方法并提交 $HTTP_RAW_POST_DATA 作为参数

该代码使用 NuSOAP 实现了一个 SOAP 服务器。图 9.2 显示了当你尝试直接从客户端调用 Web 服务时浏览器中的输出。错误消息说 XML 为空——当然，因为我们没有发送请求！

### 使用 NuSOAP 自动生成 WSDL

如前所述，当前 Web 服务几乎总是使用 WSDL。手动编写 WSDL 真的很痛苦且容易出错，但大多数严肃的 PHP Web 服务实现可以自动创建 WSDL。然而，由于 PHP 不是强类型语言，它们需要一些帮助。

要使用 NuSOAP 实现这一点，前一节的代码必须稍微扩展一下。首先，必须调用 configureWSDL() 方法来提供服务的名称和命名空间。然后，必须提供方法签名（哪些参数传入，哪些参数传出）。然后启动服务器。然而，这次会检查 $HTTP_RAW_POST_DATA 是否已设置。这是因为当它未设置时，用户发出了 GET 请求，因此他可能只是想要 WSDL 描述。

```php
<?php
    require_once 'nusoap.php';

    $soap = new soap_server;
    $soap->configureWSDL('AddService', 'http://php.phrasebook.org/');
    $soap->wsdl->schemaTargetNamespace = 'http://soapinterop.org/xsd/';
    $soap->register(
        'add',
        array('a' => 'xsd:int', 'b' => 'xsd:int'),
        array('c' => 'xsd:int'),
        'http://soapinterop.org/'
    );
    $soap->service(isset($HTTP_RAW_POST_DATA) ?
        $HTTP_RAW_POST_DATA : '');

    function add($a, $b) {
        return $a + $b;
    }
?>
```

*使用 NuSOAP 的 WSDL 启用 Web 服务 (wsdl-nusoap-server.php)*

回到 WSDL：图 9.3 显示了使用 GET 调用时浏览器中的 Web 服务。点击链接会显示有关 add() 方法的一些信息。在图 9.4 中，你可以看到当你在脚本 URL 后附加 ?WSDL 时（或点击 WSDL 链接）会发生什么：服务的 WSDL 会自动生成。想象一下如果必须手动完成这项工作...

### 使用 NuSOAP 自动生成 WSDL

![](img/1e6d362f187af50011d2666ddaa68739_278_0.png)

图 9.2 这个错误信息是个好兆头——脚本似乎可以正常工作（目前为止）。

![](img/1e6d362f187af50011d2666ddaa68739_278_1.png)

图 9.3 现在 NuSOAP 会自动为服务生成一个信息页面。

### 使用 NuSOAP 自动生成 WSDL

![](img/1e6d362f187af50011d2666ddaa68739_279_0.png)

图 9.4 这个 WSDL 是由 NuSOAP 生成的，而不是程序员。

### 使用 NuSOAP 消费 Web 服务

实际上，使用 NuSOAP 服务甚至比创建它还要容易。你只需要加载 WSDL 文件，然后获取所谓的代理类：这是一个本地类，其行为就好像 Web 服务也是一个本地类一样。因此，你可以直接调用 Web 服务的方法，而 NuSOAP 会处理剩下的所有事情（包括打开到远程服务器的连接、组装和解析 XML 等）。

为此，必须实例化 soapclient 类（不带下划线字符），然后 getProxy() 方法创建代理类。代码

### 使用 PEAR::SOAP 创建 Web 服务

在 PHP 的官方包仓库 PEAR 中，你可以在 http://pear.php.net/package/SOAP 找到一个 SOAP 扩展。它依赖于多个其他包，因此你需要安装下载页面上提到的所有包。当前发布的版本可在 PHP 4 下运行，但 PHP 的 CVS 系统（可通过 http://cvs.php.net/ 在线浏览）包含了一个 PHP 5 的移植版本。本书使用的是 PHP 4 版本，它似乎比 CVS 上的 PHP 5 版本更经过测试且使用更广泛。使用 pear install -f SOAP；你可能会得到 PEAR::SOAP 运行所需的包列表。

```php
<?php
    error_reporting(E_ALL ^ E_NOTICE);
    require_once 'SOAP/Server.php';

    $soap = new SOAP_Server;
    $service = new ServiceClass();
    $soap->addObjectMap($service, 'urn:php-phrasebook-soapservice');
    $soap->service($HTTP_RAW_POST_DATA);

    class ServiceClass {
        function add($a, $b) {
            return $a + $b;
        }
    }
?>
```

使用 PEAR::SOAP 的 Web 服务（soap-pear-server.php）

### 使用 PEAR::SOAP 创建 Web 服务

提供 Web 服务再次只需要几行代码：实例化一个类（SOAP_Server），然后将业务逻辑附加到它（这次，通过将其放入一个类中然后实例化该类）。最后，调用 addObjectMap() 为方法提供一个统一资源名称（URN），然后将其与方法 service() 连接到 $HTTP_RAW_POST_DATA。这段代码包含了所有细节，因此你可以以此为起点创建自己的 Web 服务。

> 警告
> 
> 不幸的是，当 error_reporting 设置为 E_ALL 时，PEAR::SOAP 目前无法正常工作，因为代码中会出现通知。因此，本短语中的代码在加载 PEAR::SOAP 类之前将错误报告设置为较不严重的值。

### 使用 PEAR::SOAP 自动生成 WSDL

PEAR::SOAP 也能自动创建 WSDL；不过它需要程序员提供一些帮助。首先，Web 服务类的构造函数必须设置一个 __dispatch_map 属性，其中包含输入和输出参数的列表。__dispatch_map 属性是一个数组（因此每个 Web 服务支持多个操作），函数名称是签名的键。

此外，你还需要一些代码来检查 URL。如果附加了 ?wsdl，则服务必须返回 WSDL。为此，会实例化 SOAP DISCO Server 类，然后调用其 getWSDL() 方法。

### 使用 PEAR::SOAP 自动生成 WSDL

```php
class ServiceClass {
    var $__dispatch_map = array();

    function ServiceClass() {
        $this->__dispatch_map['add'] = array(
            'in'  => array('a' => 'int', 'b' => 'int'),
            'out' => array('c' => 'int')
        );
    }

    function __dispatch($method) {
        if (isset($this->__dispatch_map[$method])) {
            return $this->__dispatch_map[$method];
        } else {
            return null;
        }
    }
    ..
}
```

*使用 NuSOAP 的 WSDL 启用 Web 服务*
*(wsdl-nusoap-server.php；摘录)*

以下包含服务器代码的其余部分；正如你所预期的那样，在 URL 末尾调用 ?wsdl 会创建服务的 WSDL 描述。

```php
<?php
error_reporting(E_ALL ^ E_NOTICE);
require_once 'SOAP/Server.php';

$soap = new SOAP_Server;
$service = new ServiceClass();
$soap->addObjectMap($service, 'urn:php-phrasebook-soapservice');
```

### 使用 PEAR::SOAP 自动生成 WSDL

```php
if (isset($_SERVER['REQUEST_METHOD']) && $_SERVER['REQUEST_METHOD'] == 'POST') {
$soap->service($HTTP_RAW_POST_DATA);
} else {
require_once 'SOAP/Disco.php';
$disco = new SOAP_DISCO_Server($soap, 'DiscoServer');
if (isset($_SERVER['QUERY_STRING']) && strpos($_SERVER['QUERY_STRING'], 'wsdl') === 0) {
header('Content-type: text/xml');
echo $disco->getWSDL();
}
}

class ServiceClass {
// ...
}
```

### 使用 PEAR::SOAP 消费 Web 服务

在 Web 服务创建并提供 WSDL 生成后，借助 PEAR::SOAP，获取代理类非常容易。用 WSDL 描述实例化 SOAP_WSDL 类，调用 getProxy()，然后使用代理即可。这段代码很简短，但在后台做了相当多的 SOAP 工作。

### 使用 PEAR::SOAP 自动生成 WSDL

```php
<?php
    error_reporting(E_ALL ^ E_NOTICE);
    require_once 'SOAP/Client.php';

    $soap = new SOAP_WSDL('http://localhost/
        wsdl-pear-server.php?wsdl');
    $proxy = $soap->getProxy();
    $result = $proxy->add(47, 11);
    if (PEAR::isError($result)) {
        echo $result->getMessage();
    } else {
        echo "47 + 11 = $result";
    }
?>
```

使用 PEAR::SOAP 消费 Web 服务（wsdl-pear-client.php）

### 使用 PHP 5 的 SOAP 扩展创建 Web 服务

PHP 5 的关键特性之一是新的 SOAP 扩展。由于它是用 C 编写的，因此比纯 PHP 编写的任何东西都要快得多。然而，该扩展相对较新，因此仍有一些小问题和缺失的功能。不过在许多情况下它工作得很好。

你必须使用 -enable-soap 配置 PHP 才能使用该扩展；Windows 用户必须在 php.ini 配置文件中添加 extension=php_soap.dll。然后，扩展即可使用，编写 SOAP 服务器相当容易。

再次强调，这只需要几个步骤：实例化 SoapServer 类，使用 addFunction() 添加你的函数，最后调用 handle()。

### 使用 PHP 5 的 SOAP 扩展创建 Web 服务

```php
<?php
$soap = new SoapServer(null, array('uri' =>
    'http://php.phrasebook.org/'));
$soap->addFunction('add');
$soap->handle();

function add($a, $b) {
    return $a + $b;
}
?>
```

使用 PHP5-SOAP 的 Web 服务（soap-php5-server.php）

提示
PHP 5-SOAP 最初是一个 PECL 扩展。因此，也可以在 PHP 4 下使用此扩展，只需从 CVS 获取代码即可。然而，目前没有预编译的 Windows 二进制文件，而且很可能永远不会有。

### 使用 PHP 5 的 SOAP 扩展自动生成 WSDL

PHP5-SOAP 最大的不足是没有办法自动生成 WSDL。这很少被提及；然而，在现实生活中它确实会造成问题。WSDL 非常复杂，WSDL 中的错误很难被发现，更难找到。

不过，你可以通过几种方式为 Web 服务创建这样的 WSDL 描述，其中大多数已在实际项目中使用过：

- 使用 NuSOAP 或 PEAR::SOAP 创建一个类似的服务，只为获取 WSDL——只需更改 `<soap:address>` 元素
- 使用类 Ctrx_SOAP_AutoDiscover（可在 http://crtx.org/index.php?area=Main&page=CrtxSoapAutoDiscover 获取）
- 使用 Webservice Helper 工具（可在 http://www.jool.nl/new/index.php?file_id=1 获取）
- 使用 WSDL_Gen 类（可在 http://www.schlossnagle.org/~george/php/WSDL_Gen.tgz 获取）

因此可以看出，WSDL 支持正在被开发，但不是作为 SOAP 扩展本身的一部分，而是以外部项目的形式存在。但希望有一天会有所改变。

如果你最终有了服务的 WSDL 描述（在下载归档中，你会找到一个名为 AddService.wsdl 的文件，它源自 PEAR::SOAP 生成的 WSDL），服务器的代码只需要稍作更新。SoapServer 实例化的第一个参数接收 WSDL URL；此外，Web 服务的方法必须

放入一个类中。然后，setClass() 为 SOAP 扩展提供要使用的类的名称。

```
<?php
$soap = new SoapServer(
    'AddService.wsdl',
    array('uri' => 'http://php.phrasebook.org/')
);
$soap->setClass('ServiceClass');
$soap->handle();

class ServiceClass {
    function add($a, $b) {
        return $a + $b;
    }
}
?>
```

### 使用 PHP 5 的 SOAP 扩展消费 Web 服务

只要您有 WSDL 描述，消费再次变得很容易。此代码调用 Web 服务，并且还捕获任何错误，这得益于 PHP 5 的 try-catch 机制。

```
<?php
$soap = new SoapClient('AddService.wsdl');
try {
    $result = $soap->add(47, 11);
    echo "47 + 11 = $result";
} catch (SoapFault $e) {
    echo "Error: {$e->faultstring}";
}
?>
```

### 提示

为了提高性能，PHP 5 的 SOAP 扩展默认缓存 WSDL。以下是 php.ini-recommended 中的标准设置：

```
[soap]
; Enables or disables WSDL caching feature.
soap.wsdl_cache_enabled=1
; Sets the directory name where SOAP extension will put cache files.
soap.wsdl_cache_dir="/tmp"
; (time to live) Sets the number of seconds
; while cached file will be used
; instead of original one.
soap.wsdl_cache_ttl=86400
```

在开发 Web 服务并且可能更改 WSDL 时，这当然是显而易见的。因此，在开发期间将 soap.wsdl_cache_enabled 设置为 Off，但在生产服务器上将其打开。

### 使用有史以来最糟糕的缩写：AJAX

Wikipedia 列出了“Ajax”一词十多种不同的含义，包括荷兰的一支足球球队、荷马《伊利亚特》中的两个人物以及一种家用清洁产品。然而，自几个月前以来，AJAX 也代表“异步 JavaScript + XML”。该技术远非新事物（底层技术，即 JavaScript 中的 XML HTTP 请求，受最近版本的 Internet Explorer 以及包括 Firefox、Safari 和 Konqueror 在内的 Mozilla 浏览器支持——此外，对于此，XML 根本不是必需的），但只有在创造了这个真正愚蠢的术语之后，人们才真正开始使用它。

基本原则是 JavaScript 现在能够调用远程服务器然后处理其返回值，而无需重新加载整个页面。当然，这与 PHP 关系不大；然而，一些 AJAX 类使从 PHP 中使用 AJAX 变得非常容易。

本书的这一最后章节展示了“AJAX”的一个非常简短的演示。本章节使用 Sajax 工具包（S 代表 simple）可在 http://www.modernmethod.com/sajax/ 获取。

此示例的完整代码相当长，因为同时需要 PHP 和 JavaScript。首先，我们需要服务器端逻辑。为此，加载了 Sajax 工具包，它作为单个 PHP 文件提供。然后我们“导出”（注册）所有希望从客户端使用的 PHP 函数。以下示例有一个小型函数，用于生成随机 RGB 颜色。

```
<?php
    require_once 'Sajax.php';

    sajax_init();
    sajax_export('randomColor');
    sajax_handle_client_request();

    function randomColor() {
        $color = '#';
        for ($i=0; $i<3; $i++) {
            $color .= dechex(rand(0, 255));
        }
        return $color;
    }
?>
```

*服务器端应用程序部分（ajax.php；摘录）*

在客户端，对 (PHP) 函数 `sajax_show_javascript()` 的调用完成了大部分工作——它创建了一些 JavaScript 代码行，在后台处理对 Web 服务器的请求。然后，所有之前注册的 PHP 函数都可以在客户端通过在函数名称前加上 `x_` 来调用。作为参数，您必须提供回调函数的名称；当服务器端响应请求时，该函数将被调用。

以下代码每五秒调用一次 `randomColor()` PHP 函数，然后以此随机颜色写入文本——全部无需服务器往返！图 9.5 显示了结果。

```
<script language="JavaScript" type="text/javascript">
    <!--
<?php
    sajax_show_javascript();
?>
    changeColor();
    setInterval('changeColor()', 5000);

    function changeColor() {
        x_randomColor(randomColor_callback);
    }

    function randomColor_callback(result) {
        var text = '<span style="color: ' + result + '">What a dumb acronym ...</span>';
        document.getElementById('output').innerHTML =
            text;
    }
//--></script>
...
<div id="output"></div>
```

客户端应用程序部分（ajax.php；摘录）

![](img/1e6d362f187af50011d2666ddaa68739_292_0.png)

Figure 9.5  使用 JavaScript 和 PHP 显示的文本。

### PEAR 提供了什么？

除了本章提到的几个模块外，以下 PEAR 包在通过 PHP 与他人连接时提供的功能可能有所帮助：

- PEAR 的 HTTP 类别提供了一些相关包，包括 HTTP、HTTP_Client、HTTP_Header、HTTP_Request 和 HTTP_Server。
- 同样，您可以在 Networking 类别中找到有用的包，包括 Net_FTP、Net_IMAP 和 Net_Socket。
- PEAR 的 Services 类别包含多个类，它们为众所周知的 Web 服务提供易于使用的接口。

## 索引

### 符号

- *(asterisk), 25
- *(星号), 25
- \ (backslash), 26
- \ (反斜杠), 26
- ^ (caret), 24
- ^ (插入符号), 24
- $ (dollar sign), 25
- $ (美元符号), 25
- . (dot), 26
- . (点), 26
- " (double primes), 69
- " (双引号), 69
- | (pipe), 25
- | (管道), 25
- ? (question mark), 25
- ? (问号), 25
- [...] special character, 25
- [...] 特殊字符, 25
- + (plus sign), 25
- + (加号), 25
- !== operator, 23
- !== 运算符, 23
- == operator, 6
- == 运算符, 6
- === compare operator, 23
- === 比较运算符, 23
- === operator, 6-7
- === 运算符, 6-7
- 401 status code, 165
- 401 状态码, 165

### A

- access
  - file access
    - PHP built-in class, 191-192
    - PHP 内置类, 191-192
    - relative paths for, 179-180
    - 相对路径, 179-180
    - security traps, 181
    - 安全陷阱, 181
- addslashes() function, 228
- addslashes() 函数, 228
- Advanced Encryption Standard (AES), 13
- 高级加密标准 (AES), 13
- AJAX, 285-287
- AJAX, 285-287
- ajax.php, 286-287
- ajax.php, 286-287
- array() function, 37
- array() 函数, 37
- arrays
  - applying effects to elements, 59-62
  - 对元素应用效果, 59-62
  - converting
    - strings to, 45-46
    - 字符串到数组, 45-46
    - into strings, 46
    - 转为字符串, 46
    - into variables, 45
    - 转为变量, 45
  - creating, 37-38
  - 创建, 37-38
  - filtering, 62-63
  - 过滤, 62-63
  - looping through
    - associative arrays, 40-41
    - 关联数组, 40-41
    - nested arrays, 41-44
    - 嵌套数组, 41-44
    - numerical arrays, 39-40
    - 数值数组, 39-40
  - nesting, 38
  - 嵌套, 38
  - random elements, getting, 63-64
  - 获取随机元素, 63-64
  - randomizing elements, 64
  - 随机化元素, 64
  - sorting
    - alphabetically, 47-48
    - 按字母顺序, 47-48
    - associative arrays, 49-50
    - 关联数组, 49-50
    - natural sorting, 54-55
    - 自然排序, 54-55
    - nested arrays, 50-51
    - 嵌套数组, 50-51
    - nested associative arrays, 52-54
    - 嵌套关联数组, 52-54
    - QuickSort algorithm, 56
    - QuickSort 算法, 56
    - special language characters, 57-58
    - 特殊语言字符, 57-58
- array_filter() function, 62-63
- array_filter() 函数, 62-63
- array_map() function, 59
- array_map() 函数, 59
- array_multisort() function, 51
- array_multisort() 函数, 51
- array_rand() function, 63-64
- array_rand() 函数, 63-64
- array_walk() function, 61
- array_walk() 函数, 61
- arsort() function, 49
- arsort() 函数, 49
- ASCII codes, protecting email addresses, 17-19
- ASCII 代码，保护电子邮件地址, 17-19
- asort() function, 49
- asort() 函数, 49
- associative arrays
  - looping through, 40-41
  - 循环遍历, 40-41
  - sorting, 49-50
  - 排序, 49-50
- attacks
  - directory traversal, 181
  - 目录遍历, 181
- Auth package PEAR), 167
- Auth 包 PEAR), 167
- authentication
  - session management, 162-163
  - 会话管理, 162-163
  - without sessions, 164
  - 无会话, 164

### B-C

- basename() function, 180
- basename() 函数, 180
- bzclose() function, 195-196
- bzclose() 函数, 195-196
- Bzip2 archives, 194-196
- Bzip2 归档, 194-196
- bzopen() function, 195-196
- bzopen() 函数, 195-196
- bzread() function, 196
- bzread() 函数, 196
- bzwrite() function, 195-196
- bzwrite() 函数, 195-196
- check boxes, preselecting, 107
- 复选框，预选, 107
- checkdate() function, 76
- checkdate() 函数, 76
- checksumming strings, 14, 16
- 字符串校验和, 14, 16
- chr() function, 18
- chr() 函数, 18
- closing
  - files, 172
  - 文件, 172
  - sessions, 153
  - 会话, 153
- compareChar() function, 58
- compareChar() 函数, 58
- comparing strings, 6
- 比较字符串, 6
- compress.bz2://, 194-196
- compress.bz2://, 194-196
- compress.zlib://, 193
- compress.zlib://, 193
- compression
  - Bzip2 archives, 194-196
  - Bzip2 归档, 194-196
  - streams, 192-194
  - 流, 192-194
  - ZIP archives, 193-194
  - ZIP 归档, 193-194
- configureWSDL() method, 271
- configureWSDL() 方法, 271
- connecting to
  - Firebird, 231-232
  - Firebird, 231-232
  - FTP servers, 260-262
  - FTP 服务器, 260-262
  - MSSQL/MSDE, 226-227
  - MSSQL/MSDE, 226-227
  - MySQL, 201
  - MySQL, 201
  - MySQLi, 202-203
  - MySQLi, 202-203
  - Oracle, 221-222
  - Oracle, 221-222
  - PostgreSQL, 216
  - PostgreSQL, 216
  - SQLite, 211-212
  - SQLite, 211-212
- converting
  - arrays
    - into strings, 46
    - 转为字符串, 46
    - into variables, 45
    - 转为变量, 45
  - data types, 31-32
  - 数据类型, 31-32
  - strings
    - into arrays, 45-46
    - 转为数组, 45-46
    - into dates, 79-80
    - 转为日期, 79-80
    - into HTML, 9-11
    - 转为 HTML, 9-11
- $_COOKIE array, 133
- $_COOKIE 数组, 133
- Cookie HTTP header, 131
- Cookie HTTP 头, 131
- cookies, 130-132
  - creating, 133, 135
  - 创建, 133, 135
  - deleting, 139
  - 删除, 139
  - domains, setting, 140-142
  - 设置域, 140-142
  - expiry date, setting, 131, 136-138
  - 设置过期日期, 131, 136-138
  - limitations, 130
  - 限制, 130
  - magic quotes, removing, 135
  - 移除 magic quotes, 135
  - prefilling form data from, 102-103
  - 从中预填充表单数据, 102-103
  - raw cookie data, sending, 135
  - 发送原始 cookie 数据, 135
  - reading out, 133
  - 读取, 133
  - saving
    - HTML form data into, 98-100
    - HTML 表单数据到其中, 98-100
  - language preferences, 146-148
  - 语言偏好, 146-148
  - multiple values, 144
  - 多个值, 144
  - specification, 131
  - 规范, 131
  - testing browser support, 142-143
  - 测试浏览器支持, 142-143
- cookietest.php, 142-143
- cookietest.php, 142-143
- copy() function, 190
- copy() 函数, 190
- count() function, 39-41
- count() 函数, 39-41
- Cross-Site Scripting (XSS) attacks
  - HTML markup, removing, 9-11
- 跨站脚本 (XSS) 攻击
  - 移除 HTML 标记, 9-11
- crypt() function, 12-13
- crypt() 函数, 12-13
- CSV files, 182-185
- CSV 文件, 182-185



数据加密标准 (DES)

### D
- 数据加密标准 (DES)，12
- 数据类型。另请参阅特定数据类型
  - 转换，31-32
  - 验证，31-32
- 数据库
  - Firebird
    - 连接到，231-232
    - 从...检索数据，233
    - 发送 SQL 语句到，232-233
  - MSSQL/MSDE
    - 连接到，226-227
    - 从...检索数据，229
    - 发送 SQL 语句到，228-229
  - MySQL
    - 连接到，201
    - 预处理 SQL 语句，206-207
    - 从...检索数据，208-210
    - 发送 SQL 语句到，203-205
  - MySQLi，连接到，202-203
- Oracle
  - 连接到，221-222
  - 从...检索数据，224-226
  - 发送 SQL 语句到，222-224
- PEAR 包，239
- PostgreSQL
  - 连接到，216
  - 插入/更新数据，218
  - 从...检索数据，219-220
  - 发送 SQL 语句到，217-218
- SQLite
  - 连接到，211-212
  - 从...检索数据，214-216
  - 发送 SQL 语句到，213
- 日期和时间，65。另请参阅 date() 函数
  - 基准操作，81，85
  - 将字符串转换为日期，79-80
  - 计算
    - 两个日期之间的差，88-90
    - 相对日期，77

GMT 格式，90
HTML 表单选择字段，84-89
闰年，确定，77
本地化日期，69-73
PEAR 包，90
可排序时间戳，创建，78
特定日期，格式化，74-75
验证日期，76
Date 包 (PEAR)，90
date() 函数，65-67
epoch 值，74
格式化符号，65，67
本地化日期，72-73
在其中使用文本，68-69
Date_Holidays 包 (PEAR)，90
date_sunrise() 函数，80-81
date_sunset() 函数，80-81
DB 包 (PEAR)，239
DB_DataObject 包 (PEAR)，239
DB_QueryTool 包 (PEAR)，239
deletecookie.php，139
DES (数据加密标准)，12-13
目录遍历攻击，181
dirname() 函数，179-180
文档对象模型 (DOM)，245
读取 XML
PHP 4，245-246
PHP 5，246-248
写入 XML
PHP 4，248-249
PHP 5，249-250
domxml_open_file() 函数，246
domxml_open_mem() 函数，246
驱动程序，PDO (PHP 数据对象)，235-236

### E
each() 函数，39-40
电子邮件
地址
使用 ASCII 代码保护，17
验证，33-34
通过...发送 HTML 表单数据，121
加密字符串，12-13

epoch 值
计算日期之间的差异，88-90
将字符串转换为，79-80
date() 格式化符号，67
特定日期，格式化，74-75
ereg() 函数，26-28
eregi() 函数，27
eregi_replace() 函数，34
ereg_replace() 函数，34
欧洲日期格式，74
explode() 函数，46
表达式
打印，19-21
正则表达式
使用...查找标签，30
PCRE，28-29
POSIX，26-28
在字符串中搜索和替换，34-36
其中的特殊字符，24-26
ext/mysql 扩展，201
可扩展标记语言。另请参阅 XML
提取子字符串，16-17

### F
fclose() 函数，172
fgetcsv() 函数，182，184
fgets() 函数，175
File 包 (PEAR)，198
File_Find 包 (PEAR)，198
file() 函数，174
fileatime() 函数，189
filegroup() 函数，189
filemtime() 函数，189
fileowner() 函数，189
文件
访问
PHP 内置类，191-192
相对路径，179-180
安全陷阱，181
关闭，172
复制，190
CSV 文件，182-185
INI 文件，解析，186-187
锁定，178-179
打开，170-171
PEAR 包，198
从...读取数据，174-175
重命名，190
检索文件信息，187-189
使用 HTTP 请求返回，197-198
取消链接，190
上传
移动已上传文件，126-127
检索已上传文件信息，123-125
写入数据到，176-177
$_FILES 数组，123
filesize() 函数，189
file_exists() 函数，173
file_get_contents() 函数，174，260
file_put_contents() 函数，176-177，260
File_SearchReplace 包 (PEAR)，198
过滤数组，62-63
Firebird
连接到，231-232
从...检索数据，233
发送 SQL 语句到，232-233
flock() 函数，178-179
fopen() 函数，170-171
for 循环，39
foreach 循环
关联数组，40
数值数组，39
fputcsv() 函数，184-185
fsocketopen() 函数，259
FTP 服务器连接，260-262
ftp-file.php，261
ftp-functions.php，262
ftp_get() 函数，262
fwrite() 函数，177
$_GET 数组
表单数据，访问，94-95
读取，91
图形提交按钮，114
magic quotes，95-97
必填字段，验证，115
预填充文本字段，101-103
预选单选按钮，105
预选选择列表，110-112
getcookie.php，133
getCookieData() 函数，99，145
getCookieData.inc.php，144-145
getFormDataGET() 函数，103
getFormDataPOST() 函数，103
gettimeofday() 函数，81，85
全局数组，93
gmdate() 函数，90
gmmktime() 函数，90
gmstrftime() 函数，90
GMT 时间格式，90
图形提交按钮，114

### H
HTML
电子邮件地址的字符代码，19
将字符串转换为，9-11
其中的换行，11
标签
使用正则表达式查找，30
删除，10-11
HTML 表单，91-92
日期选择字段，87
表单数据
magic quotes，95-97
读取，93-95
保存到 cookie，98-100
发送回当前脚本，92-93
通过电子邮件发送，121
写入文件，120-121
必填字段，验证，115-116
预填充
密码字段，101-103
文本字段，101-105
预选
复选框，107
单选按钮，105-107
选择列表，108-113
选择列表
用于日期选择，84-85，89
预选，108-113
验证，117-119
提交，检查，97
验证必填字段，30-31
htmlentities() 函数，10
htmlspecialchars() 函数，10，59，101-104
HTML_QuickForm 包 (PEAR)，127
HTTP
头部，查看，132
请求，使用...返回文件，197-198
http-socket.php，259
HTTP_Session 包 (PEAR)，167
http_Upload 包 (PEAR)，127

### I-J
ibase 扩展，231
ibase_connect() 函数，231-232
ibase_connect.php，231
ibase_execute() 函数，232
ibase_fetch.php，233
ibase_fetch_assoc() 函数，233
ibase_fetch_object() 函数，233
ibase_prepare() 函数，232
ibase_query() 函数，232
implode() 函数，46，174
INI 文件，解析，186-187
InterBase。另请参阅 Firebird
IP 地址，排序，54-55
is_array() 函数，31
is_bool() 函数，31
is_dir() 函数，189
is_executable() 函数，189
is_file() 函数，189
is_float() 函数，31
is_int() 函数，31
is_link() 函数，189
is_null() 函数，31
is_numeric() 函数，31-32
is_object() 函数，31
is_readable() 函数，189
is_string() 函数，31
is_uploaded_file() 函数，189
is_writable() 函数，189

### K-L
krsort() 函数，49
ksort() 函数，49，52
闰年，确定，77
换行，11
list() 函数，45
本地化日期，69-73
锁定文件，178-179
循环遍历
关联数组，40-41
嵌套数组，41-44
数值数组，39-40

### M
- magic quotes，95-97
  - 从 cookie 中移除，135
- MD5 (消息摘要算法 5)，14-16
- md5() 函数，16
- MDB 包 (PEAR)，239
- MDB2 包 (PEAR)，239
- Microsoft SQL Server Desktop Engine。另请参阅 MSDE
- Microsoft SQL Server。另请参阅 MSSQL
- microtimestamp() 函数，82-85
- mktime() 函数，75
- mod_files.sh 脚本，149
- 移动已上传文件，126-127
- MSDE
  - 连接到，226-227
  - 从...检索数据，229
  - 发送 SQL 语句到，228-229
- MSSQL
  - 连接到，226-227
  - 从...检索数据，229
- mssql_connect() 函数，227
- mssql_fetch_assoc() 函数，229
- mssql_fetch_object() 函数，229
- mssql_fetch_row() 函数，229
- mssql_query() 函数，228
- 多行文本字段，预填充，104-105
- multilingual.php，147
- MySQL
  - 连接到，201
  - 预处理 SQL 语句，206-207
  - 从...检索数据，208-210
  - 发送 SQL 语句到，203-205，228-229
- MySQLi，连接到，202-203
- mysqli_autocommit() 函数，207
- mysqli_commit() 函数，207
- mysqli_connect() 函数，202
- mysqli_fetch_row() 函数，208
- mysqli_insert_id() 函数，208
- mysqli_prepare() 函数，206-207



### N

### O
mysqli_query() 函数, 203
mysqli_rollback() 函数, 207
mysqli_stmt_execute() 函数, 207
mysql_close() 函数, 201
mysql_connect() 函数, 201-202
mysql_fetch_assoc() 函数, 208
mysql_fetch_object() 函数, 208
mysql_fetch_row() 函数, 208
mysql_insert_id() 函数, 208
mysql_query() 函数, 203
mysql_real_escape_string() 函数, 203
natcasesort() 函数, 55
natsort() 函数, 55
Natural Order String Comparison 项目, 55
自然排序, 55
嵌套数组
  遍历, 41-44
  打印, 41, 44
  排序, 50-54

嵌套数组, 38
Net_FTP 包 (PEAR), 288
Net_IMAP 包 (PEAR), 288
Net_Socket() 包 (PEAR), 288
nl2br() 函数, 11
数值数据类型, 转换, 31-32
数值数组
  遍历, 39-40
  排序, 47-48
NuSOAP
  使用 Web 服务, 274-275
  创建 Web 服务, 270-271
  生成 WSDL, 271-274
ocilogon() 函数, 222
oci_bind_by_name() 函数, 223
oci_connect() 函数, 221-222
oci_connect.php, 221
oci_execute() 函数, 223
oci_execute.php, 222

### P
oci_fetch.php
oci_fetch.php, 224
oci_fetch_all() 函数, 224
oci_fetch_assoc() 函数, 224
oci_fetch_object() 函数, 224
oci_fetch_row() 函数, 224
oci_parse() 函数, 223
打开文件, 170-171
Oracle
  连接, 221-222
  检索数据, 224-226
  发送 SQL 语句到, 222-224
ord() 函数, 18
包 (PEAR)
  Auth, 167
  HTTP_Session, 167
包. 参见 PEAR 包
parse_ini_file() 函数, 186-187
解析
  INI 文件, 186-187
  XML, 242-244
密码字段, 预填充, 101-103

密码
  加密, 12-13
  验证, 7-8
PCRE (Perl 兼容正则表达式), 24, 28-29
PDO (PHP 数据对象), 234, 236-238
pdo_execute.php, 236
pdo_fetch.php, 237
PEAR 包
  Auth, 167
  Date, 90
  Date_Holidays, 90
  DB, 239
  DB_DataObject, 239
  DB_QueryTool, 239
  File, 198
  File_Find, 198
  File_SearchReplace, 198
  HTML_QuickForm, 127
  HTTP_Session, 167
  HTTP_Upload, 127
  MDB2, 239
  Net_FTP, 288
  Net_IMAP, 288
  Net_Socket, 288
  Stream_Var, 198
  XML_Beautifier, 256
  XML_DTD, 256
  XML_Serializer, 256
  XML_Util, 256

PEAR::SOAP
  使用 Web 服务, 279
  创建 Web 服务, 276-277
  生成 WSDL, 277-278
PEAR::XML-RPC
  使用 Web 服务, 268-269
  创建 Web 服务, 266-267
pg_connect() 函数, 216
pg_connect.php, 216
pg_escape_string(), 217
pg_fetch_all() 函数, 220
pg_fetch_assoc() 函数, 219
pg_fetch_object() 函数, 219
pg_fetch_row() 函数, 219
pg_insert() 函数, 218
pg_insert.php, 218
pg_last_oid() 函数, 218
pg_query() 函数, 217-219
pg_select() 函数, 220
pg_update() 函数, 218
PHP, 安全的 PHP 页面, 164
PHP 数据对象 (PDO), 234
PHP 流, 192-194
PHP5-SOAP
  使用 Web 服务, 283-284
  创建 Web 服务, 280-281
  生成 WSDL, 282-283
phpMyAdmin, 200
phpversion() 函数, 26
Pool, Martin, 55
POSIX 正则表达式, 26-28
$_POST array
  访问表单数据, 94-95
  图形提交按钮, 114
  魔术引号, 95-97
  必填字段, 验证, 115
  单选按钮, 预选, 105
  选择列表, 预填充, 110-112
  文本字段, 预填充, 101-103
PostgreSQL
  连接, 216
  插入/更新数据, 218
  检索数据, 219-220
  发送 SQL 语句到, 217-218
预填充 HTML 表单
  密码字段, 101-103
  文本字段, 101-105
preg_match() 函数, 28-29
preg_match_all() 函数, 28-29
preg_replace() 函数, 34
预处理语句, 使用 MySQL, 206
预选
  复选框, 107
  单选按钮, 105-107
  选择列表, 108-113
printf() 函数, 20-21
print_r() 函数, 41, 44

### Q-R
Quicksort 算法, 56

单选按钮, 预选, 105-107
随机化数组元素, 64
原始 cookie 数据, 发送, 135
readfile() 函数, 174
读取
  cookies, 133
  文件数据, 174-175
  HTML 表单数据, 93-95
  会话, 152
  XML
    PHP 4, 245-246
    PHP 5, 246-248
正则表达式, 24-26
  使用查找标签, 30
  PCRE, 28-29
  POSIX, 26-28
  在字符串中搜索和替换, 34-36
  特殊字符, 24-26
相对日期, 计算, 77
相对路径, 用于文件访问, 179-180
relaxNG, 验证 XML, 254
rename() 函数, 190
$_REQUEST array, 94-95
请求 (HTTP) 返回文件, 197-198
REST (表述性状态), 265
检索查询数据
  来自 Firebird, 233
  来自 MySQL, 208-210
  来自 Oracle, 224-226
  通过 PDO, 237
  来自 PostgreSQL, 219-220
  来自 SQLite, 214-216
rsort() 函数, 48

### S
sajax_show_javascript() 函数, 286
saveLanguage.inc.php, 146-147
保存 HTML 表单数据到 cookies, 98-100
SAX (XML 简单 API), 242-244
扫描格式化字符串, 21-22
模式, 验证 XML, 254-255
搜索子字符串, 23-24
在字符串中搜索和替换, 34-36
安全, 文件访问, 181
选择列表
  用于日期选择, 84-85, 89
  预选, 108-113
  验证, 117-119
serialize() 函数, 102
serverstatus.php, 263
session.auto_start 指令, 151
session.save_path 指令, 149
session.user_trans_sid 指令, 151
session.use_trans_sid 指令, 155
会话, 148-149
  激活, 151-152
  关闭, 153
  自定义管理, 实现, 157-158, 161
  ID, 更改, 154-155
  维护状态, 150-151
  PEAR 包, 167
  读取和写入, 152
  创建会话感知动态链接, 155-156
  存储, 149-150
  用户身份验证, 检查, 162-163
session_authentication.inc.php, 162
session_destroy() 函数, 153
session_id() 函数, 156
session_link.php, 155
session_name() 函数, 156
session_readwrite.php, 152
session_regenerate_id() 函数, 154
session_regenerate_id.php, 154
session_set_save_handler() 函数, 158
session_start() 函数, 151
session_start.php, 151
Set-Cookie HTTP 头, 131
setcookie() 函数, 133-135
setcookie-domain.php, 140, 142
setcookie-expiry.php, 136-137
setcookie-specific.php, 137-138
setcookie.php, 133
setlocale() 函数, 69-71
setrawcookie() 函数, 135
SHA1 (安全哈希算法 1), 14-16
sha1() 函数, 16
shuffle() 函数, 64
SimpleXML 扩展, 250-251
simplexml_import_dom() 函数, 251
simplexml_load_file() 函数, 251
simplexml_load_string() 函数, 251
SOAP, 265-266
soap-pear-server.php, 276
soap-php5-server.php, 281

sort() 函数
  关联数组, 50
  嵌套数组, 51
  数值数组, 47-48
可排序时间戳, 创建, 78
排序
  数组
    按字母顺序, 47-48
    关联数组, 49-50
    自然排序, 54-55
    嵌套数组, 50-51
    嵌套关联数组, 52-54
    QuickSort 算法, 56
    特殊语言字符, 57-58
  IP地址, 54-55
特殊字符, 在正则表达式中, 24-26
sprintf() 函数, 21
SQL
  使用 MySQL 的预处理语句, 206-207
  查询数据, 检索
    来自 Firebird, 233
    来自 MSSQL/MSDE, 229
    来自 MySQL, 208-210
    来自 Oracle, 224-226
    来自 PostgreSQL, 219-220
    来自 SQLite, 214-216
    通过 PDO, 237
  发送语句
    到 Firebird, 232-233
    到 MSSQL/MSDE, 228-229
    到 MySQL, 203-205
    到 Oracle, 222-224
    通过 PDO, 236
    到 PostgreSQL, 217-218
    到 SQLite, 213
SQLite
  连接, 211-212
  检索数据, 214-216
  发送 SQL 语句到, 213
sqlite_escape_string() 函数, 213
sqlite_exec 函数, 214
sqlite_exec() 函数, 213
sqlite_exec.php, 213
sqlite_fetch_all() 函数, 214-216
sqlite_fetch_array() 函数, 214-216
sqlite_fetch_object() 函数, 214-216
sqlite_last_insert_rowid() 函数, 214
sqlite_open() 函数, 212
sqlite_open.php, 211-212
sqlite_query() 函数, 214
sscanf() 函数, 21
strcasecmp() 函数, 6-7
strcmp() 函数, 6-7
流, 192-194
  PEAR 包, 198
  返回内容, 174
Stream_Var 包 (PEAR), 198
strftime() 函数, 69-72
字符串
  校验和, 14-16
  比较, 6
  转换
    数组到, 46
    到数组, 45-46
    到日期, 79-80
    到 HTML, 9-11
  在 date() 函数中, 68-69
  加密, 12-13
  提取子字符串, 16-17
  打印, 19, 21



- 字符串
- 正则表达式，24-30
- 扫描格式化字符串，21-22
- 在其中搜索和替换，34-36
- 搜索子字符串，23-24
- 在 URL 中，10
- 验证
- 数据类型，31-32
- 电子邮件地址，33-34
- 必填表单字段输入，30-31
- 密码，7-8
- 用户名，7-8
- 变量，获取其信息，22-23
- stripCookieSlashes.inc.php，135
- stripslashes() 函数，96, 135
- strip_tags() 函数，10-11
- strnatcmp() 函数，55, 58
- strpos() 函数，23
- strtolower() 函数，7
- strtotime() 函数，79-80
- strtoupper() 函数，7
- str_replace() 函数，35
- substr() 函数，16-17
- 子字符串
- 提取，16-17
- 搜索，23-24
- 日出和日落时间，确定，80-81
- 超级全局数组，访问表单数据，94

### T-U

- 标签（HTML）
- 使用正则表达式查找，30
- 移除，10-11
- 文本字段，预填充，101, 103-105
- 时间戳
- 基准测试，82, 85
- 计算相对日期，77
- 将字符串转换为，79-80
- GMT 格式，90
- 可排序的时间戳，创建，77-78
- 时间。参见日期和时间
- 转换 XML，252-253
- trim() 函数，31

- 英国日期格式，74
- 美国日期格式，74
- unlink() 函数，190
- 删除文件，190
- unserialize() 函数，102
- 上传文件
  - 移动上传的文件，126-127
  - 获取已上传文件的信息，123-125
- urlencode() 函数，10
- URL，准备字符串以供使用，10
- 用户名，验证，7-8
- usort() 函数，56

### V-W

- 验证
  - 数据类型，31-32
  - 日期，76
  - 电子邮件地址，33-34
  - HTML 表单
    - 必填字段，30-31, 115-116
    - 选择列表，117-119
  - 密码，7-8
  - 用户名，7-8
  - XML，254-255

- 变量
  - 检查其数据类型，31
  - 将数组转换为，45
  - 获取其信息，22-23
  - 打印，19-21
- var_dump() 函数，22
- var_export() 函数，23
- vprintf() 函数，21
- vsprintf() 函数，21

- Web 表单。参见 HTML 表单
- Web 服务器
  - FTP 服务器连接，260, 262
  - HTTP 服务器连接，257-260
  - 状态，检查，263-264
- Web 服务，264-266
  - 调用
    - 使用 NuSOAP，274-275
    - 使用 PEAR::SOAP，279
    - 使用 PEAR::XML-RPC，268-269
    - 使用 PHP5-SOAP，283-284

### Web Services

- 创建
  - 使用 NuSOAP，270-271
  - 使用 PEAR::SOAP，276-277
  - 使用 PEAR::XML-RPC，266-267
  - 使用 PHP5-SOAP，280-281
- WSDL，265-266
  - 使用 NuSOAP 生成，271-272, 274
  - 使用 PEAR::SOAP 生成，277-278
  - 使用 PHP5-SOAP 生成，282-283
- while 循环
  - 关联数组，41
  - 数值数组，39
- 写入
  - 将数据写入文件，176-177
  - 将 HTML 表单数据写入文件，120-121
  - 会话，152
  - XML
    - PHP 4，248-249
    - PHP 5，249-250

### X-Y-Z

- WSDL（Web 服务描述语言），265-266
  - 使用 NuSOAP 生成，271-274
  - 使用 PEAR::SOAP 生成，277-278
  - 使用 PHP5-SOAP 生成，282-283
- wsdl-nusoap-client.php，275
- wsdl-nusoap-server.php，272
- wsdl-php5-client.php，283
- XML，241-242
  - 使用 SAX 解析，242-244
- PEAR 包，256
- 读取
  - PHP 4，245-246
  - PHP 5，246, 248
- SimpleXML 扩展，250-251
- 验证，254-255
- 写入
  - PHP 4，248-249
  - PHP 5，249-250
- XSLT（XSL 转换），252-253

- XML-RPC，265-266
- PEAR::XML-RPC
  - 调用 Web 服务，268-269
  - 创建 Web 服务，266-267
- xmlrpc-pear-client.php，269
- XMLRPCi 扩展，269
- XMLReader，244
- xmlrpc-pear-server.php，267
- XMLTextReader，244
- XMLWriter，244
- XML_Beautifier 包（PEAR），256
- XML_DTD 包（PEAR），256
- xml_parser_create() 函数，243
- xml_parser_set_option() 函数，243
- XML_Serialize 包（PEAR），256
- xml_set_character_data_handler() 函数，243
- xml_set_element_handler() 函数，243
- XML_Util 包（PEAR），256
- XSLT（XSL 转换），252-253

- XSS（跨站脚本）攻击，9-11
- ZIP 文件
  - PHP 内置函数，193-194
- compress.zlib://，193
- zip_entry_open() 函数，193
- zip_entry_read() 函数，193
- zip_open() 函数，193
- zip_read() 函数，193
- ZZIPLib 库，193

## 已撤销

不再是波士顿公共图书馆的财产。
出售此材料将使图书馆受益。

![](img/1e6d362f187af50011d2666ddaa68739_316_0.png)

Developer's Library 短语手册为常见、日常的代码“短语”提供了方便的参考。这些短语手册是写给那些已经熟悉一门新语言但尚未完全精通其代码的程序员的。

| 书名 | 作者 | ISBN |
|---|---|---|
| PHP 短语手册 | Christian Wenz | 0-672-32817-8 |
| MySQL 短语手册 | Zak Greant | 0-672-32839-9 |
| Apache 短语手册 | Daniel Lopez and Jesus Blanco | 0-672-32836-4 |
| Linux 短语手册 | Scott Granneman | 0-672-32838-0 |

## PHP 短语手册

《PHP 短语手册》为你提供所需的代码，助你使用 PHP 快速有效地完成 Web 编程项目。PHP 是用于创建动态网页的主流脚本语言。

### 简洁且易用

易于携带、易于使用——让你舍弃那些笨重的书籍，仅凭一本便携式口袋指南即可。

### 灵活且实用

包含 100 多个可定制的代码片段——让你几乎在任何情况下都能轻松编写出实用的 PHP 代码。

Christian Wenz 是一位作家、培训师和顾问，专注于 Web 技术。他是 PHP 安全联盟的创始成员之一，并为 PEAR 存储库中的多个 PHP 包做出了贡献。
