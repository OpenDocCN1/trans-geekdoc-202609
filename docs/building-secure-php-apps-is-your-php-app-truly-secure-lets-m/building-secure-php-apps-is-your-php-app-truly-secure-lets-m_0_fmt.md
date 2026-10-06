
# 构建安全 PHP 应用构建指南：你的 PHP 应用真的安全吗？让我们确保万无一失

## 构造函数

几年前，我正在为一个客户使用 `CodeIgniter` 框架编写一个应用程序，令人遗憾的是，`CodeIgniter` 并没有包含任何身份验证功能。因此，我开始寻找能够满足我需求的简洁库。为了在 `CodeIgniter` 中提供身份验证，当然，我做了任何优秀的开发人员都会做的事。这开启了我创建 `Ion Auth` 的旅程，这是一个功能简单的身份验证库。多年以后，我们许多人转向了其他框架或语言，但我仍然经常看到安全被忽视。所以让我们确保我们都能准时回家，并在晚上睡个好觉。

本书是一本快速读物，并附带了可以操作的手册风格引用。我也会尽量确保在这个过程中有一些乐趣。

### 格式

所有缩进块中的代码均假设为 PHP，除非另有说明。

以 `$` 开头的行：

```
$ ls -al
```

是普通用户使用命令行的示例。

以 `#` 开头的行：

```
# ls -al
```

是 root 用户使用命令行的示例。

服务器命令行示例将假设某种操作系统（`centos`、`redhat`、`ubuntu`、`osx` 等）。

我正尽量避免代码示例换行，因此方法参数将单独占一行。这看起来可能很奇怪，但比换行的代码易读得多。

### 错误列表

如果你发现任何错误，请随时通过电子邮件与我联系。

### 示例代码

除非另有说明，所有的示例都是 PHP。尽可能使用原生 PHP 代码，即使会产生更多的模板代码。如果某些内容用原生 PHP 很难简洁解释，我会使用 `Laravel` 框架，因为它的语法优雅且易于理解。

某些代码示例为了解释而被拆分。要查看完整的代码示例，可以参考 Github 仓库（`https://github.com/benedmunds/Building-Secure-PHP-Apps-Examples`）。

让我们开始吧。

## 关于作者

Ben Edmunds 领导开发团队创建尖端的 Web 和移动应用程序。他是各种开发社区中活跃的领导者、开发者和演讲者。他从事软件开发已超过 10 年，在此期间，他处理过从机器人到政府项目的各种任务。

PHP Town Hall 播客共同主持人。波特兰 PHP 用户小组联合组织者。开源倡导者。

让我们从一个故事开始。迈克是俄克荷马州一所私立学校的系统管理员。他的主要职责是维护网络和计算机运行。最近，他开始通过构建一个内部使用的 Web 应用程序来使学校各项任务自动化。他没有接受过任何正式培训，在大约年前才开始编程，但他对自己的工作非常满意。他了解 `PHP` 的基础知识，并为学校构建了一个相当稳定的客户关系管理系统。虽然还有很多功能需要添加，但基础部分已经涵盖了。迈克甚至因为简化运营和为学校节省费用而收到了校长的表扬。

迈克的一切进展都很顺利，直到一个特殊的新学生出现。这个学生的名字叫“小波比表格”^(2)。一天，行政办公室的乔打给迈克电话，询问系统为什么宕机了。经过检查，迈克发现包含所有学生信息的表格完全丢失了。你知道，小波比的全名实际上是“Robert’); DROP TABLE students;–”。数据库没有任何备份；这已经在迈克的“待办事项”上列了一段时间了，但他还没来得及处理。迈克有大麻烦了。

## SQL 注入

### 现实世界

虽然真实儿童的名字不太包含破坏性的 SQL 代码，但这种 `SQL 注入漏洞` 在现实世界中不断发生：^(3)

*   2012 年，LinkedIn 因为一个未公开的 SQL 注入漏洞泄露了超过 600 万用户的数据。
*   2012 年，Yahoo! 暴露了 45 万用户的密码。
*   2012 年，Nvidia 的 40 万个密码被攻破破解。
*   2012 年，Adobe 的 15 万个密码被攻破破解。
*   2013 年，eHarmony 大约有 150 万用户密码被暴露。

### SQL 注入是如何工作的

如果你直接使用用户输入的输入而不进行任何修改，恶意用户就可以传递意料之外的数据，并从根本上改变你的 SQL 查询语句。

如果你的代码看起来像这样：^(4)

```php
mysql_query('UPDATE users
  SET first_name="' . $_POST['first_name'] . '"
  WHERE id=1001');
```

你预期生成的 SQL 应该是：

```sql
UPDATE users set first_name="Liz" WHERE id=1001;
```

但如果你的恶意用户输入的第一个名字是：

```
Liz", last_name="Lemon"; --
```

那么生成的 SQL 就会变成：

```sql
UPDATE users
SET first_name="Liz", last_name="Lemon"; --"
WHERE id=1001;
```

现在你所有的用户名字都变成了 Liz Lemon，这可真不妙了。

### 如何防御

防止 SQL 注入的唯一要求是`对输入进行过滤`（sanitize input，也称为转义，escaping）。你可以对每个输入进行单独转义，或者使用一种被称为`参数绑定`（parameter binding）的更好方法。参数绑定绝对是我推荐的方法，因为它提供了更高的安全性。使用 `PHP` 的 `PDO` 类^(5)，你的代码现在变成了：

```php
$db = new PDO(...);
$query = $db->prepare('UPDATE users
  SET first_name = :first_name
  WHERE id = :id');

$query->execute([
  ':id'         => 1001,
  ':first_name' => $_POST['first_name']
]);
```

使用绑定参数意味着每个值都会被转义、正确引用，并且只预期一个值。记住，绑定参数可以保护你的查询，但它们不能保护输入数据进入系统后的状态。请记住，绑定参数保护你的查询，但*任何* 数据都可能是恶意的。你需要在保存数据到数据库之前过滤掉它们，或者在输出它们时处理，我们将在后面的清理输出章节中详细介绍。你的代码现在变得长了一些，但它是安全的。你不需要担心这些。

#### 最佳实践与其他解决方案

防止 SQL 注入的唯一要求是`对输入进行过滤`（sanitize input，也称为转义，escaping）。你可以对每个输入进行单独转义，或者使用一种被称为`参数绑定`（parameter binding）的更好方法。参数绑定绝对是我推荐的方法，因为它提供了更高的安全性。使用 `PHP` 的 `PDO` 类^(5)，你的代码现在变成了：

```php
$db = new PDO(...);
$query = $db->prepare('UPDATE users
  SET first_name = :first_name
  WHERE id = :id');

$query->execute([
  ':id'         => 1001,
  ':first_name' => $_POST['first_name']
]);
```

使用绑定参数意味着每个值都会被转义、正确引用，并且只预期一个值。记住，绑定参数可以保护你的查询，但它们不能保护输入数据进入系统后的状态。请记住，任何* 数据都可能是恶意的。你需要在保存数据到数据库之前过滤掉它们，或者在输出它们时处理，我们将在后面的清理输出章节中详细介绍。你的代码现在变得长了一些，但它是安全的。你不需要担心这些。

### 批量赋值 (Mass Assignment)

这听起来像是一个愚蠢的问题，但很多开发者和网站都曾陷落其中。最近已知的此类漏洞利用案例是某用户暴露了 Ruby on Rails 容易受到。当 Egor Homakov 最初向 Rails 团队报告新安装的 Rails 不安全时，他的漏洞报告被拒绝了。核心团队认为这是一个微小的顾虑，为了方便新开发者，默认开启它。为了引起对此问题的关注，Homakov 幽默地“黑进”了 Rails 的 GitHub 账户（GitHub 是基于 Rails 构建的），获取了他们仓库的管理员权限。不言而喻，这证明了他的观点，现在 Rails（以及 GitHub）默认受到这种攻击的保护。

你如何保护你的应用程序免受这种攻击？具体的实现细节取决于你使用的哪个框架或代码库，但你有几种选择：

*   完全关闭批量赋值
*   对可以进行批量赋值的字段设置白名单
*   对不安全的批量赋值的字段设置黑名单

根据你的实现方式，某些方法可能被同时使用。

在 Laravel 中，你为模型添加 `$fillable` 属性来设置可以批量赋值的字段白名单：

```php
class User extends Eloquent {
  protected $table = 'users';
  protected $fillable = ['first_name', 'last_name', 'email'];
}
```

或者使用 `$guarded` 设置黑名单：

```php
class User extends Eloquent {
  protected $table = 'users';
  protected $guarded = ['permissions'];
}
```

选择取决于你，取决于在你的应用程序中哪种更方便。

如果你没有使用 Laravel，你的框架可能有类似的方法来对批量赋值字段进行白名单/黑名单处理。如果你使用的是自定义框架，快开始实现白名单和黑名单机制吧！

### 类型转换 (Typecasting)

我喜欢采取的另一个额外步骤，不仅是为了安全，还为了数据完整性，就是对已知的格式进行类型转换。由于 `PHP` 是一门动态类型语言，值可以是任何类型：字符串、整数、浮点数等。通过对该值进行类型转换，我们可以验证数据是否符合我们的预期。在之前的示例中，如果 `ID` 来自一个变量，那么如果我们知道它应该始终是一个整数，那么对其进行类型转换是有意义的，如下：

```php
$id = (int) 1001;

$db    = new PDO(...);
$query = $db->prepare('UPDATE users
  SET first_name = :first_name
  WHERE id = :id');

$query->execute([
  ':id'         => $id, //我们知道它是 int
  ':first_name' => $_POST['first_name']
]);
```

在这种情况下，这并不重要，因为我们是自己定义 `ID` 的，所以我们知道它是整数。但如果 `ID` 来自提交的表单或其他来源，这将带给我们额外的安全感。

`PHP` 支持许多你可以转换的类型，它们是：

```php
$var = (array) $var;
$var = (binary) $var;
$var = (bool) $var;
$var = (boolean) $var;
$var = (double) $var;
$var = (float) $var;
$var = (int) $var;
$var = (integer) $var;
$var = (object) $var;
$var = (real) $var;
$var = (string) $var;
```

这不仅在处理数据库时有用，在整个应用程序中都是如此。仅仅因为 `PHP` 是动态类型的，并不意味着你可以在某些地方强制执行类型。没错，科学就是！

### 输出过滤 (Sanitizing Output)

#### 输出到浏览器

不仅在保存输入的数据时你应该采取措施，你还应该对输出回浏览器的任何用户生成的数据进行过滤/转义。

你可以在保存到数据库之前修改并转义你的数据，也可以在检索数据和输出到浏览器之间进行处理。这通常取决于你的数据如何被编辑和使用。例如，如果用户以后要编辑数据，那么通常原样保存它更有意义，并在输出时进行过滤。

转义你输出的用户生成数据可以带来哪些安全益处？假设用户向你的应用程序提交了以下 JavaScript 代码段，你的应用程序将其保存以备后输出：

```html
<script>alert('I am not sanitized!');</script>
```

如果你在将它 `echo` 到浏览器之前不对这段代码进行过滤，恶意的 JavaScript 将正常运行，就像是你自己写的一样。在这种情况下，只是一个无害的 `alert()`，但黑客不会那么仁慈。

此类攻击的另一个常见地方是在图片的 XIFF 数据中。如果用户上传了图片，而你的应用程序显示了 XIFF 数据，那么它也需要被过滤。在任何你显示从外部进入你的应用程序数据的地方，你都需要对它进行过滤。

如果你在使用模板库或处理模板的框架，转义可能会自动发生，或者有内置方法来这样做。请确保检查你所选择的库/框架的文档，以确定它是如何工作的。

对于那些自己处理这些工作的人，`PHP` 提供了几个函数，在输出数据时对你很有用：`htmlentities()` 和 `htmlspecialchars()`。它们会将数据转换为 HTML 实体，以防止恶意脚本执行。这在处理数据库时有用，在整个应用程序中都是如此。

#### 输出到命令行

在输出到命令行时你也应该考虑安全，这些函数是 `escapeshellcmd()` 和 `escapeshellarg()`。

## 第二章 - HTTPS/SSL/BCA/SHA/Some of Them Actually Matter

再次提到，这发生在 2010 年，让我们通过一个小故事来说明这一点。

它是 2010 年 12 月，Jane 为 Ach Inc 公司出差，住在希 Garden 酒店，恰好也是 John 住的同一家酒店。Jane 最近听说了关于 Firesheep 的新闻，心情很奇怪。她连接了酒店的 Wi-Fi 并运行了 Firesheep。幸运的是 Jane，John 正在使用 Wi-Fi，她看到他连接到了未安全的公司门户网站。只需点击一下，她就登录了 John 的邮箱账户。只需想一下她可能给他带来的麻烦，她可以访问的隐私信息，邮箱对他生活可能造成的通用控制/混乱。

这种攻击通过未加密的网络流量进行会话劫持（即 sidejacking），一直以来对于如何操作的人是可能的。现在随着 Firesheep 的发布，任何知道如何下载扩展并点击按钮的人都可以做到。

听起来很可怕吗？确实应该，因为它是。也许你正在想，这真的是件糟糕的事情。事实恰恰相反，这促使网络公司终于从过去的成就中恢复过来，认真对待 HTTPS。Gmail、Facebook 和 Twitter 现在都默认在整个站点使用 HTTPS。以前的标准只是加密登录页面，这保护了用户的登录凭据，但让他们的当前会话处于被劫持的风险之中，正如上面的。

### 什么是 HTTPS

普通的网页流量通过 HTTP 传输，当你在浏览器中输入 `http://www.google.com` 时，你使用的是 HTTP，注意开头的 `http://`。普通的 HTTP 流量使用端口 `80`，HTTPS 反之使用端口 `443`。HTTP 一点也不安全，你所做的一切都是明文发送的，任何监听者都能看到你的。HTTPS 是“安全的 HTTP”或“在 SSL 上的 HTTP”，缩写语义可以争论，但它们的意思相同。

我将仅在非常高水平上涵盖 HTTPS 如何工作，因为细节对大多数人来说并不重要。如果你感兴趣了解更多，请这样做，google.com 是一个很好的开始 ;)

解释 SSL 如何工作的一个真实生活例子是外交邮袋^(11)。其内容是安全的，只有在传输两端拥有适当凭据的人才能打开它。该邮袋受到国际法和物理手段的保护，正如 SSL 加密消息体受到强算法和密钥的保护一样。

证书颁发机构（CA）会对你的网站证书进行签名以证明其有效性。用户的网络浏览器已经认识主要的证书颁发机构，并将根据证书颁发机构提供的根证书验证网站证书。随后，流量将在两端使用此密钥进行加密，因此跨网络传输的流量只有加密流量。如果你曾经用过带有公钥身份验证的 `SSH`，你已经对这个过程熟悉了。你有一个公钥和一个密钥，用于向远程服务器验证你的身份。

如果你的整个网站都使用 `HTTPS` 加密，这将保护你免受中间人攻击，包括我们提到的会话劫持。

## 局限性

使用 `HTTPS` 有一些局限性，可能会使其在某些情况下变得不可行。

### 虚拟主机

在正常配置下，虚拟主机无法与 `SSL` 一起使用。如果你在使用共享主机或仅仅在同一台服务器上运行多个网站，就会出现问题。原因在于服务器在连接完成之前无法确定主机头（host header），而这需要 `SSL` 认证。由于证书只能有一个主机，这意味着它将无法工作。解决此问题的简单方法是设置多个 IP 地址，并使用基于 IP 的主机，而不是你可能习惯的基于名称的主机解析。不过，我通常建议为安全站点设置单独的服务器，如果你需要 `HTTPS`，你可能也到了需要专用服务器的程度了。

然而，有些托管提供商提供共享证书，可以在其托管的网站之间使用。这可以让你快速且廉价地支持 `HTTPS`。主要的限制是域名需要反映托管提供商的域名。例如，与其使用

```
https://yourApp.com/login
```

URL 将类似于

```
https://yourHost.com/yourApp/login
```

这取决于你的应用程序和品牌需求，可能是一个担心的问题，也可能不是。

### 速度

`HTTPS` 连接需要 `SSL` 握手来建立连接，从而使得整体传输变慢。一旦完成了初始握手，后续连接只需要对内容进行加密解密，这意味着一旦初始连接完成，后续连接就不会慢多少。尽管如此，对性能的影响是*极低*的，这并不是否定使用 `HTTPS` 的有效理由。

### 缓存

Cheddar。一叠钱。死总统。现金。不，实际上我们谈论的是缓存。这是你超快速加载时间背后的秘诀。你必须用英国口音说出来。现代浏览器缓存 `HTTPS` 内容的方式与 `HTTP` 内容相同，所以这方面没有区别。要让旧浏览器支持缓存，请设置 `Cache-Control` 头部，例如

```php
header('Cache-Control: max-age=31536000');
```



这将告诉浏览器缓存一年。

真正的问题在于代理缓存。代理缓存可能来自 `ISP` 或旨在加速连接的服务。这主要用于世界上互联网连接速度较慢的农村地区。使用 `HTTPS`，例如，坐下来规划你网站的哪些部分应该被加密。

### 证书类型

`SSL` 有两种类型。

`域名验证证书 (Domain Validated Certificates)` 验证的信息并不多，因为它们便宜得多。通常起价 50 美元，它们可能是小型网站的最佳选择。从用户角度来看，主要的缺点是它们可能只显示锁图标，而 `扩展验证证书 (Extended Validation Certificate)` 将显示完整的地址栏。

`扩展验证证书 (Extended Validation Certificates)` 是 `SSL` 的金标准。它们不仅验证你是域名所有者，还验证域名所有者的身份和合法性。由于通常需要证书颁发机构的介入，这些证书贵得多。通常 500 美元起。

## 何时使用 HTTPS

传统的观点是在任何凭据或其他敏感数据传输到服务器的地方使用 `HTTPS`。多年来，这意味着登录页面和购物车是加密的。这些仍然是加密有效且必要的地方，但会让用户的其他会话暴露在中间人攻击中。最近出现了一种处处使用 `HTTPS` 的趋势。这只是对于你的网站所有页面都经过加密的一种营销说法。

无论你的限制如何，你对用户都有义务实施尽可能最好的安全性。例如，如果你运行购物车或收集信用卡，`HTTP` 甚至不是一个选项。越来越多，即使对于不被认为是敏感的数据（如社交媒体账户），加密也正成为标准。

## 实现 HTTPS

### 我需要哪种 SSL 证书？

你需要问自己的主要问题是，是否需要保护子域名。如果你需要保护多个子域名，例如

```
api.yourApp.com
docs.yourApp.com
yourMom.yourApp.com
cart.yourApp.com
```

那么你需要一个`通配符 SSL 证书 (Wildcard SSL Certificate)`。如果你不需要这种功能，只需要保护类似

```
yourApp.com
```

那么标准证书就可以工作。获取以后可能需要的通配符证书的唯一障碍是成本。

### 生成你的服务器证书

为了让证书颁发机构签名并生成你的证书，你需要在服务器上生成密钥，并将这些密钥上传到证书颁发机构。

这需要 `OpenSSL`，如果你的服务器上没有它，你就需要安装它。在各种服务器操作系统和发行版上安装应用程序不在本书的涵盖范围内，希望当你达到需要设置 HTTPS 的阶段时，你已经对自己的服务器了如指掌。如果你不熟悉自己的服务器操作系统或发行版，请人帮助你设置 SSL 证书可能是个好主意。

首先创建一个目录来存储你的密钥，对于存储这些密钥的最佳位置意见很大，但对于我们的示例，我们将使用

```
/usr/bin/ssl/
```

让我们生成我们的 RSA 私钥：

```
$ openssl genrsa -out yourApp.key 1024
```

然后使用 RSA 密钥生成 CSR

```
$ openssl req -new -key yourApp.key -out yourApp.csr
```

现在你会被问到几个带有默认值的问题，主要需要注意的是“Common Name”（通用名称），它应该与你的域名匹配，例如“yourApp.com”。

现在你有了两个新文件

```
/usr/bin/ssl/yourApp.key
/usr/bin/ssl/yourApp.csr
```

在你做任何事情之前，请在某处为 `.key` 文件制作备份副本。认真的，做两个备份。如果你丢失了私钥，你就需要购买新证书，而服务器是会崩溃的。

### 获取 SSL 证书

在 HTTPS 上运行的第一步是获取证书。某些证书颁发机构提供廉价/免费的证书，但它们不会预装在流行的网络浏览器中，因此对于面向外部的网站是没用的。如果你运行的是内部应用程序，廉价的替代方案和自签名证书是可行选择，对于其他所有人，我们需要购买证书。

首先，我建议检查你的 DNS 服务商，看看他们是否提供任何类型的折扣或易于设置的证书，例如，我使用的 DNS 商是 DNSimple，他们提供大折扣的证书订阅支付。

如果你的 DNS 服务商不提供证书，Symantec/VeriSign 是一个备受尊敬的证书颁发机构。

现在去买一个吧。

然后你需要按照你所选证书颁发机构的任何流程进行操作，通常你只需要上传服务器证书（`yourApp.csr`），他们就会通过电子邮件向你发送签名证书。

你的证书颁发机构将为你提供签名证书，我们将其命名为 `yourAppSigned.crt`。将其复制到你的服务器，对于此示例，我将使用以下路径

```
/usr/bin/ssl/yourAppSigned.crt
```

### Apache 配置

如果你使用 Apache，请遵循这些步骤；如果你正在使用不同的 Web 服务器，请跳过此节并继续阅读。用你喜欢的文本编辑器打开 `httpd.conf` 文件。注意，某些发行版可能对 https 使用单独的配置文件。例如，我运行 OSX 的笔记本电脑使用 `httpd-ssl.conf` 文件。

添加一个类似下面的 VirtualHost（虚拟主机），它可能与你现有的 HTTP 站点的 VirtualHost 非常匹配

```
1 <VirtualHost *:443>
2   DocumentRoot "/path/to/your/app/htdocs"
3   ServerName yourApp.com
4   SSLEngine on
5   SSLCertificateFile /usr/bin/ssl/yourAppSigned.crt
6   SSLCertificateKeyFile /usr/bin/ssl/yourApp.key
7 </VirtualHost>
```

重启 Apache

```
$ apache restart
```

或者

```
$ service apache restart
```

### Nginx 配置

如果你使用 Nginx，请遵循这些步骤；如果你正在使用不同的 Web 服务器，请跳过此节并继续阅读。用你喜欢的文本编辑器打开 `nginx.conf` 文件。注意，某些发行版可能对 https 使用单独的配置文件。例如，我运行 OSX 的笔记本电脑使用 `nginx-ssl.conf` 文件。

添加一个类似下面的 server 块，它可能与你现有的 HTTP 站点的虚拟主机非常匹配

```
server {
    listen 443 ssl;
    server_name yourApp.com;
    root /path/to/your/app/htdocs;
    ssl_certificate /usr/bin/ssl/yourAppSigned.crt;
    ssl_certificate_key /usr/bin/ssl/yourApp.key;
}
```

重启 Nginx

```
$ nginx -s restart
```

或者

```
$ service nginx restart
```

这个故事的教训是：不要存储密码。存储用户密码的单向哈希值。现在，让我们来看看如何正确地这样做。

## 细节说明

我并不是加密学专家。这些是基于我个人经验给出的建议。这些是带有个人色彩的最佳实践，并不适用于作为安全存储核发射代码的指南。不过，你最重要的推文将会是安全的。

## 什么是哈希（Hash）？

首先，我们需要涵盖基础知识。哈希不是加密，密码应该经过单向哈希处理。这意味着它是无法被解密的，这正是“单向”的含义。永远不需要向用户/管理员/母亲/任何人显示密码。一旦输入密码，它就会变成一个完全不同的东西——一个哈希值，该哈希值只能通过输入原始密码来重建。

## 常见攻击手段

在讨论进一步内容之前，让我们深入了解针对哈希算法的常见攻击手段。

### 查找表（Lookup Tables）

查找表实际上就是一个已知密码的哈希表。它可以像这样简单：

```
password | hash
------------------------
pass1    | bidfb2enkjnf
pass2    | psdfnojn3nod
etc...
```

然后将其与你数据库中的密码进行比较，以确定所使用的密码。如果你使用了随机盐（salts），这种攻击就是无用的；但如果哈希值没有盐，它就比抢劫容易得多。

### 彩虹表（Rainbow Tables）

与查找表相比，彩虹表在技术上更复杂，但非常相似。它基本上是通过数学手段实现查找表的一种内存密集度较低的方法。正如我们提到的，你可以交替使用它们。彩虹表也可以通过使用随机盐来防御，因此与现代哈希算法相比的相关性较小。彩虹表是一种非常复杂的利用手段，确实超出了本书的解释范围。如果你想了解更多，可以阅读[Martin Hellman 发表的原始论文](http://www.stanford.edu/~hellman/publications/36.pdf)，该论文引入了这一概念。[关于彩虹表的维基百科](http://en.wikipedia.org/wiki/Rainbow_table)也是一个更易理解的来源。

### 碰撞攻击（Collision Attacks）

碰撞攻击是大多数哈希算法中发现的主要安全漏洞。碰撞攻击有两种类型。经典的碰撞攻击是两个不同的值生成了相同的哈希。一个简单的例子是：

```
string1 = 'abc123'
string2 = 'bcd234'

hash(string1) === hash(string2)
```

选择前缀碰撞攻击是指使用不同的前缀导致两个独立的值生成相同的哈希。这里有一个例子：

```
prefix1 = 'zxy'
prefix2 = 'abc'

string1 = 'abc123'
string2 = 'bcd234'

hash(prefix1 + string1) === hash(prefix2 + string2)
```

## 一撮盐（Salt）

但这还不够。下一个需要注意的问题是查找表和彩虹表。这两种利用手段基本上都维护了一份流行密码及其对应哈希列表。彩虹表稍微复杂一点，但基本上就是这样。我们如何对抗这种？盐（SALTS）。

盐是附加到密码哈希值上使其变得独特的东西。盐也是添加在玛格丽塔酒边缘使其变得美味的东西。总之，你取一个随机字符串（`salt`）并将其与明文密码结合，得到一个唯一值。这意味着，即使有已知哈希的查找表，攻击者也无法匹配用户的密码哈希，因为使用了随机盐。给定两个相同的密码，生成的哈希值将是唯一的。随机盐是你安全体系中最重要的部分之一。

### 随机并不总是随机

你的盐需要是随机的才能有效。然而，Random 不等于 random。你并不需要真正的随机数，但 `rand()` 也不够。使用 PHP 内置的 `rand()` 或 `mt_rand()` 函数的问题在于，它们使用可以被操纵和确定的数据作为种子，它们没有提供“随机性”。产生真正随机数的主要要素是在源中包含足够的熵（entropy）。熵是指产生生成你随机数的系统所收集的真实随机信息量。大多数非加密用途的随机数生成器（如 `rand()` 和 `mt_rand()`）使用算法产生数字，而没有足够的外部数据源来使它们变得真正唯一。这意味着 `rand()` 生成的数据可以被攻击者操纵和猜测。在观察了足够多的 `rand()` 输出后，攻击者可以可靠地确定未来的输出。事实上，在从 `rand()` 返回少少 624 个值后，就可以计算出所有的未来值。

你已经收到警告了，你**不应该**将 `rand()` 用于你的盐。通过购买这本书，你特此承担合同义务，如果你使用 `rand()` 来制作盐，当我亲自冲过去用第一代 iPad 抽你的脸时，你不准抱怨。那东西结实得像砖头一样。

在大多数系统上，调用服务器的 `/dev/random` 是获得真随机的最佳选择。使用它进行登录的问题是它会在从系统收集熵时发生阻塞。收集熵意味着它将从你的系统收集环境数据；各种硬件数据、键盘输入、鼠标移动、磁盘访问等，以生成一个随机位缓冲区。这意味着返回可能需要很长时间，特别是在不忙的服务器上。实际上，我最近遇到了这个问题，我团队的一位开发者使用 `/dev/random` 生成激活码。一切看起来都很好，通过了测试。但当我们把项目部署到自己的生产服务器后，请求最终花费了超过 60 秒。服务器并不忙，因为它只托管了这一个项目，导致 `/dev/random` 在收集熵时阻塞了很长时间。解决方案是什么？`/dev/urandom`

`/dev/urandom` 不被认为是真随机，但它是密码学安全的。这意味着它可能不是一个真正的随机数，但被认为足够安全用于盐。`/dev/urandom` 会立即返回一个非常好的伪随机数，且不会阻塞。`/dev/urandom` 使用现有的熵池来生成伪随机数，对于大多数身份验证系统来说足够安全。如果你正在编写核发射代码的登录页面，最好是让用户等待 `/dev/random`，但对于那个社交照片分享网站，`/dev/urandom` 足够了。

## 哈希算法

让我们讨论一下流行的哈希算法。

### MD5

### SHA-1

啊，老旧的 `SHA-1`，多年来一直既可靠又安全。这在现实世界中也是很多年了，在互联网领域那可是几十年。在 2005 年（2005 年是安全领域糟糕的一年），来自山东大学的研究人员发表了一篇论文，证明少于`2⁶⁹` 次哈希操作即可可靠地生成 `SHA-1` 碰撞。大约`2⁸⁰` 次哈希操作的碰撞被认为在加密上是安全的。供参考，`2⁸⁰` 大约是 `1.20892x10²⁴`，所以“加密安全”意味着非常安全。从那时起摩尔定律确保了 `SHA-1` 变得更加不安全，在任何需要真正安全的应用程序中应避免使用。

正如我上面解释 `MD5` 时所说，当配合随机盐使用时，`SHA1` 在算法上仍然是安全的。

## SHA-256 / SHA-512

`SHA-2` 标准于 2001 年作为 `SHA1` 的继任者引入。当 `SHA-1` 在 2005 年被证明是不安全的时，它的接受度略有所提高。`SHA256` 和 `SHA512` 基本上是相同的；`SHA-256` 使用 32 位字，`SHA-512` 使用 64 位字。它们的轮数也不同。尽管如此，核心算法实际上是完全相同的。

`SHA-2` 在在使用足够轮数（>64）时，目前被认为在加密上是安全的，没有已知的漏洞。

它没有经历像 `Blowfish`（`BCrypt` 内部使用的加密算法）那样程度的严格审查。`Blowfish` 加密算法自 1991 年以来一直存在并被认为是安全的，但配合弱密钥使用它是一个已知的弱。基于加密算法为 `BCrypt` 增加了一层额外的成本，使其优于标准的哈希算法，换句话说，`BCrypt` 在设计上更慢。慢是一件好事！

尽管我推荐 `BCrypt`，但目前 `SHA-256` 或 `SHA-512` 在作为派生算法（如 `PBKDF2` 或用 PHP 的 `crypt()` 函数实现的算法）的一部分时，是安全哈希的有效且安全的选项。

## BCrypt

`BCrypt` 被许多人视为新手，并不那样广为人知。`BCrypt`于 1999 年发布，所以在这里并不算新。`BCrypt` 是一种基于 `Blowfish` 加密算法的密钥派生函数，它是迭代的，因此它通过生成哈希相关的成本来防范暴力破解。

尽管 `BCrypt` 引起了加密研究人员的极大关注，但目前还没有发布针对 `BCrypt` 的利用方法。它已经存在了很长时间，所以截至本文写作（2014 年），`BCrypt` 被认为在加密上是安全的。

`BCrypt` 对加密的明文密码确实有 72 字符的限制。这通常通过剔除多余字符或简单验证 72 为最大长度来考虑。

在接下来的示例中，我们将密码选择 `BCrypt`。

## SCrypt

`SCrypt` 是该领域的新秀。它于 2012 年发布，是一种内存密集型密钥派生函数。理论上，由于算法固有的高成本，`SCrypt` 比 `BCrypt` 更安全，但由于它非常新，我个人并不推荐目前使用它。

在加密世界中，新是一件坏事，意味着 `SCrypt` 没有像旧算法那样受到同等的攻击和审查。最近报告了几个利用方法，这并不意味着 `SCrypt` 不安全，但确实削弱了它理论上优于 `BCrypt` 的安全优势。

`SCrypt` 的一大优势是它被用于加密货币，目前流行的有 Litecoin 和 Dogecoin。这部分将很短。

## 存储

在存储密码时，无论是使用关系型数据库还是文件系统，我们都会使用 `varchar(255)`。这是为了确保任何情况下都不会遇到 `varchar(72)` 的限制。`BCrypt` 对加密的明文密码确实有 72 字符的限制。这通常通过剔除多余字符或简单验证 72 为最大长度来考虑。

## 验证

在验证时，当配合随机盐使用时，`SHA1` 在算法上仍然是安全的。

在验证时，我们需要对用户输入的密码进行哈希，并与存储的哈希进行对比。在安全的哈希安全的时，我们通常使用 `PBKDF2` 或用 PHP 的 `crypt()` 函数实现的算法。

在验证时，我们需要对用户插入密码进行哈希，并与存储的哈希进行对比。在安全的哈希安全的时，我们通常使用 `PBKDF2` 或用 PHP 的 `crypt()` 函数实现的算法。

```php
// generate the binary random salt
$saltLength = 22;
$binarySalt = mcrypt_create_iv(
  $saltLength,
  MCRYPT_DEV_URANDOM
);

// convert the binary salt into a safe string
$salt = substr(
  strtr(
    base64_encode($binarySalt),
    '+',
    '.'
  ),
  0,
  $saltLength
);
```

我们通过带有 `MCRYPT_DEV_URANDOM` 标志调用 `mcrypt_create_iv()`，以告诉它从 `/dev/urandom` 读取缓冲区。将其封装在 `bin2hex()` 中可以获取一个十六进制字符串，而不是原始的二进制数据。



如果你的系统中没有 `MCrypt`，你可以始终回退到直接从 `/dev/urandom` 读取。除非你是在 Windows 上，如果是的话，趁为太晚之前安装 Linux 吧。去吧，我会等你的。你可以以后再感谢我；我接受支票、现金或信用卡作为谢礼。

```php
// generate the binary random salt
$saltLength = 22;
$binarySalt = file_get_contents(
  '/dev/urandom',
  false,
  null,
  0,
  $saltLength
);

// convert the binary salt into a safe string
$salt = substr(
  strtr(
    base64_encode($binarySalt),
    '+', '.'
  ),
  0,
  $saltLength
);
```

## 现在既然我们有了盐，让我们也对密码进行哈希

```php
// generate the binary random salt
$saltLength = 22;
$binarySalt = mcrypt_create_iv(
  $saltLength,
  MCRYPT_DEV_URANDOM
);

// convert the binary salt into a safe string
$salt = substr(
  strtr(
    base64_encode($binarySalt),
    '+',
    '.'
  ),
  0,
  $saltLength
);

// set the cost of the bcrypt hashing
// 记得在你的服务器上进行实验以找到合适的值
$cost = 10;

// 现在我们将算法代码 ($2y$) 与
// 成本以及我们的盐结合
$bcryptSalt = '$2y$' . $cost . '$' . $salt;

// 哈希它，好好哈希它
$passwordHash = crypt(
  $_POST['password'],
  $bcryptSalt
);

// 验证是否返回了安全的哈希
// 这可能是一个错误代码或不安全的哈希
if (strlen($passwordHash) === 60) {
  // 这一部分仅用于演示
  $db = new ImaginaryDatabase;
  $db->user()->create(array(
    'password' => $passwordHash
  ));
} else {
  // 错误处理
}
```

所以我们对密码进行了哈希并将其保存到数据库中。注意到我们没有保存盐吗？那是因为 `crypt()` 会将选定的算法、哈希后的密码和盐全部存储在返回的哈希中。

好了，现在用户已经注册了，假设他们离开了我们的网站（他们竟敢如此！）并在稍后回来，他们需要一种登录方式。登录非常简单，我们只需要将他们的明文密码与存储在数据库中的哈希值进行对比即可。

```php
// 我们将从一个默认状态开始
// 失败，首先假设失败
$valid = FALSE;

// 从我们虚拟的数据库中获取哈希
$user = $db->user()->where(array(
  'email' => $_POST['email']
))->row();

// 现在检查登录密码是否匹配
$pass = $_POST['password'];
if (crypt($pass, $user->pass) === TRUE) {
  $valid = TRUE;
}

// 其他检查、错误处理等...
if ($valid === TRUE) {
  // 有效的验证逻辑
}
```

如果你将之前生成的哈希值作为第二个参数传递给 `crypt()` 函数，它将使用该算法和盐来生成一个新的哈希，然后你可以用它与存储的密码哈希值进行比较。

## >= PHP 5.5

PHP 5.5 引入了新的密码哈希函数，极大地简化了处理密码的过程。此目的是隐藏许多复杂性，并让用户可以使用 PHP 内置的默认函数来确保安全，而不需要依赖所有开发者都清楚自己在做什么。换句话说，他们正试图偷我的内容，混蛋们。

不过说认真的，尽可能使用 PHP 函数。它们提供了内置的、最新的哈希处理，并带有额外的安全检查，这些是我们在这里甚至没有提到的，例如针对计时攻击的防护。

我们将在这里使用 PHP 5.5 语法通过完全相同的步骤。我们将使用 `password_hash` 函数来生成哈希后的密码，该函数会自动创建一个随机盐，因此我们可以完全跳过那一步。让我们直接进入：

```php
// 供参考 - 默认成本为 10，可以自定义
// 哈希它，好好哈希它
$passwordHash = password_hash($_POST['password']);

// 这一部分仅用于演示
$db = new ImaginaryDatabase;
$db->user()->create(array(
  'password' => $passwordHash
));
```

然后在登录时验证用户的密码，你将执行操作：

```php
// 我们将从一个默认状态开始
// 失败，首先假设失败
$valid = FALSE;

// 从我们虚拟的数据库中获取密码哈希
$user = $db->user()->where([
  'email' => $_POST['email']
])->row();

// 现在检查登录密码是否匹配
$pass = $_POST['password'];
if (password_verify($pass, $user->pass) === TRUE) {
  $valid = TRUE;
}

// 其他检查、错误处理等...
if ($valid === TRUE) {
  // 有效的验证逻辑
}
```

如你所示，PHP 5.5 中的新密码函数让你的生活变得简单许多。此功能被内置到 PHP 中的另一个优势是，你可以依靠它在未来保持更新，而不需要自己去跟进最新的密码算法。尽管我知道这可能很迷人，但当可能时，请把它交给 PHP 核心团队这样的专业人士处理吧，这样你有更多时间去创作酷炫的东西。

当你实现身份验证方案时，请务必参考 PHP 文档以确保你的代码是最新的。此外，确保利用其他可用的密码函数，如 `password_get_info()` 和 `password_needs_rehash()`。

你还在用 PHP 5.3 吗？错过了那些使用新 5.5 的用户的乐趣吗？别担心，Anthony Ferrara 为你除了忧。他的 `password_compat` 库为 PHP 5.3.7 及以上版本实现了新的密码函数。你可以在这里 [Anthony 的 Github](https://github.com/ircmaxell/password_compat/) 下载它。我**强烈建议**尽可能使用它，而不是自己编写代码，它经过了测试，你可以信赖。

### 暴力破解防护

你可以拥有最出色的哈希，比如完全安全的哥们儿，但如果有人不断敲击你的登录页面直到找到正确密码，那对你毫无处。暴力破解是某人使用软件反复尝试不同的密码直到进入的过程。

防止这种攻击非常简单，遗憾的是我看到很多网站都容易受到这种攻击。那么，该如何保护自己呢？只需要让通过这种方式找到密码的时间长到不可行即可。

接下来，你可以对此进行扩展。基于 IP 的封禁：针对所有用户，限制特定 IP 仅允许 X 次登录尝试，而不是仅仅针对每个单独的用户。请务必包含友好的错误信息和合理的访问恢复时间；企业用户通常共享同一个公网 IP 地址，因此如果可能的话，你不希望因为一个坏用户而惩罚成千上万有效的用户。

另外注意，同样的逻辑也适用于 API 身份验证。不要给攻击者留下通过不同路径获取相同结果的机会。如果你在应用程序的前端保护了某些内容，然后通过 API 暴露了相同的功能，请确保在后端也同样进行了安全保护。

## 升级遗留系统

现在来谈谈那个回避的问题。听懂了吗？ElePHPant。是的，这是一个漫长的夜晚，抱歉。那么，该如何升级你现有的带有无盐值 `MD5` 密码的系统呢？

我将为你提供两个选项：

- 路径 1 - 当每个用户登录时，我们将静默地将他们的哈希升级为使用 `BCrypt`。他们甚至察觉不到区别。很快，你就会拥有一个安全性良好的密码数据库。

- 路径 2 - 使用 `BCrypt` 对数据库中现 `MD5` 哈希进行哈希。新密码将先用 `MD5` 哈希，然后再用 `BCrypt`。

### 升级路径 1

路径 1 是迁移到新身份验证方案的传统建议，在大多数情况下是目前的最佳选择。要实现这一点，你需要执行类似下面的操作：

```
 1 $valid = FALSE;
 2 
 3 //从我们虚拟的数据库中获取密码哈希\
4 se
5 $user = $db->user()-where([
 6   'email' => $_POST['email']
 7 ])->row();
 8 
 9 if ($user->pass_hash_algo === 'bcrypt') {
10//他们之前登录过并且
11   //升级了哈希，所以没问题
12   //像往一样继续验证登录
13 }
14 else {
15   //这是基于我们的旧哈希检查修改的
16   $oldHash = md5($_POST['password']);
17 
18   if ($oldHash === $user->pass) {
19     //使用他们刚刚提供的明文\
20     //密码生成新的哈希
21     $newHash = password_hash($_POST['password']);
22 
23     //将新哈希和标记保存到数据库中
24     $user->pass = $newHash;
25     $user->pass_hash_upgraded = 'bcrypt';
26     $user->save();
27 
28     $valid = TRUE;
29   }
30 
31   //其他检查、错误处理等...
32 }
```

部署了此修改后的登录系统后，你的用户将在登录时自动升级到新哈希。随着推荐的哈希算法不断，这一升级路径可以在多年后轻松修改。几年后，`SCrypt` 可能会成为认可的标准，将用户升级到该标准将轻而易举。

### 升级路径 2

路径 2 的解决方案并不完美，但它可以立即实现安全。路径 1 在每个用户下次登录之前保留不安全的哈希，而这种方法会在现在就保护你的数据，让你今晚不必失眠。通过此路径，你将立即使用 `BCrypt` 对所有当前密码哈希重新哈希。你的新哈希只是密码的 `MD5` 哈希的 `BCrypt` 哈希。这增加了过程的复杂性，因为你基本上将永远都要同时使用 `BCrypt` 和 `MD5`，多年后当你需要对 `SHA1` 处理过的 `MD5` 哈希进行 `SCrypt` `BCrypt` 处理时，这可能会变得繁琐。

这是一个两步骤的过程，首先编写一个脚本执行以下操作，并在你当前的数据库上运行它。请告诉我你是在数据库备份上操作的，而不是在生产服务器上。对吧？否则我会难过的……另外，在执行此操作时，你应该为每条记录添加某种状态。基本上把这当作示例，不要直接复制粘贴好吗。

```
 1 $users = $db->users()->result();
 2 
 3 foreach ($users as $user) {
 4 
 5   $newHash = password_hash($user->pass);
 6 
 7   $user->pass = $newHash;
 8   $user->save();
 9 
10 }
```

现在你的数据库已经更新，更改你的注册方法执行以下操作：

```
1 //先用 MD5 哈希再用 BCrypt
2 $passHash = password_hash(md5($_POST['password']));
3 
4 //后续部分仅用于演示
5 $db = new ImaginaryDatabase;
6 $db->user()->create([
7   'password' => $passHash
8 ]);
```

登录方法也需要检查 `MD5` 哈希过的密码，而不是明文：

```
 1 //从我们虚拟的数据库中获取哈希
 2 $user = $db->user()-where([
 3   'email' => $_POST['email']
 4 ])->row();
 5 
 6 //在 bcrypt 之前对密码进行 md5 哈希
 7 $md5Pass = md5($_POST['password']);
 8 
 9 //现在检查登录密码是否匹配
10 if (password_verify($md5Pass, $user->pass) === TRUE) {
12   $valid = TRUE;
13 }
14 
15 //其他检查、错误处理等...
```

```php
class UserModel
{
  //... other methods

  function login($user, $password)
  {
    if (password_verify($_POST['password'], $user->pass) === TRUE) {
      $valid = TRUE;
    }

    //other checks, error handling, etc...

    if ($valid === TRUE) {
      //successfully logged in

      //just example session class
      //your own code or framework will likely
      //have it's own session wrapper
      Session::put('user', $user->id);
      return TRUE;
    }

    //failed to login
    Session::put('user', NULL);
    return FALSE;
  }
}
```

我们已经保存了用户的成功登录状态。这里的一个关键点是记录他们的用户 ID。仅仅因为他们登录了，并不意味着他们有权在你的应用程序中执行任何想做的操作。

### 访问控制

除了确定用户是否已登录外，我们还需要确定他们是否有权访问其请求的页面/区块/功能。

让我们从一个基础用例开始。假设你有两种类型的用户：“普通用户” 和“管理员”。普通用户是权限受限的普通用户。管理员是拥有所有操作权限的网站管理员。管理员可以编辑或删除用户、管理帖子等。确保普通用户（即普通用户）——无法执行这些操作是至关重要的。

不同的框架对于何时以及何处检查适当访问权限有不同的约定。在 Laravel 中，首选使用过滤器。Symfony 使用了投票器。在大多数系统中，你可能只需要使用控制器的构造函数。以下是一个假设的示例；你的具体实现将会有所不同，并取决于你的决定。

首先，我们要在 `UserModel` 中添加一个方法来查询当前用户。

```php
class UserModel
{
  //... other methods

  //... login method

  function current()
  {
    $user = FALSE;

    if (isset($_SESSION['user']) === TRUE) {
      $user = DB::findById($_SESSION['user']);
    }

    return $user;
  }

  //let's imagine there is a method for retrieving
  //the user's groups.
}
```

现在，让我们使用这些方法来验证该用户是否拥有适当的访问权限。

```php
class AdminController
{
  function __construct()
  {
    $userModel = new UserModel;
    $user = $userModel->current();

    //check to make sure the user is logged in and
    //is a member of the admin group
    if ($user === FALSE || in_array('admin', $user->groups) === FALSE) {
      //please add a legit message
      //with headers and all that stuff
      die('Not Authorized');
    }
  }
  //other admin methods
}
```

你通常会在常规控制器之上使用某种抽象的访问层。该层应该将你的路由映射到查看该内容所需的访问级别。例如，`/admin/*` 可能仅允许“管理员”组的用户访问。`POST` 和 `PUT` 请求可能仅允许“编辑者”访问。`DELETE` 请求仅由“管理员”执行。

要点在于，每个页面都应该检查用户的访问级别，并确定他们是否有权执行请求的操作。你不应该假设如果用户能看到一个表单并将其 `POST` 到正确的端点，那么该用户就有权执行该操作。这将有助于确保防止恶意用户，并防止本不该访问这些数据的用户对你的数据进行意外更改。请认真对待这一点！这将为你或其他开发者节省不必要的时间和烦恼。

### 验证重定向

在应用程序的流程中，你通常会将表单 `POST` 到一个端点，验证该数据，执行某些操作，然后将用户重定向到应用程序的下一步。

如果你重定向到的页面包含敏感数据，某些可以通过直接向该页面发送请求来绕过你预期的流程。处理此问题的几种方法：第一种是根本不进行重定向。大多数时候，当你认为需要重定向时，你可以直接调用下一个方法。例如：



```php
if ($valid === TRUE && $dataSaved === TRUE) {
  URL::redirect('/blog/edit');
}
```

你可以在不进行重定向的情况下调用 `edit` 方法：

```php
if ($valid === TRUE && $dataSaved === TRUE) {
  $this->_edit(1);
}
```

在这个示例中，`_edit()` 方法将是一个保护或私有方法，在不通过上一步的情况下无法从 URL 访问。如果你确实需要一个独立的端点（如果该目的地有多个入口点，则可能是这样），你需要验证正确的步骤已经执行。在会话变量中沿每个请求传递任何适当的数据（通常称为 flash 数据）通常是最安全的方法。

```php
if ($valid === TRUE && $dataSaved === TRUE) {
  Session::flash('blogValid', TRUE);
  URL::redirect('/blog/edit');
}
```

在你的 `edit` 端点中，你会验证这些传递的数据：

```php
public function edit($id)
{
  if (Session::get('blogValid') !== TRUE) {
    //again, this should be a proper error
    die('Not Authorized');
  }
}
```

### 混淆

你听过“通过模糊性实现安全” 这个术语吗？它很少真实，但在某些情况下是有帮助的。大多数应用程序使用每个表中的 `ID` 字段作为主键。该 ID 然后在整个系统中用于访问数据。

但是，有时你不想向用户暴露真实的 ID。可能你正在发布一个新产品，但不希望用户知道他们是第 13 个用户。可能你拥有公开数据，但不希望你的网站被爬虫轻易抓取。

在这种情况下，你可以将 `ID` 混淆为非递增的内容（例如 1, 2, 3...），但可以转换为你的 `ID` 字段。与其这样做：

```php
Route::get('/edit/{id}', function($id) {
  //id = 432134
  $post = $db->post()->where([
    'id' => $id
  ])->row();
});
```

你可以这样做：

```php
Route::get('/edit/{hash}', function($hash) {
  //hash = BaPjae
  $id = HashId::decrypt($hash);

  $post = $db->post()->where([
    'id' => $id
  ])->row();
});
```

在这个示例中，`HashId::decrypt()` 调用仅仅是从你的服务器获取预存的安全哈希并将其应用于传递的哈希以确定 `ID`。这也可以反过来调用生成哈希：

```php
$hash = HashId::encrypt(432134);
echo $hash; // 输出 BaPjae
```

自己编写这些哈希方法其实相当简单，但我建议使用经过测试的 [HashIDs](http://www.hashids.org/php/) 库。这些库不仅易于使用，而且在许多编程语言中都有良好的维护，以确保整个基础设施的互操作性。

在某些情况下，可以认为混淆是必要的，甚至在你的特定用例中可能是强制要求的。例如，我见过人们将模糊性作为 HIPAA 数据的额外保护。一个用例是要求将 HIPAA 敏感数据存储在单独的数据库中；在这种情况下这是一个三层服务器架构。Web 应用程序使用的主键存储在一个数据库中（带有非敏感数据），敏感数据存储在另一个中，而中间数据库存储关系。这种设计是为了确保即使任何一个数据库被破解，获得的数据也是匿名或非敏感的。

我要再次强调这一点，因为它极其重要：在大多数情况下，模糊性并不能保护你免受任何合法的攻击。你不应该依赖它来确保安全。它仅仅让事情变得稍微难找一点手段。

## 安全文件处理

回到我们最初的故事：如果你有提供给用户查看或下载的文档，你不能简单地对 `*.pdf` 文件设置访问控制。为什么呢？我知道你们会问这个问题。我是这里的叙述者，这倒很有帮助。

你需要做的是将文件存储在服务器上，使其无法从你的 Web 服务器访问。这里有一个推荐的目录结构示例：

```
application/
composer.json
composer.lock
htdocs/
    .htaccess
    assets/
    templates/
    index.php
    robots.txt
uploads/
workers/
```

`htdocs/` 是 Apache（或你正在使用的任何 Web 服务器）为域名服务的位置。`uploads/` 是你存储上传文档的地方。你也可以通过服务器的配置来实现。在 Apache 中，如果 `uploads` 目录位于 `htdocs` 树下，你可以对指向该目录的任何请求返回 404 错误。

在你的应用程序中实现这一点，你需要根据文档类型创建一个用于访问文档的端点。例如，你可能需要提供每月财务报表，但仅提供给“会计”组的用户。

在这里我们定义访问这些内容的端点。通过这个端点，我们将验证用户的访问级别、读取文件，最后使用适当的头部将其输出到浏览器。

```
 1 Route::get(
 2   '/accounting/statements/{year}/{month}',
 3   function($year, $month) {
 4 
5 	check user access
 6 	$userModel = new UserModel;
 7 	$user = $userModel->current();
 8 
9 	check to make sure the user is logged in
10 	//and a member of accounting
11 	if ($user === FALSE || in_array('accounting', $us\
12 er->groups) === FALSE) {
13 	  //please add a legit error message
14 	  die('Not Authorized');
15 	}
16 
17 	//the user has access, let's read the file
18 	$directory = __DIR__ . '../uploads/acct/stmnts/';
19 	$filename  = (int) substr($year, 0, 4)  .
20 	             (int) substr($month, 0, 2) .
21 	             '.pdf';
22 
23 	//error handling for invalid files
24 
25 	//open the file
26 	$fileHandle = fopen($directory . $filename, 'r');
27 
28 	//read the file and close it
29 	$fileContents = fread($fileHandle);
30 	fclose($fileHandle);
31 
32 	//send the appropriate headers
33 	header('Content-type: application/pdf');
34 	header('Content-Disposition: inline; filename="' \
35 . $filename . '"');
36 	header('Content-Length: ' . filesize($directory .\
37  $filename));
38 	header('Expires: 0');
39 	header('Cache-Control: must-revalidate');
40 	header('Pragma: public');
41 
42 	//echo the file contents to the browser
43 	echo $fileContents;
44 
45 });
```

这防止了不应该看到此文件的人访问它，因为它位于 Web 服务器之外，并且经过了适当控制的检查。

### 总结

我们涵盖了基本的身份验证、通过验证进行的妥当访问控制以及安全文件处理。我希望你在开发下一个想法时能发现这些有所帮助。继续读下去，因为我们还没有结束。记住，我说了结束了才算真的结束！

# 第 5 章 - 安全默认值、跨站脚本和其他常见的攻击手段

本章是你需要防御的攻击的合集，因此并不具有概括性。请试着忍你的失望。

## 永远不要信任你自己 - 使用安全默认

安全系统的核心概念之一是安全默认。只要可能（而且通常都是可能的），你就应该尽早定义变量、属性等，并赋予安全的默认值。安全默认意味着 `NULL`、空或 `FALSE` 状态。在确定逻辑时，默认值始终应该是失败。例如，在之前的身份验证中，我检查密码是否正确。如果失败，函数将执行针对非正结果的默认逻辑。

让我们来看一个表单验证的简单示例。

```
 1 Route::post('/signup', function()
 2 {
3   //check for valid form
4   if (Form::validate('signup') === TRUE) {
5     //process the form
6   }
7 
8   //the default logic is failure
9   die('Invalid Form Data');
10 });
```

## 永远不要信任动态类型。它不是你的朋友。

动态类型是新程序员喜爱的特性。动态类型意味着你不需要对类型那么挑剔；只要足够接近它就能工作。此的问题在于，它并不总是按照你预期的方式工作。

让我们来看一个 PHP 原生函数 `stripos()` 的经典示例。场景是你尝试找出短语 `I am the one who knocks` 中是否存在字母 `i`。

```
 1 $phrase = 'I am the one who knocks';
 2 
3 $letterExists = stripos($phrase, 'i');
 4 
5 if ($letterExists != FALSE) {
6   echo 'we should be here';
7   return TRUE;
8 }
9 
10 echo "we shouldn't be here, yet we are";
11 return FALSE;
```

`stripos()` 函数返回匹配项在字符串中的索引。由于 `i` 是字符串的第一个字母，`stripos()` 返回 `0`。由于动态类型，`!= FALSE` 等同于 `0`。现在我们使用 `!==` 来修复这个问题。

```
 1 $phrase = 'I am the one who knocks';
 2 
3 $letterExists = stripos($phrase, 'i');
 4 
5 if ($letterExists !== FALSE) {
6   echo 'we should be here';
7   return TRUE;
8 }
9
10 echo "we shouldn't be here, and we aren't";
```

显式检查的另一个不为人知的优势是性能。大多数情况下，显式检查会更快，因为它不需要类型转换。如果你对 PHP 的性能差异感兴趣，我建议查看 [http://www.phpbench.com/]。

## 跨站脚本

跨站脚本 (XSS) 是向目标网站注入恶意代码的过程。这可以通过多种方式实现，但最终结果是用户的浏览器在当前会话中以用户的身份运行未经代码。

### 非持久性 XSS

这是传统的 XSS 攻击类型。它涉及向站点注入数据并引导用户访问恶意内容。

假设你网站上的页面接收 `?page_num=2&per_page=50` 作为查询字符串参数。如果你不对这些参数进行转义，攻击者可以将其值改为恶意代码。这些代码可以将用户带到删除页面、在他们的浏览器中运行 JavaScript 或进行任何客户端攻击。

在注入恶意代码后，攻击者通过某种方式让用户访问页面。当用户到达时，应用程序将验证其有效的用户会话并执行恶意代码。用户甚至可能删除自己的账户！

### 持久性 XSS

持久性 XSS 攻击是永久存储在服务器上的攻击。例如，像 Facebook 这样的社交共享网站允许用户保存并向其他用户消息。攻击者可以将恶意代码存储在 Facebook 帖子中。如果 Facebook 在显示这些数据时没有对其进行适当转义，该代码就会被执行。因此，任何看到攻击者状态的人都会运行这段恶意代码。

### 攻击入口点

我刚刚提到了两个 XSS 攻击入口点的示例，但这些并不是唯一的。基本上，任何从用户那里获取输入并将其显示在 Web 页面上的地方都是攻击者利用你网站的机会。

务必考虑数据进入系统的 `all` 地方，而不仅仅是输入字段。例如，你可能允许用户上传图片，然后重新显示图像 XIFF 数据。也许你可能会解析从外部程序导出的各种数据的 CSV 文件。在任何你重新显示信息的地方，都需要进行保护。

## 如何保护自己

修复此问题并不困难。首先，永远不要直接从 URL 获取数据并将其回显到浏览器。来自其他来源（如你的数据库或上传的文件）的数据也是如此。为了保护自己，你只需要对进入数据库的数据进行转义，并对显示给用户的数据进行转义。

我们之前已经在第 1 章中讨论过正确的数据库转义，因此我们将重点放在数据显示上。PHP 通过内置函数 `htmlentities()` 使这变得非常简单。该函数将妥妥地处理大多数数据。

让我们看看实现后的样子。你的视图文件以前看起来是这样：

```

1 <h1>Title</h1>

2 

3 Hello <?=$name?>,

```

现在应用保护后，它看起来是这样：

```

1 <h1>Title</h1>

2 

3 Hello <?=htmlentities($name)?>

```

如果你想保持 DRY^(22)，你可能会将此抽象为视图辅助函数库。大多数框架已经将其包含在它们的视图或模板库中。

## 跨站请求伪造

跨站请求伪造（CSRF）基本上是 XSS 攻击的对面。XSS 是通过受信任的网站利用用户，而 CSRF 则是通过受信任的用户来利用网站。

这方面的例子是攻击者发送伪造邮件，其中包含一个删除博客文章、电子邮件或任何内容的链接。目标用户随后点击链接并到达删除页面。由于用户是具有有效会话的管理员，你的应用程序将按照请求删除记录。用户并不知道该链接将他们带到了哪里，而现在他们的账户在未经许可的情况下被删除了。这可不妙。

这也不非是一个文本链接；它通常附带在图像或按钮上。这听起来可能是一个很小的风险，因为大多数关键网站功能都位于等待 POST 数据的表单之后。但同样很容易地扩展到使用按钮或 JavaScript 来提交隐藏表单。

### 如何防止此类攻击

第一步是确保 GET 请求不执行任何更改数据的操作。任何对数据执行的操作都应该要求 `POST`、`PUT` 或 `DELETE` 请求。如果用户点击删除按钮，他们应该被带到一个用于确认操作的表单。如果需要通过 GET 执行更改数据的操作（可能是为了 RESTful API），你可以在查询字符串中要求一个唯一的令牌。在接下来的示例中，我们将使用 POST 数据，但在处理 GET 请求时相同的概念也适用；只需在查询字符串中设置令牌而不是在 POST 参数中设置即可。

现在你已经通过提交表单来处理数据操作，我们需要向表单中添加 CSRF 令牌。我们的 CSRF 令牌将是一个标准的 Nonce（一次性数字）。我们将生成一个随机令牌，将其存储在用户的会话中，然后将其作为隐藏字段添加到我们的表单中。一旦表单被 POST，我们就可以 CSRF 令牌与会话中的令牌进行对比以验证请求。

首先，我们将创建一个生成令牌的函数。这通常会被放置在可以全局调用的地方，也许作为路由过滤器、投票者或辅助函数库。

```

 1 //假设表单类的其他部分在这里

 2 

 3 static function generateCsrf()

 4 {

 5   $token = mcrypt_create_iv(

 6     16,

 7     MCRYPT_DEV_URANDOM

 8   );

 9 

10   Session::flash(

 11     'csrfToken',

 12     $token

 13   );

 14 

15   return $token;

16 }

```

注意，我们在这里使用了 session flash 数据。Flash 数据将存储在会话中，但在被销毁之前只能在一次请求中。大多数会话包装类都支持这个概念。这使得我们的令牌不会在多个请求中有效。

接下来，我们将在路由闭包中调用它，并将令牌传递给生成表单的视图：

```

1 Route::get('/signup', function()

2 {

3   $data['token'] = Form::generateCsrf();

4 

5   return View::render('signup.form', $data);

6 });

```

现在是我们的视图，`signup/form.php`

```

 1 <form method="POST" action="/signup">

 2 

 3   <label>

 4 	First Name:

 5 	<input type="text" name="first_name" />

 6   </label>

 7 

 8   <label>

 9 	Last Name:

10 	<input type="text" name="last_name" />

11   </label>

 12 

 13   <label>

 14 	Email:
```



## CSRF 令牌验证

```html
<input type="text" name="email" />
</label>

<input type="hidden" name="token" value="<?=$token?>" />

<input type="submit" name="submit" value="Signup" />
</form>
```

当表单被 POST 时，我们可以对比会话中的令牌来验证请求：

```php
Route::post('/signup', function() {
  // 假设我们可以处理了
  if ($_POST['token'] === Session::get('csrfToken')) {
    // 处理逻辑
  } else {
    die('Invalid Form Data');
  }
});
```

现在由于有了这种令牌检查，如果攻击者欺骗用户提交虚假表单，请求将失败，因为会话中没有匹配的 CSRF 令牌。

在应用程序中，另一个常见问题是表单重复提交。用户提交表单以执行某些操作——例如从一个钱包转账 200 比特。用户点击提交，但他们没有立即注意到变化，于是再次点击。现在用户在无意中转账了 400 比特。幸运的是，我们讨论的 CSRF 令牌逻辑可以解决这个问题，无需额外工作。要在大多数情况下防止这种情况，我们只需要传递一个唯一的令牌，验证它，并在处理后将其清除。

## 外部程序安全

需要注意的另一点是你在服务器上使用的外部程序。例如，`PhpMyAdmin` 在其生命周期内出现过多个安全漏洞，导致服务器容易受到攻击。过时的 `Wordpress` 安装版本在开发领域也为人所知，是黑客的后门。任何在你的服务器上暴露关键函数的程序都是可能的攻击入口点。

尽量将你的外部依赖减少到最低，并始终将它们更新到最新的安全发布版本。

## 析构函数

在编写这本书的过程中，我玩得很开心。我也喝了很多朗姆酒。真心希望你学到了东西并享受了阅读过程，我们需要达到那种“知识与朗姆酒的比例”。

如果你想了解更多这里涵盖的任何主题，或者只是想就生命的意义进行争论，请与我联系[^23]。

感谢阅读。

![](img/benedmunds.jpg)

## 关于作者

[Ben Edmunds](http://benedmunds.com) 领导团队创建尖端的 Web 和移动应用。他是各种开发社区中活跃的领导者、开发者和演讲者。他从事专业软件开发已超过 10 年，在此期间处理过从机器人到政府项目的各类工作。

PHP Town Hall 播客共同主持人。Portland PHP 用户组共同组织者。开源倡导者。

## 安全审计 / 咨询

需要帮助应用书中讨论的内容吗？或者你希望有人为你进行审查以验证你的 Web 应用是否安全？

我每年提供有限次数的安全审计和咨询服务。如果你感兴趣，请与我联系，可以通过电子邮件 `consulting@benedmunds.com` 联系我。

## 参考文献

[^1]: feedback@buildsecurephpapps.com
[^2]: http://xkcd.com/327/
[^3]: 对于这些精确的细节，大部分尚未公开，因此我们无法确定这些是否是由 SQL 注入攻击造成的。但很大可能是这样。
[^4]: `mysql_*` 扩展及其方法已正式弃用。请不要使用它们。
[^5]: http://us1.php.net/manual/en/intro.pdo.php
[^6]: http://stackoverflow.com/questions/7394711/what-is-dynamic-typing
[^7]: http://us1.php.net/htmlentities
[^8]: http://us1.php.net/htmlspecialchars
[^9]: http://us1.php.net/escapeshellcmd
[^10]: http://us1.php.net/escapeshellarg
[^11]: http://en.wikipedia.org/wiki/Diplomatic_bag
[^12]: 这是基于事实的虚构故事。请不要起诉我，漫威。
[^13]: http://eprint.iacr.org/2005/165.pdf
[^14]: http://cryptography.hyperlink.cz/md5/MD5_collisions.pdf
[^15]: http://link.springer.com/chapter/10.1007/11535218_2#page-1
[^16]: http://en.wikipedia.org/wiki/Moore’s_law
[^17]: http://xkcd.com/936/
[^18]: http://www.php.net/manual/en/book.password.php
[^19]: http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.65.9811
[^20]: https://www.schneier.com/book-applied.html
[^21]: http://blog.ircmaxell.com/
[^22]: http://en.wikipedia.org/wiki/Don’t_repeat_yourself
[^23]: feedback@buildsecurephpapps.com
