
# PHP和MySQL短语手册（开发者库）

## 索引 321

## 关于作者

Christian Wenz 是一位专业的措辞者、作者、培训师和顾问，专注于 Web 技术。他撰写或合著了超过一百本书。他经常为知名 IT 杂志撰稿，并在全球各地的开发者大会上演讲。Christian 为多个 PHP 库和框架以及其他开源软件做出贡献。他拥有计算机科学和商业信息学的大学学位，并在德国慕尼黑生活和工作。他也是 Zend PHP 5 和 PHP 5.3 认证的作者之一。

## 我们想听听您的意见！

作为本书的读者，您是我们最重要的批评者和评论者。我们重视您的意见，想知道我们做得对的地方、可以改进的地方、您希望我们出版的领域，以及您愿意分享的任何其他智慧之言。

您可以直接通过电子邮件或信件告诉我们您喜欢或不喜欢本书的内容——以及我们可以如何让我们的书籍更出色。

请注意，我们无法帮助您解决与本书主题相关的技术问题，并且由于我们收到的邮件数量很大，可能无法回复每一条信息。

写信时，请务必包含本书的标题和作者，以及您的姓名和联系方式。

Email: feedback@developers-library.info

Mail: Reader Feedback

Addison-Wesley Developer's Library

800 East 96th Street

Indianapolis, IN 46240 USA

## 读者服务

访问我们的网站并在 informit.com/register 注册本书，以便方便地获取本书可能提供的任何更新、下载或勘误。

## 引言

有一次，我最喜欢的开发编辑 Damon Jordan 给我发了一封电子邮件，结尾写着“ Ich möchte eine Föhnwelle，”意思是“ I’d like a blow wave。”不幸的是，我不知道 Föhnwelle 或 blow wave 是什么，所以我拒绝了。然后他告诉我，他在最近买的一本德语 phrasebook 里找到了这句话。

我很感兴趣，于是看了一些德语 phrasebook。我认为它们是在外国旅行时非常实用的工具，虽然我个人认为其中一些提供的短语根本不合逻辑。例如，在一本 phrasebook 中，我找到了一系列搭讪台词，其中包括巧妙的“ You have a beautiful personality，”这种话无论在英语、德语还是任何其他语言中对我都不起作用！一些当地指导也可能导致其他问题——你必须记住在做事时要说的一切，或者你必须用空闲的手拿着 phrasebook。最后，“ Blow waves are as dead as a pet rock，”只是再举一个例子。

无论如何，我们稍微讨论了一下 phrasebook，Damon 说他想做一个关于 phrasebook 的书系。他还提到他想与他和我最喜欢的收购编辑 Shelley Johnston 合作，所以我加入了。

在构思概念时，我们发现了语言 phrasebook 和 IT phrasebook 之间的一些差异。例如，语言 phrasebook 只是在两种语言中对照相同的句子。

然而，这并不总是有所帮助。如果想稍微改变一下短语怎么办，例如如果你想要一个 en vogue blow wave（可以说是一个矛盾修辞）？

因此，我们尝试创建一个包含大量短语的概念，但所有短语都有良好的解释，以便轻松更改代码并适应个人需求。当然，这使得短语的“ foreign language”部分比短语本身稍长一些，但我们认为在阅读本书时这真的很有帮助。

我还记得一个著名的 Monty Python 小品，其中有人使用了一本被破坏的词典，以至于询问方向会导致被殴打。因此，了解短语内部正在发生什么的真实解释至关重要。

然后我写了系列概念和一个样章，现在，仅仅几个月后，你就拿到了第一本 phrasebook（我们希望是众多之一）。

我真的很讨厌阅读计算机书籍时，代码示例被拼凑到文字处理器中却从未经过测试。为避免这种情况，每个列表也可以在 http://php.phrasebook.org 下载：文件名是列表标题的一部分。因此，每个代码示例都作为文件存在，并且实际上已经过测试，不像某些其他书籍。当然，这本书百分之百无错误只是一种错觉，尽管我们采取了多项措施来接近这一标准。任何已知的勘误也会发布在该网站上。

我不喜欢的一些书籍的另一点是它们往往非常依赖操作系统，而这对于 PHP 来说真的没有必要。一些书籍显然只在 Windows 下测试过，其他一些只在 Linux 下测试过，但可以使代码相对平台独立。我们投入了大量精力在许多服务器平台上测试本书的代码，包括 Linux、Windows、Mac OS X 和 Solaris。因此，本书中的屏幕截图也是从这些平台上截取的，所以你会发现系统（和浏览器）的健康混合。意识形态可以用许多短语表达，但你不会在这本书中找到任何这些。如果某些内容仅在特定平台（或 PHP 版本）上运行，文中会有所说明。我向你保证，你不会在这本书中找到任何看起来像 `foo`、`bar`、`baz` 或任何其他缺乏想象力的证明的短语。

当然，很容易在这本书中找到缺失的短语。PHP 提供了如此多的功能，以至于不可能涵盖每个方面。因此，我们必须选择某些感兴趣的话题——与 PHP 程序员日常工作相关的内容。如果你认为确实遗漏了某些东西，请告诉我（但也请提名一些应该从本书的后续版本中删除的内容，以腾出空间给新短语）。我期待收到你的反馈。

现在，再引用 phrasebook 一次：“ Bist du soweit? Da boxt der Papst。” That is, “ Are you ready? It’s all happening there” （但字面意思是“ There boxes the pope。”）

你的个人措辞者，

Christian Wenz

## 第二版导言

几年前我们构思 Phrasebook 系列时，对首批计划出版的书籍会取得好成绩相当有信心。如今回头看，仍有十几本书在世，并且有相当数量的外语译本，我可以说我们做得*真的*很好。令我个人感到相当自豪的是，试点作品 *PHP 短语手册* 依然经受住了时间的考验，而且当我拜访客户现场时，我很开心经常能看到这本书。

然而，过去几年 PHP 已有了相当大的进展。PHP 4 最终已消失，虽然备受期待的 PHP 6 从未实现，但 PHP 5.3 和 5.4 版本增加了许多新功能，其中很多原本是为下一个主要 PHP 更新而计划的。

我们借此机会将 *PHP 短语手册* 更新到 PHP 的最新发展。由于原书获得了非常出色的反馈，我们尝试保持原有的结构和热门短语不变，但我们增加了数十个新短语和更新的短语，突出了 PHP 5.3 和 5.4 的许多新可能性。为了向后兼容，我们始终提及新功能是在哪个 PHP 版本中引入的，并且在可能的情况下，如果我们认为合适，我们会提供不一定需要最新最好的代码。

书名也有了一些变化。第一版中我们涵盖了许多相关的数据库，现在仍然如此；然而，MySQL 仍然是 PHP 开发的事实标准数据库，因此它拥有自己的章节，并在书名页上占有一席之地。

我很感激许多读者提供的建议、勘误和一般反馈。当然，对本书这一版的任何反馈也都非常受欢迎。网站 http://php.phrasebook.org/ 包含本书的代码示例、勘误（在我得知后会尽快更新）以及联系信息。我期待听到你们的来信！

和大多数书籍一样，这是一项团队合作。Mark Taber 当年监督 Phrasebook 系列的创建，现在仍在团队中，并担任本版的项目经理。我仍然记得我们在极少数真正面对面见面的机会之一的早餐时起草新版的情况。（下次我请客。）我很高兴我的老朋友 John Coggeshall 愿意担任技术审阅者——并且几次挽救了我的声誉。还要“谢谢”Pearson 的巫师团队，他们把我的手稿变成专业的书籍。感谢我的家人和朋友，他们接受我的职业偶尔需要的奇怪工作时间。

## 操作字符串

PHP 支持的所有数据类型中，字符串数据可能是使用最频繁的一种。原因之一是，在向客户端发送内容时，某时某刻需要对某物进行字符串表示。

PHP 提供了大量适用于字符串的函数，几乎有 100 个。此外，正则表达式在查找字符串中的某些模式时也很有用。然而在现实生活中，实际使用的函数只占很小一部分。它们大多数都值得拥有忠实的粉丝群，但一些被低估的函数应该得到更多关注。本章中的短语提供了两者兼顾的良好组合：标准应用以及相当不寻常但非常有用的字符串处理方式。

### 比较字符串

```
strcmp($a, $b)
strcasecmp($a, $b)
```

```php
<?php
$a = 'PHP';
$b = 'php';
echo 'strcmp(): ' . strcmp($a, $b) . '<br />';
echo 'strcasecmp(): ' . strcasecmp($a, $b);
?>
```

*比较字符串 (compare.php)*

输出如下：

```
strcmp(): -32
strcasecmp(): 0
```

比较字符串似乎是一项简单的任务——使用 `==` 运算符进行隐式类型转换（因此 `'1' == 1` 返回 `true`）或使用 `===` 运算符进行类型检查（因此 `'1' === 1` 返回 `false`）。然而，第一种方法相当有缺陷，因为类型转换并不总是转换为字符串。例如，`1 == '1twothree'` 也返回 `true`；两个值都被转换为整数。因此，`===` 才是正确的方法。

然而，PHP 还提供了一些功能比仅仅比较字符串并返回 `true` 或 `false` 更强大的函数。`strcmp()` 在作为第一个参数传递的字符串大于第二个参数时返回正值，小于时返回负值。如果两个字符串相等，`strcmp()` 返回 `0`。如果不需要区分大小写，则使用 `strcasecmp()`。它与 `strcmp()` 工作方式相同，但不区分大小写字母。

这两个函数可用于排序数组。有关自定义数组排序的更多信息，请参阅第 2 章，“使用数组。”

### 检查用户名和密码

```php
<?php
$user = (isset($_GET['user'])) ? $_GET['user'] : '';
$pass = (isset($_GET['pass'])) ? $_GET['pass'] : '';

if (
    (strtolower($user) === 'damon' && $pass === 'secret') ||
    (strtoupper($user) === 'SHELLEY' && $pass === 'verysecret') ||
    (strcasecmp($user, 'Christian') == 0 && strcmp($pass, 'topsecret') == 0)
) {
    echo 'Login successful.';
} else {
    echo 'Login failed.';
}
?>
```

*通过比较字符串验证登录 (comparelogin.php)*

在验证用户名和密码时（例如，在支持 HTML 登录表单的脚本中），网络上似乎形成了两种事实标准：

- 密码始终区分大小写。它必须以设置时完全相同的方式提供。

- 然而，用户名不区分大小写。

因此，用户名必须在不考虑大小写的情况下进行比较。这可以通过使用 `strcasecmp()` 来完成——参见上一条短语——或先将提供的用户名和真实用户名都转换为小写字母（或大写字母）。这由函数 `strtolower()` 或 `strtoupper()` 完成。上面的代码展示了使用 `strcmp()`/`strcasecmp()` 以及比较运算符 `==` 的示例。

根据调用脚本的统一资源定位符（URL）中提供的数据，登录要么失败要么成功。例如，以下 URL 成功登录用户。（你需要更改 `服务器名` 部分。）

```
http://servername/comparelogin.php?user=CHRISTIAN&pass=topsecret
```

相比之下，以下登录会失败：

```
http://servername/comparelogin.php?user=Christian&pass=TopSecret
```

注意：当然，通过 GET 提供用户名和密码是非常糟糕的做法；建议使用 POST。（有关表单数据的更多详细信息，请参阅第 4 章，“与 Web 表单交互”。）然而，出于测试目的，本章的代码使用 GET。

### 将字符串转换为 HTML

```
htmlspecialchars($input)
htmlentities($input)
```

```php
<?php
$input = '<script>alert("I have a bad \'Föhnwelle\', therefore I crack websites.");</script>';
echo htmlspecialchars($input, ENT_QUOTES) . '<br />';
echo htmlentities($input);
?>
```

*转义字符串以用于 HTML (htmlescape.php)*

一种常用的网络攻击称为跨站脚本（XSS）。例如，用户在 Web 表单中输入一些恶意数据，如 JavaScript 代码；Web 页面随后在某个时候原样输出这些信息，而未进行适当的转义。这方面的标准例子是 Web 访客簿或讨论表单。人们输入文本供他人查看。

这里，重要的是要删除某些 HTML 标记。简单来说：几乎不可能真正捕获所有将 JavaScript 注入数据的尝试。它不仅总是使用 `<script>` 标签完成，还会在其他 HTML 元素中使用，例如 `<img onabort="badCode()" />`。因此，在大多数情况下，必须删除所有 HTML。

这样做最简单的方法是调用 `htmlspecialchars()`：它将字符串转换为 HTML，包括将所有 `<` 和 `>` 字符替换为 `&lt;` 和 `&gt;`。一个值得注意的例外是单引号，默认情况下不会被转换。然而，当使用 `ENT_QUOTES` 常量作为第二个参数时，单引号也会被正确转义：

```
htmlspecialchars($input, ENT_QUOTES)
```

另一个选项是调用 `htmlentities()`。它会为字符使用 HTML 实体（如果可用）。上面的代码展示了这两种方法之间的差异。德语 ö（o 分音符）不会被 `htmlspecialchars()` 转换；然而，`htmlentities()` 会将其替换为实体 `&ouml;`。

使用 `htmlspecialchars()` 和 `htmlentities()` 只是在浏览器中输出用户输入的内容。因此，如果用户输入 HTML 标记，这个标记本身就会被显示。因此，`htmlspecialchars()` 和 `htmlentities()` 让浏览器满意，但可能不会让用户满意。

注意：如果你想准备要在 URL 中使用的字符串，你必须使用 `urlencode()` 来正确编码诸如空格字符等不能在 URL 中使用的特殊字符。

然而，函数 `strip_tags()` 会完全去掉所有 HTML 元素。如果你只想保留某些元素（例如，使用 `<b>` 和 `<i>` 和 `<br />` 标签的一些有限格式功能），你可以在 `strip_tags()` 的第二个参数中提供允许值的列表。下面的脚本展示了这一点：图 1.1 描述了其输出。如你所见，所有不需要的 HTML 标签已被删除；然而，其内容仍然存在：

```php
<?php
$input = 'My parents <i>hate</i> me, <br />' .
'therefore I <b>crack</b> websites. ' .
'<script>alert("Nice try!");</script> ' .
'<img src="explicit.jpg" />';

echo strip_tags($input, '<b><br><i>');
?>
```

图 1.1 部分HTML标签已被剥离，但并非全部。

### 使用换行符

```php
<?php
$input = "One\nTwo\r\nThree";
echo nl2br($input);
?>
```

在每个换行处添加 `<br />` 元素（nl2br.php）

在HTML中如何使用换行符？这很简单：使用 `<br />` HTML元素即可。但是，如果数据中包含`\n`或`\r\n`换行符呢？人们可能会想到搜索替换；然而，使用PHP内置函数`nl2br()`要容易得多。该函数解析字符串并将所有换行符转换为`<br />`元素，如前面的脚本所示。

如你所见，换行符仍然存在，但`<br />`元素已经被添加。

### 加密字符串

```php
<?php
$pass = (isset($_GET['pass'])) ? $_GET['pass'] : '';
$encpass = '$1$FK3.qn2.$S15Kh...';

if (crypt($pass, $encpass) === $encpass) {
    echo 'Login successful.';
} else {
    echo 'Login failed.';
}
?>
```

使用加密密码检查登录（crypt.php）

密码绝不应原样存储在数据库中，而应加密存储。某些数据库在内部提供加密功能；对于其他所有情况，

PHP可以帮忙。`crypt()` 函数使用数据加密标准（DES）对字符串进行加密。这是一种单向加密，因此无法还原。此外，每次调用 `crypt()` 都会产生不同的结果。



例如，字符串 `'TopSecret'` 被加密为 `$1$FK3.qn2.$5i5KhnprsRb.N.SEF4GMW0`（还有 `$1$Sm61.i12.$0p1j3EHWk1XycncyepP1FZ0` 和 `$1$9S3.c/3.$5I01Bm4v3cnBNOb1AECi1.`，但本示例采用第一个）。要检查某个值是否对应于调用 `crypt()` 得到的结果，可以再次调用 `crypt()`：`crypt($value, $encryptedValue)` 必须返回 `$encryptedValue`。

前面的脚本检查通过URL提供的密码是否与之前 `crypt()` 的结果匹配。使用GET参数 `pass=TopSecret` 调用此脚本可以成功登录；所有其他密码都会失败。

**注意：** 更详细地说：`crypt()` 的第二个参数是用于加密数据的盐（初始化值）。你也可以在加密原始密码时使用盐。但是，必须确保盐值是唯一的；否则加密将不安全。因此，不要使用自定义盐值，让 PHP 来处理。另外需要提醒的是，DES 加密大约在24小时内就可能被破解，因此它已不再是万无一失的。一个更新的替代方案是高级加密标准（AES）。

### 字符串校验和

```
<?php
    $pass = (isset($_GET['pass'])) ? $_GET['pass'] : '';
    
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

使用 SHA1 和 MD5 哈希检查登录

(checksum.php)

PHP 提供了两个主要函数来创建校验和：

- `md5()` 计算字符串的 MD5 哈希值。

- `sha1()` 计算字符串的 SHA1 哈希值。

将 `crypt()` 用于字符串类似于为某些内容创建校验和；可以很容易地判断字符串是否与校验和匹配；但是，从校验和反推原始字符串并不（容易）可行。

正是为了实现这种校验和，有两种算法：安全哈希算法1（SHA1）和消息摘要算法5（MD5）。它们生成这样的校验和（即哈希）。这两种算法与 DES/`crypt()` 所用算法的主要区别在于，字符串的 SHA1 或 MD5 校验和始终相同，因此验证数据非常容易。如图 1.2 所示，甚至 PHP 发行版也在其网站上标明了 MD5 校验和，用于验证下载文件的完整性。

![](img/2862989e5dc7f1b1d0bc64321737f084_28_0.png)

图 1.2 PHP 下载页面显示了 PHP 发行版的 MD5 哈希值。

同样，目标是验证用户通过 GET 提供的密码（如前所述，这是不好的做法，仅出于演示目的）。

正确的密码依旧是 `'TopSecret'`，其哈希值如下：

- `6958b43cb096e036f872d65d6a4dc01b` 是 MD5 哈希。

- `61c2feed11e0e53eb8e295ab8da78150be12f301` 是 SHA1 哈希。

从安全角度来看，你不应依赖 MD5（因为它可以用现代计算机破解）。鉴于硬件性能的进步，SHA1 也不再完全安全。你应该考虑额外的保护措施：

- 在对值进行哈希之前，先对它加盐——即添加一个已知的前缀字符串，使攻击者更难以破解。不过，这并不能抵御使用暴力破解并尝试几乎所有可能输入组合的攻击者。

- 将 `crypt()` 与更安全的算法（如 DES）一起使用。

### 提示：

在计算文件的 MD5 或 SHA1 哈希时，无需调用 `file_get_contents()` 或其他文件函数；PHP 提供了两个计算文件哈希的函数（并负责打开和读取文件数据）：

- `md5_file()`

- `sha1_file()`

### 提取子字符串

#### `substr()`

```
<?php
$php = "PHP: Hypertext Preprocessor";
echo substr($php, 15, 4); //returns "Prep"
?>
```

*使用 `substr()` 提取子字符串（substr.php；摘录）*

`substr()` 函数返回字符串的一部分。你提供一个字符串和要提取的第一个字符的位置（请记住，第一个字符的索引为0）。从该字符开始，返回字符串的其余部分。如果只想返回其中一部分，请在第三个参数中提供长度。前面的代码演示了 `substr()` 的用法，并从 `PHP: Hypertext Preprocessor` 中提取了 `Prep`。

**提示：** 如果要从字符串末尾开始计数，请将 `substr()` 的第二个参数设为负数：

```
echo substr($php, -12, 4);
```

如果为 `substr()` 的第三个参数提供负值（例如 `-n`），则最后 `n` 个字符不包含在子字符串中。

```
echo substr($php, -12, -8);
```

所有这些对 `substr()` 的调用都会返回 `Prep`，并且包含在完整代码中。

### 保护电子邮件地址

#### 使用ASCII码

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

echo '<a href="' .
    protectMail('email@address.xy') .
    '">Send mail</a>';
?>
```

*保护电子邮件地址（protectMail.php）*

在浏览器中，你只会看到一个电子邮件链接，但底层的 HTML 代码却难以辨认：

```html
<a
href="&#109;&#97;&#105;&#108;&#116;&#111;&#58;
&#101;&#109;&#97;&#105;&#108;&#64;&#97;&#100;&#100;&#114;
&#101;&#115;&#115;&#46;&#120;&#121;">Send
mail</a>
```

然而，请看图 1.3：Web 浏览器正确地解码了电子邮件地址，如状态栏所示。

![](img/2862989e5dc7f1b1d0bc64321737f084_32_0.png)

**图 1.3** 机器胜过人类（在解读电子邮件地址时）。

有些特殊字符在字符串中使用起来很困难，因为很难用键盘输入。但它们都有 ASCII 值。PHP 提供了两个函数来处理这个问题：

- `chr()` 将 ASCII 码转换为相应的字符。

- `ord()` 返回一个字符的 ASCII 码。

例如，这可用于保护电子邮件地址。由于垃圾邮件发送者会编写软件来搜索网页上的特定模式（电子邮件地址），因此这有助于减少垃圾邮件。诀窍是使用 HTML 字符代码来表示电子邮件地址，使垃圾邮件机器人更难找到电子邮件数据。

前面的代码将一个电子邮件地址（格式为 `email@address.xy`）作为参数，并返回 `mailto:email@address.xy`——但已转换为 HTML 实体。例如，`mailto:` 中的 `m` 的 ASCII

PHP 还支持与 `printf()` 相关的多个函数：

- `sprintf()` 与 `printf()` 工作方式类似，但返回字符串而不打印它。

- `vprintf()` 与 `printf()` 工作方式类似，但期望字符串中占位符的值以数组的形式提供。

- `vsprintf()` 是 `sprintf()` 和 `vprintf()` 的混合体：占位符值以数组形式提供，且函数返回字符串但不打印它。

### 扫描格式化字符串

```
sscanf($date, '%d/%d/%d')

<?php
$date = '02/01/06';
$values = sscanf($date, '%d/%d/%d');
vprintf('Month: %d; Day: %d; Year: %d.', $values);
?>
```

扫描格式化字符串 (sscanf.php)

与 `printf()` 相关的另一个函数是 `sscanf()`。它解析一个字符串并尝试将其与包含占位符的模式匹配。输入字符串包含一个日期，并使用字符串 `'%d/%d/%d'` 中的多个占位符进行扫描，如前文所示。该函数返回一个包含所有匹配占位符值的数组。然后将此数组传递给 `vprintf()` 以打印它。

另外，你可以向 `sscanf()` 提供变量名列表作为额外参数。然后函数会将与占位符匹配的子字符串写入这些变量。以下代码展示了这一点：

```php
<?php
$date = '02/01/06';
$values = sscanf($date, '%d/%d/%d', $m, $d, $y);
echo "Month: $m; Day: $d; Year: $y.";
?>
```

扫描格式化字符串 (sscanf-alternative.php)

### 获取变量的详细信息

```
var_dump(false);
```

变量的值可以使用 `print()` 或 `echo()` 发送给客户端；然而，有时这会存在问题。例如布尔值。`echo(true)` 打印 `1`，但 `echo(false)` 什么也不打印。更好的方法是使用 `var_dump()`，该函数还会打印变量的类型。因此，这段代码返回字符串 `bool(false)`。

这也适用于对象和数组，使得 `var_dump()` 成为喜欢在没有调试器的情况下调试的开发人员的必备选项。

NOTE: 与 `var_dump()` 相关的函数是 `var_export()`。它工作方式类似：然而，有两个区别：

- `var_export()` 的返回值是 PHP 代码：例如，`var_export(false)` 返回 `false`。

- 如果向 `var_export()` 提供的第二个参数是布尔值 `true`，函数不会打印任何内容，但会返回一个字符串。

### 在字符串中搜索

#### `strpos()`

```
if (!strpos($string, $substring)) {
    echo 'No match found.'
}
```

在字符串中查找子字符串时，使用 `strpos()`（及其对应函数 `strrpos()`，它从字符串末尾开始搜索）。这个函数棘手的地方在于它返回子字符串首次出现的索引，否则返回 `false`。这意味着前面的代码片段是不正确的。

前面的代码片段不正确，因为如果 `$string` 恰好以 `$substring` 开头，`strpos()` 返回 `0`，而 `0` 会被评估为 `false`。因此，必须使用 `===` 或 `!==` 进行比较以考虑数据类型。以下代码展示了如何正确使用 `strpos()`：

```
if (strpos($string, $substring) === false) {
    echo 'No match found.';
} else {
    echo 'Match found.';
}
```

### 理解正则表达式

正则表达式简单来说是可以与字符串匹配的模式。PHP 中有两种正则表达式：POSIX 正则表达式和 PHP 正则表达式。前者已弃用，因此我们只介绍后一种选项：Perl 兼容正则表达式（PCRE）。

PCRE 通常被认为更快，并且提供更多功能。此功能在 PHP 中默认启用；然而，如果你自行编译 PHP，可以使用开关 `--without-pcre-regex` 禁用 PCRE。

正则表达式中的模式包含可在更大字符串中搜索的字符串。然而，这也可以（更快地）使用 `strpos()` 完成。正则表达式的优势在于提供一些特殊功能，例如通配符。表 1.2 显示了一些特殊字符及其含义。

| Special Character | Description | Example |

| --- | --- | --- |

| `^` | 字符串的开头 | `^a` 表示以 `a` 开头的字符串。 |

| `$` | 字符串的结尾 | `a$` 表示以 `a` 结尾的字符串。 |

| `?` | 0 或 1 次（引用前一个字符或表达式） | `ab?` 表示 `a` 或 `ab`。 |

| `*` | 0 或多次（引用前一个字符或表达式） | `ab*` 表示 `a` 或 `ab` 或 `abb` 或 ... |

| `+` | 1 或多次（引用前一个字符或表达式） | `ab+` 表示 `ab` 或 `abb` 或 `abbb` 或 ... |

| `[...]` | 替代字符 | `PHP[45]` 表示 `PHP4` 或 `PHP5` |

| `-`（在方括号内使用） | 值序列 | `PHP[3-5]` 表示 `PHP3` 或 `PHP4` 或 `PHP5`。 |

| `^`（在方括号内使用） | 匹配除以下方括号字符外的任何内容 | `[^A-C]` 表示 `D` 或 `E` 或 `F` 或 ... |

| `\|` | 替代模式 | `PHP4\|PHP5` 表示 `PHP4` 或 `PHP5` |

| `(...)` | 定义子模式 | `(a)(b)` 表示 `ab`，但包含两个子模式（`a` 和 `b`）。 |

| `.` | 任意字符 | `.` 表示 `a`、`b`、`c`、`0`、`1`、`2`、`$`、`#`、... |

| `{min, max}` | 最小和最大出现次数；如果省略 `min` 或 `max`，则表示 `0` 或无限 | `a{1,3}` 表示 `a`、`aa` 或 `aaa`。`a{,3}` 表示空字符串、`a`、`aa` 或 `aaa`。`a{1,}` 表示 `a`、`aa`、`aaa`、... |

| `\` | 转义其后的字符 | `\.` 代表句点 (`.`) |

TIP: 正则表达式的事实标准参考是 Jeffrey E. F. Friedl 所著的标题 *精通正则表达式*——一本有趣的读物。

其他特殊字符和表达式也可用（例如，引用数字的字符，`\d`）。

### 使用 Perl 兼容正则表达式

`preg_match()`

```php
<?php
$string = 'This site runs on PHP ' . phpversion();
preg_match('/php ((\d)\.\d+\.\d+)/i',
    $string, $matches);
vprintf('Match: %s<br /> Version: %s; Major: %d.',
    $matches);
?>
```

使用 PCRE 在字符串中搜索 (preg_match.php)

在 PCRE 中匹配模式时，如果只搜索一个出现位置，使用 `preg_match()`，如果可能存在多个出现位置，则使用 `preg_match_all()`。语法如下：首先是模式，然后是字符串，然后是结果数组。然而，对于模式你需要分隔符；大多数时候使用斜杠。在分隔符之后，你可以提供进一步的指令。指令 `g` 允许全局搜索（用于多个匹配），而指令 `i` 则禁用大小写敏感。

函数 `preg_match_all()` 工作方式完全相同：然而，结果数组是多维的。该数组中的每个条目都是一个匹配数组，就像 `preg_match()` 返回的那样。以下代码展示了这一点：

```php
<?php
$string = 'This site runs on PHP ' . phpversion();
preg_match_all('/php ((\d)\.\d+\.\d+)/i',
    $string, $matches);
vprintf('Match: %s<br /> Version: %s, Major: %d. ',
    $matches);
?>
```

使用 PCRE 在字符串中查找多个匹配项 (preg_match_all.php)

### 使用正则表达式查找标签

`preg_match_all('/<.*?>/', $string, $matches);`

```php
<?php
$string = '<p>Sex, drugs and <b>PHP</b></p>';
preg_match_all('/<.*?>/', $string, $matches);
foreach ($matches[0] as $match) {
    echo htmlspecialchars("$match ");
}
?>
```

使用非贪婪 PCRE 查找所有标签 (non-greedy.php)

输出如下：

`<p> <b> </b> </p>`

PCRE 或 POSIX 的一个优势是支持一些特殊构造。例如，通常正则表达式是贪婪匹配的。例如，这个正则表达式：

`<.*>`

当尝试在以下字符串中匹配它时

`<p>Sex, drugs and <b>PHP</b>.</p>`

你会得到什么？你会得到完整的字符串。当然，模式也匹配 `<p>`，但正则表达式会尝试匹配尽可能多。因此，你通常必须做一些笨拙的变通方法，例如 `<[^>]*>`。然而，可以更轻松地完成。你可以在 `*` 量词后使用 `?` 修饰符来激活非贪婪匹配。

### 验证必填输入

```
function checkNotEmpty($s) {
  return (trim($s) != "");
}
```

在验证表单字段时（有关 HTML 表单的更多信息，请参阅第 4 章），可以进行多种检查。然而，你应该尽可能少地进行测试。例如，近期我尝试订购美国音乐会的门票时未能完成订单，因为表单期望提供美国电话号码，而我无法提供。

最好的检查是检查是否有任何输入。然而，什么被认为是任何输入？如果

如果某人只输入空白字符（即空格字符和其他非文本字符），表单字段是否填写正确？



最好的方法是在检查变量或表达式中是否有内容之前使用 `trim()`。函数 `trim()` 会移除所有类型的空白字符，包括空格字符、水平制表符、垂直制表符、回车符和换行符。如果之后该字符串不等于空字符串，则该（必填）字段已被填写。

注意：文件 `check.php` 包含示例调用，以及文件 `check.inc.php` 中所有后续对验证函数的调用。

### 验证数字（和其他数据类型）

要判断任何数据是否为数字（或能否转换为数字），PHP 提供了几种可能性。首先，以下辅助函数会检查变量的数据类型：

- `is_array()` — 检查是否为数组
- `is_bool()` — 检查是否为布尔值
- `is_float()` — 检查是否为浮点数
- `is_int()` — 检查是否为整数
- `is_null()` — 检查是否为 null
- `is_numeric()` — 检查是否为整数和浮点数
- `is_object()` — 检查是否为对象
- `is_string()` — 检查是否为字符串

然而，需要注意的是，数字函数——`is_float()`、`is_int()` 和 `is_numeric()`——也会尝试将数据从原始类型转换为数字类型。

另一种转换数据类型的方法借鉴自 Java 和其他强类型的类 C 语言。在变量或表达式前面加上括号括起来的所需数据类型：

```php
$numericVar = (int)$originalVar;
```

然而，在这种情况下，PHP 会不惜一切代价进行转换。因此，`(int)'3DoorsDown'` 返回 3，而 `is_numeric('3DoorsDown')` 返回 false。相比之下，`(int)'ThreeDoorsDown'` 返回 0。

通常，`is_numeric()`（以及 `is_int()`/`is_float()`）似乎是更好的选择，而 `(int)` 即使对于非法输入也会返回整数值。因此，选择哪种方法实际上取决于当前的具体应用。

以下代码两全其美。使用 `is_numeric()` 检查给定输入是否为数字，如果是，则使用 `(int)` 将其转换为整数。要支持其他（数字）数据类型的调整非常简单：

```php
function getIntValue($s) {
    if (!is_numeric($s)) {
        return false;
    } else {
        return (int)$s;
    }
}
```

生成整数值（`check.inc.php`；摘录）

### 验证电子邮件地址

```php
function checkEmail($s) {
    $lastDot = strrpos($s, '.');
    $ampersat = strrpos($s, '@');
    $length = strlen($s);
    return !(
        $lastDot === false ||
        $ampersat === false ||
        $length === false ||
        $lastDot - $ampersat < 3 ||
        $length - $lastDot < 3
    );
}
```

验证电子邮件地址（`check.inc.php`；摘录）

检查字符串是否包含有效的电子邮件地址同时具有两个特点：非常常见且非常复杂。前面提到的关于正则表达式的书用了好几页来创建一组正则表达式来执行此任务。如果你对此感兴趣，可以看看 `http://examples.oreilly.com/regex/readme.html`。

验证电子邮件地址很困难，因为有效域名的规则在不同国家之间差异很大。例如，`bn.com` 是有效的，而 `bn.de` 无效（但 `db.de` 有效）。另外，你知道吗，`user-name@[127.0.0.1]` 是一个有效的电子邮件地址（如果 `127.0.0.1` 是邮件服务器的 IP 地址）？

因此，建议只检查电子邮件地址的主要元素：有效字符（一个 `@` 字符）以及其后某处的点号。要 100% 确定地检查电子邮件地址是不可能的；如果测试过于严格，用户只会提供一个虚构的电子邮件地址。电子邮件检查的唯一目的是在（非故意的）拼写错误发生时提供帮助。

当然，使用正则表达式也可以实现这一点，但这可能只是更慢。你还应该注意，前述代码无法检测出每一个不正确的电子邮件地址。还要留意包含特殊字符（如 `à` 或 `é`）的新国际域名。大多数正则表达式会忽略这些字符，因此使用前面的代码会好得多。

### 搜索与替换

#### `preg_replace()`

```php
<?php
$string = '02/01/13';
echo preg_replace(
    '#(\d{1,2})/(\d{1,2})/(\d{1,2})#',
    '$2/$1/$3',
    $string
);
?>
```

*使用 PCRE 替换匹配项（`preg_replace.php`）*

在字符串中搜索是一回事；将所有匹配项替换为其他内容则完全不同。不过，使用正则表达式时这相对容易；你只需要知道函数名：`preg_replace()`

在替换项的正则表达式中，你可以使用对子模式的引用。完整匹配由 `$0` 引用。然后从内到外、从左到右数括号：第一个括号的内容由 `$1` 引用，第二个括号使用 `$2` 访问，依此类推。

了解了这一点，就可以进行替换了。在示例中，美式日期（月/日/年）被转换为英式日期（日/月/年）。

提示：前面代码中的正则表达式没有使用 `/` 作为正则表达式的分隔符，因为正则表达式本身包含斜杠，如果使用 `/` 就需要进行转义。但是，通过选择其他分隔符（例如 `#`），你可以避免转义斜杠。

如果你有一个静态模式，没有任何量词或特殊字符，使用 `str_replace()` 几乎总是更快。它的参数顺序是：首先是搜索的字符串；然后是替换内容；最后是进行搜索和替换的字符串。前两个参数可以传入字符串或字符串数组。以下代码从文本中移除所有标点符号：

```php
<?php
$string = 'To be, or not to be; that\'s the question?!';
echo str_replace(
    array('.', ',', ':', ';', '!', '?'),
    '',
    $string
);
?>
```

*不使用正则表达式进行替换（`str_replace.php`）*

以下代码展示了如何使用包含替换字符的数组。

```php
<?php
$string = '<p>This is <span class="acronym">HTML</span></p>';
echo str_replace(
    array('<', '>', '"', "'", '&'),
    array('&lt;', '&gt;', '&quot;', '&apos;',
    '&amp;'),
    $string
);
?>
```

*不使用正则表达式进行替换（`str_replace_multiple.php`）*

## 使用数组

当简单变量不够用时，数组就开始发挥作用（或者对象，但那是另一个话题）。PHP 手册中的数组部分（可在 `http://php.net/array` 获取）列出了大约 80 个有用的函数。因此，仅数组相关的短语就足以写满这本书。然而，并非所有这些函数都真的经常使用。因此，本章介绍了在使用数组时必须解决的最重要的问题——当然，还有这些问题的解决方案。

数组有两种类型。它们的名称有时有所不同，但通常数组被区分为数字数组和关联数组。第一种类型的数组使用数字键，而后一种类型也可以使用字符串作为键。

创建数组可以通过以下三种方式之一完成：

- 使用 `array()` 语句

```php
$a = array('I', 'II', 'III', 'IV');
```

- 使用变量名和方括号依次向数组添加值

```php
$a[] = 'I';
$a[] = 'II';
$a[] = 'III';
$a[] = 'IV';
```

- 使用 PHP 5.4 中引入的新的方括号语法

```php
$a = ['I', 'II', 'III', 'IV'];
```

对于 Web 开发人员来说，后一种方法可能是最直观的，因为 JavaScript 具有非常相似的语法。为了向后兼容，我们仍将在本章中使用第一种方法。

使用关联数组时，可以使用同样的三种方法；但这一次必须提供键和值：

```php
$a1 = array('one' => 'I', 'two' => 'II', 'three' =>
'III', 'four' => 'IV');
$a2['one'] = 'I';
$a2['two'] = 'II';
$a2['three'] = 'III';
$a2['four'] = 'IV';
```

```php
$a1 = ['one' => 'I', 'two' => 'II', 'three' =>
'III', 'four' => 'IV'];
```

当数组元素本身也是一个数组时，也可能需要数组：

```php
$a = array(
    'Roman' =>
        array('one' => 'I', 'two' => 'II', 'three' =>
        'III', 'four' => 'IV'),
    'Arabic' =>
        array('one' => '1', 'two' => '2', 'three' =>
        '3', 'four' => '4')
);
```

现在，数字四的阿拉伯表示可以通过 `$a['Arabic']['four']` 来访问。

当然，数组不仅可以在脚本中创建，还可以来自其他来源，包括 HTML 表单（参见第 5 章“与 Web 表单交互”）以及 Cookie 和会话（参见第 6 章“记住用户（Cookie 和会话）”）。但是，如果数组已经存在，下一步该做什么？以下内容提供了一些指导。

### 访问数值数组的所有元素

#### `foreach`（`$a as $element`）

```php
<?php
$a = array('I', 'II', 'III', 'IV');
foreach ($a as $element) {
    echo htmlspecialchars($element) . '<br />';
}
?>
```

*使用 `foreach` 遍历数组（`foreach-n.php`）*

遍历数值（或索引）数组最简便的方法是使用 `foreach`，因为在每个

当然，这三个代码清单的输出总是相同的。

### 访问关联数组的所有元素

```php
foreach ($a as $key => $value)
```

```php
<?php
  $a = array('one' => 'I', 'two' => 'II', 'three' =>
    'III', 'four' => 'IV');
  foreach ($a as $key => $value) {
    echo htmlspecialchars("$key: $value") . '<br
/>';
  }
?>
```

*使用 `foreach` 遍历关联数组*

*(`foreach-a.php`)*

当使用关联数组并希望访问其中的所有数据时，键也具有相关性。为此，`foreach` 循环不仅可以为元素的值提供变量名，还可以为元素的键提供变量名。

可以使用 `count()`：`count()` 返回数组中的值的数量，而不是元素的数量。使用 `for` 遍历所有数组元素是不可行的。但是，可以使用 `each()` 和 `while` 的组合，如下面的代码所示。重要的一点是，键名可以通过索引 `0` 或字符串索引 `'key'` 来获取：

```php
<?php
$a = array('one' => 'I', 'two' => 'II', 'three' =>
'III', 'four' => 'IV');
while ($element = each($a)) {
    echo htmlentities($element['key'].' - ' .
$element['value']) . '<br />';
    //or: $element[0] / $element[1]
}
?>
```

*使用 `each` 遍历关联数组（`each-a.php`）*

### 访问嵌套数组中的所有数组元素

```php
print_r($a)
```

```html
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

*使用 `print_r` 打印嵌套数组（`print_r.php`）*

使用 `print_r()` 可以非常容易地打印嵌套数组。看一下图 2.1 中代码清单的输出。

![](img/2862989e5dc7f1b1d0bc64321737f084_56_0.png)

图 2.1 使用 `print_r()` 打印数组内容

**提示：** 如果将 `print_r()` 的第二个参数设置为 `true`，关联数组的内容将不会发送到客户端，而是从函数返回，这样你就可以将这些信息保存在变量中并进行进一步处理。

然而，上述代码（见图 2.1）的输出除了用于调试之外几乎没什么用处。因此，必须找到一种巧妙的方法来访问所有数据。递归函数是实现这一目标的合理方式。在这种方法中，数组的所有元素都会被打印出来；整个输出使用 HTML 元素 `<blockquote>` 缩进。但是，如果数组元素的值本身是一个数组，函数就会递归调用自身，从而增加一层缩进。

是否某个东西是数组，可以使用 PHP 函数 `is_array()` 来判断。利用这一点，可以编写如下代码；结果见图 2.2：

```php
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

*使用递归函数打印嵌套数组*

*(`printNestedArray.php`)*

![](img/2862989e5dc7f1b1d0bc64321737f084_58_0.png)

**图 2.2** 使用递归函数打印数组内容

### 将数组转换为变量

```php
<?php
$a = array('one' => 'I', 'two' => 'II', 'three' =>
'III', 'four' => 'IV');
while (list($key, $value) = each($a)) {
    echo htmlspecialchars("$key: $value") . '<br />';
}
?>
```

*使用 `list()` 和 `each()` 遍历数组*

*(`each-list.php`)*

只要使用 `each()`，最好配合 `list()`。在 `list()` 中，为 `each()` 返回的数组中所有带数值索引的值提供变量名。这使得 `while/each()` 循环更容易使用，如代码所示。在括号内，提供了变量名。

**提示：** 如果你只对数组的键或值感兴趣，可以删除两个变量中的一个：只需确保保留逗号。

```php
while (list(, $value) = each($a)) {
    echo htmlspecialchars("$value") . '<br />';
}
```

### 将字符串转换为数组

```php
$a = explode(',', $csvdata);
```

```php
<?php
$csvdata = 'Pearson Education,800 East 96th Street,Indianapolis,Indiana,46240';
$a = explode(',', $csvdata);
$info = print_r($a, true);
echo "<pre>$info</pre>";
?>
```

*将字符串转换为数组（`explode.php`）*

有时，我们不用数组存储信息，而是使用字符串。各个值都在字符串内，但由特殊字符分隔。一个例子就是逗号分隔值（CSV）格式。

PHP 函数 `explode()` 会从这些值中创建一个数组；你只需提供字符串需要拆分的位置的字符。浏览器随后会显示如下输出：

```text
Array
(
  [0] => Pearson Education
  [1] => 800 East 96th Street
  [2] => Indianapolis
  [3] => Indiana
  [4] => 46240
)
```

### 将数组转换为字符串

```php
$address = implode('<br />', $data);
```



```php
<?php
$data = array(
  'Pearson Education',
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

反向操作（即从数组元素生成字符串表示）可以使用 `implode()` 完成。同样，需要两个参数：先是分隔符元素，然后是数组。这个顺序相当不寻常，但很重要。

于是，PHP 使用 `<br />` HTML 元素连接数组的元素。因此，在浏览器中，数组的每个元素都单独占一行。

### 按字母顺序对数组排序

```php
sort($a, SORT_NUMERIC);
sort($a, SORT_STRING);
```

```html
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

*对数组进行排序 (sort.php)*

数值数组使用 `sort()` 可以很容易地进行排序。然而，如果数组同时包含数值和字符串值（例如，"2" > "10" 但 2 < 10），就会出现问题。因此，可以调整排序方式，以便在排序时使用特殊的数据类型来比较元素：

- `SORT_NUMERIC` 将元素作为数字排序。

- `SORT_REGULAR` 根据元素的数据类型排序（默认行为）。

- `SORT_STRING` 将元素作为字符串排序。

以下是上述代码清单的输出：

```text
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

**注意：** 如果要按相反顺序对数组元素排序，请使用 `rsort()`（r 表示 reverse，反向）。允许使用与 `sort()` 相同的可选第二参数。

### 按字母顺序对关联数组排序

```php
ksort($a);
asort($a);
```

```html
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

### 对嵌套数组排序

```
function sortNestedArray(&$sa) {
 sort($sa);
 for ($i = 0; $i < count($sa); $i++) {
 if (is_array($sa[$i])) {
 sortNestedArray($sa[$i]);
 }
 }
}
```

<pre>

<?php

function sortNestedArray(&$sa) {

 sort($sa);

 for ($i = 0; $i < count($sa); $i++) {

 if (is_array($sa[$i])) {

 sortNestedArray($sa[$i]);

 }

 }

}

$arr = array(

 'French',

 'Spanish',

 array('British English', 'American English'),

 'Portuguese',

 array('Schwitzerdütsch', 'Deutsch'),

 'Italian'

);

sortNestedArray($arr);

print_r($arr);

?>

</pre>

使用递归函数对嵌套数组排序

（sortNestedArray.php）

PHP 的标准排序函数在执行操作时不会遍历嵌套数组。但是，如果使用递归函数，只需几行代码就可以实现。

目标是排序一个嵌套数组，该数组只包含数字索引子数组，因此只使用数字（也就是无意义）键。

思路如下：调用 `sort()` 确实会对数组排序，但会跳过所有子数组。因此，对于所有元素是数组的情况，需要递归地再次调用排序函数。前面的代码展示了这一概念；图 2.4 显示了一个示例数组的排序结果。

![](img/2862989e5dc7f1b1d0bc64321737f084_65_0.png)

**图 2.4** 对嵌套数组排序

> **注意：** PHP 函数 `array_multisort()` 是另一种对多维数组排序的方法。

### 对嵌套关联数组排序

```php
foreach ($a as $key => $value) {
    if (is_array($value)) {
        sortNestedArrayAssoc($value);
    }
}
```

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

*使用递归函数对关联嵌套数组排序（sortNestedArrayAssoc.php）*

如果要对关联嵌套数组排序，与之前对数字（但嵌套）数组排序的片段相比，需要改变两处。首先，必须使用 `ksort()`，而不是 `sort()` 对数组排序。其次，递归排序必须应用于正确的变量，即本身是数组的那个数组元素。确保通过引用传递该变量，以便更改能反映回原值：

```php
foreach ($a as $key => &$value) {
    if (is_array($value)) {
        sortNestedArrayAssoc($value);
    }
}
```

图 2.5 显示了本片段开头代码的结果。

![](img/2862989e5dc7f1b1d0bc64321737f084_67_0.png)

图 2.5 对嵌套关联数组排序

### 对 IP 地址排序（像人类一样）

`natsort($a);`

```php
<?php
$a = array('100.200.300.400', '100.50.60.70',
    '100.8.9.0');
natsort($a);
echo implode(' ', $a);
?>
```

使用自然字符串顺序比较对 IP 地址排序（natsort.php）

使用 `sort()` 对 IP 地址排序实际上并不奏效，因为如果按字符串排序，'100.200.300.400'（它故意是一个无效的 IP）会小于 '50.60.70.80'。此外，字符串中不仅包含数字，因此按数字排序也行不通。

这种情况需要一种所谓的自然排序，它由 Martin Pool 的 Natural Order String Comparison 项目实现，项目地址是 http://sourcefrog.net/projects/natsort/。PHP 的 `natscasesort()` 函数就使用了该算法。根据其描述，它会像人类排序一样。当需要考虑大小写时，可以使用 `natsort()`。前面的代码展示了后者。

**注意：** 在内部，`natsort()` 使用 `strnatcmp()`（而 `natscasesort()` 使用 `strnatcasecmp()`），它们会对两个字符串进行“自然”比较。通过多次调用此函数，数组元素会被排列到正确的顺序。

### 对任意内容排序

```php
<?php
function compare($a, $b) {
    return $a - $b;
}

$a = array(4, 1345, 31, 222);
usort($a, 'compare');
echo implode(' < ', $a);
?>
```

如果你不想局限于 PHP 提供的标准排序功能，可以编写自己的排序算法。在内部，PHP 使用快速排序算法对数组中的值进行排序。要使其工作，PHP 必须知道两个值是否相等；在后一种情况下，PHP 需要找出哪个值更大。因此，要实现自定义排序，只需一个接受两个参数并返回以下结果的函数：

- 如果第一个参数小于第二个参数，则返回负值

- 如果两个参数相等，则返回 0

- 如果第二个参数小于第一个参数，则返回正值

该函数的名称必须作为字符串传递给 `usort()`；或者，如果你使用 PHP 5.3 或更高版本，也可以使用类似于 JavaScript 的匿名函数。其余工作由 PHP 完成，如代码所示。其中使用的比较函数是一种非常简单的数值排序方式。通过将两个值相减，该函数返回所需的结果：如果第一个参数大于第二个参数，则返回正数；如果两个参数相等，则返回 0；否则返回负数。

### 使用外语排序

```php
<?php
function compare($a, $b) {
    if ($a == $b) {
        return 0;
    } else {
        for ($i = 0; $i < min(strlen($a), strlen($b));
            $i++) {
            $cmp = compareChar(substr($a, $i, 1),
                substr($b, $i, 1));
            if ($cmp != 0) {
                return $cmp;
            }
        }
        return (strlen($a) > strlen($b) ? 1 : 0);
    }
}

function compareChar($a, $b) {
    // ...
}

$a = array('Frédéric', 'Froni', 'Frans');
usort($a, 'compare');
echo implode(' < ', $a);
?>
```

对包含特定语言字符的数组排序

（languagesort.php；摘录）

只要只涉及标准 ASCII 字符，排序效果就很好。然而，一旦特殊语言字符出现，排序就会产生不理想的效果。例如，对数组 `['Frans', 'Frédéric', 'Froni']` 调用 `sort()` 会将 `'Frédéric'` 排在最后，因为 `é` 字符的字符代码比 `o` 大得多。

对于这种特殊情况，PHP 没有提供专门的排序方法；不过，你可以使用 `strnatcmp()` 来模拟这一行为。思路是为某些特殊字符定义一个新的顺序；然后在比较函数中使用这个顺序来判断哪个字符“更大”、哪个“更小”。

你首先需要一个能对单个字符进行排序的函数：

```
function compareChar($a, $b) {
    $characters = 'ÁÁÁBCÇDÉÉFGHIIĴKLMNOÓÓPQRSTUÚÚVWXZ';
    $characters .= 'ááábççdeééfghiiĵjklmnoóóopqrstuúúvwxyz';
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

然后，主排序函数逐字符调用 `compareChar()`，直到发现差异为止。如果没有发现差异，则较长的字符串被认为是“更大”的。如果两个字符串完全相同，则返回 0。本片段开头的代码展示了比较函数。该代码的结果正如期望：Frans < Frédéric < Froni。

从 PHP 5.3 开始，ext/intl 扩展也提供了自然语言排序机制。如果安装了该扩展（可能还需要来自 http://site.icu-project.org/ 的 ICU 库集），你首先需要创建一个所谓的排序器（collator），它需要一个区域设置（例如 `en_US`、`en_CA`、`en_GB`、`fr_FR` 或 `de_AT`）。然后，你可以调用 `sort()` 和 `asort()` 方法，它们与 PHP 对应的函数类似，但会考虑区域设置信息：

```php
$a = array('Frédéric', 'Froni', 'Frans');
$coll = new Collator('fr_FR');
$coll->sort($a);
echo implode(' ', $a);
```

使用区域设置信息对数组排序（collator.php）

### 对所有数组元素应用效果

```php
$a = array_map('sanitize', $a);
```

```php
<?php
function sanitize($s) {
    return htmlspecialchars($s);
}

$a = array('harmless', '<bad>', '>>click here<<');
$a = array_map('sanitize', $a);
echo implode(' ', $a);
?>
```

对数组的所有元素应用 `htmlspecialchars()`（array_map.php）

有时，数组中的数据在使用前必须进行预处理。在第 4 章中，你将看到如何对来自用户 HTML 表单的数据在使用前进行清理。为此，必须处理到每一个数组元素。

不过，你并不需要编写繁琐的 `for`/`foreach`/`while` 循环；PHP 为此提供了内置功能。第一种方式是使用 `array_map()`。它接受一个数组（第二个参数），并将该数组中的每个元素提交给回调函数（第一个参数，可以是字符串、数组或匿名函数，如下所示）。最后返回处理后的数组，其中所有元素都被替换为回调函数关联的返回值。

在上面的代码中，数组中的所有值都通过 `htmlspecialchars()` 转换为 HTML 实体。

**注意：** 从 PHP 5.3 开始，只要 PHP 函数需要回调，你就可以使用内联匿名函数。因此，前面的代码可以稍微整理成如下形式：

```php
<?php
$a = array('harmless', '<bad>', '>>click here!<<');
$a = array_map(
    function ($s) {
        return htmlspecialchars($s);
    },
    $a);
echo implode(' ', $a);
?>
```

*使用匿名函数对数组的所有元素应用 `htmlspecialchars()`（array_map_anon.php）*

不过，如果数组是嵌套数组，策略就需要稍作改变。这时你可以使用递归函数。如果数组元素是字符串，则进行 HTML 编码；如果是数组，则递归函数对自身调用该数组。以下代码实现了这一点，图 2.6 显示了结果：

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
        array('<bad>', '-> <worse> <--')
);

$a = sanitize_recursive($a);
echo '<pre>' . print_r($a, true) . '</pre>';
?>
```

*递归地对嵌套数组的所有元素应用 `htmlspecialchars()`（array_map_recursive.php）*

![](img/2862989e5dc7f1b1d0bc64321737f084_75_0.png)

图 2.6 嵌套数组已被 HTML 编码。

另一个行为类似的函数是 `array_walk()`。它同样会将一个函数应用到数组的每个元素上；不过，它还允许你为这个函数调用提供一个参数。在下面的代码中，这用于打印数组的所有元素。这里传递了一个参数——计数器。由于它是通过引用传递的，在函数内将该计数器加一，就会得到一列序号：



```php
<?php
function printElement($s, &$i) {
    printf('%s: %s<br />', $i,
    htmlspecialchars($s));
    $i++;
}

$i = 0;
$a = array('one', 'two', 'three', 'four');
array_walk($a, 'printElement', $i);
?>
```

*使用 `array_walk()` 和按引用传递的计数器打印数组元素（array_walk.php）*

运行上述代码会显示以下结果：

```text
0: one
1: two
2: three
3: four
```

### 过滤数组

`array_filter($values, 'checkMail')`

```php
<?php
function checkMail($s) {
    // ...
}

$values = array(
    'valid@email.tld',
    'invalid@email',
    'also@i.nvalid',
    'also@val.id'
);
echo implode(', ', array_filter($values, 'checkMail'));
?>
```

*过滤有效的电子邮件地址（array_filter.php）*

假设你从 HTML 表单、文件或数据库中获得了一堆值，并且想要筛选出哪些值实际上可用、哪些不可用。你可以再次使用 `for`、`foreach` 或 `while` 循环来找出感兴趣的值，也可以让 PHP 替你完成大部分工作。在后一种情况下，你需要熟悉 `array_filter()` 函数。它接受两个参数：第一个是要过滤的数组；第二个是函数名（以字符串形式），用于检查数组元素是否合格。该验证函数在成功时返回 `true`，否则返回 `false`。以下是一个非常简单的电子邮件地址验证函数；关于更好的实现，请参阅第 1 章“操作字符串”：

```php
function checkMail($s) {
  $ampersand = strpos($s, '@');
  $lastDot = strrpos($s, '.');
  return ($ampersand !== false &&
          $lastDot !== false &&
          $lastDot - $ampersand >= 3);
}
```

现在，本节开头的代码调用 `array_filter()`，这样只会留下（语法上）有效的电子邮件地址。

正如你所预期的，该代码只会打印出两个有效的电子邮件地址。

### 从数组中随机获取元素

`array_rand($numbers, 6)`

```php
<?php
for ($i = 1; $i <= 49; $i++) {
    $numbers[] = $i;
}
// we could use range() instead, too

echo implode(' ', array_rand($numbers, 6));
?>
```

*从数组中随机挑选元素（array_rand.php）*

使用 `array_rand()`，可以从数组中随机抽取一个或多个元素。例如，这可以用来抽取幸运数字。比如，德国彩票从 49 个数字中抽取 6 个。前面的代码使用 PHP 和 `array_rand()` 实现了这种抽奖；输出如图 2.7 所示。该函数的第一个参数是数组；第二个（可选）参数是要返回的元素个数。

**注意：** 如果你不想随机挑选元素，而是想随机打乱数组中的元素顺序（例如洗牌时），请使用 `shuffle()` 函数。

![](img/2862989e5dc7f1b1d0bc64321737f084_79_0.png)

图 2.7 使用 PHP 生成幸运数字

### 让对象表现得像数组

`class MyArray implements ArrayAccess, Countable`

```php
<?php
class MyArray implements ArrayAccess, Countable {
    private $_data = array();

    /* ArrayAccess interface */
    public function offsetSet($offset, $value) {
        $this->_data[$offset] = $value;
    }

    public function offsetExists($offset) {
        return isset($this->_data[$offset]);
    }

    public function offsetUnset($offset) {
        unset($this->_data[$offset]);
    }

    public function offsetGet($offset) {
        //return (isset($this->_data[$offset])) ?
        //    $this->_data[$offset] : null;
        return ($this->offsetExists($offset)) ?
            $this->_data[$offset] : null;
    }

    /* Countable Interface */
    public function count() {
        return count($this->_data);
    }
}

$a = new MyArray();
$a[0] = 'I';
$a[1] = 'II';
$a[2] = 'III';
$a[3] = 'IV';
for ($i = 0; $i < count($a); $i++) {
    printf('<p>%s</p>', htmlspecialchars($a[$i]));
}
?>
```

*使用 SPL 将对象当作数组使用（splArray.php）*

SPL（标准 PHP 库）是 PHP 中最被低估的特性之一。它基本上提供了一整套接口。如果你创建的类实现了其中一个接口，就可以在类中使用标准的 PHP 函数。http://php.net/spl 上的文档并不总是像你期望的那样详细，但它确实为你提供了一些很好的指引，告诉你有哪些可能性。

作为简单示例，我们将创建一个类（关于面向对象编程（OOP）的更多内容，请参阅第 4 章），该类实现两个接口：

- `ArrayAccess`——允许访问对象集合中的各个元素（在我们的代码中是一个简单数组）

- `Countable`——允许在对象实例上调用 `count()`

如果需要完整的数组支持，你还需要实现其他接口，包括 `Iterable`（用于迭代器支持；例如通过 `foreach`）等等。`ArrayObject` 接口聚合了几个必需的接口，这些接口甚至可以实现用户自定义排序等高级功能。

## 表 3.1 `date()` 的格式化符号

| 符号 | 描述 |

| --- | --- |

| `a` | am 或 pm |

| `A` | AM 或 PM |

| `B` | Swatch 互联网时间（000 到 999 之间） |

| `c` | ISO 8601 格式的日期 |

| `d` | 月份中的第几天（01 到 31） |

| `D` | 星期几（Mon 到 Sun） |

| `F` | 月份（January 到 December） |

| `g` | 小时（1 到 12） |

| `G` | 小时（0 到 23） |

| `h` | 小时（01 到 12） |

| `H` | 小时（00 到 23） |

| `i` | 分钟（00 到 59） |

| `I` | 日期是否处于夏令时（1）或不是（0） |

| `j` | 月份中的第几天（1 到 31） |

| `l` | 星期几（Sunday 到 Saturday） |

| `L` | 是否为闰年（1）或不是（0） |

| `m` | 月份（01 到 12） |

| `M` | 月份（Jan 到 Dec） |

| `n` | 月份（1 到 12） |

| `O` | 与 GMT 的差值（例如，+0100 表示提前 1 小时） |

| `r` | RFC 2822 格式的日期 |

| `s` | 秒（00 到 59） |

| `S` | 月份中第几天的序数后缀（st、nd、rd、th） |

| `t` | 给定月份的天数（28 到 31） |

| 符号 | 说明 |

|---|---|

| `T` | 服务器时区（例如 CET） |

| `U` | 纪元值（自 1970 年 1 月 1 日 GMT 午夜以来的秒数） |

| `w` | 星期几（从 0 [星期日] 到 6 [星期六]） |

| `W` | 周数（根据 ISO 8601，从 1 到 53） |

| `y` | 年份（2 位） |

| `Y` | 年份（4 位） |

| `z` | 年中日期（从 0 到 365） |

| `Z` | 与 UTC 的时区差（秒） |

**注意：** 表 3.1 中显示的所有格式化符号几乎都自 PHP 3 起可用。只有两个例外：使用 `w` 确定日期的周数是在 PHP 4.1.0 中添加的，而使用 `c` 获取日期（例如 2006-06-30T12:34:56+01:00）的 ISO 8601 表示法是在 PHP 5 中出现的。

`date()` 函数非常强大，提供了多种使用方式。然而，特别是当你有本地化内容时，你需要一些好的短语。在本章中，你将找到许多这样的短语。

PHP 中较新的日期和时间处理方式使用了 `DateTime` 等类。在本章选定的短语中，我们也会使用这个类及一些相关的类。

PHP 的日期和时间功能在 PHP 手册中有自己的一节。你可以在 http://php.net/datetime 找到关于 `DateTime` 及其相关功能的更多信息。

### 在 `date()` 中使用文本

```php
<?php
echo date('\\Tod\\ay \\i\\s t\\he jS \\d\\ay of F');
?>
```

假设你想输出当前日期（或特定日期）并在其中使用自定义字符串。如果你尝试像这样编写代码，代码可能会看起来很混乱：

```php
<?php
echo 'Today is the ' . date('jS') . ' day of the
month ' . date('F');
?>
```

此脚本的输出类似于这样，具体取决于当前日期：

```text
Today is the 3rd day of the month May
```

`date()` 的行为如下：第一个参数中所有具有特殊含义的字符（例如格式化符号）都会被替换为相应的值。然而，所有其他字符保持不变。如果字符使用反斜杠字符（`\\`）进行转义，则它会按原样返回。因此，本短语开头的代码展示了仅调用一次 `date()` 的新版本代码。

**注意：** 如果你使用双引号而不是单引号，那么在 `date()` 中转义某些字符时可能会遇到麻烦。在前面的示例中，转义 `n` 将使用 `\n`，在双引号内它会被替换为换行符。

### 格式化 DateTime 对象

PHP 5.2 中引入的新的日期和时间处理方法使用 `DateTime` 类来表示日期值。创建类实例的方法有很多种，但最方便的可能是以给定格式提供日期，并反过来告诉 PHP 你使用的是哪种格式。格式化符号是表 3.1 中的那些。以下是一个示例：

```php
$d = DateTime::createFromFormat('d.m.Y', '21.11.2012');
```

变量 `$d` 现在持有一个表示 2012 年 11 月 21 日的日期。

在获得这样的日期并使用它（参见本章中的其他一些短语）之后，我们可以使用与之前相同的格式化字符以及 `format()` 方法将日期格式化为字符串：

```php
echo $d->format('Y-m-d');
```

**注意：** 除了面向对象编程（OOP）应用程序编程接口（API）之外，PHP 的 `DateTime` 功能也可以通过过程化接口使用。前面的代码行也可以写成这样——尽管在本章中我们更倾向于 OOP 语法：

```php
$d = date_create_from_format('d.m.Y', '10.11.2012');
echo date_format($d, 'Y-m-d');
```

### 自动本地化日期

```php
<?php
setlocale(LC_TIME, 'en_US');
echo strftime('In (American) English: %c<br />');
setlocale(LC_TIME, 'en_GB');
```

| 符号 | 说明 |

|---|---|

| `%j` | 年中日期（从 001 到 366） |

| `%m` | 月份（从 01 到 12） |

| `%M` | 分钟（从 00 到 59） |

| `%n` | 换行符（`\n`） |

| `%p` | am 或 pm（或本地等效值） |

| `%r` | 使用 a.m./p.m. 记法的时间 |

| `%R` | 使用 24 小时记法的时间 |

| `%S` | 秒（从 00 到 59） |

| `%t` | 制表符（`\t`） |

| `%T` | 格式为 hh:ss:mm 的时间 |

| `%u` | 星期几（从 1 [星期一] 到 7 [星期日]） |

| `%U` | 周数（规则：第一个星期日是第一个星期的第一天。） |

| `%V` | 周数（规则：一年中至少有 4 天的第一个星期计为第 1 周。） |

| `%w` | 星期几（从 0 [星期日] 到 6 [星期六]） |

| `%W` | 周数（规则：第一个星期一是第一个星期的第一天。） |

| `%x` | 标准格式的日期（不含时间） |

| `%X` | 标准格式的时间（不含日期） |

| `%y` | 年份（2 位） |

| `%Y` | 年份（4 位） |

| `%z` 或 `%Z` | 时区 |

只要表 3.2 中提到*标准格式*，格式化符号就会根据本地设置被替换为相应的值。前面的代码使用 `setlocale()` 多次更改区域设置，然后调用 `strftime()`。注意图 3.1 中显示的区别。再看一下图 3.2，其中同一个脚本在 Windows 机器上执行。根据文档，`strftime()` 的大部分功能在 Windows 上也能使用，但在某些配置上更改区域设置似乎不起作用。因此，首先测试系统是否支持本地化日期非常重要。

![](img/2862989e5dc7f1b1d0bc64321737f084_89_0.png)

图 3.1 不同区域设置下的当前日期

![](img/2862989e5dc7f1b1d0bc64321737f084_89_1.png)

图 3.2 此特定系统似乎不支持区域设置

### 手动本地化日期

```php
<?php
$weekdays = array(
    'domingo', 'lunes', 'martes', 'miércoles',
    'jueves', 'viernes', 'sábado'
);
$months = array(
    'enero', 'febrero', 'marzo', 'abril',
    'mayo', 'junio', 'julio', 'agosto',
    'septiembre', 'octubre', 'noviembre', 'diciembre'
);
$weekday = date('w');
$month = date('n');
echo $weekdays[$weekday] . date(', j ') .
    $months[$month - 1] . date(' Y');
?>
```

如果你不能依赖 `setlocale()`，但又想使用本地化的日期和时间值，你必须自己进行翻译并将结果存储在数组中。然后你可以使用 `date()` 检索有关日期的信息。这作为你数组的索引。

前面的代码对月中的日期和月份本身都执行了此操作。一个数组包含西班牙语的星期几；另一个数组包含月份名称。

请注意，月份的值减一，因为 `$months` 数组在位置 0 处没有虚拟元素；因此，一月（月份一）的索引为 0。

### 使用当前日期：美国/英国/欧洲方式

```php
<?php
    echo 'US format: ' . date('m/d/Y<br />');
    echo 'UK format: ' . date('d/m/Y<br />');
    echo 'German format: ' . date('d.m.Y<br />');
    echo 'International format: ' . date('Y-m-d');
?>
```

为了给你一个简短方便的参考，前面的代码包含了几种常用的日期格式。根据你所在的位置，日、月、年的使用顺序可能会有所不同：

- 在美国，主要使用月、日、年。

- 在英国和欧洲其他地区，主要使用日、月、年。

- 国际标准日期表示法以年份开头，然后是月和日。

注意：前面的代码使用了四位数的年份表示，因为这样没有歧义。然而，在实践中，两位数年份也很常用。

### 格式化特定日期

```php
<?php
    echo 'Time stamp: ' . mktime(12, 0, 0, 1, 1, 2001);
?>
```

注意：如果你喜欢收集无用的事实：2001 年 9 月 9 日凌晨 3:46:40，时间戳为 1.000.000.000。因此，如果你的时区是中欧时间，`mktime(3, 46, 40, 9, 9, 2001)` 将返回 1000000000。

### 验证日期



```php
<?php
echo '2000 was ' .
    (checkdate(2, 29, 2000) ? 'a' : 'no') .
    ' leap year.<br />';
echo '2100 will be ' .
    (checkdate(2, 29, 2100) ? 'a' : 'no') .
    ' leap year.';
?>
```

当你获得一个日期时——例如，用户通过 HTML 表单提交的日期——必须对这些数据进行验证。这包括检查月份是否存在以及该月是否有足够的天数。如果是二月，你可能还想知道它是否是闰年。

但如果这一切真的必须自己动手，那 PHP 也就不成其为 PHP 了。`checkdate()` 函数可以验证日期；你只需将月、日、年作为参数提供。

提示：为什么 2000 年是闰年，而 2100 年不是？定义是这样的：如果年份能被 4 整除，并且不能被 100 整除或能被 400 整除，那么它就是闰年，二月有 29 天（这是因为地球绕太阳公转大约需要 365.25 天）。如果你想确定某一年是否为闰年，这个函数就派上用场了：

```php
function isLeapYear($year) {
    return ($year % 4 == 0 &&
        ($year % 100 != 0 || $year % 400 == 0));
}
```

你也可以使用 `DateTime::createFromFormat()`，如果发生错误它会返回 false。然而 `checkdate()` 可能更明确，因为函数名准确地描述了我们想要做的事情。

### 计算相对日期

```php
<?php
echo 'The license you have just bought is valid till ';
$expiry = time() + 30 * 24 * 60 * 60; // 30 days
echo strftime('%c', $expiry);
?>
```

有时你需要计算一个相对于当前日期的日期（例如，从现在起 30 天）。当然，你可以真正投入工作来计算这个值，考虑到它是星期几、是否为闰年以及是否与夏令时相关。

使用纪元时间戳要容易得多。例如，前面提到的找到未来 30 天的日期的任务。一天有 24 小时，1 小时有 60 分钟，1 分钟有 60 秒。因此，要获取当前时间戳（使用 `time()` 或 `date('U')`），你只需加上 `30 * 24 * 60 * 60`，就得到了所需日期的时间戳。然后你可以使用此时间戳来设置 cookie 的过期日期，或只是打印出有关此日期的一些信息。

如果你使用 `DateTime` 类，也可以使用 `add()` 和 `sub()` 方法，这些方法将在本章后面“计算两个日期之间的差异”部分中详细介绍。

### 创建可排序的时间戳

```php
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

在数据库中使用日期值并不总是明智的。数据库的不同语言版本、其驱动程序或底层操作系统在区域日期格式不匹配时可能会引起一些问题。

一种潜在的替代方案是使用时间戳。有几种不同的格式可用，但大多数格式具有以下结构：年-月-日 小时-分钟-秒。使用这种值顺序，日期的字符串表示可以轻松排序，从而允许在数据库中使用。

要创建这样的时间戳，只需对 `date()` 进行特殊调用即可。在前面的代码中，这被封装在一个函数中以便重复使用。

提示：此格式也由 MySQL 用于其 `TIMESTAMP` 数据类型的表示。

### 将字符串转换为日期

```php
<?php
echo 'Yesterday: ' . date('r', strtotime('Yesterday')) . '<br />';
echo 'Today: ' . date('r', strtotime('Today')) . '<br />';
echo 'Tomorrow: ' . date('r', strtotime('Tomorrow')) . '<br />';
echo 'In one week: ' . date('r', strtotime('+1 week')) . '<br />';
echo 'One month before: ' . date('r', strtotime('-1 month')) . '<br />';
echo 'Last Sunday: ' . date('r', strtotime('Last Sunday')) . '<br />';
echo 'Next fantasy day: ' . var_export(@date('r', strtotime('Next fantasy day')), true);
?>
```

之前，你看到的是日期的数字表示——要么是日、月、年的三元组，要么是时间戳值。这次，你可以反过来，将日期/时间值的字符串表示转换为 epoch 值或 PHP 及其日期/时间函数中可用的其他内容。

所有魔力都放在了 PHP 函数 `strtotime()` 中。根据文档，它“将几乎任何英文文本日期/时间描述解析为 UNIX 时间戳。”听起来很神奇，而且确实很神奇。其基础是 GNU date 语法；本段开头的代码展示了一些 `strtotime()` 的示例。

注意：在撰写本文时，`strtotime()` 在计算相对日期且即将发生夏令时变更或结束时表现出一些奇怪的行为。同样在撰写本文时，PHP 的日期/时间函数即将被重写和修改。

### 确定日出和日落

```php
<?php
echo 'Sunrise: ' .
    date_sunrise(time(), SUNFUNCS_RET_STRING, 48,
    11.5, 90, 1) . '<br />';
    echo 'Sunset: ' .
    date_sunset(time(), SUNFUNCS_RET_STRING, 48,
    11.5, 90, 1);
?>
```

根据当前位置和日期，日出和日落的时间可能差异很大。然而，存在根据纬度和经度确定此值的公式，并且 PHP 从 PHP 5 开始已将此功能集成到其核心中。你需要做的就是调用 `date_sunrise()` 和 `date_sunset()`。这两个函数都期望若干参数：

- 用于确定日出/日落的日期的时间戳（epoch 值）。

- 返回值的期望格式。`SUNFUNCS_RET_DOUBLE` 将时间作为浮点值返回（介于 0 和 23.99 之间），`SUNFUNCS_RET_STRING` 将其作为字符串返回（介于 00:00 和 23:59 之间），而 `SUNFUNCS_RET_TIMESTAMP` 返回 epoch 值。

- 纬度（北纬；南纬使用负值）。

- 经度（东经；西经使用负值）。

- 日出的天顶（以度为单位）。

- 相对于 GMT 的偏移量（以小时为单位）。

因此，前面的代码计算了德国慕尼黑的日出和日落，慕尼黑位于约 48° 北纬、11°30′ 东经，当天为当前日期。我检查过了：它有效！

### 使用日期和时间进行基准测试

```php
<?php
// ...

$start = microtimestamp();
$s = "";
for ($i=0; $i < 100000; $i++) {
    $s .= "$i";
}
$end = microtimestamp();
echo 'Using double quotes: ' . ($end-$start) . '<br />';

$start = microtimestamp();
$s = '';
for ($i=0; $i < 100000; $i++) {
    $s .= $i;
}
$end = microtimestamp();
echo 'Using no quotes: ' . ($end-$start) . '<br />';
?>
```

![](img/2862989e5dc7f1b1d0bc64321737f084_100_0.png)

Figure 3.3 测量两段代码的性能

提示：你可以用以下代码替换 `microtimestamp()` 函数：

```php
function microtimestamp() {
    return microtime(true);
}
```

当提供参数 `true` 时，函数 `microtime()` 返回当前微时间的浮点值（这是在 PHP 5 中添加的）。然而，据说这比使用 `gettimeofday()` 慢，后者只是执行底层的 gettimeofday 系统调用。

### 使用表单字段进行日期选择

```php
<form method="post" action="">
<select name="day"><?php
    for ($i = 1; $i <= 31; $i++) {
        echo "<option value=\"$i\">$i</option>\n";
    }
?>
</select>
<select name="month"><?php
for ($i = 1; $i <= 12; $i++) {
    $monthname = date('F', mktime(12, 0, 0, $i, 1, 2012));
    echo "<option value=\"$i\">$monthname</option>";
}
?></select>
<select name="year"><?php
for ($i = 2012; $i <= 2015; $i++) {
    echo "<option value=\"$i\">$i</option>";
}
?></select>
</form>
```

如果你想提供一个 HTML 表单来选择日期，就像许多酒店和航班预订服务提供的那样，你可以使用 `date()` 的各种参数；遍历一年的所有月份；从而创建日、月、年的选择列表。前面的代码包含了此的语法；请参阅图 3.4 查看结果。

![](img/2862989e5dc7f1b1d0bc64321737f084_101_0.png)

Figure 3.4 月份名称是自动生成的。

### 创建自更新的表单字段进行日期选择

```php
<?php
if (isset($_POST['month']) &&
    is_numeric($_POST['month']) &&
    ((int)$_POST['month'] >= 1 &&
    (int)$_POST['month'] <= 12)) {
    $month = (int)$_POST['month'];
} else {
    $month = date('n');
}
if (isset($_POST['year']) &&
    is_numeric($_POST['year']) &&
    ((int)$_POST['year'] >= 2012 &&
    (int)$_POST['year'] <= 2015)) {
    $year = (int)$_POST['year'];
} else {
    $year = date('Y');
}
?>
<form method="post" action="<?php echo
htmlspecialchars($_SERVER['PHP_SELF']); ?>">
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
    }
    echo "<option value=\"$i\"$sel>$i</option>\n";
```

```
}
?></select>
// ...
</form>
```

前面片段中的代码有一个小缺陷：每月的天数总是从1到31，即使在某些月份没有那么多天。使用JavaScript，可以编写一个巧妙的脚本来计算当前月份有多少天，然后更新选择列表。

然而，结合使用JavaScript和PHP会更加方便。使用JavaScript，你可以自动提交表单。使用PHP，你可以预填表单字段（更多信息请参见第5章“与Web表单交互”），更重要的是，可以找出相关年份有多少天。

JavaScript代码被限制到最少：选择另一个月份会提交HTML表单（选择另一个年份也是如此，因为闰年会让二月变长）：

```
<select name="month" onchange="this.form.submit();">
...
<select name="year" onchange="this.form.submit();">
```

使用`date('t')`可以找到每月的天数。本片段开头的代码清单包含了其完整代码，其中包括对传输信息的一些合理性检查。此外，除非用户选择了其他日期，否则代码会自动预选当前日期。图3.5显示了完整代码的输出。

![](img/2862989e5dc7f1b1d0bc64321737f084_104_0.png)

图3.5 PHP代码在月份选择列表中填充了适当的天数。

### 计算两个日期之间的差异

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

由`time()`和其他PHP函数获取的纪元值（epoch value）可用于轻松计算两个日期之间的差异。诀窍是将日期转换为时间戳（如果尚未采用这种格式）。然后计算这两个时间戳之间的差值。结果是以秒为单位的时间差。然后可以利用这个值来计算出对应的分钟数、小时数和天数：

- 将结果除以60得到分钟数。

- 将结果除以60 * 60 = 3,600得到小时数。

- 将结果除以60 * 60 * 24 = 86,400得到天数。

如果从天数开始，将每个结果向下取整并从结果中减去该值；你也可以将差值分解为天、小时和分钟。

`DateTime`类提供了一种更直接（且支持时区/夏令时）的方法。它提供了三种方法，可以帮助你计算日期/时间差：

- `add()` 向日期添加一个间隔（`DateInterval`类）。

- `sub()` 从日期中减去一个间隔（`DateInterval`类）。

- `diff()` 计算两个`DateTime`实例之间的差异，返回一个`DateInterval`实例。

#### 表3.3（续）

| Symbol | Description |

|---|---|

| %i | 分钟数（数字） |

| %I | 分钟数（至少两位数字） |

| %m | 月份数（数字） |

| %M | 月份数（至少两位数字） |

| %r | 为负数时为 -，否则为空字符串 |

| %R | 根据正负号为 + 或 - |

| %s | 秒数（数字） |

| %S | 秒数（至少两位数字） |

| %y | 年数（数字） |

| %Y | 年数（至少两位数字） |

| %% | 转义的百分号 |

下面是一个会输出 +01:02:03 的示例：

```php
<?php
$d1 = DateTime::createFromFormat('d.m.Y H:i:s',
    '10.11.2012 23:34:45');
$d2 = DateTime::createFromFormat('d.m.Y H:i:s',
    '11.11.2012 00:36:48');
$i = $d1->diff($d2);
echo $i->format('%R%H:%I:%S');
?>
```

### 使用GMT日期/时间信息

通常，PHP使用本地设置来处理时间格式。但在某些特殊情况下，必须使用GMT时间格式。为此，PHP提供了其部分日期/时间函数的“支持GMT”版本：

- `gmdate()` 的用法与 `date()` 相同，用于格式化日期/时间值；不过返回值使用GMT格式。

- `gmmktime()` 像 `mktime()` 一样创建时间戳；不过它使用GMT。

- `gmstrftime()` 像 `strftime()` 一样格式化时间；不过它使用GMT。

当需要在HTTP标头中设置页面的过期日期，或手动设置Cookie的过期日期（同样是在HTTP标头中）时，GMT非常重要。

### PEAR能提供什么？

以下PHP扩展与应用库（PEAR）包提供了有助于处理各种表单数据的功能：

- `Date` 包含一组用于处理各种日期/时间值的函数，包括时区之间以及各种日期/时间表示形式之间的转换。

- `Date_Holidays` 计算特殊节日的名称和日期。



## 使用对象（及相关主题）

面向对象编程（OOP）是当今最常用的编程范式之一。PHP最初并不是作为面向对象语言设计的，但它在PHP 4中增加了一些有限的OOP支持，并在PHP 5.x中增添了更多。

由于这是一本代码片段手册，OOP不像本书中大多数其他主题那样适合。OOP片段往往很长，或者非常特定于某个场景，或者太普遍以至于可被视为常识（无需经常查阅）。

我们考虑过几种方案，但最终决定呈现各种OOP及与OOP相关主题的混合内容，包括展示PHP实用但非平凡的OOP特性的片段、解释基本构造的片段等等。使用OOP时，大多数时候重要的是经验，但本章仍将提供大量你会想要时常查阅的信息。

### 建立类

```
class MyClass {
}
```

这个片段从PHP的角度简明（当然并不全面）地介绍了最重要的OOP基础知识。OOP概念的核心元素是类。类可以包含常量、属性和方法。可见性关键字`public`、`protected`和`private`表示谁可以访问哪个属性或方法。

如果类被实例化（使用`new`），`$this`关键字会提供对调用对象的引用。如果类包含名为`__construct()`的方法，则该类在实例化时会调用此方法：

```php
<?php
class MyClass {
    private $prop = null;

    public function setProperty($value) {
        $this->prop = $value;
    }

    public function getProperty() {
        return $this->prop;
    }

    public function __construct($value = null) {
        if ($value !== null) {
            $this->prop = $value;
        }
    }
}
```

```php
$c = new MyClass('abc');
echo $c->getProperty();
?>
```

*实现一个类（`class.php`）*

**注意：**可用的三种可见性级别如下：

- `public`——可从任何地方访问

- `protected`——只能从类内部、派生类以及同一个类或派生类的实例访问

- `private`——只能从类内部以及同一个类的实例访问

也可以通过使用`static`上下文（以及`static`关键字），在不需要实例的情况下访问类的属性或方法。显然，静态方法无法访问`$this`。不过，`self`提供了当前类：

```php
<?php
class MyStaticClass {
    private static $prop = 'abc';

    public static function getProperty() {
        return self::$prop;
    }
}

echo MyStaticClass::getProperty();
?>
```

*实现一个带有静态方法和属性的类（`static.php`）*

### 理解继承

```
class DerivedClass extends BaseClass {
```

一个类可以通过`extends`关键字从另一个类继承。这样一来，新类会包含（继承）基类中所有公共（`public`）和保护（`protected`）方法。当然，你也可以在派生类中覆盖这些方法。

通过`parent`关键字可以访问父类。相关语法看起来像静态引用，但实际上并不是——因此你可以在被调用的方法中使用`$this`。

清单 4.3 中的代码覆盖了派生类中的构造函数，同时也调用了父类构造函数。请注意，这两个构造函数的签名是不同的。主代码还调用了基类中的一个方法：

```php
<?php
class MyBaseClass {
    protected $value1 = null;
    protected $value2 = null;

    protected function __construct($value = null) {
        if ($value !== null) {
            $this->value1 = $value;
        }
    }

    public function getValue1() {
        return $this->value1;
    }
}

class MyDerivedClass extends MyBaseClass {
    protected $value2 = null;

    public function __construct($value1 = null,
        $value2 = null) {
        if ($value1 !== null) {
            parent::__construct($value1);
            if ($value2 !== null) {
                $this->value2 = $value2;
            }
        }
    }

    public function getValue2() {
        return $this->value2;
    }
}

$c = new MyDerivedClass('abc', 'def');
echo '1: ', $c->getValue1(), ', 2: ', $c->getValue2();
?>
```

*使用 PHP 实现继承（`extends.php`）*

**注意：** PHP 不支持多重继承，因此一个类只能（恰好）从另一个类派生。当然，你可以让类 B 从类 A 派生，再让类 C 从类 B 派生，这样类 C 也会继承 A 中所有公共（`public`）和保护（`protected`）方法。

### 使用抽象类和接口

```
abstract class MyAbstractBaseClass {
}
```

PHP 还支持另外两种继承方式：抽象类和接口。这两种方式很相似，但差异至关重要。它们的共同目标是为派生类提供一种约定或蓝图：基类（或后续会讨论的多个基类）定义新类中应包含哪些方法。

使用抽象类时，继承方式与之前相同，使用`extends`关键字。不过，新增之处在于基类通过`abstract`关键字被定义为抽象类。同时，抽象类中的一组方法也可以被标记为`abstract`，但这些方法不包含任何代码：

```
protected abstract function myMethod();
```

派生类现在必须实现这些方法，使用相同的签名，以及相同（或至少限制更宽松）的可见性设置。例如，如果抽象基类定义了一个抽象`protected`方法，派生类需要将该方法实现为`protected`或`public`。如果使用了类型提示，这些也必须完全相同。

如果抽象类还包含其他未声明为`abstract`的方法，只要它们是`protected`或`public`，也会像普通类一样被继承：

```php
<?php
abstract class MyAbstractBaseClass {
    protected $value1 = null;
    protected $value2 = null;

    protected function getValue1() {
        return $this->value1;
    }

    protected function getValue2() {
        return $this->value2;
    }

    protected abstract function dumpData();
}

class MyAbstractClass extends MyAbstractBaseClass {
    public function __construct($value1 = null,
        $value2 = null) {
        if ($value1 !== null) {
            $this->value1 = $value1;
            if ($value2 !== null) {
                $this->value2 = $value2;
            }
        }
    }

    public function dumpData() {
        echo '1: ', $this->getValue1(), ', 2:',
        $this->getValue2();
    }
}

$c = new MyAbstractClass('ghi', 'jkl');
$c->dumpData();
?>
```

*使用抽象类（`abstract.php`）*

与普通类一样，抽象类也仅支持单继承。

另一种“大同小异”的方式则使用接口。接口看起来像一个普通 PHP 类，但使用`interface`关键字而不是`class`。接口完全不包含任何实现，只有函数签名。所有这些函数都必须是`public`。

实际的类现在从这个接口“继承”；但在这种上下文中，我们说该类实现了（`implements`）这个接口。这一点通过`implements`关键字来体现，它取代了`extends`。

其他规则与抽象类非常相似：必须实现接口中的所有方法，函数签名需要保持一致（包括可见性级别，反正都是`public`）。额外的好处是，一个类可以同时实现多个接口，只要所涉及的所有接口具有不同的方法名。

下面的代码创建了两个接口，然后在同一个类中实现这两个接口：

```php
<?php

interface MyInterface1 {
    public function getValue1();
    public function getValue2();
}

interface MyInterface2 {
    public function dumpData();
}

class MyInterfaceClass implements MyInterface1, MyInterface2 {
    protected $value1 = null;
    protected $value2 = null;

    public function __construct($value1 = null,
        $value2 = null) {
        if ($value1 !== null) {
            $this->value1 = $value1;
            if ($value2 !== null) {
                $this->value2 = $value2;
            }
        }
    }

    public function getValue1() {
        return $this->value1;
    }

    public function getValue2() {
        return $this->value2;
    }

    public function dumpData() {
        echo '1: ', $this->getValue1(), ', 2:', $this->getValue2();
    }
}

$c = new MyInterfaceClass('mno', 'pqr');
$c->dumpData();
?>
```

### 防止继承与重写

```
final class MyFinalBaseClass {}
public final function myMethod() {}
```

有些类你不希望被继承（例如，如果它们包含关键功能，并且你不希望其他开发人员覆盖这些重要方法）。PHP 的`final`关键字正适合这项任务。你可以将一个类设为`final`（这样根本不可能继承它），也可以将一个方法声明为`final`（这样代码就无法覆盖它）。因此，下面的代码会导致异常，如图 4.1 所示：

```php
<?php
class MyFinalBaseClass {
    public final function getCopyrightNotice() {
        return '&copy; by Original Author';
    }
}

class MyFinalClass extends MyFinalBaseClass {
    function getCopyrightNotice() {
        return '&copy; by me!';
    }
}
?>
```

*使用`final`关键字防止覆盖（`final.php`）*

![](img/2862989e5dc7f1b1d0bc64321737f084_120_0.png)

图 4.1 `final`方法无法被覆盖。

当然，如果你是唯一的开发人员，将类或方法设为`final`似乎没有必要。然而，你应当时刻做好准备，也许开发团队会扩大，或者你会将代码库重构为一个供他人使用的库。

### 使用自动加载

```
spl_autoload_register('myAutoloadFunction');
```

当你使用一个类时，它必须已被定义；否则 PHP 会抛出错误。不过，如果某个类在使用时尚未可用，还有第二次机会。`spl_autoload_register()` 函数会注册一个函数，当 PHP 代码尝试使用一个尚未注册的类时，这个函数就会被调用。在调用注册函数之后，使用未定义类的代码会再次运行。如果此时类可用，那就很好；否则，就会发生通常的错误。

一种常见模式是：对包含类的文件使用固定的命名规则，并将类放在指定的目录中。例如，类`MyClass`位于文件`/classes/MyClass.class.php`中。在这种情况下，下面的自动加载函数会按需加载该类：

```php
<?php
function myAutoloadFunction($classname) {
    if (preg_match('/^[a-zA-Z_\x7f-\xff][a-zA-Z0-9_\x7f-\xff]*$/', $classname)) {
        //check for valid classname
        require_once "/path/to/classes/$classname.class.php";
    }
}

spl_autoload_register('myAutoloadFunction');
?>
```

*自动加载类（`autoload.php`）*

因此，例如下面的调用

`$c = new UnknownClass();`

会转而调用`myAutoloadFunction()`，并将`UnknownClass`作为`$classname`参数的值传入。如果你多次调用`spl_autoload_register()`，所有自动加载函数都会被注册，因此 PHP 会依次调用它们，直到目标类最终被定义——或者直到所有这些函数都被调用完毕。

**注意：**`spl_autoload_register()` 函数是 PHP 5.1.2 中作为 SPL（标准 PHP 库）的一部分引入的。以前，你必须编写一个函数

called `__autoload()` and put your autoloading code there. At some point in the future, `__autoload()` might be removed from PHP, so it is more forward compatible to use `spl_autoload_register()` instead.

**注意：** PHP 还提供了访问不存在的类方法和类属性的功能：

- 如果调用的类方法不存在，则如果存在则执行该类的`__call()` 方法。

- 如果访问的类属性不存在，则如果存在则执行该类的`__get()` 和`__set()` 方法（用于读取和写入访问）。

### 克隆对象

```php
$b = clone $a;
```

假设`$a`中有一个类实例。赋值`$b = $a`不会创建`$a`的副本，但`$b`现在将包含对`$a`的引用；你仍然只有一个类实例。

作为替代方案，PHP 提供了`clone`关键字，可用于创建类的副本：

```php
$b = clone $a;
```

然而，有时你并不想要完全相同的副本。例如，想象每个类实例都有一个属性包含全局唯一标识符（GUID）。即使你克隆了一个类实例，你也希望 GUID 仍然尽可能唯一。

PHP 提供了一种在对象被克隆后注入代码的方法。如果类包含名为`__clone()` 的方法，则在克隆过程完成后会为克隆的类实例执行它：

```php
<?php
class MyCloneableClass {
    private $guid = null;

    public function __construct() {
        $this->guid = uniqid();
    }

    public function __clone() {
        $this->guid = uniqid();
    }

    public function getGuid() {
        return $this->guid;
    }
}

$c1 = new MyCloneableClass();
$c2 = clone $c1;
echo '1: ', $c1->getGuid(), ', 2:', $c2->getGuid();
?>
```

克隆对象（并且仍然更改它们）(`clone.php`)

运行前述代码会导致与图 4.2 相当的结果：两个实例具有不同的 GUID。




图 4.2 两个实例具有不同的 GUID。

### 序列化和反序列化对象

```php
public function __sleep() {
    $this->db->close();
    return array('guid');
}
public function __wakeup() {
    $this->connectDb();
}
```

当你将对象存储以供以后使用时，它们需要被转换为可以轻松放入例如数据库中的东西。PHP 提供了多种将对象实例转换为字符串（并将其恢复为原始形式）的方法；最常见的方法是使用 `serialize()` 和 `unserialize()` 函数，这些函数也在本书的其他章节中使用。

从面向对象编程的角度来看，有趣的是可以拦截序列化和反序列化过程。例如，假设你的类包含一个不应（或不能）被序列化的属性（也许是一个数据库句柄）。理想情况下，该属性应在序列化前移除，并在反序列化时重新创建。

PHP 帮助我们完成此任务并提供了以下两个“魔术”方法名称。如果你的类包含这些方法，它们将被相应执行：

- `__sleep()`—需要返回一个包含所有待序列化属性的数组，也可执行清理操作

- `__wakeup()`—在反序列化后被调用，可用于重新设置属性

以下代码列表显示了关闭和重置数据库连接的典型实现。序列化并反序列化后，GUID 相同，但数据库连接已重新建立：

```php
<?php
class MySerializableClass {
    public $guid = null;
    public $db = null;

    public function __construct() {
        $this->guid = uniqid();
        $this->connectDb();
    }

    private function connectDb() {
        $this->db = new MySQLi('server', 'user',
        'password', 'db');
    }

    public function __sleep() {
        $this->db->close();
        return array('guid');
    }

    public function __wakeup() {
        $this->connectDb();
    }
}

$c1 = new MySerializableClass();
echo 'Before: ', $c1->guid;
$s = serialize($c1);
$c2 = unserialize($s);
echo '; after: ', $c2->guid;
?>
```

序列化和反序列化对象 (`serialize.php`)

**注意：** 反序列化对象时，你需要确保该类存在；否则，PHP 会在结果中使用令人讨厌的“特殊” `PHP Incomplete Class Name` 类。

**提示：** PHP 支持多种魔术方法和函数。在线手册在 `http://php.net/oop5.magic` 处列出了一个列表。

### 实现单例

```php
if (self::$instance == null) {
    self::$instance = new self;
}
return self::$instance;
```

一种常见——但也备受批评——的设计模式是单例模式。它并不完全容易实现，因此我们专门为其创建制定了一句话。

使用单例模式的主要目标是无论你实例化某个类多少次，你都只会得到一个对象。例如，在创建数据库连接时这可能很有用：通常，你只需要一个可以在代码中重复使用的连接。

一种常见的 PHP 单例模式实现使用语言的几个面向对象特性来防止一个类的多个不同实例。首先，类构造函数不可用，因为我们将其设为私有：

```php
private function __construct() {
}
```

创建两个类实例的另一种方法是使用一个实例然后克隆它。这也可以通过将 `__clone()` 魔术方法设为私有来避免：

```php
private function __clone() {
}
```

因此，现在我们无法创建类的多个实例，甚至无法创建一个实例。因此，我们引入一个方法来为我们提供类实例。在类内部，我们可以调用类构造函数——私有可见性允许这样做。然后类实例将存储在静态且私有的类成员中。因此，虚拟实例化方法首先检查我们是否已在该静态属性中存储了类实例。如果是，则返回实例；否则，代码会创建一个新的（且唯一的）实例：

```php
static private $instance = null;

static public function getInstance() {
    if (self::$instance == null) {
        self::$instance = new self;
    }
    return self::$instance;
}
```

以下代码列表包含单例类的完整语法：

```php
<?php
class PHPSingleton{
    static private $instance = null;

    static public function getInstance() {
        if (self::$instance == null) {
            self::$instance = new self;
        }
        return self::$instance;
    }

    private function __construct() {
    }
    private function __clone() {
    }
}
?>
```

实现单例 (`singleton.php`)

**注意：** 如前所述，单例模式有一些缺点。代码通常更难测试，因为单例类需要是全局的并为应用程序添加状态。如同往常一样，因人而异。

### 使用命名空间

PHP 5.3 的一个主要新特性是命名空间的引入。命名空间是用于分组相关功能并避免名称冲突的工具。想象一下你编写了一个通用名称的函数，例如 `showInfo()`。同一项目的另一位开发人员编写了不同的函数但使用了相同的名称。通常，你会为函数名添加前缀使其唯一，这会导致令人讨厌的、非常长的标识符，如 `Project_Module Submodule showInfo()`。命名空间可以在这里提供帮助：你以命名空间的形式提供上下文；在该命名空间内，`showInfo()` 是唯一的；其他开发人员使用其他命名空间。最终，这促进了功能的封装。

命名空间的主要关键字是——惊喜！——`namespace`。`namespace` 关键字必须是 PHP 页面中的第一个命令（可选注释之后），甚至不能被 HTML 标记前置。如果你想结构化命名空间，你可以使用（有点不寻常的）反斜杠字符作为分隔符来创建层次结构：

```php
namespace Project\Module\Submodule;
```

此命名空间现在对整个文件有效。如果你在此文件中创建 `showInfo()` 方法，并将该文件包含在另一个 PHP 脚本中，则可以使用以下代码执行该方法：

```php
Project\Module\Submodule\showInfo();
```

要在一个文件中定义多个命名空间，你可以使用多个 `namespace` 语句；然而首选的方式是使用大括号：

```php
namespace Namespace1 {
    // ...
}
```

```php
namespace Namespace2 {
    // ...
}
```

要使用命名空间，PHP 提供了几种选项。当然，你可以像前面的示例一样提供完全限定的命名空间名称；也支持相对语法。对于局部命名空间，更方便的方式是使用别名。语法 `use <namespace>` 或 `use <namespace> as <alias>` 可以大大减少输入量，并方便命名空间的访问。下面是一个仅导入命名空间的示例：

```php
use Project\Module\Submodule;
Submodule\showInfo();
```

当你使用别名时，代码可能如下所示：

```php
use Project\Module\Submodule as Mod;
Mod\showInfo();
```

在命名空间内，访问 PHP 内置类起初似乎是个难题，因为 PHP 会在当前命名空间中查找这些类。但只需在类名前面加上反斜杠，就能让 PHP 在全局类列表中查找：

```php
namespace Project\Module\Submodule;
$c = new \SoapClient('file.wsdl');
```

关于命名空间，还有很多内容可以讨论，但本着短语手册的宗旨，我们只简要说明命名空间的工作原理。PHP 在线手册在 `http://php.net/namespace` 上有更多相关信息。

### 使用 Trait

```php
class MyTraitClass {
    use MyTrait1, MyTrait2 {
        MyTrait1::showTime as now;
        MyTrait2::showCopyright insteadof MyTrait1;
    }
}
```

PHP 5.4 的新特性之一是支持 Trait，这是一种代码复用的方式。Trait 是函数的集合，是一种无需实例化的类。要使用这一新特性，你必须使用 `trait` 关键字创建 Trait。

```php
trait MyTrait1 {
    public function showTime() {
        $date = new DateTime('now');
        echo $date->format('H:i:s');
    }
}
```

然后，在类中，你可以使用 `use` 关键字加载 Trait。之后这些方法就可以供你使用了：

```php
class MyTraitClass {
    use MyTrait1;
}

$c = new MyTraitClass();
$c->showTime();
```

你也可以在一个类中使用多个 Trait。但在这种情况下，如果有多个 Trait 定义了相同的方法，你就需要小心了；否则你会收到一条错误消息，就像接口有相同方法名时那样。不过，与接口不同，Trait 提供了一种防止该错误的方法。加载 Trait 时，你可以使用 `insteadof` 运算符解决这些命名冲突。例如，假设有两个 Trait，`MyTrait1` 和 `MyTrait2`，它们都定义了 `showTime()` 方法。下面的语法可以确保不会发生错误，并且会使用 `MyTrait1` 中的 `showTime()` 实现，而不是 `MyTrait2` 中的：

```php
class MyTraitClass {
    use MyTrait1, MyTrait2{
        MyTrait1::showTime insteadof MyTrait2;
    }
}
```

另一个特性是使用别名（使用 `as` 关键字），甚至可以在 Trait 中使用抽象方法。下面的代码列表使用了两个 Trait、`insteadof` 和一个别名，其输出与图 4.3 类似：

```php
<?php
    trait MyTrait1 {
        public function showTime() {
            $date = new DateTime('now');
            echo $date->format('H:i:s');
        }

        public function showCopyright() {
            echo '&copy; Trait 1';
        }
    }

    trait MyTrait2 {
        public function showCopyright() {
            echo '&copy; Trait 2';
        }
    }
```

```php
class MyTraitClass {
    use MyTrait1, MyTrait2 {
        MyTrait1::showTime as now;
        MyTrait2::showCopyright insteadof MyTrait1;
    }
}

$c = new MyTraitClass();
$c->now();
echo '<hr />';
$c->showCopyright();
?>
```

使用两个 Trait (`trait.php`)

图 4.3 使用了第二个 Trait 中的 copyright 方法。

## 与 Web 表单交互

HTML 表单是任何动态网站的关键要素之一，因为它们能让网站用户与之交互。否则，网站或多或少是静态的：它们可能由数据库驱动，因此会定期变化，但每一位访问者看到的都是相同的页面。HTML 表单可以改变这种情况；因此，在 PHP 中使用表单数据非常重要。

读取这些信息非常容易：对于通过 GET 提交的表单数据（即在所请求页面的统一资源标识符 [URI] 中），可以在 `$_GET[<表单字段 name 属性的值>]` 中找到这些数据。如果表单是通过 POST 提交的，则 `$_POST[<表单字段 name 属性的值>]` 保存字段数据。然而，这仅仅是开始。假设用户填写了一个表单，但漏掉了某个字段。用户不会看到要求点击浏览器“后退”按钮的错误消息，而会看到一个所有字段都已填入他先前提供的值的表单。许多书都忽略了这一点；更糟糕的是，有些书干脆做错了。你一定不要忘记对表单字段值进行特殊编码：否则，表单容易遭受跨站脚本（XSS）攻击，或者至少会看起来很难看。图 5.1 演示了这一点：你会看到两个文字相同的按钮；然而，只有第一个按钮的文字在 HTML 代码中被正确编码。

图 5.1 必须对特殊字符进行正确编码。

其他值得关注的重要主题包括超文本传输协议（HTTP）文件上传，以及处理 `php.ini` 或其他地方可能妨碍开发人员良好意图的各种设置。

### 将表单数据发送回当前脚本

```php
<form action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
</form>
```

如果在 `<form>` 元素中未提供 `action` 属性，所有相关浏览器都会将表单数据发送回当前页面。然而，HTML 和可扩展超文本标记语言（XHTML）规范都声明 `action` 是必需属性（在文档类型定义 [DTD] 中标记为 `#REQUIRED`）。用户代理的行为是未定义的，正如 `http://w3.org/TR/html4/interact/forms.html#adef-action` 上的 HTML 规范所解释的那样。因此，最好明确提供当前脚本的统一资源定位符（URL）作为表单的 `action`。上面的代码就做到了这一点，并且出于安全原因还会转义 `$_SERVER['PHP_SELF']` 中的特殊字符。另一种更简单（且依然有效）的方法是将 `action` 属性设置为空字符串（`""`）。

### 读取表单数据

在非常早期的 PHP 版本中，读取表单数据非常容易：如果表单字段具有 `name` 属性 `"whatever"`（在较新版本的 HTML/XHTML 中为 `id` 属性 `"whatever"`），PHP 会在全局作用域中创建一个变量 `$whatever`。这非常方便，但从架构的角度来看，无论过去还是现在都是一个糟糕的想法。因此，从 PHP 4.2 开始，通过以下 `php.ini` 指令默认禁用了此功能：

```
register_globals = Off
```

自 PHP 3 以来，以下全局数组一直可用于表单数据：

- `$HTTP_GET_VARS`——通过 GET 提供的所有数据

- `$HTTP_POST_VARS`——通过 POST 提供的所有数据

- `$HTTP_REQUEST_VARS`——通过 GET 或 POST 或 cookie 提供的所有数据（不建议使用）

这些数组是全局的；因此，你必须使用

| 表 5.1 表单字段类型及在 `$_GET`/`$_POST` 中返回的数据 |  |

|---|---|

| **表单字段类型** | **返回的数据** |

| 文本字段 | 字段中的文本 |

| 密码字段 | 字段中的文本（明文，未加密） |

| 多行文本字段 | 字段中的文本 |

| 隐藏字段 | 字段的 `value` 属性 |

| 单选按钮 | 所选单选按钮的 `value` 属性 |

| 复选框 | 复选框选中时的 `value` 属性（若未设置 `value`，通常为 `"on"`） |

| 选择列表 | 所选列表项的 `value` 属性（若未设置 `value`，则为所选列表项的显示文本） |

| 多选列表 | 所选列表项的 `value` 属性组成的数组（若未设置 `value`，则为所选列表项显示文本组成的数组） |

| 提交按钮 | 提交按钮的 `value` 属性（如果该按钮用于提交表单；若有多个提交按钮，这一点很重要） |

> **提示：** 剩下两种表单字段类型——图形提交按钮和文件上传——将在本章后面专门介绍。

### 检查表单是否已提交




```php
<?php
if (isset($_POST['Submit'])) {
    echo '<h1>Thank you for filling out this form!</h1>';
} else {
?>
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
    <input type="submit" name="Submit" value="Submit form" />
</form>
<?php
}
?>
```

当 HTML 表单和处理 PHP 代码位于同一页面时（在预填充表单方面这是推荐的做法），需要确定表单是否只是通过浏览器调用（使用 `GET`）还是已提交（并且数据必须被处理）。

可以采用多种不同的方法来完成此任务：一种始终有效的方法是为提交按钮分配一个名称，然后在表单提交时测试该名称是否存在。

**提示：** 如果你的表单有多个提交按钮，请为每个按钮赋予一个独特的名称；然后，你可以专门检查该名称，从而确定使用了哪个提交按钮。

### 将表单数据保存到 Cookie 中

```php
function setCookieData($arr) {
    $formdata = getCookieData();
    if ($formdata == null) {
        $formdata = array();
    }
    foreach ($arr as $name => $value) {
        $formdata[$name] = $value;
    }
    setcookie('formdata', serialize($formdata), time()+30*24*60*60);
}
```

表单提交后，数据必须去往某个地方，可能存入数据库（参见第 8 章，“使用 MySQL 数据库”，和第 9 章，“使用其他数据库”），写入文件，或通过电子邮件发送。当网站包含多个相似的表单（例如，所有表单都要求用户提供姓名和联系信息）时，在用户填写后保存数据是个好主意。因为 HTTP 是无状态协议，你必须使用 Cookie（参见第 7 章，“在服务器文件系统中使用文件”）——会话是无用的，因为它们在用户关闭浏览器时就会过期。

因为用户代理只需保存每个域的 20 个 Cookie（尽管它们可能存储更多），因此最好将表单信息存储在一个 Cookie 中，以数组的形式。然而，Cookie 中只允许字符串值；这就是为什么你必须序列化数组。此外，请注意你通常只能在 Cookie 中存储不到 4KB 的数据；其余部分可能会被截断。

本段开头列出的函数会将作为参数提供的数组内容写入 Cookie。

函数`getCookieData()`返回 Cookie 中已存在的数据（如有），并将其反序列化为数组。你将在后面的段落中看到代码。

剩下的唯一工作就是将所需的表单数据写入此数组。你可以只提交某些特定值，或完整的数组`$_GET`或`$_POST`，如下代码所示：

```php
<?php
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
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
...
</form>
<?php
}
?>
```

图 5.2 显示了由此产生的 Cookie。

![](img/2862989e5dc7f1b1d0bc64321737f084_142_0.png)

图 5.2 序列化后的表单数据保存在 Cookie 中。

**注意：** 请注意，你必须在任何 HTML 输出之前保存表单数据。因为 Cookie 是作为 HTTP 头的一部分发送的，所以它们必须在 HTML 开始之前声明（因此 HTTP 头也就结束了）。你可以在第 6 章找到有关 Cookie 时机的更多信息。

### 预填充文本字段和密码字段

```php
<input type="text" name="textfieldname" value="<?php echo isset($_POST['textfieldname']) ? htmlspecialchars($_POST['textfieldname']) : '';?>" />
```

文本字段（以及密码字段和隐藏字段）中的值通过其`value`属性提供。然而，那里的數據必須使用`htmlspecialchars()`正确编码，以去掉诸如`"`, `<` 或 `>`等危险字符。前述代码片段期望表单提交回自身：因此，它从`$_POST`中提取文本字段的当前值（使用`$_GET`也可类似工作）。这同样适用于密码字段和隐藏字段（尽管预填充密码字段被认为是不良做法，因为其中的“秘密”数据在 HTML 中未加密）。

**注意：** 如果你还想转义单引号 (`'`) 字符，请按以下方式使用`htmlspecialchars()`：

```php
htmlspecialchars($_POST['textfieldname'], ENT_QUOTES)
```

因为在我们的表单中所有 HTML 属性都由双引号分隔，所以我们不需要特别转义单引号。然而，如果你使用单引号，则绝对需要在属性值中转义它们。

如果你想为此表单元素使用默认值，只需在 PHP 代码中提供该默认值，而不是空字符串：

```php
<input type="text" name="textfieldname"
    value="<?php
    echo (isset($_POST['textfieldname'])) ?
    htmlspecialchars($_POST['textfieldname']) : 'default
    value';
    ?>" />
```

另一种可能性是从 Cookie 预填充表单值。当用户多次向表单输入数据时，这非常有用。因此，当他们几天后再次访问网站上的表单时，旧数据可以从 Cookie 中检索。是的，只需 1 个 Cookie，因为每个域只允许 20 个 Cookie。我们当然为此使用数组。然而，Cookie 值只允许字符串，所以需要使用`serialize()`和`unserialize()`。

下面的函数从包含表单数据的 Cookie 中检索一个值。优先级默认如下（但可通过`variables_order` `php.ini`设置更改）：如果`$_GET`或`$_POST`包含此字段的当前值，则使用该值。（针对`$_GET`和`$_POST`存在特定版本的函数，因为这两种方法通常一次只使用一种。）否则，脚本会在`$_COOKIE`中查找相关值。如果未找到任何内容，则返回空字符串：

```php
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

现在，预填充表单值很容易：因为`getFormDataGET()`和`getFormDataPOST()`总是返回内容——包括空字符串——因此返回值可以直接用于文本字段的`value`属性中：

```php
<?php
require_once 'getFormData.inc.php';
?>
...
<input type="text" name="textfieldname"
    value="<?php
    echo
    htmlspecialchars(getFormDataPOST('textfieldname'));
?>">
```

### 预填充多行文本字段

```php
<textarea cols="40" rows="5" name="areafieldname"><?php echo (isset($_POST['areafieldname'])) ? htmlspecialchars($_POST['areafieldname']) : ''; ?></textarea>
```

对于多行文本字段，几乎可以使用与单行文本字段和密码字段相同的方法。唯一的区别是放置预填充值的位置：它应位于`<textarea>`和`</textarea>`之间，如前述代码所示。

**注意：** 如果你想在多行文本字段中提供默认值（例如，“在此输入你的数据”），请在 PHP 代码中提供它而不是空字符串。请记住，换行也是可能的：

```php
<?php
 echo (isset($_POST['areafieldname'])) ?
 htmlspecialchars($_POST['areafieldname']) :
 "default\nvalue";
?>
```

使用组合的 Cookie/GET 或 Cookie/POST 方法，代码会简化一些：

```php
<?php
require_once 'getFormData.inc.php';
?>
...
<textarea cols="40" rows="5" name="areafieldname"><?php
 echo htmlspecialchars(getFormDataPOST('areafieldname'));
?></textarea>
```

### 预选单选按钮

```php
<input type="radio" name="groupname" value="php52"
<?php
if (isset($_POST['groupname']) && $_POST['groupname'] == 'php52') {
    echo 'checked="checked" ';
}
?>/>PHP 5.2
<input type="radio" name="groupname" value="php53"
<?php
if (isset($_POST['groupname']) && $_POST['groupname'] == 'php53') {
    echo 'checked="checked" ';
}
?>/>PHP 5.3
<input type="radio" name="groupname" value="php54"
<?php
if (isset($_POST['groupname']) && $_POST['groupname'] == 'php54') {
    echo 'checked="checked" ';
}
?>/>PHP 5.4
```

单选按钮组通过共同的`name`属性来标识。在一组按钮中，只能选择一个（或都不选）。提交表单到服务器时，所选单选按钮的`value`属性会被传输到服务器。因此，预先填充一组单选按钮虽然有点繁琐但相当简单：只需将`$_GET/$_POST`中的值与关联的值进行比较。如果匹配，就输出`checked`，即预选单选按钮的 HTML 属性，如前面的代码所示。

此代码可以扩展，以便在用户之前已将其选择保存在 cookie 中时预选单选按钮，使用包含文件`getFormData.inc.php`，如以下代码所示：

```php
<?php
    require_once 'getFormData.inc.php';
?>
...
<input type="radio" name="groupname" value="php52"
<?php
    if (getFormDataPOST('groupname') == 'php52') {
        echo 'checked="checked" ';
    }
?>/>PHP 5.2
<input type="radio" name="groupname" value="php53"
<?php
    if (getFormDataPOST('groupname') == 'php53') {
        echo 'checked="checked" ';
    }
?>/>PHP 5.3
<input type="radio" name="groupname" value="php54"
<?php
    if (getFormDataPOST('groupname') == 'php54') {
        echo 'checked="checked" ';
    }
?>/>PHP 5.4
```

### 预选复选框

```php
<input type="checkbox" name="boxname" value="yes"
<?php
    if (isset($_POST['boxname']) && $_POST['boxname'] == 'yes') {
        echo 'checked="checked" ';
    }
?>/>I agree. ...
```

尽管有些网站假装像单选按钮一样对复选框进行分组，但从技术上讲这并不正确。每个复选框都是独立的；因此它们都应该有不同的名称；给它们相同的名称是没有意义的。然后可以单独处理每个复选框：检查关联的`value`属性，然后如果找到匹配项就输出`checked` HTML 属性。

使用 cookie 数据（如果可用）时，代码会略有变化：

```php
<?php
require_once 'getFormData.inc.php';
?>
...
<input type="checkbox" name="boxname" value="yes"
<?php
if (getFormDataPOST('boxname') == 'yes') {
    echo 'checked="checked" ';
}
?>/>I agree.
```

### 预选选择列表

```php
<select name="listname">
<option value="php52"<?php
if (isset($_POST['listname']) && $_POST['listname'] == 'php52') {
    echo ' selected="selected"';
}
?>>PHP 5.2</option>
<option value="php53"<?php
if (isset($_POST['listname']) && $_POST['listname'] == 'php53') {
    echo ' selected="selected"';
}
?>>PHP 5.3</option>
<option value="php54"<?php
if (isset($_POST['listname']) &&
$_POST['listname'] == 'php54') {
    echo ' selected="selected"';
}
?>>PHP 5.4</option>
</select>
```

在单选选择列表中，提交表单时，所选`<option>`元素的值会传输到服务器。然后可以使用`selected` HTML 属性手动检查该值以预先填充表单，如前面的代码所示。

使用`getFormData.inc.php`也可实现相同的效果；然后如果可用，就使用站点 cookie 中的数据：



```php
<?php
require_once 'getFormData.inc.php';
?>
...
<select name="listname">
<option value="php52"<?php
if (getFormDataPOST('listname') == 'php52') {
    echo ' selected="selected"';
}
?>>PHP 5.2</option>
<option value="php53"<?php
if (getFormDataPOST('listname') == 'php53') {
    echo ' selected="selected"';
}
?>>PHP 5.3</option>
<option value="php54"<?php
if (getFormDataPOST('listname') == 'php54') {
    echo ' selected="selected"';
}
?>>PHP 5.4</option>
</select>
```

### 预选多选列表

```php
<select name="multilistname[]" multiple="multiple" size="3">
<option value="php52"<?php
if (isset($_POST['multilistname']) &&
is_array($_POST['multilistname']) &&
in_array('php52',
$_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>>PHP 5.2</option>
<option value="php53"<?php
if (isset($_POST['multilistname']) &&
is_array($_POST['multilistname']) &&
in_array('php53',
$_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>>PHP 5.3</option>
<option value="php54"<?php
if (isset($_POST['multilistname']) &&
is_array($_POST['multilistname']) &&
in_array('php54',
$_POST['multilistname'])) {
    echo ' selected="selected"';
}
?>>PHP 5.4</option>
</select>
```

谈到预先填充表单元素时，多选列表是最难实现的一种。这是因为在`$_GET`或`$_POST`中，你有一个所选选项的数组；因此不能只比较字符串，而必须在数组中搜索指定的值。幸运的是，PHP 提供了`in_array()`函数来满足这一需求。因此所需的工作量并不比其他表单元素多多少：如果当前值在`$_GET/$_POST`中，就输出`selected`属性。

然而，HTML 表单必须特别准备，以便 PHP 能访问多选列表的数据：`name`属性的值必须以`[]`结尾，提示 PHP 应该期望一个值数组，而不是仅一个字符串值。但是，访问列表数据仍然可以使用`$_GET['listname']/$POST['listname']`，而不是`$_GET['listname[]']/$POST['listname[]']`，如前面的代码所示。

如果想用 cookie 中的数据预先填充列表，只需使用前面各节中已知的`getFormData.inc.php`文件即可。它包含两个额外的函数，它们返回数组而不是字符串：

```php
function getFormDataArrayGET($name) {
    if (isset($_GET[$name])) {
        return $_GET[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null && isset($cookiedata[$name])) {
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

这些函数为多选列表返回一个数组，你可以像在`select-multiple.php`中那样使用它。

```php
<?php
    require_once 'getFormData.inc.php';
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
<head>
    <title>Forms</title>
</head>
<body>
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
    <select name="multilistname[]" multiple="multiple" size="3">
        <option value="php52"<?php
if (in_array('php52', getFormDataArrayPOST('multilistname'))) {
    echo ' selected="selected"';
}
?>>PHP 5.2</option>
        <option value="php53"<?php
if (in_array('php53', getFormDataArrayPOST('multilistname'))) {
    echo ' selected="selected"';
}
?>>PHP 5.3</option>
        <option value="php54"<?php
if (in_array('php54', getFormDataArrayPOST('multilistname'))) {
    echo ' selected="selected"';
}
?>>PHP 5.4</option>
    </select><br />
    <input type="submit" />
</form>
</body>
</html>
```

### 处理图形提交按钮

```php
<?php
if (isset($_POST['Submit_x']) &&
isset($_POST['Submit_y'])) {
    printf('<h1>You clicked at the following
coordinates: x-%s, y-%s</h1>',
        htmlspecialchars($_POST['Submit_x']),
        htmlspecialchars($_POST['Submit_y'])
    );
} else {
?>
```

```php
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
<input type="image" name="Submit"
src="pearsoned.gif" />
</form>
<?php
}
?>
```

图形提交按钮 (`<input type="image" />`) 不仅是美化表单布局的好方法，而且还提供了一个不错的功能：浏览器在点击按钮时会提交鼠标指针的 x 和 y 坐标。在 PHP 中，这通过在按钮的`name`属性后附加`_x`和`_y`并将其写入`$_GET`或`$_POST`来实现。前面的代码评估了此信息。

**注意：** 当您使用键盘提交表单时（例如，使用 Enter 键），两个坐标都为 0。

### 检查必填字段

```php
<?php
if (isset($_POST['Submit']) &&
    isset($_POST['textfieldname']) &&
    trim($_POST['textfieldname']) != '') {
    echo '<h1>Thank you for filling out this form!</h1>';
} else {
?>
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
```

```php
<input type="text" name="textfieldname"
    value="<?php
echo (isset($_POST['textfieldname'])) ?
htmlspecialchars($_POST['textfieldname']) : '';
?>" />
<input type="submit" name="Submit" />
</form>
<?php
}
?>
```

在表单验证期间，大多数情况下重点在于必填字段。您可以以两种方式检查它们是否包含值：

- 检查字段是否存在于 `$_GET/$_POST` 中：

```php
if (!isset($_GET['fieldname'])) {
    // Error!
}
```

- 检查 `$_GET/$_POST` 中的值是否包含除空白字符之外的信息：

```php
if (trim($_GET['fieldname']) == '') {
    // Error!
}
```

非常重要的一点是您要结合这两种技术。您始终必须使用 `isset()` 检查字段是否存在，以避免在尝试访问不存在的数组值时出现错误消息。但是，由于文本字段始终会被提交，您始终必须检查字段内是否除了空白字符之外还有内容。此外，当为空时，`isset()` 始终返回 true，与字段的值无关。本节开头的代码显示了一个示例。

提示：此方法也适用于所有其他文本表单元素、单选按钮和复选框。它可以很容易地扩展以检查某些模式，包括有效的电子邮件地址。有关此处的帮助，请参阅第 2 章“使用数组”。

注意：表单元素的预填充代码已被保留，以便此代码片段可以与其他代码片段合并。因此，如果表单仅部分填写，则正确的表单字段会被预填充。

### 检查选择列表

```php
<?php
    if (isset($_POST['Submit']) &&
        isset($_POST['listname']) &&
        $_POST['listname'] != '') {
        echo '<h1>Thank you for filling out this
        form!</h1>';
    } else {
?>
<form method="post" action="<?php echo
htmlspecialchars($_SERVER['PHP_SELF']); ?>">
    <select name="listname">
        <option value="">Please select from
        list</option>
        <option value="php52"><?php
        if (isset($_POST['listname']) &&
            $_POST['listname'] == 'php52') {
            echo ' selected="selected"';
        }
        ?>
?>PHP 5.2</option>
<option value="php53"><?php
if (isset($_POST['listname']) && $_POST
['listname'] == 'php53') {
echo ' selected="selected"';
}
?>PHP 5.3</option>
<option value="php54"><?php
if (isset($_POST['listname']) && $_POST
['listname'] == 'php54') {
echo ' selected="selected"';
}
?>PHP 5.4</option>
</select><br />
<input type="submit" name="Submit" />
</form>
<?php
}
?>
```

在验证选择列表时，方法取决于列表的类型：

- 如果是只能选择一个元素的列表，则在以下情况下认为列表填写不正确

  - 列表中未选择任何选项。

  - 所选选项的值为空字符串。

- 如果是可选择多个元素的列表，则在以下情况下认为列表填写不正确

  - 列表中未选择任何选项。

  - 所有选定选项的值均为空字符串。

如果列表包含功能性的虚拟条目，其标题为“Please choose from list.” 等，则会使用值为空字符串的选项。这些列表选项不得接收除“”之外的其他值，以便验证算法可以将这些条目与合理的条目区分开。

本节开头的列表验证单个选择列表——再次包括用于预填充列表的 PHP 代码。

对于多个列表，需要做更多的工作，如以下代码所示。如果表单已被提交，则会搜索所选列表元素的数组。如果找到一个非空元素，则过程完成，用户可以因成功完成表单而受到祝贺。否则，表单将再次显示：

```php
<?php
$ok = false;
if (isset($_POST['Submit']) &&
    isset($_POST['multilistname'])) {
    if (is_array($_POST['multilistname'])) {
        for ($i=0; $i < count(
$_POST['multilistname']); $i++) {
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
}
```

```php
} else {
?>
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
<select name="multilistname[]" multiple="multiple" size="3">
</select>
<br />
<input type="submit" name="Submit" />
</form>
<?php
}
?>
```

### 转义输出

```php
filter_input(INPUT_POST, 'FieldName', FILTER_SANITIZE_SPECIAL_CHARS);
```

转义输出是安全 Web 开发的关键支柱之一。如果您输出动态数据（即由客户端或任何其他不可信的外部源提供的信息），则需要根据输出数据的上下文转义特殊字符。通常，上下文是 HTML，因此您需要转义 HTML 中的特殊字符——`'`、`<`、`>` 和 `&`。PHP 为此任务提供了`htmlspecialchars()`函数，但 PHP 5.2 中添加的 filter 扩展提供了更通用的方法。

`filter_input()`函数不一定会过滤输入，但也可能有助于转义特殊字符。作为第一个参数，您提供要查找要过滤的数据的位置（例如，`INPUT_POST`用于 POST 数据和`INPUT_GET`用于 GET 数据）。在第二个函数参数中，您提供要处理的`GET/POST/...`变量的名称。在第三个参数中，您提供要使用的过滤器。以下代码生成可用于`filter_input()`的所有过滤器及其数字 ID 的列表：

```php
$list = filter_list();
foreach ($list as $value) {
    print('%s: %s', $value, filter_id($value));
}
```

PHP 也有所有过滤器的内置常量（例如，`FILTER_SANITIZE_SPECIAL_CHARS` 而不是其数字值 515）。

**注意：** 您也可以转义变量。只需使用 `filter_var()` 代替 `filter_input()` 并提供变量和要使用的过滤器。

### 验证输入

```php
$email = filter_input(INPUT_POST, 'email',
    FILTER_VALIDATE_EMAIL);
```



不仅 `filter_input()` 和 `filter_var()` 函数（及其同级函数）支持数据的转义，还支持数据的验证（例如，变量或表单字段是否包含有效的电子邮件地址）。这些验证过滤器很容易被发现——例如，`FILTER_VALIDATE_EMAIL`。其他验证常量是 `FILTER_VALIDATE_REGEXP`、`FILTER_VALIDATE_URL` 和 `FILTER_VALIDATE_IP`。

这些验证的返回值可能有点令人惊讶，但它们与其它过滤器的返回值保持一致：返回已验证（在这种情况下未更改）的数据。但是，如果验证失败，函数将返回 false。因此，在验证输入或变量之后，您要么拥有有效数据，要么没有数据。

### 将所有表单数据写入文件

```php
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
<form method="post" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
...
</form>
<?php
}
?>
```

After a user fills out a form correctly, what do you do with the form data? A very intuitive approach that does not require too much setup on the server is to write the data into a file on the server.

The preceding code contains a very naive approach: All data is stored in a file on the server. When the form is submitted, the file is read in and unserialized into an array. Then, the form data is appended to the array. Finally, the array is serialized again and written back to the file.

Figure 5.3 shows this file in a text editor.

![](img/2862989e5dc7f1b1d0bc64321737f084_163_0.png)

Figure 5.3 Data written into the form (but which can later be unserialized)

注意：当然，可能会发生竞态条件，文件可能被两个进程同时读取，这会导致只有其中一个进程出现在文件中。为避免这种情况，你必须实现如第 7 章所示的文件锁定。

### 通过电子邮件发送所有表单数据

```php
<?php
if (isset($_POST['Submit']) &&
isset($_POST['fieldname']) &&
trim($_POST['fieldname']) != '' &&
$_POST['groupname'] != '') {
echo '<h1>Thank you for filling out this form</h1>';
$text = '';
foreach ($_POST as $name => $value) {
if (is_array($value)) {
$text .= sprintf("%s: %s\n", $name, join(', ', $value));
} else {
$text .= sprintf("%s: %s\n", $name, $value);
}
}
mail('recipient@example.com', 'Form data',
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

可以通过发送表单数据到电子邮件来实现对有人填写表单的更及时通知。当然，你可以为每个表单编写自定义的邮件脚本；然而，前面的代码展示了如何通用地完成此操作。通过 `foreach`，所有表单数据被合并成一个字符串。对数组形式的表单值给予了特别关注——这可能发生在多选列表中。然后表单数据会被发送给网站管理员；只是不要忘记更改电子邮件地址。

### 获取文件上传信息

```php
<?php
if (isset($_POST['Submit']) &&
    isset($_FILES['File']) &&
    is_uploaded_file($_FILES['File']['tmp_name'])) {
printf('<p>Error: %s<br />
    Original name: %s<br />
    File size: %s<br />
    Temporary name: %s<br />
    MIME type: %s</p>',
    $_FILES['File']['error'],
    htmlspecialchars($_FILES['File']['name']),
    $_FILES['File']['size'],
    $_FILES['File']['tmp_name'],
    htmlspecialchars($_FILES['File']['type'])
);
} else {
?>
<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="post" enctype="multipart/form-data">
<input type="file" name="File" />
<input type="submit" name="Submit" value="Submit form" />
</form>
<?php
}
?>
```

当你使用 `<input type="file" />` 向 Web 服务器上传文件时，HTML 表单必须满足两个要求：

- The enctype attribute has to be set to "multipart/form-data".

- The method attribute has to be set to "post".

如果没有这些设置，文件上传将无法工作。如果 `php.ini` 中缺少以下信息，也无法工作：

```
file_uploads = On
```

但如果设置了，获取文件信息就非常容易：在（超全局）数组 `$_FILES` 中，你可以在其名称下找到文件上传表单字段。然后，以下子键提供了有关上传文件的更多信息：

- `$_FILES["File"]["error"]`—错误代码（成功时为 0）

- `$_FILES["File"]["name"]`—原始文件名

- `$_FILES["File"]["size"]`—文件大小

- `$_FILES["File"]["tmp_name"]`—PHP 保存文件的临时文件名

- `$_FILES["File"]["type"]`—客户端发送的文件 MIME 类型，不可靠

前面的代码输出了可用的文件信息（参见图 5.4）。对 `is_uploaded_file()` 的调用通过首先检查文件是否确实由客户端上传，增加了额外的安全层。

![](img/2862989e5dc7f1b1d0bc64321737f084_167_0.png)

Figure 5.4 Information about the uploaded file

注意：在处理表单字段时存在一些注意事项。你可以在隐藏表单字段中提供上传文件的最大文件长度；然而，此检查随后在服务器端执行，因此最好在自己的脚本中使用 "type" 数组子元素自行完成。

此外，不要依赖 "name" 数组子元素，因为此信息（原始文件名）可能被伪造。更糟糕的是，一些浏览器并不总是发送原始文件名，而是发送其完整路径。因此，始终调用 `basename()` 仅提取文件名。

在我们的代码中，在输出这两个信息中的任何一个之前，我们都会运行 `htmlspecialchars()`。

### 将上传文件移动到安全位置

```php
<?php
    if (isset($_POST['Submit']) &&
        isset($_FILES['File'])) {
        $move = move_uploaded_file(
            $_FILES['File']['tmp_name'],
            '/tmp/' . basename($_FILES['File']['name'])
        );
        echo '<h1>';
        echo ($move) ? 'Moved' : 'Did not move';
        echo ' the file!</h1>';
    } else {
?>
<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="post" enctype="multipart/form-data">
    <input type="file" name="File" />
    <input type="submit" name="Submit" value="Submit form" />
</form>
<?php
}
?>
```

当用户使用 `<input type="file" />` HTML 元素向 PHP 脚本上传文件时，PHP 会将文件存储在临时位置（在 `php.ini` 指令 `upload_tmp_dir` 中设置）并在脚本执行完成后删除它。因此，你必须在脚本内访问上传的文件。为此，PHP 包含函数 `move_uploaded_file()`，它可以将文件从一个位置移动到另一个位置。`move_uploaded_file()` 的优点是该函数首先进行健全性检查，检查你提供的文件名是否确实是一个上传的文件，还是恶意用户试图诱骗你将 `/etc/passwd` 或 `C:\boot.ini` 移动到其他地方。

假设路径 `/tmp` 存在并且可被 Web 服务器和 PHP 进程写入。在这种情况下，前面的代码会使用其原始文件名将上传的文件移动到此目录（你不关心文件名是否已存在）。

### 监控文件上传进度

```php
var_dump($_SESSION[ini_get('session.upload_progress_prefix') . 'myUpload']); ?>
```

截至撰写本文时，Web 浏览器不包含确定文件上传状态的内置功能。尤其是对于大文件或慢速连接，此信息将非常有价值。

当今大多数显示文件已上传多少的 Web 应用程序都使用 Flash、Silverlight 或 Java 等插件技术。从 PHP 5.4 版本开始，也可以通过服务器端手段确定文件上传的状态。

`php.ini` 文件包含文件上传状态功能配置选项。以下是最重要的选项：

- `session.upload_progress.enabled` — 激活文件上传跟踪，必须设置为 On。

- `session.upload_progress.prefix`—`$_SESSION` 数组中存储文件上传状态信息的键前缀。默认为 `upload_progress_`。

- `session.upload_progress.name`—POST 值的名称，其中将包含 `$_SESSION` 数组中存储文件上传状态信息的键后缀。默认为 `PHP_SESSION_UPLOAD_PROGRESS`。

通常在使用此功能时，你会包含一些 JavaScript 代码，持续调用服务器脚本以了解更新状态。为了简洁起见，我们在这里使用一种更简单的方法。

在一个文件中，我们设置文件上传。如果满足以下两个条件，PHP 会自动将文件上传信息存储在会话中：

- The form must contain a (ideally hidden) form field with the name equaling the `session.upload_progress.prefix` value.

- The PHP session must have been started.

这是一个典型的表单：

```php
<?php
session_start();
?>
<form method="post" action="" enctype="multipart/form-data">
<input type="file" name="upload" />
<input type="hidden" name="<?php echo ini_get('session.upload_progress.name'); ?>" value="<?php echo session_id(); ?>" />
<input type="submit" value="Upload" />
</form>
```

隐藏的表单字段可能看起来像这样——当然，这取决于 `php.ini` 设置和当前的会话 ID：

```
<input type="hidden"
name="PHP_SESSION_UPLOAD_PROGRESS"
value="ktgbht0abtnb897fv3j4pr16g6" />
```

然后，当用户提交表单从而上传文件时，`$_SESSION['upload_progress_ktgbht0abtnb897fv3j4pr16g6']` 包含有关文件上传的信息，形式为数组，包括开始时间、服务器期望的总字节数以及客户端已传输了多少。`$_SESSION` 键的名称由 `session.upload_progress.prefix` 值和隐藏表单字段中的值生成。

为测试目的，你可能想在另一个标签页中打开一个 PHP 文件，持续输出该 `$_SESSION` 字段中的数据。图 5.5 显示了可能的输出。

![](img/2862989e5dc7f1b1d0bc64321737f084_171_0.png)

图 5.5 确定 HTTP 文件上传的状态

注意：在测试期间，我们发现此功能并非在所有服务器上都有效。尤其是在 Windows 系统上，`$_SESSION` 功能保持为空。我们有信心在未来版本的 PHP 中这会工作得更好。

### PEAR 提供什么？

以下 PHP 扩展和应用程序仓库（PEAR）包提供了有助于处理任何类型表单数据的功能：

- `HTML_QuickForm2` 是一个非常方便的包，可使用面向对象编程语法创建表单，并包含非常强大的验证和处理功能。

- `HTTP Upload` 有助于管理文件上传，并提供高级功能，例如为上传提供有效扩展。然而，截至撰写时，该包已无人维护。

## 记住用户（Cookie 和会话）

超文本传输协议（HTTP）是一种无状态协议。简单来说，客户端（Web 浏览器）连接到 Web 服务器，发送请求并获得响应。然后连接关闭。其后果是下一次同一客户端向同一 Web 服务器发送请求时，这是一个新请求，因此 Web 服务器无法识别调用者。当然，这对于必须维护状态的应用程序来说是个问题（例如，具有购物车功能的电子商务应用程序）。

然而，你可以通过几种方式克服这一限制。基本思路是随 HTTP 响应发送一些信息；为实现这一目的，这些信息会在后续所有请求中发回给该服务器。存在以下可能性：

- 通过 POST 发送数据（即每次都需要表单）

- 通过 GET 发送数据（即通过将此信息附加到请求的统一资源定位符 [URL]）

- 将数据作为 HTTP 头的一部分发送（以 cookie 的形式）

在实际项目中，使用两种方法之一：会话（通过 GET 或 cookie）和 cookie。

### 理解 Cookie

Cookie 作为 HTTP 头的一部分发送，基本上是一个名称-值对。其主要缺点是可以在 Web 浏览器中停用 cookie（也可以在代理服务器中将其过滤掉）。有些人认为 cookie 会造成隐私问题。其中一部分可能是由 John Udell 于 1997 年 3 月撰写的一篇文章引起的，他在其中写道每个 cookie 都可以被每个 Web 服务器读取，因此没有隐私。这引起了相当大的轰动，尽管不幸的是，两个月后的更正并未得到同等程度的关注。

事实上，cookie 有一些限制：

- Cookie 与域绑定，通常是发送 cookie 的域。

- Cookie 可以与 Web 服务器上的路径绑定。

- Cookie 仅包含文本信息，最多 4096 字节（包括 cookie 名称和名称与值之间的 = 字符）。

- 浏览器最多只能接受每个域 20 个 cookie，总共 300 个 cookie（尽管某些浏览器接受更多）。

注意：（非官方的）cookie 规范可追溯到 Netscape，并已归档在 `http://curl.haxx.se/rfc/cookie_spec.html`。曾尝试为下一代 cookie 创建特殊的请求评论（RFC），但尚未获得合理的浏览器支持。



Cookie 作为 HTTP 头的一部分发送。如果设置了 cookie，则会创建 HTTP 头条目 `Set-Cookie`。cookie 的名称和值（均为字符串）随后出现，并且可选地还有诸如过期日期、域和 cookie 路径等进一步信息。例如，访问 `www.php.net/` 时，PHP 网站会发送此头条目。（因人而异，尤其是在使用的语言和 IP 地址方面。）

```
Set-Cookie: COUNTRY=DEU%2C84.154.17.84; expires=Thu, 17-May-12 15:23:29 GMT; path=/; domain=.php.net
```

当浏览器（或用户）接受 cookie 时，它随后会在 HTTP 头 `Cookie` 中发回服务器：

```
Cookie: COUNTRY=DEU%2C84.154.17.84
```

**提示：**要实际查看 HTTP 头，你可以使用标准 Web 浏览器的特殊扩展。对于 Mozilla 浏览器（包括 Firefox），可在 `http://livehttpheaders.mozdev.org/` 获取的 LiveHTTPHeaders 扩展是真正的省时工具。Microsoft Internet Explorer 用户可能有兴趣安装 `ieHTTPHeaders`，这是一个可从 `www.blunck.info/iehttpheaders.html` 获取的 Explorer 栏。许多现代浏览器的内置 Web 开发附加组件也提供了轻松访问 cookie 信息的方式。图 6.1 显示了访问 PHP 主页时 Firefox 扩展显示的一些输出。

![](img/2862989e5dc7f1b1d0bc64321737f084_177_0.png)

图 6.1 Cookie 作为 HTTP 头的一部分设置。

Cookie 可以有过期日期。如果设置了，cookie 最多存活到该日期，被称为持久 cookie。之后，浏览器会自动删除 cookie——但这也可能更早发生（例如，当浏览器中的 cookie 数量达到最大值时，最旧的 cookie 会被清除）。如果未设置 cookie 过期日期，则会创建所谓的会话 cookie 或临时 cookie。它在 Web 浏览器运行期间存活。当关闭时，cookie 会被删除。

## 创建 Cookie

### setcookie()

```php
<?php
setcookie('version', phpversion());
?>
```

尝试发送 cookie。

设置 Cookie（setcookie.php）

要创建 cookie，可以使用 PHP 函数 `setcookie()`。它期望以下参数；然而，只有第一个是强制性的：

- cookie 的名称

- cookie 的值

- 过期日期（UNIX 纪元格式）

- 可以访问 cookie 的 Web 服务器上的路径

- 可以访问 cookie 的域

- cookie 是否只能通过安全（HTTP 安全 [HTTPS]/安全套接字层 [SSL]）连接发送

- cookie 是否只能由服务器在 HTTP 请求后访问，但应隐藏于 JavaScript

前面的代码设置了一个简单的会话 cookie，其值为当前 PHP 版本。

**提示**

`setcookie()` 的最后两个选项可以是重要的安全保护措施。通过将 cookie 限制为 HTTPS 连接，在开放网络中“嗅探” cookie 数据（如会话 ID）会更困难。而且如果 JavaScript 无法访问 cookie 信息，一些攻击向量可能会不复存在。

图 6.2 显示了 Firefox 浏览器中的 cookie 警告。你可以清楚地看到 cookie 名称和脚本。

![](img/2862989e5dc7f1b1d0bc64321737f084_179_0.png)

图 6.2 Firefox 接收到 cookie 并询问用户该怎么做。

**警告：**由于 cookie 作为 HTTP 头的一部分发送，因此必须在发送任何超文本标记语言（HTML）内容之前创建它们（除非你使用输出缓冲）。否则，你会收到如图 6.3 所示的错误消息。

![](img/2862989e5dc7f1b1d0bc64321737f084_180_0.png)

图 6.3 Cookie 必须在任何 HTML 内容之前发送。

注意：通常，PHP 会处理 cookie 值中的特殊字符转义（URL 格式）。然而，可以通过发送原始 cookie 数据手动执行此操作。为此，函数 `setrawcookie()` 接受与 `setcookie()` 相同的参数，但不编码 cookie 的值。你必须手动执行此操作，使用函数 `urlencode()`。

## 读取 Cookie

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

读取 Cookie（getcookie.php）

服务器可以访问的所有 cookie（并非浏览器中存储的所有 cookie！）都可以在超全局数组 `$_COOKIE` 中获取。`foreach` 循环会读取所有 cookie，并将它们以 HTML 表格的形式发送给客户端。

## 设置（合理的）过期日期

```php
<?php
    setcookie('version', phpversion(), time() + 
    21*24*60*60);
?>
```

已尝试发送 cookie。

*设置具有相对过期日期的 Cookie*

*（setcookie-expiry.php）*

cookie 的过期日期是 `setcookie()` 的第三个参数。它是一个整数值：因此，必须使用时间戳的纪元值。第 3 章“日期与时间”包含大量关于如何处理此类信息的内容。

通常，为 cookie 设置相对的过期日期（如“三周后”）而非绝对日期（如“2012 年 5 月底”）是更好的做法。如果使用绝对日期，你可能需要定期修改脚本，因为绝对过期日期可能很快就会到来。将过期日期设置得很遥远，例如 2030 年，也被认为是非常不专业的。收到此 cookie 的客户端到那一年几乎肯定不会再启动了。

因此，请使用相对日期。PHP 函数 `time()` 会获取当前的纪元值；然后加上你希望 cookie 存活的秒数。本段开头的代码设置了一个存在三周的 cookie。

## 设置客户端特定的过期日期

```
setcookie('version', phpversion(),
$_GET['time'] + 21*24*60*60)
```

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

已尝试发送 cookie。

*设置具有特定过期日期的 Cookie*

*（setcookie-specific.php）*

请记住，cookie 何时过期的决定是在客户端做出的，使用的是客户端的时钟设置。因此，如果客户端的日期不正确（这是你无法从服务器端控制的事情），你的 cookie 可能会比你预期的更早过期。因此，不要试图设置仅存活一小时左右的 cookie；像夏令时（DST）这样的小事就可能破坏你的计划。

不过，借助一点 JavaScript，就有可能避开这个陷阱。下面清单中的代码是客户端 JavaScript 代码，它将当前时间（客户端）确定为纪元值，并将其发送到服务器端脚本 `setcookie-specific.php`。PHP 的 `time()` 函数与 JavaScript 的 `getTime()` 方法之间的主要区别在于，后者返回自 1970 年 1 月 1 日以来的毫秒数，而前者只使用秒数。因此，JavaScript 值必须首先除以 1,000 并向下取整。

此文件的代码见本段开头：传输的值被用作计算相对 cookie 过期日期的基础：

```html
<script type="text/javascript">
var epoch = (new Date()).getTime();
epoch = Math.floor(epoch / 1000);
location.replace("setcookie-specific.php?time=" +
epoch);
</script>
```

*使用 JavaScript 将本地时间信息传输到服务器（setcookie-specific.html；节选）*

## 删除 Cookie

```php
<?php
setcookie('version', '', time() -
10*365*24*60*60);
?>
```

已尝试删除 cookie。

*删除 Cookie（deletecookie.php）*

删除 cookie 的一种直观方法是将其值设置为空字符串。然而，cookie 仍然存在，只是没有值。更好的方法是再次发送一个同名的 cookie，但提供一个已经过去的过期日期。同样，必须考虑本地时钟设置不正确的情况，所以使用一个非常早的过期日期（例如，距今十年前）。此清单实现了这一点，并删除了前面清单发送的 `version` cookie。这里结合了两种方法：cookie 值被设置为空字符串，过期日期则设在过去。图 6.4 显示了结果：浏览器试图将过期日期设置为当前时间来删除 cookie；因此，下一秒它就会消失。

![](img/2862989e5dc7f1b1d0bc64321737f084_184_0.png)

图 6.4 该 cookie 将被删除（如果用户接受它）。

**警告：** 如果你试图将过期日期设置为 0，PHP 会直接跳过这个参数；因此这不起作用。你必须提供一个正参数，即使是 1 也可以。

## 让 Cookie 可供多个域访问

```php
<?php
setcookie('version', phpversion(), 0,
'.example.com');
?>
```

已尝试发送 cookie。

*设置 Cookie 的域（setcookie-domain.php）*

服务器发送的 `Set-Cookie` 标头的组成部分之一是可访问此 cookie 的域。如果没有特别发送，此值默认为发送 cookie 的域。将此域设置为完全不同的值（例如，广告服务器的域[所谓的第三方 cookie；用于尝试生成用户画像]）并不总是有效，因为许多浏览器允许用户专门禁用这种功能。（图 6.5 展示了 Netscape 4.x 浏览器中的一个示例，即使在那个“史前”鼎盛时期，它也能够拦截不使用源域的 cookie。）

![](img/2862989e5dc7f1b1d0bc64321737f084_186_0.png)

图 6.5 即使是 Netscape 4.x 也允许你拦截不使用源域的 cookie。

然而，有时在三级域或子域（例如 `www.example.com`、`store.example.com` 和 `ssl.example.com`）上需要使用 cookie。拥有许多子域的大型网站（如 Amazon 和 eBay）要求支持所有顶级域（TLD）。要实现这一点，必须设置 cookie 的域——即 `setcookie()` 的第四个参数。诀窍来了：只要包含两个点，所有域名都是有效的。因此，如果将域设置为 `.example.com`，则 `example.com` 的所有三级域都可以访问此 cookie。但有一个问题：`http://example.com/` 上的页面无法访问此 cookie。因此，你可能想尝试将域设置为 `example.com`；但这不符合规范，而且可能并非所有浏览器都支持。

## 检查客户端是否支持 Cookie

```
if (isset($_COOKIE['test_temp'])) {
    'supports' : 'does not support';
}
if (isset($_COOKIE['test_persist'])) {
    'supports' : 'does not support';
}
```

```php
<?php
    if (isset($_GET['step']) && $_GET['step'] == '2')
    {
        $test_temp = isset($_COOKIE['test_temp']) ?
            'supports' : 'does not support';
        $test_persist = isset($_COOKIE['test_persist'])
            ? 'supports' : 'does not support';
        setcookie('test_temp', '', time() -
            365*24*60*60);
        setcookie('test_persist', '', time() -
            365*24*60*60);
        echo "Browser $test_temp temporary cookies.<br />";
        echo "Browser $test_persist persistent cookies.";
    } else {
        setcookie('test_temp', 'ok');
        setcookie('test_persist', 'ok', time() +
            14*24*60*60);
        header("Location: {$_SERVER['PHP_SELF']}?step=2");
    }
?>
```

*测试浏览器的 Cookie 配置（cookietest.php）*

记住 cookie 的发送方式：首先，服务器将 cookie 作为 HTTP 响应的一部分发送给客户端。在下一个请求中，如果客户端接受了 cookie，就会将其发送回来。因此，调用 `setcookie()` 然后检查 `$_COOKIE` 的内容是行不通的。你必须等待下一个 HTTP 请求。

不过，你可以使用 `header()` 强制客户端发出第二个请求。在第一个请求中，你设置 cookie；在第二个请求中，你检查是否生效。

在前面的代码中，设置了两个 cookie，一个是临时 cookie，一个是持久 cookie——因为有些浏览器可以配置为只接受其中一种 cookie，而不接受另一种。然后，使用 `header()` 和 `Location:` HTTP 头完成重定向，并检查 cookie 是否存在。

当然，你应该将浏览器配置为在收到 cookie 时显示消息窗口；这会让调试容易得多。

## 在一个 Cookie 中保存多个数据

```
setcookie('cookiedata', serialize($cookiedata));
```

```php
<?php
function setCookieData($arr) {
    $cookiedata = getAllCookieData();
    if ($cookiedata == null) {
        $cookiedata = array();
    }
    foreach ($arr as $name => $value) {
        $cookiedata[$name] = $value;
    }
    setcookie('cookiedata',
```

```php
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

### 将多个值保存到一个 Cookie 中的辅助库

(getCookieData.inc.php)

通常，一个 cookie 只有一个值：一个字符串。因此，要在 cookie 中存储多个数据，就必须使用多个 cookie。然而，这可能会造成一些问题（例如，每个域的 cookie 数量限制为 20）。因此，尝试将多个数据保存到一个 cookie 中可能是有意义的。对于此，数组非常有用。只要记住 cookie 只能包含字符串，因此我们需要使用序列化来准备数据。

为此，你可以编写一个库，它与第 2 章“使用数组”中用于将表单数据保存到 cookie 的库非常相似。一个名为 `cookieData` 的 cookie 以关联数组的形式包含所有值。函数 `getCookieData()` 返回一个特定值，而 `setCookieData()` 接受一个数组并将其内容写入 cookie。前面的列表显示了此库的完整代码。

以下列表使用此库来实现前一章节中的 cookie 测试：



```php
<?php
    require_once 'getCookieData.inc.php';

    if (isset($_GET['step']) && $_GET['step'] == '2')
{
    $test = (getCookieData('test') === 'ok') ?
        'supports' : 'does not support';
    echo "Browser $test cookies.";
} else {
    setCookieData(array('test' => 'ok'));
    header("Location:
{$_SERVER['PHP_SELF']}?step=2");
}
?>
```

*使用辅助库测试浏览器 Cookie 配置 (`cookietest-serialize.php`)*

### 保存用户的语言偏好

```
setcookie('lang', $_SERVER['PHP_SELF'], time() + 10*24*60*60, '/');
```

```php
<?php
if (!isset($_COOKIE['lang']) ||
    $_COOKIE['lang'] != $_SERVER['PHP_SELF']) {
    setcookie('lang', $_SERVER['PHP_SELF'],
        time() + 30*24*60*60, '/');
}
?>
```

#### 将当前路径保存到 Cookie 中 (`saveLanguage.inc.php`)

许多网页都是多语言的。此外，它们通常是这样组织的，每个本地化部分都位于自己的目录中，类似于以下方法：

- 英文版本位于 `en` 目录中。
- 西班牙语版本位于 `es` 目录中。
- 法语版本位于 `fr` 目录中。

你可以通过几种不同方式检测用户的语言：

- 通过尝试将客户端 IP 地址与地理区域关联
- 通过读取 `Accept-Language` HTTP 头来确定首选语言
- 通过询问用户

虽然所有这些方法或多或少都有效，但最后一种（或几种方法的组合）被认为是最用户友好的。因此，你确实需要一个主页，提供指向所有三个版本的链接。这是简单的 HTML，如下所示：

```
<a href="en/index.php">English version</a><br />
<a href="es/index.php">Versión español</a><br />
<a href="fr/index.php">Version française</a>
```

*主页链接到各种语言版本 (`multilingual.php`; 摘录)*

现在，每个语言目录都有一个特定语言的 `index.php` 文件。在此文件中，代码包含自本节开头处的列表。这会检查是否已存在语言 cookie。如果没有，它会尝试使用当前路径（从 `$_SERVER['PHP_SELF']` 获取）设置一个 cookie。

**注意：** 重要的是将 cookie 的路径设置为 Web 服务器的根目录。否则，路径默认为当前路径，并且 cookie 只能在当前目录及其子目录中读取，而不能在主页上读取。

最后，你必须在主页上检查 cookie 是否存在，如果存在，则将用户重定向到适当的页面。为此，你必须在 `multilingual.php` 页面的顶部添加以下代码：

```
<?php
if (isset($_COOKIE['lang']) && $_COOKIE['lang'] != '' ) {
```

```
header("Location: {$_COOKIE['lang']}");
}
?>
```

#### 检查语言 Cookie (`multilingual.php`; 摘录)

### 理解会话

最初，会话是用户对网站的一次访问。他点击几个链接，查看几页，然后离开。这定义了一个会话。换句话说，如果用户在一段时间内（例如 20 分钟）未向网站请求任何数据，则会话结束。

HTTP 不知道任何会话机制：该协议是无状态的。然而，PHP 带有内置的会话支持，使得使用会话变得相当容易。

会话创建后，PHP 会生成一个会话 ID（即标识会话的长字符串）。然后 PHP 为此会话创建一个文件或数据库条目。然后 PHP 应用程序可以将会话数据存储在会话中。这些数据随后写入会话文件或数据库。（共享内存是另一种但很少使用的选项。）

因此，客户端和服务器之间必须传输的唯一东西是会话 ID。所有其他与会话相关的其他数据都驻留在服务器上。因此，没有敏感数据会被不必要地多次通过线路发送。

PHP 会话机制的配置完全在 `php.ini` 配置文件的 `[session]` 部分中触发。默认设置可能不适合所有应用程序，因此接下来的几节涵盖了一些可能的配置。

#### 会话存储位置

通常，会话数据存储在文件中。这些文件的位置由 `php.ini` 指令 `session.save_path` 设置。当然，此路径必须 (a) 存在且 (b) 对 PHP 进程（通常是 Web 服务器的进程）可读可写。否则，会话信息无法存储。

然而，当你有大量用户，因此有大量会话时，PHP 不应将所有会话文件放在一个目录中，因为这可能会导致一些严重的性能问题。以下语法允许 PHP 将会话数据移动到多个子目录中：

```
session.save_path = "n;/tmp"
```

这会在 `/tmp` 目录内创建最多 n 级的子目录。然而，这些子目录必须存在，以便 PHP 的会话机制可以写入其中；为此，`ext/session` 目录中存在 shell 脚本 `mod_files.sh`。

当然，只有 Web 服务器应被允许读取此目录；否则，系统中的其他用户可能能够读取包含可能敏感数据的会话信息。

#### 如何维护会话状态

会话 ID 必须随每次响应发送到浏览器，并且——更重要的是——必须随每次请求发送回服务器。最简单的方法是使用 cookie。

然后 PHP 向客户端发送一个名为 `PHPSESSID` 的 cookie（可通过指令 `session.name` 更改）。然而，要实现这一点，必须设置以下 `php.ini` 指令：

```
session.use_cookies = 1
```

然而，如果客户端不支持 cookie 会怎样？然后，第二种机制会发挥作用，形式如下指令：

```
session.use_trans_sid = 0
```

然后，PHP 自动回退到一种模式，其中会话 ID 会自动附加到所有 URL。这可能会产生一些潜在的安全风险（例如会话固定和会话劫持）。大多数知名电子商务网站已停止使用此机制（例如 Amazon）。当会话中未存储个人数据时，你可能仍想使用此功能。

要能够使用 `session.use_trans_sid`，PHP 必须使用 `enable-trans-sid` 开关编译，这对于 Windows 和 Mac OS X 二进制文件是自动完成的。

另一个选项是只允许 cookie，而不是在统一资源定位符（URL）中使用会话 ID。为此，你可以使用以下 `php.ini` 指令：

```
session.use_only_cookies = 1
```

注意：URL 中的会话 ID 通常是不好的事情。例如，因为人们可以书签保存此信息，如果包含此类信息，一些搜索引擎将不会收录您的网站。如今几乎每个主要电子商务网站都需要 cookie。

#### 激活会话

##### `session_start()`

```php
<?php
    session_start();
    echo 'Sessions activated.';
?>
```

*激活会话 (`session_start.php`)*

使用会话管理始终需要资源，因此会消耗性能。所以，会话必须被激活。因为 cookie 可能是其中的一部分，所以必须在任何 HTML 内容发送到客户端之前完成。这可以通过两种方式实现：

- 使用 `php.ini` 指令 `session.auto_start = 1` 全局激活会话。
- 使用函数 `session_start()` 按脚本激活会话。

从性能角度来看，后一种选项是最好的。

### 读取和写入会话

```php
<?php
    session_start();
    echo 'Sessions activated.<br />';
    $_SESSION['version'] = phpversion();
    echo 'Session data written.<br />';
    echo "Session data read: {$_SESSION['version']}.";
    //could also be used on another page
?>
```

*读取和写入会话 (`session_readwrite.php`)*

所有会话数据都通过 `$_SESSION` 数组从 PHP 脚本访问。因为数据本身存储在服务器端，所以您可以写入会话数据并在下一个 PHP 语句中读取它，而不需要像 cookie 那样进行服务器往返。只需记住先调用 `session_start()`，然后访问 `$_SESSION`。前面的列表创建了一个会话文件，如图 6.6 所示。

![](img/2862989e5dc7f1b1d0bc64321737f084_197_0.png)

图 6.6 前述代码创建的会话文件的内容。

### 关闭会话

##### `session_destroy()`

```php
<?php
session_start();
echo 'Before: <pre>';
print_r($_SESSION);
echo '</pre>After: <pre>';
session_destroy();
print_r($_SESSION);
echo '</pre>';
?>
```

移除所有会话数据 (`session_destroy.php`)

在某些情况下（例如用户注销时），应删除所有会话数据并关闭会话。当然，可以使用 `foreach` 遍历 `$_SESSION`，然后将每个值设为空字符串或 `null`，但有更快的方法：调用 `session_destroy()`。之后，当前会话中的所有数据将被销毁，正如函数名所暗示的那样。

### 更改会话 ID

##### `session_regenerate_id()`

```php
<?php
ob_start();
session_start();
echo 'Old: '. session_id();
session_regenerate_id();
echo '<br />New: ' . session_id();
ob_end_flush();
?>
```

*更改会话 ID (`session_regenerate_id.php`)*

针对使用会话保护的网站的常见攻击之一是用户的会话 ID 以某种方式被窃取（例如，通过分析 HTTP 请求中的 `HTTP_REFERER` 条目），然后被用来冒充该特定用户。这很难防范，但使攻击者更难的一个便捷方法是，只要发生“重要”事件，例如用户登录时，就更改会话 ID。例如，亚马逊要求已通过 cookie 进行身份验证的用户在想要下单时再次登录。

在这种情况下，函数 `session_regenerate_id()` 只是更改当前会话 ID，但保留所有数据不变。这在前面的代码中显示，其中使用 `session_id()` 函数检索当前会话 ID（旧的和新的）。图 6.7 显示了此脚本的可能输出。

**注意：** 此代码使用输出缓冲— `ob_start()` 和 `ob_end_flush()`—因为 `session_regenerate_id()` 也必须在任何 HTML 输出发送到客户端之前调用。

![](img/2862989e5dc7f1b1d0bc64321737f084_200_0.png)

图 6.7 两个会话 ID（一个旧的，一个新的）

### 实现自定义会话管理

```
session_set_save_handler(
'sess_open', 'sess_close', 'sess_read',
'sess_write', 'sess_destroy', 'sess_gc');
```

*自定义会话管理 (`session_mysql.inc.php`; 摘录)*

不将会话数据存储在文件中有一些很好的理由。性能可能是其中一个问题，安全性是另一个问题。存储会话信息的另一种方法是使用数据库。为此，您只需要一个名为 `sessiondata` 的数据库表，包含三列。名称可能会有所不同，但本章即将出现的代码列表中使用以下名称：

- 列 `id`（主键）的类型为 `VARCHAR(32)`，包含会话 ID。
- 列 `data` 的类型为 `TEXT`，包含会话数据。
- 列 `access` 的类型为 `VARCHAR(14)`，包含对会话信息最近访问的时间戳。

使用哪种数据库并不重要。本章使用 MySQL 和 PHP5 的新 `mysqli` 扩展，但也可以轻松更改代码以适用于其他数据库。（请参阅第 8 章“使用 MySQL 数据库”和第 9 章“使用其他数据库”，了解有关使用 PHP 使用各种相关数据库的信息。）

您可以使用 PHP 函数 `session_set_save_handler()` 为 PHP 内部使用的所有相关六个会话操作提供自定义函数：

- 打开会话
- 关闭会话
- 读取会话变量
- 写入会话变量
- 销毁会话
- 清理（垃圾回收 [例如，从数据存储中删除旧的会话数据]）

对于这六个操作，以下列表包含从 MySQL 数据源读取和写入会话数据的代码。您只需要 PHP 5 并适当设置连接参数（服务器、用户名、密码）。然后，使用 `require_once` 包含此列表中的代码，然后像往常一样使用会话。在后台，PHP 然后将所有会话信息保存在数据库中，而不是文件系统中。



```php
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
        mysqli_real_escape_string($GLOBALS['sess_mysqli'], $id))
    );
    if ($row = mysqli_fetch_object($result)) {
        $ret = $row->data;
        mysqli_query(
            $GLOBALS['sess_mysqli'],
            sprintf('UPDATE sessiondata SET access=\'%s\' WHERE id=\'%s\'',
            date('YmdHis'),
            mysqli_real_escape_string($GLOBALS['sess_mysqli'], $id))
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

自定义会话管理 (`session_mysqli.inc.php`)

**注意：** 从 PHP 5.3 开始，你也可以使用内联匿名函数来设置这六个保存处理函数，如下所示：

```php
session_set_save_handler(
    function () {/* ... */},
    function () {/* ... */},
    function ($id) {/* ... */},
    function ($id, $data) {/* ... */},
    function ($id) {/* ... */},
    function ($timeout) {/* ... */}
);
```

**提示：** 下载包中的 `session.sql` 文件包含一个用于在 MySQL 中创建数据库表的 SQL 文件。文件 `session_mysqli_readwrite.php` 使用了前面列表中的代码，并在会话中保存了一些数据。

图 6.8 展示了数据写入后 session 表中的内容。

![](img/2862989e5dc7f1b1d0bc64321737f084_205_0.png)

图 6.8 会话数据现在存储在数据库中。

### 使用会话创建安全区域

```php
session_start();
if (!isset($_SESSION['authorized']) &&
    $_SESSION['authorized'] != '') {
    header("Location: login.php?url={$_SERVER['PHP_SELF']}");
}
```

*检查用户是否已通过身份验证* (`session_authentication.inc.php`)

会话是保护网站特定区域的绝佳方式。方法很简单：用户通过身份验证后，将此信息写入会话变量。在所有受保护的页面上，检查此会话变量是否存在。

你可以先检查会话变量。本节开头的代码必须通过 (`require_once`) 包含在所有仅供授权用户访问的页面中。

脚本 `login.php` 包含了前面的代码重定向用户的地址，其中包含一个 HTML 表单（另见图 6.9），并检查提供的数据是否正确；你可能需要添加自己的用户和密码，并且可能希望使用加密。你可能已经注意到，之前的 URL 作为 GET 参数提供。因此，如果可用，登录代码会将用户重定向回他们来自的页面：

```php
<?php
if (isset($_POST['user']) && $_POST['user'] == 'Damon' &&
    isset($_POST['pass']) && $_POST['pass'] == 'secret') {
    session_start();
    $_SESSION['authorized'] = 'ok';
    $url = (isset($_GET['url'])) ? $_GET['url'] : 'index.php';
    header("Location: $url");
}
?>
```

就是这样！下载包中的脚本 `secret.php` 包含一些相当机密的信息，并由前面两个列表中的代码保护。

![](img/2862989e5dc7f1b1d0bc64321737f084_207_0.png)

### 不使用会话创建安全区域

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

使用 HTTP 保护 PHP 页面 (`http_authentication.php`；摘录)

如果使用 PHP 的会话管理进行身份验证显得开销过大，你有另外两种选择：

- 配置你的 Web 服务器，使得只有授权用户才能访问某些文件或目录。例如，Apache 用户可以使用 `.htaccess` 文件；http://httpd.apache.org/docs/current/howto/htaccess.html 包含了一些关于此主题的有用信息。Microsoft IIS 提供了用于管理访问权限的图形用户界面（GUI），因此也可以这样做。

- 一种或多或少与平台无关的保护网站的方式是通过 HTTP 进行身份验证。如果你发送 HTTP 状态码 401（未授权），浏览器会提示客户端输入用户名和密码。然后，这些信息可以通过 `$_SERVER['PHP_AUTH_USER']` 和 `$_SERVER['PHP_AUTH_PW']` 获取——但是，只有当 PHP 作为服务器模块运行时才可用，而不是在通用网关接口（CGI）模式下。

然后你可以检查这些信息，并决定是再次发送 401 头还是显示页面的实际内容。前面的列表展示了该功能的实现。图 6.10 显示了用户名和密码的提示框。

![](img/2862989e5dc7f1b1d0bc64321737f084_209_0.png)

图 6.10 浏览器提示输入用户名和密码。

### PEAR 提供了什么？

以下 PHP 扩展和应用仓库（PEAR）包提供了与会话和 HTTP 身份验证相关的功能：

- Auth 实现了各种用户身份验证方式，从而保护 PHP 页面。

- HTTP_Session 基于 PHP 的会话机制，但提供了面向对象的会话信息访问方式。

## 使用服务器文件系统上的文件

尽管数据库非常常见，但使用文件系统来存储数据可能是一个真正的替代方案。通常，这种方式实现起来更容易。有时它更快，更重要的是，所有托管服务商都启用了文件访问，而数据库支持可能只提供在额外费用下。

PHP 通过一组特定的函数支持处理文件。使用包装器，同样的技术还可以通过超文本传输协议（HTTP）或文件传输协议（FTP）等协议访问远程数据，但这将在第 9 章“与他人通信”中详细讨论。

本章涵盖标准任务，如读写文件，以及高级任务，如以 ZIP 或 BZ2 格式存档文件。许多这些任务可以用不同但同样可用的方式解决，因此你确实有选择的自由。

### 打开和关闭文件

```php
<?php
$fp = @fopen('file.txt', 'at');
fclose($fp);
```

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

*打开（和关闭）文件* (`fopen.php`)

对于大多数文件系统函数，必须首先打开文件。函数 `fopen()` 正是执行此操作，并返回所谓的文件句柄，即指向文件的指针。这个文件句柄可以在后续函数中使用，例如从文件读取信息或向文件写入信息。

`fopen()` 至少需要两个参数：

- 文件名

- 访问文件时使用的文件模式

文件模式参数非常重要。这是一个由一个或多个字符组成的字符串。第一个字符是 `a`、`r`、`w` 或 `x` 之一；之后，可以使用一个或多个特殊修饰符。表 7.1 显示了所有模式。

**表 7.1 PHP 文件函数的文件模式**

| 模式 | 描述 |

|------|------|

| a | 打开文件以追加（写入）数据；如果文件不存在则创建它 |

| a+ | 与模式 a 相同，但额外具有对文件的读取权限 |

| r | 打开文件以读取数据 |

| r+ | 与模式 r 相同，但额外具有对文件的写入权限 |

| w | 打开文件以写入数据，清除其内容；如果文件不存在则创建它 |

| w+ | 与模式 w 相同，但额外具有对文件的读取权限 |

| x | 创建文件以写入数据；如果文件已存在则发送 `E_WARNING` |

| x+ | 与模式 x 相同，但额外具有对文件的读取权限 |

因此，修饰符 `+` 总是为文件模式添加缺失的读取或写入权限。还有其他修饰符。PHP 会很好地判断文件是文本文件还是二进制文件，并适当转换特殊字符。如果你在文件模式后附加 `b`，则强制 PHP 以二进制文件方式打开文件；例如，文件模式 `rb` 以二进制模式打开文件进行读取。

另一个特殊修饰符可能对 Windows 用户很有用：`t`。如果将其附加到文件模式，所有 `\n` 换行符都会转换为 `\r\n`，正如 Windows 应用程序可能期望的那样。

`fopen()` 返回文件句柄，如果打开文件失败则返回 `false`。然而，你应该使用 `@` 字符抑制任何潜在的错误消息。

一旦文件不再使用，就应该关闭它。PHP 会在脚本终止时自动关闭所有打开的文件；然而，为了尽可能高效地利用系统资源，应尽早关闭文件以释放内存并加速系统。为此，使用 `fclose()` 并提供文件句柄作为参数。

本节开头的代码同时使用了 `fopen()` 和 `fclose()`。

运行脚本后，会创建一个名为 `file.txt` 的文件。

**注意：** 为了让本示例（以及本章中的其他示例）正常工作，你必须确保 PHP 脚本具有访问文件所需的适当权限。通常，Apache 要么在特殊用户账户下运行（如 UNIX/Linux 上的 `nobody`、`apache` 或 `www-data`），要么在普通用户账户下运行（Windows）。使用 `chmod` 相应地设置访问权限。

Microsoft IIS（互联网信息服务）在名为 `IUSR_<机器名>` 的特殊来宾账户下运行 PHP 脚本。你可以使用图 7.1 中显示的图形用户界面来调整文件或目录的访问设置。

**提示：** 为了避免在尝试访问不存在的文件时出错，你可以使用函数 `file_exists()`，如果给定的文件名存在，该函数返回 true。

```php
if (file_exists('file.txt')) {
    // ...
}
```

![](img/2862989e5dc7f1b1d0bc64321737f084_216_0.png)

Figure 7.1 允许 IIS 用户访问文件或目录

### 从文件读取

```php
echo file_get_contents('file.txt');
```

读取文件数据时，PHP 提供了多种可能性。最简单的方法可能是将文件一次性全部读入，然后输出给用户。

函数 `file_get_contents()` 以字符串形式返回文件（或流）的内容，以便进一步处理。以下代码读取名为 `file.txt` 的文件并打印其内容。该函数是二进制安全的，因此不需要（或不能）使用文件模式：

```php
<?php
echo file_get_contents('file.txt');
?>
```

`file()` 函数的工作方式与 `file_get_contents()` 相同，但返回文件内容为数组：每个元素是文件中的一行（包括换行符）。以下代码将此数组转换为字符串并发送到浏览器。函数 `implode()` 将数组元素粘合在一起；请参阅第 2 章，“使用数组”：

```php
<?php
echo implode('', file('file.txt'));
?>
```

为了获得最大灵活性，可以使用手动方式；然而，对于文本文件，这通常不是必需的。用 `fopen()` 打开文件，然后只要返回数据就调用 `fgets()`（这里使用 while 循环很方便）并输出数据。`fgets()` 返回其第二个参数提供的字符数，但最多为当前行结束前的所有字符：

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

*逐行将文件内容发送到浏览器*



### 写入文件

```php
file_put_contents('file.txt', '--> This text file contains\nsome random text. <--');
```

```php
<?php
file_put_contents('file.txt',
    "--> This text file contains\nsome random text.
<--");
echo 'File written.';
?>
```

`file_put_contents.php`

写入文件与从文件中读取一样简单——如果您使用的是 PHP 5 或更高版本。然后，函数 `file_put_contents()` 直接将数据写入文件，并且是二进制安全的。调用函数后，文件将被关闭。上述代码将数据写入文件。

然而，上述代码会覆盖现有文件。如果您想追加数据（因此模拟文件模式 `a`），则首先必须读取文件的数据：

```php
<?php
function file_append_contents($filename, $data) {
    $olddata = @file_get_contents($filename);
    return file_put_contents($filename,
        "$olddata$data");
}

file_append_contents('file.txt',
    "\n--> This text file contains\neven more random text. <--");
echo 'Data appended to file';
?>
```

`file_append_contents.php`

**提示：** 提供第三个参数给 `file_put_contents()` 以追加数据而不是覆盖文件，甚至更简单：

```php
file_put_contents($filename, $data, FILE_APPEND);
```

### 锁定文件

```php
flock($fp, LOCK_EX);
```

```php
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

`flock.php: excerpts`

在读取和写入文件时，您必须考虑并发性。如果两个进程同时尝试访问文件会怎样？为了避免一个进程写入而另一个进程读取时出现问题，您必须锁定文件。这是通过 PHP 函数 `flock()` 完成的。

第一个参数是文件句柄；第二个参数是要使用的锁定类型。以下选项可用：

- `LOCK_EX`—用于写入的独占锁

- `LOCK_NB`—非阻塞锁

- `LOCK_SH`—用于读取的共享锁

- `LOCK_UN`—释放锁

上述代码包含来自上一节的自定义 `file_put_contents()` 函数的更新版本，这次使用独占锁。

### 使用相对路径进行文件访问

```php
dirname(__FILE__)
basename(__FILE__)
```

```php
<?php
$directory = dirname(__FILE__);
$filename = basename(__FILE__);
print "This script is called $filename and resides
in $directory.";
?>
```

`pathinfos.php`

通常，文件是相对于文档路径打开（或搜索）的。如果您在 Windows 下将 PHP 用作 ISAPI 模块，则 `php5.dll` 或 `php5ts.dll` 的位置可能相关。为了确保您搜索的是当前脚本的路径，可以使用两步方法：

- 常量 `__FILE__` 包含当前脚本的完整路径。

- 函数 `dirname()` 确定路径的目录名称部分。

要使用相对路径，您现在可以调用 `dirname(__FILE__)` 然后附加相对路径，同时考虑目录分隔符字符，在 UNIX/Linux 上是 `/`，在 Windows 上是 `\`，在 Mac OS X 上是 `:`。PHP 在其 `DIRECTORY_SEPARATOR` 常量中告诉您系统的默认值。

`dirname()` 的姊妹函数是 `basename()`：它确定路径的文件名部分。

本节开头的列表使用 `basename()` 和 `dirname()` 以及 `__FILE__` 来确定有关当前路径的信息：目录和文件名。图 7.2 显示了脚本的输出。

![](img/2862989e5dc7f1b1d0bc64321737f084_221_0.png)

Figure 7.2 检测脚本的名称及其目录

### 避免文件访问中的安全陷阱

一点非常重要：如果您使用 PHP 处理文件，请避免从外部检索文件名

### 处理 CSV 数据

```php
fgetcsv($fp, 4096)
```

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

`fgetcsv.php`

CSV 是一种文件格式，代表逗号分隔值。许多电子表格应用程序可以将数据导出为 CSV 文件。似乎使用 `explode()` 将 CSV 值转换为数组很容易；然而，这实际上非常复杂。如果值中包含逗号怎么办？那么内容会被双引号包围，这使得使用 `explode()` 变得困难。

如（几乎）总是那样，PHP 项目已完成了大部分工作并提供了 `fgetcsv()`。此函数的工作方式与 `fgets()` 相同；然而，它将行转换为数组，以逗号（或第三个参数中提供的任何其他字符）分隔内容。

`fgetcsv()` 的第二个参数是 CSV 文件中行的最大长度。在 PHP 5 中这是可选的。因此您需要检查 CSV 文件中最长行的长度；否则，数据将被截断。

本节开头的代码读取 CSV 文件并将其作为 HTML 表格输出。这是通过循环中使用以下代码完成的：

```php
$line = fgetcsv($fp, 4096);
echo '<tr><td>';
echo implode('</td><td>', $line);
echo '</td></tr>';
```

这在 HTML 表格中创建一行：`<tr><td>...</td></tr>`。

图 7.3 同时显示了原始电子表格文件（在 OpenOffice.org 中）和浏览器中的结果。

![](img/2862989e5dc7f1b1d0bc64321737f084_224_0.png)

Figure 7.3 OpenOffice.org 中的 CSV 电子表格以及浏览器中的结果 (`fgetcsv.php`; excerpt)

**注意：** 在本节开头的代码中，输出未使用 `htmlspecialchars()` 进行清理——在这种情况下是为了使代码简短。然而，根据您的数据，您应考虑对 `fgetcsv()` 返回的数组的所有元素运行 `htmlspecialchars()`。

对于写入 CSV 文件，PHP 提供了一个姊妹函数 `fputcsv()`。您提供文件指针和值数组，PHP 会完成其余工作，包括转义特殊字符。该函数在 PHP 5.1 中引入。基本上，您只需用逗号连接所有数组元素。您还必须处理元素内的逗号，因此您用双引号包围所有值。如果元素包含双引号，则必须转义它们。然而，这不是使用反斜杠完成的，而是通过重复引号完成的。以下是 CSV 数据有效行的示例：

```csv
Quote,"And she said: ""No."" ...",Unknown
```

以下是旧版 PHP 的 `fputcsv()` 代码：

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
        fwrite($fp, implode($separator, $line) .
        "\r\n");
    }
}
```

下面的代码使用 `fputcsv()` 函数手动创建之前使用过的 CSV 文件：

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

`fputcsv.php; 摘录`

这段代码创建文件 `usage.csv`，其内容如下：

April 2005,"19,720,597","1,310,181"

January 2005,"18,455,683","1,317,871"

December 2004,"17,826,404","1,318,739"

### 解析 INI 文件

```php
parse_ini_file('php.ini', true);
```

```php
<?php
echo '<xmp>' .
    print_r(parse_ini_file('php.ini', true), true) .
    '</xmp>';
?>
```

`parse_ini_file.php`

从 INI 文件读取信息

另一种非常知名的文件格式是 INI 文件格式。它在 Windows 世界中曾被广泛使用，但今天也驱动着像 PHP 这样复杂软件产品的配置。例如，查看 `php.ini`。以下是默认 `php.ini` 的（修改过）摘录，很好地展示了 INI 文件的结构：

```
[mail function]
; For Win32 only.
; SMTP = localhost
; For Unix only. You may supply arguments as well
; (default: "sendmail -t -i").
sendmail_path =
```

因此，存在以方括号中的节标题开头的节、以分号开头的注释，以及格式为 `name=value` 的设置。PHP 函数 `parse_ini_file()` 现在读取此类文件并将其创建为数组：每个节都是一个子数组，在这些子数组中可以找到 INI 文件中指令的名称和值。本段开头的代码执行此操作（如果合适，请记住更改 `php.ini` 的路径），图 7.4 显示了输出。

![](img/2862989e5dc7f1b1d0bc64321737f084_228_0.png)

图 7.4 `php.ini` 的内容作为多维数组 (`parse_ini_file.php`; 摘录)。

**TIP：** 如果你想避免 INI 文件中按节分组，只需省略第二个参数 `parse_ini_file()`；那么，你会一次性获得所有设置。

`parse_ini_file('php.ini');`

### 获取文件信息

```php
<?php
$filename = __FILE__;
$data = array(
    'fileatime' => fileatime($filename),
    'filegroup' => filegroup($filename),
    'filemtime' => filemtime($filename),
    'fileowner' => fileowner($filename),
    'filesize' => filesize($filename),
    'is_dir' => var_export(is_dir($filename), true),
    'is_executable' => var_export(is_executable($filename), true),
    'is_file' => var_export(is_file($filename), true),
    'is_link' => var_export(is_link($filename), true),
    'is_readable' => var_export(is_readable($filename), true),
    'is_uploaded_file' => var_export(is_uploaded_file($filename), true),
    'is_writable' => var_export(is_writable($filename), true)
);

echo '<table>';
foreach ($data as $function => $result) {
    echo "<tr><td>$function</td><td>$result</td></tr>";
}
echo '</table>';
?>
```

`fileinfos.php`

读取有关文件的信息

使用 PHP 访问目录和文件信息相当不寻常——至少在绝大多数 PHP 脚本通过 HTTP 在 Web 服务器上运行而不是使用命令行界面 (CLI) 或 PHP 的情况下。然而，PHP 提供了各种辅助函数来提供有关文件的信息。它们大多数只是调用相关的操作系统函数。

下面的列表显示了在这方面最相关的辅助函数：

- `fileatime($filename)`—对文件的最后访问

- `filegroup($filename)`—拥有文件的组

- `filemtime($filename)`—文件的最后更改

- `fileowner($filename)`—文件所有者

- `filesize($filename)`—文件的大小

另一组辅助函数也接受文件名，这意味着在使用这些函数之前无需打开文件：

- `is_dir($path)`—路径是否为目录

- `is_executable($filename)`—文件名是否可执行

- `is_file($path)`—路径是否为（常规）文件

- `is_link($filename)`—文件名是否为符号链接

- `is_readable($filename)`—文件是否可读

- `is_uploaded_file($path)`—路径是否是通过 HTTP 上传的文件（参见第 5 章，“记住用户（Cookies 和 Sessions）”）

- `is_writable($filename)`—文件是否可写

图 7.5 包含本段开头代码的结果。

![](img/2862989e5dc7f1b1d0bc64321737f084_231_0.png)

图 7.5 有关当前脚本的信息 (`fileinfos.php`)

### 复制、移动和删除文件

```php
copy($filename, $tempname1);
rename($tempname1, $tempname2);
unlink($tempname2);
```

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

`copymovedelete.php`



method `read()` 遍历条目列表。之前的代码正是这样做的，并打印出当前目录的内容。

请注意，两个目录条目 `.`（当前目录）和 `..`（如果不在根目录，则为父目录）会被打印出来。

### 使用 PHP 流

```
<?php
$filename = __FILE__;
$zipfile = "$filename.zip";

$data = file_get_contents(__FILE__);
echo 'Loaded file (size: ' . strlen($data) . ')<br />';

file_put_contents("compress.zlib://$zipfile", $data);
echo 'Zipped file (new size: ' . filesize($zipfile) . ')<br />';

$data = file_get_contents("compress.zlib://$zipfile");
echo 'Original file size: ' . strlen($data) . '.';
?>
```

*压缩和解压缩文件 (zip.php; 摘录)*

在 PHP 中引入了 PHP 流的概念。自那时起，所有类型资源都有一个共同分母：文件、HTTP 和 FTP 数据，甚至归档文件格式。你可以在第 11 章“与他人通信”中找到关于此网络方面的更多详细信息。本章仅挑选了一些特定于文件的特性：压缩流。

其中之一可用于使用 ZIP 文件。伪协议 `compress.zlib://` 可用于像访问常规文件一样访问 ZIP 文件。为此工作，你需要在 UNIX/Linux 下使用配置开关 `-with-gzip`；Windows 系统已包含所需的库。然后，你可以使用文件——例如，使用 `file_get_contents()` 和 `file_put_contents()`。

前面的代码加载当前文件（使用 `file_get_contents()`），对其进行压缩，并将其写入硬盘（使用 `file_put_contents()`）。然后，它读取压缩文件（使用 `file_get_contents()`）并比较文件大小。

在测试时，代码成功将文件从 729 字节压缩到 336 字节。

另外，你可以使用 PHP 内置的 ZIP 函数，它由 http://zzip.lib.sourceforge.net/ 的 ZZLib 库的包装器实现。不幸的是，它只能从 ZIP 文件读取数据，但也支持归档中的多个文件（当使用流包装器 `compress.zlib://` 时，你首先必须 tar 数据以支持多个文件）。

要安装，在 Windows 下在 `php.ini` 中使用 `extension=php_zip.dll`，或使用 `-with-zip` 配置 PHP，提供 ZZLib 的路径。使用此扩展必须采取以下步骤：

- 1. 使用 `zip_open()` 打开归档。

- 2. 使用 `zip_read()` 遍历归档的条目。

- 3. 使用 `zip_entry_open()` 和 `zip_entry_read()` 读取特定文件。

下面的代码显示 ZIP 归档的内容并确定所有条目的名称和文件大小：

```
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

*使用 ZZLib 解压缩文件 (zziplib.php)*

### 使用 Bzip2 归档

```
file_put_contents("compress.bzip2://$bzip2file", $data);
```

```
<?php
    $filename = __FILE__;
    $bzip2file = "$filename.bz2";

    $data = file_get_contents(__FILE__);
    echo 'Loaded file (size: ' . strlen($data) . '
        <br />';

    file_put_contents("compress.bzip2://$bzip2file",
        $data);
    echo 'Bzipped file (new size: '
        . filesize($bzip2file) . ')<br />';
```

#### 使用 HTTP 请求返回文件

```php
$filename = 'httpfile.zip';
header("Content-Disposition: attachment; filename = $filename");
```

```php
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

*使用 HTTP 发送文件 (httpfile.php)*

当 PHP 脚本需要返回（可下载的）文件而不是 HTML 时，必须发送正确的 HTTP 头：

- `Content-Disposition` 用于文件的（建议）名称

- `Content-Length` 用于文件大小

- `Content-Type` 用于文件的 MIME 类型

前面的代码读取 ZIP 文件并将其发送给客户端；图 7.6 显示了它在浏览器中的结果。

![](img/2862989e5dc7f1b1d0bc64321737f084_239_0.png)

**图 7.6** 浏览器想要保存文件。

### PEAR 提供了什么？

以下 PHP 扩展和应用程序仓库（PEAR）包提供了可用于处理文件和流的功能：

- `File` 提供了一些文件访问的辅助函数，其中一些已弃用，取而代之的是较新 PHP 版本中的新功能。

- `File_Find` 在路径中搜索特定文件或模式。

- `File_SearchReplace` 在文件中执行搜索和替换。

- `Stream_Var` 允许你将变量保存到流中，以便像访问文件或流一样访问它们。

## 使用 MySQL 数据库

PHP 的主要优势之一是对大量数据库的支持。很常见的是，PHP 和 MySQL 被视为一个整体。然而，其他数据库也有其优势。例如，MySQL 花了相当长的时间才支持在其他系统中被视为标准的功能；不过，MySQL 以速度很快而闻名。

本章重点介绍 MySQL，而第 9 章“使用其他数据库”则涉及相当多的其他数据库。两章都展示了它们的基本操作：连接、发送 SQL 语句以及评估返回值。无论你的数据库驱动 Web 应用程序必须做什么，它总是必须执行这些步骤。

为了拥有一些测试数据，我们在关系数据库管理系统（RDBMS）中创建了一个名为 `phrasebook` 的数据库，并在其中放置了一个名为 `quotes` 的表。该表包含四个字段：

- `id`—一个整数值，每向数据库输入一条新记录就会增加一。取决于数据库系统，数据类型称为 IDENTITY、auto_increment 或类似名称。

- `quote`—引文，作为 `VARCHAR(255)`：此长度适用于所有系统。

- `author`—产生引文的人，作为 `VARCHAR(50)`。

- `year`—引文产生的年份（有时这高度推测性），类型为 `INT`。

每个数据库系统都附带管理工具或可用的第三方产品。例如，图 8.1 所示的基于 PHP 的 phpMyAdmin (http://www.phpmyadmin.net/) 为 MySQL 安装提供了非常好的访问方式。

![](img/2862989e5dc7f1b1d0bc64321737f084_241_0.png)

**图 8.1** 使用 phpMyAdmin 管理 MySQL 安装

### 连接到 MySQLi

```php
@mysqli_connect('localhost', 'user', 'password')
```

```php
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

有多个 MySQL 扩展可用于 PHP。最旧的一个 `ext/mysql` 用于 PHP 4 及更早版本；其继任者 `ext/mysqli`（i 官方代表 improved，unofficially 代表 incompatible——但这是愤世嫉俗的）随 PHP 5 提供，但需要 MySQL 4.1 或更高版本。然而，PHP 5 也支持旧扩展。本章仅涵盖后者扩展。第三个选项 `PDO` 在第 9 章末尾介绍，因为你也可以将此 API 与其他数据库一起使用。

除了不同的 API 外，PHP 用户还可以选择不同的库。较旧的 PHP 安装通常使用 MySQL 客户端服务器库（`libmysql`），但 PHP 5.3 引入了 MySQL 原生驱动程序（`mysqlnd`）。该驱动程序提供额外功能和更好的性能，因此建议使用此驱动程序。

如果你想使用 `ext/mysqli`，`--with-mysql` 开关必须指向 `/path/to/mysql config`。Windows 用户必须使用文件 `php_mysqli.dll` 和 `lib-mysql.dll`；其余先前的安装说明保持不变。

现在连接数据库很容易：只需调用 `mysql_connect()`，提供服务器、用户名和密码。然后你会得到一个句柄，可用于 `mysqli_select_db()` 或在服务器上选择数据库。最后，`mysqli_close()` 关闭到数据源的连接。

如果你使用过旧的 `ext/mysql`，请记住 `mysql(i)_select_db()` 的不同变量顺序是这两个扩展之间最显著的差异之一。新版本希望数据库句柄排在第一位。这两个扩展之间的另一个区别是，每当使用时数据库句柄都是强制参数。对于 `ext/mysql`，`mysql_connect()` 创建的最后一个句柄是页面的当前默认句柄。另一个区别：`mysqli_connect()` 接受数据库名称作为可选的第四个参数，因此可以避免使用 `mysqli_select_db()`。

**注意：** 另外，`mysqli` 扩展还提供面向对象的语法来访问数据源。虽然本章使用函数式方法是为了使从 `ext/mysql` 到 `ext/mysqli` 的可能过渡尽可能无痛，但下面展示了面向对象方法是什么样的：

```php
$db = new mysqli('localhost', 'user', 'password');
$db->select_db('phrasebook');
$db->close();
```

### 向 MySQL 发送 SQL

```php
<?php
if ($db = @mysqli_connect('localhost', 'user',
    'password')) {
    require_once 'stripFormSlashes.inc.php';
    mysqli_select_db($db, 'phrasebook');
    mysqli_query($db, sprintf(
        'INSERT INTO quotes (quote, author, year)
        VALUES (\'%s\', \'%s\', \'%s\')',
        mysqli_real_escape_string($db,
        $_POST['quote']),
        mysqli_real_escape_string($db,
        $_POST['author']),
        intval($_POST['year'])));
    echo 'Quote saved.';
    mysqli_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

*向 MySQLi 发送 SQL (mysqli_query.php; 摘录)*

函数 `mysqli_query()` 将 SQL 发送到由句柄标识的数据库——`mysql_query()` 的第二个参数，`mysqli_query()` 的第一个参数。然而，为了避免一种称为 SQL 注入的攻击（使用 GET 或 POST 数据注入 SQL 语句的方法），你绝对必须使用 `mysqli_real_escape_string()` 来转义任何危险字符，例如单引号。参见前面的和下面的列表以获取实现。那些列表中缺少的代码（但当然它包含在

在代码下载中）基本上是一个 HTML 表单，它接受一条语录、其作者和年份。图 8.2 显示了用于语录收藏的 HTML 输入表单：

```php
<?php
if ($db = @mysqli_connect('localhost', 'user',
    'password')) {
    mysqli_select_db($db, 'phrasebook');
    mysqli_query($db, sprintf(
        'INSERT INTO quotes (quote, author, year)
        VALUES (\'%s\', \'%s\', \'%s\')',
        mysqli_real_escape_string($db,
        $_POST['quote']),
        mysqli_real_escape_string($db,
        $_POST['author']),
        intval($_POST['year'])));
    echo 'Quote saved.';
    mysqli_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

![](img/2862989e5dc7f1b1d0bc64321737f084_245_0.png)

图 8.2 用于向数据库添加语录的 HTML 输入表单

### 使用 MySQL 的预处理语句

```
$stmt = mysqli_prepare()
mysqli_stmt_execute($stmt)
```

```php
<?php
if ($db = @mysqli_connect('localhost', 'user',
'password')) {
    $stmt = mysqli_prepare($db, 'INSERT INTO quotes
(quote, author, year) VALUES (?, ?, ?)');
    $quote = mysqli_real_escape_string($db,
$_POST['quote']);
    $author = mysqli_real_escape_string($db,
$_POST['author']);
    $year = intval($_POST['year']);
    mysqli_stmt_bind_param($stmt, 'ssi', $quote,
$author, $year);
    if (mysqli_stmt_execute($stmt)) {
        echo 'Quote saved.';
    } else {
        echo 'Error writing quote.';
    }
    mysqli_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

使用 MySQL 的预处理语句（`mysqli_stmt_execute.php`；节选）

新的 MySQL 扩展提供了一种既能避免 SQL 注入又能加速 SQL 语句的方法：即所谓的预处理语句。在其中，你提供

```php
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



# 从 MySQL 检索数据（`mysqli_fetch.php`；节选）

`mysqli_query()` 的返回值是指向实际结果集的指针。它可以用于遍历 `SELECT` 语句返回的完整条目列表。为此，以下函数会很有用：

- `mysqli_fetch_assoc()` 将结果集中的当前行作为关联数组返回（字段名变为键），然后移动到下一行。
- `mysqli_fetch_object()` 将结果集中的当前行作为对象返回（字段名变为属性），然后移动到下一行。
- `mysqli_fetch_row()` 将结果集中的当前行作为数字数组返回，然后移动到下一行。

当然还有其他函数；不过，这三个是最常用的。下面的代码使用 `mysqli_fetch_assoc()`，而前面的列表使用 `mysqli_fetch_object()` 打印数据库表的内容。主要思想是使用 `while` 循环——当结果集中没有剩余数据时，所有 `mysqli_fetch_*` 函数都会返回 `false`：

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
if ($db = @mysqli_connect('localhost', 'user', 'password')) {
    mysqli_select_db($db, 'phrasebook');
    $result = mysqli_query($db, 'SELECT * FROM quotes');
    while ($row = mysqli_fetch_assoc($result)) {
        printf(
            '<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
            htmlspecialchars($row['id']),
            htmlspecialchars($row['quote']),
            htmlspecialchars($row['author']),
            htmlspecialchars($row['year'])
        );
    }
    mysqli_close($db);
} else {
    echo '<tr><td colspan="4">Connection failed:</td></tr>';
}
?>
</table>
```

图 8.3 显示了在填入一些（政治）语录后数据库的内容。（抱歉，我不是来自美国；我随便找了一些。）

![](img/2862989e5dc7f1b1d0bc64321737f084_250_0.png)

**图 8.3** 数据库的内容

## 检索最后插入的 ID

```
$id = mysqli_insert_id($db);
```

```php
<?php
if ($db = @mysqli_connect('localhost', 'user',
'password')) {
    mysqli_select_db($db, 'phrasebook');
    mysqli_query($db, sprintf(
    'INSERT INTO quotes (quote, author, year)
    VALUES (\'%s\', \'%s\', \'%s\')',
    mysqli_real_escape_string($db,
    $_POST['quote']),
    mysqli_real_escape_string($db,
    $_POST['author']),
    intval($_POST['year'])));
$id = mysqli_insert_id($db);
echo "Quote saved (ID=$id).";
mysqli_close($db);
} else {
echo 'Connection failed.';
}
?>
```

当使用 MySQL 的 `auto_increment` 特性时，每当你向表中插入新项，数据库都会自动为该列分配一个值。在插入之后确定这个生成的值可能会很有用。`mysqli_insert_id()` 函数可以帮我们做到这一点。只需提供数据库连接句柄，你就会收到返回的 ID。该值仅对使用该连接执行的最后一条 `INSERT` SQL 语句有效。

## 使用事务

```
mysqli_autocommit($db, false);
mysqli_commit($db);
```

```php
<?php
if ($db = @mysqli_connect('localhost', 'user',
'password')) {
    mysqli_select_db($db, 'phrasebook');
    mysqli_autocommit($db, false);
    if (mysqli_query($db, sprintf(
        'INSERT INTO quotes (quote, author, year)
        VALUES (\'%s\', \'%s\', \'%s\')',
        mysqli_real_escape_string($db,
        $_POST['quote']),
        mysqli_real_escape_string($db,
        $_POST['author']),
        intval($_POST['year'])))) {
        $result = mysqli_query($db, 'SELECT MAX(id)
        FROM quotes');
        $row = mysqli_fetch_object($result);
        $id = $row->id;
        mysqli_commit($db);
        echo "Quote saved (ID=$id).";
    } else {
        mysqli_rollback($db);
        echo 'An error has occurred.';
    }
    mysqli_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

使用 MySQL 检索先前插入项的 ID（`mysqli_commit.php`；节选）

默认情况下，你发送到数据库的 MySQL 语句会立即执行；这种模式也称为自动提交。最近的 MySQL 版本还支持事务，这意味着多条 SQL 语句可以“捆绑”成一条语句。当你使用事务时，要么整个事务完整执行，要么完全不执行；不可能出现部分执行的情况。

要使用事务，首先禁用自动提交（例如使用 `mysqli_autocommit()` 函数），此后所使用连接上的所有 SQL 语句都将成为事务的一部分。使用 `mysqli_commit()`，语句最终被执行，而 `mysqli_rollback()` 则让数据库回到没有该事务的状态。在脚本结束时，所有待处理的事务都会自动提交，但为了性能考虑，你应该尽快调用 `mysqli_commit()`。

## 使用其他数据库

除了 MySQL 之外，PHP 还支持地球上几乎所有相关的（以及一些不太相关的）数据库。本章介绍其中许多系统所使用的基本技术，尤其是连接数据库、执行 SQL 语句和检索返回数据。与第 8 章“使用 MySQL 数据库”一样，我们使用一个名为 `phrasebook` 的示例数据库，以及其中的一个示例模式/表，名为 `quotes`，包含以下四个字段：

- `id`——一个整数值，每向数据库添加一条新记录就增加 1。取决于数据库系统，该数据类型称为 `IDENTITY`、`auto_increment` 或类似的名称。
- `quote`——语录本身，类型为 `VARCHAR(255)`；这一长度适用于所有系统。
- `author`——产生该语录的人，类型为 `VARCHAR(50)`。
- `year`——该语录产生的年份，类型为 `INT`。

### 连接到 SQLite

```
@sqlite_open('quotes.db', 0666, $error)
$db = new SQLite3('quotes.db');
```

```php
<?php
if ($db = @sqlite_open('quotes.db', 0666, $error)) {
    echo 'Connected to the database.';
    sqlite_close($db);
} else {
    echo 'Connection failed: ' .
    htmlspecialchars($error);
}
?>
```

从 PHP 5 开始，SQLite 已捆绑在脚本语言中。这是一个轻量级的文件型数据库。这使得读取非常快（在许多情况下，甚至比使用“真实”数据库更快），但写入有时可能比其他系统更慢，因为文件锁定是一个问题。然而，PHP 4 用户也可以使用 SQLite，因为有一个 PECL（PHP 扩展社区库）模块可用 (`http://pecl.php.net/`)。

如果你使用 PHP 5.0-5.3，SQLite 支持已包含在内。在 PHP 5.4 中，SQLite 扩展（`ext/sqlite`）已移至 PECL。作为替代方案，PHP 5.4（以及 PHP 5.3）提供了 `ext/sqlite3` 扩展，本章也涵盖了该扩展。

Windows 用户必须使用（或编译）`php_sqlite.dll`，将其复制到 PHP 的扩展文件夹中，然后在 `php.ini` 中使用 `extension=php_sqlite.dll` 加载 `ext/sqlite` 或使用 `extension=php_sqlite3.dll` 加载 `ext/sqlite3`。

使用 `ext/sqlite` 时，你可以使用 `sqlite_open()` 连接到 SQLite 数据源。第一个参数提供数据库文件名；如果文件尚不存在，则会创建它。为此，PHP 进程需要对该文件具有读写权限。第二个参数是文件打开模式（推荐 `0666`）；然而，截至本文撰写时，该参数被忽略。第三个参数是一个包含任何错误消息的变量（例如权限不足）。

**注意：** 就像 `ext/mysqli` 一样，PHP 5 下的 SQLite 扩展也可以使用面向对象编程（OOP）方法访问：

```php
<?php
$db = new SQLiteDatabase('quotes.db');
echo 'Connected to the database.';
$db->close();
?>
```

为了向后兼容，本章在后续内容中使用函数式方法。

`ext/sqlite3` 扩展使用强制性的面向对象应用程序编程接口（API）。在这里，`SQLite3` 类的 `open()` 方法会打开数据库文件。由于无论如何都需要实例化该类，更快捷的方法是在类构造函数中提供文件名，这同样会打开数据库。错误处理可以通过 `try-catch` 块实现：

```php
<?php
    try {
        $db = new SQLite3('quotes.db');
        echo 'Connected to the database.';
        $db->close();
    } catch ($ex) {
        echo 'An error has occurred.';
    }
?>
```

### 向 SQLite 发送 SQL

```
SQLite3 METHOD
$db->exec()
```

```php
<?php
    if ($db = @sqlite_open('quotes.db', 0666, $error))
    {
        sqlite_exec($db, sprintf(
            'INSERT INTO quotes (quote, author, year)
VALUES (\'%s\', \'%s\', \'%s\')',
            sqlite_escape_string($_POST['quote']),
            sqlite_escape_string($_POST['author']),
            intval($_POST['year'])));
        echo 'Quote saved.';
        sqlite_close($db);
    } else {
        echo 'Connection failed: ' .
        htmlspecialchars($error);
    }
?>
```

PHP 函数 `sqlite_exec()` 使用 `ext/sqlite` 将 SQL 语句发送到数据库。第一个参数使用由 `sqlite_open()` 返回的数据库句柄；第二个参数是 SQL 字符串。为了避免 SQL 注入，PHP 函数 `sqlite_escape_string()` 会转义动态数据中的危险字符。上述代码对此进行了实现，针对的是示例表 `quotes`，该表也在第 8 章的 MySQL 短语中使用过。

`ext/sqlite3` 的用户需要执行 `SQLite3` 类的 `exec()` 方法：

```php
<?php
try {
    $db = new SQLite3('quotes.db');
    $db->exec(sprintf(
        'INSERT INTO quotes (quote, author, year)
VALUES (\'%s\', \'%s\', \'%s\')',
        $db->escape_string($_POST['quote']),
        $db->escape_string($_POST['author']),
        intval($_POST['year'])));
    echo 'Quote saved.';
    $db->close();
} catch ($ex) {
    echo 'An error has occurred.';
}
?>
```

**提示：** 如果表包含一个标识列（使用 SQLite 时的数据类型为 `INTEGER PRIMARY KEY`），在发送 SQL 语句后调用 `sqlite_last_insert_rowid()` 函数（用于 `ext/sqlite`）或 `lastInsertRowID()` 方法（用于 `ext/sqlite3`）会返回该列对数据库中新条目的值。

### 检索 SQLite 查询结果

```
$result = sqlite_query($db, 'SELECT * FROM quotes');
sqlite_fetch_array($result);
$result = $db->query('SELECT * FROM quotes');
$result->fetchArray();
```

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
try {
    $db = new SQLite3('quotes.db');
    $result = $db->query('SELECT * FROM quotes');
    while ($row = $result->fetchArray()) {
        printf(
            '<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
            htmlspecialchars($row['id']),
            htmlspecialchars($row['quote']),
            htmlspecialchars($row['author']),
            htmlspecialchars($row['year'])
        );
    }
    $db->close();
} catch ($ex) {
    echo 'An error has occurred.';
}
?>
</table>
```

上一节中的函数 `sqlite_exec()` 和方法 `exec()` 执行非常快；然而，不可能访问通过它发送的 SQL 语句的返回值。为此，必须使用 `sqlite_query()`（`ext/sqlite`）或 `query()`（`ext/sqlite3`）。此函数或方法返回查询结果集的句柄。然后可以使用以下函数和方法遍历结果集：

- `sqlite_fetch_array()` 函数和 `fetchArray()` 方法以关联数组的形式返回结果集中当前行（字段名变为键），并前进到下一行。
- `sqlite_fetch_object()`（`ext/sqlite3` 中没有等价物）以对象的形式返回结果集中当前行（字段名变为属性），并前进到下一行。
- `sqlite_fetch_all()`（同样，`ext/sqlite3` 中没有等价物）以关联数组的数组形式返回完整的结果集。

上述列表展示了如何使用 `fetchArray()` 方法访问结果集中的所有数据；以下代码大致做同样的事情，这次使用 `sqlite_fetch_object()`。`while` 循环只要该方法或函数返回的值不是 `false`（表示没有剩余数据）就会调用它：



```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
if ($db = @sqlite_open('quotes.db', 0666, $error))
{
    $result = sqlite_query($db, 'SELECT * FROM
    quotes');
    while ($row = sqlite_fetch_object($result)) {
        printf(
            '<tr><td>%s</td><td>%s</td><td>%s</td><td>%s
</td></tr>',
            htmlspecialchars($row->id),
            htmlspecialchars($row->quote),
            htmlspecialchars($row->author),
            htmlspecialchars($row->year)
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

*从 SQLite 检索数据 (sqlite_fetch.php; 摘录)*

**提示：** 使用 `sqlite_fetch_all()` 会将整个结果集同时读入内存。如果你使用 ext/sqlite，请注意 ext/sqlite3 不支持此功能。因此，如果数据量不大，这是性能最好的方法。如果数据量较大，使用 `sqlite_fetch_array()` 和 `sqlite_fetch_object()` 的迭代方法可能更好。

### 使用 SQLite 预处理语句

```
$stmt = $db->prepare('INSERT INTO quotes (quote, author, year) VALUES (:quote, :author, :year)');
$stmt->bindParam(':quote', ...);
```

```php
<?php
try {
    $db = new SQLite3('quotes.db');
    $stmt = $db->prepare('INSERT INTO quotes (quote,
author, year) VALUES (:quote, :author, :year)');
    $stmt->bindValue(':quote', $_POST['quote'],
SQLITE3_TEXT);
    $stmt->bindValue(':author', $_POST['author'],
SQLITE3_TEXT);
    $stmt->bindValue(':year',
intval($_POST['year']), SQLITE3_INTEGER);
    $db->close();
} catch ($ex) {
    echo 'An error has occurred.';
}
?>
```

*使用 SQLite3 预处理语句 (sqlite3_prepare.php; 摘录)*

预处理语句通过在 SQL 中支持占位符，将 SQL 命令与数据分离。在第二步中，可以为这些占位符分配值。

使用 ext/sqlite3 时，可以使用预处理语句。第一步中，`prepare()` 方法创建一个表示语句的 `SQLite3Stmt` 对象。占位符由冒号和占位符名称表示：

```
$stmt = $db->prepare('INSERT INTO quotes (quote, author, year) VALUES (:quote, :author, :year)');
```

然后，语句对象的 `bindValue()` 方法为特定占位符分配值。你提供占位符的名称、要分配的值以及要使用的数据类型：

```
$stmt->bindValue(':quote', $_POST['quote'], SQLITE3_TEXT);
```

(目前，ext/sqlite3 支持以下数据类型：

- `SQLITE3_BLOB`—BLOB 数据（二进制大对象）

- `SQLITE3_FLOAT`—一个浮点值

- `SQLITE3_INTEGER`—一个整数值

- `SQLITE3_NULL`—一个 NULL 值

- `SQLITE3_TEXT`—一个字符串

**注意：** `bindValue()` 方法将你提供的值绑定到占位符。相反，你也可以使用 `bindParam()` 方法，它将你提供的参数绑定到语句占位符。请注意，在这种情况下你不能使用值，因为你需要提供一个可能按引用传递的参数。以下代码将无法工作：

```php
$stmt->bindParam(':year', 2012, SQLITE3_INTEGER);
```

### 连接到 PostgreSQL

```php
<?php
    if ($db = @pg_connect('host=localhost port=5432
    dbname=phpsaltbook user=postgres password=abc123'))
    {
        echo 'Connected to the database.';
        pg_close($db);
    }
    else {
        echo 'Connection failed.';
    }
?>
```

*连接到 PostgreSQL (pg_connect.php)*

PostgreSQL 拥有不断增长的粉丝群。有些人甚至说这是因为在 8.0 版本终于推出了原生 Windows 版本。然而，大多数使用 PostgreSQL 的生产系统仍然托管在 Linux 或 UNIX 上。

在安装数据库后，你可以使用基于 Web 的管理软件，例如 phpPgAdmin (http://sourceforge.net/projects/phpgadmin) 或其他工具，例如图形用户界面 (GUI) 应用程序 pgAdmin (www.pgadmin.org/) 来管理数据库。或者，你也可以使用命令行工具。为了让 PHP 访问 PostgreSQL 安装，Windows 用户必须在 php.ini 中使用条目 `extension=php_pgsql.dll` 加载扩展；UNIX/Linux 用户使用开关 `--with-pgsql=/path/to/pgsql` 配置 PHP。

然后，`pg_connect()` 连接到数据源。你必须提供一个连接字符串，其中包含所有重要数据，包括主机、端口、数据库名称和用户凭据。

### 向 PostgreSQL 发送 SQL

#### pg_query()

```php
<?php
if ($db = @pg_connect('host=localhost port=5432
dbname=phrasebook user=postgres password=abc123'))
{
    pg_query($db, sprintf(
        'INSERT INTO quotes (quote, author, year)
        VALUES (\'%s\', \'%s\', \'%s\')',
        pg_escape_string($_POST['quote']),
        pg_escape_string($_POST['author']),
        intval($_POST['year'])));
}
```

```php
$data = array(
'quote' => pg_escape_string($_POST['quote']),
'author' =>
pg_escape_string($_POST['author']),
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

向 PostgreSQL 发送 SQL (pg_insert.php; 摘录)

另一种在 PostgreSQL 中插入或更新数据的方式是使用 `pg_insert()` 和 `pg_update()` 函数。第一个参数必须是数据库句柄，第二个参数是要插入/更新的表，第三个参数包含以关联数组形式表示的一些数据。（列名是键。）在 UPDATE SQL 语句的情况下，更新条件还必须作为函数的第四个参数以数组形式提交。前面的代码展示了如何插入数据。

### 检索 PostgreSQL 查询的结果

```php
$result = pg_query();
pg_fetch_row($result);
```

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
if ($db = @pg_connect('host=localhost port=5432 dbname=phrasebook user=postgres password=abc123')) {
$result = pg_query($db, 'SELECT * FROM quotes');
while ($row = pg_fetch_row($result)) {
vprintf('<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>', $row);
}
pg_close($db);
} else {
echo '<tr><td colspan="4">Connection failed.</td></tr>';
}
?>
</table>
```

从 PostgreSQL 检索数据 (pg_fetch.php: 摘录)

对 `pg_query()` 的调用的返回值是指向可与以下函数一起使用的结果集的指针：

- `pg_fetch_assoc()` 以关联数组的形式返回结果集中当前行。

- `pg_fetch_object()` 以对象形式返回结果集中当前行。

- `pg_fetch_row()` 以数字数组形式返回结果集中当前行。

- `pg_fetch_all()` 以关联数组的数组形式返回完整结果集。

前面的代码使用 `pg_fetch_row()` 读取 quotes 表中的所有数据。

另外，`pg_select()` 的工作方式与 `pg_insert()` 和 `pg_update()` 类似。只需提供数据库句柄、表名以及可能以数组形式表示的 WHERE 子句，即可获得作为（关联）数组的数组的完整结果集：

```php
$data = pg_select($db, 'quotes');
```

### 连接到 Oracle

```php
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

*连接到 Oracle (oci_connect.php)*

有两个 PHP 扩展可用于 Oracle，但只有一个仍在积极维护，并且也适用于较新版本的数据库管理系统 (RDBMS)。要安装它，请使用开关 `--with-oci8` 配置 PHP。必须设置环境变量 `ORACLE_HOME`，以便 PHP 找到客户端库。Windows 用户需要 php.ini 指令 `extension=php_oci8.dll`。此外，PHP 需要对客户端库具有读取权限（这些库需要单独安装）。然后，`oci_connect()` 尝试建立到服务器的连接。参数的顺序有点奇怪：首先是用户名和密码，然后是服务名称（使用配置助手配置或属于 `tnsnames.ora` 文件的一部分）。返回值是连接的句柄，后续数据库操作都需要它。

### 向 Oracle 发送 SQL

```php
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
  } else {
    echo 'Connection failed.';
  }
?>
```

向 Oracle 发送 SQL (oci_execute.php; 摘录)

本节再次使用 quotes 表，其中还包括一个标识列；然而，使用 Oracle 实现起来有点复杂。请参阅下载存档中的脚本 `quotes.oracle.sql` 了解更多信息。

要向 Oracle 发送 SQL，需要两个步骤。首先，对 `oci_parse()` 的调用解析 SQL 字符串并返回一个资源，然后可以使用 `oci_execute()` 执行它。`oci_execute()` 的第二个参数非常重要。允许使用多个常量，但大多数情况下使用 `OCI_DEFAULT`。尽管名字如此，这并不是时间，`OCI_DEFAULT` 值，而是表示“无自动提交”。相比之下，`OCI_COMMIT_ON_SUCCESS` 在未发生错误时提交挂起的事务。而这，确实是默认值。

不幸的是，没有 `oci_escape_string()` 这样的函数来转义 SQL 语句中使用的特殊字符。因此，预处理语句是必须的——但也非常容易实现。为此，SQL 语句必须包含以冒号开头的占位符：

```
$sql = 'INSERT INTO quotes (quote, author, year) VALUES (:quote, :author, :year)';
```

然后，这些占位符必须用值填充。为此，必须使用 `oci_bind_by_name()`：

```
oci_bind_by_name($stmt, ':quote', $_POST['quote']);
```

前面的代码将一些表单数据发送到数据库。无需担心特殊字符，因为 `oci_bind_by_name()` 会处理这些。

**注意：** 当你使用 `OCI_DEFAULT` 作为提交模式时，必须使用 `oci_commit($db)` 将更改写入数据库：`oci_rollback($db)` 执行回滚。

**提示：** 顺便说一下，如果你想检索最近一次 INSERT 操作的自动值，你必须在事务中执行并执行 `SELECT quotes_id.CURRVAL AS id FROM DUAL`，其中 `quotes_id` 是你正在使用的序列的名称。

### 检索 Oracle 查询的结果

#### oci_fetch_object($stmt)

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
if ($db = @oci_connect('scott', 'tiger', 'orcl')) {
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



从 Oracle 检索数据 (`oci_fetch.php`; 摘录)

你有多种方式访问 SQL 查询的返回值，但以下函数在实践中最常使用：

- `oci_fetch_assoc()` 返回结果集中当前行作为关联数组。
- `oci_fetch_object()` 返回结果集中当前行作为对象。
- `oci_fetch_row()` 返回结果集中当前行作为数字数组。
- `oci_fetch_all()` 将完整的结果集作为关联数组的数组返回。然而，需要五个参数：来自 `oci_parse()` 的语句对象、用于返回数据的数组、要跳过的行数、要返回的最大行数（-1 表示无限），以及返回数字 (`OCI_NUM`) 还是关联 (`OCI_ASSOC`) 数组。

本节中的示例使用 `while` 循环和 `oci_fetch_object()` 来检索表中的所有数据。

## 第 9 章 使用其他数据库

注意：Oracle 总是以大写返回列名。因此，在访问 SQL 查询的返回值时，你必须使用大写对象属性或大写关联数组键。

```php
<?php

$config = array('UID' => 'user', 'PWD' =>

'password',

'Database' => 'phrasebook');

if ($db = @sqlsrv_connect('localhost\SQLExpress',

$config)) {

	echo 'Connected to the database.';

	sqlsrv_close($db);

} else {

	echo 'Connection failed.';

}

?>
```

Microsoft SQL 引擎有两种版本：功能齐全（价格也全）的 Microsoft SQL Server（简称：MSSQL）和免费版 Microsoft SQL Server Express Edition，可在 `www.microsoft.com/sqlserver/en/us/editions/express.aspx` 免费获取。PHP 支持这两个版本，因为它们彼此兼容。

PHP 附带了用于 MSSQL 的扩展 `ext/mssql`。然而它相当老旧且不再积极维护。相反，Microsoft 提供了一个新的（仅限 Windows）扩展 `ext/sqlsrv`，这是推荐使用的。

要使其工作，你需要在 `php.ini` 中使用 `extension=<filename>.dll` 添加扩展。此外，你还需要扩展本身。根据你使用的 PHP 版本，需要特定版本。PHP 手册页面 `http://php.net/sqlsrv.installation` 会指向正确的下载页面。如果可能，你应至少使用扩展的版本 3，它使用 Microsoft SQL Server 2012 Native Client 库；版本 2 需要 Microsoft SQL Server 2008 R2 Native Client 库。Microsoft 在 `http://msdn.microsoft.com/en-us/library/cc296170.aspx` 描述了最新的系统要求。

要连接到 MSSQL，调用 `mssql_connect()` 并提供服务器名称（`(local)` 可作为 `localhost` 的快捷方式）；如果你使用的是 Microsoft SQL Server 的命名实例（例如 `SQLEXPRESS`，默认随 MSSQL Express Edition 安装），则将其附加到服务器名称后，用反斜杠分隔：`(local)\SQLEXPRESS`。作为第二个参数，你可以提供一个包含连接信息的数组。扩展支持以下数组键：

- `Database`—数据库名称
- `PWD`—密码
- `UID`—用户名

如果你想使用当前用户（有时也称为受信任连接）对数据库进行身份验证，只需省略 `UID` 和 `PWD` 配置设置即可。

### 向 MSSQL 发送 SQL

```php
<?php

$config = array('UID' => 'user', 'PWD' =>

'password', 'Database' => 'phrasebook');

if ($db = @sqlsrv_connect('localhost\SQLEXPRESS')) {

ini_set('magic_quotes_sybase', 'On');

sqlsrv_query($db, sprintf(

"INSERT INTO quotes (quote, author, year) VALUES (\'%s\', \'%s\', \'%s\')",

addslashes($_POST["quote"]),

addslashes($_POST["author"]),

intval($_POST["year"])));

echo 'Quote saved.';

sqlsrv_close($db);

} else {

echo 'Connection failed.';

}

?>
```

向 MSSQL 发送 SQL (`sqlsrv.execute.php`; 摘录)

函数 `sqlsrv_query()` 将 SQL 语句发送到 MSSQL 安装。其参数顺序与 `ext/mysql` 类似：首先是数据库句柄，然后是 SQL 命令。

另一个重要点是转义特殊字符。在 MSSQL 中，单引号不应使用反斜杠转义，而应使用双引号：

INSERT INTO quotes (quote, author, year) VALUES ('Ain\'t Misbehavin\'', 'Louis Armstrong', 1929)

为此，你可以使用 `addslashes()`。不过，首先必须对其进行配置，使其返回 MSSQL/MSDE 兼容的字符串：

```php
ini_set('magic_quotes_sybase', 'On');

$author = addslashes($_POST['author']);
```

不过要提醒一点：`magic_quotes_sybase` 设置在 PHP 5.3 中已弃用，并在 PHP 5.4 中移除。如果你要在 SQL 语句中使用用户信息，应改用预处理语句（两节之后）。本节开头的示例对一些表单数据进行了清理并写入了（到现在为止）众所周知的示例数据库。

### 检索 MSSQL 查询结果

```php
$result = sqlsrv_query();

sqlsrv_fetch_object($result);
```

```php
<table>

<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>

<?php

$config = array('UID' => 'user', 'PWD' => 'password', 'Database' => 'phrasebook');

if ($db = @sqlsrv_connect('(local)\SQLEXPRESS', $config)) {

    $result = sqlsrv_query($db, 'SELECT * FROM quotes');

    while ($obj = sqlsrv_fetch_object($result)) {

        printf(

'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s

</td></tr>',

htmlspecialchars($row->id),

htmlspecialchars($row->quote),

htmlspecialchars($row->author),

htmlspecialchars($row->year)

);

sqlsrv_close($db);

} else {

echo '<tr><td colspan="4">Connection

failed.</td></tr>';

}

?>

</table>
```

*从 MSSQL 检索数据 (`sqlsrv_fetch.php`; 摘录)*

最后，当然也有一种方法可以检索结果集中的所有数据。`while` 循环会派上用场，使用以下其中一个函数：

- `sqlsrv_fetch_array()` 将结果集中当前行作为关联数组和/或数字索引数组返回；默认情况下，它返回两者。
- `sqlsrv_fetch_object()` 将结果集中当前行作为对象返回。

### 使用 MSSQL 预处理语句

```php
$stmt = sqlsrv_query();

sqlsrv_execute($stmt);
```

```php
<?php

$config = array('UID' => 'user', 'PWD' => 'phrasebook', 'Database' => 'phrasebook');

if ($db = @sqlsrv_connect('(local)\SQLEXPRESS', $config)) {

    $year_as_int = intval($_POST['year']);

    $data = array(&$_POST['quote'], &$_POST['author'], &$year_as_int);

    $stmt = sqlsrv_query(

        $db,

        'INSERT INTO quotes (quote, author, year)

VALUES (?, ?, ?)',

        $data);

    sqlsrv_execute($stmt);

    echo 'Quote saved.';

    sqlsrv_close($db);

} else {

    echo 'Connection failed.';

}

?>
```

使用预处理语句从 MSSQL 检索数据 (`sqlsrv_prepare.php`; 摘录)

因为 `ext/sqlsrv` 中没有指定的转义函数，所以预处理语句是使用用户提供的数据在 SQL 语句中并避免 SQL 注入的唯一可行方法。像往常一样，必须执行两个步骤。首先，你创建一个语句对象（此处使用的函数是带占位符的 `sqlsrv_prepare()`），然后执行该语句。在准备语句时，你还必须提供占位符的数据。

`ext/sqlsrv` 扩展期望每个占位符使用一个问号 (`?`)。这些占位符的值以数组形式提供，其顺序与 SQL 语句中占位符的顺序完全相同。这些值可以按引用传递。

### 在非 Windows 系统上使用 MSSQL

```php
$db = @mssql_connect();

$result = mssql_query();

mssql_fetch_assoc($result);
```

```php
<table>

<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>

<?php

if ($db = @mssql_connect('localhost', 'user', 'password')) {

    mssql_select_db('phrasebook', $db);

    $result = mssql_query('SELECT * FROM quotes', $db);

    while ($row = mssql_fetch_assoc($result)) {

        print(

            '<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',

            htmlspecialchars($row['id']),

            htmlspecialchars($row['quote']),

            htmlspecialchars($row['author']),

            htmlspecialchars($row['year'])

        );

    }

    mssql_close($db);

} else {

    echo '<tr><td colspan="4">Connection failed.</td></tr>';

}

?>

</table>
```

*使用 `ext/mssql` 从 MSSQL 检索数据 (`mssql_fetch.php`; 摘录)*

还有一个使用已弃用的 `ext/mssql` 扩展的剩余原因：在异构网络中，UNIX/Linux 系统可以访问 MSSQL 安装，并使用旧的 MSSQL 扩展连接到它们。要实现这一点，你必须从 `www.freetds.org/` 下载 FreeTDS 库，并在解压发行版后使用以下命令安装：

```
./configure --prefix=/usr/local/tds --with-tdsver=4.2

make

sudo make install
```

然后，使用 `--with-sybase=/usr/local/freetds` 开关重新配置 PHP。

最后，你可以使用 `mssql_connect()` 连接到服务器，并使用 `mssql_select_db()` 选择要使用的数据库，这与其他数据库扩展使用的 API 类似。使用 `mssql_query()` 执行 SQL 查询后，可以使用以下函数之一检索返回的数据：

- `mssql_fetch_assoc()` 将结果集中的当前行作为关联数组返回。
- `mssql_fetch_object()` 将结果集中的当前行作为对象返回。
- `mssql_fetch_row()` 将结果集中的当前行作为数值数组返回。

注意：MSSQL 支持两种用户认证模式：SQL 认证和 Windows 认证。后者检查当前 Windows 用户是否具有足够的权限访问数据库。在受控环境中，这可能比使用用户名和密码更好。但是，你首先必须找出使用的是哪个用户。例如，Microsoft Internet 信息服务（IIS）Web 服务器软件通常使用 Internet 来宾帐户（即 `IUSR <机器名>`）。因此，该用户需要数据库中的权限。

要使用 Windows 认证——有时也称为受信任连接——你需要以下 `php.ini` 指令：

```
mssql.secure_connection = On
```

### 连接到 Firebird

```php
<?php

if ($db = ibase_connect('localhost:/tmp/quotes.gdb', 'user', 'password')) {

	echo 'Connected to the database.';

	ibase_close($db);

} else {

	echo 'Connection failed.';

}

?>
```

### 连接到 InterBase/Firebird (`ibase_connect.php`)

Firebird 数据库目前更像是一个内行才知道的秘诀，而不是广泛使用的数据库，但它正在获得更多用户，并且可能成为成熟关系型数据库管理系统（RDBMS）的替代品。该数据库起源于 Borland 的 InterBase 产品。因此，Windows 用户需要在 `php.ini` 中设置 `extension=php_interbase.dll`，而“自行编译者”必须使用 `--with-interbase=/path/to/firebird` 开关配置 PHP。此外，Firebird 支持两种模式：一种是与 SQLite 类似的文件模式，一种是服务器模式。为了互操作性和易于部署，本节使用文件模式。

本节还使用与 Firebird 和 InterBase 兼容的 `.gdb` 文件；新的 Firebird 格式扩展名为 `.fdb`。创建此文件后，`ibase_connect()` 连接到该文件或数据库。对于主机，当使用 TCP/IP 时，你必须提供格式为 `'localhost:/path/to/file.gdb'` 的字符串，或提供本地文件名（列表假定文件位于本地机器的 `/tmp` 目录中）；你还需要用户名和密码。

### 向 Firebird 发送 SQL

#### `ibase_execute()`

```php
<?php

if ($db = ibase_connect('localhost:/tmp/quotes.gdb', 'user', 'password')) {

    require_once 'stripFormSlashes.inc.php';

    $sql = 'INSERT INTO quotes (id, quote, author, year) ' .

        'VALUES (GEN_ID(quotes_gen, 1), ?, ?, ?)';

    $stmt = ibase_prepare($db, $sql);

    ibase_execute($stmt, $_POST['quote'], $_POST['author'], intval($_POST['year']));

    echo 'Quote saved.';

    ibase_close($db);

} else {

    echo 'Connection failed.';

}

?>
```

向 InterBase/Firebird 发送 SQL (`ibase_execute.php`; 摘录)

可以使用 `ibase_query()` 函数向数据库发送 SQL 字符串。但是，没有 `ibase_escape_string()` 函数；因此，为防止 SQL 注入，必须使用预处理语句。这里，`ibase_prepare()` 函数发挥作用：它解析一条 SQL 语句（以问号作为占位符）并返回一个语句对象。然后，`ibase_execute()` 执行该语句，并将占位符的值作为附加参数获取。

注意：前面的代码包含 Firebird 的两个特性。首先，标识列由数据库中的生成器驱动：插入新字段时，调用 `GEN_ID(quotes_gen, 1)` 会在此列中输入下一个可用值。另外，单词 `year` 在 Firebird 中是保留字，因此列名为 `qyear`。

### 检索 Firebird 查询结果

```php
$result = ibase_query();

ibase_fetch_object($result);
```

```html
<table>



```
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>

<?php

if ($db = ibase_connect('/CHRISTIAN2003/tmp/quotes.gdb', 'user', 'password')) {

    $result = ibase_query($db, 'SELECT * FROM quotes');

    while ($row = ibase_fetch_object($result)) {

        printf(

'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',

htmlspecialchars($row->ID),

htmlspecialchars($row->QUOTE),

htmlspecialchars($row->AUTHOR),

htmlspecialchars($row->YEAR)

);

}

ibase_close($db);

} else {

echo '<tr><td colspan="4">Connection failed.</td></tr>';

}

?>
</table>
```

从InterBase/Firebird检索数据（`ibase_fetch.php`；摘录）

无论你使用`ibase_query()`还是`ibase_execute()`，最终都会有一个结果集的句柄，你可以使用`ibase_fetch_assoc()`（返回关联数组）或`ibase_fetch_object()`（返回对象）对其进行迭代。此代码使用后一种方法。

请记住，Firebird和InterBase以大写形式返回列名，因此对象属性（以及关联数组中的键）也是大写的。

### 通过`PDO`连接

```
try {
$db = new PDO('sqlite:PDOquotes.db');
}
```

```
<?php
try {
  $db = new PDO('sqlite:PDOquotes.db');
  echo 'Connected to the database.';
} catch (PDOException $ex) {
  echo 'Connection failed: ' . htmlspecialchars($ex->getMessage());
}
?>
```

通过`PDO`连接（`pdo_connect.php`）

`PDO`是PHP Data Objects的缩写，是由一些PHP核心开发者推动的新成果，也是PHP 5.1的关键特性之一。PHP中有几个抽象类，但`PDO`最终将成为官方标准。从PHP 5.3开始，`PDO`是PHP核心的一部分，因此Windows用户不需要在`php.ini`中引用特定的DLL。（在旧版PHP中，`extension=php_pdo.dll`可以实现这一点。）

除了可以使用`PDO`本身之外，还必须加载用于目标数据库的驱动程序。截至撰写本文时，可用的驱动程序如下：

- `PDO_CUBRID` 用于Cubrid
- `PDO_DBLIB` 用于Microsoft SQL Server（基于旧的`ext/mssql`扩展）
- `PDO_FIREBIRD` 用于InterBase/Firebird
- `PDO_IBM` 用于DB2
- `PDO_INFORMIX` 用于Informix
- `PDO_MYSQL` 用于MySQL 3.x–5.x
- `PDO_OCI` 用于Oracle
- `PDO_ODBC` 用于ODBC
- `PDO_PGSQL` 用于PostgreSQL
- `PDO_SQLITE` 用于SQLite版本2和3
- `PDO_SQLSRV` 用于Microsoft SQL Server（基于新的`ext/sqlsrv`扩展）
- `PDO_4D` 用于4D

为了尽可能使其可移植且易于部署，下面的示例使用SQLite驱动程序；但其他驱动程序和数据库系统也同样出色。无论你选择哪个系统，请在`php.ini`中下载并安装驱动程序。如果使用的是PHP 5.3之前的版本，请确保在`PDO`之后加载驱动程序——在新版PHP中，无需特意加载`PDO`。

`PDO`提供了一种面向对象的方法。你只需要一个合适的数据源名称（DSN）、一个用户和一个密码（可能还有其他选项）。前面的代码连接/创建了一个SQLite版本3文件。

### 通过`PDO`发送SQL

```
$stmt = $db->prepare($sql);
$stmt->execute();
```

```
<?php
try {
    $db = new PDO('sqlite:PDOquotes.db');
    $sql = 'INSERT INTO quotes (quote, author, year)
VALUES (:quote, :author, :year)';
    $stmt = $db->prepare($sql);
    $stmt->bindValue('quote', $_POST['quote']);
    $stmt->bindValue('author', $_POST['author']);
    $stmt->bindValue('year',
    intval($_POST['year']));
```

```
$stmt->execute();
echo 'Quote saved.';
} catch (PDOException $ex) {
echo 'Connection failed: ' .
htmlspecialchars($ex->getMessage());
}
?>
```

通过`PDO`发送SQL（`pdo_execute.php`：摘录）

要通过 `PDO` 发送 SQL，必须使用 `query()` 方法执行语句。像往常一样，你需要一种转义特殊字符的方法。这再次可以通过预处理语句来完成。首先，可以使用名为 `prepare()` 的方法解析 SQL 查询，其中占位符以冒号开头。然后，`bindValue()` 方法将值绑定到占位符名称（`bindParam()` 也可用，但需要可能被引用的值）。最后，`execute()` 方法将语句发送到数据库。

### 通过 `PDO` 检索查询结果

```
$result = $db->query();
$result->fetch(PDO::FETCH_ASSOC);
```

```
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
try {
$db = new PDO('sqlite:PDOquotes.db');
$result = $db->query('SELECT * FROM quotes');
while ($row = $result->fetch(PDO::FETCH_ASSOC)) {
```

```
printf(
    '<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
    htmlspecialchars($row['id']),
    htmlspecialchars($row['quote']),
    htmlspecialchars($row['author']),
    htmlspecialchars($row['year'])
);
}
} catch (PDOException $ex) {
    echo 'Connection failed: ' .
    htmlspecialchars($ex->getMessage());
}
?>
</table>
```

### 通过 `PDO` 检索数据（`pdo_fetch.php`；摘录）

最后，使用 `PDO` 读取 SQL 查询的结果采用标准方法：向服务器发送 `SELECT` 查询，然后使用 `while` 循环遍历结果。这里的迭代使用 `fetch()` 方法完成。你可以提供诸如 `PDO::FETCH_ASSOC`（返回关联数组）或 `PDO::FETCH_OBJ`（返回对象）等常量作为参数。或者，你可以使用 `fetchAll()` 方法并获取数组的数组，以便一次性获得所有数据。

此代码使用 `fetch()` 和 `PDO::FETCH_ASSOC` 从数据源读取所有数据。

**注意：** 截至本文撰写时，`PDO` 尚不能被视为稳定；因此，`PDO` 的 API 或行为将来可能会发生变化。此外，如果你尝试使用 `PDO`，请注意它尚未被证明像 PHP 本身一样可靠。

### PEAR 提供了什么？

以下 PHP 扩展和应用程序仓库（PEAR）软件包（其中之一）提供了数据库抽象层和其他用于数据库访问的实用功能：

- `DB_DataObject` 可以从对象创建 SQL。
- `MDB_QueryTool` 在构建 SQL 查询方面提供一些帮助。
- `MDB2` 是一个功能非常丰富的数据库抽象层。

如果你使用 Symfony 或 Zend Framework 等框架，你在那里也会有额外的数据库访问选项。

## 第10章 使用 XML

在炒作之后，可扩展标记语言（XML）现在几乎在任何地方都被真正使用。备受关注的应用是 Web 服务，这项技术在第 9 章“使用其他数据库”中有详细介绍。然而，XML 也可用于其他地方。它是存储任何类型数据的良好格式。

使用 XML 背后的任务始终相同：从 XML 读取数据并向其中写入数据。因此，本章重点介绍这些任务并展示如何实现它们。

不幸的是，PHP 4 的 XML 支持 somewhat 有限。一些扩展被证明并不十分稳定。随着 PHP 5 和重新设计的 XML 支持，这一情况发生了巨大变化。因此，我们在本章（以及本书其余部分）中完全省略了 PHP 4。在 PHP 5.1 和 5.2 中，添加了一些新功能，本章也涵盖了这些功能。

作为本章中的示例 XML 文件和格式，以下代码中的 XML 重用了前一章中的 `quotes` 数据库示例。如你所见，`<quotes>` 是根元素，每个 `quote`（包括其作者和短语创造年份）包含在 `<quote>` 元素中。

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<quotes>
<quote year="1991">
<phrase>Hasta la vista, baby!</phrase>
<author>Arnold Schwarzenegger</author>
</quote>
</quotes>
```

示例 XML 文件（`quotes.xml`；摘录）

### 使用 SAX 解析 XML

```
$sax = xml_parser_create();
xml_parser_set_option($sax, XML_OPTION_CASE_FOLDING, false);
xml_parser_set_option($sax, XML_OPTION_SKIP_WHITE, true);
xml_set_element_handler($sax, 'sax_start',
'sax_end');
xml_set_character_data_handler($sax, 'sax_cdata');
xml_parse($sax, file_get_contents('quotes.xml'), true);
xml_parser_free($sax);
```

简单的 XML API（SAX）是一种解析 XML 文档的方法，但不用于验证它们。

你使用 `xml_parser_create()` 创建 SAX 解析器，可选择提供编码作为参数。此解析器可以查看 XML 文件并对各种事件做出反应。以下三个事件是最重要的：

- 元素的开始
- 元素的结束
- CDATA 块

然后你可以为这些元素定义处理函数，并使用它们将 XML 转换为其他内容，例如超文本标记语言（HTML）。以下列表展示了这一点，并将 XML 文件的内容作为项目符号 HTML 列表输出，如图 10.1 所示。函数 `xml_set_element_handler()` 设置元素的开始和结束的处理程序，而 `xml_set_character_data_handler()` 设置 CDATA 块的处理程序。通过 `xml_parser_set_option()`，你可以配置处理程序，例如忽略空白并将标签名称作为区分大小写处理（然后标签名称不会自动转换为大写字母）。以下代码包含处理函数的代码：

```
function sax_start($sax, $tag, $attr) {
    if ($tag == 'quotes') {
        echo '<ul>';
    } elseif ($tag == 'quote') {
        echo '<li>' . htmlspecialchars($attr['year']) . '
        ': ';
    } elseif ($tag == 'phrase') {
        echo '"';
    } elseif ($tag == 'author') {
        echo ' (';
    }
}
```

```
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

![](img/2862989e5dc7f1b1d0bc64321737f084_293_0.png)

图 10.1 从 XML 创建的 HTML

### 使用 `XMLReader` 解析 XML

```
echo '<ul>';
$xml = new XMLReader();
$xml->open('quotes.xml');
```

```
while ($xml->read()) {
    if ($xml->nodeType == XMLReader::ELEMENT) {
        if ($xml->localName == 'phrase') {
            $xml->read();
            echo '<li>' . htmlspecialchars($xml->value) . 
                '<\/li>';
        }
    }
}
echo '<\/ul>';
```

使用 `XMLReader` 解析 XML（`xmlreader.php`）

`XMLReader` 是 Microsoft .NET 中 `XmlTextReader` 接口的克隆，从 5.1.0 版本开始成为 PHP 发行版的一部分，并且默认激活。乍一看，它看起来与 SAX 解析器相似，但存在一个根本区别：SAX 是基于事件的解析器，而 `XMLReader` 使用一个光标遍历 XML 文件中的所有元素。

要使用 `XMLReader`，你实例化 `XMLReader` 类，然后打开文件（`open()` 方法）。常用的模式使用 `while` 循环和 `read()` 方法遍历所有元素。

在该循环中，你可以确定光标到达的节点的类型（`nodeType` 属性），然后相应地采取行动（例如，通过读取标签名称 [`localName` 属性] 并访问文本节点的值 [`value` 属性]）。

前面的代码再次从 XML 文档中读取所有短语并将其作为项目符号列表输出。

### 使用 DOM 读取 XML

```
<?php
$dom = new DOMDocument();
$dom->load('quotes.xml');
echo '<ul>';
foreach ($dom->getElementsByTagName('quote') as $element) {
    $year = $element->getAttribute('year');
    foreach (($element->childNodes) as $e) {
        if ($e instanceof DOMElement) {
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




# 使用 DOM 解析 XML

W3C 的文档对象模型（DOM）定义了一种统一的方式来访问 XML 结构中的元素。因此，使用 JavaScript 的 DOM 访问在 HTML 页面中访问元素，以及使用 PHP 的 DOM 访问在 XML 文件中访问元素，相当相似。

DOM 扩展随 PHP 捆绑，因此无需安装。首先，你实例化一个 `DOMDocument` 对象。

创建 `DOMDocument` 对象后，你可以使用 `load()` 加载文件，或使用 `loadXML()` 加载字符串。这个新对象除其他功能外，还支持两个方法：`getElementsByTagName()` 和 `getElementById()`，它们返回具有特定标签名的所有节点，或通过 ID 标识的特定元素。然后，每个节点都会公开一些属性，如下所示：

- `firstChild` — 第一个子节点
- `lastChild` — 最后一个子节点
- `nextSibling` — 下一个节点
- `previousSibling` — 上一个节点
- `nodeValue` — 节点的值

前面的代码使用 DOM 访问 XML 文件中的所有引文并将其输出。

请注意，代码清单使用了 `instanceof`，因此仅在 `DOMElement` 类型的节点中对标签名进行求值。这是因为空白会被视为 DOM 节点（但类型为 `DOMText`）。

## 使用 DOM 编写 XML

```php
<?php

$dom = new DOMDocument();

$dom->load('quotes.xml');

$quote = $dom->createElement('quote');

$quote->setAttribute('year', $_POST['year']);

$phrase = $dom->createElement('phrase');

$phraseText = $dom->createTextNode($_POST['quote']);

$phrase->appendChild($phraseText);

$author = $dom->createElement('author');

$authorText = $dom->createTextNode($_POST['author']);

$author->appendChild($authorText);

$quote->appendChild($phrase);

$quote->appendChild($author);

$dom->documentElement->appendChild($quote);

$dom->save('quotes.xml');

echo 'Quote saved.';

?>
```

除了读取访问之外，还可以使用 PHP 的 DOM 支持从头构建完整的 XML 文档。这可能看起来有点笨拙，但在需要自动解析大量数据时非常有效。

`createElement()` 方法用于创建新元素。您可以通过追加新的文本节点（使用 `createTextNode()` 创建）来设置其内容，并使用 `setAttribute()` 添加属性。然后，使用 `documentElement` 访问 XML 文件的根元素，再调用 `appendChild()`。最后，`save()` 将整个 XML 文件写入硬盘。

前面的代码将作者、引文和年份保存到 XML 文档中，并追加到已有数据之后。

注意：PHP 5 的 DOM 扩展不提供类似 `set_content()` 的方法（PHP 4 中有），因此您必须使用 `createTextNode()` 方法定义节点的文本值，如前面的代码所示。

## 使用 XMLWriter 编写 XML

```php
<?php

header('Content-type: text/xml; charset=ISO-8859-1');

$xml1 = new XMLWriter();

$xml1->openMemory();

$xml1->startDocument('1.0', 'ISO-8859-1');

$xml1->startElement('quotes');

$xml1->writeAttribute('year', '1991');

$xml1->startElement('phrase');

$xml1->text('Hasta la vista, baby!');

$xml1->endElement();

$xml1->startElement('author');

$xml1->text('Arnold Schwarzenegger');

$xml1->endElement();

$xml1->endElement();

$xml1->endDocument();

echo $xml1->outputMemory();

?>
```

XMLWriter 是 XMLReader 的姊妹扩展，在 PHP 5.1.2 版本中引入。它提供了一套结构化的 API 来创建 XML 文件，在动态创建 XML 数据（例如，处理来自数据库的数据）时尤其有价值。

该 API 非常简单：在内存中打开 XML 文档后，您可以使用特定的函数来启动文档、启动和结束元素，以及写入属性和文本节点。前面的代码创建了本章开头的 XML 文件（缩进除外）；结果见图 10.2。

![](img/2862989e5dc7f1b1d0bc64321737f084_299_0.png)

## 使用 SimpleXML

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

PHP 5.1 中最出色的新特性之一是 SimpleXML 扩展，这个想法借鉴自 CPAN 中的一个 Perl 模块。这种方法既简单又巧妙。访问 XML 最直观的方式可能就是面向对象编程（OOP）方法：子节点是其父节点/对象的属性，XML 属性则成为对象属性。这使得访问 XML 变得非常容易，并且完全支持迭代器，因此可以使用 `foreach`。

这段代码使用 `simplexml_load_file()` 加载文件——你也可以对字符串使用 `simplexml_load_string()`——然后读取所有信息。

将其与 DOM 方法进行比较。在某些情况下，SimpleXML 可能比 DOM 慢，但编写代码的速度要快得多。

注意：写入操作也很容易完成。但是，如果没有外部帮助，就不能追加元素（例如，使用 DOM 并通过 `simplexml_import_dom()` 将此 DOM 加载到 SimpleXML 中）。

## 将 XPath 与 SimpleXML 结合使用

### `$xml->xpath()`

```php
<?php

$xml = simplexml_load_file('quotes.xml');

foreach ($xml->xpath('*/quote') as $quote) {

    echo '<p>' . htmlspecialchars($quote) . '</p>';

}

?>
```

SimpleXML 最不为人知的秘密之一是，该扩展内置了对 XPath（XML 查询语言）的支持。使用起来很简单：创建 SimpleXML 对象后，你可以使用 `xpath()` 方法获取所有匹配的节点。

## 使用 XSL 转换 XML

```php
<?php

$xml = new DOMDocument();

$xml->load('quotes.xml');

$xsl = new DOMDocument();

$xsl->load('quotes.xsl');

$xslt = new XSLTProcessor();

$xslt->importStylesheet($xsl);

$result = $xslt->transformToDoc($xml);

echo $result->saveXML();

?>
```

将 XML 转换为另一种格式通常由 XSLT（XSL 转换）完成。在 PHP 中，XSLT 由 libxslt 实现，在 Windows 上可以使用 `php_xslt.dll`（在 php.ini 中）启用，在其他平台上使用 `--with-xslt` 开关启用。编写 XSL 文件可能很困难，但之后的 PHP 代码相当简单：将 XML 和 XSLT（它也是一个 XML 文档）加载到 DOM 对象中，然后实例化一个 `XSLTProcessor` 对象。调用 `importStylesheet()`，然后调用 `transformToDoc()`。

前面的代码包含了这些步骤的代码，下载仓库中的 `quotes.xsl` 文件包含将引文 XML 转换为众所周知的 HTML 项目符号列表的标记。

## 验证 XML

```php
<?php

$dom = new DOMDocument();

$dom->load('quotes.xml');

echo 'Validation ';

echo (($dom->relaxNGValidate('quotes.rng')) ? 'succeeded.' : 'failed.');

?>
```

PHP 可以针对三类文件验证 XML：文档类型定义（DTD）、Schema（.xsd）和 relaxNG。对于后两类，可以使用 DOM 对象的以下四种方法：

- `schemaValidate('file.xsd')` — 根据 Schema 文件验证
- `schemaValidateSource('...')` — 根据 Schema 字符串验证
- `relaxNGValidate('file.rng')` — 根据 relaxNG 文件验证
- `relaxNGValidateSource('...')` — 根据 relaxNG 字符串验证

前面的代码使用 `relaxNGValidate()` 针对不匹配的 relaxNG 文件验证一个（格式良好的）XML 文件。如果在文件 `"quotes.rng"` 中将 `<element name="person">` 改为 `<element name="author">`，验证就会成功。

提示：创建 relaxNG 文件可能相当困难；Java 工具 Trang（可从 http://www.thaiopensource.com/relaxng/trang.html 获取）可以读取 XML 文件并从中创建 relaxNG Schema 或 DTD 文件。

验证 Schema 的方法与此类似，见下载仓库中的 `validate-xsd.php` 文件。对于 DTD 的验证，你需要对 XML 稍作修改。DTD 文件必须包含在文件中，或者像这样引用：

```xml
<!DOCTYPE note SYSTEM "quotes.dtd">
```

然后，只需将 XML 文档加载到 DOM 对象中并调用 `validate()`。下面包含相应的代码；代码仓库中引用的文件在 DTD 中包含一个故意引入的错误（month 而不是 year）：

```php
<?php

    $dom = new DOMDocument();

    $dom->load('quotes-dtd.xml');

    echo 'Validation '

        . (($dom->validate()) ? 'succeeded.' : 'failed.');

?>
```

## PEAR 提供了什么？

截至本文撰写时，PHP 扩展和应用程序仓库（PEAR）中的 XML 部分包含 35 个软件包，太多无法一一列举。以下是其中一些：

- XML Beautifier 可格式化 XML 文档，使其更美观。
- XML_DTD 允许解析 DTD，即使在 PHP 4 下也行。
- XML_Parser2 提供了一个高级 XML 解析器。
- XML_Serializer 将 XML 文件转换为数据结构，反之亦然。
- XML_Util 包含大量用于处理 XML 的辅助函数。

# 与他人通信

先前讨论的大多数短语都在所使用的 PHP 脚本和 Web 服务器的生态系统内工作。然而，由于某些短语也可以被他人理解，本章涵盖了一些此类示例。你可以通过多种方式连接到远程服务器。

```php
<?php

echo file_get_contents('http://www.php.net/');

?>
```

超文本传输协议（HTTP）可能是 PHP 用于与其他系统连接（除各种数据库协议外）最常用的协议。从 PHP 4.3 开始，连接此类数据源变得非常容易，因为该版本中 PHP 的流支持得到了极大改进。（当然，以本代码所示方式使用 HTTP 在更早的 PHP 版本中也已可能。）其思想是，当你使用文件操作时，你访问的是数据流。实际上，无论是本地系统上的文件、网络共享上的文件，还是通过 HTTP、文件传输协议（FTP）或其他受支持协议连接的远程服务器上的文件，都无关紧要。只需提供适当的文件名，PHP 就会处理其余部分。前面代码展示了这一点：它打开 PHP 主页，并在浏览器中打印其超文本标记语言（HTML）代码。用一行代码实现，无法更简单。图 11.1 包含输出。

![](img/2862989e5dc7f1b1d0bc64321737f084_307_0.png)

图 11.1 一行代码打印 PHP 主页的 HTML 标记。

警告：出于安全原因，你可以在 php.ini 中通过将 `allow_url_fopen` 设置为 Off 来关闭此行为；因此，在你无法控制的 Web 服务器上---例如大型互联网服务提供商（ISP）的共享托管---你不能依赖它。

如果你想自行控制 HTTP 请求，可以使用套接字。首先，使用 `fsockopen()` 向 Web 服务器打开一个套接字，如果成功，则发送格式良好的 HTTP 请求。以下代码实现了这一点，同样查询 PHP 主页：

```php
<?php

$fp = @fsockopen('www.php.net', 80, $errno, $errstr, 30);

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

    echo "Error: $errstr ($errno)";

}

?>
```

输出相同，只有一个区别：套接字方法还会返回服务器发送的所有 HTTP 标头，而流包装器则省略了它们。

注意：当你必须处理 HTTP 安全（HTTPS）资源（例如使用 SSL [安全套接字层] 保护的网站）时，这两种方法仍然有效，只是需要稍作修改：

- 使用 `file_get_contents()` 等文件函数时，只需提供一个 `https://` 统一资源定位符（URL）即可。
- 使用套接字时，使用 `ssl://` URL。

## 连接 FTP 服务器

```php
<?php

$data = file_get_contents('ftp://mirror.netcologne.de/apache.org/httpd/README.html');

file_put_contents('Apache-README.html', $data);

echo 'File written.';

?>
```

当你访问 FTP 服务器时，PHP 的流包装器也非常方便。你只有读取权限，但访问仍然是二进制安全的。此代码展示了如何使用 `file_get_contents()` 从 FTP 服务器下载 Apache 的当前 README 文件并将其保存到本地硬盘。写入也可能；只需使用 `file_put_contents()` 或 `fopen()` 的正确文件模式即可。注意，不过，同时进行读写尚不支持。

提示：如果不提供任何凭据，PHP 会尝试使用大多数公共 FTP 服务器提供的访客账户登录到 FTP 服务器。你也可以自行提供凭据：




```php
$data = file_get_contents('ftp://USER:PASSWORD@ftp.example.com/');
```

这也适用于 HTTP 资源（参见前面的短语）！

PHP 还内置了对 FTP 的支持以及一组特殊函数，实现了相关请求评论（RFC）中定义的完整 FTP 功能。在 Windows 发行版中，这默认启用，而在其他系统上，PHP 必须使用 `--enable-ftp` 开关进行配置。然后，使用 FTP 服务器通常包括以下步骤：

1. 使用`ftp_connect()`连接到服务器。
2. 使用`ftp_login()`登录。
3. 使用`ftp_chdir()`进入目标目录。
4. 从 FTP 服务器读取文件（`ftp_get()`）或向其写入文件（`ftp_put()`）。
5. 使用`ftp_close()`关闭连接。

由于读取比写入更常见，以下展示了前者的执行。再次从 FTP 服务器获取 Apache README：

```php

<?php

$ftp = @ftp_connect('mirror.netcologne.de');

$login = @ftp_login($ftp, 'anonymous',

'email@example.com');

if ($ftp && $login) {

    ftp_chdir($ftp, '/apache.org/httpd/');

    ftp_get($ftp, 'Apache-README-ftp.html',

    'README.html', FTP_ASCII);

    echo 'File written.';

    ftp_close($ftp);

} else {

    echo 'Error!';

}

?>

```

使用内置函数读取 FTP 文件（`ftp-functions.php`）

请注意 `ftp_get()` 的语法有点奇怪。在 FTP 资源之后，你首先必须提供本地文件名，然后必须提供远程文件名。（直观上，你会期望顺序相反。）最后一个参数是传输模式：文本文件使用 FTP ASCII，其他所有数据使用 FTP BINARY。

### 检查服务器是否仍在响应

```php

<?php

$server = 'localhost';

$port = '80';

$status = 'unavailable';

$fp = @fsockopen($server, $port, $errno, $errstr, 10);

if ($fp) {

    $status = 'alive, but not responding';

    fwrite($fp, "HEAD / HTTP/1.0\r\n\r\n");

    fwrite($fp, "Host: $server\r\n\r\n");

    if (strlen(@fread($fp, 1024)) > 0) {

        $status = 'alive and kicking';

    }

    fclose($fp);

}

echo "The server is $status.";

?>

```

检查服务器状态（`serverstatus.php`）

假设你有一个 Web 服务器，并且想定期检查它是否再次崩溃。在这种情况下，使用 PHP 脚本来执行此任务是个好主意。只需向服务器打开一个套接字并等待。（`fsockopen()` 的最后一个参数是超时值。）在此时间过去后，你就知道服务器是否在线或离线。

**提示：** 如果只需要检查一个服务器的状态，这效果很好。如果有多个服务器，这种方法有一些缺点。`fsockopen()` 的调用可能需要长达超时值的时间才会执行下一个命令。因此，所有服务器都是顺序且同步检查的。对于多个服务器来说，这花费的时间太长了。然而，使用 PHP 5 和流套接字，可以异步完成。代码有点复杂，但 Wez Furlong 在 `http://wezfurlong.org/blog/2005/may/guru-multiplexing/` 上对此方法进行了详细解释。

SOAP 一度代表简单对象访问协议，但由于它既不简单也与对象访问关系不大，今天 SOAP 就只是代表... SOAP。它是一个相当复杂的协议，但克服了 XML-RPC 的许多限制（顺便说一下，XML-RPC 由一些也参与 SOAP 工作的人创建）。

大多数情况下，XML-RPC 或 SOAP 调用通过 HTTP 作为承载协议传输。然而，其他协议也是可能的，包括简单邮件传输协议（SMTP）甚至用户数据报协议（UDP）。

使用 SOAP 时，你需要考虑另一个重要方面：当你确切知道 Web 服务是如何实现的时，你也知道如何调用（访问或使用）它。然而，很多时候这些信息不可用，因此必须有一种 Web 服务的自我描述，其中包含所有相关信息，例如暴露了哪些方法和函数，它们期望哪些参数和数据类型，以及它们返回什么。这也可以使用专门制作的 XML 文件来完成。其背后的标准是 Web 服务描述语言（WSDL）。今天，WSDL 用于所有相关的 Web 服务，因为它使使用它们变得相当简单。大多数服务器端技术提供一种（或多种）方式来读取 WSDL，然后像访问本地可用类一样访问 Web 服务。

生成所有这些 XML 相当复杂。并不是说 PHP 没有良好的 XML 支持，但语法可能相当困难。然而，一些扩展和外部包使使用 Web 服务变得容易得多。以下短语各自实现了一个 Web 服务，只需将两个数字相加。你肯定会更发挥想象力，根据本章所学内容创建一些真实世界的Web服务。另外，我们重点介绍SOAP Web服务；XML-RPC如今似乎不太常用了，而JSON Web服务（本章后面会介绍）已经变得更为流行。

### 使用NuSOAP创建Web服务

```
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

一个使用NuSOAP的SOAP Web服务（`soap-nusoap.server.php`）

在 `http://nusoap.sourceforge.net/` 上，你会发现NuSOAP，它是PHP最著名的外部SOAP类之一。有些人甚至可能知道它的前身SOAPx4。如今，其发布新版本的频率不高，但这个库相当稳定。你可能还想查看Subversion（SVN）仓库以获取最新代码。那里可能有几个文件，但你需要的只有`nusoap.php`。

使用NuSOAP创建Web服务非常简单，因为该模块处理了所有麻烦的事情，包括SOAP。只需按以下步骤操作：

1. 编写你想作为Web方法暴露的函数。
2. 实例化`soap_server`类。
3. 向SOAP服务器注册你的函数。
4. 调用`service()`方法并提交`$HTTP_RAW_POST_DATA`作为参数。

这段代码使用NuSOAP实现了一个SOAP服务器。图11.2展示了当你试图直接从客户端调用Web服务时浏览器的输出。错误消息提示XML为空——这是理所当然的，因为我们没有发送请求！

![](img/2862989e5dc7f1b1d0bc64321737f084_316_0.png)

图11.2 这个错误消息是个好兆头；脚本似乎可以工作（目前而言）。

![](img/2862989e5dc7f1b1d0bc64321737f084_319_0.png)

图11.4 这份WSDL是由NuSOAP生成的，而不是程序员编写的。

### 使用NuSOAP调用Web服务

```
<?php

    require_once 'nusoap.php';

    $soap = new soapclient('http://localhost/wsdl-nusoap-server.php?wsdl', true);

    $proxy = $soap->getProxy();

    $result = $proxy->add(47, 11);

    echo "47 + 11 = $result";

?>
```

使用NuSOAP调用Web服务（`wsdl-nusoap-client.php`）

实际上，使用NuSOAP服务比创建它还要容易。你只需加载WSDL文件，然后获得一个所谓的代理类。（这是一个本地类，其行为就像Web服务也是一个本地类一样。）因此，你可以直接调用Web服务的方法，NuSOAP会处理其余所有事情（包括打开到远程服务器的连接、组装和解析XML等）。

要做到这一点，必须实例化`soapclient`类（不带下划线字符），然后`getProxy()`方法会创建代理类。上面的代码针对前一个示例中的演示服务实现了这个流程。注意WSDL文件的URL：它是Web服务的URL末尾加上`?wsdl`；请根据你的系统相应地更改URL。

**注意：** 在URL末尾附加`?wsdl`以获取Web服务的WSDL描述，这个想法借鉴自Microsoft .NET（现在也被其他技术采用）。然而，在.NET中该后缀不区分大小写，而NuSOAP要求使用小写字母。在跨平台开发时请记住这一点。

### 使用PHP 5 SOAP扩展创建Web服务

```
<?php

$soap = new SoapServer(null, array('uri' => 'http://php.phrasebook.org/'));

$soap->addFunction('add');

$soap->handle();

function add($a, $b) {

    return $a + $b;

}

?>
```

一个使用PHP 5 SOAP的Web服务（`soap-php5-server.php`）

PHP 5的关键特性之一是新的SOAP扩展。由于它是用C语言编写的，因此比任何纯PHP代码都快得多。然而，这个扩展相对较新，因此仍然存在一些小问题和不完善的功能。不过，它通常能很好地工作。

要使用该扩展，你必须使用`--enable-soap`配置PHP；Windows用户必须在`php.ini`配置文件中添加`extension=php_soap.dll`。然后，扩展即可使用，编写SOAP服务器也变得相当容易。

同样，只需很少的步骤：实例化`SoapServer`类，使用`addFunction()`添加你的函数，最后调用`handle()`。

### 使用PHP 5 SOAP扩展自动生成WSDL

PHP 5 SOAP的最大缺点是无法使用它自动生成WSDL。这一点并不常被提及，但它确实在现实生活中造成问题。WSDL非常复杂，其中的错误难以察觉，甚至更难找到。然而，你仍然可以通过几种方式为Web服务创建这样的WSDL描述，其中大部分已在真实项目中使用。

- 使用`NuSOAP`或`PEAR::SOAP`创建一个类似的服务，仅为了获取WSDL——只需修改`<soap:address>`元素
- 使用`Ctrx_SOAP_AutoDiscover`类（可从 `http://crtx.org/index.php?area=Main&page=Crtx_SOAP_AutoDiscover` 获取）
- 使用Webservice Helper工具（可从 `http://www.jool.nl/new/index.php?file_id=1` 获取）
- 使用`WSDL_Gen`类（可从 `http://www.schlossnagle.org/~george/php/WSDL_Gen.tgz` 获取）

因此你可以看到，WSDL支持正在开发中，但不是作为SOAP扩展本身的一部分，而是以外部项目的形式。希望有一天这种情况会改变。

如果你最终拥有了服务的WSDL描述（在下载归档中，你会找到一个名为`AddService.wsdl`的文件，它源自`PEAR::SOAP`生成的WSDL），服务器的代码只需稍作更新。`SoapServer`实例化的第一个参数接收WSDL URL；此外，Web服务的方法必须放在一个类中。然后，`setClass()`向SOAP扩展提供要使用的类名：

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

一个支持WSDL的、使用PHP 5 SOAP的Web服务（`wsdl-php5-server.php`）

### 使用PHP 5 SOAP扩展调用Web服务

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

使用PHP 5 SOAP调用Web服务（`wsdl-php5-client.php`）

调用同样很容易，只要你拥有WSDL描述。这段代码调用Web服务并捕获任何错误，这要归功于PHP 5的try-catch机制。

提示：为了提高性能，PHP 5的SOAP扩展默认会缓存WSDL。以下是`php.ini`中推荐的标准设置：

```
[soap]

; Enables or disables WSDL caching feature.

soap.wsdl_cache_enabled=1

; Sets the directory name where SOAP extension

will put cache files.

soap.wsdl_cache_dir="/tmp"

; (time to live) Sets the number of seconds while

cached file will be used

; instead of original one.

soap.wsdl_cache_ttl=86400
```

当开发Web服务并可能更改WSDL时，这当然是个不费脑筋的决定。因此，在开发期间将`soap.wsdl_cache_enabled`设置为Off，但在生产服务器上应将其打开。

### 使用Ajax

维基百科列出了Ajax一词几十种不同的含义，包括一支荷兰足球队、荷马《伊利亚特》中的两个人物，以及一种家用清洁产品。然而，自2005年以来，Ajax还代表Asynchronous JavaScript + XML。这项技术远非新事物（其底层技术——来自JavaScript的XML HTTP请求——已得到Internet Explorer、Firefox、Safari和Chrome最新版本的支持；而且，XML对此并不是必需的），但直到这个奇怪的术语被创造出来之后，人们才真正开始使用它。

其基本原理是，JavaScript现在可以调用远程服务器，然后处理返回值，而无需重新加载整个页面。当然，这与PHP关系不大；然而，一些Ajax类使得在PHP中使用Ajax变得非常容易。

这个示例展示了 Ajax 的一个非常简短的演示。此示例使用可在 `www.modernmethod.com/sajax` 获取的 Sajax 工具包（S 代表 simple 简单）。有许多 Ajax 库和框架可供选择，因此请随意选择你最喜欢的一个；我们在这里只选择一个简单的，以专注于 Ajax 和 PHP 的结合。

此示例的完整代码相当长，因为同时需要 PHP 和 JavaScript。首先，你需要服务器端逻辑。为此，加载了 Sajax 工具包，它作为单个 PHP 文件提供。然后你“导出”（注册）所有希望从客户端使用的 PHP 函数。以下示例包含一个生成随机 RGB 颜色的小函数：

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

应用程序的服务器端部分（`ajax.php`：摘录）

在客户端，对（PHP）函数 `sajax_show_javascript()` 的调用完成了大部分工作；它创建了一些 JavaScript 代码行，在后台处理对 Web 服务器的请求。然后，所有之前已注册的 PHP 函数都可以通过在函数名称前加上 `x_` 来在客户端调用。你必须提供的一个参数是回调函数的名称；当服务器端响应请求时，该函数将被调用。

以下代码每五秒调用一次 `randomColor()` PHP 函数，然后以这种随机颜色写入文本——全部无需服务器往返！图 11.5 显示了结果：

```
<script type="text/javascript">

<?php

sajax_show_javascript();

?>

changeColor();

setInterval(changeColor, 5000);

function changeColor() {

    x_randomColor(randomColor_callback);

}

function randomColor_callback(result) {

    var text = '<span style="color: ' + result + '">A colorful acronym ...</span>';
```




```
    document.getElementById('output').innerHTML =

    text;

}

</script>

...

<div id="output"></div>
```

应用程序的客户端部分（`ajax.php`；摘录）

![](img/2862989e5dc7f1b1d0bc64321737f084_327_0.png)

图 11.5 文本出现，感谢 JavaScript 代码调用 PHP

### 与服务器交换数据

在前面的示例中，我们与服务器交换的数据相当简单——一个简单的字符串。然而，在实际应用中，我们需要从客户端发送到服务器并返回的往往是更复杂的数据。XML 可用作交换格式，但它臃肿，因此不适合高性能应用。PHP 的 `serialize()` 和 `unserialize()` 方法可用于将复杂信息转换为可通过 HTTP 交换的字符串，但 JavaScript 并没有内置的对应功能。

与 JavaScript 进行数据交换的事实标准是 JSON，即 JavaScript 对象表示法。非官方主页 at http://json.org/ 详细解释了该格式，但基本上 JSON 概括了 JavaScript 规范中解释数组的部分。例如，看看这个字符串：

```
[

{"url": "http:\\/\\/json.org\/", "text": "JSON"},

{"url": "http:\\/\\/php.net\/", "text": "PHP"}

]
```

这是在 JavaScript 中可用于定义包含两个关联数组（或对象，正如某些人所称，尽管这些元素实际上并不是对象）的数组的语法。现代浏览器具有将此类字符串轻松转换为真实 JavaScript 值的内置功能（并且针对旧版本也有变通方法），因此 JSON 非常适合 Ajax 应用。

从 5.2 版本开始，PHP 原生支持 JSON。函数 `json_encode()` 将可序列化的 PHP 值转换为 JSON，而 `json_decode()` 将 JSON 字符串转换回 PHP 可处理的内容。以下代码基本上创建了前面的 JSON 字符串，只是去除了缩进和额外的空白字符：

```
<?php

class LinkData {

    public $url;

    public $text;

    public function __construct($url, $text) {

        $this->url = $url;

        $this->text = $text;

    }

}

$data = array(

    new LinkData('http://json.org/', 'JSON'),

    new LinkData('http://php.net/', 'PHP')

);

echo json_encode($data);

?>
```

JSON 服务器端点（`json.php`）

在客户端，JavaScript 代码随后可以调用 PHP 脚本并处理数据。使用像流行的 jQuery（http://jquery.com/）这样的 JavaScript 库时，处理 JSON 数据会相当容易（参见图 11.6）。以下代码以项目符号列表的形式显示 JSON 字符串中包含的信息：

```
<script type="text/javascript" src="http://code.jquery.com/jquery-latest.js"></script>

<script type="text/javascript">

$(function() {

    $.getJSON("json.php", function(data) {

        $.each(data, function(key, value) {

            $("<a>").attr("href", value.url)

                .html(value.text)

                .wrap("<li>")

                .parent()

                .appendTo("ul");

        });

    });

});

</script>

...

<body>

    <ul></ul>
</body>
```




## 使用 jQuery 的 JSON 客户端（`json.html`）

![](img/2862989e5dc7f1b1d0bc64321737f084_330_0.png)

图 11.6 JSON 数据被解析，然后作为列表显示，感谢 jQuery 调用 PHP 代码。

### PEAR 提供什么？

除了本章中提到的几个模块外，以下 PHP 扩展和应用程序仓库（PEAR）包在通过 PHP 与他人连接时提供的功能可能很有帮助：

- PEAR 的 HTTP 类别提供了一些相关包，包括 `HTTP`、`HTTP_Header`、`HTTP_Request2` 和 `HTTP_Server`。
- 同样，你可以在 Networking 类别中找到有用的包，包括 `Net_FTP`、`Net_IMAP` 和 `Net_Socket`。
- PEAR 的 Services 类别包含多个类，它们为知名 Web 服务提供易于使用的接口。

## 索引

### 符号和数字

- `!=` 运算符，比较字符串，26
- `[...]` 特殊字符，在正则表达式中，28
- `*`（星号），在正则表达式中，28
- `\`（反斜杠），在正则表达式中，29
- `^`（插入符号），在正则表达式中，27
- `$`（美元符号），在正则表达式中，27
- `.`（点），在正则表达式中，28
- `==` 运算符，比较字符串，8-10，26
- `|`（管道），在正则表达式中，28
- `+`（加号），在正则表达式中，28
- `?`（问号），在正则表达式中，27
- `$_COOKIE` 数组，170
- `$_FILES` 数组 检索上传文件信息，155
- `$_GET` 数组
  - 访问表单数据，126-127
  - 图形化提交按钮，144
  - 验证必填字段，145
  - 预填充文本字段，131，133-134
  - 预选单选按钮，136
  - 预选选择列表，141-142
  - 读取表单数据，123
- `$_POST` 数组
  - 访问表单数据，126-127
  - 图形化提交按钮，144
  - 验证必填字段，145
  - 预填充文本字段，131，133-134
  - 预选单选按钮，136
  - 预选选择列表，141-142
- `$_REQUEST` 数组，访问表单数据，126-127
- 401 状态码，198

### A

- 抽象类，104-107
- access，文件访问
  - PHP 内置类，221-222
  - 相对路径，209-210
  - 安全陷阱，210-211
- `addslashes()` 函数，265
- AES（高级加密标准），15
- Ajax，313-316
- `ajax.php`，314-315
- `array()` 函数，创建数组，40
- `array_filter()` 函数，66
- `array_map()` 函数，62
- `array_multisort()` 函数，54
- `array_rand()` 函数，67-68
- `array_walk()` 函数，64
- arrays
  - 对元素应用效果，62-65
  - 转换为变量，47-48
  - 将字符串转换为数组，48-49
  - 转换为字符串，49
  - 创建，40-41
- 过滤，65-66
- 用于表单数据，125
- 循环遍历
  - 关联数组，43
  - 嵌套数组，44-47
  - 数值数组，41-43
- 嵌套，40
- 检索随机元素，67-68
- 排序
  - 按字母顺序，50-51
  - 关联数组，51-52
  - 自然排序，57
  - 嵌套数组，53-54
  - 嵌套关联数组，55-56
- QuickSort 算法，58
- 特殊语言字符，59-60
- ASCII 代码，保护电子邮件地址，20-22
- `asort()` 函数，52
- 关联数组
  - 循环遍历，43
  - 排序，51-52
- attacks，目录遍历，210-211
- Auth 包（PEAR），199
- 身份验证
  - 会话管理，195-196
  - 不使用会话，197
- 自动加载类，109-111

### B

- `basename()` 函数，210
- `bzclose()` 函数，225-226
- Bzip2 压缩包，224-226
- `bzopen()` 函数，225-226
- `bzread()` 函数，226
- `bzwrite()` 函数，225-226

### C

- 预选复选框，138
- `checkdate()` 函数，82
- 计算字符串校验和，16-18
- `chr()` 函数，21
- 类
  - 抽象，104-107
  - 自动加载，109-111
  - 继承，102-103
  - 定义，100-101
  - Trait，120-122
- 克隆对象，111-112
- 关闭
  - 文件，204
  - 会话，187
- `compareChar()` 函数，60
- 字符串比较，8
- `compress.bzip2://`，224-226
- `compress.zlib://`，223
- 压缩
  - Bzip2 压缩包，224-226
  - ZIP 压缩包，223-224
- 压缩流，222-224
- `configureWSDL()` 方法，307
- 连接
  - Firebird，270-271
  - MSSQL，262
  - MySQL，231-232
  - MySQLi，232
  - Oracle，257
  - PostgreSQL，253
  - SQLite，244-245
- FTP 服务器连接，298-300
- 转换
  - 数组转换为变量，47-48
  - 数组转换为字符串，49
  - 数据类型，32-33
  - 字符串
    - 转换为日期，85-86
    - 转换为 HTML，11-13
    - 字符串转换为数组，48-49
- Cookie HTTP 头，165
- Cookie，164-166
  - 创建，167-169
  - 删除，173
  - 设置域，174-175
  - 设置过期时间，166,170-172
  - 限制，164
  - 从 Cookie 预填表单数据，132-134
  - 发送原始 Cookie 数据，169
  - 读取，170
  - 保存
    - 语言偏好，180-181
    - 多个值，177-178
  - 将 HTML 表单数据保存到 Cookie 中，129-131
  - 规范，165
  - 测试浏览器支持，176-177
- `cookietest.php`，176-177
- `copy()` 函数，221
- 复制文件，221
- `count()` 函数，42-43
- 创建
  - 数组，40-41
  - 校验和，16-18
- 跨站脚本（XSS）攻击，移除 HTML 标记，11-13
- `crypt()` 函数，14-15
- CSV 文件，212-215

### D

- 通过 JSON 交换数据，316,319
- 数据加密标准（DES），加密字符串，14-15
- 数据类型，32-33。另请参阅特定数据类型
- 数据库
  - Firebird
    - 连接，270-271
    - 检索数据，273
    - 发送 SQL 语句，272
  - MSSQL
    - 连接，262
    - 检索数据，266
    - 发送 SQL 语句，264-265
  - MSSQL/MSDE，检索数据，269
  - MySQL
    - 连接，231-232
    - 预处理 SQL 语句，235
    - 检索数据，237-239
    - 发送 SQL 语句，233-234
  - Oracle
    - 连接，257
    - 检索数据，261-262
    - 发送 SQL 语句，259-260
  - PEAR 包，278
  - PostgreSQL
    - 连接，253
    - 插入/更新数据，255
    - 检索数据，256-257
    - 发送 SQL 语句，254
  - SQLite
    - 连接，244-245
    - 检索数据，248-250
    - 发送 SQL 语句，247
- `date()` 函数，71-73
  - Epoch 值，81
  - 格式化符号，71-73
  - 本地化日期，79
  - 在 `date()` 中使用文本，74
- `Date_Holidays` 包（PEAR），97
- `date_sunrise()` 函数，86-87
- `date_sunset()` 函数，86-87
- 日期和时间，71。另请参阅 `date()` 函数
  - 基准测试操作，88-89
  - 将字符串转换为日期，85-86
  - 计算两个日期之间的差值，93-94
  - 日出和日落，86-87
  - GMT 格式，96-97
  - HTML 表单选择字段，90-93
  - 确定闰年，82
  - 本地化日期，76-79
  - PEAR 包，97
  - 计算相对日期，83
  - 创建可排序的时间戳，84
  - 格式化特定日期，81
  - 验证日期，82
- `Date` 包（PEAR），97
- `DB_DataObject` 包（PEAR），278
- `deletecookie.php`，173
- 删除 Cookie，173
- DES（数据加密标准），加密字符串，14-15
- 反序列化对象，113,115
- 目录遍历攻击，210-211
- `dirname()` 函数，209-210
- DOM（文档对象模型），284
  - 读取 XML，284-285
  - 写入 XML，285-286
- PDO（PHP 数据对象）驱动，274-275

### E

- `each()` 函数，42-43
- 通过电子邮件发送 HTML 表单数据，153
- 电子邮件地址
  - 使用 ASCII 代码保护，20
  - 验证，34-35
- 加密字符串，14-15
- Epoch 值
  - 计算日期差值，93-94
  - 将字符串转换为 Epoch 值，85-86
  - `date()` 格式化符号，73
  - 格式化特定日期，81
- 欧洲日期格式，80
- 与 JSON 交换数据，316,319
- `explode()` 函数，49
- 表达式
  - 打印，22-24
  - 正则。参见正则表达式
- `ext/mysql` 扩展，231
- 可扩展标记语言。参见 XML
- 提取子字符串，19

### F-G

- `fclose()` 函数，204
- `fgetcsv()` 函数，212-214
- `fgets()` 函数，206
- `File_Find` 包（PEAR），228
- `file()` 函数，206
- `file_exists()` 函数，204
- `file_get_contents()` 函数，205,298
- `file_put_contents()` 函数，207,298
- `File_SearchReplace` 包（PEAR），228
- `File` 包（PEAR），228
- `filectime()` 函数，219
- `filegroup()` 函数，219
- `filemtime()` 函数，219
- `fileowner()` 函数，219
- 文件
  - 访问
    - PHP 内置类，221-222
    - 相对路径，209-210
    - 安全陷阱，210-211
  - 关闭，204
  - 复制，221
  - CSV 文件，212-215
  - 解析 INI 文件，216-217
  - 锁定，208-209
  - 打开，202-203
  - PEAR 包，228
  - 读取数据，205-206
  - 重命名，221
  - 获取文件信息，218-219
  - 通过 HTTP 请求返回，227-228
  - 删除（`unlink`），221
  - 上传
    - 移动上传的文件，157-158
    - 获取已上传文件信息，154-155
  - 写入数据，207
- `filesize()` 函数，219
- 过滤数组，65-66
- Firebird
  - 连接，270-271
  - 检索数据，273
  - 发送 SQL 语句，272
- `flock()` 函数，208-209
- `fopen()` 函数，202-203
- for 循环，数值数组，42
- foreach 循环
  - 关联数组，43
  - 数值数组，41
- `strftime()` 函数的格式化符号，76-77
- `fputcsv()` 函数，214-215
- `fsockopen()` 函数，297
- `ftp-file.php`，298
- `ftp-functions.php`，300
- `ftp_get()` 函数，300

### H

- HTML 表单
  - 检查提交，128
  - 验证必填字段，31-32
- `htmlentities()` 函数，11-12
- `htmlspecialchars()` 函数，11-12,62,131,134-135
- `HTML_QuickForm2` 包（PEAR），161
- 查看 HTTP 头，165
- 通过 HTTP 请求返回文件，227-228
- `http-file.php`，295
- `HTTP_Session` 包（PEAR），199
- `http-socket.php`，297
- `HTTP_Upload` 包（PEAR），161

### I

- `ibase` 扩展，270
- `ibase_connect()` 函数，270-271
- `ibase_connect.php`，270
- `ibase_execute()` 函数，272
- `ibase_fetch.php`，273
- `ibase_fetch_assoc()` 函数，273
- `ibase_fetch_object()` 函数，273
- `ibase_prepare()` 函数，272
- `ibase_query()` 函数，272
- 实现单例，116-119
- `implode()` 函数，49,206
- 继承，102-103,108
- 解析 INI 文件，216-217
- InterBase。参见 Firebird
- 接口，104-107
- IP 地址排序，57
- `is_array()` 函数，32
- `is_bool()` 函数，32
- `is_dir()` 函数，219
- `is_executable()` 函数，219
- `is_file()` 函数，219
- `is_float()` 函数，32
- `is_int()` 函数，32
- `is_link()` 函数，219
- `is_null()` 函数，32
- `is_numeric()` 函数，32-33
- `is_object()` 函数，32
- `is_readable()` 函数，219
- `is_string()` 函数，32
- `is_uploaded_file()` 函数，219
- `is_writable()` 函数，219

### J-K-L

- JavaScript 对象表示法：参见 JSON
- JSON，数据交换，316,319
- `krsort()` 函数，52
- `ksort()` 函数，52,55
- 确定闰年，82
- 换行符，14
- `list()` 函数，48
- 本地化日期，76-79
- 锁定文件，208-209
- 遍历
  - 关联数组，43
  - 嵌套数组，44-47
  - 数值数组，41-43

### M

- MD5（消息摘要算法 5），17-18
- `md5()` 函数，16-18
- `mktime()` 函数，81-82
- `mod_files.sh` 脚本，183
- 移动上传的文件，157-158
- MSDE
  - 检索数据，269
  - 发送 SQL 语句，264-265
- MSSQL（Microsoft SQL Server）
  - 连接，262
  - 检索数据，266,269
  - 发送 SQL 语句，264-265
- `mssql_connect()` 函数，269
- `mssql_fetch_assoc()` 函数，269
- `mssql_fetch_object()` 函数，269
- `mssql_fetch_row()` 函数，269

...

### S

- `substr()` 函数，19
- 子字符串
  - 提取，19
  - 搜索，26
- 日出和日落时间，确定，86-87
- 超全局数组，访问表单数据，126
- 符号，`date()` 函数，71-73

### T

- 标签（HTML）
  - 使用正则表达式查找，31
  - 移除，12-13
- 文本
  - 字段，预填充，131, 134-135
  - `date()` 函数中的文本，74
- 时间。参见日期和时间
- 时间和日期，日期格式，80
- 时间戳
  - 基准测试，88-89
  - 计算相对日期，83
  - 将字符串转换为时间戳，85-86
  - GMT 格式，97
  - 创建可排序时间戳，83-84
- Traits（特征），120-122
- 转换 XML，290
- `trim()` 函数，32

### U

- 英国日期格式，80
- 美国日期格式，80
- `unlink()` 函数，221
- 删除文件，221
- `unserialize()` 函数，132
- 上传文件
  - 移动上传的文件，157-158
  - 获取上传文件的信息，154-155
- `urlencode()` 函数，12
- URL，准备在其中使用的字符串，12
- 用户名，验证，9-10
- `usort()` 函数，58

### V

- 验证
  - 数据类型，32-33
  - 日期，82
  - 电子邮件地址，34-35
  - HTML 表单
    - 必填字段，31-32, 145-146
    - 选择列表，147-149
  - 密码，9-10
  - 用户名，9-10
  - XML，291-292
- 变量
  - 检查数据类型，32-33
  - 将数组转换为变量，47-48
  - 获取变量信息，25-26
  - 打印，22-24
  - `var_dump()` 函数，25
  - `var_export()` 函数，26
  - `vprintf()` 函数，24
  - `vsprintf()` 函数，24

### W

- Web 表单。参见 HTML 表单
- Web 服务器
  - FTP 服务器连接，298-300
  - HTTP 服务器连接，295-298
  - 检查状态，301
- Web 服务，302-304
  - 使用
    - 使用 NuSOAP，309
    - 使用 PHP5-SOAP，312-313
  - 创建
    - 使用 NuSOAP，304-305
    - 使用 PHP5-SOAP，310
  - WSDL，303
    - 使用 NuSOAP 生成，306-308
    - 使用 PHP5-SOAP 生成，310-311
- while 循环
  - 关联数组，43
  - 数值数组，42
- 写入
  - 将 HTML 表单数据写入文件，151-152, 158
  - 会话，186
  - XML，285-286
- 将数据写入文件，207
- WSDL（Web 服务描述语言），303
  - 使用 NuSOAP 生成，306-308
  - 使用 PHP5-SOAP 生成，310-311
  - `wsdl-nusoap-client.php`，308
  - `wsdl-nusoap-server.php`，306
  - `wsdl-php5-client.php`，312
  - `wsdl-php5-server.php`，312

### X-Y

- XML，279-280
  - 使用 SAX 解析，280-282
  - PEAR 包，293
  - 在 PHP 4 中读取，284-285
  - `SimpleXML` 扩展，289
  - 验证，291-292
  - 写入，285-286
- XSLT（XSL 转换），290
- XML-RPC，302
- `XML_Beautifier` 包（PEAR），293
- `XML_DTD` 包（PEAR），293
- `XML_Parser2` 包（PEAR），293
- `xml_parser_create()` 函数，281
- `xml_parser_set_option()` 函数，281
- `XML_Serialize` 包（PEAR），293
- `xml_set_character_data_handler()` 函数，281
- `xml_set_element_handler()` 函数，281
- `XML_Util` 包（PEAR），293
- XSLT（XSL 转换），290
- XSS（跨站脚本）攻击
  - HTML 标记，移除，11-13

### Z

- ZIP 文件
  - PHP 内建函数，223-224
  - `compress.zlib://`，223
- `zip_entry_open()` 函数，223
- `zip_entry_read()` 函数，223
- `zip_open()` 函数，223
- `zip_read()` 函数，223
- ZZIPLib 库，223

![](img/2862989e5dc7f1b1d0bc64321737f084_360_0.png)

![](img/2862989e5dc7f1b1d0bc64321737f084_360_1.png)

## 充实你的大脑

获得来自 O'Reilly Media、Addison-Wesley、Microsoft Press、Cisco Press、McGraw Hill、Wiley、WROX、Prentice Hall、Que、Sams、Apress、Adobe Press 等顶级出版商的数千本关于技术、数字媒体和专业发展的书籍和视频的无限制访问权限。

### 眼见为实

观看数百个由专家主讲的、关于当下最热门主题的教学视频。

### 等等，还有更多！

### 获得竞争优势

通过 Rough Cuts 预出版手稿和 Short Cuts 中的新技术概览，抢先了解最新技术和主题。

### 加速你的项目

复制并粘贴代码，创建智能搜索，让你在有关你喜爱主题的新书可用时第一时间知晓，并用收藏夹、高亮、标签、笔记、混搭等自定义你的资料库。

\*仅限新订户。折扣适用于 Safari 图书馆，并在前 12 个连续月度计费周期内有效。Safari 图书馆并非在所有国家/地区都可用。

![](img/2862989e5dc7f1b1d0bc64321737f084_361_0.png)

![](img/2862989e5dc7f1b1d0bc64321737f084_361_1.png)

### 免费在线版

购买《PHP and MySQL Phrasebook》后，即可通过 Safari Books Online 订阅服务在 45 天内访问免费在线版。几乎每本 Addison-Wesley Professional 图书都可以通过 Safari Books Online 在线获取，此外还有来自 Cisco Press、Exam Cram、IBM Press、O'Reilly Media、Prentice Hall、Que、Sams、VMware Press 等出版商的数千本图书和视频。

Safari Books Online 是一个数字图书馆，可提供可搜索的、按需访问的来自领先出版商的数千本技术、数字媒体和专业发展书籍和视频。只需支付每月或每年的订阅费用，即可无限制地访问学习工具以及有关移动应用和软件开发、使用你喜爱的设备的小技巧、网络、项目管理、平面设计等主题的信息。

### 在 `informit.com/safarifree` 激活你的免费在线版

- 步骤 1：输入优惠券代码：LHVKNVH。
- 步骤 2：Safari 新用户，请填写简短的注册表。Safari 订户，直接登录即可。

如果在 Safari 上注册或访问在线版时遇到困难，请发送电子邮件至 customer-service@safaribooksonline.com

![](img/2862989e5dc7f1b1d0bc64321737f084_362_0.png)

- PHP 和 MySQL Web 开发 — Luke Welling and Laura Thomson — 978-0-672-32916-6
- …an D. Eisenhamer
- **高级 PHP 编程** — George Schlossnagle
  - ISBN-13: 978-0-672-32561-8
- **SQLite** — Chris Newman
  - ISBN-13: 978-0-672-32685-1

Developer’s Library 图书在大多数实体书店和在线书店均有销售。如需了解更多信息或直接订购，请访问我们的在线书店 `informit.com/store`。

所有 Developer’s Library 图书的在线版本均可通过 Safari Books Online 订阅获取，网址为 `safari.informit.com`。

![](img/2862989e5dc7f1b1d0bc64321737f084_362_1.png)

![](img/2862989e5dc7f1b1d0bc64321737f084_363_0.png)

### 基本代码和命令

### PHP and MySQL™ PHRASEBOOK

PHP and MySQL Phrasebook 为你提供了所需代码，让你能够使用 PHP（创建动态网页的领先脚本语言）快速高效地完成 Web 编程项目。

### 简洁易用

携带方便、易于使用——让你抛弃所有笨重的书籍，换成一册便携的袖珍指南。

### 灵活实用

内含 100 多个可自定义代码片段——让你几乎在任何情况下都能轻松编写可用的 PHP 和 MySQL 代码。

Christian Wenz 是一位专注于 Web 技术的作者和顾问。他合著了 Zend PHP 5 和 Zend PHP 5.3 认证教材，并为 PEAR 仓库中的多个 PHP 包做出了贡献。

请在 `informit.com/register` 注册你的图书，以便在有更新和更正时方便地下载。

编程 / PHP / MySQL

封面图片 © zwiebackess

购买本书即可免费访问在线版 45 天，详情见末页。

Addison-Wesley Developer’s Library `informit.com/devlibrary`

![](img/2862989e5dc7f1b1d0bc64321737f084_363_1.png)

![](img/2862989e5dc7f1b1d0bc64321737f084_363_2.png)

