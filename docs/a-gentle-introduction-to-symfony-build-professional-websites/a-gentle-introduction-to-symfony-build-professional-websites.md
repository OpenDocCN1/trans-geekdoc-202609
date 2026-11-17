# symfony 温和入门指南：PHP 和 symfony 构建专业网站指南：symfony 1.3 & 1.4：doctrine





![](img/0f886a7f4cbcc3939be96e985ca35ff4_0_0.png)


![](img/0f886a7f4cbcc3939be96e985ca35ff4_0_1.png)

# 第 1 章
介绍 Symfony

Symfony 能为您做什么？使用它需要什么？本章回答了这些问题。

## Symfony 简介

框架通过自动化许多为特定目的采用的模式来简化应用程序开发。框架还为代码添加结构，促使开发者编写更好的、更易读且更易维护的代码。最终，框架使编程更容易，因为它将复杂操作封装为简单语句。

Symfony 是一个完整的框架，旨在通过多种关键特性优化 Web 应用程序的开发。首先，它将 Web 应用程序的业务规则、服务器逻辑和表现层视图分开。它包含大量旨在缩短复杂 Web 应用程序开发时间的工具和类。此外，它自动化常见任务，使开发者能够完全专注于应用程序的具体细节。这些优势的最终结果意味着，每次构建新 Web 应用程序时都无需重复造轮子！

Symfony 完全使用 PHP 编写。它已在各种实际项目中经过彻底测试，实际上正在用于高要求的电子商务网站。它与大多数可用的数据库引擎兼容，包括 MySQL、PostgreSQL、Oracle 和 Microsoft SQL Server。它在 *类 Unix 和 Windows 平台上运行。让我们开始更仔细地了解其特性。

## Symfony 特性

Symfony 的构建旨在满足以下要求：

- 在大多数平台上易于安装和配置（并且保证在标准 *类 Unix 和 Windows 平台上运行）
- 与数据库引擎无关
- 大多数情况下易于使用，但仍足够灵活以适应复杂情况
- 基于“约定大于配置”的前提——开发者只需配置非约定部分
- 符合大多数 Web 最佳实践和设计模式
- 1. http://sf-to.org/answers
- 2. http://sf-to.org/delicious
- 3. http://sf-to.org/dailymotion
- 企业就绪——可适应现有信息技术（IT）政策和架构，并且足够稳定以用于长期项目
- 代码非常易读，带有 phpDocumentor 注释，便于维护
- 易于扩展，允许与其他供应商库集成

## 自动化 Web 项目特性

Web 项目中的大多数常见功能在 Symfony 中实现了自动化，如下所示：

- 内置的国际化层允许对数据和界面进行翻译，以及内容本地化。
- 表示层使用模板和布局，HTML 设计师无需了解框架即可构建。助手通过将大量代码封装为简单的函数调用来减少需要编写的表示代码量。
- 表单支持自动验证和重新填充，这确保了数据库中的数据质量以及更好的用户体验。
- 输出转义保护应用程序免受损坏数据的攻击。
- 缓存管理功能减少带宽使用和服务器负载。
- 身份验证和凭据功能便于创建受限区域和用户安全性管理。
- 路由和智能 URL 使页面地址成为界面的一部分且对搜索引擎友好。
- 内置电子邮件和 API 管理功能允许 Web 应用程序超越经典的浏览器交互。
- 列表由于自动分页、排序和过滤而更加用户友好。
- 工厂、插件和事件提供了高度的可扩展性。

## 开发环境和工具

为了满足拥有自身编码指南和项目管理规则的企业的需求，Symfony 可以完全自定义。它默认提供多个开发环境，并随附多个自动化常见软件工程任务的工具：

- 代码生成工具非常适合原型设计和一键式后端管理。
- 内置的单元和功能测试框架提供了完美的工具，允许进行测试驱动开发。
- 调试面板通过在开发者正在处理的页面上显示所需的所有信息来加速调试。
- 命令行界面自动化两台服务器之间的应用程序部署。
- 实时配置更改是可能且有效的。
- 日志记录功能为管理员提供有关应用程序活动的完整细节。

## 谁制作了 Symfony 以及为什么？

Symfony 的第一个版本于 2005 年 10 月由项目创始人 Fabien Potencier 发布，他是本书的合著者。Fabien 是 Sensio（http://www.sensio.com/）的首席执行官，Sensio 是一家法国 Web 机构，以其在 Web 开发方面的创新观点而闻名。

早在 2003 年，Fabien 就花了一些时间调查 PHP 中用于 Web 应用程序的现有开源开发工具。他发现没有任何工具满足前述要求。当 PHP 5 发布时，他决定可用工具已达到一个

- 4. http://www.sensio.com/





## Symfony 社区

Symfony 网站（http://www.symfony-project.org）一经推出，来自世界各地的众多开发者便下载并安装了该框架，阅读了在线文档，并使用 Symfony 构建了他们的第一个应用程序，热度开始不断升温。

当时，Web 应用程序框架正变得流行，PHP 社区对功能完整的框架需求旺盛。得益于其出色的代码质量和大量文档——这两点在框架类别中胜过其他竞争对手——Symfony 提供了一个引人注目的解决方案。贡献者很快开始涌现，提出补丁和改进，校对文档，并承担其他亟需的角色。

公开的源代码仓库和票务系统提供了多种贡献方式，所有志愿者都受到欢迎。Fabien 仍然是源代码仓库主干的主要提交者，并保证代码质量。

今天，Symfony 论坛、邮件列表和互联网中继聊天（IRC）频道提供了理想的支持渠道，几乎每个问题都能得到平均四个回答。新手每天都在安装 Symfony，Wiki 和代码片段部分托管了大量用户贡献的文档。如今，Symfony 是最流行的 PHP 框架之一。

Symfony 社区是该框架的第三大优势，我们希望你在读完本书后能加入其中。

- 5. http://www.symfony-project.org/
- 6. http://forum.symfony-project.org/
- 7. http://groups.google.com/group/symfony-users
- 8. http://groups.google.com/group/symfony-devs
- 9. irc://irc.freenode.net/symfony

## Symfony 适合我吗？

无论你是 PHP 专家还是 Web 应用程序编程的新手，都能使用 Symfony。决定是否使用它的主要因素是你项目的规模。

如果你想开发一个只有五到十页的简单网站，数据库访问受限，且无需确保其性能或提供文档，那么你应该坚持单独使用 PHP。你从 Web 应用程序框架中获益不大，使用面向对象或 MVC 模型很可能只会拖慢你的开发进程。顺便说一句，Symfony 未针对仅能在公共网关接口（CGI）模式下运行 PHP 脚本的共享服务器进行高效运行优化。

另一方面，如果你开发的是具有复杂业务逻辑的更复杂 Web 应用程序，单独使用 PHP 是不够的。如果你计划在未来维护或扩展你的应用程序，你需要代码轻量、可读且高效。如果你想以直观的方式使用最新的用户交互进展（例如 Ajax），你不能只写几百行 JavaScript。如果你想既享受乐趣又快速开发，那么单独使用 PHP 可能会让你失望。在所有这些情况下，Symfony 都是为你而设的。

而且，如果你是一名专业的 Web 开发人员，你已经了解 Web 应用程序框架的所有优势，并且需要一个成熟、文档完善且拥有庞大社区的框架。无需再搜索，Symfony 就是你的解决方案。

> 如果你想要直观演示，请查看 Symfony 网站上提供的演示视频。你会发现使用 Symfony 开发应用程序既快速又有趣。

## 基本概念

在开始使用 Symfony 之前，你应该了解一些基本概念。如果你已经知道 OOP、ORM、RAD、DRY、KISS、TDD 和 YAML 的含义，可以随意跳过此部分。

### PHP

Symfony 使用 PHP（http://www.php.net/）开发，并致力于使用同一种语言构建 Web 应用程序。因此，要充分利用该框架，需要扎实的 PHP 和面向对象编程知识。运行 Symfony 所需的最低 PHP 版本是 PHP 5.2.4。

### 面向对象编程（OOP）

本章不会讲解面向对象编程（OOP）。这本身就需要一整本书！因为 Symfony 大量使用了 PHP 5 起可用的面向对象机制，OOP 是学习 Symfony 的先决条件。

Wikipedia 对 OOP 的解释如下：

> "面向对象编程背后的理念是：计算机程序可以被视为由单个单元或对象组成的集合，这些对象相互作用，这与传统观点不同，传统观点认为程序是函数的集合，或者仅仅是给计算机的一组指令列表。"

PHP 实现了类、对象、方法、继承等面向对象范式及更多内容。不熟悉这些概念的人建议阅读相关的 PHP 文档，可在 http://www.php.net/manual/en/language.oop5.basic.php 查阅。

### 魔术方法

PHP 对象功能的优势之一是使用魔术方法。这些方法可用于在不修改外部代码的情况下覆盖类的默认行为。它们使 PHP 语法更简洁、更具可扩展性。它们很容易识别，因为魔术方法的名称以两个下划线（__）开头。

例如，在显示对象时，PHP 会隐式查找该对象的 __toString() 方法，以查看开发者是否定义了自定义显示格式：

```
$myObject = new myClass();
echo $myObject;

// Will look for a magic method
echo $myObject->__toString();
```

Symfony 使用魔术方法，因此你应该对它们有深入的了解。它们在 PHP 文档（http://www.php.net/manual/en/language.oop5.magic.php）中有所描述。

### 对象关系映射（ORM）

数据库是关系型的。PHP 和 Symfony 是面向对象的。要以面向对象的方式访问数据库，需要一个将对象逻辑转换为关系逻辑的接口。这种接口称为对象关系映射，或 ORM。

ORM 由提供数据访问并将业务规则封装在内的对象组成。

对象/关系抽象层的一个好处是，它防止你使用特定于某个数据库的语法。它会自动将对模型对象的调用转换为针对当前数据库优化的 SQL 查询。

这意味着在项目进行中切换到另一个数据库系统很容易。想象一下，你需要为一个应用程序编写快速原型，但客户尚未决定哪种数据库系统最适合他的需求。例如，你可以先使用 SQLite 开始构建应用程序，并在客户准备好决定时切换到 MySQL、PostgreSQL 或 Oracle。只需更改配置文件中的一行即可。

抽象层封装了数据逻辑。应用程序的其余部分不需要知道 SQL 查询，访问数据库的 SQL 也易于查找。专注于数据库编程的开发人员也清楚地知道去哪里。

使用对象代替记录、使用类代替表格，还有另一个好处：你可以为表添加新的访问器。例如，如果你有一个名为 Client 的表，包含 FirstName 和 LastName 两个字段，你可能希望只需要一个 Name。在面向对象的世界中，这就像向 Client 类添加一个新的访问器方法一样简单，如下所示：

```
public function getName()
{
 return $this->getFirstName().' '.$this->getLastName();
}
```

所有重复的数据访问函数和数据的业务逻辑都可以在这样的对象中维护。例如，考虑一个你用来保存项目的 ShoppingCart 类。





（它们都是对象）。要在结账时获取购物车的总金额，可以添加一个`getTotal()`方法，如下所示：

```
public function getTotal()
{
    $total = 0;
    foreach ($this->getItems() as $item)
    {
        $total += $item->getPrice() * $item->getQuantity();
    }

    return $total;
}
```

使用此方法，我们可以控制对象层面返回的值。假设以后决定添加影响总价的折扣逻辑，只需将其添加到`getTotal()`方法，甚至添加到项目的`getPrice()`方法中，即可返回正确的值。

开箱即用，symfony支持PHP中两种最流行的开源ORM：Propel和Doctrine。Symfony与两者无缝集成。创建新symfony项目时，使用Propel或Doctrine是个人选择问题。

本书将介绍如何使用Propel和Doctrine对象，但如需更完整的参考，建议访问Propel网站或Doctrine网站。

- 13. http://www.propelorm.org/
- 14. http://www.doctrine-project.org/

## 快速应用开发（RAD）

编写Web应用程序长期以来一直是一项乏味且缓慢的工作。遵循通常的软件工程生命周期（例如统一软件开发过程提出的生命周期），在编写完整的需求规格说明、绘制大量统一建模语言（UML）图表并制作大量初步文档之前，Web应用程序的开发无法开始。这主要是由于开发速度总体较慢、编程语言的通用性不足（在实际看到程序运行之前，你需要构建、编译、重启，还不知道要做什么），以及最重要的是，客户过去相当理智，不会不断改变主意。

如今，商业发展日益加快，客户倾向于在项目开发过程中不断改变主意。当然，他们期望开发团队能适应他们的需求并快速修改应用程序的结构。幸运的是，使用Python、Ruby和PHP等脚本语言，可以轻松应用其他编程策略，例如快速应用开发（RAD）或敏捷软件开发。

这些方法论的一个理念是尽早开始开发，以便客户可以审查可用原型并提供进一步指导。随后，应用程序通过迭代过程构建，在短开发周期中发布功能越来越丰富的版本。

对开发人员而言，后果众多。开发人员在实现功能时不需要考虑未来。所使用的方法应尽可能简单直接。KISS原则的箴言很好地说明了这一点：保持简单，傻瓜。

当需求演变或添加功能时，现有代码通常需要部分重写。这一过程称为重构，在Web应用程序开发中非常常见。代码会根据其性质移动到其他位置。重复的代码部分会被重构到单一位置，从而应用不要重复自己（DRY）原则。

并且为了确保应用程序在不断变化时仍能运行，它需要一套可自动化的完整单元测试。如果编写良好，单元测试是确保添加或重构代码不会损坏任何东西的可靠方式。有些开发方法论甚至规定在编码之前编写测试——这被称为测试驱动开发（TDD）。

> 与敏捷开发相关的其他原则和良好习惯还有很多。最有效的敏捷开发方法论之一称为极限编程（缩写为XP），XP文献将教你大量关于如何快速有效地开发应用程序的知识。一个不错的起点是Kent Beck（Addison-Wesley）的XP系列图书。

Symfony是RAD的完美工具。事实上，该框架是由一家Web机构为其自身项目应用RAD原则而构建的。这意味着学习使用symfony不仅仅是学习一门新语言，更多的是运用正确的反应和最佳判断，以更有效的方式构建应用程序。

## YAML

根据官方YAML网站的描述，YAML是“一种对所有人类友好的、用于所有编程语言的数据序列化标准”。换一种说法，YAML是一种非常简单的语言，用以类XML的方式描述数据，但语法更加简单。它尤其适用于描述可以转换为数组和哈希的数据，例如：

```
$house = array(
    'family' => array(
        'name' => 'Doe',
        'parents' => array('John', 'Jane'),
        'children' => array('Paul', 'Mark', 'Simone')
    ),
    'address' => array(
        'number' => 34,
        'street' => 'Main Street',
        'city' => 'Nowheretown',
        'zipcode' => '12345'
    )
);
```

这个PHP数组可以通过解析YAML字符串自动创建：

```
house:
  family:
    name: Doe
    parents:
      - John
      - Jane
    children:
      - Paul
      - Mark
      - Simone
  address:
    number: 34
    street: Main Street
    city: Nowheretown
    zipcode: "12345"
```

- 15. http://www.yaml.org/

在YAML中，结构通过缩进显示，序列项由破折号表示，映射中的键/值对由冒号分隔。YAML还具有简写语法，可用更少行描述相同结构，其中数组用[]显式表示，哈希用{}表示。因此，前面的YAML数据可以以更短的方式编写，如下所示：

```
Listing 1-6
house:
family: { name: Doe, parents: [John, Jane], children: [Paul, Mark,
Simone] }
address: { number: 34, street: Main Street, city: Nowheretown, zipcode:
"12345" }
```

YAML是“YAML不是标记语言”的缩写，发音为“yaml”。该格式自2001年以来一直存在，YAML解析器适用于多种语言。

> YAML格式的规范可在 http://www.yaml.org/16 上查阅。

如你所见，YAML比XML编写速度快得多（不再需要闭合标签或显式引号），且比.ini文件更强大（后者不支持层次结构）。这就是为什么symfony使用YAML作为存储配置的首选语言。你将在本书中看到大量YAML文件，但它非常直截了当，你可能不需要再了解更多关于它的内容。

## 总结

Symfony是一个PHP Web应用程序框架。它在PHP语言之上增加了一个新层，提供了加速复杂Web应用程序开发的工具。本书将向你介绍它的方方面面，你只需熟悉现代编程的基本概念即可理解它——即面向对象编程（OOP）、对象关系映射（ORM）和快速应用开发（RAD）。唯一所需的技术背景是PHP知识。

# 第 2 章

## 探索Symfony的代码

乍一看，基于symfony的应用程序背后的代码可能显得相当令人生畏。它由许多目录和脚本组成，文件是PHP类、HTML甚至两者混合的集合。你还会看到对类的引用，这些类在应用程序文件夹中找不到，且目录深度可达六层。但一旦你理解了这种看似复杂现象背后的原因，你会突然觉得它是如此自然，以至于你不会用任何其他结构来替换symfony应用程序结构。本章将消除那种畏难情绪。

## MVC模式

Symfony基于经典Web设计模式，即MVC架构，包含三个层次：

- 模型表示应用程序所操作的信息——其业务逻辑。
- 视图将模型渲染为适合与用户交互的网页。
- 控制器响应用户操作，并在适当的时候调用对模型或视图的更改。

图2-1说明了MVC模式。

MVC架构将业务逻辑（模型）与表示（视图）分离，从而提高可维护性。例如，如果你的应用程序需要同时在标准Web浏览器和手持设备上运行，你只需要一个新视图；可以保留原始控制器和模型。控制器有助于从模型和视图中隐藏请求所使用的协议细节（HTTP、控制台模式、邮件等等）。而模型抽象了数据的逻辑，使视图和动作独立于应用程序使用的数据库类型等因素。

图2-1 - MVC模式



![](img/0f886a7f4cbcc3939be96e985ca35ff4_19_0.png)

## MVC 分层

为了帮助你理解 MVC 的优势，让我们看看如何将一个基本的 PHP 应用程序转换为 MVC 架构的应用程序。博客应用程序的帖子列表将是一个完美的示例。

### 扁平化编程

在一个扁平的 PHP 文件中，显示数据库条目列表可能就像清单 2-1 中所示的脚本。

### 清单 2-1 - 扁平脚本

```php
<?php

// Connecting, selecting database
$link = mysql_connect('localhost', 'myuser', 'mypassword');
mysql_select_db('blog_db', $link);

// Performing SQL query
$result = mysql_query('SELECT date, title FROM post', $link);

?>

<html>
<head>
<title>List of Posts</title>
</head>
<body>
<h1>List of Posts</h1>
<table>
<tr><th>Date</th><th>Title</th></tr>
<?php
// Printing results in HTML
while ($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    echo "</tr>\n";
    printf("<td>%s</td>\n", $row['date']);
    printf("<td>%s</td>\n", $row['title']);
    echo "</tr>\n";
}
?>
</table>
</body>
</html>

<?php

// Closing connection
mysql_close($link);
?>

```

编写快速，执行迅速，却难以维护。这段代码的主要问题如下：

- 没有错误检查（如果数据库连接失败怎么办？）。
- HTML 和 PHP 代码混在一起，甚至交织在一起。
- 代码与 MySQL 数据库绑定。

### 隔离表现层

清单 2-1 中的 echo 和 print 调用使代码难以阅读。使用当前语法修改 HTML 代码以增强表现效果很麻烦。因此，可以将代码分为两部分。首先，包含所有业务逻辑的纯 PHP 代码放在控制器脚本中，如清单 2-2 所示。

### 清单 2-2 - 控制器部分，位于 index.php 中

```php
<?php

// Connecting, selecting database
$link = mysql_connect('localhost', 'myuser', 'mypassword');
mysql_select_db('blog_db', $link);

// Performing SQL query
$result = mysql_query('SELECT date, title FROM post', $link);

// Filling up the array for the view
$posts = array();
while ($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    $posts[] = $row;
}

// Closing connection
mysql_close($link);

// Requiring the view
require('view.php');
```

包含类模板 PHP 语法的 HTML 代码存储在视图脚本中，如清单 2-3 所示。

### 清单 2-3 - 视图部分，位于 view.php 中

```
<html>
  <head>
  <title>List of Posts</title>
  </head>
  <body>
    <h1>List of Posts</h1>
    <table>
      <tr><th>Date</th><th>Title</th></tr>
      <?php foreach ($posts as $post): ?>
      <tr>
        <td><?php echo $post['date'] ?></td>
        <td><?php echo $post['title'] ?></td>
      </tr>
      <?php endforeach; ?>
    </table>
  </body>
</html>
```

判断视图是否足够简洁的一个好经验是：它应该只包含最少量的 PHP 代码，以便没有 PHP 知识的 HTML 设计师也能理解。视图中最常见的语句是 echo、if/endif、foreach/endforeach，基本上就这些。此外，不应有 PHP 代码输出 HTML 标签。

所有逻辑都已移至控制器脚本，该脚本仅包含纯 PHP 代码，不包含任何 HTML。事实上，你可以想象同一个控制器可以重复用于完全不同的表现形式，例如 PDF 文件或 XML 结构。

### 隔离数据操作

控制器脚本中的大部分代码都用于数据操作。但是，如果你需要为另一个控制器（例如输出博客文章 RSS 源的控制器）获取帖子列表，该怎么办？如果你想将所有数据库查询保存在同一位置，以避免代码重复，该怎么办？如果你决定更改数据模型，将 post 表重命名为 weblog_post，该怎么办？如果你想从 MySQL 切换到 PostgreSQL，该怎么办？为了实现所有这些可能性，你需要从控制器中删除数据操作代码，并将其放入另一个称为模型的脚本中，如清单 2-4 所示。

### 清单 2-4 - 模型部分，位于 model.php 中

```php
<?php

function getAllPosts()
{
  // Connecting, selecting database
  $link = mysql_connect('localhost', 'myuser', 'mypassword');
  mysql_select_db('blog_db', $link);

  // Performing SQL query
  $result = mysql_query('SELECT date, title FROM post', $link);

  // Filling up the array
  $posts = array();
  while ($row = mysql_fetch_array($result, MYSQL_ASSOC))
  {
    $posts[] = $row;
  }
// Closing connection
mysql_close($link);

return $posts;
}
```

修订后的控制器如清单 2-5 所示。

### 清单 2-5 - 控制器部分（修订版），位于 index.php 中

```php
<?php

// Requiring the model
require_once('model.php');

// Retrieving the list of posts
$posts = getAllPosts();

// Requiring the view
require('view.php');
```

控制器变得更易于阅读。它的唯一任务是从模型获取数据并将其传递给视图。在更复杂的应用程序中，控制器还处理请求、用户会话、身份验证等等。在模型中使用明确的函数名称，甚至使控制器中的代码注释变得多余。

模型脚本专用于数据访问，并可以相应地组织。所有不依赖于数据层（例如请求参数）的参数都必须由控制器提供，而不是由模型直接访问。模型函数可以轻松地在另一个控制器中重用。

### 超越 MVC 的层分离

因此，MVC 架构的原则是根据代码的性质将其分为三层：数据逻辑代码放在模型中，表现代码放在视图中，应用逻辑放在控制器中。

其他附加设计模式可以使编码体验更加轻松。模型、视图和控制器层可以进一步细分。

### 数据库抽象

模型层可以拆分为数据访问层和数据库抽象层。这样，数据访问函数将不使用依赖数据库的查询语句，而是调用其他将自行执行查询的函数。如果日后更改数据库系统，只需更新数据库抽象层。

清单 2-6 展示了一个数据库抽象层示例，随后是清单 2-7 中 MySQL 特定数据访问层的示例。

### 清单 2-6 - 模型的数据库抽象部分

```php
<?php

function open_connection($host, $user, $password)
{
    return mysql_connect($host, $user, $password);
}

function close_connection($link)
{
    mysql_close($link);
}

function query_database($query, $database, $link)
{
    mysql_select_db($database, $link);

    return mysql_query($query, $link);
}

function fetch_results($result)
{
    return mysql_fetch_array($result, MYSQL_ASSOC);
}
```

### 清单 2-7 - 模型的数据访问部分

```php
function getAllPosts()
{
    // Connecting to database
    $link = open_connection('localhost', 'myuser', 'mypassword');

    // Performing SQL query
    // $result = query_database('SELECT date, title FROM post', 'blog_db',
    $link);

    // Filling up the array
    $posts = array();
    while ($row = fetch_results($result))
    {
        $posts[] = $row;
    }

    // Closing connection
    close_connection($link);

    return $posts;
}
```

你可以检查数据访问层中没有任何依赖数据库引擎的函数，从而使其与数据库无关。此外，数据库抽象层中创建的函数可以重复用于许多其他需要访问数据库的模型函数。

> 清单 2-6 和 2-7 中的示例仍然不够理想，要实现完全的数据库抽象（例如通过数据库无关的查询构建器抽象 SQL 代码、将所有函数移入类中等）还有许多工作要做。但本书的目的不是教你手动编写所有这些代码，你将在第 8 章中看到 symfony 原生支持出色的抽象。




## 视图元素

视图层也可以从代码分离中获益。一个网页在整个应用程序中通常包含一致的元素：页面标题、图形布局、页脚和全局导航。只有页面的内部部分会发生变化。这就是为什么视图被分为布局和模板。布局通常对整个应用程序或一组页面是全局的。模板只是将控制器提供的变量成形。需要一些逻辑来使这些组件协同工作，这个视图逻辑层将保留“视图”名称。根据这些原则，清单 2-3 中的视图部分可以分为三部分，如清单 2-8、2-9 和 2-10 所示。

```
Listing 2-8 - The Template Part of the View, in mytemplate.php

<h1>List of Posts</h1>
<table>
<tr><th>Date</th><th>Title</th></tr>
<?php foreach ($posts as $post): ?>
    <tr>
    <td><?php echo $post['date'] ?></td>
    <td><?php echo $post['title'] ?></td>
    </tr>
<?php endforeach; ?>
</table>
```

```
Listing 2-9 - The View Logic Part of the View

<?php
$title = 'List of Posts';
$posts = getAllPosts();
```

```
Listing 2-10 - The Layout Part of the View

<html>
<head>
<title><?php echo $title ?></title>
</head>
<body>
<?php include('mytemplate.php'); ?>
</body>
</html>
```

## 动作和前端控制器

在之前的示例中，控制器不做太多工作，但在真实的 Web 应用程序中，控制器有大量工作要做。这项工作的重要部分对应用程序中的所有控制器都是共通的。共通任务包括请求处理、安全处理、加载应用程序配置以及类似的例行工作。这就是为什么控制器通常被分为一个对整个应用程序唯一的前端控制器，以及仅包含特定于单个页面的控制器代码的动作。

前端控制器的一大优势是，它为整个应用程序提供了唯一的入口点。如果你决定关闭对应用程序的访问，只需编辑前端控制器脚本即可。在没有前端控制器的应用程序中，每个单独的控制器都需要被禁用。

## 面向对象

之前的所有示例都使用过程式编程。现代语言的面向对象能力使编程变得更加容易，因为对象可以封装逻辑、相互继承，并提供整洁的命名约定。

在非面向对象语言中实现 MVC 架构会引起命名空间和代码重复问题，且整体代码难以阅读。

面向对象让开发者能够处理视图对象、控制器对象和模型类等内容，并将之前示例中的所有函数转换为方法。对于 MVC 架构而言，这是必不可少的。

> 如果你想深入了解在面向对象环境中 Web 应用程序的设计模式，请阅读马丁·福勒（Martin Fowler）的《企业应用架构模式》（Patterns of Enterprise Application Architecture，Addison-Wesley，ISBN: 0-32112-742-0）。福勒书中的代码示例使用 Java 或 C# 编写，但 PHP 开发者仍然可以轻松阅读。

## Symfony 的 MVC 实现

稍等一下。对于单个页面列出博客文章，需要多少个组件？如图 2-2 所示，我们有以下部分：

- 模型层
  - 数据库抽象
  - 数据访问
- 视图层
  - 视图
  - 模板
  - 布局
- 控制器层
  - 前端控制器
  - 动作

七个脚本——每次创建新页面都要打开和修改如此多的文件！不过，symfony 让事情变得简单。在吸收 MVC 架构精华的同时，symfony 以一种使应用程序开发快速且无痛苦的方式实现了它。

首先，前端控制器和布局对应用程序中的所有动作都是共通的。你可以有多个控制器和布局，但每种只需要一个。前端控制器是纯粹的 MVC 逻辑组件，你永远不需要编写任何前端控制器，因为 symfony 会为你生成它。

另一个好消息是，模型层的类也会根据你的数据结构自动生成。这是 ORM 库的工作，它提供类骨架和代码生成。如果 ORM 发现外键约束或日期字段，它将提供特殊的访问器和修改器方法，使数据操作变得轻而易举。而且，数据库抽象对你来说完全不可见，因为它由 PHP Data Objects 原生处理。因此，如果你决定随时更换数据库引擎，你无需重构任何代码。你只需要更改一个配置参数。

最后，视图逻辑可以轻松地转换为一个简单的配置文件，无需编程。

图 2-2 - Symfony 工作流

![](img/0f886a7f4cbcc3939be96e985ca35ff4_26_0.png)

这意味着，我们示例中描述的文章列表在 symfony 中只需要三个文件即可工作，如清单 2-11、2-12 和 2-13 所示。

```
Listing 2-11 - list Action, in myproject/apps/myapp/modules/weblog/actions/actions.class.php

```php
<?php

class weblogActions extends sfActions
{
    public function executeList()
    {
        $this->posts = PostPeer::doSelect(new Criteria());
    }
}
```
```

```
Listing 2-12 - list Template, in myproject/apps/myapp/modules/weblog/templates/listSuccess.php

```php
<?php slot('title', 'List of Posts') ?>

<h1>List of Posts</h1>
<table>
<tr><th>Date</th><th>Title</th></tr>
<?php foreach ($posts as $post): ?>
<tr>
<td><?php echo $post->getDate() ?></td>
<td><?php echo $post->getTitle() ?></td>
</tr>
<?php endforeach; ?>
</table>
```
```

此外，你仍然需要定义一个布局，如清单 2-13 所示，但它将被多次重用。

清单 2-13 - 布局，位于 myproject/apps/myapp/templates/layout.php

```
<html>
<head>
<title><?php include_slot('title') ?></title>
</head>
<body>
<?php echo $sf_content ?>
</body>
</html>
```

这真的是你所需要的全部。这是显示与之前清单 2-1 中所示平面脚本完全相同页面所需的精确代码。其余部分（使所有组件协同工作）由 symfony 处理。如果你数一下行数，你会发现，使用 symfony 在 MVC 架构中创建文章列表所需的时间和编码量，与编写平面文件并无不同。尽管如此，它为你带来巨大的优势，尤其是代码组织清晰、可重用性、灵活性，以及更多乐趣。作为额外福利，你还拥有 XHTML 合规性、调试能力、易配置、数据库抽象、智能 URL 路由、多环境以及更多开发工具。

## Symfony 核心类

symfony 的 MVC 实现使用了几个你在这本书中会经常遇到的类：

- sfController 是控制器类。它解码请求并将其交给动作。
- sfRequest 存储所有请求元素（参数、cookie、标头等）。
- sfResponse 包含响应标头和内容。这是最终将被转换为 HTML 响应并发送给用户的对象。
- 上下文（通过 sfContext::getInstance() 获取）存储对所有核心对象和当前配置的引用；它可从任何位置访问。

你将在第 6 章了解更多关于这些对象的内容。

正如你所见，所有 symfony 类都使用 sf 前缀，模板中的 symfony 核心变量也是如此。这应当避免与你自己的类和变量发生名称冲突，并使核心框架类易于识别。

> 在 symfony 使用的编码规范中，UpperCamelCase 是类和变量命名的标准。存在两个例外：核心 symfony 类以 sf 开头，该前缀为小写；模板中的变量使用下划线分隔语法。




## 代码组织

现在你已经了解了 Symfony 应用程序的不同组件，你可能想知道它们是如何组织的。Symfony 在项目结构中组织代码，并将项目文件放入标准树形结构中。

## 项目结构：应用程序、模块和动作

在 Symfony 中，项目是在给定域名下可用的一组服务和操作，共享相同的对象模型。

在项目中，操作被逻辑地分组到应用程序中。一个应用程序通常可以独立于同一项目中的其他应用程序运行。在大多数情况下，项目将包含两个应用程序：一个用于前台，一个用于后台，共享同一个数据库。但你也可以让一个项目包含许多小型网站，每个网站作为不同的应用程序。请注意，应用程序之间的超链接必须是绝对形式。

每个应用程序由一个或多个模块组成。一个模块通常表示一个页面或一组具有相似目的的页面。例如，你可能会有 home、articles、help、shoppingCart、account 等模块。

模块包含动作，表示在模块中可以执行的各种操作。例如，购物车模块可以有 add、show 和 update 动作。通常，动作可以用动词来描述。处理动作几乎就像处理经典 Web 应用程序中的页面一样，尽管两个动作可能会导致同一页面（例如，在博客中添加评论会重新显示带有新评论的帖子）。

> 如果这对初始项目来说层级太多，将所有动作分组到一个单一模块中非常简单，这样可以保持文件结构简单。当应用程序变得更复杂时，就该将动作组织到单独的模块中了。如前所述，为了改善代码结构或可读性（但保持其行为不变）而重写代码称为重构，在应用 RAD 原则时你会经常这样做。

### 图 2-3 - 代码组织示例

![](img/0f886a7f4cbcc3939be96e985ca35ff4_28_0.png)

## 文件树结构

所有 Web 项目通常共享相同类型的内容，例如：

- 数据库，如 MySQL 或 PostgreSQL
- 静态文件（HTML、图像、JavaScript 文件、样式表等）
- 站点用户和管理员上传的文件
- PHP 类和库
- 外部库（第三方脚本）
- 批处理文件（通过命令行或 cron 表启动的脚本）
- 日志文件（应用程序和/或服务器写入的跟踪）
- 配置文件

Symfony 提供标准文件树结构，以逻辑方式组织所有这些内容，与架构选择（MVC 模式和项目/应用程序/模块分组）保持一致。这是初始化每个项目、应用程序或模块时自动创建的树结构。当然，你可以完全自定义它，以便按自己的意愿重新组织文件和目录，或满足客户的要求。

## 根目录树结构

以下是 Symfony 项目根目录下的目录：

```
apps/
    frontend/
    backend/
    cache/
    config/
    data/
    sql/
    doc/
    lib/
    model/
    log/
    plugins/
    test/
        bootstrap/
        unit/
        functional/
    web/
        css/
        images/
        js/
        uploads/
```

### 表 2-1 - 根目录

| 目录 | 描述 |
| --- | --- |
| apps/ | 包含项目中每个应用程序的一个目录（通常，前台和后台分别为 frontend 和 backend）。 |
| cache/ | 包含配置的缓存版本，以及（如果你启用它）项目操作和模板的缓存版本。缓存机制（第 12 章详细介绍）使用这些文件来加快 Web 请求的响应速度。每个应用程序都会在此处有一个子目录，包含预处理的 PHP 和 HTML 文件。 |
| config/ | 保存项目的一般配置。 |
| data/ | 在这里，你可以存储项目的数据文件，例如数据库架构、创建表的 SQL 文件，甚至 SQLite 数据库文件。 |
| doc/ | 存储项目文档的默认位置 |
| lib/ | 专用于外部类或库。在这里，你可以添加需要在应用程序之间共享的代码。model/ 子目录存储项目的对象模型（在第 8 章中描述）。 |
| log/ | 存储由 Symfony 直接生成的适用日志文件。它还可以包含 Web 服务器日志文件、数据库日志文件或项目任何部分的日志文件。Symfony 为每个应用程序和每个环境创建一个日志文件（日志文件在第 16 章中讨论）。 |
| plugins/ | 存储应用程序中安装的插件（插件在第 17 章中讨论）。 |
| test/ | 包含用 PHP 编写且与 Symfony 测试框架兼容的单元测试和功能测试（在第 15 章中讨论）。在项目设置期间，Symfony 会自动添加一些带有少量基本测试的存根。 |
| web/ | Web 服务器的根目录。仅此目录中的文件可以从 Internet 访问。 |

## 应用程序树结构

所有应用程序目录的树结构相同：

```
apps/
[application name]/
config/
i18n/
lib/
modules/
templates/
layout.php
```

### 表 2-2 - 应用程序子目录

| 目录 | 描述 |
| --- | --- |
| config/ | 包含大量 YAML 配置文件。这里存储了大部分应用程序配置，除了框架本身中的默认参数。请注意，如果需要，默认参数仍然可以在此处覆盖。你将在第 5 章了解更多关于应用程序配置的内容。 |
| i18n/ | 包含用于应用程序国际化的文件，主要是界面翻译文件（第 13 章涉及国际化）。如果你选择使用数据库进行国际化，可以跳过此目录。 |
| lib/ | 包含特定于应用程序的类和库。 |
| modules/ | 存储包含应用程序功能的所有模块。 |
| templates/ | 列出应用程序的全局模板，即由所有模块共享的模板。默认情况下，它包含一个 layout.php 文件，这是模块模板插入的主布局。 |

对于新应用程序，i18n/、lib/ 和 modules/ 目录为空。

应用程序的类无法访问同一项目中其他应用程序的方法或属性。还要注意，同一项目中两个应用程序之间的超链接必须采用绝对形式。在初始化时（即选择如何将项目划分为应用程序时），你需要牢记这一最后限制。

## 模块树结构

每个应用程序包含一个或多个模块。每个模块在 modules 目录中都有自己的子目录，该目录名称在设置期间选择。

这是模块的典型树结构：

```
apps/
  [application name]/
    modules/
      [module name]/
        actions/
          actions.class.php
        config/
        lib/
        templates/
          indexSuccess.php
```

### 表 2-3 - 模块子目录

| 目录 | 描述 |
| --- | --- |
| actions/ | 通常包含一个名为 `actions.class.php` 的单一类文件，你可以在其中存储模块的所有动作。你也可以将模块的不同动作写入单独的文件。 |
| config/ | 可以包含带有模块局部参数的自定义配置文件。 |
| lib/ | 存储特定于模块的类和库。 |
| templates/ | 包含与模块动作对应的模板。模块设置期间会创建一个名为 `indexSuccess.php` 的默认模板。 |

对于新模块，config/ 和 lib/ 目录不会自动创建，因此如果需要，你需要手动创建它们。

## Web 树结构

Web 目录（即公开可访问文件的目录）的限制非常少。遵循一些基本命名约定将在模板中提供默认行为和有用的快捷方式。以下是 Web 目录结构的示例：

```
web/
  css/
  images/
  js/
  uploads/
```





通常，静态文件分布在表 2-4 列出的目录中。

## 表 2-4 - 典型 Web 子目录

| Directory | Description |
|---|---|
| css/ | 包含带 .css 扩展名的样式表。 |
| images/ | 包含带 .jpg、.png 或 .gif 扩展名的图像。 |
| js/ | 包含带 .js 扩展名的 JavaScript 文件。 |
| uploads/ | 可以包含用户上传的文件。尽管该目录通常包含图像，但它与 images 目录不同，以便开发和生产服务器的同步不会影响上传的图像。 |

尽管强烈建议您保持默认的树形结构，但出于特定需求（例如，允许项目在具有不同树形结构规则和编码约定的服务器上运行），仍可对其进行修改。有关修改文件树形结构的更多信息，请参阅第 19 章。

## 常用机制

symfony 中反复使用的一些技术，你会在这本书和自己的项目中频繁遇到。这些包括参数容器、常量和类自动加载。

### 参数容器

许多 symfony 类包含一个参数容器。这是一种通过简洁的 getter 和 setter 方法封装属性的便捷方式。例如，sfRequest 类持有一个参数容器，您可以通过调用 getParameterHolder() 方法来获取它。每个参数容器以相同的方式存储数据，如清单 2-14 所示。

### 清单 2-14 - 使用 sfRequest 参数容器

```php
$request->getParameterHolder()->set('foo', 'bar');
echo $request->getParameterHolder()->get('foo');
=> 'bar'
```

大多数使用参数容器的类都提供代理方法，以缩短 get/set 操作所需的代码。sfRequest 对象也是如此，因此您可以使用清单 2-15 的代码，执行与清单 2-14 相同的操作。

### 清单 2-15 - 使用 sfRequest 参数容器代理方法

```php
$request->setParameter('foo', 'bar');
echo $request->getParameter('foo');
=> 'bar'
```

参数容器的 getter 接受第二个参数作为默认值。这提供了一种有用的回退机制，比使用条件语句要简洁得多。示例请参见清单 2-16。

### 清单 2-16 - 使用属性容器 getter 的默认值

```php
// The 'foobar' parameter is not defined, so the getter returns an empty value
echo $request->getParameter('foobar');
=> null
```

```php
// A default value can be used by putting the getter in a condition
if ($request->hasParameter('foobar'))
{
    echo $request->getParameter('foobar');
}
else
{
    echo 'default';
}
=> default
```

```php
// But it is much faster to use the second getter argument for that
echo $request->getParameter('foobar', 'default');
=> default
```

一些 symfony 核心类还使用支持命名空间的参数容器（归功于 sfNamespacedParameterHolder 类）。如果您向 setter 或 getter 指定第三个参数，它将被用作命名空间，且该参数将仅在该命名空间内定义。清单 2-17 显示了一个示例。

### 清单 2-17 - 使用 sfUser 参数容器命名空间

```php
$user->setAttribute('foo', 'bar1');
$user->setAttribute('foo', 'bar2', 'my/name/space');
echo $user->getAttribute('foo');
=> 'bar1'
echo $user->getAttribute('foo', null, 'my/name/space');
=> 'bar2'
```

当然，您可以将参数容器添加到自己的类中，以利用其语法便利性。清单 2-18 展示了如何定义带有参数容器的类。

### 清单 2-18 - 向类添加参数容器

```php
class MyClass
{
    protected $parameterHolder = null;

    public function initialize($parameters = array())
    {
        $this->parameterHolder = new sfParameterHolder();
        $this->parameterHolder->add($parameters);
    }

    public function getParameterHolder()
    {
        return $this->parameterHolder;
    }
}
```

### 常量

在 symfony 中您找不到任何常量，因为常量一经定义后，由于其本质就无法更改其值。Symfony 使用其自己的配置对象，即 sfConfig，它替代了常量。它提供静态方法，可从任何地方访问参数。清单 2-19 演示了 sfConfig 类方法的用法。

### 清单 2-19 - 使用 sfConfig 类方法而非常量

```php
// Instead of PHP constants,
define('FOO', 'bar');
echo FOO;

// symfony uses the sfConfig object
sfConfig::set('foo', 'bar');
echo sfConfig::get('foo');
```

sfConfig 方法支持默认值，您可以多次对同一参数调用 sfConfig::set() 方法来更改其值。第 5 章将更详细地讨论 sfConfig 方法。

### 类自动加载

通常，在 PHP 中使用类方法或创建对象时，首先需要包含类定义：

```php
include_once 'classes/MyClass.php';
$myObject = new MyClass();
```

在类文件众多且目录结构深层的大型项目中，跟踪所有需要包含的类文件及其路径可能非常耗时。通过提供 spl_autoload_register() 函数，symfony 使 include_once 语句变得多余，您可以直接编写：

```php
$myObject = new MyClass();
```

然后，Symfony 将在项目的 lib/ 目录中的所有以 class.php 结尾的文件中查找 MyClass 定义。如果找到类定义，它将自动包含。

因此，如果您将所有类都存储在 lib/ 目录中，就不再需要包含类了。这就是为什么 symfony 项目通常不包含任何 include_once 或 require_once 语句的原因。

为了获得更好的性能，symfony 自动加载器在第一次请求期间会扫描目录列表（在内部配置文件中定义）。然后它会注册这些目录中包含的所有类，并将类/文件对应关系作为关联数组存储在 PHP 文件中。这样，未来的请求就不再需要扫描目录了。这就是为什么您每次在项目中添加或移动类文件时，都需要通过调用 symfony cache:clear 命令来清除缓存（开发环境除外，symfony 在找不到类时会清除缓存）。您将在第 12 章了解更多关于缓存的内容，以及在第 19 章了解自动加载配置。

## 总结

使用 MVC 框架迫使您按照框架的约定划分和组织代码。表示代码放在视图中，数据操作代码放在模型中，请求操作逻辑放在控制器中。这使得应用 MVC 模式既非常有用，同时又相当受限。

Symfony 是一个用 PHP 编写的 MVC 框架。其结构旨在充分发挥 MVC 模式的优势，同时保持极高的易用性。得益于其通用性和可配置性，symfony 适用于所有 Web 应用程序项目。

现在您了解了 symfony 背后的基本理论，几乎可以开始开发您的第一个应用程序了。但在此之前，您需要在开发服务器上安装并运行 symfony。

# 第 3 章 运行 Symfony

正如您在前几章中所学，symfony 框架是一组用 PHP 编写的文件。symfony 项目使用这些文件，因此安装 symfony 意味着获取这些文件并使其可供项目使用。

Symfony 要求至少 PHP 5.2.4。请打开命令行并键入以下命令，确保已安装：

```bash
$ php -v

PHP 5.3.1 (cli) (built: Jan 6 2010 20:54:10)
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2009 Zend Technologies
```

如果版本号为 5.2.4 或更高，则您已准备好进行安装，如本章所述。

## 前提条件

在安装 symfony 之前，您需要检查计算机是否已正确安装和配置所有内容。请花时间认真阅读本章并遵循所有检查配置所需的步骤，这在日后可能会为您节省大量时间。

## 第三方软件

首先，您需要检查计算机是否拥有适合 Web 开发的友好工作环境。至少，您需要一个 Web 服务器（例如 Apache）、一个数据库引擎（MySQL、PostgreSQL、SQLite 或任何兼容 PDO17 的数据库引擎）以及 PHP 5.2.4 或更高版本。

## 命令行界面

symfony 框架自带一个命令行工具，可为您自动完成大量工作。如果您是类 Unix 操作系统的用户，会感到非常熟悉。如果您运行的是 Windows 系统，它也能正常工作，但您只需在 cmd 提示符下输入几个命令即可。





## PHP 配置

由于 PHP 配置在不同操作系统之间，甚至在不同 Linux 发行版之间可能差异很大，你需要检查你的 PHP 配置是否满足 symfony 的最低要求。

首先，使用 phpinfo() 内置函数或在命令行运行 php -v，确保已安装至少 PHP 5.2.4。请注意，在某些配置下，你可能安装了两个不同的 PHP 版本：一个用于命令行，另一个用于 Web。

然后，从以下 URL 下载 symfony 配置检查脚本：

```
Listing 3-2
http://sf-to.org/1.4/check.php
```

将脚本保存到当前 Web 根目录下的某个位置。

从命令行启动配置检查脚本：

```
Listing 3-3
$ php check_configuration.php
```

如果 PHP 配置有问题，命令的输出会给出修复什么以及如何修复的提示。

你还应该从浏览器执行检查器并修复它可能发现的问题。这是因为 PHP 对这两个环境可以有不同的独立 php.ini 配置文件，设置也不同。

之后别忘了从 Web 根目录中删除该文件。

如果你的目标是尝试 symfony 几个小时，可以按照本章末尾的描述安装 symfony 沙箱。如果你想引导一个真实世界项目，或想了解更多关于 symfony 的内容，请继续阅读。

## Symfony 安装

### 初始化项目目录

在安装 symfony 之前，你首先需要创建一个目录来存放与项目相关的所有文件：

```
Listing 3-4
$ mkdir -p /home/sfproject
$ cd /home/sfproject
```

或者在 Windows 上：

```
c:\> mkdir c:\dev\sfproject
c:\> cd c:\dev\sfproject
```

建议 Windows 用户在不包含空格的路径下运行 symfony 并设置新项目。避免使用“文档和设置”目录，包括“我的文档”下的任何位置。

如果你在 Web 根目录下创建 symfony 项目目录，则不需要配置 Web 服务器。当然，对于生产环境，我们强烈建议你按照 Web 服务器配置部分的说明配置 Web 服务器。

### 选择 Symfony 版本

现在，你需要安装 symfony。由于 symfony 框架有几个稳定版本，你需要通过阅读 symfony 网站上的安装页面20来选择要安装的版本。

### 选择 Symfony 安装位置

你可以在机器上全局安装 symfony，或者将其嵌入到每个项目中。后者是推荐的方法，因为项目之间将完全独立，升级本地安装的 symfony 不会意外地破坏某些项目。这也意味着你可以使用不同版本的 symfony 进行项目开发，并按需逐个升级。

作为最佳实践，许多人将 symfony 框架文件安装在 lib/vendor 项目目录中。因此，首先创建此目录：

```
$ mkdir -p lib/vendor
```

### 安装 Symfony

### 从存档安装

安装 symfony 的最简单方法是从 symfony 网站下载你选择的版本的存档。转到你刚刚选择的版本的安装页面，例如 symfony 1.421。

在“源码下载”部分，你将找到 .tgz 或 .zip 格式的存档。下载存档，将其放在新创建的 lib/vendor/ 目录下，解压缩，并将目录重命名为 symfony：

```
$ cd lib/vendor
$ tar zxpf symfony-1.4.0.tgz
$ mv symfony-1.4.0 symfony
$ rm symfony-1.4.0.tgz
```

在 Windows 上，可以使用资源管理器解压 zip 文件。将目录重命名为 symfony 后，应该会出现类似于 c:\dev\sfproject\lib\vendor\symfony 的目录结构。

20. http://www.symfony-project.org/installation
21. http://www.symfony-project.org/installation/1.4

### 从 Subversion 安装（推荐）

如果你的项目使用 Subversion，使用 svn:externals 属性将 symfony 嵌入到 lib/vendor/ 目录中的项目中会更好：

```
$ svn pe svn:externals lib/vendor/
```

如果一切顺利，此命令将运行你喜欢的编辑器，让你有机会配置外部 Subversion 来源。

> 在 Windows 上，你可以使用 TortoiseSVN22 等工具，无需使用控制台即可完成所有操作。

如果你比较保守，可以将项目绑定到特定版本（Subversion 标签）：

```
symfony http://svn.symfony-project.com/tags/RELEASE_1_4_0
```

每当有新版本发布（如 symfony 博客23所宣布），你都需要将 URL 更改为新版本。

如果你想走前沿路线，请使用 1.4 分支：

```
symfony http://svn.symfony-project.com/branches/1.4/
```

使用分支意味着，每次运行 svn update 时，你的项目都会自动获得错误修复。

### 安装验证

symfony 安装完成后，使用 symfony 命令行显示 symfony 版本来检查一切是否正常（注意大写 V）：

```
$ cd ../..
$ php lib/vendor/symfony/data/bin/symfony -V
```

在 Windows 上：

```
c:\> cd ../..
c:\> php lib\vendor\symfony\data\bin\symfony -V
```

创建项目后（见下文），运行此命令还会显示 symfony 安装目录的路径，该路径存储在 config/ProjectConfiguration.class.php 中。

如果检查时 symfony 的路径是绝对路径（默认情况下不应该是，如果你按照以下说明操作），请将其更改为如下形式，以便更具可移植性：

```
// config/ProjectConfiguration.class.php
require_once dirname(__FILE__).'./../lib/vendor/symfony/lib/autoload/sfCoreAutoload.class.php';
```

这样，你就可以将项目目录移动到机器上的任何位置或另一台机器，它都能正常工作。

22. http://tortoisesvn.net/
23. http://www.symfony-project.org/blog/

如果你对这个命令行工具能为你做什么感到好奇，请输入 symfony 以列出可用的选项和任务：

```
$ php lib/vendor/symfony/data/bin/symfony
```

在 Windows 上：

```
c:\> php lib\vendor\symfony\data\bin\symfony
```

symfony 命令行是开发者的好帮手。它提供了许多实用程序，可提高你在日常活动（如清除缓存、生成代码等）中的工作效率。

## 项目设置

在 symfony 中，共享相同数据模型的 **应用程序** 被分组到 **项目** 中。对于大多数项目，你会有两个不同的应用程序：前端和后端。

### 创建项目

从 sfproject/ 目录运行 symfony generate:project 任务以实际创建 symfony 项目：

```
$ php lib/vendor/symfony/data/bin/symfony generate:project PROJECT_NAME
```

在 Windows 上：

```
c:\> php lib\vendor\symfony\data\bin\symfony generate:project PROJECT_NAME
```

generate:project 任务生成 symfony 项目所需的默认目录和文件结构。

> 为什么 symfony 会生成这么多文件？使用全栈框架的主要好处之一是标准化你的开发。得益于 symfony 默认的文件和目录结构，任何具备一些 symfony 知识的开发者都可以接手任何 symfony 项目的维护工作。几分钟内，他就能深入代码，修复错误并添加新功能。

generate:project 任务还在项目根目录中创建了一个 symfony 快捷方式，以减少运行任务时需要输入的字符数。

因此，从现在开始，不再使用 symfony 程序的完全限定路径，而可以使用 symfony 快捷方式。

### 配置数据库

symfony 框架开箱即用支持所有 PDO24支持的数据库（MySQL、PostgreSQL、SQLite、Oracle、MSSQL 等）。在 PDO 之上，symfony 包含两个 ORM 工具：Propel 和 Doctrine。

创建新项目时，Doctrine 默认启用。配置 Doctrine 使用的数据库就像使用 configure:database 任务一样简单：

24. http://www.php.net/PDO





```
$ php symfony configure:database "mysql:host=localhost;dbname=dbname" root mYsEcret
```

The configure:database task takes three arguments: the PDO DSN<sup>25</sup>, the username, and the password to access the database. If you don't need a password to access your database on the development server, just omit the third argument.

> If you want to use Propel instead of Doctrine, add `--orm=Propel` when creating the project with the generate:project task. And if you don't want to use an ORM, just pass `--orm=none`.

## Application Creation

Now, create the frontend application by running the generate:app task:

```
$ php symfony generate:app frontend
```

> Because the symfony shortcut file is executable, Unix users can replace all occurrences of 'php symfony' by './symfony' from now on.
> On Windows you can copy the 'symfony.bat' file to your project and use 'symfony' instead of 'php symfony':

```
c:\> copy lib\vendor\symfony\data\bin\symfony.bat .
```

Based on the application name given as an argument, the generate:app task creates the default directory structure needed for the application under the apps/frontend/ directory.

## Security

By default, the generate:app task has secured our application from the two most widespread vulnerabilities found on the web. That's right, symfony automatically takes security measures on our behalf. To prevent XSS attacks, output escaping has been enabled; and to prevent CSRF attacks, a random CSRF secret has been generated.

Of course, you can tweak these settings thanks to the following options:

- --escaping-strategy: Enables or disables output escaping
- --csrf-secret: Enables session tokens in forms

If you know nothing about XSS<sup>26</sup> or CSRF<sup>27</sup>, take the time to learn more about these security vulnerabilities.

## Directory Structure Rights

Before trying to access your newly created project, you need to set the write permissions on the cache/ and log/ directories to the appropriate levels, so that both your web server and command line user can write to them:

- 25. http://www.php.net/manual/en/pdo.drivers.php
- 26. http://en.wikipedia.org/wiki/Cross-site_scripting
- 27. http://en.wikipedia.org/wiki/CSRF

```
$ symfony project:permissions
```

> ### Tips for People using an SCM Tool
> 
> symfony only ever writes to two directories of a symfony project, cache/ and log/. The content of these directories should be ignored by your SCM (by editing the svn:ignore property if you use Subversion for instance).

## Web Server Configuration

### The ugly Way

In the previous chapters, you have created a directory that hosts the project. If you have created it somewhere under the web root directory of your web server, you can already access the project in a web browser.

Of course, as there is no configuration, it is very fast to set up, but try to access the config/databases.yml file in your browser to understand the bad consequences of such a lazy attitude. If the user knows that your website is developed with symfony, he will have access to a lot of sensitive files.

**Never ever use this setup on a production server**, and read the next section to learn how to configure your web server properly.

### The secure Way

A good web practice is to only put the files that need to be accessed by a web browser under the web root directory, such as stylesheets, JavaScripts and images. By default, we recommend storing these files under the web/ sub-directory of a symfony project.

If you have a look at this directory, you will find some sub-directories for web assets (css/ and images/) and the two front controller files. The front controllers are the only PHP files that need to be under the web root directory. All other PHP files can be hidden from the browser, which is a good idea as far as security is concerned.

## Web Server Configuration

Now it is time to change your Apache configuration, to make the new project accessible to the world.

Locate and open the httpd.conf configuration file and add the following configuration at the end:

```
# Be sure to only have this line once in your configuration
NameVirtualHost 127.0.0.1:8080

# This is the configuration for your project
Listen 127.0.0.1:8080

<VirtualHost 127.0.0.1:8080>
    DocumentRoot "/home/sfproject/web"
    DirectoryIndex index.php
    <Directory "/home/sfproject/web">
        AllowOverride All
        Allow from All
</Directory>
Alias /sf /home/sfproject/lib/vendor/symfony/data/web/sf
<Directory "/home/sfproject/lib/vendor/symfony/data/web/sf">
AllowOverride All
Allow from All
</Directory>
</VirtualHost>
```

The /sf alias gives you access to images and javascript files needed to properly display default symfony pages and the web debug toolbar.
On Windows, you need to replace the Alias line with something like:

```
Alias /sf "c:\dev\sfproject\lib\vendor\symfony\data\web\sf"
```

And /home/sfproject/web should be replaced with:

```
c:\dev\sfproject\web
```

This configuration makes Apache listen to port 8080 on your machine, so the website will be accessible at the following URL:

```
http://localhost:8080/
```

You can change 8080 to any number, but favour numbers greater than 1024 as they do not require administrator rights.

## Configure a dedicated Domain Name

If you are an administrator on your machine, it is better to setup virtual hosts instead of adding a new port each time you start a new project. Instead of choosing a port and adding a Listen statement, choose a domain name (for instance the real domain name with .localhost added at the end) and add a ServerName statement:

```
# This is the configuration for your project
<VirtualHost 127.0.0.1:80>
ServerName www.myproject.com.localhost
<!--- same configuration as before --->
</VirtualHost>
```

The domain name www.myproject.com.localhost used in the Apache configuration has to be declared locally. If you run a Linux system, it has to be done in the /etc/hosts file. If you run Windows XP, Vista or Win7, this file is located in the C:\WINDOWS\system32\drivers\etc\ directory.

Add the following line:

```
127.0.0.1 www.myproject.com.localhost
```

## Test the New Configuration

Restart Apache, and check that you now have access to the new application by opening a browser and typing http://localhost:8080/index.php/, or http://www.myproject.com.localhost/index.php/ depending on the Apache configuration you chose in the previous section.

![](img/0f886a7f4cbcc3939be96e985ca35ff4_44_0.png)

If you have the Apache mod_rewrite module installed, you can remove the index.php/ part of the URL. This is possible thanks to the rewriting rules configured in the web/.htaccess file.

You should also try to access the application in the development environment (see the next section for more information about environments). Type in the following URL:

```
http://www.myproject.com.localhost/frontend_dev.php/
```

The web debug toolbar should show in the top right corner, including small icons proving that your sf/ alias configuration is correct.

![](img/0f886a7f4cbcc3939be96e985ca35ff4_45_0.png)

The setup is a little different if you want to run symfony on an IIS server in a Windows environment. Find how to configure it in the related tutorial 28.

## Using the Sandbox

If your goal is to give symfony a try for a few hours, keep reading this chapter as we will show you the fastest way to get you started.

The fastest way to experiment with symfony is to install the symfony sandbox. The sandbox is a dead-easy-to-install pre-packaged symfony project, already configured with some sensible defaults. It is a great way to practice using symfony without the hassle of a proper installation that respects the web best practices.

> As the sandbox is pre-configured to use SQLite as a database engine, you need to check that your PHP supports SQLite. You can also read the Configuring the Database section to learn how to change the database used by the sandbox.

You can download the symfony sandbox in .tgz or .zip format from the symfony installation page 29 or at the following URLs:

```
http://www.symfony-project.org/get/sf_sandbox_1_4.tgz
http://www.symfony-project.org/get/sf_sandbox_1_4.zip
```

Un-archive the files somewhere under your web root directory, and you are done. Your symfony project is now accessible by requesting the web/index.php script from a browser.





将所有 symfony 文件放在 web 根目录下，在本地计算机上测试 symfony 没问题，但对于生产服务器来说是个非常糟糕的主意，因为这可能会让最终用户看到应用程序的所有内部细节。

你现在可以通过阅读 Web 服务器配置部分来完成安装。

沙箱本质上只是一个为你执行了一些任务并更改了一些配置的普通 symfony 项目，因此将其用作新项目的起点非常容易。不过请记住，你可能需要调整配置；例如更改与安全相关的设置（参见本章中 XSS 和 CSRF 的配置）。

## 摘要

在本地服务器上测试和尝试 symfony，安装的最佳选择无疑是沙箱，它包含一个预配置的 symfony 环境。

对于真正的开发或生产服务器，请选择存档安装或 SVN 检出。这将安装 symfony 库，你仍然需要初始化一个项目和一个应用程序。应用程序设置的最后一步是服务器配置，这可以通过多种方式完成。Symfony 与虚拟主机配合使用非常完美，也是推荐的解决方案。

如果在安装过程中遇到任何问题，可以在 symfony 网站上找到许多教程和常见问题解答。如果需要，可以将问题提交给 symfony 社区，你将得到快速且有效的回答。

项目初始化后，启动版本控制流程是一个好习惯。

既然你已经准备好使用 symfony，是时候学习如何构建基本的 Web 应用程序了。

# 第 4 章 页面创建基础

出人意料的是，程序员学习新语言或新框架时跟随的第一个教程，通常是那个在屏幕上显示“Hello, world！”的教程。把电脑当作能够向全世界问候的东西，这听起来很奇怪，因为人工智能领域的每一次尝试到目前为止都导致了糟糕的对话能力。但 symfony 不比其他任何程序更笨，证明就是，你可以用它创建一个显示“Hello, <你的名字>”的页面。

## 创建模块骨架

如第 2 章所述，symfony 将页面分组为模块。在创建页面之前，你需要创建一个模块，它最初是一个带有 symfony 能识别的文件结构的空壳。

symfony 命令行自动化了模块的创建。你只需要以应用程序名称和模块名称作为参数调用 generate:module 任务。在上一章中，你创建了一个 frontend 应用程序。要向此应用程序添加一个 content 模块，请键入以下命令：

```
Listing 4-1
$ cd ~/myproject
$ php symfony generate:module frontend content

>> dir+  ~/myproject/apps/frontend/modules/content/actions
>> file+  ~/myproject/apps/frontend/modules/content/actions/
actions.class.php
>> dir+  ~/myproject/apps/frontend/modules/content/templates
>> file+  ~/myproject/apps/frontend/modules/content/templates/
indexSuccess.php
>> file+  ~/myproject/test/functional/frontend/contentActionsTest.php
>> tokens  ~/myproject/test/functional/frontend/contentActionsTest.php
>> tokens  ~/myproject/apps/frontend/modules/content/actions/
actions.class.php
>> tokens  ~/myproject/apps/frontend/modules/content/templates/
indexSuccess.php
```

除了 actions/ 和 templates/ 目录外，此命令仅创建了三个文件。test/ 文件夹中的文件涉及功能测试，直到第 15 章之前你都不需要关心它。actions.class.php（如清单 4-1 所示）会转发到默认模块的 congratulation 页面。templates/indexSuccess.php 文件为空。

### 清单 4-1 - 默认生成的动作，位于 actions/actions.class.php

```php
<?php
class contentActions extends sfActions
{
    public function executeIndex()
    {
        $this->forward('default', 'module');
    }
}
```

如果你查看实际的 actions.class.php 文件，会发现不止这几行，还包含大量注释。这是因为 symfony 建议使用 PHP 注释来记录你的项目，并使每个类文件与 phpDocumentor 工具兼容。

对于每个新模块，symfony 都会创建一个默认的 index 动作。它由名为 executeIndex 的动作方法和名为 indexSuccess.php 的模板文件组成。execute 前缀和 Success 后缀的含义将分别在第 6 章和第 7 章中解释。在此之前，你可以将此命名视为一种约定。你可以通过访问以下 URL 查看相应的页面（如图 4-1 所示）：

http://localhost/frontend_dev.php/content/index

本章不会使用默认的 index 动作，因此你可以从 actions.class.php 文件中删除 executeIndex() 方法，并从 templates/ 目录中删除 indexSuccess.php 文件。

Symfony 提供了除命令行之外的其他方式来初始化模块。其中一种方法是自己创建目录和文件。在许多情况下，模块的动作和模板旨在操作给定表的数据。由于创建、检索、更新和删除表中记录所需的代码通常相同，symfony 提供了一种机制为你生成此代码。

### 图 4-1 - 默认生成的索引页面

![](img/0f886a7f4cbcc3939be96e985ca35ff4_49_0.png)

## 添加页面

在 symfony 中，页面背后的逻辑存储在动作中，表现层在模板中。没有逻辑的页面（仍然）需要一个空动作。

### 添加动作

“Hello, world！”页面将通过 show 动作访问。要创建它，只需向 contentActions 类添加一个 executeShow 方法，如清单 4-2 所示。

*清单 4-2 - 添加动作就像向动作类添加一个 Execute 方法*

```php
<?php
class contentActions extends sfActions
{
  public function executeShow()
  {
  }
}
```

动作方法的名称始终是 executeXxx()，其中名称的第二部分是首字母大写的动作名称。

现在，如果你请求以下 URL：

```
http://localhost/frontend_dev.php/content/show
```

symfony 会抱怨缺少 showSuccess.php 模板。这很正常；在 symfony 中，页面始终由动作和模板组成。

>> URL（不包括域名）区分大小写，symfony 也是如此（尽管 PHP 中的方法名不区分大小写）。这意味着如果你在浏览器中调用 sHow，symfony 会返回 404 错误。

### URL 是响应的一部分

Symfony 包含一个路由系统，允许你在实际动作名称和调用它所需的 URL 形式之间实现完全分离。这允许对 URL 进行自定义格式化，就好像它是响应的一部分。你不再受限于文件结构或请求参数；动作的 URL 可以看起来像你想要的短语。例如，调用名为 article 的模块的 index 动作通常如下所示：

```
http://localhost/frontend_dev.php/article/index?id=123
```

此 URL 从数据库中检索给定文章。在此示例中，它检索 Europe 部分中专门讨论法国金融的一篇文章（id=123）。但 URL 可以通过对 routing.yml 配置文件进行简单更改，以完全不同的方式编写：

```
http://localhost/articles/europe/france/finance.html
```

生成的 URL 不仅对搜索引擎友好，对用户也很有意义，用户可以将地址栏作为伪命令行来执行自定义查询，如下所示：

```
http://localhost/articles/tagged/finance+france+euro
```

Symfony 知道如何为用户解析和生成智能 URL。路由系统会自动从智能 URL 中剥离请求参数并使其可用于动作。它还格式化响应中包含的超链接，使其看起来“智能”。你将在第 9 章中了解更多有关此功能的信息。

总的来说，这意味着动作的命名不应受调用其 URL 形式的影响，而应受动作在应用程序中功能的影响。动作名称解释了动作实际做什么，通常是动词原形（如 show、list、edit 等）。动作名称可以对最终用户完全不可见，因此请不要犹豫，使用明确的动作名称（如 listByName 或 showWithComments）。你将节省解释动作功能的代码注释，而且代码也会更易于阅读。

### 添加模板

动作期望一个模板来呈现自身。模板是模块 templates/ 目录中的一个文件，由动作和动作终止符命名。默认动作终止符是“success”，因此 show 动作要创建的模板文件应命名为 showSuccess.php。

模板应该只包含表现层代码，因此在其中尽可能少地使用 PHP 代码。事实上，显示“Hello, world！”的页面可以有一个像清单 4-3 中那样简单的模板。

### 清单 4-3 - content/templates/showSuccess.php 模板

```php
<p>Hello, world!</p>
```

如果你需要在模板中执行一些 PHP 代码，应该避免使用通常的 PHP 语法，如清单 4-4 所示。相反，应使用 PHP 替代语法编写模板，如清单 4-5 所示，以便非 PHP 程序员也能理解代码。最终代码不仅会正确缩进，还能帮助你将复杂的 PHP 代码保留在动作中，因为只有控制语句（if、foreach、while 等）才有替代语法。




## 清单 4-4 - 常用 PHP 语法，适用于操作，但不适用于模板

```php
<p>Hello, world!</p>
<?php
if ($test)
{
echo "<p>".time()."</p>";
}
?>
```

## 清单 4-5 - 备选 PHP 语法，适用于模板

```php
<p>Hello, world!</p>
<?php if ($test): ?>
<p><?php echo time(); ?></p>
<?php endif; ?>
```

> 一个检查模板语法是否足够易读的经验法则是：文件不应包含 PHP 输出的 HTML 代码或花括号。而且大多数时候，当打开 <?php 时，你会在同一行用 ?> 将其关闭。

## 将信息从操作传递到模板

操作的工作是完成所有复杂的计算、数据检索和测试，并为模板设置要输出或测试的变量。Symfony 使操作类的属性（在操作中通过 $this->variableName 访问）在全局命名空间中直接对模板可用（通过 $variableName）。清单 4-6 和 4-7 展示了如何将信息从操作传递到模板。

## 清单 4-6 - 在操作中设置操作属性以使其对模板可用

```php
<?php
class contentActions extends sfActions
{
public function executeShow()
{
$today = getdate();
$this->hour = $today['hours'];
}
}
```

## 清单 4-7 - 模板可以直接访问操作属性

```php
<p>Hello, world!</p>
<?php if ($hour >= 18): ?>
<p>Or should I say good evening? It is already <?php echo $hour ?>.</p>
<?php endif; ?>
```

请注意，不建议在专业 Web 应用程序中使用短开标签（<?=，等同于 <?php echo），因为您的生产 Web 服务器可能能够理解多种脚本语言，从而产生混淆。此外，短开标签在默认 PHP 配置下无法工作，需要服务器调整才能启用。归根结底，当您需要处理 XML 和验证时，它会力不从心，因为 <? 在 XML 中具有特殊含义。

> 模板已经可以访问一些数据，而无需在操作中设置任何变量。每个模板都可以调用 $sf_request、$sf_params、$sf_response 和 $sf_user 对象的方法。它们分别包含与当前请求、请求参数、响应和会话相关的数据。您很快就会学会如何高效地使用它们。

## 链接到另一个操作

您已经知道，操作名称与用于调用它的 URL 之间是完全解耦的。因此，如果您在模板中创建指向 update 的链接，如清单 4-8 所示，它只能与默认路由一起使用。如果您以后决定更改 URL 的外观，那么您将需要检查所有模板以更改超链接。

## 清单 4-8 - 超链接，经典方式

```html
<a href="/frontend_dev.php/content/update?name=anonymous">
I never say my name
</a>
```

为避免此麻烦，您应始终使用 link_to() 辅助函数来创建指向应用程序操作的超链接。如果您只想生成 URL 部分，则 url_for() 是您要找的辅助函数。

辅助函数是由 symfony 定义的 PHP 函数，旨在在模板中使用。它输出一些 HTML 代码，比您亲自编写实际 HTML 代码更快。清单 4-9 演示了超链接辅助函数的用法。

## 清单 4-9 - link_to() 和 url_for() 辅助函数

```php
<p>Hello, world!</p>
<?php if ($hour >= 18): ?>
<p>Or should I say good evening? It is already <?php echo $hour ?>.</p>
<?php endif; ?>
<form method="post" action="<?php echo url_for('content/update') ?>">
<label for="name">What is your name?</label>
<input type="text" name="name" id="name" value="" />
<input type="submit" value="Ok" />
<?php echo link_to('I never say my name', 'content/update?name=anonymous') ?>
</form>
```

生成的 HTML 将与之前相同，只是当您更改路由规则时，所有模板都将正确运行并相应地重新格式化 URL。

表单处理值得单独成章，因为 symfony 提供了许多工具使其变得更加容易。您将在第 10 章中了解更多有关这些辅助函数的信息。

link_to() 辅助函数与许多其他辅助函数一样，接受另一个参数用于特殊选项和其他标签属性。清单 4-10 显示了选项参数的示例及其生成的 HTML。选项参数要么是关联数组，要么是简单字符串，显示用空格分隔的键值对。

## 清单 4-10 - 大多数辅助函数接受选项参数

```php
// Option argument as an associative array
<?php echo link_to('I never say my name', 'content/update?name=anonymous',
array(
    'class' => 'special_link',
    'confirm' => 'Are you sure?',
    'absolute' => true
)) ?>

// Option argument as a string
<?php echo link_to('I never say my name', 'content/update?name=anonymous',
    'class=special_link confirm=Are you sure? absolute=true') ?>

// Both calls output the same
=> <a class="special_link" onclick="return confirm('Are you sure?');"
    href="http://localhost/frontend_dev.php/content/update/name/anonymous">
    I never say my name</a>
```

每当您使用输出 HTML 标签的 symfony 辅助函数时，都可以在选项参数中插入其他标签属性（例如清单 4-10 示例中的 class 属性）。您甚至可以以“快而脏”的 HTML 4.0 方式（不带双引号）编写这些属性，symfony 会将它们输出为格式良好的 XHTML。这就是辅助函数比编写 HTML 更快的另一个原因。

由于需要额外的解析和转换，字符串语法比数组语法稍慢一些。

与所有 symfony 辅助函数一样，链接辅助函数数量众多且选项很多。第 9 章将详细描述它们。

### 从请求获取信息

无论用户是通过表单（通常是 POST 请求）还是通过 URL（GET 请求）发送信息，您都可以使用 sfRequest 对象的 getParameter() 方法从操作中检索相关数据。清单 4-11 演示了如何在 update 中检索 name 参数的值。

## 清单 4-11 - 在操作中从请求参数获取数据

```php
<?php
class contentActions extends sfActions
{
    // ...

    public function executeUpdate($request)
    {
        $this->name = $request->getParameter('name');
    }
}
```

为方便起见，所有 executeXxx() 方法都将当前 sfRequest 对象作为其第一个参数。

如果数据处理很简单，您甚至不需要使用操作来检索请求参数。模板可以访问一个名为 $sf_params 的对象，它提供了一个 get() 方法来检索请求参数，就像操作中的 getParameter() 一样。

如果 executeUpdate() 为空，清单 4-12 展示了 updateSuccess.php 模板如何检索相同的 name 参数。

## 清单 4-12 - 在模板中直接从请求参数获取数据

```php
<p>Hello, <?php echo $sf_params->get('name') ?>!</p>
```

> 为什么不直接使用 $_POST、$_GET 或 $_REQUEST 变量呢？因为那样的话，您的 URL 格式将有所不同（例如 http://localhost/articles/europe/france/finance.html，不包含 ? 或 =），通常的 PHP 变量将不再起作用，只有路由系统才能检索请求参数。而且，您可能希望添加输入过滤以防止恶意代码注入，而这只有在将所有请求参数保存在一个整洁的参数容器中时才有可能实现。

$sf_params 对象的功能比仅提供等效于数组的 getter 要强大。例如，如果您只想测试请求参数是否存在，可以简单地使用 $sf_params->has() 方法，而不是使用 get() 测试实际值，如清单 4-13 所示。

## 清单 4-13 - 在模板中测试请求参数是否存在

```php
<?php if ($sf_params->has('name')): ?>
<p>Hello, <?php echo $sf_params->get('name') ?>!</p>
<?php else: ?>
<p>Hello, John Doe!</p>
<?php endif; ?>
```

您可能已经猜到，这可以写成一行。与 symfony 中大多数 getter 方法一样，操作中的 $request->getParameter() 方法和模板中的 $sf_params->get() 方法（实际上，它们调用同一对象上的同一方法）都接受第二个参数：如果请求参数不存在时要使用的默认值。

```php
<p>Hello, <?php echo $sf_params->get('name', 'John Doe') ?>!</p>
```

## 总结

在 symfony 中，页面由操作（actions/actions.class.php 文件中以 execute 开头的方法）和模板（templates/ 目录中的文件，通常以 Success.php 结尾）组成。它们根据其在应用程序中的功能分组到模块中。编写模板由辅助函数辅助，辅助函数是由 symfony 提供的返回 HTML 代码的函数。您还需要将 URL 视为响应的一部分，可以根据需要进行格式化，因此应避免在操作命名或请求参数检索中直接引用 URL。

一旦了解这些基本原则，您就可以使用 symfony 编写完整的 Web 应用程序。但这会花费您太多时间，因为在应用程序开发过程中，您几乎需要完成的每项任务，都会以某种方式得到某个 symfony 功能的辅助……这就是本书不会在此停止的原因。




# 第 5 章 配置 Symfony

为了简单易用，Symfony 定义了一些约定，这些约定应能满足标准应用的最常见需求，无需修改。然而，通过一组简单而强大的配置文件，可以自定义框架与您的应用交互的几乎所有方面。使用这些文件，您还可以为应用添加特定参数。

本章将解释配置系统的工作原理：

- Symfony 的配置保存在用 YAML 编写的文件中，不过您始终可以选择其他格式。

- 配置文件位于项目目录结构的项目、应用和模块层级中。

- 您可以定义多组配置设置；在 Symfony 中，一组配置称为一个环境。

- 配置文件中定义的值可从应用的 PHP 代码中获取。

- 此外，Symfony 允许在 YAML 文件中使用 PHP 代码以及其他技巧，以使配置系统更加灵活。

## 配置系统

无论用途如何，大多数 Web 应用都共享一组共同特征。例如，某些部分可能仅限部分用户访问，或者页面可以使用布局进行装饰，或者表单可以在验证失败后填充用户输入。框架定义了模拟这些特征的结构，开发者可以通过更改配置设置进一步调整它们。这种策略节省了大量开发时间，因为许多更改不需要编写一行代码，即使背后有大量代码。它也更高效，因为它确保此类信息可以维护在单个且易于识别的位置。

然而，这种方法有两个严重缺点：

- 开发人员最终会编写无限复杂的 XML 文件。

- 在 PHP 架构中，每个请求的处理时间要长得多。

考虑到这些缺点，Symfony 仅在配置文件最擅长的方面使用它们。事实上，Symfony 配置系统的雄心是：

- 功能强大：几乎所有可以使用配置文件管理的方面都使用配置文件进行管理。

- 简单：许多配置方面在普通应用中不显示，因为它们很少需要更改。

- 易用：配置文件易于读取、修改和由开发者创建。

- 可定制：默认配置语言是 YAML，但也可以是 INI、XML 或开发者偏好的任何格式。

- 快速：配置文件从不由应用处理，而是由配置系统处理，它将它们编译为 PHP 服务器快速处理的代码块。

## YAML 语法和 Symfony 约定

为其配置，Symfony 默认使用 YAML 格式，而非更传统的 INI 或 XML 格式。YAML 通过缩进显示结构，编写速度快。其优势和基本规则已在第 1 章中描述。但是，在编写 YAML 文件时，您需要牢记一些约定。本节介绍几项最突出的约定。要完整阐述该主题，请阅读参考指南书中的专用章节31。

31. http://www.symfony-project.org/reference/1_4/en/02-YAML

首先，切勿在 YAML 文件中使用制表符；请改用空格。YAML 解析器无法理解带有制表符的文件，因此请使用空格缩进您的行（双空格是 Symfony 缩进的惯例），如清单 5-1 所示。

### 清单 5-1 - YAML 文件禁止使用制表符

```
# Never use tabs
all:
	mail:
		webmaster:  webmaster@example.com

# Use blanks instead
all:
  mail:
    webmaster:  webmaster@example.com
```

如果您的参数是以空格开头或结尾的字符串，包含特殊字符（例如“井号”（#）或逗号），或“true、false”等关键字（其中字符串为预期内容），则必须将值用单引号括起来，如清单 5-2 所示。

### 清单 5-2 - 非标准字符串应用单引号括起来

```
error1:  This field is compulsory
error2:  ' This field is compulsory '
error3:  'Don''t leave this field blank'  # Single quotes must be doubled
error4:  'Enter a # symbol to define an extension number'
i18n:    'false' # if we left off the quotes here, a boolean false would be returned
```

您可以使用特殊字符串标头（> 和 |）加上额外缩进来定义多行长字符串以及多行字符串。清单 5-3 演示了此约定。

### 清单 5-3 - 定义长字符串和多行字符串

```
# Folded style, introduced by >
# Each line break is folded to a space
# Makes YAML more readable
accomplishment: >
  Mark set a major league
  home run record in 1998.

# Literal style, introduced by |
# All line breaks count
# Indentation doesn't appear in the resulting string
stats: |
  65 Home Runs
  0.278 Batting Average
```

要将值定义为数组，请将元素括在方括号中或使用带破折号的扩展语法，如清单 5-4 所示。

### 清单 5-4 - YAML 数组语法

```
# Shorthand syntax for arrays
players: [ Mark McGwire, Sammy Sosa, Ken Griffey ]

# Expanded syntax for arrays
players:
  - Mark McGwire
  - Sammy Sosa
  - Ken Griffey
```

要将值定义为关联数组（或哈希），请将元素括在花括号中，并在键:值对的键和值之间始终插入空格，任何列表项之间用逗号分隔。您也可以通过为每个新键添加缩进和回车来使用扩展语法，如清单 5-5 所示。

### 清单 5-5 - YAML 关联数组语法

```
# Incorrect syntax, blanks are missing after the colons and comma
mail: {webmaster:webmaster@example.com,contact:contact@example.com}

# Correct shorthand syntax for associative arrays
mail: { webmaster: webmaster@example.com, contact: contact@example.com }

# Expanded syntax for associative arrays
mail:
  webmaster: webmaster@example.com
  contact: contact@example.com
```

要指定布尔值，可以使用 false 和 true 值，前提是它们不被引号括起来。

### 清单 5-6 - YAML 布尔值语法

```
true_value:  true
false_value: false
```

不要犹豫，添加注释（以井号 # 开头）和额外空格到值中，以使您的 YAML 文件更易读，如清单 5-7 所示。

### 清单 5-7 - YAML 注释语法和值对齐

```
# This is a comment line
mail:
  webmaster:  webmaster@example.com
  contact:   contact@example.com
admin:  admin@example.com  # extra spaces allow nice alignment of values
```

在某些 Symfony 配置文件中，您有时会看到以井号开头（因此被 YAML 解析器忽略）但看起来像通常设置行的行。这是 Symfony 的惯例：继承自 Symfony 核心中其他 YAML 文件的默认配置，会以注释行重复在您的应用程序配置中，供您参考。如果要更改此类参数的值，需要先取消注释该行，如清单 5-8 所示。

### 清单 5-8 - 默认配置以注释形式显示

```
# The cache is off by default
settings:
# cache: false

# If you want to change this setting, uncomment the line first
settings:
  cache: true
```

Symfony 有时会将参数定义分组到类别中。给定类别的所有设置都以缩进形式出现在类别标题下方。通过将长键:值对列表分组到类别中来构建结构，可以提高配置的可读性。类别标题以点 (.) 开头。清单 5-9 显示了类别示例。

### 清单 5-9 - 类别标题看起来像键，但以点开头

```
all:
  .general:
    tax: 19.6

mail:
  webmaster: webmaster@example.com
```

在此示例中，mail 是键，而 general 只是类别标题。一切工作如同类别标题不存在一样，如清单 5-10 所示。tax 参数实际上是 all 键的直接子项。但是，使用类别有助于 Symfony 处理 all 键下的数组。

### 清单 5-10 - 类别标题仅用于可读性，实际被忽略

```
all:
  tax: 19.6

mail:
  webmaster: webmaster@example.com
```





## 如果你不喜欢 YAML

YAML 只是一个用于定义 PHP 代码所用设置的接口，因此 YAML 文件中定义的配置最终会被转换为 PHP。浏览完一个应用程序后，检查其缓存的配置（例如，在 cache/frontend/dev/config/ 中）。你将看到与你的 YAML 配置对应的 PHP 文件。你将在本章后面了解更多关于配置缓存的内容。

好消息是，如果你不想使用 YAML 文件，仍然可以手动（使用 PHP 或通过其他格式，如 XML、INI 等）完成配置文件所做的事情。在本书中，你将遇到不使用 YAML 来定义配置的替代方法，甚至会学习如何替换 symfony 配置处理器（在第 19 章）。如果明智地使用这些技巧，它们将使你能够绕过配置文件或定义自己的配置格式。

## 救命，YAML 文件导致我的应用程序崩溃了！

YAML 文件会被解析为 PHP 哈希和数组，然后这些值在应用程序的各个部分中用于修改视图、控制器或模型的行为。很多时候，当 YAML 文件中存在问题时，直到实际需要使用该值时才会被发现。此外，此时抛出的错误或异常通常与 YAML 配置文件没有明显的关联。

如果你的应用程序在配置更改后突然停止工作，你应该检查自己是否犯了粗心的 YAML 编码人员常见的任何错误：

- 你在键和值之间漏掉了空格：

```
Listing 5-11
key1:value1   # A space is missing after the :
```

- 序列中的键缩进方式不一致：

```
Listing 5-12
all:
  key1: value1
  key2: value2   # Indentation is not the same as the other
sequence members
  key3: value3
```

- 键或值中包含保留的 YAML 字符，且没有字符串分隔符：

```
Listing 5-13
message: tell him: go way   # : , [ , ], { and } are reserved in YAML
message: 'tell him: go way'   # Correct syntax
```

- 你正在修改一行注释：

```
Listing 5-14
# key: value   # Will never be taken into account due to the
leading #
```

- 你在同一层级中两次设置了同名键的值：

```
Listing 5-15
key1: value1
key2: value2
key1: value3   # key1 is defined twice, the value is the last
one defined
```

- 你认为该设置采用特殊类型，但实际上它始终是字符串，直到你将其转换为止：

```
income: 12,345  # Until you convert it, this is still a string
```

## 配置文件概览

配置按主题分布在不同的文件中。这些文件包含参数定义或设置。其中一些参数可以在多个层级（项目、应用程序和模块）中被覆盖；有些则特定于某个层级。接下来的章节将讨论与其主题相关的配置文件，第 19 章将讨论高级配置。

## 项目配置

默认情况下有几个项目配置文件。以下是可在 myproject/config/ 目录中找到的文件：

- ProjectConfiguration.class.php：这是任何请求或命令包含的第一个文件。它包含框架文件的路径，你可以更改它以使用不同的安装。有关此文件的高级用法，请参见第 19 章。
- databases.yml：这是你定义数据库访问和连接设置（主机、登录名、密码、数据库名称等）的地方。第 8 章将告诉你更多相关信息。它也可以在应用程序级别被覆盖。
- properties.ini：此文件保存命令行工具使用的一些参数，包括项目名称和远程服务器的连接设置。有关使用此文件的功能概览，请参见第 16 章。
- rsync_exclude.txt, rsync_include.txt：此文件指定在服务器间同步时必须排除和/或包含的目录和文件。在第 16 章中讨论。
- schema.yml：这是 Propel 和 Doctrine（symfony 的 ORM 层）使用的数据访问配置文件。它用于使 ORM 库能够与 symfony 类和你的项目数据协同工作。schema.yml 包含项目关系数据模型的表示。对于 Doctrine，此文件在 config/doctrine/ 中创建。

这些文件主要由外部组件或命令行使用，或者在框架加载任何 YAML 解析程序之前就需要被处理。这就是为什么其中一些文件不使用 YAML 格式的原因。

## 应用程序配置

配置的主要部分是应用程序配置。它在前端控制器（web/ 目录中）中为主配置定义，在应用程序 config/ 目录中的 YAML 文件中定义，在 i18n/ 目录中为国际化文件定义，并在框架文件中为不可见——虽然有用——的附加应用程序配置定义。

## 前端控制器配置

实际上，最初的应用程序配置位于前端控制器中，即请求执行的第一个脚本。请查看清单 5-11 中的默认 web/index.php。

_清单 5-11 - 默认生产前端控制器_

清单 5-17

```php
<?php
require_once(dirname(__FILE__).'/../config/ProjectConfiguration.class.php');

$configuration = ProjectConfiguration::getApplicationConfiguration('frontend', 'prod', false);
sfContext::createInstance($configuration)->dispatch();
```

在定义应用程序名称（frontend）、环境（prod）和调试模式（false）后，在创建上下文和分发之前会调用应用程序配置。因此，应用程序配置类中提供了一些有用的方法：

- $configuration->getRootDir()：项目根目录（通常，应保持其默认值，除非你更改文件结构）。
- $configuration->getApplication()：项目中的应用程序名称。计算文件路径所必需。
- $configuration->getEnvironment()：环境名称（prod、dev、test 或你定义的任何其他特定于项目的环境）。将确定使用哪些配置设置。环境将在本章后面解释。
- $configuration->isDebug()：启用调试模式（详情请参见第 16 章）。

如果你想更改其中任何一个值，可能需要一个额外的前端控制器。下一章将告诉你更多关于前端控制器以及如何创建新控制器的信息。

## 主应用程序配置

主应用程序配置存储在 myproject/apps/frontend/config/ 目录中的文件中：

- app.yml：此文件应包含特定于应用程序的配置；也就是说，定义特定于应用程序的业务或应用逻辑的全局变量，这些变量无需存储在数据库中。税率、运费和电子邮件地址通常存储在此文件中。默认情况下为空。
- frontendConfiguration.class.php：此类引导应用程序，这意味着它执行所有非常基本的初始化以允许应用程序启动。你可以在这里自定义目录结构或添加特定于应用程序的常数（第 19 章提供更多详细信息）。它继承自 sfApplicationConfiguration 类。
- factories.yml：Symfony 定义了自己的类来处理视图、请求、响应、会话等。如果你想使用自己的类，可以在此处指定。第 17 章提供更多信息。
- filters.yml：过滤器是为每个请求执行的代码部分。此文件用于定义要处理哪些过滤器，并且可以针对每个模块进行覆盖。第 6 章更详细地讨论了过滤器。
- routing.yml：路由规则存储在此文件中，这些规则允许将不可读和不可加书签的 URL 转换为“智能”和明确的 URL。对于新应用程序，存在一些默认规则。第 9 章完全关于链接和路由。
- settings.yml：symfony 应用程序的主设置在此文件中定义。你可以在此处指定应用程序是否具有国际化、默认语言、请求超时以及是否启用缓存。通过在此文件中进行一行更改，你可以关闭应用程序以执行维护或升级其组件之一。常见设置及其用途在第 19 章中有描述。





- view.yml: 默认视图的结构（布局名称、要包含的默认样式表和 JavaScript 文件、默认内容类型等）在此文件中设置。第 7 章将详细介绍此文件。这些设置可以为每个模块覆盖。

> symfony 参考书32中详细介绍了所有 symfony 配置文件。

## Internationalization Configuration

国际化应用程序可以以多种语言显示页面。这需要特定的配置。国际化有两个配置位置：

- The factories.yml of the application config/ directory: This file defines the i18n factory and general translation options, such as the default culture for the translation, whether the translations come from files or a database, and their format.

- 应用程序 config/ 目录中的 factories.yml：此文件定义 i18n 工厂和常规翻译选项，例如翻译的默认区域设置、翻译是来自文件还是数据库，以及其格式。

- Translation files in the application i18n/ directory: These are basically dictionaries, giving a translation for each of the phrases used in the application templates so that the pages show translated text when the user switches language.

- 应用程序 i18n/ 目录中的翻译文件：这些本质上是字典，为应用程序模板中使用的每个短语提供翻译，以便当用户切换语言时页面显示翻译后的文本。

Note that the activation of the i18n features is set in the settings.yml file. You will find more information about these features in Chapter 13.

请注意，i18n 功能的激活在 settings.yml 文件中设置。您将在第 13 章中找到有关这些功能的更多信息。

## Additional Application Configuration

A second set of configuration files is in the symfony installation directory (in sfConfig::get('sf_symfony_lib_dir')/config/config/) and doesn't appear in the configuration directory of your applications. The settings defined there are defaults that seldom need to be modified, or that are global to all projects. However, if you need to modify them, just create an empty file with the same name in your myproject/apps/frontend/config/ directory, and override the settings you want to change. The settings defined in an application always have precedence over the ones defined in the framework. The following are the configuration files in the symfony installation config/ directory:

第二组配置文件位于 symfony 安装目录中（在 sfConfig::get('sf_symfony_lib_dir')/config/config/ 中），不会出现在应用程序的配置目录中。在那里定义的设置是默认值，很少需要修改，或者对所有项目都是全局的。但是，如果您需要修改它们，只需在 myproject/apps/frontend/config/ 目录中创建一个同名的空文件，并覆盖要更改的设置。应用程序中定义的设置始终优于框架中定义的设置。以下是 symfony 安装 config/ 目录中的配置文件：

- autoload.yml: This file contains the settings of the autoloading feature. This feature exempts you from requiring custom classes in your code if they are located in specific directories. It is described in detail in Chapter 19.

- autoload.yml：此文件包含自动加载功能的设置。如果自定义类位于特定目录中，此功能可免除您在代码中手动加载它们的要求。第 19 章将详细介绍此功能。

- core_compile.yml: These are lists of classes to be included to start an application. These classes are actually concatenated into an optimized PHP file without comments, which will accelerate the execution by minimizing the file access operations (one file is loaded instead of more than forty for each request). This is especially useful if you don't use a PHP accelerator. Optimization techniques are described in Chapter 18.

- core_compile.yml：这些是启动应用程序时要包含的类列表。这些类实际上被连接成一个没有注释的优化 PHP 文件，通过减少文件访问操作来加速执行（每个请求加载一个文件，而不是四十多个文件）。如果您不使用 PHP 加速器，这尤其有用。第 18 章将介绍优化技术。

- config_handlers.yml: This is where you can add or modify the handlers used to process each configuration file. Chapter 19 provides more details.

- config_handlers.yml：您可以在此添加或修改用于处理每个配置文件的处理程序。第 19 章提供了更多详细信息。

## Module Configuration

By default, a module has no specific configuration. But, if required, you can override some application-level settings for a given module. For instance, you might do this to include a specific JavaScript file for all actions of a module. You can also choose to add new parameters restricted to a specific module to preserve encapsulation.

默认情况下，模块没有特定的配置。但是，如果需要，您可以为特定模块覆盖一些应用程序级别的设置。例如，您可能需要这样做来为模块的所有操作包含特定的 JavaScript 文件。您还可以选择添加仅限于特定模块的新参数以保持封装性。

As you may have guessed, module configuration files must be located in a myproject/apps/frontend/modules/mymodule/config/ directory. These files are as follows:

如您所料，模块配置文件必须位于 myproject/apps/frontend/modules/mymodule/config/ 目录中。这些文件如下：

- generator.yml: For modules generated according to a database table (scaffoldings and administrations), this file defines how the interface displays rows and fields, and which interactions are proposed to the user (filters, sorting, buttons, and so on). Chapter 14 will tell you more about it.

- generator.yml：对于根据数据库表生成的模块（脚手架和管理模块），此文件定义界面如何显示行和字段，以及向用户提出哪些交互（过滤器、排序、按钮等）。第 14 章将详细介绍此文件。

- module.yml: This file contains custom parameters specific to a module and action configuration. Chapter 6 provides more details.

- module.yml：此文件包含特定于模块的自定义参数和操作配置。第 6 章提供了更多详细信息。

- security.yml: This file sets access restrictions for actions. This is where you specify that a page can be viewed only by registered users or by a subset of registered users with special permissions. Chapter 6 will tell you more about it.

- security.yml：此文件为操作设置访问限制。您可以在此指定页面仅供注册用户或拥有特殊权限的注册用户子集查看。第 6 章将详细介绍此文件。

- view.yml: This file contains configuration for the views of one or all of the actions of a module. It overrides the application view.yml and is described in Chapter 7.

- view.yml：此文件包含模块一个或所有操作的视图配置。它覆盖应用程序的 view.yml，并在第 7 章中描述。

Most module configuration files offer the ability to define parameters for all the views or all the actions of a module, or for a subset of them.

大多数模块配置文件都提供为模块的所有视图或所有操作（或其子集）定义参数的功能。

## Too many files?

You might be overwhelmed by the number of configuration files present in the application. But please keep the following in mind:

您可能会被应用程序中大量的配置文件弄不知所措。但请牢记以下几点：

Most of the time, you don't need to change the configuration, since the default conventions match the most common requirements. Each configuration file is related to a particular feature, and the next chapters will detail their use one by one. When you focus on a single file, you can see clearly what it does and how it is organized. For professional web development, the default configuration is often not completely adapted. The configuration files allow for an easy modification of the symfony mechanisms without code. Imagine the amount of PHP code necessary to achieve the same amount of control. If all the configuration were located in one file, not only would the file be completely unreadable, but you could not redefine configuration at several levels (see the “Configuration Cascade” section later in this chapter).

大多数时候，您不需要更改配置，因为默认约定符合最常见的要求。每个配置文件都与特定功能相关，后续章节将逐一详细介绍其用法。当您专注于单个文件时，可以清楚地看到它的作用和组织方式。对于专业 Web 开发，默认配置通常并不完全适用。配置文件允许无需代码即可轻松修改 symfony 机制。想象一下，要实现相同级别的控制需要多少 PHP 代码。如果所有配置都位于一个文件中，不仅该文件将完全无法阅读，而且您还无法在多个级别重新定义配置（参见本章后面的“配置级联”部分）。

The configuration system is one of the great strengths of symfony, because it makes symfony usable for almost every kind of web application, and not only for the ones for which the framework was originally designed.

配置系统是 symfony 的巨大优势之一，因为它使 symfony 可用于几乎每种 Web 应用程序，而不仅仅是框架最初设计的那些应用程序。

## Environments

During the course of application development, you will probably need to keep several sets of configuration in parallel. For instance, you will need to have the connection settings for your tests database available during development, and the ones for your real data available for production. To answer the need of concurrent configurations, symfony offers different environments.

在应用程序开发过程中，您可能需要并行保存多组配置。例如，您需要在开发期间使用测试数据库的连接设置，并在生产环境中使用真实数据的连接设置。为了满足并发配置的需求，symfony 提供了不同的环境。

### What Is an Environment?

### 什么是环境？

An application can run in various environments. The different environments share the same PHP code (apart from the front controller), but can have completely different configurations. For each application, symfony provides three default environments: production (prod), test (test), and development (dev). You're also free to add as many custom environments as you wish.

应用程序可以在各种环境中运行。不同的环境共享相同的 PHP 代码（前置控制器除外），但可以拥有完全不同的配置。对于每个应用程序，symfony 提供三个默认环境：生产环境（prod）、测试环境（test）和开发环境（dev）。您也可以根据需要添加任意数量的自定义环境。

So basically, environments and configuration are synonyms. For instance, a test environment will log alerts and errors, while a prod environment will only log errors. Cache acceleration is often deactivated in the dev environment, but activated in the test and prod environments. The dev and test environments may need test data, stored in a database distinct from the one used in the production environment. So the database configuration will be different between the two environments. All environments can live together on the same machine, although a production server generally contains only the prod environment.

基本上，环境和配置是同义词。例如，测试环境会记录警告和错误，而生产环境只会记录错误。缓存加速在开发环境中通常被禁用，但在测试环境和生产环境中被启用。开发环境和测试环境可能需要测试数据，这些数据存储在与生产环境使用的不同的数据库中。因此，两个环境之间的数据库配置会有所不同。所有环境都可以在同一台机器上共存，尽管生产服务器通常只包含生产环境。

In the dev environment, the logging and debugging settings are all enabled, since maintenance is more important than performance. On the contrary, the prod environment has settings optimized for performance by default, so the production configuration turns off many features. A good rule of thumb is to navigate in the development environment until you are satisfied with the feature you are working on, and then switch to the production environment to check its speed.

在开发环境中，日志记录和调试设置均已启用，因为维护比性能更重要。相反，生产环境默认针对性能进行了优化设置，因此生产配置会关闭许多功能。一个好的经验法则是在开发环境中浏览，直到您对正在处理的功能满意，然后切换到生产环境以检查其速度。

The test environment differs from the dev and prod environment in other ways. You interact with this environment solely through the command line for the purpose of functional testing and batch scripting. Consequently, the test environment is close to the production one, but it is not accessed through a web browser. It simulates the use of cookies and other HTTP specific components.

测试环境与开发环境和生产环境在其他方面有所不同。您仅通过命令行与该环境交互，用于功能测试和批量脚本。因此，测试环境与生产环境很接近，但不是通过 Web 浏览器访问的。它模拟 Cookie 和其他 HTTP 特定组件的使用。

To change the environment in which you're browsing your application, just change the front controller. Until now, you have seen only the development environment, since the URLs used in the example called the development front controller:

要更改浏览应用程序时所在的环境，只需更改前置控制器即可。到目前为止，您只看到了开发环境，因为示例中使用的 URL 调用的是开发前置控制器：

```
http://localhost/frontend_dev.php/mymodule/index
```

However, if you want to see how the application reacts in production, call the production front controller instead:

但是，如果您想查看应用程序在生产环境中的反应，请改用生产前置控制器：

```
http://localhost/index.php/mymodule/index
```

If your web server has mod_rewrite enabled, you can even use the custom symfony rewriting rules, written in web/.htaccess. They define the production front controller as the default execution script and allow for URLs like this:

如果您的 Web 服务器启用了 mod_rewrite，您甚至可以使用 web/.htaccess 中编写的自定义 symfony 重写规则。它们将生产前置控制器定义为默认执行脚本，并允许使用类似这样的 URL：

```
http://localhost/mymodule/index
```





## 环境与服务器

不要混淆环境和服务器的概念。在 symfony 中，不同的环境对应不同的配置，并对应一个前端控制器（执行请求的脚本）。不同的服务器对应 URL 中的不同域名。

```
Listing 5-21 http://localhost/frontend_dev.php/mymodule/index
server environment
```

通常，开发人员在开发服务器上处理应用程序，该服务器断开互联网连接，并且可以随意更改所有服务器和 PHP 配置。当准备将应用程序发布到生产环境时，应用程序文件将被传输到生产服务器并提供给最终用户访问。

这意味着每个服务器上都有多种环境可用。例如，你甚至可以在开发服务器上以生产环境运行。但是，大多数时候，生产服务器上应该只能访问生产环境，以避免服务器配置和安全风险公开可见。为防止生产系统上意外暴露非生产控制器，symfony 为这些前端控制器添加了基本的 IP 检查，仅允许来自 localhost 的访问。如果你希望将其设为可访问，可以删除该检查，但请考虑任何人都能访问的风险，因为恶意用户可能会猜测默认的 frontend_dev.php 并获取大量敏感信息。

要添加新环境，无需创建目录或使用 symfony CLI。只需创建一个新的前端控制器并更改其中的环境名称定义即可。该环境继承所有默认配置以及所有环境共有的设置。下一章将向你展示如何操作。

## 配置级联

同一设置可以在不同位置定义多次。例如，你可能希望将页面的 MIME 类型设置为整个应用程序的 text/html，但 RSS 模块的页面除外，后者需要 text/xml MIME 类型。Symfony 允许你将第一个设置写入 frontend/config/view.yml，将第二个设置写入 frontend/modules/rss/config/view.yml。配置系统知道在模块级别定义的设置必须覆盖在应用程序级别定义的设置。

实际上，symfony 中存在多个配置级别：

- 粒度级别：
  - 框架中位于默认配置
  - 整个项目的全局配置（在 myproject/config/ 中）
  - 项目中应用程序的本地配置（在 myproject/apps/frontend/config/ 中）
  - 限定于模块的本地配置（在 myproject/apps/frontend/modules/mymodule/config/ 中）
- 环境级别：
  - 特定于某个环境
  - 适用于所有环境

在所有可自定义的属性中，许多都依赖于环境。因此，许多 YAML 配置文件按环境划分，另外还有一个适用于所有环境的尾部部分。结果是典型的 symfony 配置如清单 5-12 所示。

### 清单 5-12 - Symfony 配置文件的结构

```
# Production environment settings
prod:
...

# Development environment settings
dev:
...

# Test environment settings
test:
...

# Custom environment settings
myenv:
...

# Settings for all environments
all:
...
```

此外，框架本身在不位于项目目录结构中的文件中定义了默认值，而是位于 symfony 安装目录的 sfConfig::get('sf_symfony_lib_dir')/config/config/ 目录中。默认配置在这些文件中设置，如清单 5-13 所示。这些设置被所有应用程序继承。

### 清单 5-13 - 默认配置，位于 sfConfig::get('sf_symfony_lib_dir')/config/config/settings.yml

```
# Default settings:
default:
  .actions:
    default_module:      default
    default_action:      index
    ...
```

这些默认定义以注释形式重复出现在项目、应用程序和模块配置文件中，如清单 5-14 所示，以便你知道某些参数是默认定义的并且可以修改。

### 清单 5-14 - 默认配置，仅供参考，位于 frontend/config/settings.yml

```
#all:
  # .actions:
    #   default_module:      default
    #   default_action:      index
    #   ...
```

这意味着一个属性可以被定义多次，实际值由定义级联得出。在命名环境中对参数的定义优先于适用于所有环境的同一参数定义，后者又优先于默认配置中的定义。在模块级别对参数的定义优先于在应用程序级别的同一参数定义，后者又优先于在项目级别的定义。这可以总结为以下优先级列表：

1. 模块
2. 应用程序
3. 项目
4. 特定环境
5. 所有环境
6. 默认

## 配置缓存

解析 YAML 并在运行时处理配置级联会对每个请求造成显著的开销。Symfony 内置了配置缓存机制，旨在加快请求速度。

无论配置文件格式如何，都会由一些称为处理程序的特殊类进行处理，这些类将其转换为快速处理的 PHP 代码。在开发环境中，处理程序会在每个请求时检查配置更改，以促进交互性。它们会解析最近修改的文件，因此你可以立即看到 YAML 文件中的更改。但是，在生产环境中，处理过程仅在第一个请求期间发生一次，然后将处理后的 PHP 代码存储在缓存中以供后续请求使用。性能得到保证，因为生产环境中的每个请求都只需执行一些经过良好优化的 PHP 代码。

例如，如果 app.yml 文件包含以下内容：

```
all:
    # Setting for all environments
mail:
  webmaster:  webmaster@example.com
```

那么位于项目 cache/ 文件夹中的文件 config_app.yml.php 将包含以下内容：

```php
<?php
sfConfig::add(array(
  'app_mail_webmaster' => 'webmaster@example.com',
));

```

因此，大多数时候，YAML 文件甚至不会被框架解析，而是依赖配置缓存。但是，在开发环境中，symfony 会系统地比较 YAML 文件和缓存文件的修改日期，并仅重新处理自上次请求以来更改的文件。

这相比许多 PHP 框架具有重大优势，后者会在每个请求（甚至在生产环境中）编译配置文件。与 Java 不同，PHP 在请求之间不共享执行上下文。对于其他 PHP 框架，保持 XML 配置文件的灵活性需要在每个请求时处理所有配置，这会带来巨大的性能损失。symfony 并非如此。得益于缓存系统，配置造成的开销非常低。

这种机制有一个重要后果。如果你在生产环境中更改了配置，则需要强制重新解析所有配置文件，以便考虑你的修改。为此，你只需清除缓存，即通过删除 cache/ 目录的内容，或者更轻松地调用 cache:clear 任务：

```
$ php symfony cache:clear
```

## 从代码中访问配置

所有配置文件最终都会转换为 PHP，其中包含的许多设置会由框架自动使用，无需进一步干预。但是，你有时需要从代码中（在操作、模板、自定义类等）访问配置文件中定义的一些设置。settings.yml、app.yml 和 module.yml 中定义的设置可通过名为 sfConfig 的特殊类使用。

### sfConfig 类

你可以通过 sfConfig 类从应用程序代码中访问设置。它是配置参数的注册表，带有一个简单的 getter 类方法，可从代码的每个部分访问：

```php
// Retrieve a setting
$parameter = sfConfig::get('param_name', $default_value);
```

请注意，你也可以从 PHP 代码中定义或覆盖设置：

```php
// Define a setting
sfConfig::set('param_name', $value);
```

参数名称是按以下顺序用下划线分隔的多个元素的串联：

- 与配置文件名相关的前缀（settings.yml 为 sf_，app.yml 为 app_，module.yml 为 mod_）
- 父级键（如果已定义），小写
- 键名，小写

不包含环境，因为你的 PHP 代码只能访问其执行环境中定义的值。

例如，如果你需要访问清单 5-15 中所示 app.yml 文件中定义的值，则需要清单 5-16 所示的代码。

### 清单 5-15 - 示例 app.yml 配置

```yaml
all:
  .general:
    tax:             19.6
    default_user:
      name:          John Doe
    mail:
      webmaster:     webmaster@example.com
      contact:       contact@example.com
dev:
  mail:
    webmaster:     dummy@example.com
    contact:       dummy@example.com
```

### 清单 5-16 - 在 dev 环境中从 PHP 访问配置设置

```php
echo sfConfig::get('app_tax');  // Remember that category headers are
                                    ignored
                                    => '19.6'
echo sfConfig::get('app_default_user_name');
```



```
=> 'John Doe'
echo sfConfig::get('app_mail_webmaster');
=> 'dummy@example.com'
echo sfConfig::get('app_mail_contact');
=> 'dummy@example.com'
```

Symfony 配置设置拥有 PHP 常量的所有优点，但没有缺点，因为值可以更改。

因此，settings.yml 文件（你可以在其中为应用程序设置框架设置）相当于一系列 sfConfig::set() 调用。清单 5-17 的解释如清单 5-18 所示。

### 清单 5-17 - settings.yml 摘要

```yaml
all:
  .settings:
    csrf_secret: FooBar
    escaping_strategy: true
    escaping_method: ESC_SPECIALCHARS
```

### 清单 5-18 - Symfony 解析 settings.yml 时的操作

```php
sfConfig::add(array(
  'sf_csrf_secret' => 'FooBar',
  'sf_escaping_strategy' => true,
  'sf_escaping_method' => 'ESC_SPECIALCHARS',
));
```

有关 settings.yml 文件中设置的含义，请参阅第 19 章。

## 自定义应用程序设置和 app.yml

与应用程序功能相关的大多数设置都应存储在 myproject/apps/frontend/config/ 目录中的 app.yml 文件中。此文件随环境而异，默认为空。放入你希望轻松更改的每个设置，并使用 sfConfig 类从代码中访问这些设置。清单 5-19 显示了一个示例。

### 清单 5-19 - 用于定义给定站点接受的信用卡运营商的示例 app.yml

```yaml
all:
  creditcards:
    fake: false
    visa: true
    americanexpress: true
dev:
  creditcards:
    fake: true
```

要了解当前环境是否接受伪造信用卡，请获取以下值：

```php
sfConfig::get('app_creditcards_fake');
```

> 当你需要在 all 键下直接获取一个 PHP 数组时，需要使用类别标头，否则 Symfony 会像上面所示分别提供这些值。

```yaml
all:
  .array:
    creditcards:
      fake: false
      visa: true
      americanexpress: true
```

```php
print_r(sfConfig::get('app_creditcards'));

Array(
  [fake] => false
  [visa] => true
  [americanexpress] => true
)
```

**提示** 每次你想要在脚本中定义常量或设置时，考虑一下是否将其放在 app.yml 文件中会更好。这是存储所有应用程序设置的非常方便的位置。

当使用 app.yml 语法处理自定义参数变得困难时，你可能需要定义自己的语法。在这种情况下，可以将配置存储在由新配置处理器解释的新文件中。有关配置处理器的更多信息，请参阅第 19 章。

## 从配置文件中获取更多信息的技巧

在编写自己的 YAML 文件之前，还有几个最后的技巧需要学习。它们将使你能够避免配置重复并处理自己的 YAML 格式。

## 在 YAML 配置文件中使用常量

某些配置设置依赖于其他设置的值。为了避免两次设置相同的值，Symfony 在 YAML 文件中支持常量。当配置处理器遇到用 % 符号括起来的大写设置名称（即可以通过 sfConfig::get() 访问的名称）时，会将其替换为当前值。示例请参见清单 5-20。

### 清单 5-20 - 在 YAML 文件中使用常量，autoload.yml 示例

```yaml
autoload:
  symfony:
    name: symfony
    path: %SF_SYMFONY_LIB_DIR%
    recursive: true
    exclude: [vendor]
```

path 参数将采用 sfConfig::get('sf_symfony_lib_dir') 返回的值。如果你希望一个配置文件依赖于另一个，则需要确保所依赖的文件已经解析（在 Symfony 源代码中查找配置文件解析顺序）。app.yml 是最后解析的文件之一，因此你可以在其中依赖其他文件。

所有可用常量在 Symfony 参考书第 33 章中有描述。

## 使用可脚本化的配置

你的配置可能依赖于外部参数（例如数据库或另一个配置文件）。为了处理这些特殊情况，Symfony 配置文件在传递给 YAML 解析器之前会作为 PHP 文件解析。这意味着你可以在 YAML 文件中插入 PHP 代码，如清单 5-21 所示。

### 清单 5-21 - YAML 文件可包含 PHP

```yaml
all:
  translation:
    format: <?php echo (sfConfig::get('sf_i18n') == true ? 'xliff' : null)."\n" ?>
```

但请注意，配置在请求生命周期非常早期就被解析，因此你无法使用任何 Symfony 内置方法或函数来提供帮助。

另外，由于 echo 语言结构默认不会添加回车符，你需要添加 "\n" 或使用 echoln 辅助函数以保持 YAML 格式有效。

### 清单 5-39

```yaml
all:
  translation:
    format: <?php echoln(sfConfig::get('sf_i18n') == true ? 'xliff' : 'none') ?>
```

> 在生产环境中，配置会被缓存，因此配置文件仅在缓存清除后解析（并执行）一次。

## 浏览你自己的 YAML 文件

每当你想要直接读取 YAML 文件时，可以使用 sfYaml 类。它是一个 YAML 解析器，可以将 YAML 文件转换为 PHP 关联数组。清单 5-22 展示了一个示例 YAML 文件，清单 5-23 演示了如何解析它。

### 清单 5-22 - 示例 test.yml 文件

```yaml
house:
  family:
    name: Doe
    parents: [John, Jane]
    children: [Paul, Mark, Simone]
  address:
    number: 34
    street: Main Street
    city: Nowheretown
    zipcode: 12345
```

### 清单 5-23 - 使用 sfYaml 类将 YAML 文件转换为关联数组

```php
$test = sfYaml::load('/path/to/test.yml');
print_r($test);

Array(
  [house] => Array(
    [family] => Array(
      [name] => Doe
      [parents] => Array(
        [0] => John
        [1] => Jane
      )
      [children] => Array(
        [0] => Paul
        [1] => Mark
        [2] => Simone
      )
    )
    [address] => Array(
      [number] => 34
      [street] => Main Street
      [city] => Nowheretown
      [zipcode] => 12345
    )
  )
)
```

## 摘要

Symfony 配置系统使用 YAML 语言以实现简单易读。能够处理多个环境并通过定义级联设置参数，为开发人员提供了灵活性。部分配置可以通过 sfConfig 对象在代码中访问，特别是存储在 app.yml 文件中的应用程序设置。

是的，Symfony 确实有很多配置文件，但这种方法使其更具适应性。请记住，除非你的应用程序需要高度定制，否则无需担心这些文件。

# 第 6章 控制器层内部

在 Symfony 中，控制器层包含连接业务逻辑和展示层的代码，分为多个组件，用于不同目的：

- 前控制器是应用程序的唯一入口点。它加载配置并确定要执行的操作。
- 操作包含应用程序逻辑。它们检查请求的完整性并准备展示层所需的数据。
- 请求、响应和会话对象提供对请求参数、响应标头和持久用户数据的访问。它们在控制器层中非常常用。
- 过滤器是在每个请求之前或之后执行的代码部分。例如，安全过滤器和验证过滤器通常用于 Web 应用程序。你可以通过创建自己的过滤器来扩展框架。

本章介绍了所有这些组件，但请不要被它们的数量吓到。对于基本页面，你可能只需要在操作类中写几行代码，就完成了。其他控制器组件仅在特定情况下有用。

## 前控制器

所有 Web 请求都由单个前控制器处理，它是特定环境下整个应用程序的唯一入口点。

当前控制器接收到请求时，它使用路由系统将用户输入（或点击）的 URL 与操作名和模块名进行匹配。例如，以下请求 URL 调用 index.php 脚本（即前控制器），并将被理解为对 mymodule 模块中 myAction 操作的调用：

### 清单 6-1

```
http://localhost/index.php/mymodule/myAction
```

如果你不关心 Symfony 的内部机制，那么关于前控制器你需要知道的就是这些。它是 Symfony MVC 架构中不可或缺的组件，但你很少需要修改它。因此，除非你真的想了解前控制器的内部工作原理，否则可以跳到下一节。

## 前控制器工作的详细情况

前控制器负责请求分发，但这不仅仅是确定要执行的操作。实际上，它执行所有操作共有的代码，包括以下内容：

- 加载项目配置类和 Symfony 库。





- 创建应用程序配置和 symfony 上下文。
- 加载并启动核心框架类。
- 加载配置。
- 解码请求 URL 以确定要执行的操作和请求参数。
- 如果操作不存在，则重定向到 404 错误操作。
- 激活过滤器（例如，如果请求需要身份验证）。
- 执行过滤器，第一遍。
- 执行操作并渲染视图。
- 执行过滤器，第二遍。
- 输出响应。

## 默认前置控制器

默认前置控制器名为 index.php，位于项目 web/ 目录下，是一个简单的 PHP 文件，如清单 6-1 所示。

## 清单 6-1 - 默认生产环境前置控制器

```
<?php
require_once(dirname(__FILE__).'/../config/ProjectConfiguration.class.php');

$configuration =
ProjectConfiguration::getApplicationConfiguration('frontend', 'prod',
false);
sfContext::createInstance($configuration)->dispatch();
```

前置控制器创建应用程序配置实例，负责处理步骤 2 至 4。调用 sfController 对象（即 symfony MVC 架构的核心控制器对象）的 dispatch() 方法会分发请求，负责处理步骤 5 至 7。最后的步骤由过滤器链处理，如本章后面所述。

## 调用另一前置控制器以切换环境

每个环境都有一个前置控制器。事实上，正是前置控制器的存在定义了环境。环境由你传递给 ProjectConfiguration::getApplicationConfiguration() 方法调用的第二个参数定义。

要更改浏览应用程序所在的环境，只需选择另一个前置控制器。使用 generate:app 任务创建新应用程序时可用的默认前置控制器有：生产环境的 index.php 和开发环境的 frontend_dev.php（前提是你的应用名为 frontend）。默认的 mod_rewrite 配置会在 URL 不包含前置控制器脚本名称时使用 index.php。因此，以下两个 URL 在生产环境下显示相同页面（mymodule/index）：

```
http://localhost/index.php/mymodule/index
http://localhost/mymodule/index
```

而此 URL 在开发环境下显示相同页面：

```
http://localhost/frontend_dev.php/mymodule/index
```

创建新环境与创建新前置控制器一样简单。例如，你可能需要一个预发布环境，以便客户在上线前测试应用程序。要创建此预发布环境，只需将 web/frontend_dev.php 复制到 web/frontend_staging.php，并将 ProjectConfiguration::getApplicationConfiguration() 调用的第二个参数值更改为 staging。现在，在所有配置文件中，你可以添加一个新的 staging: 部分来为此环境设置特定值，如清单 6-2 所示。

## 清单 6-2 - 适用于预发布环境的示例 app.yml，包含特定设置

```
staging:
  mail:
    webmaster: dummy@mysite.com
    contact: dummy@mysite.com
  all:
    mail:
      webmaster: webmaster@mysite.com
      contact: contact@mysite.com
```

如果你想查看应用程序在此新环境下的表现，请调用相关前置控制器：

```
http://localhost/frontend_staging.php/mymodule/index
```

## 操作

操作是应用程序的核心，因为它们包含应用程序的所有逻辑。它们调用模型并为视图定义变量。当你在 symfony 应用程序中发出 Web 请求时，URL 定义了操作和请求参数。

## 操作类

操作是名为 moduleNameActions、继承自 sfActions 类且按模块分组的类中的 executeActionName 方法。模块的操作类存储在模块 actions/ 目录中的 actions.class.php 文件中。

## 清单 6-3 - 示例操作类，位于 apps/frontend/modules/mymodule/actions/actions.class.php

```
class mymoduleActions extends sfActions
{
  public function executeIndex($request)
  {
    // ...
  }
}
```

> 尽管 PHP 中的方法名不区分大小写，但在 symfony 中区分大小写。因此请记住，操作方法必须以小写 execute 开头，后跟首字母大写的精确操作名称。

要请求一个操作，需要以模块名和操作名为参数调用前置控制器脚本。默认情况下，通过将 module_name/action_name 对追加到脚本来实现。这意味着清单 6-4 中定义的操作可通过以下 URL 调用：

http://localhost/index.php/mymodule/index

添加更多操作只需向 sfActions 对象添加更多 execute 方法，如清单 6-4 所示。

## 清单 6-4 - 包含两个操作的操作类，位于 frontend/modules/mymodule/actions/actions.class.php

```
class mymoduleActions extends sfActions
{
    public function executeIndex($request)
    {
        // ...
    }

    public function executeList($request)
    {
        // ...
    }
}
```

如果操作类规模过大，你可能需要进行一些重构，并将部分代码移至模型层。操作通常应保持简短（不超过几行），所有业务逻辑通常应位于模型中。

不过，模块中的操作数量可能足够多，以至于你需要将其拆分为两个模块。

## Symfony 编码规范

在本书给出的代码示例中，你可能已经注意到，左花括号和右花括号（{ 和 }）各自占用一行。这一规范使代码更易于阅读。

在框架的其他编码规范中，缩进始终使用两个空格；不使用制表符。这是因为制表符根据所使用的文本编辑器具有不同的空格值，而且混合使用制表符和空格缩进的代码无法阅读。

核心和生成的 symfony PHP 文件不以通常的 ?> 结束标签结尾。这是因为它并非真正需要，而且如果此标签后有空格，可能会在输出中造成问题。

如果你真的留意，会发现 symfony 中的行永远不会以空格结尾。这次的原因更为平凡：以空格结尾的行在 Fabien 的文本编辑器中看起来很难看。

## 替代操作类语法

提供了一种替代操作语法，用于将操作分发到单独的文件中，每个操作一个文件。在这种情况下，每个操作类扩展 sfAction（而不是 sfActions）并命名为 actionNameAction。实际的操作方法简单地命名为 execute。文件名与类名相同。这意味着清单 6-4 的等效代码可以使用清单 6-5 和 6-6 中显示的两个文件来编写。

## 清单 6-5 - 单个操作文件，位于 frontend/modules/mymodule/actions/indexAction.class.php

```
class indexAction extends sfAction
{
  public function execute($request)
  {
    // ...
  }
}
```

## 清单 6-6 - 单个操作文件，位于 frontend/modules/mymodule/actions/listAction.class.php

```
class listAction extends sfAction
{
  public function execute($request)
  {
    // ...
  }
}
```

## 在操作中检索信息

操作类提供了一种访问控制器相关信息和核心 symfony 对象的方式。清单 6-7 演示了如何使用它们。

## 清单 6-7 - sfActions 常用方法

```
class mymoduleActions extends sfActions
{
  public function executeIndex(sfWebRequest $request)
  {
    // Retrieving request parameters
    $password = $request->getParameter('password');

    // Retrieving controller information
    $moduleName = $this->getModuleName();
    $actionName = $this->getActionName();

    // Retrieving framework core objects
    $userSession = $this->getUser();
    $response = $this->getResponse();
    $controller = $this->getController();
    $context = $this->getContext();

    // Setting action variables to pass information to the template
    $this->setVar('foo', 'bar');
    $this->foo = 'bar';         // Shorter version
  }
}


## 上下文单例

你之前已经在前端控制器中看到了对 sfContext::createInstance() 的调用。在动作中，getContext() 方法返回同一个单例。这是一个非常有用的对象，它存储了与给定请求相关的所有 symfony 核心对象的引用，并为每个对象提供访问器：

- sfController：控制器对象（->getController()）
- sfRequest：请求对象（->getRequest()）
- sfResponse：响应对象（->getResponse()）
- sfUser：用户会话对象（->getUser()）
- sfRouting：路由对象（->getRouting()）
- sfMailer：邮件对象（->getMailer()）
- sfI18N：国际化对象（->getI18N()）
- sfLogger：日志对象（->getLogger()）
- sfDatabaseConnection：数据库连接（->getDatabaseConnection()）

所有这些核心对象都可以通过任何代码中的 sfContext::getInstance() 单例来使用。然而，这是一种非常糟糕的做法，因为这会创建一些硬依赖，使你的代码非常难以测试、重用和维护。你将在本书中学习如何避免使用 sfContext::getInstance()。

## 动作终止

动作执行结束时可能出现各种行为。动作方法返回的值决定了视图将如何渲染。sfView 类的常量用于指定使用哪个模板来显示动作的结果。

如果有一个默认视图可调用（这是最常见的情况），动作应如下结束：

```
return sfView::SUCCESS;
```

Symfony 将查找名为 actionNameSuccess.php 的模板。这被定义为默认动作行为，因此如果你在动作方法中省略 return 语句，symfony 也会查找 actionNameSuccess.php 模板。空动作也会触发该行为。有关成功动作终止的示例，请参见清单 6-8。

### 清单 6-8 - 将调用 indexSuccess.php 和 listSuccess.php 模板的动作

```
public function executeIndex()
{
    return sfView::SUCCESS;
}

public function executeList()
{
}
```

如果有一个错误视图可调用，动作应如下结束：

```
return sfView::ERROR;
```

Symfony 将查找名为 actionNameError.php 的模板。

要调用自定义视图，请使用以下结尾：

### 清单 6-16

```
return 'MyResult';
```

Symfony 将查找名为 actionNameMyResult.php 的模板。

如果没有视图可调用——例如，在批处理中执行的动作的情况——动作应如下结束：

### 清单 6-17

```
return sfView::NONE;
```

在这种情况下，不会执行任何模板。这意味着你可以完全绕过视图层，直接从动作中设置响应 HTML 代码。如清单 6-9 所示，symfony 为此情况提供了特定的 renderText() 方法。当你需要动作具有极高的响应速度时，这可能很有用，例如 Ajax 交互，这将在第 11 章中讨论。

### 清单 6-9 - 通过回显响应并返回 sfView::NONE 来绕过视图

```
public function executeIndex()
{
    $this->getResponse()->setContent("<html><body>Hello,
    World!</body></html>");
    return sfView::NONE;
}
```

```
// Is equivalent to
public function executeIndex()
{
    return $this->renderText("<html><body>Hello, World!</body></html>");
}
```

在某些情况下，你需要发送一个空响应，但其中包含一些定义的头部（尤其是 X-JSON 头部）。通过下一章讨论的 sfResponse 对象定义头部，并返回 sfView::HEADER_ONLY 常量，如清单 6-10 所示。

### 清单 6-10 - 绕过视图渲染并仅发送头部

```
public function executeRefresh()
{
    $output = '<"title","My basic letter"],["name","Mr Brown">';
    $this->getResponse()->setHttpHeader("X-JSON", '('. $output .')');
    return sfView::HEADER_ONLY;
}
```

如果动作必须由特定模板渲染，请忽略 return 语句，改用 setTemplate() 方法。

### 清单 6-20

```
public function executeIndex()
{
    $this->setTemplate('myCustomTemplate');
}
```

使用此代码，symfony 将查找 myCustomTemplateSuccess.php 文件，而不是 indexSuccess.php。

## 跳转到另一个动作

在某些情况下，动作执行结束于请求新的动作执行。例如，处理 POST 请求中表单提交的动作通常在更新数据库后重定向到另一个动作。

动作类提供两种方法来执行另一个动作：

- 如果动作将调用转发给另一个动作：

```
$this->forward('otherModule', 'index');
```

- 如果动作导致 Web 重定向：

```
$this->redirect('otherModule/index');
$this->redirect('http://www.google.com/');
```

动作中 forward 或 redirect 之后的代码永远不会执行。你可以认为这些调用等同于 return 语句。它们抛出 sfStopException 以停止动作的执行；此异常随后被 symfony 捕获并简单地忽略。

在重定向和转发之间做选择有时很棘手。要选择最佳解决方案，请记住，转发是应用程序内部的，对用户透明。就用户而言，显示的 URL 与请求的 URL 相同。相比之下，重定向是发送给用户浏览器的消息，涉及来自浏览器的新请求，并更改最终生成的 URL。

如果动作是由 method="post" 的提交表单调用，你应该 **始终** 进行重定向。主要优势是，如果用户刷新生成的页面，表单不会被重新提交；此外，后退按钮会按预期工作，显示表单而不是询问用户是否要重新提交 POST 请求的警告。

有一种特殊的转发非常常用。forward404() 方法转发到“页面未找到”动作。当动作执行所需的参数在请求中不存在时（从而检测到错误输入的 URL），通常会调用此方法。清单 6-11 显示了一个期望 id 参数的 show 动作示例。

### 清单 6-11 - forward404() 方法的使用

```
public function executeShow(sfWebRequest $request)
{
// Doctrine
//article =
Doctrine::getTable('Article')->find($request->getParameter('id'));

// Propel
$article = ArticlePeer::retrieveByPK($request->getParameter('id'));

if (!$article)
{
$this->forward404();
}
}
```

如果你要查找错误 404 动作和模板，可以在 $sf_symfony_lib_dir/controller/default/ 目录中找到它们。你可以通过向应用程序添加新的默认模块来自定义此页面，覆盖框架中位于该位置的模块，并在其中定义 error404 动作和 error404Success 模板。或者，你可以在 settings.yml 文件中设置 error_404_module 和 error_404_action 常量以使用现有动作。

经验表明，大多数情况下，动作在测试某些内容后会进行重定向或转发，如清单 6-12 所示。这就是为什么 sfActions 类有一些更多方法，名为 forwardIf()、forwardUnless()、forward404If()、forward404Unless()、redirectIf() 和 redirectUnless()。这些方法只需一个额外参数，表示一个条件，如果测试结果为 true（对于 xxxIf() 方法）或 false（对于 xxxUnless() 方法），则触发执行，如清单 6-12 所示。

### 清单 6-12 - forward404If() 方法的使用

```
// This action is equivalent to the one shown in Listing 6-11
public function executeShow(sfWebRequest $request)
{
  $article =
  Doctrine::getTable('Article')->find($request->getParameter('id'));
  $this->forward404If(!$article);
}
```

```
// So is this one
public function executeShow(sfWebRequest $request)
{
  $article =
  Doctrine::getTable('Article')->find($request->getParameter('id'));
  $this->forward404Unless($article);
}
```

使用这些方法不仅能保持代码简短，还能使其更具可读性。

> 当动作调用 forward404() 或其同类方法时，symfony 会抛出 sfError404Exception 来管理 404 响应。这意味着，如果你需要在不想访问控制器的位置显示 404 消息，可以直接抛出类似异常。

## 模块中多个动作的重复代码

命名动作 executeActionName()（在 sfActions 类的情况下）或 execute()（在 sfAction 类的情况下）的约定保证了 symfony 会找到动作方法。它让你能够添加自己的其他方法，只要它们不以 execute 开头，这些方法就不会被视为动作。

当你需要在每个动作的实际执行之前重复多条语句时，还有另一个有用的约定。你可以将它们提取到动作类的 preExecute() 方法中。你可能已经猜到如何在每个动作执行之后重复语句：将它们封装在 postExecute() 方法中。这些方法的语法在清单 6-13 中显示。

### 清单 6-13 - 在动作类中使用 preExecute()、postExecute() 和自定义方法

```
class mymoduleActions extends sfActions
{
  public function preExecute()
  {
```





```
The code inserted here is executed at the beginning of each action
call
...
}

public function executeIndex($request)
{
...
}

public function executeList($request)
{
...
$this->myCustomMethod(); // Methods of the action class are accessible
}

public function postExecute()
{
// The code inserted here is executed at the end of each action call
...
}

protected function myCustomMethod()
{
// You can also add your own methods, as long as they don't start with
"execute"
// In that case, it's better to declare them as protected or private
...
}
}
```

> 由于前置/后置执行方法会对当前模块的**每个**操作进行调用，请务必确认你确实需要为**所有**操作执行这段代码，以避免不必要的副作用。

## 访问请求

任何动作方法的第一个参数都是请求对象，在 symfony 中称为 sfWebRequest。你已经熟悉 `getParameter('myparam')` 方法，用于按名称检索请求参数的值。表 6-1 列出了最有用的 sfWebRequest 方法。

## 表 6-1 - sfWebRequest 对象的方法

| 名称 | 功能 | 示例输出 |
|---|---|---|
| 请求信息 | | |
| isMethod($method) | 这是 POST 还是 GET？ | true 或 false |
| getMethod() | 请求方法名称 | 'POST' |
| getHttpHeader('Server') | 指定 HTTP 标头的值 | 'Apache/2.0.59 (Unix) DAV/2 PHP/5.1.6' |
| getCookie('foo') | 名为指定 Cookie 的值 | 'bar' |
| isXmlHttpRequest()* | 这是 Ajax 请求吗？ | true |
| isSecure() | 这是 SSL 请求吗？ | true |
| **请求参数** | | |
| hasParameter('foo') | 请求中是否存在某个参数？ | true |
| getParameter('foo') | 名为指定参数的值 | 'bar' |
| getParameterHolder()->getAll() | 所有请求参数的数组 | |
| **与 URI 相关的信息** | | |
| getUri() | 完整 URI | 'http://localhost/frontend_dev.php/mymodule/myaction' |
| getPathInfo() | 路径信息 | '/mymodule/myaction' |
| getReferer()** | 来源页面 | 'http://localhost/frontend_dev.php/' |
| getHost() | 主机名 | 'localhost' |
| getScriptName() | 前置控制器路径和名称 | 'frontend_dev.php' |
| **客户端浏览器信息** | | |
| getLanguages() | 接受的语言数组 | Array( [0] => fr [1] => fr_FR [2] => en_US [3] => en ) |
| getCharsets() | 接受的字符集数组 | Array( [0] => ISO-8859-1 [1] => UTF-8 [2] => * ) |
| getAcceptableContentTypes() | 接受的内容类型数组 | Array( [0] => text/xml [1] => text/html |

* 适用于 prototype、Prototype、Mootools 和 jQuery
** 有时会被代理服务器阻止

你无需担心服务器是否支持 `$_SERVER` 或 `$ENV` 变量，也无需担心默认值或服务器兼容性问题——sfWebRequest 方法会为你处理所有这些。此外，这些方法的名称非常直观，你不再需要浏览 PHP 文档来了解如何从请求中获取信息。

## 用户会话

Symfony 会自动管理用户会话，并能够在用户请求之间保留持久数据。它使用内置的 PHP 会话处理机制，并对其进行增强，使其更具可配置性且更易于使用。

## 访问用户会话

在动作中通过 `getUser()` 方法访问当前用户的会话对象，它是 `sfUser` 类的实例。该类包含一个参数持有器，允许你在其中存储任何用户属性。这些数据在用户会话结束前都可用于其他请求，如清单 6-14 所示。用户属性可以存储任何类型的数据（字符串、数组和关联数组）。可以为每个单独的用户设置它们，即使该用户未被识别。

## 清单 6-14 - sfUser 对象可以存储跨请求存在的自定义用户属性

```
class mymoduleActions extends sfActions
{
  public function executeFirstPage($request)
  {
    $nickname = $request->getParameter('nickname');

    // Store data in the user session
    $this->getUser()->setAttribute('nickname', $nickname);
  }

  public function executeSecondPage()
  {
    // Retrieve data from the user session with a default value
    $nickname = $this->getUser()->getAttribute('nickname', 'Anonymous Coward');
  }
}
```

> 你可以将对象存储在用户会话中，但强烈不建议这样做。这是因为会话对象在请求之间会被序列化。当会话被反序列化时，存储对象的类必须已经加载，而情况并非总是如此。此外，如果存储 Propel 或 Doctrine 对象，可能会出现“停滞”对象。

与 symfony 中的许多 getter 方法一样，`getAttribute()` 方法接受第二个参数，用于指定属性未定义时使用的默认值。要检查用户是否已定义某个属性，请使用 `hasAttribute()` 方法。属性存储在可通过 `getAttributeHolder()` 方法访问的参数持有器中。它允许使用常规参数持有器方法轻松清理用户属性，如清单 6-15 所示。

## 清单 6-15 - 从用户会话中删除数据

```
class mymoduleActions extends sfActions
{
  public function executeRemoveNickname()
  {
    $this->getUser()->getAttributeHolder()->remove('nickname');
  }

  public function executeCleanup()
  {
    $this->getUser()->getAttributeHolder()->clear();
  }
}
```

用户会话属性默认也可在模板中通过 `$sf_user` 变量使用，该变量存储当前的 `sfUser` 对象，如清单 6-16 所示。

## 清单 6-16 - 模板也可以访问用户会话属性

```
<p>
Hello, <?php echo $sf_user->getAttribute('nickname') ?>
</p>
```

## 闪存属性

用户属性的一个反复出现的问题是，在不再需要该属性后清理用户会话。例如，你可能希望在通过表单更新数据后显示确认消息。由于表单处理动作会执行重定向，将信息从这个动作传递到其重定向目标动作的唯一方法是将信息存储在用户会话中。但是，在显示确认消息后，你需要清除该属性；否则，它将保留在会话中直到过期。

闪存属性是一种短暂的属性，你可以定义它然后就忘掉它，因为它会在紧接着的下一个请求后消失，并为将来保持用户会话的整洁。在你的动作中，按如下方式定义闪存属性：

```
Listing 6-29
$this->getUser()->setFlash('notice', $value);
```

模板将被呈现并交付给用户，用户随后会向另一个动作发起新请求。在这个第二个动作中，只需按如下方式获取闪存属性的值：

```
Listing 6-30
$value = $this->getUser()->getFlash('notice');
```

然后就忘掉它。在交付这个第二个页面后，notice 闪存属性将被刷新。即使你在这个第二个动作中不需要它，闪存也会从会话中消失。

如果需要从模板访问闪存属性，请使用 `$sf_user` 对象：

```
Listing 6-31
<?php if ($sf_user->hasFlash('notice')): ?>
<?php echo $sf_user->getFlash('notice') ?>
<?php endif; ?>
```

或：

```
Listing 6-32
<?php echo $sf_user->getFlash('notice') ?>
```

闪存属性是将信息传递给紧接着下一个请求的一种干净方式。

## 会话管理

Symfony 的会话处理功能对开发者完全屏蔽了客户端和服务器上会话 ID 的存储方式。但是，如果你想修改会话管理机制的默认行为，这仍然是可能的。这主要面向高级用户。

在客户端，会话通过 Cookie 处理。symfony 会话 Cookie 名为 symfony，但你可以通过编辑 `factories.yml` 配置文件来更改其名称，如清单 6-17 所示。

### 清单 6-17 - 在 apps/frontend/config/factories.yml 中更改会话 Cookie 名称

```
Listing 6-33
all:
storage:
class: sfSessionStorage
param:
session_name: my_cookie_name
```





只有当 factories.yml 中的 auto_start 参数设置为 true 时（默认情况下即为此值），会话才会启动（使用 PHP 函数 session_start()）。如果你想手动启动用户会话，请禁用存储工厂的此设置。

Symfony 的会话处理基于 PHP 会话。这意味着，如果你希望客户端的会话管理由 URL 参数而非 Cookie 处理，只需更改 php.ini 中的 use_trans_sid 设置即可。请注意，不推荐这样做。

```
session.use_trans_sid = 1
```

在服务器端，Symfony 默认将用户会话存储在文件中。你可以通过更改 factories.yml 中 class 参数的值将它们存储在数据库中，如清单 6-18 所示。

### 清单 6-18 - 更改服务器会话存储，位于 apps/frontend/config/factories.yml

```yaml
all:
  storage:
    class: sfMySQLSessionStorage
    param:
      db_table: session  # Name of the table storing the sessions
      database: propel   # Name of the database connection to use
      # Optional parameters
      db_id_col: sess_id   # Name of the column storing the session id
      db_data_col: sess_data  # Name of the column storing the session data
      db_time_col: sess_time  # Name of the column storing the session timestamp
```

database 设置定义要使用的数据库连接。Symfony 随后将使用 databases.yml（参见第 8 章）来确定此连接的连接设置（主机、数据库名、用户和密码）。

可用的会话存储类包括 sfCacheSessionStorage、sfMySQLSessionStorage、sfMySQLiSessionStorage、sfPostgreSQLSessionStorage 和 sfPDOSessionStorage；推荐使用后者。要完全禁用会话存储，可以使用 sfNoStorage 类。

会话过期会在 30 分钟后自动发生。此默认设置可以在同一个 factories.yml 配置文件中为每个环境进行修改，但这次是在用户工厂中，如清单 6-19 所示。

### 清单 6-19 - 更改会话生存期，位于 apps/frontend/config/factories.yml

```yaml
all:
  user:
    class: myUser
    param:
      timeout: 1800     # Session lifetime in seconds
```

要了解有关工厂的更多信息，请参阅第 19 章。

## 动作安全

执行动作的能力可以限制为具有特定权限的用户。Symfony 为此目的提供的工具允许创建安全的应用程序，用户在访问某些功能或应用程序的某些部分需要先进行身份验证。保护应用程序需要两个步骤：为每个动作声明安全要求，并登录具有权限的用户，以便他们可以访问这些安全动作。

### 访问限制

在执行之前，每个动作都会通过一个特殊的过滤器，该过滤器检查当前用户是否有权访问请求的动作。在 Symfony 中，权限由两部分组成：

- 安全动作要求用户经过身份验证。
- 凭据是命名的安全权限，允许按组织分组管理安全。

限制对动作的访问只需在模块 config/ 目录中创建和编辑名为 security.yml 的 YAML 配置文件即可。在此文件中，你可以指定用户必须为每个动作或所有动作满足的安全要求。清单 6-20 显示了一个示例 security.yml。

### 清单 6-20 - 设置访问限制，位于 apps/frontend/modules/mymodule/config/security.yml

```yaml
read:
    is_secure: false    # All users can request the read action

update:
    is_secure: true    # The update action is only for authenticated users

delete:
    is_secure: true    # Only for authenticated users
    credentials: admin    # With the admin credential

all:
    is_secure: false    # false is the default value anyway
```

动作默认不安全，因此当没有 security.yml 或其中未提及某个动作时，所有用户都可以访问该动作。如果存在 security.yml，Symfony 会查找请求动作的名称，如果存在，则检查安全要求是否满足。当用户尝试访问受限动作时会发生什么取决于其凭据：

- 如果用户已通过身份验证并具有适当的凭据，则执行该动作。
- 如果用户未经过身份识别，他将被重定向到默认的登录动作。
- 如果用户已通过身份识别但没有适当的凭据，他将被重定向到默认的安全动作，如图 6-1 所示。

默认的登录和安全页面非常简单，你可能希望对其进行自定义。你可以在应用程序的 settings.yml 中更改清单 6-21 所示属性的值，以配置在权限不足时应调用哪些动作。

### 图 6-1 - 默认安全动作页面

![](img/0f886a7f4cbcc3939be96e985ca35ff4_88_0.png)

### 清单 6-21 - 默认安全动作定义在 apps/frontend/config/settings.yml 中

```yaml
all:
  .actions:
    login_module:  default
    login_action:  login

    secure_module: default
    secure_action: secure
```

### 授予访问权限

要访问受限动作，用户需要经过身份验证和/或具有特定的凭据。你可以通过调用 sfUser 对象的方法来扩展用户的权限。用户的身份验证状态由 setAuthenticated() 方法设置，并可使用 isAuthenticated() 进行检查。清单 6-22 显示了用户身份验证的简单示例。

### 清单 6-22 - 设置用户的身份验证状态

```php
class myAccountActions extends sfActions
{
  public function executeLogin($request)
  {
    if ($request->getParameter('login') == 'foobar')
    {
      $this->getUser()->setAuthenticated(true);
    }
  }

  public function executeLogout()
  {
    $this->getUser()->setAuthenticated(false);
  }
}
```

凭据的处理稍微复杂一些，因为你可以检查、添加、删除和清除凭据。清单 6-23 描述了 sfUser 类的凭据方法。

### 清单 6-23 - 在动作中处理用户凭据

```php
class myAccountActions extends sfActions
{
    public function executeDoThingsWithCredentials()
    {
        $user = $this->getUser();

        // Add one or more credentials
        $user->addCredential('foo');
        $user->addCredentials(array('foo', 'bar'));

        // Check if the user has a credential
        echo $user->hasCredential('foo');               =>  true

        // Check if the user has both credentials
        echo $user->hasCredential(array('foo', 'bar'));   =>  true

        // Check if the user has one of the credentials
        echo $user->hasCredential(array('foo', 'bar'), false); =>  true

        // Remove a credential
        $user->removeCredential('foo');
        echo $user->hasCredential('foo');               =>  false

        // Remove all credentials (useful in the logout process)
        $user->clearCredentials();
        echo $user->hasCredential('bar');               =>  false
    }
}
```

如果用户具有 foo 凭据，则该用户将能够访问 security.yml 要求该凭据的动作。凭据也可用于在模板中仅显示授权内容，如清单 6-24 所示。

### 清单 6-24 - 在模板中处理用户凭据

```php
<ul>
  <li><?php echo link_to('section1', 'content/section1') ?></li>
  <li><?php echo link_to('section2', 'content/section2') ?></li>
  <?php if ($sf_user->hasCredential('section3')): ?>
    <li><?php echo link_to('section3', 'content/section3') ?></li>
  <?php endif; ?>
</ul>
```

与身份验证状态一样，凭据通常在登录过程中授予用户。这就是为什么 sfUser 对象经常被扩展以添加登录和注销方法，以便在一个集中的位置设置用户的安全状态。

> 在 Symfony 插件中，sfGuardPlugin<sup>34</sup> 和 sfDoctrineGuardPlugin<sup>35</sup> 扩展了会话类以简化登录和注销。有关更多信息，请参阅第 17 章。

34. http://www.symfony-project.org/plugins/sfGuardPlugin
35. http://www.symfony-project.org/plugins/sfDoctrineGuardPlugin





## 复杂凭证

security.yml 文件中使用的 YAML 语法允许你通过 AND 类型或 OR 类型关联来限制拥有凭证组合的用户的访问权限。使用这种组合，你可以构建复杂的工作流和用户权限管理系统——例如，仅允许拥有 admin 凭证的用户访问的内容管理系统（CMS）后台，其中文章只能由拥有 editor 凭证的用户编辑，只能由拥有 publisher 凭证的用户发布。清单 6-25 显示了此示例。

### 清单 6-25 - 凭证组合语法

```
Listing 6-25 - Credentials Combination Syntax

editArticle:
  credentials: [ admin, editor ]     # admin AND editor

publishArticle:
  credentials: [ admin, publisher ]  # admin AND publisher

userManagement:
  credentials: [ [ admin, superuser ]]  # admin OR superuser
```

每次添加新的方括号层级时，逻辑会在 AND 和 OR 之间切换。因此，你可以创建非常复杂的凭证组合，例如：

```
credentials: [[root, [supplier, [owner, quasiowner]]], accounts]]
  # root OR (supplier AND (owner OR quasiowner)) OR accounts
```

## 过滤器

安全过程可以理解为一个过滤器，所有请求在执行动作之前都必须通过它。根据在过滤器中执行的一些测试，请求的处理会被修改——例如，更改执行的动作（在安全过滤器的情况下，使用 default/secure 代替请求的动作）。Symfony 将此想法扩展到过滤器类。你可以指定任意数量的过滤器类在动作执行之前或响应呈现之前执行，并且针对每个请求都如此。你可以将过滤器视为一种打包代码的方式，类似于 `preExecute()` 和 `postExecute()`，但在更高级别（针对整个应用程序而不是整个模块）。

## 过滤器链

Symfony 实际上将请求的处理视为一系列过滤器链。当框架接收到请求时，第一个过滤器（始终是 sfRenderingFilter）会被执行。在某个时刻，它会调用链中的下一个过滤器，然后是下一个，依此类推。当最后一个过滤器（始终是 sfExecutionFilter）被执行时，前一个过滤器才能结束，依此类推，直到渲染过滤器。图 6-3 用序列图说明了这一想法，使用了一个人为缩小的过滤器链（实际链包含更多过滤器）。

### 图 6-3 - 示例过滤器链

![](img/0f886a7f4cbcc3939be96e985ca35ff4_91_0.png)

此过程证明了过滤器类结构的合理性。它们都扩展 sfFilter 类，并包含一个 execute() 方法，该方法期望 $filterChain 对象作为参数。在此方法的某处，过滤器通过调用 $filterChain->execute() 将控制权传递给链中的下一个过滤器。有关示例，请参见清单 6-26。基本上，过滤器分为两部分：

- 对 $filterChain->execute() 的调用之前的代码在动作执行之前执行。
- 对 $filterChain->execute() 的调用之后的代码在动作执行之后、呈现之前执行。

### 清单 6-26 - 过滤器类结构

```php
class myFilter extends sfFilter
{
  public function execute($filterChain)
  {
    // Code to execute before the action execution
    ...

    // Execute next filter in the chain
    $filterChain->execute();

    // Code to execute after the action execution, before the rendering
    ...
  }
}
```

默认过滤器链在名为 filters.yml 的应用程序配置文件中定义，如清单 6-27 所示。此文件列出了要针对每个请求执行的过滤器。

### 清单 6-27 - 默认过滤器链，在 frontend/config/filters.yml

```yaml
rendering: ~
security: ~

# Generally, you will want to insert your own filters here

cache: ~
execution: ~
```

这些声明没有参数（波浪号字符 ~ 在 YAML 中表示“null”），因为它们继承了 Symfony 核心中定义的参数。在核心中，Symfony 为每个过滤器定义了 class 和 param 设置。例如，清单 6-28 显示了渲染过滤器的默认参数。

### 清单 6-28 - 渲染过滤器的默认参数，在 sfConfig::get('sf_symfony_lib_dir')/config/config/filters.yml

```yaml
rendering:
  class: sfRenderingFilter   # Filter class
  param:                     # Filter parameters
    type: rendering
```

通过在应用程序的 filters.yml 中留空值（~），你告诉 Symfony 使用核心中定义的默认设置应用过滤器。

你可以通过多种方式自定义过滤器链：

- 通过添加 enabled: false 参数从链中禁用某些过滤器。例如，要禁用安全过滤器，请写入：

```
security:
  enabled: false
```

- 不要从 filters.yml 中删除条目来禁用过滤器；Symfony 在这种情况下会抛出异常。

- 在链中的某个位置（通常在安全过滤器之后）添加你自己的声明以添加自定义过滤器（如下一节所述）。请注意，渲染过滤器必须是第一个条目，执行过滤器必须是过滤器链的最后一个条目。

- 重写默认过滤器的默认类和参数（特别是为了修改安全系统并使用你自己的安全过滤器）。

## 构建你自己的过滤器

构建过滤器非常简单。创建一个类定义，类似于清单 6-26 所示的，并将其放在项目的某个 lib/ 文件夹中，以利用自动加载功能。

由于动作可以转发或重定向到另一个动作，从而重新启动完整的过滤器链，你可能希望将你自己的过滤器执行限制在请求的第一个动作调用上。sfFilter 类的 isFirstCall() 方法为此目的返回一个布尔值。此调用仅在动作执行之前才有意义。

通过示例，这些概念会更清晰。清单 6-29 显示了一个用于自动登录带有特定 MyWebSite Cookie 的用户的过滤器，该 Cookie 据说是由登录动作创建的。这是一种简单但可行的方式，用于实现登录表单中提供的“记住我”功能。

### 清单 6-29 - 示例过滤器类文件，保存在 apps/frontend/lib/rememberFilter.class.php

```php
class rememberFilter extends sfFilter
{
  public function execute($filterChain)
  {
      // Execute this filter only once
      if ($this->isFirstCall())
      {
          // Filters don't have direct access to the request and user objects.
          // You will need to use the context object to get them
          $request = $this->getContext()->getRequest();
          $user = $this->getContext()->getUser();

          if ($request->getCookie('MyWebSite'))
          {
              // sign in
              $user->setAuthenticated(true);
          }
      }

      // Execute next filter
      $filterChain->execute();
  }
}
```

在某些情况下，而不是继续执行过滤器链，你需要在过滤器末尾转发到特定动作。sfFilter 没有 forward() 方法，但 sfController 有，因此你可以通过调用以下内容轻松实现：

```
return $this->getContext()->getController()->forward('mymodule',
'myAction');
```

> sfFilter 类具有一个 initialize() 方法，在创建过滤器对象时执行。如果你需要以自己的方式处理过滤器参数（如下一节所述，在 filters.yml 中定义），可以在自定义过滤器中重写它。

## 过滤器激活和参数

仅创建过滤器文件不足以激活它。你需要将过滤器添加到过滤器链中，为此，必须在位于应用程序或模块 config/ 目录中的 filters.yml 中声明过滤器类，如清单 6-30 所示。

### 清单 6-30 - 示例过滤器激活文件，保存在 apps/frontend/config/filters.yml

```yaml
rendering: ~
security: ~

remember:
    # Filters need a unique name
    class: rememberFilter
    param:
        cookie_name: MyWebSite
        condition: %APP_ENABLE_REMEMBER_ME%

cache: ~
execution: ~
```

激活后，过滤器会针对每个请求执行。过滤器配置文件可以在 param 键下包含一个或多个参数定义。过滤器类具有


能够使用 getParameter() 方法获取这些参数的值。清单 6-31 演示了如何获取过滤器参数值。

```
Listing 6-31 - Getting the Parameter Value, in apps/frontend/lib/rememberFilter.class.php

class rememberFilter extends sfFilter
{
    public function execute($filterChain)
    {
        // ...

        if ($request->getCookie($this->getParameter('cookie_name')))
        {
            // ...
        }

        // ...
    }
}
```

过滤器链会测试条件参数，以查看是否必须执行过滤器。因此，您的过滤器声明可以依赖于应用程序配置，就像清单 6-30 中的一样。只有当您的应用程序 app.yml 显示以下内容时，才会执行 remember 过滤器：

```
all:
  enable_remember_me: true
```

## 示例过滤器

过滤器功能对于在每个操作中重复代码很有用。例如，如果您使用远程分析系统，您可能需要在每个页面中放置一段调用远程跟踪脚本的代码片段。您可以将此代码放在全局布局中，但这样它将对整个应用程序生效。或者，您可以将其放在过滤器中，例如清单 6-32 所示的过滤器，并按模块基础激活它。

```
Listing 6-32 - Google Analytics Filter

class sfGoogleAnalyticsFilter extends sfFilter
{
    public function execute($filterChain)
    {
        // Nothing to do before the action
        $filterChain->execute();

        // Decorate the response with the tracker code
        $googleCode = '
<script src="http://www.google-analytics.com/urchin.js" type="text/javascript">
</script>
<script type="text/javascript">
_uacct="UA-'.$this->getParameter('google_id').'";urchinTracker();
</script>';
        $response = $this->getContext()->getResponse();
        $response->setContent(str_ireplace('</body>',
        $googleCode.'</body>',$response->getContent()));
    }
}
```

请注意，此过滤器并不完美，因为它不应将跟踪器添加到不是 HTML 的响应中。

另一个示例是将请求切换到 SSL（如果尚未切换）的过滤器，以保护通信，如清单 6-33 所示。

### 清单 6-33 - 安全通信过滤器

```
class sfSecureFilter extends sfFilter
{
    public function execute($filterChain)
    {
        $context = $this->getContext();
        $request = $context->getRequest();

        if (!$request->isSecure())
        {
            $secure_url = str_replace('http', 'https', $request->getUri());

            return $context->getController()->redirect($secure_url);
            // We don't continue the filter chain
        }
        else
        {
            // The request is already secure, so we can continue
            $filterChain->execute();
        }
    }
}
```

过滤器在插件中被广泛使用，因为它们允许您全局扩展应用程序的功能。有关插件的更多信息，请参阅第 17 章。

## 模块配置

少数模块行为依赖于配置。要修改它们，您必须在模块的 config/ 目录中创建 module.yml 文件，并按环境定义设置（或在 all: 标题下为所有环境定义）。清单 6-34 显示了 mymodule 模块的 module.yml 文件示例。

### 清单 6-34 - 模块配置，位于 apps/frontend/modules/mymodule/config/module.yml

```
all:   # For all environments
  enabled:        true
  is_internal:    false
  view_class:     sfPHP
  partial_view_class: sf
```

enabled 参数允许您禁用模块的所有操作。所有操作都将重定向到 module_disabled_module/module_disabled_action 操作（如 settings.yml 中定义）。

is_internal 参数允许您将模块所有操作的执行限制为内部调用。例如，这对于邮件操作很有用，您必须能够从另一个操作调用它们来发送电子邮件，但不能从外部调用。

view_class 参数定义视图类。它必须继承自 sfView。覆盖此值允许您使用其他视图系统，配合其他模板引擎，例如 Smarty。

partial_view_class 参数定义用于此模块部分的视图类。它必须继承自 sfPartialView。

## 摘要

在 symfony 中，控制器层分为两部分：前置控制器（针对给定环境是应用程序的唯一入口）和操作（包含页面逻辑）。操作有能力通过返回 sfView 常量之一来确定其视图将如何执行。在操作内部，您可以操作上下文的不同元素，包括请求对象 (sfRequest) 和当前用户会话对象 (sfUser)。

结合会话对象、操作对象和安全配置的功能，symfony 提供了一个完整的安全系统，具有访问限制和凭据。如果 preExecute() 和 postExecute() 方法用于模块内的代码复用，那么过滤器通过使控制器代码针对每个请求执行，授权所有应用程序的相同复用性。

# 第 7 章

## 视图层内部

视图负责呈现与特定操作相关联的输出。在 symfony 中，视图由几个部分组成，每个部分都设计为通常与之打交道的人可以轻松修改。

- Web 设计师通常处理模板（当前操作数据的呈现）和布局（包含所有页面通用代码）。这些文件使用 HTML 编写，其中嵌入了少量 PHP 代码，大多是对辅助函数的调用。
- 为了复用性，开发人员通常将模板代码片段封装为部分或组件。他们使用插槽来影响布局中的多个区域。Web 设计师也可以处理这些模板片段。
- 开发人员关注 YAML 视图配置文件（设置响应和其他界面元素的属性）以及响应对象。在处理模板中的变量时，不得忽略跨站点脚本的风险，并且需要很好地理解输出转义技术才能安全地记录用户数据。

但无论您的角色是什么，您都会找到有用的工具来加快呈现操作结果这一繁琐工作。本章涵盖了所有这些工具。

## 模板

清单 7-1 显示了一个典型的 symfony 模板。它包含一些 HTML 代码和一些基本 PHP 代码，通常是对操作中定义的变量（通过 $this->name = 'foo';）和辅助函数的调用。

```
Listing 7-1 - A Sample indexSuccess.php Template

<h1>Welcome</h1>
<p>Welcome back, <?php echo $name ?>!</p>
<h2>What would you like to do?</h2>
<ul>
  <li><?php echo link_to('Read the last articles', 'article/read') ?></li>
  <li><?php echo link_to('Start writing a new one', 'article/write') ?></li>
</ul>
```

如第 4 章所述，替代 PHP 语法更适合模板，以便非 PHP 开发人员可以阅读。您应该在模板中尽量减少 PHP 代码，因为这些文件用于设计应用程序的 GUI，有时由另一团队创建和维护，该团队专注于呈现而不是应用程序逻辑。将逻辑保留在操作内部也使得为单个操作拥有多个模板变得更容易，而无需任何代码重复。

## 辅助函数

辅助函数是返回 HTML 代码并可在模板中使用的 PHP 函数。在清单 7-1 中，link_to() 函数是一个辅助函数。有时，辅助函数只是节省时间的工具，将模板中经常使用的代码片段打包。例如，您可以轻松想象此辅助函数的函数定义：

```
<?php echo image_tag('photo.jpg') ?>
=> <img src="http://www.symfony-project.org/images/photo.jpg" />
```

它应该看起来像清单 7-2。

### 清单 7-2 - 辅助函数定义示例

```
function image_tag($source)
{
  return '<img src="http://www.symfony-project.org/images/'.$source.'" />';
}
```

事实上，symfony 内置的 image_tag() 函数比这要复杂一些，因为它接受第二个参数来向  标签添加其他属性。您可以在在线 API 文档36 中查看其完整语法和选项。

大多数情况下，辅助函数承载智能并为您节省冗长复杂的代码：

```
<?php echo auto_link_text('Please visit our website www.example.com') ?>
=> Please visit our website <a
href="http://www.example.com">www.example.com</a>
```

辅助函数简化了编写模板的过程，并在性能和可访问性方面生成最佳的 HTML 代码。您始终可以使用纯 HTML，但辅助函数通常编写更快。

> 您可能会想知道，为什么辅助函数按照下划线语法命名，而不是使用 symfony 其他地方采用的 camelCase 约定。这是因为辅助函数是函数，而所有核心 PHP 函数都使用下划线语法约定。

### 声明辅助函数

包含辅助函数定义的 symfony 文件不会自动加载（因为它们包含函数而不是类）。辅助函数按用途分组。例如，所有处理文本的辅助函数都定义在名为 TextHelper.php 的文件中，称为 Text 辅助函数组。因此，如果您需要在模板中使用辅助函数，必须通过 use_helper() 函数在模板中较早的位置加载相关的辅助函数组。清单 7-3 显示了使用 auto_link_text() 辅助函数的模板，该辅助函数属于 Text 辅助函数组。

### 清单 7-3 - 声明使用辅助函数

```
// Use a specific helper group in this template
<?php use_helper('Text') ?>
...
<h1>Description</h1>
<p><?php echo auto_link_text($description) ?></p>
```

36. http://www.symfony-project.org/api/1.4/



如果需要声明多个助手组，请向 use_helper() 调用添加更多参数。例如，要在模板中加载 Text 和 Javascript 助手组，请调用 `<?php use_helper('Text', 'Javascript') ?>`。

每个模板中默认提供少量助手，无需声明。这些是以下助手组的助手：

- Helper：用于助手包含（实际上，use_helper() 函数本身就是一个助手）
- Tag：基本标签助手，几乎所有助手都使用它
- Url：链接和 URL 管理助手
- Asset：填充 HTML <head> 部分的助手，并提供指向外部资源（图片、JavaScript 和样式表文件）的便捷链接
- Partial：允许包含模板片段的助手
- Cache：缓存代码片段的操作助手

每个模板默认加载的标准助手列表可在 settings.yml 文件中配置。因此，如果你知道不会使用 Cache 组的助手，或者将始终使用 Text 组的助手，请相应地修改 standard_helpers 设置。这将稍微加快你的应用程序速度。你不能删除前面列表中的前四个助手组（Helper、Tag、Url 和 Asset），因为模板引擎正常工作需要它们。因此，它们甚至不出现在标准助手列表中。

如果需要在模板之外使用助手，你仍然可以通过调用 sfProjectConfiguration::getActive()->loadHelpers($helpers) 从任何位置加载助手组，其中 $helpers 是助手组名称或助手组名称数组。例如，如果你想在动作中使用 auto_link_text()，则需要先调用 sfProjectConfiguration::getActive()->loadHelpers('Text')。

## 常用助手

你将在后续章节中详细了解一些助手，与它们所辅助的功能相关。清单 7-4 简要列出了使用频率最高的默认助手，以及它们返回的 HTML 代码。

## 清单 7-4 - 常用默认助手

```
// Helper group
<?php use_helper('HelperName') ?>
<?php use_helper('HelperName1', 'HelperName2', 'HelperName3') ?>

// Url group
<?php echo link_to('click me', 'mymodule/myaction') ?>
=> <a href="/route/to/myaction">click me</a> // Depends on the routing settings

// Asset group
<?php echo image_tag('myimage', 'alt=foo size=200x100') ?>
=> <img src="http://www.symfony-project.org/images/myimage.png" alt="foo" width="200" height="100" />
<?php echo javascript_include_tag('myscript') ?>
=> <script language="JavaScript" type="text/javascript" src="http://www.symfony-project.org/js/myscript.js"></script>
<?php echo stylesheet_tag('style') ?>
=> <link href="/stylesheets/style.css" media="screen" rel="stylesheet" type="text/css" />
```

symfony 中还有许多其他助手，要详细描述所有助手需要一整本书。助手的最佳参考是在线 [API 文档](http://www.symfony-project.org/api/1_4/)，其中所有助手都有详细文档，包括语法、选项和示例。

## 添加你自己的助手

Symfony 自带了许多用于各种目的的助手，但如果你在 API 文档中找不到所需内容，可能会想要创建一个新助手。这非常容易实现。

助手函数（返回 HTML 代码的常规 PHP 函数）应保存为名为 FooBarHelper.php 的文件，其中 FooBar 是助手组的名称。将文件存储在 apps/frontend/lib/helper/ 目录中（或存储在项目中任意 lib/ 文件夹下的 helper/ 目录中），以便 use_helper('FooBar') 助手可以自动找到它并包含。

> 此系统甚至允许你覆盖现有的 symfony 助手。例如，要重新定义 Text 助手组的所有助手，只需在 apps/frontend/lib/helper/ 目录中创建一个 TextHelper.php 文件。每当你调用 use_helper('Text') 时，symfony 将使用你的助手组而非其自身的助手组。但请注意：由于原始文件甚至不会被加载，你必须重新定义助手组的所有函数才能覆盖它；否则，某些原始助手将完全不可用。

## 页面布局

清单 7-1 所示的模板不是有效的 XHTML 文档。缺少 DOCTYPE 定义以及 <html> 和 <body> 标签。这是因为它们存储在应用程序的其他位置，即名为 layout.php 的文件中，该文件包含页面布局。该文件也称为全局模板，存储了应用程序所有页面共有的 HTML 代码，以避免在每个模板中重复编写。模板的内容集成到布局中，或者，如果你改变视角，布局“装饰”模板。这是装饰器设计模式的应用，如图 7-1 所示。

> 有关装饰器和其他设计模式的更多信息，请参阅 Martin Fowler 编著的《企业应用架构模式》（Addison-Wesley 出版，ISBN: 0-32112-742-0）。

## 图 7-1 - 使用布局装饰模板

![](img/0f886a7f4cbcc3939be96e985ca35ff4_100_0.png)

清单 7-5 显示了默认页面布局，位于应用程序 templates/ 目录中。

## 清单 7-5 - 默认布局，位于 myproject/apps/frontend/templates/layout.php

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <?php include_javascripts() ?>
  <?php include_stylesheets() ?>
  <?php include_http_metas() ?>
  <?php include_metas() ?>
  <?php include_title() ?>
  <link rel="shortcut icon" href="/favicon.ico" />
</head>
<body>
  <?php echo $sf_content ?>
</body>
</html>
```

在 <head> 部分中调用的助手会从响应对象和视图配置中获取信息。<body> 标签输出模板的结果。使用此布局、默认配置以及清单 7-1 中的示例模板，处理后的视图如清单 7-6 所示。

## 清单 7-6 - 布局、视图配置和模板的组合

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <meta name="title" content="symfony project" />
  <meta name="robots" content="index, follow" />
  <meta name="description" content="symfony project" />
  <meta name="keywords" content="symfony, project" />
  <title>symfony project</title>
  <link rel="stylesheet" type="text/css" href="/css/main.css" />
  <link rel="shortcut icon" href="/favicon.ico">
</head>
<body>
  <h1>Welcome</h1>
  <p>Welcome back, <?php echo $name ?>!</p>
  <h2>What would you like to do?</h2>
  <ul>
    <li><?php echo link_to('Read the last articles', 'article/read') ?>
    </li>
    <li><?php echo link_to('Start writing a new one', 'article/write') ?>
    </li>
  </ul>
</body>
</html>
```

全局模板可以针对每个应用程序完全自定义。添加所需的任何 HTML 代码。此布局通常用于保存站点导航、徽标等。你甚至可以拥有多个布局，并决定每个动作应使用哪个布局。暂时不要担心 JavaScript 和样式表包含；本章稍后的“视图配置”部分将介绍如何处理。

## 模板快捷方式

在模板中，始终可用一些 symfony 变量。这些快捷方式通过核心 symfony 对象，提供对模板中最常用信息的访问：

- $sf_context：整个上下文对象（sfContext 的实例）
- $sf_request：请求对象（sfRequest 的实例）
- $sf_params：请求对象的参数
- $sf_user：当前用户会话对象（sfUser 的实例）

上一章详细介绍了 sfRequest 和 sfUser 对象的有用方法。你可以实际上在模板中通过 $sf_request 和 $sf_user 变量调用这些方法。例如，如果请求包含 total 参数，其值可在模板中通过以下方式获取：

```
// Long version
<?php echo $sf_request->getParameter('total') ?>

// Shorter version
<?php echo $sf_params->get('total') ?>

// Equivalent to the following action code
echo $request->getParameter('total')
```

## 代码片段

你可能经常需要在多个页面中包含一些 HTML 或 PHP 代码。为了避免重复代码，大多数时候 PHP include() 语句就足够了。

例如，如果应用程序的许多模板需要使用相同的代码片段，请将其保存为名为 myFragment.php 的文件，放在全局模板目录（myproject/apps/frontend/templates/）中，并在模板中按如下方式包含：

```
<?php include(sfConfig::get('sf_app_template_dir').'/myFragment.php') ?>
```

但这不是打包片段的非常干净的方法，主要原因是片段与包含它的各种模板之间可能有不同的变量名。此外，symfony 缓存系统（第 12 章中描述）无法检测 include，因此片段无法独立于模板进行缓存。Symfony 提供了三种替代的智能代码片段类型来替换 include：

- 如果逻辑较轻量，你只需包含一个可访问你传递给它的某些数据的模板文件。为此，你将使用 partial。
- 如果逻辑较重（例如，如果你需要访问数据模型和/或根据会话修改内容），你将更倾向于将展示与逻辑分开。为此，你将使用 component。
- 如果片段旨在替换布局的特定部分，而该部分可能已有默认内容，你将使用 slot。

这些片段的包含由 Partial 组的助手实现。这些助手可从任何 symfony 模板使用，无需初始声明。

## Partials

Partial 是可重复使用的模板代码块。例如，在出版应用程序中，显示文章的模板代码用于文章详细信息页面，也用于文章列表中。



最佳文章列表和最新文章列表。这段代码非常适合作为 partial，如图 7-2 所示。

## 图 7-2 - 在模板中重用 partials

![](img/0f886a7f4cbcc3939be96e985ca35ff4_103_0.png)

和模板一样，partials 是位于 templates/ 目录下的文件，包含嵌入 PHP 的 HTML 代码。partial 文件名始终以下划线 (_) 开头，这有助于将 partials 与模板区分开来，因为它们位于同一个 templates/ 文件夹中。

模板可以包含 partials，无论它们位于同一模块、另一个模块还是全局 templates/ 目录中。使用 include_partial() 辅助函数来包含 partial，并将模块名和 partial 名作为参数指定（但省略前导下划线和尾部 .php），如清单 7-7 所示。

### 清单 7-7 - 在 mymodule 模块的模板中包含 Partial

```php
// Include the frontend/modules/mymodule/templates/_mypartial1.php partial
// As the template and the partial are in the same module,
// you can omit the module name
<?php include_partial('mypartial1') ?>

// Include the frontend/modules/foobar/templates/_mypartial2.php partial
// The module name is compulsory in that case
<?php include_partial('foobar/mypartial2') ?>

// Include the frontend/templates/_mypartial3.php partial
// It is considered as part of the 'global' module
<?php include_partial('global/mypartial3') ?>
```

partials 可以访问常见的 symfony 辅助函数和模板快捷方式。但是，由于 partials 可以从应用程序的任何地方调用，它们无法自动访问在调用包含它们的模板的动作中定义的变量，除非显式地作为参数传递。例如，如果您希望 partial 可以访问 $total 变量，动作必须将其传递给模板，然后由模板将其作为 include_partial() 调用的第二个参数传递给辅助函数，如清单 7-8、7-9 和 7-10 所示。

### 清单 7-8 - 动作定义变量，位于 mymodule/actions/actions.class.php

```php
class mymoduleActions extends sfActions
{
  public function executeIndex()
  {
    $this->total = 100;
  }
}
```

### 清单 7-9 - 模板将变量传递给 Partial，位于 mymodule/templates/indexSuccess.php

```php
<p>Hello, world!</p>
<?php include_partial('mypartial', array('mytotal' => $total)) ?>
```

### 清单 7-10 - Partial 现在可以使用该变量，位于 mymodule/templates/_mypartial.php

```php
<p>Total: <?php echo $mytotal ?></p>
```

目前为止所有辅助函数都通过 <?php echo functionName() ?> 调用。但是 partial 辅助函数只是通过 <?php include_partial() ?> 调用，不带 echo，以便其行为类似于常规的 PHP include() 语句。如果您需要一个返回 partial 内容但不实际显示它的函数，请改用 get_partial()。本章中描述的所有 include_helpers 都有对应的 get_counterpart，可以与 echo 语句一起调用。

提示：动作不仅可以生成模板，还可以返回 partial 或 component。动作类的 renderPartial() 和 renderComponent() 方法有助于提高代码可重用性。此外，它们利用了 partials 的缓存功能（参见第 12 章）。动作中定义的变量将自动传递给 partial/component，除非您将变量关联数组作为方法的第二个参数定义。

```php
public function executeFoo()
{
 // do things
 $this->foo = 1234;
 $this->bar = 4567;

 return $this->renderPartial('mymodule/mypartial');
}
```

在此示例中，partial 将可以访问 $foo 和 $bar。如果动作以以下行结尾：

```php
return $this->renderPartial('mymodule/mypartial', array('foo' =>
$this->foo));
```

那么 partial 将只能访问 $foo。

## 组件

在第 2 章中，第一个示例脚本被分成两部分，以将逻辑与表示分开。就像 MVC 模式适用于动作和模板一样，您可能需要将 partial 分为逻辑部分和表示部分。在这种情况下，您应该使用组件。

组件类似于动作，但速度快得多。组件的逻辑保存在继承自 sfComponents 的类中，位于 actions/components.class.php 文件。其表示保存在 partial 中。sfComponents 类的方法以单词 execute 开头，与动作一样，它们可以以动作传递变量的相同方式将变量传递给其表示部分。用作组件表示的 partial 以组件命名（不带前导 execute，而是使用下划线）。表 7-1 比较了动作和组件的命名约定。

### 表 7-1 - 动作和组件命名约定

| 约定 | 动作 | 组件 |
| --- | --- | --- |
| 逻辑文件 | actions.class.php | components.class.php |
| 逻辑类继承 | sfActions | sfComponents |
| 方法命名 | executeMyAction() | executeMyComponent() |
| 表示文件命名 | myActionSuccess.php | _myComponent.php |

> 就像您可以拆分动作文件一样，sfComponents 类有 sfComponent 对应物，允许使用相同语法的单个组件文件。

例如，假设您有一个侧边栏，显示给定主题的最新新闻头条，具体取决于用户个人资料，并且在多个页面中重复使用。获取新闻头条所需的查询太复杂，无法出现在简单的 partial 中，因此需要将其移动到类似于动作的文件——组件中。图 7-3 说明了此示例。

对于此示例，如清单 7-11 和 7-12 所示，组件将保存在其自己的模块（称为 news）中，但如果从功能角度来看合理，您可以在单个模块中混合组件和动作。

### 图 7-3 - 在模板中使用组件

![](img/0f886a7f4cbcc3939be96e985ca35ff4_105_0.png)

### 清单 7-11 - 组件类，位于 modules/news/actions/components.class.php

```php
<?php

class newsComponents extends sfComponents
{
    public function executeHeadlines()
    {
        // Propel
        $c = new Criteria();
        $c->addDescendingOrderByColumn(NewsPeer::PUBLISHED_AT);
        $c->setLimit(5);
        $this->news = NewsPeer::doSelect($c);

        // Doctrine
        $query = Doctrine::getTable('News')
        ->createQuery()
        ->orderBy('published_at DESC')
        ->limit(5);

        $this->news = $query->execute();
    }
}
```

### 清单 7-12 - Partial，位于 modules/news/templates/_headlines.php

```php
<div>
<h1>Latest news</h1>
<ul>
<?php foreach($news as $headline): ?>
<li>
<?php echo $headline->getPublishedAt() ?>
<?php echo link_to($headline->getTitle(), 'news/show?id='.$headline->getId()) ?>
</li>
<?php endforeach ?>
</ul>
</div>
```

现在，每次在模板中需要组件时，只需调用此内容：

```php
<?php include_component('news', 'headlines') ?>
```

与 partials 一样，组件接受以关联数组形式的其他参数。参数按名称在 partial 中可用，并在组件中通过 $this 对象可用。请参见清单 7-13 获取示例。

### 清单 7-13 - 将参数传递给组件及其模板

```php
// Call to the component
<?php include_component('news', 'headlines', array('foo' => 'bar')) ?>

// In the component itself
echo $this->foo;
=> 'bar'

// In the _headlines.php partial
echo $foo;
=> 'bar'
```

您可以将组件包含在组件中，或在全局布局中，就像任何常规模板一样。与动作一样，组件的 execute 方法可以将变量传递给相关 partial 并可以访问相同的快捷方式。但是，相似之处到此为止。组件不处理安全性或验证，无法从 Internet 调用（只能从应用程序本身调用），并且没有各种返回可能性。这就是为什么组件的执行速度比动作快。

## 插槽

partials 和组件非常适合重用性。但是，在许多情况下，需要代码片段来填充布局中不止一个动态区域。例如，假设您想根据动作的内容在布局的 <head> 部分中添加一些自定义标签。或者，假设布局有一个主要动态区域，由动作的结果填充，还有许多其他较小的区域，它们在布局中定义了默认内容，但可以在模板级别被覆盖。

对于这些情况，解决方案是插槽。基本上，插槽是一个占位符，您可以将其放在任何视图元素中（在布局、模板或 partial 中）。填充此占位符就像设置变量一样。填充代码在响应中全局存储，因此您可以在任何地方定义它（在布局、模板或 partial 中）。只需确保在包含它之前定义插槽，并记住布局在模板之后执行（这是 the


装饰过程），部分模板在模板中调用时执行。这听起来太抽象了吗？让我们看一个例子。

想象一个布局，包含一个用于模板的区域和两个插槽：一个用于侧边栏，另一个用于页脚。插槽值在模板中定义。在装饰过程中，布局代码会包装模板代码，插槽会用之前定义的值填充，如图 7-4 所示。侧边栏和页脚随后可以相对于主操作具有上下文。这就像拥有一个带有不止一个“洞”的布局。

图 7-4 - 在模板中定义的布局插槽

![](img/0f886a7f4cbcc3939be96e985ca35ff4_107_0.png)

查看一些代码将进一步澄清问题。要包含一个插槽，请使用 include_slot() 辅助函数。如果插槽之前已定义，has_slot() 辅助函数将返回 true，作为额外好处提供回退机制。例如，在布局中为 'sidebar' 插槽定义占位符及其默认内容，如清单 7-14 所示。

清单 7-14 - 在布局中包含 'sidebar' 插槽

```php
<div id="sidebar">
<?php if (has_slot('sidebar')): ?>
    <?php include_slot('sidebar') ?>
<?php else: ?>
    <!-- default sidebar code -->
    <h1>Contextual zone</h1>
    <p>This zone contains links and information
    relative to the main content of the page.</p>
<?php endif; ?>
</div>
```

如果未定义插槽，显示一些默认内容是很常见的，include_slot 辅助函数返回一个布尔值，指示插槽是否已定义。清单 7-15 展示了如何考虑此返回值来简化代码。

清单 7-15 - 在布局中包含 'sidebar' 插槽

```php
<div id="sidebar">
<?php if (!include_slot('sidebar')): ?>
    <!-- default sidebar code -->
    <h1>Contextual zone</h1>
    <p>This zone contains links and information
    relative to the main content of the page.</p>
<?php endif; ?>
</div>
```

每个模板都能定义插槽的内容（实际上，即使是部分模板也能做到）。由于插槽旨在保存 HTML 代码，symfony 提供了一种方便的方式来定义它们：只需在 slot() 和 end_slot() 辅助函数调用之间编写插槽代码，如清单 7-16 所示。

清单 7-16 - 在模板中覆盖 'sidebar' 插槽内容

```php
// ...
<?php slot('sidebar') ?>

<!-- custom sidebar code for the current template-->
<h1>User details</h1>
<p>name: <?php echo $user->getName() ?></p>
<p>email: <?php echo $user->getEmail() ?></p>
<?php end_slot() ?>
```

slot 辅助函数之间的代码在模板上下文中执行，因此可以访问在操作中定义的所有变量。Symfony 会自动将此代码的结果放入响应对象中。它不会在模板中显示，而是可用于未来的 include_slot() 调用，例如清单 7-14 中的调用。

插槽非常适合定义用于显示上下文内容的区域。它们还可用于仅为某些操作向布局添加 HTML 代码。例如，显示最新新闻列表的模板可能希望在布局的 <head> 部分添加一个 RSS 订阅源链接。只需在布局中添加一个 'feed' 插槽并在列表的模板中覆盖它即可实现。

如果插槽内容非常短，例如定义标题插槽时的情况，您可以简单地将内容作为 slot() 方法的第二个参数传递，如清单 7-17 所示。

清单 7-17 - 使用 slot() 定义短值

```php
<?php slot('title', 'The title value') ?>
```

## 在哪里查找模板片段

使用模板的人通常是网页设计师，他们可能不太了解 symfony，并且可能难以找到模板片段，因为这些片段可能散布在整个应用程序中。以下指南将使他们更熟悉 symfony 模板系统。

首先，虽然 symfony 项目包含许多目录，但所有布局、模板和模板片段文件都位于名为 templates/ 的目录中。就网页设计师而言，项目结构可以简化为如下所示：

```
myproject/
apps/
application1/
templates/	# Layouts for application 1
modules/
module1/
templates/	# Templates and partials for module 1
module2/
templates/	# Templates and partials for module 2
module3/
templates/	# Templates and partials for module 3
```

所有其他目录均可忽略。

遇到 include_partial() 时，网页设计师只需了解第一个参数很重要。该参数的模式是 module_name/partial_name，这意味着表示代码位于 modules/module_name/templates/_partial_name.php。

对于 include_component() 辅助函数，模块名和 partial 名是前两个参数。至于其余部分，对辅助函数是什么以及模板中最常用的辅助函数有大致了解，就足以开始为 symfony 应用程序设计模板了。

## 视图配置

在 symfony 中，视图由两个不同的部分组成：

- 操作结果的 HTML 表示（存储在模板、布局和模板片段中）
- 其余所有内容，包括以下内容：
  - Meta 声明：关键字、描述或缓存持续时间。
  - 页面标题：不仅可以帮助打开多个浏览器窗口的用户找到您的页面，而且对于搜索网站的索引也非常重要。
  - 文件包含：JavaScript 和样式表文件。
  - 布局：某些操作需要自定义布局（弹出窗口、广告等）或根本不需要布局（例如 Ajax 操作）。

在视图中，所有非 HTML 的内容都称为视图配置，symfony 提供两种操作方式。通常的方式是通过 view.yml 配置文件。当值不依赖于上下文或数据库查询时，可以使用它。当需要设置动态值时，替代方法是在操作中直接通过 sfResponse 对象属性设置视图配置。

> 如果您同时通过 sfResponse 对象和 view.yml 文件设置了视图配置参数，则 sfResponse 定义优先。

### view.yml 文件

每个模块可以有一个 view.yml 文件来定义其视图的设置。这允许您在单个文件中为整个模块和每个视图定义视图设置。view.yml 文件的一级键是模块视图名称。清单 7-18 显示了视图配置示例。

清单 7-18 - 模块级 view.yml 示例

```yaml
editSuccess:
  metas:
    title: Edit your profile

editError:
  metas:
    title: Error in the profile edition

all:
  stylesheets: [my_style]
  metas:
    title: My website
```

> 请注意，view.yml 文件中的主键是视图名称，而不是操作名称。作为提醒，视图名称由操作名称和操作终止组成。例如，如果 edit 操作返回 sfView::SUCCESS（或根本不返回任何内容，因为它是默认操作终止），则视图名称是 editSuccess。

模块的默认设置在模块 view.yml 的 all: 键下定义。所有应用程序视图的默认设置在应用程序 view.yml 中定义。再次，您识别了配置级联原则：

- 在 apps/frontend/modules/mymodule/config/view.yml 中，每个视图的定义仅适用于一个视图并覆盖模块级定义。
- 在 apps/frontend/modules/mymodule/config/view.yml 中，all: 定义适用于模块的所有操作并覆盖应用程序级定义。
- 在 apps/frontend/config/view.yml 中，default: 定义适用于应用程序的所有模块和所有操作。

> > 默认情况下不存在模块级 view.yml 文件。第一次需要为模块调整视图配置参数时，您需要在其 config/ 目录中创建一个空的 view.yml。

在查看清单 7-5 中的默认模板和清单 7-6 中的最终响应示例后，您可能想知道标题值来自哪里。事实上，它们是默认视图设置，定义在应用程序 view.yml 中，如清单 7-19 所示。

清单 7-19 - 默认应用程序级视图配置，在 apps/frontend/config/view.yml 中

```yaml
default:
  http_metas:
    content-type: text/html

  metas:
    #title:         symfony project
    #description:   symfony project
    #keywords:      symfony, project
    #language:      en
    #robots:        index, follow

  stylesheets:    [main]

  javascripts:    []

  has_layout:     true
  layout:         layout
```

这些设置中的每一项将在“视图配置设置”部分中详细描述。

### 响应对象

虽然属于视图层的一部分，但响应对象通常由操作修改。操作可以通过 getResponse() 方法访问名为 sfResponse 的 symfony 响应对象。清单 7-20 列出了在操作中经常使用的一些 sfResponse 方法。

清单 7-20 - 操作可以访问 sfResponse 对象方法

```php
class mymoduleActions extends sfActions
{
  public function executeIndex()
  {
    $response = $this->getResponse();

    // HTTP headers
    $response->setContentType('text/xml');
    $response->setHttpHeader('Content-Language', 'en');
    $response->setStatusCode(403);
    $response->addVaryHttpHeader('Accept-Language');
  }
}
```



```
$response->addCacheControlHttpHeader('no-cache');

// Cookies
$response->setCookie($name, $content, $expire, $path, $domain);

// Metas and page headers
$response->addMeta('robots', 'NONE');
$response->addMeta('keywords', 'foo bar');
$response->setTitle('My FooBar Page');
$response->addStyleSheet('custom_style');
$response->addJavaScript('custom_behavior');
}
}
```

除此处所示的设值方法外，sfResponse 类还有获取方法，用于返回响应属性的当前值。

在 symfony 中，设置头部的方法非常强大。头部会尽可能晚地发送（在 sfRenderingFilter 中），因此你可以随心所欲地修改它们，并且可以在尽可能晚的时候修改。它们还提供了非常有用的快捷方式。例如，如果你在调用 setContentType() 时未指定字符集，symfony 会自动添加 settings.yml 文件中定义的默认字符集。

```
Listing 7-29
$response->setContentType('text/xml');
echo $response->getContentType();
=> 'text/xml; charset=utf-8'
```

symfony 中响应的状态码符合 HTTP 规范。异常返回状态码 500，找不到页面返回状态码 404，正常页面返回状态码 200，未修改的页面可以减少为带有状态码 304 的简单头部（详情见第 12 章），等等。但你可以通过在动作中使用 setStatusCode() 响应方法设置自己的状态码来覆盖这些默认值。你可以指定自定义代码和自定义消息，或者仅指定自定义代码——在这种情况下，symfony 会为该代码添加最常见的消息。

```
Listing 7-30
$response->setStatusCode(404, 'This page does not exist');
```

> 在发送头部之前，symfony 会规范它们的名称。因此，你无需担心在调用 setHttpHeader() 时应写 content-language 还是 Content-Language，因为 symfony 会理解前者并自动将其转换为后者。

## 视图配置设置

你可能已经注意到，视图配置设置分为两种：

- 具有唯一值的设置（值在 view.yml 文件中是字符串，响应针对这些设置使用 set 方法）
- 具有多个值的设置（view.yml 对这些设置使用数组，响应使用 add 方法）

请记住，配置级联会擦除唯一值设置，但会累加多个值设置。随着你深入本章，这一点会变得更加明显。

## Meta 标记配置

响应中 <meta> 标记里写入的信息不会在浏览器中显示，但对机器人和搜索引擎很有用。它还控制每个页面的缓存设置。在 view.yml 的 http_metas: 和 metas: 键下定义这些标记，如清单 7-21 所示，或在动作中使用 addHttpMeta() 和 addMeta() 响应方法，如清单 7-22 所示。

### 清单 7-21 - view.yml 中的键值对形式的 Meta 定义

```
http_metas:
cache-control: public

metas:
description: Finance in France
keywords: finance, France
```

### 清单 7-22 - 动作中作为响应设置的 Meta 定义

```
$this->getResponse()->addHttpMeta('cache-control', 'public');
$this->getResponse()->addMeta('description', 'Finance in France');
$this->getResponse()->addMeta('keywords', 'finance, France');
```

默认情况下，添加已有的键会替换其当前内容。对于 HTTP Meta 标记，你可以添加第三个参数并将其设置为 false，这样 addHttpMeta() 方法（以及 setHttpHeader()）会将值追加到现有值中，而不是替换它。

```
$this->getResponse()->addHttpMeta('accept-language', 'en');
$this->getResponse()->addHttpMeta('accept-language', 'fr', false);
echo $this->getResponse()->getHttpHeader('accept-language');
=> 'en, fr'
```

为了让这些 Meta 标记出现在最终文档中，必须在 <head> 部分调用 include_http_metas() 和 include_metas() 辅助函数（默认布局中如此；参见清单 7-5）。symfony 会自动聚合所有 view.yml 文件（包括清单 7-18 中所示的默认文件）和响应属性中的设置，以输出正确的 <meta> 标记。清单 7-21 中的示例最终会显示如清单 7-23 所示。

### 清单 7-23 - 最终页面中输出的 Meta 标记

```
<meta http-equiv="content-type" content="text/html; charset=utf-8" />
<meta http-equiv="cache-control" content="public" />
<meta name="robots" content="index, follow" />
<meta name="description" content="Finance in France" />
<meta name="keywords" content="finance, France" />
```

此外，响应的 HTTP 头部也会受到 http-metas: 定义的影响，即使布局中没有 include_http_metas() 辅助函数，或者根本没有布局。例如，如果需要将页面作为纯文本发送，请定义以下 view.yml：

```
http_metas:
content-type: text/plain

has_layout: false
```

## 标题配置

页面标题是搜索引擎索引的关键部分。它也非常有助于提供标签页浏览功能的现代浏览器。在 HTML 中，标题既是页面的一个标签，也是元信息，因此 view.yml 文件将 title: 键视为 metas: 键的子项。清单 7-24 显示了 view.yml 中的标题定义，清单 7-25 显示了动作中的定义。

### 清单 7-24 - view.yml 中的标题定义

```
indexSuccess:
  metas:
    title: Three little piggies
```

### 清单 7-25 - 动作中的标题定义——允许动态标题

```
$this->getResponse()->setTitle(sprintf('%d little piggies', $number));
```

在最终文档的 <head> 部分中，如果存在 include_metas() 辅助函数，标题定义会设置 <meta name="title"> 标记；如果存在 include_title() 辅助函数，则会设置 <title> 标记。如果两者都已包含（如清单 7-5 中的默认布局所示），标题将在文档源中出现两次（参见清单 7-6），这是无害的。

> 处理标题定义的另一种方法是使用插槽，如上文所述。这种方法可以更好地将控制器与模板分离：标题属于视图，而不属于控制器。

## 文件包含配置

向视图添加特定样式表或 JavaScript 文件很容易，如清单 7-26 所示。

### 清单 7-26 - 资源文件包含

```
// In the view.yml
indexSuccess:
  stylesheets: [mystyle1, mystyle2]
  javascripts: [myscript]

// In the action
$this->getResponse()->addStylesheet('mystyle1');
$this->getResponse()->addStylesheet('mystyle2');
$this->getResponse()->addJavascript('myscript');

// In the Template
<?php use_stylesheet('mystyle1') ?>
<?php use_stylesheet('mystyle2') ?>
<?php use_javascript('myscript') ?>
```

在每种情况下，参数都是文件名。如果文件有逻辑扩展名（样式表为 .css，JavaScript 文件为 .js），可以省略它。如果文件有逻辑位置（样式表为 /css/，JavaScript 文件为 /js/），也可以省略它。symfony 足够智能，可以自行确定正确的扩展名或位置。

与 Meta 和标题定义一样，文件包含定义需要在模板或布局中使用 include_javascripts() 和 include_stylesheets() 辅助函数才能包含。这意味着，前面的设置将输出清单 7-27 中的 HTML 代码。

### 清单 7-27 - 文件包含结果

```
<head>
...
<link rel="stylesheet" type="text/css" media="screen" href="/css/mystyle1.css" />
<link rel="stylesheet" type="text/css" media="screen" href="/css/mystyle2.css" />
<script language="javascript" type="text/javascript"
src="http://www.symfony-project.org/js/myscript.js">
</script>
</head>
```

请记住，配置级联原则适用，因此在应用程序 view.yml 中定义的任何文件包含都会出现在应用程序的每个页面中。清单 7-28、7-29 和 7-30 演示了这一原则。

### 清单 7-28 - 示例应用程序 view.yml

```
default:
  stylesheets: [main]
```

### 清单 7-29 - 示例模块 view.yml

```
indexSuccess:
  stylesheets: [special]

all:
  stylesheets: [additional]
```

### 清单 7-30 - 生成的 indexSuccess 视图

```
<link rel="stylesheet" type="text/css" media="screen" href="/css/main.css" />
<link rel="stylesheet" type="text/css" media="screen" href="/css/additional.css" />
<link rel="stylesheet" type="text/css" media="screen" href="/css/special.css" />
```

如果需要删除高级别定义的文件，只需在低级别定义中在文件名前加上减号（-），如清单 7-31 所示。

### 清单 7-31 - 删除应用程序级别定义的文件的示例模块 view.yml

```
indexSuccess:
  stylesheets: [-main, special]

all:
  stylesheets: [additional]
```

要删除所有样式表或 JavaScript 文件，请使用 -* 作为文件名，如清单 7-32 所示。

### 清单 7-32 - 删除应用程序级别定义的所有文件的示例模块 view.yml

```
indexSuccess:
  stylesheets: [-*]
  javascripts: [-*]
```





你可以更精确，并定义一个额外的参数来强制指定包含文件的位置（第一个或最后一个位置），如清单 7-33 所示。这适用于样式表和 JavaScript 文件。

## 清单 7-33 - 定义所包含资源的位置

```
// In the view.yml
indexSuccess:
  stylesheets: [special: { position: first }]

// In the action
$this->getResponse()->addStylesheet('special', 'first');

// In the template
```

你也可以决定绕过资源文件名的转换，以便生成的 <link> 或 <script> 标签引用精确指定的位置，如清单 7-34 所示。

## 清单 7-34 - 使用原始名称包含样式表

```
// In the view.yml
indexSuccess:
  stylesheets: [main, paper: { raw_name: true }]

// In the Action
$this->getResponse()->addStylesheet('main', '', array('raw_name' => true));

// In the template
true)) ?>

// Resulting View
<link rel="stylesheet" type="text/css" href="main" />
```

要为样式表包含指定媒体，可以更改默认的样式表标签选项，如清单 7-35 所示。

## 清单 7-35 - 带媒体的样式表包含

```
// In the view.yml
indexSuccess:
  stylesheets: [main, paper: { media: print }]

// In the Action
$this->getResponse()->addStylesheet('paper', '', array('media' =>
  'print'));

// In the template
'print')) ?>

// Resulting View
<link rel="stylesheet" type="text/css" media="print" href="/css/paper.css" />
```

> **关于使用 view.yml 文件包含资源的说明**
> 
> 最佳实践是在项目的 view.yml 文件中定义默认的样式表和 JavaScript 文件，并在模板中使用专用助手来包含特定的样式表或 JavaScript 文件。这样，你就不必删除或替换已包含的资源，在某些情况下这可能会很麻烦。

## 布局配置

根据网站的图形规范，你可能有多个布局。经典网站至少有两个：默认布局和弹出式布局。

你已经看到默认布局是 myproject/apps/frontend/templates/layout.php。其他布局必须添加到同一个全局 templates/ 目录中。如果你想让视图使用 frontend/templates/my_layout.php 文件，请使用清单 7-36 所示的语法。

```
Listing 7-36 - Layout Definition

// In view.yml
indexSuccess:
  layout: my_layout

// In the action
$this->setLayout('my_layout');

// In the template
<?php decorate_with('my_layout') ?>
```

某些视图根本不需要布局（例如，纯文本页面或 RSS 源）。在这种情况下，将 has_layout 设置为 false，如清单 7-37 所示。

```
Listing 7-37 - Layout Removal

// In `view.yml`
indexSuccess:
  has_layout: false

// In the Action
$this->setLayout(false);

// In the template
<?php decorate_with(false) ?>
```

> Ajax 操作视图默认没有布局。

## 输出转义

在模板中插入动态数据时，你必须确保数据的完整性。例如，如果数据来自匿名用户填写的表单，则存在包含旨在发起跨站脚本（XSS）攻击的恶意脚本的风险。你必须能够转义输出数据，以便其中包含的任何 HTML 标签都变得无害。

作为示例，假设用户在输入字段中填充了以下值：

```
<script>alert(document.cookie)</script>
```

如果你不谨慎地输出此值，JavaScript 将在每个浏览器上执行，并允许比仅显示警告框危险得多的攻击。这就是为什么你必须在显示之前转义该值，使其变成类似这样：

```
&lt;script&gt;alert(document.cookie)&lt;/script&gt;
```

你可以手动转义输出，将每个不确定的值包裹在 htmlspecialchars() 调用中，但这种方法非常重复且容易出错。相反，symfony 提供了一种名为输出转义的特殊系统，它会自动转义模板中输出的每个变量。它在应用程序的 settings.yml 中默认启用。

## 激活输出转义

输出转义在 settings.yml 文件中为应用程序全局配置。两个参数控制输出转义的工作方式：策略决定变量如何提供给视图，而方法是应用于数据的默认转义函数。

基本上，要激活输出转义，你只需将 escaping_strategy 参数设置为 true（这是默认值），如清单 7-38 所示。

清单 7-38 - 激活输出转义，在 frontend/config/settings.yml 中

```
all:
  .settings:
    escaping_strategy: true
    escaping_method:  ESC_SPECIALCHARS
```

这将默认将 htmlspecialchars() 添加到所有变量输出中。例如，假设你在操作中按如下方式定义测试变量：

```
$this->test = '<script>alert(document.cookie)</script>';
```

启用输出转义后，在模板中输出该变量将输出转义后的数据：

```
echo $test;
=> &lt;script&gt;alert(document.cookie)&lt;/script&gt;
```

此外，每个模板都可以访问 $sf_data 变量，它是引用所有转义变量的容器对象。因此，你也可以通过以下方式输出测试变量：

```
echo $sf_data->get('test');
=> &lt;script&gt;alert(document.cookie)&lt;/script&gt;
```

> $sf_data 对象实现了 Array 接口，因此你不必使用 $sf_data->get('myvariable')，而是可以通过调用 $sf_data['myvariable'] 来检索转义后的值。但它不是真正的数组，因此 print_r() 之类的函数不会按预期工作。

$sf_data 还允许你访问未转义或原始数据。当变量存储旨在由浏览器解释的 HTML 代码且你信任该变量时，这很有用。当你需要输出原始数据时，请调用 getRaw() 方法。

```
echo $sf_data->getRaw('test');
=> <script>alert(document.cookie)</script>
```

每当你需要包含 HTML 的变量真正作为 HTML 解释时，都必须访问原始数据。

当 escaping_strategy 为 false 时，$sf_data 仍然可用，但它始终返回原始数据。

## 转义助手

转义助手是返回输入转义版本的函数。它们可以作为 settings.yml 文件中的默认 escaping_method 提供，也可以用于为视图中特定值指定转义方法。可用的转义助手如下：

- ESC_RAW: 不转义该值。
- ESC_SPECIALCHARS: 将 PHP 函数 htmlspecialchars() 应用于输入。
- ESC_ENTITIES: 将 PHP 函数 htmlentities() 应用于输入，引用样式为 ENT_QUOTES。
- ESC_JS: 转义一个值以便放入将用作 HTML 的 JavaScript 字符串中。这对于使用 JavaScript 动态更改 HTML 的内容的转义非常有用。
- ESC_JS_NO_ENTITIES: 转义一个值以便放入 JavaScript 字符串中，但不添加实体。如果该值将使用对话框显示（例如，用于 javascript:alert(myString); 中的 myString 变量），这很有用。

## 转义数组和对象

输出转义不仅适用于字符串，还适用于数组和对象。任何是对象或数组的值都会将其转义状态传递给其子项。假设你的策略设置为 true，清单 7-39 演示了转义级联。

清单 7-39 - 转义也适用于数组和对象

```
// Class definition
class myClass
{
  public function testSpecialChars($value = '')
  {
    return '<'.$value.'>';
  }
}

// In the action
$this->test_array = array('&', '<', '>');
$this->test_array_of_arrays = array(array('&'));
$this->test_object = new myClass();

// In the template
<?php foreach($test_array as $value): ?>
<?php echo $value ?>
<?php endforeach; ?>
=> &amp; &lt; &gt;
<?php echo $test_array_of_arrays[0][0] ?>
=> &amp;
<?php echo $test_object->testSpecialChars('&') ?>
=> &lt;&amp;&gt;





事实上，模板中的变量并非你所期望的类型。输出转义系统会“装饰”它们并将其转换为特殊对象：

```
<?php echo get_class($test_array) ?>
=> sfOutputEscaperArrayDecorator
<?php echo get_class($test_object) ?>
=> sfOutputEscaperObjectDecorator
```

这就是为什么一些常用的 PHP 函数（如 array_shift()、print_r() 等）不再适用于转义后的数组。但它们仍然可以使用 [] 访问，使用 foreach 遍历，并且通过 count() 返回正确结果。而且在模板中，数据本应是只读的，因此大多数访问都将通过正常工作的方法进行。

你仍然可以通过 $sf_data 对象检索原始数据。此外，转义对象的方法已修改为接受一个额外参数：转义方法。因此，每次在模板中显示变量时，你都可以选择一种替代转义方法，或使用 ESC_RAW 辅助函数来禁用转义。示例请参见清单 7-40。

### 清单 7-40 - 转义对象的方法接受额外参数

```
<?php echo $test_object->testSpecialChars('&') ?>
=> &lt;&amp;&gt;
// The three following lines return the same value
<?php echo $test_object->testSpecialChars('&', ESC_RAW) ?>
<?php echo $sf_data->getRaw('test_object')->testSpecialChars('&') ?>
<?php echo $sf_data->get('test_object', ESC_RAW)->testSpecialChars('&') ?>
=> <&>
```

如果在模板中处理对象，你会大量使用这个额外参数技巧，因为这是在方法调用中获取原始数据的最快方式。

> 启用输出转义时，常规 symfony 变量也会被转义。因此请注意，$sf_user、$sf_request、$sf_param 和 $sf_context 仍然有效，但它们的方法会返回转义后的数据，除非在方法调用中将 ESC_RAW 作为最终参数添加。

> 尽管 XSS 是网站最常见的攻击手段之一，但这并非唯一的威胁。CSRF 同样很常见，symfony 提供了自动表单保护。你将在第 10 章中了解这种安全保护的工作原理。

## 总结

各种可用工具可操作表示层。得益于辅助函数，模板可在几秒钟内构建完成。布局、部分和组件兼具模块化和可重用性。视图配置利用 YAML 的速度来处理（大部分）页面标题。配置层叠使你无需为每个视图定义每个设置。对于取决于动态数据的每项表示修改，动作均可访问 sfResponse 对象。而且，得益于输出转义系统，视图免受 XSS 攻击。

# 第 8 章

## 模型层内部 (Doctrine)

迄今为止的大部分讨论都致力于构建页面以及处理请求和响应。但 Web 应用程序的业务逻辑主要依赖于其数据模型。Symfony 的默认模型组件基于对象/关系映射层。Symfony 自带了两种最流行的 PHP ORM：Propel37 和 Doctrine38。在 symfony 应用程序中，你通过对象访问和修改存储在数据库中的数据；从不显式地访问数据库。这保持了高度的抽象性和可移植性。

本章解释了如何创建对象数据模型，以及在 Doctrine 中访问和修改数据的方法。它还演示了 Doctrine 在 Symfony 中的集成。

如果你想使用 Propel 而非 Doctrine，请改为阅读附录 A，因为它包含完全相同的信息，但针对的是 Propel。

## 为什么使用 ORM 和抽象层？

数据库是关系型的。PHP 5 和 symfony 都是面向对象的。为了在面向对象的上下文中最有效地访问数据库，需要一个将对象逻辑转换为关系逻辑的接口。如第 1 章所述，此接口称为对象关系映射（ORM），它由提供数据访问并将业务规则封装在自身中的对象组成。

ORM 的主要优点是可重用性，允许从应用程序的各个部分（甚至不同的应用程序）调用数据对象的方法。ORM 层还封装了数据逻辑——例如，根据论坛用户的贡献数量及其受欢迎程度计算用户评级。当页面需要显示此类用户评级时，只需调用数据模型的方法，而无需担心计算细节。如果计算之后发生变化，你只需在模型中修改评级方法，其余应用程序保持不变即可。

使用对象而非记录、使用类而非表格，还有另一个好处：它们允许你向对象添加不一定与表中的列相匹配的新访问器。例如，如果你有一个名为 client 的表，其中包含 first_name 和 last_name 两个字段，你可能希望只需要一个 Name。在面向对象的世界中，只需向 Client 类添加一个新的访问器方法即可，如清单 8-1 所示。从应用程序的角度来看，Client 类的 FirstName、LastName 和 Name 属性之间没有区别。只有类本身可以确定哪些属性对应数据库列。

### 清单 8-1 - 模型类中的访问器掩盖了实际表结构

37. http://www.propelorm.org/

38. http://www.doctrine-project.org/

```
Listing 8-1
public function getName()
{
    return $this->getFirstName().' '.$this->getLastName();
}
```

所有重复的数据访问函数和数据本身的业务逻辑都可以保留在这样的对象中。假设你有一个 ShoppingCart 类，其中保存了 Items（即对象）。为了获取结账时的购物车总金额，请编写一个自定义方法来封装实际计算，如清单 8-2 所示。

### 清单 8-2 - 访问器掩盖了数据逻辑

```
Listing 8-2
public function getTotal()
{
    $total = 0;
    foreach ($this->getItems() as $item)
    {
        $total += $item->getPrice() * $item->getQuantity();
    }

    return $total;
}
```

构建数据访问过程时还需考虑另一个重要点：不同数据库厂商使用不同的 SQL 语法变体。切换到另一个数据库管理系统（DBMS）会迫使你重写为之前系统设计的部分 SQL 查询。如果你使用与数据库无关的语法构建查询，并将实际的 SQL 转译交给第三方组件，则可以无缝切换数据库系统。这就是数据库抽象层的目标。它强制你为查询使用特定语法，并承担遵循 DBMS 特性及优化 SQL 代码这项脏活累活。

抽象层的主要优点是可移植性，因为它使得即使在项目中期也可以切换到另一个数据库。假设你需要为应用程序快速编写原型，但客户尚未决定哪种数据库系统最适合他的需求。例如，你可以先使用 SQLite 构建应用程序，并在客户准备好做出决定时切换到 MySQL、PostgreSQL 或 Oracle。只需更改配置文件中的一行，即可生效。

Symfony 将 Propel 或 Doctrine 用作 ORM，它们使用 PHP Data Objects 进行数据库抽象。这两个由 Propel 和 Doctrine 团队开发的第三方组件已无缝集成到 symfony 中，你可以将其视为框架的一部分。本章中描述的它们的语法和约定已进行了调整，以尽量减少与 symfony 语法的差异。

> 在 symfony 项目中，所有应用程序共享同一个模型。这就是项目级别的意义所在：将依赖共同业务规则的应用程序组合在一起。这就是模型与应用程序独立的原因，模型文件存储在项目根目录的 lib/model/ 目录中。

## Symfony 的数据库架构

为了创建 symfony 将使用的数据对象模型，你需要将数据库中的关系模型转换为对象数据模型。ORM 需要关系模型的描述来执行映射，这被称为架构。在架构中，你定义表、它们之间的关系以及列的特性。





## Schema 示例

如何将数据库结构转换为 schema？示例是理解它的最佳方式。假设你有一个包含两个表的博客数据库：blog_article 和 blog_comment，结构如图 8-1 所示。

![](img/0f886a7f4cbcc3939be96e985ca35ff4_122_0.png)

相关的 schema.yml 文件应如清单 8-3 所示。

## 清单 8-3 - 示例 schema.yml

```
Article:
  actAs: [Timestampable]
  tableName: blog_article
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    title: string(255)
    content: clob

Comment:
  actAs: [Timestampable]
  tableName: blog_comment
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    article_id: integer
    author: string(255)
    content: clob
  relations:
    Article:
      onDelete: CASCADE
      foreignAlias: Comments
```

请注意，数据库名称本身（blog）不会出现在 schema.yml 文件中。相反，数据库是在连接名称下描述的（本示例中为 doctrine）。这是因为实际的连接设置可能取决于应用程序运行的环境。例如，当你在开发环境中运行应用程序时，将访问开发数据库（也许是 blog_dev），但与生产数据库使用相同的 schema。连接设置将在 databases.yml 文件中指定，本章后面“数据库连接”部分将对此进行描述。

schema 不包含任何详细的连接设置，只包含一个连接名称，以维护数据库抽象。

## 基本 Schema 语法

在 schema.yml 文件中，第一个键表示模型名称。你可以指定多个模型，每个模型都有一组列。根据 YAML 语法，键以冒号结尾，结构通过缩进显示（一个或多个空格，但不包括制表符）。

模型可以具有特殊属性，包括 tableName（模型的数据库表名）。如果你没有为模型提及 tableName，Doctrine 将根据模型名称的带下划线版本创建它。

> 下划线约定在单词之间添加下划线，并将所有内容转换为小写。Article 和 Comment 的默认带下划线版本分别是 article 和 comment。

模型包含列。列值可以以两种不同的方式定义：

- 如果你只定义一个属性，则它是列类型。Symfony 理解常见的列类型：boolean、integer、float、date、string(size)、clob（例如，在 MySQL 中转换为 text）等等。
- 如果你需要定义其他列属性（如默认值、必填等），则应将列属性写成一组 key: value。这种扩展的 schema 语法将在本章后面描述。

模型还可以包含显式外键和索引。有关更多信息，请参阅本章后面的“扩展 Schema 语法”部分。

## 模型类

schema 用于构建 ORM 层的模型类。为了节省执行时间，这些类是通过名为 doctrine:build-model 的命令行任务生成的。

```
$ php symfony doctrine:build-model
```

> 构建模型后，必须记得使用 php symfony cc 清除 symfony 的内部缓存，以便 symfony 可以找到你新创建的模型。

键入此命令将启动对 schema 的分析，并在你的项目的 lib/model/doctrine/base 目录中生成基础数据模型类：

- BaseArticle.php
- BaseComment.php

此外，实际的数据模型类将在 lib/model/doctrine 中创建：

- Article.php
- ArticleTable.php
- Comment.php
- CommentTable.php

你只定义了两个模型，却最终得到了六个文件。这没有问题，但值得解释一下。

## 基类和自定义类

为什么要在两个不同的目录中保留数据对象模型的两个版本？

你可能需要为模型对象添加自定义方法和属性（想想清单 8-1 中的 getName() 方法）。但随着项目的发展，你也会添加表或列。每当你更改 schema.yml 文件时，都需要通过再次调用 doctrine:build-model 来重新生成对象模型类。如果你的自定义方法写在实际生成的类中，它们将在每次生成后被擦除。

保存在 lib/model/doctrine/base/ 目录中的 Base 类是直接从 schema 生成的。你绝不应该修改它们，因为每次重新构建模型都会完全擦除这些文件。

另一方面，保存在 lib/model/doctrine 目录中的自定义对象类实际上继承自 Base 类。当在现有模型上调用 doctrine:build-model 任务时，这些类不会被修改。因此，这是你可以添加自定义方法的地方。

清单 8-4 展示了通过首次调用 doctrine:build-model 任务创建的自定义模型类示例。

## 清单 8-4 - 示例模型类文件，位于 lib/model/doctrine/Article.php

```
class Article extends BaseArticle
{
}
```

它继承了 BaseArticle 类的所有内容，但对 schema 的修改不会影响它。

自定义类继承基类的机制允许你开始编码，即使不了解数据库的最终关系模型。相关的文件结构使模型既可定制又可演化。

## 对象类和表类

Article 和 Comment 是表示数据库中记录的对象类。它们提供对记录列及相关记录的访问。这意味着你将能够通过调用 Article 对象的方法来获取文章的标题，如清单 8-5 中的示例所示。

## 清单 8-5 - 对象类中可用的记录列获取方法

```
$article = new Article();
// ...
$title = $article->getTitle();
```

ArticleTable 和 CommentTable 是表类，即包含用于操作表的公共方法的类。它们提供从表中检索记录的方式。它们的方法通常返回相关对象类的一个对象或对象集合，如清单 8-6 所示。

## 清单 8-6 - 表类中可用的检索记录的公共方法

```
// $article is an instance of class Article
$article = Doctrine_Core::getTable('Article')->find(123);
```

## 访问数据

在 symfony 中，数据是通过对象来访问的。如果你习惯使用关系模型并使用 SQL 来检索和修改数据，那么对象模型方法可能看起来很复杂。但一旦你体会到了使用面向对象方式进行数据访问的强大功能，你可能会非常喜欢它。

但首先，让我们确保我们使用相同的术语。关系数据模型和对象数据模型使用相似的概念，但它们各自有自己的命名法：

| 关系型 | 面向对象 |
| --- | --- |
| 表 | 类 |
| 行，记录 | 对象 |
| 字段，列 | 属性 |

## 检索列值

当 symfony 构建模型时，它会为 schema.yml 中定义的每个模型创建一个基础对象类。这些类中的每一个都带有基于列定义的默认访问器和修改器：new、getXXX() 和 setXXX() 方法有助于创建对象并访问对象属性，如清单 8-7 所示。

_清单 8-7 - 生成的对象类方法_

```
$article = new Article();
$article->setTitle('My first article');
$article->setContent("This is my very first article.\n Hope you enjoy it!");

$title = $article->getTitle();
$content = $article->getContent();
```

> 生成的对象类名为 Article，但存储在名为 blog_article 的数据库表中。如果在 schema 中未定义 tableName，则该类将命名为 article。访问器和修改器使用列名的 camelCase 变体，因此 getTitle() 方法检索 title 列的值。

要一次设置多个字段，可以使用每个对象类也提供的 fromArray() 方法，如清单 8-8 所示。

_清单 8-8 - fromArray() 方法是一个多设置器_

```
$article->fromArray(array(
  'Title' => 'My first article',
  'Content' => 'This is my very first article.\n Hope you enjoy it!',
));
```

## 检索相关记录

blog_comment 表中的文章 id 列隐式定义了指向 blog_article 表的外键。每条评论都与一篇文章相关，一篇文章可以有多条评论。生成的类包含五种方法，以面向对象的方式翻译这种关系，如下所示：



- $comment->getArticle(): 获取相关 Article 对象
- $comment->getArticleId(): 获取相关 Article 对象的 ID
- $comment->setArticle($article): 定义相关 Article 对象
- $comment->setArticleId($id): 通过 ID 定义相关 Article 对象
- $article->getComments(): 获取相关 Comment 对象

getArticleId() 和 setArticleId() 方法表明，你可以将 article_id 列视为常规列并手动设置关系，但它们并不十分有趣。面向对象方法的优势在其他三个方法中更为明显。清单 8-9 展示了如何使用生成的设置器。

## 清单 8-9 - 外键被翻译为特殊设置器

```
$comment = new Comment();
$comment->setAuthor('Steve');
$comment->setContent('Gee, dude, you rock: best article ever!');

// Attach this comment to the previous $article object
$comment->setArticle($article);

// Alternative syntax
// Only makes sense if the object is already saved in the database
// $comment->setArticleId($article->getId());
```

清单 8-10 展示了如何使用生成的获取器。它还演示了如何在模型对象上链式调用方法。

## 清单 8-10 - 外键被翻译为特殊获取器

```
// Many to one relationship
echo $comment->getArticle()->getTitle();
=> My first article
echo $comment->getArticle()->getContent();
=> This is my very first article.
Hope you enjoy it!

// One to many relationship
$comments = $article->getComments();
```

getArticle() 方法返回一个 Article 类的对象，该对象可使用 getTitle() 访问器。这比自己执行连接要好得多，后者可能需要几行代码（从 $comment->getArticleId() 调用开始）。

清单 8-10 中的 $comments 变量包含一个 Comment 类对象的数组。你可以使用 $comments[0] 显示第一个，或者使用 foreach ($comments as $comment) 遍历集合。

## 保存和删除数据

通过调用 new 构造函数，你创建了一个新对象，但不是 blog_article 表中的实际记录。修改对象对数据库也没有影响。为了将数据保存到数据库，你需要调用对象的 save() 方法。

```
$article->save();
```

ORM 足够智能，能够检测对象之间的关系，因此保存 $article 对象也会保存相关的 $comment 对象。它还知道保存的对象是否在数据库中有现有的对应项，因此对 save() 的调用有时会被翻译为 SQL 中的 INSERT，有时则是 UPDATE。主键由 save() 方法自动设置，因此保存后，你可以使用 $article->getId() 检索新主键。

你可以通过调用 isNew() 检查对象是否为新对象。如果你想知道对象是否已修改并值得保存，请调用其 isModified() 方法。

如果你读到关于文章的评论，可能会改变对在互联网上发表文章的看法。如果你不欣赏文章评论者的反讽，可以使用 delete() 方法轻松删除评论，如清单 8-11 所示。

## 清单 8-11 - 使用相关对象上的 delete() 方法从数据库中删除记录

```
foreach ($article->getComments() as $comment)
{
    $comment->delete();
}
```

## 按主键检索记录

如果知道特定记录的主键，请使用表类的 find() 类方法获取相关对象。

```
$article = Doctrine_Core::getTable('Article')->find(7);
```

schema.yml 文件将 id 字段定义为 blog_article 表的主键，因此此语句实际将返回 id 为 7 的文章。由于你使用了主键，你知道只会返回一条记录；$article 变量包含一个 Article 类的对象。

在某些情况下，主键可能包含多个列。在这种情况下，find() 方法接受多个参数，每个主键列对应一个参数。

## 使用 Doctrine_Query 检索记录

当你想要检索多条记录时，需要调用要检索对象所对应表类的 createQuery() 方法。例如，要检索 Article 类的对象，请调用 Doctrine_Core::getTable('Article')->createQuery()->execute()。

execute() 方法的第一个参数是一个参数数组，即用于替换查询中找到的任何占位符的值数组。

空的 Doctrine_Query 返回该类的所有对象。例如，清单 8-12 所示的代码检索所有文章。

## 清单 8-12 - 使用 createQuery() 的空查询通过 Doctrine_Query 检索记录

```
$q = Doctrine_Core::getTable('Article')->createQuery();
$articles = $q->execute();
```

```
// Will result in the following SQL query
SELECT b.id AS b__id, b.title AS b__title, b.content AS b__content,
b.created_at AS b__created_at, b.updated_at AS b__updated_at FROM
blog_article b
```

## 水合

对 ->execute() 的调用实际上比简单的 SQL 查询强大得多。首先，SQL 针对你选择的 DBMS 进行了优化。其次，传递给 Doctrine_Query 的任何值在集成到 SQL 代码之前都会被转义，从而防止 SQL 注入风险。第三，该方法返回对象数组，而不是结果集。ORM 会根据数据库结果集自动创建并填充对象。此过程称为水合（hydrating）。

对于更复杂的对象选择，你需要 WHERE、ORDER BY、GROUP BY 等 SQL 语句的等价物。Doctrine_Query 对象针对所有这些条件都有相应的方法和参数。例如，要获取 Steve 撰写的所有评论并按日期排序，请按清单 8-13 所示构建 Doctrine_Query。

## 清单 8-13 - 使用 createQuery() 的带条件 Doctrine_Query 通过 Doctrine_Query 检索记录

```
$q = Doctrine_Core::getTable('Comment')
->createQuery('c')
->where('c.author = ?', 'Steve')
->orderBy('c.created_at ASC');
$comments = $q->execute();

// Will result in the following SQL query
SELECT b.id AS b_id, b.article_id AS b__article_id, b.author AS b__author, b.content AS b__content, b.created_at AS b__created_at,
b.updated_at AS b__updated_at FROM blog_comment b WHERE (b.author = ?)
ORDER BY b.created_at ASC
```

表 8-1 比较了 SQL 语法与 Doctrine_Query 对象语法。

## 表 8-1 - SQL 和 Criteria 对象语法

| SQL | Criteria |
|---|---|
| WHERE column = value | ->where('acolumn = ?', 'value') |
| **其他 SQL 关键字** | |
| ORDER BY column ASC | ->orderBy('acolumn ASC') |
| ORDER BY column DESC | ->addOrderBy('acolumn DESC') |
| LIMIT limit | ->limit(limit) |
| OFFSET offset | ->offset(offset) |
| FROM table1 LEFT JOIN table2 ON table1.coll = table2.col2 | ->leftJoin('a.Model2 m') |
| FROM table1 INNER JOIN table2 ON table1.coll = table2.col2 | ->innerJoin('a.Model2 m') |

清单 8-14 展示了另一个带有多个条件的 Doctrine_Query 示例。它检索 Steve 在包含单词“enjoy”的文章上发表的所有评论，并按日期排序。

## 清单 8-14 - 使用 createQuery() 的带条件 Doctrine_Query 通过 Doctrine_Query 检索记录的另一个示例

```
$q = Doctrine_Core::getTable('Comment')
 ->createQuery('c')
 ->where('c.author = ?', 'Steve')
 ->leftJoin('c.Article a')
 ->andWhere('a.content LIKE ?', '%enjoy%')
 ->orderBy('c.created_at ASC');
$comments = $q->execute();
```

```
// Will result in the following SQL query
SELECT b.id AS b__id, b.article_id AS b__article_id, b.author AS
b__author, b.content AS b__content, b.created_at AS b__created_at,
b.updated_at AS b__updated_at, b2.id AS b2__id, b2.title AS b2__title,
b2.content AS b2__content, b2.created_at AS b2__created_at, b2.updated_at
AS b2__updated_at FROM blog_comment b LEFT JOIN blog_article b2 ON
b.article_id = b2.id WHERE (b.author = ? AND b2.content LIKE ?) ORDER BY
b.created_at ASC
```

正如 SQL 是一种允许你构建非常复杂查询的简单语言一样，Doctrine_Query 对象可以处理任何复杂程度的条件。但由于许多开发人员首先用 SQL 思考，然后再将条件转换为面向对象逻辑，因此 Doctrine_Query 对象起初可能难以理解。理解它的最佳方式是从示例和示例应用程序中学习。例如，symfony 项目网站充满了 Doctrine_Query 构建示例，将从多个方面启发你。

每个 Doctrine_Query 实例都有一个 count() 方法，它只计算查询的记录数并返回一个整数。由于没有对象可返回，在这种情况下不会发生水合过程，且 count() 方法比 execute() 更快。

表类还提供 findAll()、findBy*() 和 findOneBy*() 方法，它们是构建 Doctrine_Query 实例、执行它们并返回结果的快捷方式。

最后，如果你只想要返回的第一个对象，请用 fetchOne() 调用替换 execute()。当你知道 Doctrine_Query 只会返回一个结果时可能会出现这种情况，其优势在于该方法返回一个对象而不是对象数组。

> 当 execute() 查询返回大量结果时，你可能希望在响应中只显示其中一个子集。Symfony 提供了一个名为 sfDoctrinePager 的分页类，它自动化了结果的分页。

## 使用原始 SQL 查询

有时，你不想检索对象，而只想获取数据库计算的合成结果。例如，要获取所有文章的最新创建日期，检索所有文章并循环遍历数组没有意义。你更愿意让数据库只返回结果，因为它会跳过对象水合过程。

另一方面，你不想直接调用 PHP 的数据库管理命令，因为那样会失去数据库抽象的好处。这意味着你需要绕过 ORM（Doctrine），但不能绕过数据库抽象（PDO）。

使用 PHP 数据对象查询数据库需要执行以下步骤：

- 1. 获取数据库连接。
- 2. 构建查询字符串。
- 3. 由此创建语句。
- 4. 遍历语句执行产生的结果集。

如果这对你来说像天书一样，清单 8-15 中的代码可能会更明确。





### 清单 8-15 - 使用 PDO 的自定义 SQL 查询

```
$connection = Doctrine_Manager::connection();
$query = 'SELECT MAX(created_at) AS max FROM blog_article';
$statement = $connection->execute($query);
$statement->execute();
$resultset = $statement->fetch(PDO::FETCH_OBJ);
$max = $resultset->max;
```

就像 Doctrine 查询一样，刚开始使用 PDO 查询时也会感到棘手。再次强调，现有应用程序和教程中的示例会向你展示正确的方法。

> 如果你想绕过此过程直接访问数据库，你将有失去 Doctrine 提供的安全性和抽象性的风险。采用 Doctrine 的方式虽然更冗长，但它迫使你使用良好的实践，以保证应用程序的性能、可移植性和安全性。对于包含来自不可信来源（例如互联网用户）的参数的查询，这一点尤其正确。Doctrine 会执行所有必要的转义并保护你的数据库。直接访问数据库会使你面临 SQL 注入攻击的风险。

## 使用特殊日期列

通常，当表中有一个名为 created_at 的列时，它用于存储记录创建日期的时间戳。updated_at 列也是如此，每当记录本身被更新时，都会将其更新为当前时间。

好消息是 Doctrine 具有一个 Timestampable 行为，它会为你处理它们的更新。你不需要手动设置 created_at 和 updated_at 列；它们会自动更新，如列表 8-16 所示。

### 清单 8-16 - created_at 和 updated_at 列会自动处理

```
$comment = new Comment();
$comment->setAuthor('Steve');
$comment->save();

// Show the creation date
echo $comment->getCreatedAt();
=> [date of the database INSERT operation]
```

## 重构到数据层

开发 symfony 项目时，你通常会先在操作中编写领域逻辑代码。但数据库查询和模型操作不应存储在控制器层中。因此，所有与数据相关的逻辑都应移至模型层。每当你需要在操作中的多个位置执行相同的请求时，考虑将相关代码转移到模型中。这有助于保持操作简洁且易读。

例如，假设博客中需要检索给定标签（作为请求参数传递）的十篇最热门文章的代码。这段代码不应放在操作中，而应放在模型中。事实上，如果你需要在模板中显示此列表，操作应简单如下所示：

```
public function executeShowPopularArticlesForTag($request)
{
    $tag =
    Doctrine_Core::getTable('Tag')->findOneByName($request->getParameter('tag'));
    $this->forward404Unless($tag);
    $this->articles = $tag->getPopularArticles(10);
}
```

操作从请求参数中创建一个 Tag 类的对象。然后，查询数据库所需的所有代码都位于该类的 getPopularArticles() 方法中。这使操作更易读，并且模型代码可以轻松在另一个操作中复用。

将代码移动到更合适的位置是重构的一种技术。如果你经常这样做，你的代码将易于维护，也易于其他开发人员理解。关于何时进行数据层重构的一个好经验法则是：操作中的代码很少应包含超过十行 PHP 代码。

## 数据库连接

数据模型与所使用的数据库独立，但你肯定会使用数据库。symfony 向项目数据库发送请求所需的最少信息是数据库名称、凭据和数据库类型。这些连接设置可以通过将数据源名称 (DSN) 传递给 configure:database 任务来配置：

```
$ php symfony configure:database "mysql:host=localhost;dbname=blog" root
mYsEcret
```

连接设置取决于环境。你可以使用 env 选项为 prod、dev 和 test 环境，或应用程序中的任何其他环境定义不同的设置：

```
$ php symfony configure:database --env=dev
"mysql:host=localhost;dbname=blog_dev" root mYsEcret
```

此配置也可以按应用程序覆盖。例如，你可以使用此方法为前端和后端应用程序设置不同的安全策略，并在数据库中定义多个具有不同权限的数据库用户来处理此问题：

```
$ php symfony configure:database --app=frontend
"mysql:host=localhost;dbname=blog" root mYsEcret
```

对于每个环境，你可以定义多个连接。使用的默认连接名称为 doctrine。name 选项允许你创建另一个连接：

```
$ php symfony configure:database --name=main
"mysql:host=localhost;dbname=example" root myS3cret
```

你也可以手动在 config/ 目录下的 databases.yml 文件中输入这些连接设置。列表 8-17 显示了此类文件的示例，列表 8-18 显示了使用扩展表示法的相同示例。

### 清单 8-17 - 数据库连接设置的简写形式

```
all:
  doctrine:
    class: sfDoctrineDatabase
    param:
      dsn: mysql://login:passwd@localhost/blog
```

### 清单 8-18 - 数据库连接设置示例，位于 myproject/config/databases.yml

```
prod:
  doctrine:
    param:
      dsn: mysql:dbname=blog;host=localhost
      username: login
      password: passwd
    attributes:
      quote_identifier: false
      use_native_enum: false
      validate: all
      idname_format: %s_id
      seqname_format: %s_seq
      tblname_format: %s
```

若要按应用程序覆盖配置，你需要编辑应用程序特定的文件，例如 apps/frontend/config/databases.yml。

如果你想使用 SQLite 数据库，dsn 参数必须设置为数据库文件的路径。例如，如果你将博客数据库保存在 data/blog.db 中，databases.yml 文件将如列表 8-19 所示。

### 清单 8-19 - SQLite 的数据库连接设置，使用文件路径作为主机

```
all:
  doctrine:
    class: sfDoctrineDatabase
    param:
      dsn: sqlite:///%SF_DATA_DIR%/blog.db
```

## 扩展模型

生成的模型方法很棒，但通常还不够。一旦你实现自己的业务逻辑，就需要通过添加新方法或覆盖现有方法来扩展它。

### 添加新方法

你可以向 lib/model/doctrine 目录中生成的空模型类添加新方法。使用 $this 调用当前对象的方法，使用 self:: 调用当前类的静态方法。请记住，自定义类从 lib/model/doctrine/base 目录中的 Base 类继承方法。

例如，针对基于列表 8-3 生成的 Article 对象，你可以添加一个魔术 __toString() 方法，以便输出 Article 类对象时显示其标题，如列表 8-20 所示。

### 清单 8-20 - 自定义模型，位于 lib/model/doctrine/Article.php

```
class Article extends BaseArticle
{
    public function __toString()
    {
        return $this->getTitle(); // getTitle() is inherited from BaseArticle
    }
}
```

你也可以扩展表类——例如，添加一个按创建日期检索所有文章的方法，如列表 8-21 所示。

### 清单 8-21 - 自定义模型，位于 lib/model/doctrine/ArticleTable.php

```
class ArticleTable extends BaseArticleTable
{
    public function getAllOrderedByDate()
    {
        $q = $this->createQuery('a')
        ->orderBy('a.created_at ASC');

        return $q->execute();
    }
}
```

新方法的使用方式与生成的方法相同，如列表 8-22 所示。

### 清单 8-22 - 使用自定义模型方法就像使用生成的方法一样

```
$articles = Doctrine_Core::getTable('Article')->getAllOrderedByDate();
foreach ($articles as $article)
{
    echo $article; // Will call the magic __toString() method
}
```

### 覆盖现有方法

如果 Base 类中的某些生成方法不符合你的要求，你仍然可以在自定义类中覆盖它们。只需确保使用相同的方法签名（即相同的参数数量）。

例如，$article->getComments() 方法返回一组 Comment 对象，顺序不定。如果你希望按创建日期对结果进行排序，最新的评论排在最前面，那么请创建 getComments() 方法，如列表 8-23 所示。

### 清单 8-23 - 覆盖现有模型方法，位于 lib/model/doctrine/Article.php




## 使用模型行为

有些模型修改是通用的，可以复用。例如，使模型对象可排序的方法，以及用于防止并发对象保存冲突的乐观锁，都是可以添加到许多类中的通用扩展。

Symfony 将这些扩展打包为行为。行为是提供额外方法给模型类的外部类。模型类中已包含钩子，而 symfony 知道如何扩展它们。

要在模型类中启用行为，必须修改架构并使用 actAs 选项：

```
Article:
  actAs: [Timestampable, Sluggable]
  tableName: blog_article
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    title: string(255)
    content: clob
```

重建模型后，Article 模型将拥有一个 slug 列，它会根据标题自动设置为 URL 友好的字符串。

Doctrine 自带的一些行为如下：

- Timestampable
- Sluggable
- SoftDelete
- Searchable
- I18n
- Versionable
- NestedSet

## 扩展架构语法

schema.yml 文件可以很简单，如清单 8-3 所示。但关系型模型通常较为复杂。因此，架构拥有广泛的语法，能够处理几乎所有情况。

## 属性

连接和表可以拥有特定属性，如清单 8-24 所示。它们在 _attributes 键下设置。

### 清单 8-24 - 模型设置的属性

```
Listing 8-33
Article:
  attributes:
    export: tables
    validate: none
```

export 属性控制为该模型创建表时，将哪些 SQL 导出到数据库。使用 tables 值将仅导出表结构，而不会导出外键、索引等。

包含本地化内容的表（即，在关联表中存储多个版本的内容，用于国际化）应使用 I18n 行为（详情见第 13 章），如清单 8-25 所示。

### 清单 8-25 - I18n 行为

```
Listing 8-34
Article:
  actAs:
    I18n:
      fields: [title, content]
```

## 处理多个架构

每个应用程序可以拥有一个以上的架构。Symfony 会考虑 `config/doctrine` 文件夹中所有以 `.yml` 结尾的文件。如果你的应用程序拥有许多模型，或者某些模型不共享相同的连接，你会发现这种方法非常有用。

考虑这两个架构：

```
// In config/doctrine/business-schema.yml
Article:
  id:
    type: integer
    primary: true
    autoincrement: true
  title: string(50)

// In config/doctrine/stats-schema.yml
Hit:
  actAs: [Timestampable]
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    resource: string(100)
```

两个架构共享相同的连接（doctrine），Article 和 Hit 类将在相同的 lib/model/doctrine 目录下生成。一切都会如同你只编写了一个架构一样发生。

你还可以让不同的架构使用不同的连接（例如 doctrine 和 doctrine_bis，需在 databases.yml 中定义），并将其与该连接关联：

```
// In config/doctrine/business-schema.yml
Article:
  connection: doctrine
  id:
    type: integer
    primary: true
    autoincrement: true
  title: string(50)

// In config/doctrine/stats-schema.yml
Hit:
  connection: doctrine_bis
  actAs: [Timestampable]
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    resource: string(100)
```

许多应用程序使用多个架构。特别是，某些插件拥有自己的架构，以避免干扰你自己的类（详情见第 17 章）。

## 列详细信息

基本语法允许使用 type 关键字之一定义类型。清单 8-26 演示了这些选择。

### 清单 8-26 - 基本列属性

```
Article:
columns:
  title: string(50) # Specify the type and length
```

但你可以为列定义更多内容。如果你这样做，就需要将列设置定义为关联数组，如清单 8-27 所示。

### 清单 8-27 - 复杂列属性

```
Article:
columns:
  id:     { type: integer, notnull: true, primary: true,
            autoincrement: true }
  name:   { type: string(50), default: foobar }
  group_id: { type: integer }
```

列参数如下：

- * type：列类型。选项包括 boolean、integer、double、float、decimal、string(size)、date、time、timestamp、blob 和 clob。
- * notnull：布尔值。如果你希望列为必填项，则将其设置为 true。
- * length：受支持类型的字段大小或长度。
- * scale：用于 decimal 数据类型的小数位数（必须同时指定 size）。
- * default：默认值。
- * primary：布尔值。对于主键，将其设置为 true。
- * autoincrement：布尔值。对于需要自增值的 integer 类型列，将其设置为 true。
- * sequence：用于为 autoIncrement 列使用序列的数据库的序列名称（例如 PostgreSQL 和 Oracle）。
- * unique：布尔值。如果你希望列是唯一的，则将其设置为 true。

## 关系

你可以在模型的 relations 键下指定外键关系。清单 8-28 中的架构将在 user_id 列上创建外键，与 blog_user 表中的 id 列匹配。

### 清单 8-28 - 外键替代语法

```
Article:
  actAs: [Timestampable]
  tableName: blog_article
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    title:   string(255)
    content: clob
    user_id: integer
  relations:
    User:
      onDelete: CASCADE
      foreignAlias: Articles
```

## 索引

你可以在模型的 indexes: 键下添加索引。如果要定义唯一索引，必须使用 type: unique 语法。对于需要指定大小的列（因为它们是文本列），索引的大小以与列长度相同的方式使用括号指定。清单 8-30 显示了索引的替代语法。

### 清单 8-30 - 索引和唯一索引

```
Article:
  actAs: [Timestampable]
  tableName: blog_article
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    title: string(255)
    content: clob
    user_id: integer
  relations:
    User:
      onDelete: CASCADE
      foreignAlias: Articles
  indexes:
    my_index:
      fields:
        title:
          length: 10
      user_id: []
    my_other_index:
      type: unique
      fields:
        created_at
```

## I18n 表

Symfony 支持在关联表中进行内容国际化。这意味着，当你拥有需要国际化的内容时，它将存储在两个独立的表中：一个包含不变列，另一个包含国际化列。

### 清单 8-33 - 显式 i18n 机制

```
DbGroup:
  actAs:
    I18n:
      fields: [name]
  columns:
    name: string(50)
```

## 行为

行为是由插件提供的模型修饰符，用于为你的 Doctrine 类添加新功能。第 17 章详细介绍了行为。你可以直接在架构中定义行为，即在 actAs 键下为每个表列出行为及其参数。清单 8-34 通过将 Sluggable 行为扩展到 Article 类，给出了一个示例。

### 清单 8-34 - 行为声明

```
Article:
  actAs: [Sluggable]
  # ...
```

## 不要创建两次模型

使用 ORM 的权衡在于，你必须定义两次数据结构：一次用于数据库，一次用于对象模型。幸运的是，symfony 提供了命令行工具，可以基于另一方生成其中一方，从而避免重复工作。

## 基于现有架构构建 SQL 数据库结构

如果你通过编写 schema.yml 文件来启动应用程序，symfony 可以生成一个 SQL 查询，直接从 YAML 数据模型创建表。要使用该查询，请进入项目根目录并输入：

```
$ php symfony doctrine:build-sql
```

schema.sql 文件将在 myproject/data/sql/ 中创建。请注意，生成的 SQL 代码将针对 databases.yml 中定义的数据库系统进行优化。

你可以直接使用 schema.sql 文件来构建表。例如，在 MySQL 中，输入：

```
$ mysqladmin -u root -p create blog
$ mysql -u root -p blog < data/sql/schema.sql
```

生成的 SQL 也有助于在另一个环境中重建数据库，或更换另一种 DBMS。

> 命令行还提供了一个基于文本文件填充数据库的任务。有关 doctrine:data-load 任务和 YAML 夹具文件的更多信息，请参见第 16 章。

## 从现有数据库生成 YAML 数据模型

Symfony 可以使用 Doctrine 从现有数据库生成 schema.yml 文件，这要归功于内省（数据库确定其正在操作的表结构的能力）。在进行逆向工程时，或者如果你更喜欢先处理数据库再处理对象模型，这会特别有用。

为此，你需要确保项目 databases.yml 文件指向正确的数据库并包含所有连接设置，然后调用 doctrine:build-schema 命令：

```
$ php symfony doctrine:build-schema
```

基于数据库结构生成的全新 schema.yml 文件将生成在 config/doctrine/ 目录中。你可以基于此架构构建模型。




## Summary

Symfony 使用 Doctrine 作为 ORM，使用 PHP Data Objects 作为数据库抽象层。这意味着在生成对象模型类之前，你必须先在 YAML 中描述数据库的关系模式。然后，在运行时，使用对象和表类的方法来检索关于单条记录或一组记录的信息。你可以通过向自定义类添加方法来轻松重写和扩展模型。连接设定在 databases.yml 文件中定义，该文件可以支持多个连接。命令行包含特殊任务，以避免重复的结构定义。

模型层是 Symfony 框架中最复杂的部分。这种复杂性的一个原因是，数据操作是一件复杂的事情。相关的安全问题对网站至关重要，不应被忽视。另一个原因是，Symfony 更适合企业环境中的中大型应用程序。在这样的应用程序中，Symfony 模型提供的自动化功能确实代表了时间的节省，值得投入精力去学习其内部原理。

所以，不要犹豫，花些时间测试模型对象和方法，以便完全理解它们。你的应用程序的稳健性和可扩展性将是巨大的回报。

# 第 9 章

## 链接和路由系统

在 Web 应用程序框架中，链接和 URL 值得特殊对待。这是因为
应用程序的唯一入口点（前端控制器）以及模板中辅助函数的使用，
允许 URL 的工作方式与其外观之间完全分离。
这称为路由。路由不仅仅是一个小工具，它是一个有用的工具，可以使 Web 应用程序
更加用户友好和安全。本章将告诉你在 Symfony 应用程序中处理 URL 所需了解的一切：

- 路由系统是什么以及它如何工作
- 如何在模板中使用链接辅助函数来启用传出 URL 的路由
- 如何配置路由规则以更改 URL 的外观

你还将发现一些掌握路由性能和添加最终润色的技巧。

## 什么是路由？

路由是一种重写 URL 以使其更加用户友好的机制。但为了
理解这一点为何重要，你必须先花几分钟思考 URL。

## 作为服务器指令的 URL

URL 承载了从浏览器到服务器执行用户所需操作所需的信息。例如，传统 URL 包含指向脚本的文件路径以及完成请求所需的一些参数，如本示例所示：http://www.example.com/web/controller/article.php?id=123456&format_code=6532

此 URL 泄露了应用程序架构和数据库的信息。开发人员通常
在界面中隐藏应用程序的基础架构（例如，他们选择“个人资料页面”这样的页面标题，而不是“QZ7.65”）。在 URL 中泄露应用程序内部的重要线索与这一努力相悖，并有严重缺点：

- URL 中出现的技术数据会造成潜在的安全漏洞。在上述示例中，如果恶意用户更改了 id 参数的值，会发生什么？这是否意味着应用程序提供了直接访问数据库的接口？或者，如果用户出于好玩尝试其他脚本名称，比如 admin.php，会怎样？总的来说，原始 URL 提供了黑客攻击应用程序的便捷途径，使用它们来管理安全几乎是不可能的。

- URL 的晦涩难懂使得它们无论出现在何处都令人不安，并且削弱了周围内容的影响力。如今，URL 不仅出现在地址栏中。当用户将鼠标悬停在链接上时，它们也会出现，并在搜索结果中出现。当用户查找信息时，你希望给他们关于所找到内容的易于理解的线索，而不是令人困惑的 URL，如图 9-1 所示。

### 图 9-1 - URL 出现在许多地方，例如搜索结果中

**Microsoft Office 剪贴画和媒体主页**
Microsoft Office 剪贴画和媒体 - 超过 140,000 个剪贴画图形、动画、照片和声音，供 Microsoft Office 产品使用。
office.microsoft.com/clipart/default.aspx?lcl=en-us - 56k - 2006 年 8 月 30 日 -
缓存 - 相关页面

- 如果必须更改一个 URL（例如，如果脚本名称或其参数之一被修改），则指向此 URL 的每个链接也必须更改。这意味着控制器结构的修改既繁重又昂贵，在敏捷开发中并非理想状态。

如果 Symfony 不使用前端控制器模式，情况可能会更糟；也就是说，如果应用程序包含许多可从 Internet 访问的脚本，分布在许多目录中，比如：

```
http://www.example.com/web/gallery/album.php?name=my%20holidays
http://www.example.com/web/weblog/public/post/list.php
http://www.example.com/web/general/content/page.php?name=about%20us
```

在这种情况下，开发人员需要将 URL 结构与文件结构匹配，当其中任何一种结构发生变化时，这将导致维护噩梦。

## 作为界面一部分的 URL

路由背后的理念是将 URL 视为界面的一部分。应用程序可以格式化 URL 以向用户传达信息，用户可以使用 URL 访问应用程序的资源。

在 Symfony 应用程序中，这是可能的，因为呈现给最终用户的 URL 与执行请求所需的服务器指令无关。相反，它与所请求的资源相关，并且可以自由格式化。例如，Symfony 可以理解以下 URL，并使其显示与本章所示第一个 URL 相同的页面：

```
http://www.example.com/articles/finance/2010/activity-breakdown.html
```

好处是巨大的：

- URL 实际上有实际含义，可以帮助用户决定链接背后的页面是否包含他们期望的内容。链接可以包含有关其返回资源的其他详细信息。这对于搜索引擎结果尤其有用。此外，URL 有时出现时不提及页面标题（例如，当你在电子邮件中复制 URL 时），在这种情况下，它们本身必须有实际含义。有关用户友好型 URL 的示例，请参见图 9-2。

- 技术实现对用户隐藏：他们不知道使用了哪个脚本，也无法猜测 id 或类似参数：你的应用程序更不易受到潜在安全漏洞的影响。此外，你可以完全更改幕后发生的事情，而不会影响他们的体验（他们不会遇到 404 错误或永久重定向）。

### 图 9-2 - URL 可以传达关于页面的其他信息，例如发布日期

Symfony PHP5 框架 » 简单的 AJAX 分页
AJAX 分页演示使用两个非常简单的动作，两者都将分页器传递给其模板：class pagerActions extends sfActions { public function ...
www.symfony-project.com/weblog/2006/07/17/ajax-pagination-made-simple.html - 12k - 缓存 - 相关页面

- 纸质文档中书写的 URL 更容易输入和记住。如果你的公司网站在名片上显示为 http://www.example.com/controller/web/index.jsp?id=ERD4，它可能不会获得很多访问量。

- URL 可以成为一种命令行工具，以直观的方式执行操作或检索信息。提供此类可能性的应用程序对高级用户来说使用起来更快。

```
Listing 9-3
// List of results: add a new tag to narrow the list of results
http://del.icio.us/tag/symfony+ajax
// User profile page: change the name to get another user profile
http://www.askeet.com/user/francois
```

- 你可以通过一次修改独立更改 URL 格式和动作名称/参数。这意味着你可以先进行开发，稍后再格式化 URL，而不会完全搞乱你的应用程序。

- 即使重新组织应用程序的内部，URL 对外部世界也可以保持不变。这使得 URL 持久化，这是必不可少的，因为它允许在动态页面上设置书签。

- 搜索引擎在索引网站时往往会跳过动态页面（以 .php、.asp 等结尾）。因此，你可以格式化 URL，让搜索引擎认为它们在浏览静态内容，即使遇到动态页面，从而使你的应用程序页面获得更好的索引。

- 这更安全。任何无法识别的 URL 都将被重定向到开发人员指定的页面，用户无法通过测试 URL 来浏览 Web 根目录文件结构。请求实际调用的脚本名称及其参数都被隐藏。

用户看到的 URL 与实际脚本名称和请求参数之间的对应关系，是通过基于可通过配置修改的模式的路由系统来实现的。

> 资源怎么办？幸运的是，资源（图像、样式表和 JavaScript）的 URL 在浏览过程中不常出现，因此对这些资源并不真正需要路由。在 Symfony 中，所有资源都位于 web/ 目录下，其 URL 与其在文件系统中的位置匹配。但是，你可以通过在资源辅助函数中使用生成的 URL 来管理动态资源（由动作处理）。例如，要显示动态生成的图像，请使用 image_tag(url_for('captcha/image?key='.$key))。

## 工作原理

Symfony 将外部 URL 及其内部 URI 分离开来。两者之间的对应关系由路由系统建立。为了简化事情，Symfony 为内部 URL 使用了一种与常规 URL 非常相似的语法。清单 9-1 显示了一个示例。

### 清单 9-1 - 外部 URL 和内部 URI

```
Listing 9-4
// Internal URI syntax
<module>/<action>[?param1=value1][&param2=value2][&param3=value3]...
```



```
Example internal URI, which never appears to the end user
article/permalink?year=2010&subject=finance&title=activity-breakdown
```

```
Example external URL, which appears to the end user
http://www.example.com/articles/finance/2010/activity-breakdown.html
```

路由系统使用一个特殊的配置文件，称为 routing.yml，你可以在其中定义路由规则。考虑 Listing 9-2 中所示的规则。它定义了一个类似 articles/*/*/* 的模式，并为匹配通配符的内容片段命名。

### Listing 9-2 - 示例路由规则

```
article_by_title:
 url:   articles/:subject/:year/:title.html
 param: { module: article, action: permalink }
```

发送到 symfony 应用程序的每个请求首先由路由系统分析（这很简单，因为每个请求都由单个前端控制器处理）。路由规则会在请求 URL 与路由规则中定义的模式之间查找匹配项。如果找到匹配项，则命名的通配符将成为请求参数，并与 param: 键中定义的参数合并。请参见 Listing 9-3 中的工作原理。

### Listing 9-3 - 路由系统解析传入的请求 URL

```
// The user types (or clicks on) this external URL
http://www.example.com/articles/finance/2010/activity-breakdown.html

// The front controller sees that it matches the article_by_title rule
// The routing system creates the following request parameters
'module' => 'article'
'action' => 'permalink'
'subject' => 'finance'
'year' => '2010'
'title' => 'activity-breakdown'
```

然后将请求传递给 article 模块的 permalink 操作，该操作在请求参数中拥有确定显示哪篇文章所需的所有信息。

但是该机制也必须双向工作。为了让应用程序在其链接中显示外部 URL，你必须为路由系统提供足够的数据来确定应应用哪个规则。你还不能直接使用 <a> 标签编写超链接——这将完全绕过路由——而应使用特殊的辅助函数，如 Listing 9-4 所示。

### Listing 9-4 - 路由系统在模板中格式化传出 URL

```
// The url_for() helper transforms an internal URI into an external URL
<a href="<?php echo url_for('article/permalink?subject=finance&year=2010&title=activity-breakdown') ?>">click here</a>
```

```
// The helper sees that the URI matches the article_by_title rule
// The routing system creates an external URL out of it
=> <a href="http://www.example.com/articles/finance/2010/activity-breakdown.html">click here</a>
```

```
// The link_to() helper directly outputs a hyperlink
// and avoids mixing PHP with HTML
<?php echo link_to(
 'click here',
'article/permalink?subject=finance&year=2010&title=activity-breakdown'
) ?>
```

```
// Internally, link_to() will make a call to url_for() so the result is
the same
=> <a href="http://www.example.com/articles/finance/2010/activity-breakdown.html">click here</a>
```

因此，路由是一种双向机制，只有当你使用 link_to() 辅助函数来格式化所有链接时，它才能正常工作。

## URL 重写

在深入了解路由系统之前，需要澄清一个问题。在上一节给出的示例中，内部 URI 未提及前端控制器（index.php 或 frontend_dev.php）。是前端控制器，而不是应用程序的元素，决定了环境。因此，所有链接都必须与环境无关，前端控制器名称永远不会出现在内部 URI 中。

生成的 URL 示例中也没有脚本名称。这是因为生成的 URL 默认在生产环境中不包含任何脚本名称。settings.yml 文件中的 no_script_name 参数精确控制生成的 URL 中前端控制器名称的出现。如 Listing 9-5 所示，将其设置为 false，则链接辅助函数输出的 URL 将在每个链接中提及前端控制器脚本名称。

### Listing 9-5 - 在 apps/frontend/config/settings.yml 中在 URL 中显示前端控制器名称

```
prod:
 .settings
 no_script_name: false
```

现在，生成的 URL 将如下所示：

```
http://www.example.com/index.php/articles/finance/2010/activity-breakdown.html
```

除了生产环境外，在所有环境中，no_script_name 参数默认设置为 false。因此，例如，当你在开发环境中浏览应用程序时，前端控制器名称始终会出现在 URL 中。

```
http://www.example.com/frontend_dev.php/articles/finance/2010/activity-breakdown.html
```

在生产环境中，no_script_name 设置为 true，因此 URL 仅显示路由信息且更加用户友好。不会出现任何技术信息。

```
http://www.example.com/articles/finance/2010/activity-breakdown.html
```

但是应用程序如何知道调用哪个前端控制器脚本？这就是 URL 重写的用武之地。可以配置 Web 服务器，以便在 URL 中没有脚本时调用给定脚本。

在 Apache 中，启用 mod_rewrite 扩展后即可实现此功能。每个 symfony 项目都附带一个 .htaccess 文件，该文件为 web/ 目录的服务器配置添加了 mod_rewrite 设置。该文件的默认内容如 Listing 9-6 所示。

### Listing 9-6 - myproject/web/.htaccess 中 Apache 的默认重写规则

```
<IfModule mod_rewrite.c>
RewriteEngine On

# uncomment the following line, if you are having trouble
# getting no_script_name to work
#RewriteBase /

# we skip all files with .something
#RewriteCond %{REQUEST_URI} \..+$
#RewriteCond %{REQUEST_URI} !\.html$
#RewriteRule .* - [L]

# we check if the .html version is here (caching)
RewriteRule ^$ index.html [QSA]
RewriteRule ^([^.]+)$ $1.html [QSA]
RewriteCond %{REQUEST_FILENAME} !-f

# no, so we redirect to our front web controller
RewriteRule ^(.*)$ index.php [QSA,L]
</IfModule>
```

Web 服务器会检查其接收到的 URL 格式。如果 URL 不包含后缀（默认情况下已注释）且没有可用的页面缓存版本（第 12 章介绍缓存），则请求将交给 index.php。

但是，symfony 项目的 web/ 目录在项目的所有应用程序和环境之间共享。这意味着 web 目录中通常不止一个前端控制器。例如，一个同时拥有前端和后端应用程序，以及 dev 和 prod 环境的项目，在 web/ 目录中包含四个前端控制器脚本：

- index.php // 前端，生产环境
- frontend_dev.php // 前端，开发环境
- backend.php // 后端，生产环境
- backend_dev.php // 后端，开发环境

mod_rewrite 设置只能指定一个默认脚本名称。如果你为所有应用程序和环境都将 no_script_name 设置为 true，则所有 URL 都将被解释为针对生产环境中前端应用程序的请求。这就是为什么对于给定项目，只能有一个应用程序和一个环境利用 URL 重写。

> 有一种方法可以拥有多个无脚本名称的应用程序。只需在 Web 根目录中创建子目录，并将前端控制器移入其中。相应地更改 ProjectConfiguration 文件的路径，并为每个应用程序创建所需的 .htaccess URL 重写配置。

## 链接辅助函数

由于路由系统，你应该在模板中使用链接辅助函数，而不是常规的 <a> 标签。不要将其视为麻烦，而应将其视为保持应用程序整洁且易于维护的机会。此外，链接辅助函数提供了一些非常有用的快捷方式，你绝不想错过。

## 超链接、按钮和表单

你已经了解 link_to() 辅助函数。它输出一个符合 XHTML 标准的超链接，并需要两个参数：可单击的元素及其指向的资源的内部 URI。如果你想要的是按钮而不是超链接，请使用 button_to() 辅助函数。表单也有一个辅助函数来管理 action 属性的值。你将在下一章中了解更多关于表单的内容。Listing 9-7 显示了一些链接辅助函数的示例。

### Listing 9-7 - <a>、<input> 和 <form> 标签的链接辅助函数

```
// Hyperlink on a string
<?php echo link_to('my article', 'article/read?title=Finance_in_France') ?>
=> <a href="/routed/url/to/Finance_in_France">my article</a>
```

```
// Hyperlink on an image
<?php echo link_to(image_tag('read.gif'), 'article/read?title=Finance_in_France') ?>
=> <a href="/routed/url/to/Finance_in_France"><img src="http://www.symfony-project.org/images/read.gif" /></a>
```

```
// Button tag
<?php echo button_to('my article', 'article/read?title=Finance_in_France') ?>
=> <input value="my article" type="button" onclick="document.location.href='/routed/url/to/Finance_in_France';" />
```

```
// Form tag
<?php echo form_tag('article/read?title=Finance_in_France') ?>
=> <form method="post" action="/routed/url/to/Finance_in_France" />
```

链接辅助函数可以接受内部 URI 以及绝对 URL（以 http:// 开头，并由路由系统跳过）和锚点。请注意，在实际应用程序中，内部 URI 是使用动态参数构建的。Listing 9-8 显示了所有这些情况的示例。

### Listing 9-8 - 链接辅助函数接受的 URL

```
// Internal URI
<?php echo link_to('my article', 'article/read?title=Finance_in_France') ?>
=> <a href="/routed/url/to/Finance_in_France">my article</a>
```

```
// Internal URI with dynamic parameters
<?php echo link_to('my article', 'article/read?title='.$article->getTitle()) ?>
```

```
// Internal URI with anchors
<?php echo link_to('my article', 'article/read?title=Finance_in_France#foo') ?>
=> <a href="/routed/url/to/Finance_in_France#foo">my article</a>
```

```
// Absolute URL
<?php echo link_to('my article', 'http://www.example.com/foobar.html') ?>
=> <a href="http://www.example.com/foobar.html">my article</a>
```





## 链接辅助选项

如第 7 章所述，辅助函数接受一个额外的选项参数，该参数可以是关联数组或字符串。链接辅助函数也是如此，如清单 9-9 所示。

### 清单 9-9 - 链接辅助函数接受额外选项

```
// Additional options as an associative array
<?php echo link_to('my article', 'article/read?title=Finance_in_France',
array(
  'class' => 'foobar',
  'target' => '_blank'
)) ?>
```

```
// Additional options as a string (same result)
<?php echo link_to('my article', 'article/
read?title=Finance_in_France','class=foobar target=_blank') ?>
=> <a href="/routed/url/to/Finance_in_France" class="foobar"
target="_blank">my article</a>
```

你还可以为链接辅助函数添加 symfony 特有的选项：confirm 和 popup。第一个选项在单击链接时显示 JavaScript 确认对话框，第二个选项在新窗口中打开链接，如清单 9-10 所示。

### 清单 9-10 - 链接辅助函数的 'confirm' 和 'popup' 选项

```
<?php echo link_to('delete item', 'item/delete?id=123', 'confirm=Are you
sure?') ?>
=> <a onclick="return confirm('Are you sure?');"
href="/routed/url/to/delete/123.html">delete item</a>
```

```
<?php echo link_to('add to cart', 'shoppingCart/add?id=100', 'popup=true') ?>
=> <a onclick="window.open(this.href);return false;"
href="/fo_dev.php/shoppingCart/add/id/100.html">add to cart</a>
```

```
<?php echo link_to('add to cart', 'shoppingCart/add?id=100', array(
  'popup' => array('popupWindow', 'width=310,height=400,left=320,top=0')
)) ?>
=> <a onclick="window.open(this.href,'popupWindow',
'width=310,height=400,left=320,top=0');return false;"
href="/fo_dev.php/shoppingCart/add/id/100.html">add to cart</a>
```

这些选项可以组合使用。

### 假的 GET 和 POST 选项

有时 Web 开发人员使用 GET 请求来实际执行 POST。例如，考虑以下 URL：

```
http://www.example.com/index.php/shopping_cart/add/id/100
```

此请求会更改应用程序中包含的数据，例如将商品添加到存储在会话或数据库中的购物车对象。此 URL 可以被加入书签、缓存，并被搜索引擎索引。想象一下，使用此技术的网站的数据库或网站指标可能会发生所有不好的事情。事实上，此请求应被视为 POST，因为搜索引擎机器人在索引时不会执行 POST 请求。

symfony 提供了一种将 link_to() 或 button_to() 辅助函数的调用转换为实际 POST 的方法。只需添加 post=true 选项，如清单 9-11 所示。

### 清单 9-11 - 使链接调用 POST 请求

```
<?php echo link_to('go to shopping cart', 'shoppingCart/add?id=100',
array('post' => true)) ?>
==> <a onclick="f = document.createElement('form');
document.body.appendChild(f);
f.method = 'POST'; f.action = this.href; f.submit();return false;"
href="/shoppingCart/add/id/100.html">go to shopping cart</a>
```

这个 <a> 标签带有 href 属性，不支持 JavaScript 的浏览器（如搜索引擎机器人）将执行默认的 GET 并跟随链接。因此，你还必须限制你的动作仅响应 POST 方法，在动作开头添加类似以下的内容：

```
$this->forward404Unless($this->getRequest()->isMethod('post'));
```

只要确保不要在表单中的链接上使用此选项，因为它会生成自己的 <form> 标签。

将实际提交数据的链接标记为 POST 是个好习惯。

### 强制请求参数为 GET 变量

根据你的路由规则，作为参数传递给 link_to() 的变量会被转换为模式。如果 routing.yml 文件中的路由没有规则匹配内部 URI，默认规则会将 module/action?key=value 转换为 /module/action/key/value，如清单 9-12 所示。

### 清单 9-12 - 默认路由规则

```
<?php echo link_to('my article', 'article/read?title=Finance_in_France') ?>
==> <a href="/article/read/title/Finance_in_France">my article</a>
```

如果你确实需要保留 GET 语法——即以 ?key=value 形式传递请求参数——则应将需要强制的变量放在 URL 参数之外，放在 query_string 选项中。由于这也会与 URL 中的锚点冲突，你必须将其放在 anchor 选项中，而不是将其追加到内部 URI。所有链接辅助函数都接受这些选项，如清单 9-13 所示。

### 清单 9-13 - 使用 query_string 选项强制 GET 变量

```
<?php echo link_to('my article', 'article/read', array(
  'query_string' => 'title=Finance_in_France',
  'anchor' => 'foo'
)) ?>
==> <a href="/article/read?title=Finance_in_France#foo">my article</a>
```

一个将请求参数显示为 GET 变量的 URL 可以由客户端脚本解释，也可以由服务器端的 $_GET 和 $_REQUEST 变量解释。

## 资源辅助函数

第 7 章介绍了资源辅助函数 image_tag()、stylesheet_tag() 和 javascript_include_tag()，它们允许你在响应中包含图像、样式表或 JavaScript 文件。这些资源的路径不会经过路由系统处理，因为它们链接到实际位于公共 Web 目录下的资源。

你不需要为资源提及文件扩展名。symfony 会自动为图像、JavaScript 或样式表辅助函数调用添加 .png、.js 或 .css。此外，symfony 会自动在 web/images/、web/js/ 和 web/css/ 目录中查找这些资源。当然，如果你想包含特定文件格式或特定位置的文件，只需将完整文件名或完整文件路径作为参数即可。

要固定图像大小，请使用 size 属性。它期望以像素为单位、由 x 分隔的宽度和高度。

```
<?php echo image_tag('test', 'size=100x20') ?>
=> <img href="/images/test.png" width="100" height="20"/>
```

如果你希望资源包含在 <head> 部分中（针对 JavaScript 文件和样式表），则应该在模板中使用 use_stylesheet() 和 use_javascript() 辅助函数，而不是在布局中使用 _tag() 版本。它们将资源添加到响应中，这些资源会在 </head> 标签发送到浏览器之前被包含。

## 使用绝对路径

链接和资源辅助函数默认生成相对路径。要强制输出绝对路径，请将 absolute 选项设置为 true，如清单 9-14 所示。此技术适用于在电子邮件消息、RSS 订阅源或 API 响应中包含链接。

### 清单 9-14 - 获取绝对 URL 而非相对 URL

```
<?php echo url_for('article/read?title=Finance_in_France') ?>
=> '/routed/url/to/Finance_in_France'
<?php echo url_for('article/read?title=Finance_in_France', true) ?>
=> 'http://www.example.com/routed/url/to/Finance_in_France'

<?php echo link_to('finance', 'article/read?title=Finance_in_France') ?>
=> <a href="/routed/url/to/Finance_in_France">finance</a>
<?php echo link_to('finance', 'article/
read?title=Finance_in_France','absolute=true') ?>
=> <a href=" http://www.example.com/routed/url/to/
Finance_in_France">finance</a>

// The same goes for the asset helpers
<?php echo image_tag('test', 'absolute=true') ?>
<?php echo javascript_include_tag('myscript', 'absolute=true') ?>
```

## Mail 辅助函数

如今，收集电子邮件地址的机器人在 Web 上四处游荡，如果你在网站上显示电子邮件地址，几天之内就会成为垃圾邮件的受害者。这就是 symfony 提供 mail_to() 辅助函数的原因。

mail_to() 辅助函数接受两个参数：实际的电子邮件地址和应显示的字符串。额外选项接受一个 encode 参数，以输出在 HTML 中相当不可读的内容，浏览器可以理解，但机器人无法理解。

### 清单 9-25

```
<?php echo mail_to('myaddress@mydomain.com', 'contact') ?>
=> <a href="mailto:myaddress@mydomain.com">contact</a>
<?php echo mail_to('myaddress@mydomain.com', 'contact', 'encode=true') ?>
=> <a href="&#109;&#x61;... &#111;...">&#x65;...</a>
```

编码的电子邮件消息由随机十进制和十六进制实体编码器转换的字符组成。此技巧目前可阻止大多数地址收集垃圾邮件机器人，但请注意，收集技术发展迅速。

## 路由配置

路由系统做两件事：

- 它解释传入请求的外部 URL 并将其转换为内部 URI，以确定 module/action 和请求参数。
- 它将链接中使用的内部 URI 格式化为外部 URL（前提是你使用链接辅助函数）。

转换基于一组路由规则。这些规则存储在应用程序 config/ 目录下的 routing.yml 配置文件中。清单 9-15 显示了每个 symfony 项目都附带的默认路由规则。

### 清单 9-15 - 默认路由规则，位于 frontend/config/routing.yml

```
Listing 9-26
# default rules
homepage:
  url:   /
  param: { module: default, action: index }

# generic rules
# please, remove them by adding more specific rules
default_index:
  url:   /:module
  param: { action: index }

default:
  url:   /:module/:action/*
```

## 规则和模式

路由规则是外部 URL 与内部 URI 之间的双向关联。典型的规则由以下部分组成：

- 一个唯一标签，用于可读性和速度，并可被链接辅助函数使用





- 要匹配的模式（url 键）
- 请求参数值的数组（param 键）

模式可以包含通配符（由星号 * 表示）和命名通配符（以冒号 : 开头）。对命名通配符的匹配将成为请求参数值。例如，清单 9-15 中定义的默认规则将匹配类似 /foo/bar 的任何 URL，并将 module 参数设置为 foo，将 action 参数设置为 bar。

命名通配符可以用斜杠或点分隔，因此你可以编写如下模式：

```
my_rule:
  url:   /foo/:bar.:format
  param: { module: mymodule, action: myaction }
```

这样一来，像 'foo/12.xml' 这样的外部 URL 将匹配 my_rule 并在 mymodule/myaction 中执行，带有两个参数：$bar=12 和 $format=xml。你可以通过更改 sfPatternRouting 工厂配置中的 segment_separators 参数值来添加更多分隔符（参见第 19 章）。

路由系统会从上到下解析 routing.yml 文件，并在第一个匹配处停止。这就是为什么你必须将自己的规则添加到默认规则之上的原因。例如，URL /foo/123 匹配清单 9-16 中定义的两条规则，但 symfony 会先测试 my_rule:，由于该规则匹配成功，它甚至不会测试 default: 规则。请求由 mymodule/myaction 处理，bar 设置为 123（而不是由 foo/123 处理）。

### 清单 9-16 - 规则按从上到下的顺序解析

```
my_rule:
  url: /foo/:bar
  param: { module: mymodule, action: myaction }

# default rules
default:
  url:  /:module/:action/*
```

创建新操作时，并不意味着你必须为它创建路由规则。如果默认 module/action 模式适合你，那么就忘掉 routing.yml 文件吧。但是，如果你想自定义操作的外部 URL，请在默认规则之上添加一条新规则。

清单 9-17 展示了更改 article/read 操作外部 URL 格式的过程。

### 清单 9-17 - 更改 article/read 操作的外部 URL 格式

```
<?php echo url_for('article/read?id=123') ?>
=> /article/read/id/123   // Default formatting

// To change it to /article/123, add a new rule at the beginning
// of your routing.yml
article_by_id:
  url:   /article/:id
  param: { module: article, action: read }
```

问题是，清单 9-17 中的 article_by_id 规则会破坏 article 模块中所有其他操作的默认路由。事实上，像 article/delete 这样的 URL 将匹配此规则而不是默认规则，并以 delete 作为 id 调用 read 操作，而不是调用 delete 操作。为了解决这个问题，你必须添加模式约束，使 article_by_id 规则仅匹配 id 通配符为整数的 URL。

## 模式约束

当 URL 可以匹配多条规则时，你必须通过向模式添加约束或要求来细化规则。要求是一组正则表达式，通配符必须匹配这些表达式，规则才能匹配。

例如，要修改 article_by_id 规则，使其仅匹配 id 参数为整数的 URL，请向规则添加一行，如清单 9-18 所示。

### 清单 9-18 - 向路由规则添加要求

```
article_by_id:
  url: /article/:id
  param: { module: article, action: read }
  requirements: { id: \d+ }
```

现在，article/delete URL 不再能匹配 article_by_id 规则，因为 'delete' 字符串不满足要求。因此，路由系统将继续在以下规则中查找匹配项，并最终找到默认规则。

## 永久链接

路由的一个良好安全准则是尽可能隐藏主键，并用有意义的字符串替换它们。如果你想根据文章标题而不是 ID 来访问文章，会怎样呢？这将使外部 URL 如下所示：

```
http://www.example.com/article/Finance_in_France
```

为此，你需要创建一个新的 permalink 操作，它将使用 slug 参数而不是 id 参数，并为其添加一条新规则：

```
article_by_id:
  url: /article/:id
  param: { module: article, action: read }
  requirements: { id: \d+ }
```

```
article_by_slug:
  url: /article/:slug
  param: { module: article, action: permalink }
```

permalink 操作需要根据标题确定请求的文章，因此你的模型必须提供一个适当的方法。

```
public function executePermalink($request)
{
 $article = ArticlePeer::retrieveBySlug($request->getParameter('slug'));
 $this->forward404Unless($article); // Display 404 if no article matches slug
 $this->article = $article; // Pass the object to the template
}
```

你还需要在模板中将 read 操作的链接替换为 permalink 操作的链接，以便正确格式化内部 URL。

```
// Replace
<?php echo link_to('my article', 'article/read?id='.$article->getId()) ?>
```

```
// With
<?php echo link_to('my article', 'article/permalink?slug='.$article->getSlug()) ?>
```

由于要求行，像 /article/Finance_in_France 这样的外部 URL 将匹配 article_by_slug 规则，即使 article_by_id 规则出现在前面。

请注意，由于文章将通过 slug 检索，你应该在 Article 模型描述中为 slug 列添加索引以优化数据库性能。

## 设置默认值

你可以为命名通配符指定默认值，即使未定义参数，规则也能工作。在 param: 数组中设置默认值。

例如，如果未设置 id 参数，article_by_id 规则不匹配。你可以强制它，如清单 9-19 所示。

### 清单 9-19 - 为通配符设置默认值

```
article_by_id:
  url: /article/:id
  param: { module: article, action: read, id: 1 }
```

默认参数不需要是模式中存在的通配符。在清单 9-20 中，即使 URL 中不存在 display 参数，它也将取值 true。

### 清单 9-20 - 为请求参数设置默认值

```
article_by_id:
  url: /article/:id
  param: { module: article, action: read, id: 1, display: true }
```

如果你仔细看，可以看到 article 和 read 也是模式中未找到的 module 和 action 变量的默认值。

> 你可以通过调用 sfRouting::setDefaultParameter() 方法为所有路由规则定义默认参数。例如，如果你希望所有规则的 theme 参数默认设置为 default，请将 $this->context->getRouting()->setDefaultParameter('theme', 'default'); 添加到你的某个全局过滤器中。

## 使用规则名称加速路由

如果规则标签以 '@' 符号开头，则链接助手可以接受规则标签，而不是模块/操作对，如清单 9-21 所示。

### 清单 9-21 - 使用规则标签代替模块/操作

```
<?php echo link_to('my article', 'article/read?id='.$article->getId()) ?>
// can also be written as
<?php echo link_to('my article', '@article_by_id?id='.$article->getId()) ?>
// or the fastest one (does not need extra parsing):
<?php echo link_to('my article', 'article_by_id', array('id' => $article->getId())) ?>
```

这个技巧有利有弊。优点如下：

- 内部 URI 的格式化速度更快，因为 symfony 不需要浏览所有规则来找到与链接匹配的那条。在带有大量路由超链接的页面中，如果你使用规则标签而不是模块/操作对，性能提升将很明显。

- 使用规则标签有助于抽象操作背后的逻辑。如果你决定更改操作名称但保持 URL 不变，只需简单更改 routing.yml 文件即可。所有 link_to() 调用仍然可以正常工作，无需进一步更改。

- 使用规则名称，调用逻辑更加明显。即使你的模块和操作有明确的名称，调用 @display_article_by_slug 通常也比调用 article/display 更好。

- 通过阅读 routing.yml 文件，你确切知道哪些操作是启用的。

另一方面，缺点是添加新超链接变得不那么直观，因为你始终需要参考 routing.yml 文件来找出操作应使用哪个标签。而且在大型项目中，你最终会有大量路由规则，使得维护它们变得有点困难。在这种情况下，你应该将应用程序打包为多个插件，每个插件定义一组有限的功能。

然而，经验表明，从长远来看，使用路由规则是最佳选择。




> 在测试期间（在开发环境中），如果您想检查浏览器中给定请求匹配了哪条规则，请展开 Web 调试工具栏的“日志”部分，并查找指定“matched route XXX”的一行。有关 Web 调试模式的更多信息，请参见第 16 章。

## 在不使用 routing.yml 的情况下创建规则

与大多数配置文件一样，routing.yml 是定义路由规则的一种解决方案，但不是唯一的解决方案。您可以在 PHP 中定义规则，但在调用 dispatch() 之前，因为该方法根据当前路由规则确定要执行的操作。在 PHP 中定义规则授权您创建动态规则，具体取决于配置或其他参数。

处理路由规则的对象是 sfPatternRouting 工厂。它可以通过 sfContext::getInstance()->getRouting() 在代码的每个部分中使用。其 prependRoute() 方法在 routing.yml 中定义的现有规则之上添加一条新规则。它期望两个参数：路由名称和一个 sfRoute 对象。例如，清单 9-18 中显示的 routing.yml 规则定义与清单 9-22 中显示的 PHP 代码等效。

### 清单 9-22 - 在 PHP 中定义规则

```php
sfContext::getInstance()->getRouting()->prependRoute(
 'article_by_id',          // Route name
 new sfRoute('/article/:id', array('module' => 'article', 'action' =>
 'read'), array('id' => '\d+')),   // Route object
);
```

sfRoute 类构造函数接受三个参数：一个模式、一个关联数组形式的默认值，以及另一个用于要求的关联数组。

sfPatternRouting 类还有其他用于手动处理路由的有用方法：clearRoutes()、hasRoutes() 等等。有关更多信息，请参阅 API 文档 39。

> 一旦您开始完全理解本书中介绍的概念，您就可以通过浏览在线 API 文档或，更好的，symfony 源代码来加深对框架的理解。本书无法描述 symfony 的所有调整和参数。然而，在线文档是无限的。

> 路由类可以在 factories.yml 配置文件中进行配置（要更改默认路由类，请参见第 17 章）。本章介绍的是 sfPatternRouting 类，它是默认配置的路由类。

## 在操作中处理路由

如果您需要检索有关当前路由的信息——例如，为将来的“back to page xxx”链接做准备——应该使用 sfPatternRouting 对象的方法。getCurrentInternalUri() 方法返回的 URI 可以用于 link_to() 辅助函数的调用，如清单 9-23 所示。

### 清单 9-23 - 使用 sfRouting 获取有关当前路由的信息

```php
// If you require a URL like
http://myapp.example.com/article/21

$routing = $this->getContext()->getRouting();

// Use the following in article/read action
$uri = $routing->getCurrentInternalUri();
=> article/read?id=21

$uri = $routing->getCurrentInternalUri(true);
=> @article_by_id?id=21

$rule = $routing->getCurrentRouteName();
=> article_by_id

// If you just need the current module/action names,
// remember that they are actual request parameters
$module = $request->getParameter('module');
$action = $request->getParameter('action');
```

如果您需要在操作中将内部 URI 转换为外部 URL——就像模板中的 url_for() 所做的那样——请使用 sfController 对象的 genUrl() 方法，如清单 9-24 所示。

### 清单 9-24 - 使用 sfController 转换内部 URI

```php
$uri = 'article/read?id=21';

$url = $this->getController()->genUrl($uri);
=> /article/21

$url = $this->getController()->genUrl($uri, true);
=> http://myapp.example.com/article/21
```

## 总结

路由是一种双向机制，旨在允许格式化外部 URL，使其更加用户友好。URL 重写是必需的，以便在每个项目的一个应用程序的 URL 中省略前置控制器名称。如果您希望路由系统双向工作，则每次需要在模板中输出 URL 时都必须使用链接辅助函数。routing.yml 文件配置路由系统的规则，并使用优先级顺序和规则要求。settings.yml 文件包含有关外部 URL 中前置控制器名称存在情况以及可能后缀的其他设置。

# 第 10 章 表单

处理表单输入的显示、表单提交的验证以及表单的所有特殊情况是 Web 开发中最复杂的任务之一。幸运的是，symfony 为一个非常强大的表单子框架提供了简单的接口，并帮助您在几行代码内设计和处理任何复杂程度的表单。

## 显示表单

一个包含姓名、电子邮件、主题和消息字段的简单联系表单通常呈现如下：

| 姓名 | |
|---|---|
| 电子邮件 | |
| 主题 | 主题 A ▼ |
| | 主题 A |
| | 主题 B |
| | 主题 C |
| 消息 | |
| | 提交查询 |

在 symfony 中，表单是在操作中定义并传递给模板的一个对象。要显示表单，必须首先定义它包含的字段 - symfony 使用术语“widget”。最简单的方法是在操作方法中创建一个新的 sfForm 对象。

```php
// in modules/foo/actions/actions.class.php
public function executeContact($request)
{
$this->form = new sfForm();
$this->form->setWidgets(array(
'name' => new sfWidgetFormInputText(),
'email' => new sfWidgetFormInputText(array('default' =>
'me@example.com')),
'subject' => new sfWidgetFormChoice(array('choices' => array('Subject
A', 'Subject B', 'Subject C'))),
'message' => new sfWidgetFormTextarea(),
)));
}
```

sfForm::setWidgets() 期望一个 widget 名称/对象的关联数组。sfWidgetFormInputText、sfWidgetFormChoice 和 sfWidgetFormTextarea 是 symfony 提供的众多 widget 类中的一些；您将在本章后面找到完整列表。

上一个示例显示了您可以使用的两个 widget 选项：default 设置 widget 值，适用于所有 widget。choices 是 choice widget 特有的选项（它呈现为下拉列表）：它定义用户可选择的可用选项。

因此，foo/contact 操作定义了一个表单对象，然后通过 $form 变量将其传递给 contactSuccess 模板。模板可以使用此对象在 HTML 中呈现表单的各个部分。最简单的方法是调用 echo $form，这将呈现带有标签的所有字段作为表单控件。您也可以使用表单对象生成表单标签：

### 清单 10-2

```php
// in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
<table>
<?php echo $form ?>
<tr>
<td colspan="2">
<input type="submit" />
</td>
</tr>
</table>
</form>
```

使用传递给 setWidgets() 的参数，symfony 拥有足够的信息来正确显示表单。生成的 HTML 与上面的屏幕截图完全相同，其底层代码如下：

### 清单 10-3

```html
<form action="/frontend_dev.php/foo/contact" method="POST">
<table>
<tr>
<th><label for="name">Name</label></th>
<td><input type="text" name="name" id="name" /></td>
</tr>
<tr>
<th><label for="email">Email</label></th>
<td><input type="text" name="email" id="email"
value="me@example.com" /></td>
</tr>
<tr>
<th><label for="subject">Subject</label></th>
<td>
<select name="subject" id="subject">
<option value="0">Subject A</option>
<option value="1">Subject B</option>
<option value="2">Subject C</option>
</select>
</td>
</tr>
<tr>
<th><label for="message">Message</label></th>
<td><textarea rows="4" cols="30" name="message"
id="message"></textarea></td>
</tr>
<tr>
<td colspan="2">
<input type="submit" />
</td>
</tr>
</table>
</form>
```

每个 widget 都会生成一个包含 `<label>` 标签和表单输入标签的表格行。Symfony 通过将 widget 名称大写来推断标签名称（`subject` widget 名称生成“Subject”标签）。至于输入标签，它取决于 widget 类型。Symfony 根据每个 widget 的名称添加一个 `id` 属性。最后，表单的呈现始终符合 XHTML 标准。

## 自定义表单显示

使用 echo $form 对于原型开发非常好，但您可能希望完全控制生成的 HTML 代码。表单对象包含一个字段数组，调用 echo $form 实际上会遍历字段并逐个呈现它们。要获得更多控制权，您可以手动遍历字段，并在每个字段上调用 renderRow()。下一个清单生成与之前完全相同的 HTML 代码，但模板会逐个输出每个字段：

```php
// in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
<table>
<?php echo $form['name']->renderRow() ?>
<?php echo $form['email']->renderRow() ?>
<?php echo $form['subject']->renderRow() ?>
<?php echo $form['message']->renderRow() ?>
<tr>
<td colspan="2">
<input type="submit" />
</td>
</tr>
</table>
</form>
```

逐个呈现字段允许您更改显示顺序，还可以自定义其外观。`renderRow()` 将 HTML 属性列表作为第一个参数，因此您可以定义自定义类、`id` 或 JavaScript 事件处理程序。`renderRow()` 的第二个参数是一个可选标签，用于覆盖从 widget 名称推断的标签。以下是联系表单的自定义示例：

```php
// in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
<table>
<?php echo $form['name']->renderRow(array('size' => 25, 'class' =>
'foo'), 'Your Name') ?>
<?php echo $form['email']->renderRow(array('onclick' => 'this.value =
```





```php
"";'), 'Your Email') ?>
<?php echo $form['message']->renderRow() ?>
<tr>
<td colspan="2">
<input type="submit" />
</td>
</tr>
</table>
</form>
```

但也许你需要将每个字段的标签和输入放在 `<li>` 标签中，而不是放在 `<tr>` 标签中。一个字段“行”由一个标签、一个可选的错误消息（由验证系统添加，本章后面将解释）、一段帮助文本和一个小部件组成（注意小部件可以由多个表单控件组成）。正如你可以逐个输出表单的各个字段一样，你也可以独立渲染表单的各个部分。不要使用 renderRow()，而可以使用 render()（用于小部件）、renderError()、renderLabel() 和 renderHelp() 中的任意一个。例如，如果你想使用 `<li>` 标签渲染整个表单，请按如下方式编写模板：

```php
// in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
<ul>
<?php foreach ($form as $field): ?>
<li>
<?php echo $field->renderLabel() ?>
<?php echo $field->render() ?>
</li>
<?php endforeach; ?>
<li>
<input type="submit" />
</li>
</ul>
</form>
```

这将呈现为以下 HTML：

```html
<form action="/frontend_dev.php/foo/contact" method="POST">
<ul>
<li>
<label for="name">Name</label>
<input type="text" name="name" id="name" />
</li>
<li>
<label for="email">Email</label>
<input type="text" name="email" id="email" />
</li>
<li>
<label for="subject">Subject</label>
<select name="subject" id="subject">
<option value="0">Subject A</option>
<option value="1">Subject B</option>
<option value="2">Subject C</option>
</select>
</li>
<li>
<label for="message">Message</label>
<textarea rows="4" cols="30" name="message" id="message"></textarea>
</li>
<li>
<input type="submit" />
</li>
</ul>
</form>
```

字段行是格式化程序对表单字段所有元素（标签、错误消息、帮助文本、表单输入）的表示。默认情况下，symfony 使用表格格式化程序，这就是为什么 renderRow() 返回一组 `<tr>`、`<th>` 和 `<td>` 标签的原因。或者，你可以通过为表单指定备选列表格式化程序来获得与上面相同的 HTML 代码，如下所示：

```php
// in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
<ul>
<?php echo $form->renderUsing('list') ?>
<li>
<input type="submit" />
</li>
</ul>
</form>
```

查看 sfWidgetFormSchemaFormatter 类的 API 文档，了解如何创建自己的格式化程序。

## 表单小部件

你可以使用许多可用的表单小部件来构建表单。所有小部件至少接受默认选项。

你还可以在创建表单时定义小部件的标签，甚至其 HTML 属性：

```php
$this->form = new sfForm();
$this->form->setWidgets(array(
'name' => new sfWidgetFormInput(array('label' => 'Your Name'), array('size' => 25, 'class' => 'foo')),
'email' => new sfWidgetFormInput(array('default' => 'me@example.com', 'label' => 'Your Email'), array('onclick' => 'this.value = "";')),
'subject' => new sfWidgetFormChoice(array('choices' => array('Subject A', 'Subject B', 'Subject C'))),
'message' => new sfWidgetFormTextarea(array(), array('rows' => '20', 'cols' => 5)),
));
```

Symfony 使用这些参数来显示小部件，你仍然可以通过在模板中向 renderRow() 传递自定义参数来覆盖它们。

作为调用 setWidgets() 并传入关联数组的替代方案，你可以多次调用 setWidget($name, $widget) 方法。

### 标准小部件

以下是可用小部件类型的列表，以及它们通过 renderRow() 转换为 HTML 的方式：

```php
// Text input
$form->setWidget('full_name', new sfWidgetFormInput(array('default' => 'John Doe')));
<label for="full_name">Full Name</label>
<input type="text" name="full_name" id="full_name" value="John Doe" />
// Textarea
$form->setWidget('address', new sfWidgetFormTextarea(array('default' => 'Enter your address here'), array('cols' => 20, 'rows' => 5)));
<label for="address">Address</label>
<textarea name="address" id="address" cols="20" rows="5">Enter your address here</textarea>
// Password input
// Note that 'password' type widgets don't take a 'default' parameter for security reasons
$form->setWidget('pwd', new sfWidgetFormInputPassword());
<label for="pwd">Pwd</label>
<input type="password" name="pwd" id="pwd" />
// Hidden input
$form->setWidget('id', new sfWidgetFormInputHidden(array('default' => 1234)));
<input type="hidden" name="id" id="id" value="1234" />
// Checkbox
$form->setWidget('single', new sfWidgetFormInputCheckbox(array('value_attribute_value' => 'single', 'default' => true)));
<label for="single">Single</label>
<input type="checkbox" name="single" id="single" value="true" checked="checked" />
```

每个小部件可用的选项比这里展示的更多。查看小部件 API 文档，了解每个小部件期望什么以及如何渲染的完整描述。

### 列表小部件

每当用户需要在值列表中做出选择，并且无论他们可以在此列表中选择一个还是多个选项时，一个小部件就能满足所有需求：选择小部件。根据两个可选参数（multiple 和 expanded），该小部件的渲染方式不同：

| | multiple=false（默认值） | multiple=true |
| --- | --- | --- |
| expanded=false（默认值） | 下拉列表（`<select>`） | 下拉框（`<select multiple>`） |
| expanded=true | 单选按钮列表 | 复选框列表 |

选择小部件至少需要一个 choices 参数，并使用关联数组来定义每个选项的值和文本。以下是每种语法的示例：

```php
// Dropdown list (select)
$form->setWidget('country', new sfWidgetFormChoice(array(
    'choices' => array('' => 'Select from the list', 'us' => 'USA', 'ca' => 'Canada', 'uk' => 'UK', 'other'),
    'default' => 'uk',
)));
// symfony renders the widget in HTML as
<label for="country">Country</label>
<select id="country" name="country">
<option value="">Select from the list</option>
<option value="us">USA</option>
<option value="ca">Canada</option>
<option value="uk" selected="selected">UK</option>
<option value="0">other</option>
</select>
```

```php
// Dropdown list with multiple choices
$form->setWidget('languages', new sfWidgetFormChoice(array(
    'multiple' => 'true',
    'choices' => array('en' => 'English', 'fr' => 'French', 'other'),
    'default' => array('en', 0)
)));
// symfony renders the widget in HTML as
<label for="languages">Language</label>
<select id="languages" multiple="multiple" name="languages[]">
<option value="en" selected="selected">English</option>
<option value="fr">French</option>
<option value="0" selected="selected">other</option>
</select>
```

```php
// List of Radio buttons
$form->setWidget('gender', new sfWidgetFormChoice(array(
    'expanded' => true,
    'choices' => array('m' => 'Male', 'f' => 'Female'),
    'class' => 'gender_list'
)));
// symfony renders the widget in HTML as
<label for="gender">Gender</label>
<ul class="gender_list">
<li><input type="radio" name="gender" id="gender_m" value="m"><label
for="gender_m">Male</label></li>
<li><input type="radio" name="gender" id="gender_f" value="f"><label
for="gender_f">Female</label></li>
</ul>
```

```php
// List of checkboxes
$form->setWidget('interests', new sfWidgetFormChoice(array(
    'multiple' => 'true',
    'expanded' => true,
    'choices' => array('Programming', 'Other')
)));
// symfony renders the widget in HTML as
<label for="interests">Interests</label>
<ul class="interests_list">
<li><input type="checkbox" name="interests[]" id="interests_0"
value="0"><label for="interests_0">Programming</label></li>
<li><input type="checkbox" name="interests[]" id="interests_1"
value="1"><label for="interests_1">Other</label></li>
</ul>
```

> 你可能已经注意到，symfony 根据小部件的名称和值的组合自动为每个表单输入定义 id 属性。你可以逐个小部件覆盖 id 属性，或者也可以使用 sfWidgetForm 类的 setIdFormat() 方法为整个表单设置全局规则：

```php
Listing 10-13
// in modules/foo/actions/actions.class.php
$this->form = new sfForm();
$this->form->getWidgetSchema()->setIdFormat('my_form_%s');
```

### 外键小部件

通过表单编辑 Model 对象时，总会出现一个特定的选择列表：即可以与当前对象关联的对象列表。当模型通过一对一或多对多关系关联时会发生这种情况。幸运的是，symfony 捆绑的 sfPropelPlugin 提供了专门用于这些情况的 sfWidgetFormPropelChoice 小部件（sfDoctrinePlugin 提供了类似的 sfWidgetFormDoctrineChoice 小部件）。

例如，如果一个 Section 包含多个 Articles，那么在编辑文章时，你应该能够从现有列表中选择一个 Section。为此，ArticleForm 应该使用 sfWidgetFormPropelChoice 小部件：

```php
Listing 10-14
// in modules/foo/actions/actions.class.php
$articleForm = new sfForm();
$articleForm->setWidgets(array(
  'id' => sfWidgetFormInputHidden(),
  'title' => sfWidgetFormInputText(),
  'section_id' => sfWidgetFormPropelChoice(array(
    'model' => 'Section',
    'column' => 'name'
  )
));
```

这将显示现有 Section 列表……前提是你在 Section 模型类中定义了 __toString() 方法。这是因为 symfony 首先检索可用的 Section 对象，并尝试输出每个对象来填充选择小部件。因此，Section 模型至少应包含以下方法：

```php
Listing 10-15
// in lib/model/Section.php
public function __toString()
{
  return $this->getName();
}
```

sfWidgetFormPropelChoice 小部件是 sfWidgetFormChoice 小部件的扩展，因此你可以使用 multiple 选项来处理多对多关系，并使用 expanded 选项来更改小部件的渲染方式。

如果你想以特殊方式对选项列表进行排序，或对其进行过滤以仅显示可用选项的一部分，请使用 criteria 选项将 Criteria 对象传递给小部件。Doctrine 支持同样的自定义：你可以使用 query 选项将 Doctrine_Query 对象传递给小部件。





## 日期窗口小部件

日期和时间窗口小部件输出一组下拉列表，其中包含可用于天、月、年、小时或分钟的可用值。

```
// Date
$years = range(1950, 1990);
$form->setWidget('dob', new sfWidgetFormDate(array(
    'label' => 'Date of birth',
    'default' => '01/01/1950', // can be a timestamp or a string understandable by strtotime()
    'years' => array_combine($years, $years)
)));
// symfony renders the widget in HTML as
<label for="dob">Date of birth</label>
<select id="dob_month" name="dob[month]">
<option value=""/>
<option selected="selected" value="1">01</option>
<option value="2">02</option>
...
<option value="12">12</option>
</select> /
<select id="dob_day" name="dob[day]">
<option value=""/>
<option selected="selected" value="1">01</option>
<option value="2">02</option>
...
<option value="31">31</option>
</select> /
<select id="dob_year" name="dob[year]">
<option value=""/>
<option selected="selected" value="1950">1950</option>
<option value="1951">1951</option>
...
<option value="1990">1990</option>
</select>

// Time
$form->setWidget('start', new sfWidgetFormTime(array('default' => '12:00')));
// symfony renders the widget in HTML as
<label for="start">Start</label>
<select id="start_hour" name="start[hour]">
<option value=""/>
<option value="0">00</option>
...
<option selected="selected" value="12">12</option>
...
<option value="23">23</option>
</select> :
<select id="start_minute" name="start[minute]">
<option value=""/>
<option selected="selected" value="0">00</option>
<option value="1">01</option>
...
<option value="59">59</option>
</select>

// Date and time
$form->setWidget('end', new sfWidgetFormDateTime(array('default' => '01/01/2008 12:00')));
// symfony renders the widget in HTML as 5 dropdown lists for month, day, year, hour, minute
```

当然，你可以自定义日期格式，以欧洲样式而不是国际样式（%day%/%month%/%year% 而不是 %month%/%day%/%year%）来显示，你可以改为每天 2x12 小时而不是 24 小时，你可以为每个下拉框的第一个选项定义自定义值，并且可以为可能的值定义限制。再次提醒，请查看 API 文档，以了解有关日期和时间窗口小部件选项的更多详细信息。

日期窗口小部件是 symfony 中窗口小部件功能的一个很好示例。窗口小部件不仅仅是简单的表单输入。它可以是多个输入的组合，symfony 可以以透明的方式呈现和读取它们。

## 国际化窗口小部件

在多语言应用程序中，日期必须按照用户区域设置的格式显示（有关区域设置和本地化的详细信息，请参见第 13 章）。为了便于在表单中进行此本地化，symfony 提供了一个 sfWidgetFormI18nDate 窗口小部件，它需要用户区域设置来决定日期格式化参数。你还可以指定 month_format，以使月份下拉列表显示月份名称（用户语言）而不是数字。

```
// Date
$years = range(1950, 1990);
$form->setWidget('dob', new sfWidgetFormI18nDate(array(
  'culture'     => $this->getUser()->getCulture(),
  'month_format' => 'name',    // Use any of 'name' (default), 'short_name', and 'number'
  'label'       => 'Date of birth',
  'default'     => '01/01/1950',
  'years'       => array_combine($years, $years)
)));
// For an English-speaking user, symfony renders the widget in HTML as
<label for="dob">Date of birth</label>
<select id="dob_month" name="dob[month]">
<option value=""/>
<option selected="selected" value="1">January</option>
<option value="2">February</option>
...
<option value="12">December</option>
</select>
<select id="dob_day" name="dob[day]">...</select>
<select id="dob_year" name="dob[year]">...</select>
// For an French-speaking user, symfony renders the widget in HTML as
<label for="dob">Date of birth</label>
<select id="dob_day" name="dob[day]">...</select>
<select id="dob_month" name="dob[month]">
<option value=""/>
<option selected="selected" value="1">Janvier</option>
<option value="2">Février</option>
...
<option value="12">Décembre</option>
</select>
<select id="dob_year" name="dob[year]">...</select>
```

时间（sfWidgetFormI18nTime）和日期时间（sfWidgetFormI18nDateTime）也有类似的窗口小部件。

有两个在许多表单中出现且也依赖于用户区域设置的下拉列表：国家和语言选择器。symfony 特别为此目的提供了两个窗口小部件。你不需要在这些窗口小部件中定义选项，因为 symfony 将使用用户的语言（前提是用户讲 symfony 中引用的 250 种语言之一）填充国家和语言列表。

```
// Country list
$form->setWidget('country', new sfWidgetFormI18nCountryChoice(array('default' => 'UK')));
// For an English-speaking user, symfony renders the widget in HTML as
<label for="country">Country</label>
<select id="country" name="country">
<option value=""/>
<option value="AD">Andorra</option>
<option value="AE">United Arab Emirates</option>
...
<option value="ZW">Zimbabwe</option>
</select>

// Language list
$form->setWidget('language', new sfWidgetFormI18nLanguageChoice(array(
'languages' => array('en', 'fr', 'de'), // optional restricted list of languages
'default' => 'en'
)));
// For an English-speaking user, symfony renders the widget in HTML as
<label for="language">Language</label>
<select id="language" name="language">
<option value=""/>
<option value="de">German</option>
<option value="en" selected="selected">English</option>
<option value="fr">French</option>
</select>
```

## 文件窗口小部件

处理文件输入标签并不比处理其他窗口小部件更复杂：

```
// Input file
$form->setWidget('picture', new sfWidgetFormInputFile());
// symfony renders the widget in HTML as
<label for="picture">Picture</label>
<input id="picture" type="file" name="picture"/>
// Whenever a form has a file widget, renderFormTag() outputs a <form> tag with the multipart option
```

```
// Editable input file
$form->setWidget('picture', new sfWidgetFormInputFileEditable(array('default' => '/images/foo.png')));
// symfony renders the widget in HTML as a file input tag, together with a preview of the current file
```

> 第三方插件提供许多其他窗口小部件。你可以轻松找到富文本编辑器窗口小部件、日历窗口小部件，或各种 JavaScript 库的其他“富 UI”窗口小部件。有关更多详细信息，请查看插件存储库40。

## 处理表单提交

当用户填写表单并提交时，Web 应用程序服务器需要从请求中检索数据并对其进行一些处理。sfForm 类提供了所有必要的方法，只需几行代码即可完成该操作。

## 简单表单处理

由于窗口小部件输出为常规 HTML 表单字段，在处理表单提交的操作中获取其值就像检查相关请求参数一样容易。对于示例联系表单，操作可能如下所示：

```
Listing 10-20 // in modules/foo/actions/actions.class.php
public function executeContact($request)
{
    // Define the form
    $this->form = new sfForm();
    $this->form->setWidgets(array(
        'name' => new sfWidgetFormInputText(),
        'email' => new sfWidgetFormInput(array('default' =>
            'me@example.com')),
        'subject' => new sfWidgetFormChoice(array('choices' => array('Subject A', 'Subject B', 'Subject C'))),
        'message' => new sfWidgetFormTextarea(),
    ));
    // Deal with the request
    if ($request->isMethod('post'))
    {
        // Handle the form submission
        $name = $request->getParameter('name');
        // Do stuff
        // ...
        $this->redirect('foo/bar');
    }
}
```

如果请求方法是 'GET'，此操作将以 sfView::SUCCESS 结束，因此呈现 contactSuccess 模板以显示表单。如果请求方法是 'POST'，则该操作处理表单提交并重定向到另一个操作。要使此操作起作用，<form> 的目标操作必须与显示它的操作相同。这就是为什么之前的示例使用 foo/contact 作为表单目标的原因：

```
Listing 10-21 // in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
...
```




## 带数据验证的表单处理

在实际中，处理表单提交远不止获取用户输入的值。对于大多数表单提交，应用程序控制器需要：

- 1. 检查数据是否符合一组预定义的规则（必填字段、电子邮件格式等）
- 2. 可选地转换一些输入数据以使其可理解（修剪空格、将日期转换为 PHP 格式等）
- 3. 如果数据无效，则再次显示表单，并在适用的地方显示错误消息
- 4. 如果数据正确，则执行一些操作并重定向到另一个动作

Symfony 提供了一种自动方式，用于根据一组预定义规则验证提交的数据。首先，为每个字段定义一组验证器。其次，当表单提交时，将表单对象与用户提交的值“绑定”（即，检索用户提交的值并将其放入表单）。最后，要求表单检查数据是否有效。以下示例展示了如何检查从电子邮件小部件检索的值确实是一个电子邮件地址，以及检查消息的最小长度为 4 个字符：

```php
// in modules/foo/actions/actions.class.php
public function executeContact($request)
{
// Define the form
$this->form = new sfForm();
$this->form->setWidgets(array(
'name' => new sfWidgetFormInputText(),
'email' => new sfWidgetFormInput(array('default' => 'me@example.com')),
'subject' => new sfWidgetFormChoice(array('choices' => array('Subject A', 'Subject B', 'Subject C'))),
'message' => new sfWidgetFormTextarea(),
));
$this->form->setValidators(array(
'name' => new sfValidatorString(),
'email' => new sfValidatorEmail(),
'subject' => new sfValidatorString(),
'message' => new sfValidatorString(array('min_length' => 4)),
));
// Deal with the request
if ($request->isMethod('post'))
{
$this->form->bind(/* user submitted data */);
if ($this->form->isValid())
{
// Handle the form submission
// ...
$this->redirect('foo/bar');
}
}
}
```

setValidators() 使用与 setWidgets() 方法类似的语法。sfValidatorEmail 和 sfValidatorString 是众多 symfony 验证器类中的两个，将在本章后面列出。当然，sfForm 还提供 setValidator() 方法以逐个添加验证器。

要将请求数据放入表单并将它们绑定，请使用 sfForm::bind() 方法。表单必须绑定一些数据才能检查其有效性。

isValid() 检查所有注册的验证器是否通过。如果是，isValid() 返回 true，动作可以继续进行表单提交。如果表单无效，则动作以默认的 sfView::SUCCESS 结束并再次显示表单。但表单不仅仅是像第一次显示时那样带有默认值显示。表单输入将显示用户之前输入的数据，并且验证器未通过的位置会出现错误消息。

![](img/0f886a7f4cbcc3939be96e985ca35ff4_171_0.png)

> > 当表单遇到无效字段时，验证过程不会停止。isValid() 处理整个表单数据并检查所有字段的错误，以避免在用户更正错误并再次提交表单时显示新的错误消息。

## 使用干净的表单数据

在之前的示例中，我们没有定义绑定过程中表单接收的请求数据。问题在于请求不仅包含表单数据，还包含头部、Cookie、作为 GET 参数传递的参数等，所有这些都可能污染绑定过程。良好的做法是仅将表单数据传递给 bind() 方法。

幸运的是，symfony 提供了一种使用数组语法为所有表单输入命名的方法。在动作中定义表单时，使用 setNameFormat() 方法定义 name 属性格式，如下所示：

```php
// in modules/foo/actions/actions.class.php
// Define the form
$this->form->getWidgetSchema()->setNameFormat('contact[%s]');
```

这样，生成的所有表单输入都将呈现为 form[WIDGET_NAME] 这样的名称，而不是仅仅 WIDGET_NAME：

```html
<label for="contact_name">Name</label>
<input type="text" name="contact[name]" id="contact_name" />
...
<label for="contact_email">Email</label>
<input type="text" name="contact[email]" id="contact_email"
value="me@example.com" />
...
<label for="contact_subject">Subject</label>
<select name="contact[subject]" id="contact_subject">
<option value="0">Subject A</option>
<option value="1">Subject B</option>
<option value="2">Subject C</option>
</select>
...
<label for="contact_message">Message</label>
<textarea rows="4" cols="30" name="contact[message]"
id="contact_message"></textarea>
```

操作现在可以将 contact 请求参数检索到单个变量中。该变量包含用户在表单中输入的所有数据的数组：

```php
// in modules/foo/actions/actions.class.php
// Deal with the request
if ($request->isMethod('post'))
{
$this->form->bind($request->getParameter('contact'));
if ($this->form->isValid())
{
// Handle the form submission
$contact = $this->form->getValues();
$name = $contact['name'];
// Or to get a specific value
$name = $this->form->getValue('name');
// Do stuff
// ...
$this->redirect('foo/bar');
}
}
```

当 bind() 方法接收到参数数组时，symfony 会自动避免客户端注入额外字段。如果 contact 参数数组中包含原始表单定义中不存在的字段，此安全功能将导致表单验证失败。

你会注意到上面的动作代码与之前编写的代码还有一个区别。该动作使用表单对象传递的值数组（$form->getValues()），而不是来自请求的值。这是因为验证器有能力过滤并清理输入，因此依赖从表单对象（通过 getValues() 或 getValue()）检索的数据总是比依赖请求中的数据更好。对于复合字段（如日期小部件），getValues() 返回的数据已重新组合为原始名称：

```html
<label for="contact_dob">Date of birth</label>
<select id="contact_dob_month" name="contact[dob][month]">...</select> /
<select id="contact_dob_day" name="contact[dob][day]">...</select> /
<select id="contact_dob_year" name="contact[dob][year]">...</select>
```

// ...result in three request parameters in the action
$contact = $request->getParameter('contact');
$month = $contact['dob']['month'];
$day = $contact['dob']['day'];
$year = $contact['dob']['year'];
$dateOfBirth = mktime(0, 0, 0, $month, $day, $year);
// But if you use getValues(), you can retrieve directly a correct date
$contact = $this->form->getValues();
$dateOfBirth = $contact['dob'];

因此，请养成始终为表单字段使用数组语法（使用 setNameFormat()）以及始终使用干净的表单输出（使用 getValues()）的习惯。

## 自定义错误消息显示

上面截图中显示的错误消息来自哪里？您知道小部件由四个组件组成，错误消息是其中之一。实际上，默认的（表格）格式化程序将字段行呈现如下：

```php
Listing 10-27
<?php if ($field->hasError()): ?>
<tr>
<td colspan="2">
<?php echo $field->renderError() ?>        // List of errors
</td>
</tr>
<?php endif; ?>
<tr>
<th><?php echo $field->renderLabel() ?></th>        // Label
<td>
<?php echo $field->render() ?>        // Widget
<?php if ($field->hasHelp()): ?>
<br /><?php echo $field->renderHelp() ?>        // Help
<?php endif; ?>
</td>
</tr>
```

使用上述任何方法，您都可以自定义每个字段的错误消息出现的位置和方式。此外，如果表单无效，您还可以在表单顶部显示全局错误消息：

```php
Listing 10-28
<?php if ($form->hasErrors()): ?>
The form has some errors you need to fix.
<?php endif; ?>
```

## 自定义验证器

在表单中，所有字段都必须有验证器，并且默认情况下所有字段都是必填的。如果需要将字段设置为可选，请将 required 选项传递给验证器并将其设置为 false。例如，以下示例展示了如何将 name 字段设为必填，将 email 字段设为可选：

```php
Listing 10-29
$this->form->setValidators(array(
    'name'    => new sfValidatorString(),
    'email'   => new sfValidatorEmail(array('required' => false)),
    'subject' => new sfValidatorString(),
```

'message' => new sfValidatorString(array('min_length' => 4))));

您可以在一个字段上应用多个验证器。例如，您可能希望检查电子邮件字段是否同时满足 sfValidatorEmail 和 sfValidatorString 验证器，且最小长度为 4 个字符。在这种情况下，请使用 sfValidatorAnd 验证器来组合两个验证器，并将这两个 sfValidatorEmail 和 sfValidatorString 验证器作为参数传递：

```
$this->form->setValidators(array(
  'name' => new sfValidatorString(),
  'email' => new sfValidatorAnd(array(
    new sfValidatorEmail(),
    new sfValidatorString(array('min_length' => 4)),
  ), array('required' => false)),
  'subject' => new sfValidatorString(),
  'message' => new sfValidatorString(array('min_length' => 4))
));

```

如果两个验证器都有效，则电子邮件字段被声明为有效。同样，您可以使用 sfValidatorOr 验证器来组合多个验证器。如果其中一个验证器有效，则该字段被声明为有效。

每个无效的验证器都会在字段中生成一条错误消息。这些错误消息是英文的，但使用了 symfony 国际化辅助函数；如果您的项目使用其他语言，您可以使用 i18n 字典轻松翻译这些错误消息。或者，每个验证器都提供第三个参数来自定义其错误消息。每个验证器至少有两条错误消息：必填消息和无效消息。某些验证器可以针对不同目的显示错误消息，并且始终支持通过其第三个参数重写错误消息：

```
// in modules/foo/actions/actions.class.php
$this->form->setValidators(array(
  'name' => new sfValidatorString(),
  'email' => new sfValidatorEmail(array(), array(
    'required' => 'Please provide an email',
    'invalid' => 'Please provide a valid email address (me@example.com)'
  )),
  'subject' => new sfValidatorString(),
  'message' => new sfValidatorString(array('min_length' => 4), array(
    'required' => 'Please provide a message',
    'min_length' => 'Please provide a longer message (at least 4 characters)'
  ))
));

```

自然地，这些自定义消息将通过 i18n 辅助函数在模板中呈现，因此任何多语言应用程序也可以在字典中翻译自定义错误消息（详情请参见第 13 章）。

## 将验证器应用于多个字段

上面用于在表单上定义验证器的语法不允许验证两个字段是否共同有效。例如，在注册表单中，通常有两个密码字段必须匹配，否则注册会被拒绝。每个密码字段本身并不有效，只有与另一个字段关联时才有效。

这就是为什么您可以通过 setPostValidator() 设置“多重”验证器，以设置作用于多个值的验证器。后置验证器在所有其他验证器之后执行，并接收一个清理后的值数组。如果您需要验证原始输入表单数据，请改用 setPreValidator() 方法。

典型的注册表单定义如下：

```
// in modules/foo/actions/actions.class.php
// Define the form
$this->form = new sfForm();
$this->form->setWidgets(array(
	'login' => new sfWidgetFormInputText(),
	'password1' => new sfWidgetFormInputText(),
	'password2' => new sfWidgetFormInputText()
	));
$this->form->setValidators(array(
	'login' => new sfValidatorString(), // login is required
	'password1' => new sfValidatorString(), // password1 is required
	'password2' => new sfValidatorString(), // password2 is required
	));
$this->form->setPostValidators(new sfValidatorSchemaCompare('password1',
	'==', 'password2'));

```

sfValidatorSchemaCompare 验证器是一种特殊的多重验证器，它接收所有清理后的值，并可以选取其中两个进行比较。自然地，您可以使用 sfValidatorAnd 和 sfValidatorOr 验证器定义多个后置验证器。

## 验证器

Symfony 提供了大量验证器。请记住，每个验证器都接受一个选项数组和一个错误数组作为参数，您可以在其中至少自定义必填和无效错误消息。

```
// String validator
$form->setValidator('message', new sfValidatorString(array(
	'min_length' => 4,
	'max_length' => 50,
	),
	array(
	'min_length' => 'Please post a longer message',
	'max_length' => 'Please be less verbose',
	)));

// Number validator
$form->setValidator('age', new sfValidatorNumber(array( // use
	'sfValidatorInteger' instead if you want to force integer values
	'min' => 18,
	'max' => 99.99,
	),
	array(
	'min' => 'You must be 18 or more to use this service',
	'max' => 'Are you kidding me? People over 30 can\'t even use the
	Internet',
	)));

```

```
// Email validator
$form->setValidator('email', new sfValidatorEmail());
// URL validator
$form->setValidator('website', new sfValidatorUrl());
// Regular expression validator
$form->setValidator('IP', new sfValidatorRegex(array(
    'pattern' => '^[0-9]{3}\\.[0-9]{3}\\.[0-9]{2}\\.[0-9]{3}$'
)));
```

尽管某些表单控件（如下拉列表、复选框、单选按钮组）限制了可能的选项，但恶意用户始终可以尝试通过使用 Firebug 操作页面或使用脚本语言提交查询来攻击您的表单。因此，您也应该验证那些仅接受有限值数组的字段：

```
// Boolean validator
$form->setValidator('has_signed_terms_of_service', new sfValidatorBoolean());
// Choice validator (to restrict values in a list)
$form->setValidator('subject', new sfValidatorChoice(array(
    'choices' => array('Subject A', 'Subject B', 'Subject C')
)));
// Multiple choice validator
$form->setValidator('languages', new sfValidatorChoice(array(
    'multiple' => true,
    'choices' => array('en' => 'English', 'fr' => 'French', 'other')
)));
```

I18n 选择验证器适用于国家列表（sfValidatorI18nChoiceCountry）和语言列表（sfValidatorI18nChoiceLanguage）。如果您想限制可能的选项，这些验证器接受受限的国家和语言列表。

sfValidatorChoice 验证器常用于验证 sfWidgetFormChoice 小部件。由于您可以将 sfWidgetFormChoice 小部件用于外键列，因此 symfony 还提供了一个验证器来检查外键值是否存在于外键表中：

```
// Propel choice validator
$form->setValidator('section_id', new sfValidatorPropelChoice(array(
    'model' => 'Section',
    'column' => 'name'
)));
```

```
// Doctrine choice validator
$form->setValidator('section_id', new sfValidatorDoctrineChoice(array(
    'model' => 'Section',
    'column' => 'name'
)));
```

另一个有用的与模型相关的验证器是 sfValidatorPropelUnique 验证器，它检查通过表单输入的新值是否与数据库中具有唯一索引的列上的现有值冲突。例如，两个用户不能拥有相同的登录名，因此在使用表单编辑 User 对象时，必须在此列上添加 sfValidatorPropelUnique 验证器：

```
// Listing 10-36
// Propel unique validator
$form->setValidator('nickname', new sfValidatorPropelUnique(array(
  'model' => 'User',
  'column' => 'login'
)));
```

```
$form->setValidator('nickname', new sfValidatorDoctrineUnique(array(
  'model' => 'User',
  'column' => 'login'
)));
```

为了使您的表单更安全并避免跨站请求伪造攻击，您可以启用 CSRF 保护：

```
// Listing 10-37
// CSRF protection - set the secret to a random string that nobody knows
$form->addCSRFProtection('flkd445rvvrGV34G');
```

> 您可以在 settings.yml 文件中一次性为整个网站设置 CSRF 密钥：

```
// Listing 10-38
# in apps/myapp/config/settings.yml
all:
 .settings:
  # Form security secret (CSRF protection)
  csrf_secret: ##CSRF_SECRET## # Unique secret to enable CSRF
  protection or false to disable
```

多重验证器作用于整个表单，而不是单个输入。以下是可用的多重验证器列表：

```
// Listing 10-39
// compare validator - compare two fields
$form->setPostValidator(new sfValidatorSchemaCompare('password1', '==',
 'password2'));
```

```
// Extra field validator: looks for fields in the request not present in
the form
$form->setOption('allow_extra_fields', false);
$form->setOption('filter_extra_fields', true);
```

## 使用表单的其他方式

## 表单类

考虑到所有小部件选项、验证器和表单参数，在操作类中编写的联系表单定义看起来相当混乱：

```
// Listing 10-40
// in modules/foo/actions/actions.class.php
// Define the form
$this->form = new sfForm();
$this->form->getWidgetSchema()->setNameFormat('contact[%s]');
$this->form->getWidgetSchema()->setIdFormat('my_form_%s');
```





```php
$this->form->setWidgets(array(
    'name'       => new sfWidgetFormInputText(),
    'email'      => new sfWidgetFormInput(array('default' => 'me@example.com')),
    'subject'    => new sfWidgetFormChoice(array('choices' => array('Subject A', 'Subject B', 'Subject C'))),
    'message'    => new sfWidgetFormTextarea(),
));
$this->form->setValidators(array(
    'name'       => new sfValidatorString(),
    'email'      => new sfValidatorEmail(),
    'subject'    => new sfValidatorString(),
    'message'    => new sfValidatorString(array('min_length' => 4))
));
```

最佳实践是创建一个具有相同属性的表单类，并在所有使用它的动作中实例化它。例如，下面是如何为联系表单创建一个类：

```php
// in lib/form/ContactForm.class.php
class ContactForm extends sfForm
{
    protected static $subjects = array('Subject A', 'Subject B', 'Subject C');

    public function configure()
    {
        $this->widgetSchema->setNameFormat('contact[%s]');
        $this->widgetSchema->setIdFormat('my_form_%s');
        $this->setWidgets(array(
            'name'   => new sfWidgetFormInputText(),
            'email'  => new sfWidgetFormInput(array('default' => 'me@example.com')),
            'subject' => new sfWidgetFormChoice(array('choices' =>
                array('Subject A', 'Subject B', 'Subject C'))),
            'message' => new sfWidgetFormTextarea(),
        ));
        $this->setValidators(array(
            'name'   => new sfValidatorString(),
            'email'  => new sfValidatorEmail(),
            'subject' => new sfValidatorString(),
            'message' => new sfValidatorString(array('min_length' => 4))
        ));
        $this->setDefaults(array(
            'email' => 'me@example.com'
        ));
    }
}
```

现在在动作中获取联系表单对象从未如此简单过：

```php
// in modules/foo/actions/actions.class.php
// Define the form
$this->form = new ContactForm();
```

## 修改表单对象

当你使用表单类定义时，表单是在动作之外定义的。这使得动态默认值赋值相当困难。因此，表单对象将默认值数组作为其第一个参数：

```php
// in modules/foo/actions/actions.class.php
// Define the form
$this->form = new ContactForm(array('email' => 'me@example.com'));
```

你还可以通过在现有字段名上调用 setWidget() 或 setValidator() 来覆盖现有的小部件或验证器设置。

但是，在 symfony 中，小部件和验证器是对象，并提供了一个简洁的 API 来修改它们的属性：

```php
// in modules/foo/actions/actions.class.php
// Define the form
$this->form = new ContactForm();

// Allow multiple language selections
$form->getWidget('language')->setOption('multiple', true);

// Add a 'gender' list of options widget
$form->setWidget('gender', new sfWidgetFormChoice(array('expanded' => true, 'choices' => array('m' => 'Male', 'f' => 'Female')), array('class' => 'gender_list')));

// Change the HTML attributes of the 'subject' widget
$form->getWidget('subject')->setAttribute('disabled', 'disabled');

// Remove the 'subject' field
unset($form['subject'])

// Note: You cannot remove just the widget. Removing a widget will also remove the related validators

// Change the 'min_length' error in the 'message' validator
$form->getValidator('message')->setMessage('min_length', 'Message too short');

// Make the 'name' field optional
$form->getValidator('name')->setOption('required', false);
```

## 自定义小部件和验证器类

自定义小部件只是一个扩展 sfWidgetForm 并提供 configure() 和 render() 方法的类。查看现有小部件类的代码，以更深入地了解小部件系统。下一个清单展示了 sfWidgetFormInput 小部件的代码，以说明小部件结构：

```php
class sfWidgetFormInputText extends sfWidgetForm
{
/**
 * Configures the current widget.
 *
 * This method allows each widget to add options or HTML attributes
 * during widget creation.
 *
 * Available options:
 *  * type: The widget type (text by default)
 *
 * @param array $options     An array of options
 * @param array $attributes  An array of default HTML attributes
 * @see sfWidgetForm
*/
protected function configure($options = array(), $attributes = array())
{
    $this->addOption('type', 'text');
    $this->setOption('is_hidden', false);
}

/**
 * Renders the widget as HTML
 *
 * @param string $name         The element name
 * @param string $value        The value displayed in this widget
 * @param array  $attributes   An array of HTML attributes to be merged with the default HTML attributes
 * @param array  $errors       An array of errors for the field
 * @return string An HTML tag string
 * @see sfWidgetForm
 */
public function render($name, $value = null, $attributes = array(),
$errors = array())
{
    return $this->renderTag('input', array_merge(
        array('type' => $this->getOption('type'), 'name' => $name, 'value' => $value),
        $attributes
    ));
}
}
```

验证器类必须扩展 sfValidatorBase 并提供 configure() 和 doClean() 方法。为什么是 doClean() 而不是 validate()？因为验证器做两件事：它们检查输入是否符合一组规则，并且它们可选择地清理输入（例如通过强制类型、修剪、将日期字符串转换为时间戳等）。因此，doClean() 方法必须返回清理后的输入，如果输入不满足任何验证器规则，则抛出 sfValidatorError 异常。以下是使用 sfValidatorInteger 验证器的代码来说明这一概念。

```php
class sfValidatorInteger extends sfValidatorBase
{
    /**
     * Configures the current validator.
     *
     * This method allows each validator to add options and error messages during validator creation.
     *
     * Available options:
     *  * max: The maximum value allowed
     *  * min: The minimum value allowed
     Available error codes:
     *  * max
     *  * min
     *
     * @param array $options   An array of options
     * @param array $messages  An array of error messages
     * @see sfValidatorBase
     */
    protected function configure($options = array(), $messages = array())
    {
        $this->addOption('min');
        $this->addOption('max');
        $this->addMessage('max', '"%value%" must be less than %max%.');
        $this->addMessage('min', '"%value%" must be greater than %min%.');
        $this->setMessage('invalid', '"%value%" is not an integer.');
    }

    /**
     * Cleans the input value.
     *
     * @param mixed $value The input value
     * @return mixed The cleaned value
     * @throws sfValidatorError
     */
    protected function doClean($value)
    {
        $clean = intval($value);
        if (strval($clean) != $value)
        {
            throw new sfValidatorError($this, 'invalid', array('value' => $value));
        }
        if ($this->hasOption('max') && $clean > $this->getOption('max'))
        {
            throw new sfValidatorError($this, 'max', array('value' => $value,
                'max' => $this->getOption('max')));
        }
        if ($this->hasOption('min') && $clean < $this->getOption('min'))
        {
            throw new sfValidatorError($this, 'min', array('value' => $value,
                'min' => $this->getOption('min')));
        }
        return $clean;
    }
}
```

查看 symfony API 文档，了解小部件和验证器类的名称和语法。

## 使用选项向表单类传递参数

表单的一个常见问题是如何使用应用程序参数，例如用户的区域设置。最快但丑陋的方法是通过 sfContext 实例检索用户实例，使用 sfContext::getInstance()->getUser() 方法。但是，此解决方案在表单和上下文之间创建了强耦合，使测试和重用性变得更加困难。为了避免此问题，你可以简单地使用选项将区域设置值传递给表单：

```php
// from an action
public function executeContact(sfWebRequest $request)
{
  $this->form = new ContactForm(array(), array('culture' => $this->getUser()->getCulture()));
}

// from a unit test
$form = new ContactForm(array(), array('culture' => 'en'));

class ContactForm extends sfForm
{
  public function configure()
  {
    /* ... */
    $this->setWidget('country', new sfWidgetFormI18nCountry(array('culture' => $this->getOption('culture'))));
    /* ... */
  }
}
```

## 基于模型的表单

表单是 Web 应用程序中编辑数据库记录的主要方式。并且 symfony 应用程序中的大多数表单都允许编辑模型对象。但是，构建用于编辑模型的表单所需的信息已经存在：它在架构中。因此，symfony 为模型对象提供了一个表单生成器，使创建模型编辑表单变得轻而易举。

> Doctrine 也存在下文所述的类似功能。

## 生成模型表单

Symfony 可以根据架构推断用于模型编辑表单的小部件类型和验证器。例如，使用 Propel ORM 的以下架构：

```yaml
// config/schema.yml
propel:
  article:
    id:        ~
    title:     { type: varchar(255), required: true }
    slug:      { type: varchar(255), required: true, index: unique }
    content:   longvarchar
    is_published: { type: boolean, required: true }

```



author_id: { type: integer, required: true, foreignTable: author,
foreignReference: id, OnDelete: cascade }
created_at: ~

author:
  id: ~
  first_name: varchar(20)
  last_name: varchar(20)
  email: { type: varchar(255), required: true, index: unique }
  active: boolean

编辑 Article 对象的表单应该为 id 使用隐藏组件，为 title 使用文本组件，为 title 使用字符串验证器，等等。Symfony 会为你生成表单，前提是你调用 propel:build-forms 任务：

```
// propel
$ php symfony propel:build-forms

// doctrine
$ php symfony doctrine:build-forms
```

对于模型中的每个表，此命令都会在 lib/form/ 目录下创建两个文件：一个是 BaseXXXForm 类，每次调用 propel:build-forms 任务时都会被重写；另一个是空的 XXXForm 类，它扩展前一个类。这与 Propel 模型类的生成系统相同。

```
class BaseArticleForm extends BaseFormPropel
{
    public function setup()
    {
        $this->setWidgets(array(
            'id' => new sfWidgetFormInputHidden(),
            'title' => new sfWidgetFormInputText(),
            'slug' => new sfWidgetFormInputText(),
            'content' => new sfWidgetFormTextarea(),
            'is_published' => new sfWidgetFormInputCheckbox(),
            'author_id' => new sfWidgetFormPropelChoice(array('model' =>
            'Author', 'add_empty' => false)),
            'created_at' => new sfWidgetFormDatetime(),
        ));
        $this->setValidators(array(
            'id' => new sfValidatorPropelChoice(array('model' =>
            'Article', 'column' => 'id', 'required' => false)),
            'title' => new sfValidatorString(array('max_length' => 255)),
            'slug' => new sfValidatorString(array('max_length' => 255)),
            'content' => new sfValidatorString(array('max_length' => 255,
            'required' => false)),
            'is_published' => new sfValidatorBoolean(),
            'author_id' => new sfValidatorPropelChoice(array('model' =>
            'Author', 'column' => 'id')),
            'created_at' => new sfValidatorDatetime(array('required' =>
            false)),
        ));
        $this->setPostValidator(
            new sfValidatorPropelUnique(array('model' => 'Article', 'column' =>
array('slug'))
);
$this->widgetSchema->setNameFormat('article[%s]');
parent::setup();
}

public function getModelName()
{
    return 'Article';
}
}
```

请注意，即使 id 列是整数，Symfony 也会使用 sfValidatorPropelChoice 验证器检查提交的 id 是否存在于表中。表单生成器始终设置最强的验证规则，以确保数据库中的数据最清洁。

### 使用模型表单

你可以通过向空的 ArticleForm::configure() 方法添加代码，为整个项目自定义生成的表单类。

下面是在动作中处理模型表单的示例。在这个表单中，slug 验证器被修改为可选，author_id 组件被自定义为仅显示作者的一个子集——即“活跃”的作者。

```
// in lib/form/ArticleForm.class.php
public function configure()
{
    $this->getWidget('author_id')->setOption('criteria',
    $this->getOption('criteria'));
    $this->getValidator('slug')->setOption('required', false);
}
```

```
// in modules/foo/actions/actions.class.php
public function executeEditArticle($request)
{
    $c = new Criteria();
    $c->add(AuthorPeer::ACTIVE, true);

    $this->form = new ArticleForm(
    ArticlePeer::retrieveByPk($request->getParameter('id')),
    array('criteria' => $c)
    );

    if ($request->isMethod('post'))
    {
        $this->form->bind($request->getParameter('article'));
        if ($this->form->isValid())
        {
            $article = $this->form->save();
            $this->redirect('article/edit?id='.$author->getId());
        }
    }
}
```

与通过关联数组设置默认值不同，模型表单使用模型对象来初始化组件值。要显示一个空表单，只需传递一个新的模型对象。

由于表单对象包含一个嵌入的模型对象，因此表单提交的处理大大简化了。在有效表单上调用 $this->form->save() 会使用清理后的值更新嵌入的 Article 对象，并在 Article 对象以及相关对象（如果存在）上触发 save() 方法。

> 处理表单所需的动作代码几乎总是相同的，但这不是从一个模块复制到另一个模块的理由。Symfony 提供了一个模块生成器，它会创建操作和模板的全部代码，以便通过 Symfony 表单操作模型对象。

### 结论

Symfony 表单组件本身就是一个完整的框架。它通过组件简化了视图中表单的显示，通过验证器简化了控制器中表单的验证和处理，并通过模型表单简化了模型对象的编辑。虽然设计时有清晰的 MVC 分离，但表单子框架始终易于使用。大多数时候，代码生成会将你的自定义表单代码减少到几行。

Symfony 表单类中包含的内容远比本章所展示的多。事实上，有一本整本书⁴²描述了所有通过使用示例的功能。如果表单框架本身没有提供你需要的组件或验证器，它的设计具有高度可扩展性，你只需编写一个类即可获得确切所需的功能。

# 第 11 章
电子邮件

使用 Symfony 发送电子邮件既简单又强大，这要归功于 Swift Mailer43 库的使用。虽然 Swift Mailer 使发送电子邮件变得容易，但 Symfony 在其之上提供了一个薄包装器，使发送电子邮件更加灵活和强大。本章将教你如何发挥所有可用的功能。

Symfony 1.3 包含 Swift Mailer 4.1 版。

## 简介

Symfony 中的电子邮件管理围绕邮件对象展开。与许多其他核心 Symfony 对象一样，邮件是一个工厂。它在 factories.yml 配置文件中配置，并始终通过上下文实例可用：

```
$mailer = sfContext::getInstance()->getMailer();
```

与其他工厂不同，邮件是按需加载和初始化的。如果你不使用它，则完全没有性能影响。

本教程解释了 Symfony 中的 Swift Mailer 集成。如果你想了解 Swift Mailer 库本身的详细信息，请参阅其专用文档44。

## 从动作中发送电子邮件

从动作中，使用 getMailer() 捷径方法可以简单地获取邮件实例：

```
$mailer = $this->getMailer();
```

## 最快的方法

发送电子邮件则只需使用 sfAction::composeAndSend() 方法：

43. http://www.swiftmailer.org/
44. http://www.swiftmailer.org/docs

```
Listing 11-3
$this->getMailer()->composeAndSend(
    'from@example.com',
    'fabien@example.com',
    'Subject',
    'Body'
);
```

composeAndSend() 方法接受四个参数：

- 发件人电子邮件地址（from）；
- 收件人电子邮件地址（to）；
- 消息主题；
- 消息正文。

每当方法将电子邮件地址作为参数时，你可以传递字符串或数组：

```
Listing 11-4
$address = 'fabien@example.com';
$address = array('fabien@example.com' => 'Fabien Potencier');
```

当然，你可以通过将电子邮件数组作为方法的第二个参数，一次向多个人发送电子邮件：

```
Listing 11-5
$to = array(
    'foo@example.com',
    'bar@example.com',
);
$this->getMailer()->composeAndSend('from@example.com', $to, 'Subject',
    'Body');
```

```
$to = array(
    'foo@example.com' => 'Mr Foo',
    'bar@example.com' => 'Miss Bar',
);
$this->getMailer()->composeAndSend('from@example.com', $to, 'Subject',
    'Body');
```

## 灵活的方式

如果你需要更多灵活性，也可以使用 sfAction::compose() 方法创建消息，按需自定义，并最终发送它。例如，当你需要添加附件时，这很有用，如下所示：

```
Listing 11-6
// create a message object
$message = $this->getMailer()
    ->compose('from@example.com', 'fabien@example.com', 'Subject', 'Body')
    ->attach(Swift_Attachment::fromPath('/path/to/a/file.zip'))
;

// send the message
$this->getMailer()->send($message);
```

## 强大的方式

你也可以直接创建消息对象以获得更多灵活性：

```
Listing 11-7
$message = Swift_Message::newInstance()
    ->setFrom('from@example.com')
```




->setTo('to@example.com')
->setSubject('Subject')
->setBody('Body')
->attach(Swift_Attachment::fromPath('/path/to/a/file.zip'))
;

$this->getMailer()->send($message);

> Swift Mailer 官方文档中的“创建消息”45 和“消息头”46 章节描述了你了解创建消息所需的所有内容。

## 使用 Symfony 视图

从操作中发送邮件可以让你非常轻松地利用部分和组件的强大功能。

```
$message->setBody($this->getPartial('partial_name', $arguments));
```

## 配置

与其他 symfony 工厂一样，邮件发送器可以在 factories.yml 配置文件中配置。默认配置如下：

```
mailer:
  class: sfMailer
  param:
    logging:      %SF_LOGGING_ENABLED%
    charset:      %SF_CHARSET%
    delivery_strategy: realtime
    transport:
      class: Swift_SmtpTransport
      param:
        host:       localhost
        port:       25
        encryption: ~
        username:   ~
        password:   ~
```

创建新应用程序时，本地 factories.yml 配置文件会使用针对 prod、env 和 test 环境的一些合理默认值来覆盖默认配置：

```
test:
  mailer:
    param:
      delivery_strategy: none

dev:
  mailer:
    param:
      delivery_strategy: none
```

45. http://swiftmailer.org/docs/messages
46. http://swiftmailer.org/docs/headers

## 发送策略

Swift Mailer 与 symfony 集成中最有用的功能之一是发送策略。发送策略允许你指定 symfony 如何投递邮件消息，并通过 `factories.yml` 的 `delivery_strategy` 设置进行配置。该策略会改变 `send()` 方法的行为。默认提供四种策略，足以满足所有常见需求：

- realtime: 消息实时发送。
- single_address: 消息发送到单一地址。
- spool: 消息存储在队列中。
- none: 消息将被直接忽略。

### 实时策略

实时策略是默认的发送策略，也是最容易设置的，因为没有特殊需要做的事情。

邮件消息通过 `factories.yml` 配置文件 `transport` 部分中配置的传输方式发送（有关如何配置邮件传输的更多信息，请参见下一节）。

### 单一地址策略

使用 `single_address` 策略时，所有消息都会发送到一个单一地址，该地址通过 `delivery_address` 设置配置。

该策略在开发环境中非常有用，可以避免将消息发送给真实用户，同时仍然允许开发者在邮件阅读器中查看渲染后的消息。

> > 如果您需要验证原始 to、cc 和 bcc 收件人，它们分别可作为以下标头的值获取：X-Swift-To、X-Swift-Cc 和 X-Swift-Bcc。

邮件消息通过与实时策略使用的相同邮件传输方式发送。

### 队列策略

使用队列策略时，消息将存储在队列中。

这是生产环境的最佳策略，因为 Web 请求不需要等待邮件发送。

队列类通过 `spool_class` 设置进行配置。默认情况下，symfony 包含以下三种：

- Swift_FileSpool: 消息存储在文件系统上。
- Swift_DoctrineSpool: 消息存储在 Doctrine 模型中。
- Swift_PropelSpool: 消息存储在 Propel 模型中。

实例化队列时，`spool_arguments` 设置用作构造函数参数。以下是内置队列类可用的选项：

- Swift_FileSpool:
  - 队列目录的绝对路径（消息存储在此目录中）
- Swift_DoctrineSpool:
  - 用于存储消息的 Doctrine 模型（默认为 MailMessage）
  - 用于消息存储的列名（默认为 message）
  - 用于获取待发送消息的方法（可选）。它接收队列选项作为参数。
- Swift_PropelSpool:
  - 用于存储消息的 Propel 模型（默认为 MailMessage）
  - 用于消息存储的列名（默认为 message）
  - 用于获取待发送消息的方法（可选）。它接收队列选项作为参数。

以下是 Doctrine 队列的经典配置：

```
# Schema configuration in schema.yml
MailMessage:
  actAs: { Timestampable: ~ }
  columns:
    message: { type: clob, notnull: true }
```

```
# configuration in factories.yml
mailer:
  class: sfMailer
  param:
    delivery_strategy: spool
    spool_class:      Swift_DoctrineSpool
    spool_arguments: [ MailMessage, message, getSpooledMessages ]
```

以下是 Propel 队列的相同配置：

```
# Schema configuration in schema.yml
mail_message:
  message: { type: clob, required: true }
  created_at: ~
```

```
# configuration in factories.yml
dev:
  mailer:
    param:
      delivery_strategy: spool
      spool_class:      Swift_PropelSpool
      spool_arguments: [ MailMessage, message, getSpooledMessages ]
```

要发送存储在队列中的消息，可以使用 project:send-emails 任务（请注意，此任务与队列实现完全独立，且所接受的选项也是如此）：

```
$ php symfony project:send-emails
```

> project:send-emails 任务接受 application 和 env 选项。

调用 project:send-emails 任务时，邮件消息将通过与实时策略相同的传输方式发送。

请注意，project:send-emails 任务可以在任何机器上运行，不一定在创建消息的机器上运行。之所以能工作，是因为所有内容（包括文件附件）都存储在消息对象中。

内置的队列实现非常简单。它们发送邮件时没有任何错误管理，就像使用实时策略时一样。当然，默认的队列类可以被扩展以实现您自己的逻辑和错误管理。

project:send-emails 任务接受两个可选选项：

- message-limit: 限制要发送的消息数量。
- time-limit: 限制发送消息所花费的时间（以秒计）。

两个选项可以组合使用：

```
$ php symfony project:send-emails --message-limit=10 --time-limit=20
```

上述命令将在发送 10 条消息后或 20 秒后停止发送消息。

即使在使用队列策略时，您也可能需要立即发送一条消息而不将其存储在队列中。这可以通过使用邮件发送器的特殊 sendNextImmediately() 方法来实现：

```
$this->getMailer()->sendNextImmediately()->send($message);
```

在前面的示例中，$message 不会存储在队列中，而是会立即发送。正如其名称所暗示的，sendNextImmediately() 方法仅影响即将发送的下一条消息。

当发送策略不是队列时，sendNextImmediately() 方法没有特殊效果。

## 无策略

该策略在开发环境中很有用，可以避免将电子邮件发送给真实用户。消息仍然可在 Web 调试工具栏中查看（有关 Web 调试工具栏邮件发送器面板的更多信息，请参见下文）。

它也是测试环境的最佳策略，在该环境中，sfTesterMailer 对象允许您在不实际发送消息的情况下检查消息（有关测试的更多信息，请参见下文）。

## 邮件传输

邮件消息实际上是由传输方式发送的。传输方式在 factories.yml 配置文件中配置，默认配置使用本地机器的 SMTP 服务器：

```
transport:
  class: Swift_SmtpTransport
  param:
    host:   localhost
    port:   25
    encryption: ~
    username: ~
    password: ~
```

Swift Mailer 包含三种不同的传输类：

- Swift_SmtpTransport: 使用 SMTP 服务器发送消息。
- Swift_SendmailTransport: 使用 sendmail 发送消息。
- Swift_MailTransport: 使用原生 PHP mail() 函数发送消息。

> Swift Mailer 官方文档中的“传输类型”47 章节描述了你了解内置传输类及其不同参数所需的所有内容。

## 从任务中发送电子邮件

从任务中发送电子邮件与从操作中发送电子邮件非常相似，因为任务系统也提供了 getMailer() 方法。

创建邮件发送器时，任务系统依赖于当前配置。因此，如果您想使用特定应用程序的配置，必须接受 --application 选项（有关此主题的更多信息，请参见任务章节）。

请注意，任务使用与控制器相同的配置。因此，如果在使用队列策略时想强制发送，请使用 sendNextImmediately()：

```
$this->getMailer()->sendNextImmediately()->send($message);
```

## 调试

传统上，调试电子邮件一直是一场噩梦。借助 symfony，得益于 Web 调试工具栏，这变得非常简单。

在浏览器中，您可以轻松快速地查看当前操作发送了多少条消息：

![](img/0f886a7f4cbcc3939be96e985ca35ff4_192_0.png)

如果您单击电子邮件图标，发送的消息将以下方所示的原始形式在面板中显示。

47. http://swiftmailer.org/docs/transport-types




![](img/0f886a7f4cbcc3939be96e985ca35ff4_193_0.png)

每次发送电子邮件时，symfony 也会在日志中添加一条消息。

## 测试

当然，如果没有一种方法来测试邮件消息，集成就不会完整。默认情况下，symfony 注册了一个邮件测试器 (sfMailerTester) 以便在功能测试中简化邮件测试。

hasSent() 方法用于测试当前请求期间发送的消息数量：

```
Listing 11-19
$browser->
  get('/foo')->
  with('mailer')->
  hasSent(1)
;
```

上述代码检查 /foo URL 是否仅发送一封电子邮件。

每封已发送的电子邮件可以借助 checkHeader() 和 checkBody() 方法进行进一步测试：

```
Listing 11-20
$browser->
  get('/foo')->
  with('mailer')->begin()->
  hasSent(1)->
  checkHeader('Subject', '/Subject/')->
  checkBody('/Body/')->
  end()
;
```

checkHeader() 的第二个参数和 checkBody() 的第一个参数可以是以下之一：

- 用于检查精确匹配的字符串；
- 用于检查值的正则表达式；
- 负向正则表达式（以 ! 开头的正则表达式），用于检查值不匹配。

默认情况下，检查针对的是第一条已发送的消息。如果已发送多条消息，可以使用 withMessage() 方法选择要测试的那一条：

```
$browser->
    get('/foo') ->
    with('mailer') ->begin() ->
        hasSent(2) ->
        withMessage('foo@example.com') ->
        checkHeader('Subject', '/Subject/') ->
        checkBody('/Body/') ->
    end()
;

```

withMessage() 以收件人作为其第一个参数。它还接受第二个参数，以指示在同一收件人处发送了多条消息时要测试哪一条。

最后但同样重要的是，debug() 方法会转储已发送的消息，以便在测试失败时发现问题：

```
$browser->
    get('/foo') ->
    with('mailer') ->
    debug()
;

```

### 将电子邮件消息作为类

在本章的介绍中，你已经学习了如何从动作中发送电子邮件。这可能是在 symfony 应用程序中发送电子邮件最简单的方法，并且在只需要发送少量简单消息时可能是最佳方式。

但是，当你的应用程序需要管理大量不同的电子邮件消息时，你可能应该采用不同的策略。

> 作为额外的好处，使用类来处理电子邮件消息意味着同一封电子邮件消息可以在不同的应用程序中使用；例如前端和后端应用程序。

由于消息是普通的 PHP 对象，组织消息的明显方法是为每个消息创建一个类：

```
// lib/email/ProjectConfirmationMessage.class.php
class ProjectConfirmationMessage extends Swift_Message
{
    public function __construct()
    {
        parent::__construct('Subject', 'Body');

        $this
            ->setFrom(array('app@example.com' => 'My App Bot'))
            ->attach('...')
        ;
    }
}

```

从动作（或任何其他地方）发送消息，只需实例化合适的消息类即可：

```
$this->getMailer()->send(new ProjectConfirmationMessage());
```

当然，添加一个基类来集中管理共享标头（如 From 标头）或添加通用签名会很方便：

```
// lib/email/ProjectConfirmationMessage.class.php
class ProjectConfirmationMessage extends ProjectBaseMessage
{
    public function __construct()
    {
        parent::__construct('Subject', 'Body');

        // specific headers, attachments, ...
        $this->attach('...');
    }
}

// lib/email/ProjectBaseMessage.class.php
class ProjectBaseMessage extends Swift_Message
{
    public function __construct($subject, $body)
    {
        $body .= <<<EOF
--
Email sent by My App Bot
EOF
;
        parent::__construct($subject, $body);

        // set all shared headers
        $this->setFrom(array('app@example.com' => 'My App Bot'));
    }
}
```

如果消息依赖于某些模型对象，你当然可以将它们作为参数传递给构造函数：

```
// lib/email/ProjectConfirmationMessage.class.php
class ProjectConfirmationMessage extends ProjectBaseMessage
{
    public function __construct($user)
    {
        parent::__construct('Confirmation for ' . $user->getName(), 'Body');
    }
}
```

## 配方

## 通过 Gmail 发送电子邮件

如果你没有 SMTP 服务器但有 Gmail 帐户，请使用以下配置
以使用 Google 服务器发送和存档消息：

```
transport:
    class: Swift_SmtpTransport
    param:
        host:      smtp.gmail.com
        port:      465
        encryption: ssl
        username:  your_gmail_username_goes_here
        password:  your_gmail_password_goes_here
```

将用户名和密码替换为你的 Gmail 凭据即可。

## 自定义邮件器对象

如果通过 factories.yml 配置邮件器还不够，你可以监听 mailer.configure 事件，并进一步自定义邮件器。

你可以在 ProjectConfiguration 类中如下连接到此事件：

```
class ProjectConfiguration extends sfProjectConfiguration
{
    public function setup()
    {
        // ...

        $this->dispatcher->connect(
            'mailer.configure',
            array($this, 'configureMailer')
        );
    }

    public function configureMailer(sfEvent $event)
    {
        $mailer = $event->getSubject();

        // do something with the mailer
    }
}
```

下一节说明了此技术的强大用法。

## 使用 Swift Mailer 插件

要使用 Swift Mailer 插件，请监听 mailer.configure 事件（参见上一节）：

```
public function configureMailer(sfEvent $event)
{
    $mailer = $event->getSubject();

    $plugin = new Swift_Plugins_ThrottlerPlugin(
        100, Swift_Plugins_ThrottlerPlugin::MESSAGES_PER_MINUTE
);
$mailer->registerPlugin($plugin);
}
```

> Swift Mailer 官方文档的“插件”部分描述了你需要了解的所有关于内置插件的内容。

## 自定义队列行为

内置的队列实现非常简单。每个队列以随机顺序从队列中检索所有电子邮件并发送它们。

你可以配置队列以限制发送电子邮件所花费的时间（以秒为单位），或限制要发送的消息数量：

```
Listing 11-30
$spool = $mailer->getSpool();
$spool->setMessageLimit(10);
$spool->setTimeLimit(10);
```

在本节中，你将学习如何为队列实现优先级系统。这将为你提供实现自定义逻辑所需的所有信息。

首先，向架构中添加优先级列：

```
Listing 11-31
# for Propel
mail_message:
message: { type: clob, required: true }
created_at: ~
priority: { type: integer, default: 3 }
# for Doctrine
MailMessage:
actAs: { Timestampable: ~ }
columns:
message: { type: clob, notnull: true }
priority: { type: integer }
```

发送电子邮件时，设置优先级标头（1 表示最高）：

```
Listing 11-32
$message = $this->getMailer()
->compose('john@doe.com', 'foo@example.com', 'Subject', 'Body')
->setPriority(1)
;
$this->getMailer()->send($message);
```

然后，覆盖默认的 setMessage() 方法以更改 MailMessage 对象本身的优先级：

```
Listing 11-33
// for Propel
class MailMessage extends BaseMailMessage
{
    public function setMessage($message)
    {
        $msg = unserialize($message);
        $this->setPriority($msg->getPriority());
        parent::setMessage($message);
    }
}

// for Doctrine
class MailMessage extends BaseMailMessage
{
    public function setMessage($message)
    {
        $msg = unserialize($message);
        $this->priority = $msg->getPriority();

        $this->_set('message', $message);
    }
}
```

请注意，消息由队列序列化，因此在获取优先级值之前必须先反序列化。现在，创建一个按优先级对消息进行排序的方法：

```
// for Propel
class MailMessagePeer extends BaseMailMessagePeer
{
    static public function getSpooledMessages(Criteria $criteria)
    {
        $criteria->addAscendingOrderByColumn(self::PRIORITY);

        return self::doSelect($criteria);
    }

    // ...
}
```

```
// for Doctrine
class MailMessageTable extends Doctrine_Table
{
    public function getSpooledMessages()
    {
        return $this->createQuery('m')
            ->orderBy('m.priority')
        ;

    }

    // ...
}
```

最后一步是在 factories.yml 配置中定义检索方法，以更改从队列中获取消息的默认方式：

```
spool_arguments: [ MailMessage, message, getSpooledMessages ]
```

就这么多。现在，每次运行 project:send-emails 任务时，每封电子邮件都将根据其优先级发送。





## 使用任意标准自定义队列

前面的示例使用标准消息头（优先级）。但是，如果您想使用任意标准，或者不想修改要发送的消息，也可以将标准作为自定义头存储，并在发送电子邮件之前将其删除。

首先，向要发送的消息添加自定义头：

Listing 11-36
```php
public function executeIndex()
{
    $message = $this->getMailer()
        ->compose('john@doe.com', 'foo@example.com', 'Subject', 'Body')
        ;

    $message->getHeaders()->addTextHeader('X-Queue-Criteria', 'foo');

    $this->getMailer()->send($message);
}
```

然后，在将消息存储到队列时，从此头中检索值，并立即将其删除：

Listing 11-37
```php
public function setMessage($message)
{
    $msg = unserialize($message);

    $headers = $msg->getHeaders();
    $criteria = $headers->get('X-Queue-Criteria')->getFieldBody();
    $this->setCriteria($criteria);
    $headers->remove('X-Queue-Criteria');

    parent::setMessage($message);
}
```

# 第 12 章 缓存

加速应用程序的方法之一是为将来的请求存储生成的 HTML 代码片段，甚至是完整页面。这种技术称为缓存，可以在服务器端和客户端进行管理。

Symfony 提供了一个灵活的服务器缓存系统。它允许将完整的响应、动作的结果、局部模板或模板片段保存到文件中，其设置基于 YAML 文件，非常直观。当底层数据发生变化时，您可以使用命令行或特殊动作方法轻松清除缓存的特定部分。Symfony 还提供了一种通过 HTTP 1.1 头控制客户端缓存的简便方法。本章将讨论所有这些主题，并为您提供一些监控缓存为应用程序带来的改进的技巧。

## 缓存响应

HTML 缓存的原理很简单：在响应请求时发送给用户的部分或全部 HTML 代码可以用于类似的请求。此 HTML 代码存储在一个特殊位置（symfony 中的 cache/ 文件夹），前置控制器在执行动作之前会查找该位置。如果找到缓存版本，则在不执行动作的情况下直接发送，从而极大地加快该过程。如果未找到缓存版本，则执行动作，并将其结果（视图）存储在缓存文件夹中，以供将来的请求使用。

由于所有页面都可能包含动态信息，HTML 缓存默认处于禁用状态。由站点管理员决定是否启用它以提高性能。

Symfony 处理三种不同类型的 HTML 缓存：

- 动作缓存（包含或不包含布局）
- 局部模板或组件缓存
- 模板片段缓存

前两种类型通过 YAML 配置文件处理。模板片段缓存由模板中的辅助函数调用来管理。

## 全局缓存设置

对于项目中的每个应用程序，HTML 缓存机制可以在 settings.yml 文件的 cache 设置中按环境启用或禁用（默认）。清单 12-1 演示了如何启用缓存功能。请注意，这不会导致任何内容被缓存；为此，您必须在每个模块/动作中启用缓存（见下文）。

Listing 12-1 - 激活缓存，位于 frontend/config/settings.yml

```
dev:
.settings:
cache: true
```

## 缓存动作

显示静态信息（不依赖数据库或会话相关数据）的动作，或从数据库读取信息但不修改它（通常为 GET 请求）的动作，通常非常适合缓存。图 12-1 显示了在这种情况下页面中哪些元素被缓存：要么是动作结果（其模板），要么是动作结果连同布局。

## 图 12-1 - 缓存动作

![](img/0f886a7f4cbcc3939be96e985ca35ff4_201_0.png)

例如，考虑一个返回网站所有用户列表的 user/list 动作。除非用户被修改、添加或删除（此事将在“从缓存中删除项目”部分稍后讨论），否则此列表始终显示相同的信息，因此它是缓存的良好候选者。

每个动作的缓存激活和设置都定义在模块 config/ 目录中的 cache.yml 文件中。参见清单 12-2 了解示例。

## 清单 12-2 - 为动作激活缓存，位于 frontend/modules/user/config/cache.yml

```
list:
enabled: true
with_layout: false # Default value
lifetime: 86400 # Default value
```

此配置规定 list 动作的缓处于开启状态，并且布局不会与动作一起缓存（这是默认行为）。这意味着即使动作的缓存版本存在，布局（连同其局部模板和组件）仍会被执行。如果将 with_layout 设置设置为 true，则布局将与动作一起缓存且不会再次执行。

要测试缓存设置，请在浏览器中从开发环境调用该动作。

## 清单 12-3

```
http://myapp.example.com/frontend_dev.php/user/list
```

您会注意到页面中动作区域周围有一个边框。第一次时，该区域有蓝色标题，表明它不是来自缓存。刷新页面，动作区域将有黄色标题，表明它来自缓存（响应时间会有显著提升）。您将在本章后面了解更多关于测试和监控缓存的方法。

插槽是模板的一部分，缓存动作还将存储该动作模板中定义的插槽的值。因此，缓存对插槽的支持是原生的。

缓存系统也适用于带有参数的页面。例如，user 模块可能有一个 show 动作，它期望一个 id 参数来显示用户详细信息。修改 cache.yml 文件，也为此动作启用缓存，如清单 12-3 所示。

为了组织您的 cache.yml，您可以将模块中所有动作的设置分组在 all: 键下，如清单 12-3 所示。

## 清单 12-3 - cache.yml 完整示例，位于 frontend/modules/user/config/cache.yml

```
list:
  enabled:  true
show:
  enabled:  true

all:
  with_layout:  false  # Default value
  lifetime:   86400    # Default value
```

现在，每次使用不同 id 参数调用 user/show 动作都会在缓存中创建一条新记录。因此，此动作的缓存：

```
http://myapp.example.com/user/show/id/12
```

与

```
http://myapp.example.com/user/show/id/25
```

的缓存不同。

> 使用 POST 方法或带有 GET 参数调用的动作不会被缓存。

with_layout 设置还需多加说明。它实际上决定了缓存中存储什么类型的数据。对于不带布局的缓存，仅将模板执行结果和动作变量存储在缓存中。对于带布局的缓存，将整个响应对象存储。这意味着带布局的缓存比不带布局的缓存快得多。

如果功能上可以负担（即布局不依赖会话相关数据），您应选择带布局的缓存。不幸的是，布局通常包含一些动态元素（例如，已连接用户的名称），因此不带布局的动作缓存是最常见的配置。但是，RSS 源、弹出窗口以及不依赖 Cookie 的页面可以连同布局一起缓存。

## 缓存局部模板或组件

第 7 章解释了如何使用 include_partial() 辅助函数在多个模板中重用代码片段。局部模板的缓存与动作一样简单，其缓存激活遵循相同的规则，如图 12-2 所示。

## 图 12-2 - 缓存局部模板或组件

## 组件缓存

例如，清单 12-4 显示了如何编辑 cache.yml 文件以在 user 模块中启用 _my_partial.php 局部模板的缓存。请注意，在这种情况下，with_layout 设置没有意义。

Listing 12-4 - 缓存局部模板，位于 frontend/modules/user/config/cache.yml

```
__my_partial:
  enabled: true
  list:
    enabled: true
    ...
```

现在，所有使用此局部模板的模板都不会实际执行局部模板的 PHP 代码，而是改用缓存版本。

Listing 12-8

```php
<?php include_partial('user/my_partial') ?>
```

与动作一样，当局部模板的结果取决于参数时，局部模板缓存也同样相关。缓存系统将存储与不同参数值一样多的模板版本。

Listing 12-9

```php
<?php include_partial('user/my_other_partial', array('foo' => 'bar')) ?>
```

> 动作缓存比局部模板缓存更强大，因为当动作被缓存时，模板甚至不会被执行；如果模板中包含对局部模板的调用，这些调用也不会执行。因此，只有在调用动作不使用动作缓存或局部模板包含在布局中的情况下，局部模板缓存才有用。

来自第 7 章的一点提醒：组件是建立在局部模板之上的轻量级动作。这种包含类型与局部模板非常相似，并以相同的方式支持缓存。例如，如果您的全局布局包含名为 day 的组件，并使用 include_component('general/day') 来显示当前日期，请按如下设置 general 模块的 cache.yml 文件以启用此组件的缓存：

Listing 12-10

```
_day:
  enabled: true
```

缓存组件或局部模板时，您必须决定是为所有调用模板存储单个版本，还是为每个模板存储一个版本。默认情况下，组件是独立于调用它的模板存储的。但是，上下文组件（例如，每个动作显示不同侧边栏的组件）应被存储与调用它的模板同样多的次数。只要将 contextual 参数设置为 true，缓存系统就可以处理这种情况，如下所示：



_day:
 contextual: true
 enabled: true

位于应用程序 templates/ 目录中的全局组件可以被缓存，前提是你在应用程序的 cache.yml 中声明它们的缓存设置。

## 缓存模板片段

动作缓存仅适用于一部分动作。对于其他动作——即那些在模板中更新数据或显示与会话相关的信息的动作——仍然有缓存改进的空间，只是方式不同。Symfony 提供了第三种缓存类型，专门用于模板片段，并直接在模板中启用。在此模式下，动作始终会被执行，模板被分为已执行的片段和缓存中的片段，如图 12-3 所示。

图 12-3 - 缓存模板片段

![](img/0f886a7f4cbcc3939be96e985ca35ff4_204_0.png)

## 片段缓存

例如，你可能有一个用户列表，显示最后访问用户的链接，而这些信息是动态的。cache() 辅助函数定义了模板中需要缓存的部分。有关语法的详细信息，请参见清单 12-5。

清单 12-5 - 使用 cache() 辅助函数，位于 frontend/modules/user/templates/listSuccess.php

```
<!- - Code executed each time - ->
<?php echo link_to('last accessed user', 'user/
show?id='.$last_accessed_user_id) ?>

<!- - Cached code - ->
<?php if (!cache('users')): ?>
<?php foreach ($users as $user): ?>
<?php echo $user->getName() ?>
<?php endforeach; ?>
<?php cache_save() ?>
<?php endif; ?>
```

其工作原理如下：

- 如果找到了名为 ‘users’ 的片段的缓存版本，则用它来替换 `<?php if (!cache($unique_fragment_name)): ?>` 和 `<?php endif; ?>` 行之间的代码。
- 否则，这些行之间的代码会被处理并保存到缓存中，并使用唯一片段名称进行标识。

不包含在这些行之间的代码始终会被处理，且不会被缓存。

> 该动作（示例中的 list）不得启用缓存，因为这会绕过整个模板执行并忽略片段缓存声明。

使用模板片段缓存带来的速度提升不如动作缓存显著，因为动作始终会被执行，模板仅被部分处理，布局始终用于装饰。

你可以在同一模板中声明更多片段；但是，需要为每个片段提供唯一名称，以便 symfony 缓存系统之后能够找到它们。

与动作和组件一样，缓存的片段可以将秒数作为缓存生命周期，作为对 cache() 辅助函数调用的第二个参数。

清单 12-13 <?php if (!cache('users', 43200)): ?>

如果未向辅助函数提供参数，则使用默认缓存生存期（86400 秒，即一天）。

> 使动作可缓存的另一种方法是，将导致其变化的变量插入动作的路由模式中。例如，如果主页显示已连接用户的名称，则除非 URL 包含用户昵称，否则无法缓存。另一个例子是面向国际化的应用程序：如果要对具有多个翻译的页面启用缓存，语言代码必须以某种方式包含在 URL 模式中。此技巧会增加缓存中的页面数量，但对于加速高度交互的应用程序非常有帮助。

## 动态配置缓存

cache.yml 文件是定义缓存设置的一种方式，但它不变的缺点在于缺乏灵活性。然而，与 symfony 的常规做法一样，你可以使用纯 PHP 而不是 YAML，这样就可以动态配置缓存。

为什么要动态更改缓存设置？一个很好的例子是：某个页面对已认证用户和匿名用户显示的内容不同，但 URL 保持不变。假设有一个文章/show 页面，带有文章评分系统。匿名用户禁用评分功能。对这些用户而言，评分链接会触发登录表单的显示。该页面版本可以被缓存。另一方面，对于已认证用户，点击评分链接会发出 POST 请求并创建新评分。此时，必须为该页面禁用缓存，以便 symfony 动态构建它。

定义动态缓存设置的正确位置是在 sfCacheFilter 之前执行的过滤器中。事实上，缓存是 symfony 中的一个过滤器，就像安全功能一样。为了仅在用户未经过身份验证时才为 article/show 页面启用缓存，请在应用程序 lib/ 目录中创建一个 conditionalCacheFilter，如清单 12-6 所示。

清单 12-6 - 在 PHP 中配置缓存，位于 frontend/lib/conditionalCacheFilter.class.php

```
class conditionalCacheFilter extends sfFilter
{
public function execute($filterChain)
{
$context = $this->getContext();
if (!$context->getUser()->isAuthenticated())
{
foreach ($this->getParameter('pages') as $page)
{
    $context->getViewCacheManager()->addCache($page['module'],
$page['action'], array('lifetime' => 86400));
    }
}
// Execute next filter
$filterChain->execute();
}
}
```

必须在 filters.yml 文件中注册此过滤器，位置在 sfCacheFilter 之前，如清单 12-7 所示。

## 清单 12-7 - 注册自定义过滤器，位于 frontend/config/filters.yml

```
...
security: ~
conditionalCache:
class: conditionalCacheFilter
param:
  pages:
    - { module: article, action: show }
cache: ~
...
```

清除缓存（以自动加载新的过滤器类），条件缓存即可使用。它将仅为未经过身份验证的用户启用 pages 参数中定义的页面缓存。

sfViewCacheManager 对象的 addCache() 方法需要模块名、动作名，以及一个关联数组，其中包含与在 cache.yml 文件中定义的相同参数。例如，如果要定义 article/show 动作必须与布局一起缓存，且生存期为 3600 秒，请编写以下内容：

```
$context->getViewCacheManager()->addCache('article', 'show', array(
    'withLayout' => true,
    'lifetime'   => 3600,
));
```

## 替代缓存存储

默认情况下，symfony 缓存系统将数据存储在 Web 服务器硬盘的文件中。你可能希望将缓存存储在内存中（例如，通过 memcached）或存储在数据库中（特别是如果要在多个服务器之间共享缓存或加速缓存删除）。你可以轻松更改 symfony 的默认缓存存储系统，因为 symfony 视图缓存管理器使用的缓存类是在 factories.yml 中定义的。
默认视图缓存存储工厂是 sfFileCache 类：

```
view_cache:
 class: sfFileCache
 param:
 automaticCleaningFactor: 0
 cacheDir: %SF_TEMPLATE_CACHE_DIR%
```

你可以使用自己的缓存存储类替换该类，也可以使用 symfony 的替代类之一（包括 sfAPCCache、sfEAcceleratorCache、sfMemcacheCache、sfSQLiteCache 和 sfXCacheCache）。在 param 键下定义的参数会作为关联数组传递给缓存类的构造函数。任何视图缓存存储类都必须实现抽象 sfCache 类中的所有方法。有关此主题的更多信息，请参见第 19 章。

使用两个 memcache 服务器的 memcache 后端配置：view_cache: class: sfMemcacheCache param: servers: server_1: host: 192.168.1.10 server_2: host: 192.168.1.11

## 使用超快缓存

即使是缓存页面也涉及一些 PHP 代码执行。对于这种页面，symfony 仍会加载配置、构建响应等。如果你确实确定某个页面在一段时间内不会更改，可以将生成的 HTML 代码直接放入 web/ 文件夹，从而完全绕过 symfony。这归功于 Apache mod_rewrite 设置，前提是你的路由规则指定了不带后缀或以 .html 结尾的模式。

你可以手动逐页执行此操作，只需一个简单的命令行调用：

```
$ curl http://myapp.example.com/user/list.html > web/user/list.html
```

此后，每次请求 user/list 动作时，Apache 都会找到相应的 list.html 页面并完全绕过 symfony。其代价是你无法再通过 symfony 控制页面缓存（生存期、自动删除等），但速度提升非常显著。

或者，你可以使用 sfSuperCache symfony 插件，它可以自动化该过程并支持生存期和缓存清除。有关插件的更多信息，请参见第 17 章。





## 其他加速策略

除 HTML 缓存外，symfony 还有另外两种缓存机制，两者均完全自动化，对开发者透明。在生产环境中，配置和模板翻译被缓存在存储于 myproject/cache/config/ 和 myproject/cache/i18n/ 目录中的文件里，无需任何干预。

PHP 加速器（eAccelerator、APC、XCache 等），也称为 opcode 缓存模块，通过将 PHP 脚本以编译状态缓存来提升其性能，从而几乎完全消除了代码解析和编译的开销。这对于包含大量代码的 ORM 类尤其有效。这些加速器与 symfony 兼容，能轻松将应用速度提升三倍。它们被推荐用于生产环境中任何拥有大量用户的 symfony 应用。

使用 PHP 加速器，你可以手动将持久数据存储在内存中，以避免对每个请求执行相同的处理，例如使用 APC 时可使用 sfAPCCache 类。如果想要缓存 CPU 密集型函数的结果，你可能会使用 sfFunctionCache 对象。关于这些机制的更多信息，请参阅第 18 章。

## 从缓存中移除项目

如果应用的脚本或数据发生变更，缓存将包含过时信息。为避免不一致和 bug，你可以根据需要以多种不同方式移除缓存的部分内容。

### 清除整个缓存

symfony 命令行的 cache:clear 任务会擦除缓存（HTML、配置、路由和 i18n 缓存）。你可以传递参数给它以仅擦除缓存的一个子集，如清单 12-8 所示。请记住，仅从 symfony 项目根目录调用它。

清单 12-8 - 清除缓存

```
// Erase the whole cache
$ php symfony cache:clear

// Short syntax
$ php symfony cc

// Erase only the cache of the frontend application
$ php symfony cache:clear --app=frontend

// Erase only the HTML cache of the frontend application
$ php symfony cache:clear --app=frontend --type=template

// Erase only the configuration cache of the frontend application
// The built-in types are config, i18n, routing, and template.
$ php symfony cache:clear --app=frontend --type=config

// Erase only the configuration cache of the frontend application and the prod environment
$ php symfony cache:clear --app=frontend --type=config --env=prod
```

### 清除缓存的选择性部分

当数据库更新时，与修改数据相关的操作的缓存必须被清除。你可以清除整个缓存，但这对于与模型变更无关的所有现有缓存操作来说是一种浪费。这时 sfViewCacheManager 对象的 remove() 方法就派上用场了。它接受内部 URI 作为参数（与你会提供给 link_to() 的参数类型相同），并移除相关操作缓存。

例如，假设 user 模块的 update 操作修改了 User 对象的列。list 和 show 操作的缓存版本需要被清除，否则将显示包含错误数据的旧版本。为处理此问题，请使用 remove() 方法，如清单 12-9 所示。

清单 12-9 - 清除给定操作的缓存，位于 modules/user/actions/actions.class.php

```
public function executeUpdate($request)
{
  // Update a user
  $user_id = $request->getParameter('id');
  $user = UserPeer::retrieveByPk($user_id);
  $this->forward404Unless($user);
  $user->setName($request->getParameter('name'));
  ...
  $user->save();

  // Clear the cache for actions related to this user
  $cacheManager = $this->getContext()->getViewCacheManager();
  $cacheManager->remove('user/list');
  $cacheManager->remove('user/show?id=' . $user_id);
  ...
}
```

移除缓存的部分和组件要棘手一些。因为你可以向它们传递任意类型的参数（包括对象），之后几乎不可能识别其缓存版本。让我们专注于部分，因为对其他模板组件的解释是相同的。symfony 使用特殊前缀（sf_cache_partial）、模块名称和部分名称，加上调用它所用所有参数的哈希值来标识缓存的部分，如下所示：

```
// A partial called by
<?php include_partial('user/my_partial', array('user' => $user)) ?>

// Is identified in the cache as
@sf_cache_partial?module=user&action=_my_partial
&sf_cache_key=bf41dd99c8d459f3574a5da244626dcc8
```

从理论上讲，如果你知道用于标识它的参数哈希值，可以使用 remove() 方法移除缓存的部分，但这非常不切实际。幸运的是，如果你在 include_partial() 辅助函数调用中添加 sf_cache_key 参数，你就可以用你知道的某个东西在缓存中标识该部分。正如你在清单 12-10 中看到的，清除单个缓存的部分（例如，基于修改后的 User 清理缓存中的部分）变得简单。

清单 12-10 - 从缓存中清除部分

```
<?php include_partial('user/my_partial', array(
  'user'   => $user,
  'sf_cache_key' => $user->getId()
) ?>
```

```
// Is identified in the cache as
@sf_cache_partial?module=user&action=_my_partial&sf_cache_key=12
```

```
// Clear _my_partial for a specific user in the cache with
$cacheManager->remove('@sf_cache_partial?module=user&action=_my_partial&sf_cache_key=' . $user->getId());
```

要清除模板片段，请使用相同的 remove() 方法。缓存中标识片段的键由相同的 sf_cache_partial 前缀、模块名称、操作名称和 sf_cache_key（由 cache() 辅助函数包含的缓存片段的唯一名称）组成。清单 12-11 显示了一个示例。

清单 12-11 - 从缓存中清除模板片段

```
<!-- Cached code -->
<?php if (!cache('users')): ?>
    ... // Whatever
    <?php cache_save() ?>
<?php endif; ?>
```

```
// Is identified in the cache as
@sf_cache_partial?module=user&action=list&sf_cache_key=users
```

```
// Clear it with
$cacheManager->remove('@sf_cache_partial?module=user&action=list&sf_cache_key=users');
```

## 选择性缓存清理可能会让你脑力过载

缓存清理工作中最棘手的部分是确定哪些操作会受到数据更新的影响。

例如，假设当前应用有一个 publication 模块，用于列出出版物（list 操作）和描述出版物（show 操作），并附带其作者（User 类的一个实例）的详细信息。修改一条 User 记录将影响用户的所有出版物描述和出版物列表。这意味着你需要在 user 模块的 update 操作中添加类似这样的内容：

```
$c = new Criteria();
$c->add(PublicationPeer::AUTHOR_ID, $request->getParameter('id'));
$publications = PublicationPeer::doSelect($c);

$cacheManager = sfContext::getInstance()->getViewCacheManager();
foreach ($publications as $publication)
{
  $cacheManager->remove('publication/show?id='.$publication->getId());
}
$cacheManager->remove('publication/list');
```

当你开始使用 HTML 缓存时，你需要清楚了解模型与操作之间的依赖关系，以免因关系被误解而出现新错误。请记住，如果应用中某处使用了 HTML 缓存，所有修改模型的操作都可能需要包含一系列 remove() 方法的调用。

而且，如果你不想为过于困难的分析而伤脑筋，每次更新数据库时总是可以清除整个缓存……

## 一次清除多个缓存部分

remove() 方法接受带有通配符的键。它允许你用一次调用移除多个缓存部分。例如：

```
$cacheManager->remove('user/show?id=*'); // Remove for all user records
```

另一个好的示例是处理多种语言的应用，语言代码出现在所有 URL 中。用户个人资料页面的 URL 应该是这样的：

```
http://www.myapp.com/en/user/show/id/12
```

要删除所有语言中 ID 为 12 的用户的缓存个人资料，你只需调用：

```
$cache->remove('user/show?sf_culture=*&id=12');
```

这对部分也适用：

```
$cacheManager->remove('@sf_cache_partial?module=user&action=_my_partial&sf_cache_key=*'); // Remove for all keys
```

remove() 方法接受两个额外参数，允许你定义要为哪些主机和变化头清除缓存。这是因为 symfony 为每个主机和变化头保留一个缓存版本，因此两个共享相同代码库但不同主机名的应用使用不同的缓存。例如，当



应用程序将子域解释为请求参数（例如 http://php.askeet.com 和 http://life.askeet.com）。如果不设置最后两个参数，symfony 将移除当前主机及所有变化头部的缓存。或者，如果要移除另一个主机的缓存，请按如下方式调用 remove()：

```
$cacheManager->remove('user/show?id=*');
// Remove records for the current host and all users
$cacheManager->remove('user/show?id=*', 'life.askeet.com'); // Remove records for the host life.askeet.com and all users
$cacheManager->remove('user/show?id=*', '*'); // Remove records for every host and all users
```

remove() 方法适用于在 factories.yml 中可定义的所有缓存策略（不仅限于 sfFileCache，还包括 sfAPCCache、sfEAcceleratorCache、sfMemcacheCache、sfSQLiteCache 和 sfXCacheCache）。

## 跨应用清除缓存

跨应用清除缓存可能会出现问题。例如，如果管理员在后台应用程序中修改了用户表的一条记录，则前台应用程序中所有依赖于该用户的操作都需要从缓存中清除。但是，后台应用程序中可用的视图缓存管理器不知道前台应用程序的路由规则（应用程序之间相互隔离）。因此，你不能在后台编写以下代码：

```
$cacheManager = sfContext::getInstance()->getViewCacheManager(); // Retrieves the view cache manager of the backend
$cacheManager->remove('user/show?id=12'); // The pattern is not found, since the template is cached in the frontend
```

解决方案是手动初始化一个 sfCache 对象，使用与前台缓存管理器相同的设置。幸运的是，symfony 中的所有缓存类都提供 removePattern 方法，其服务与视图缓存管理器的 remove 相同。

例如，如果后台应用程序需要清除前台应用程序中 ID 为 12 的用户的 user/show 操作的缓存，可以使用以下代码：

```
$frontend_cache_dir =
sfConfig::get('sf_cache_dir').DIRECTORY_SEPARATOR.'frontend'.
DIRECTORY_SEPARATOR.sfConfig::get('sf_environment').DIRECTORY_SEPARATOR.'template';
$cache = new sfFileCache(array('cache_dir' => $frontend_cache_dir)); // Use the same settings as the ones defined in the frontend factories.yml
$cache->removePattern('user/show?id=12');
```

对于不同的缓存策略，只需更改缓存对象的初始化，但缓存移除过程保持不变：

```
$cache = new sfMemcacheCache(array('prefix' => 'frontend'));
$cache->removePattern('user/show?id=12');
```

## 测试和监控缓存

如果处理不当，HTML 缓存可能会导致显示数据不一致。每次禁用某个元素的缓存时，都应彻底测试并监控执行性能提升，以便进行调整。

### 构建暂存环境

缓存系统在生产环境中容易出现无法在开发环境中检测到的新错误，因为 HTML 缓存在开发环境中默认禁用。如果为某些操作启用了 HTML 缓存，则应添加一个名为 staging 的新环境（本节中如此称呼），其设置与 prod 环境相同（因此启用缓存），但将 web_debug 设置为 true。

要设置它，请编辑应用程序的 settings.yml 文件，并在顶部添加清单 12-12 中所示的行。

清单 12-12 - 暂存环境的设置，位于 frontend/config/settings.yml

```
staging:
  .settings:
    web_debug:    true
    cache:          true
```

此外，通过复制生产环境的前端控制器（可能是 myproject/web/index.php）创建一个新的 frontend_staging.php。编辑它以更改传递给 getApplicationConfiguration() 方法的参数，如下所示：

```
$configuration =
ProjectConfiguration::getApplicationConfiguration('frontend', 'staging',
true);
```

就这样——你有了一个新环境。通过在域名后添加前端控制器名称来使用它：

```
http://myapp.example.com/frontend_staging.php/user/list
```

### 监控性能

第 16 章将探讨网页调试工具栏及其内容。但是，由于此工具栏提供了关于缓存元素的宝贵信息，以下是其缓存功能的简要描述。

当你浏览包含可缓存元素（操作、局部片段、片段等）的页面时，网页调试工具栏（位于窗口右上角）会显示一个忽略缓存按钮（一个绿色的圆形箭头），如图 12-4 所示。此按钮会重新加载页面并强制处理缓存元素。请注意，它不会清除缓存。

调试工具栏右侧的最后一个数字是请求执行的持续时间。如果在页面上启用缓存，第二次加载页面时此数字应该会下降，因为 symfony 使用缓存中的数据而不是重新处理脚本。你可以使用此指标轻松监控缓存改进情况。

图 12-4 - 使用缓存的页面的网页调试工具栏

![](img/0f886a7f4cbcc3939be96e985ca35ff4_213_0.png)

调试工具栏还显示请求处理期间执行的数据库查询数量，以及每个类别的持续时间详情（单击总持续时间以显示详情）。将此数据与总持续时间结合起来监控，将有助于你精确衡量缓存带来的性能改进。

### 基准测试

调试模式会大幅降低应用程序的速度，因为大量信息会被记录并提供给网页调试工具栏。因此，在 `staging` 环境中浏览时显示的处理时间并不能代表生产环境中的表现，因为生产环境中已关闭调试模式。

为了更好地查看每个请求的处理时间，你应该使用基准测试工具，例如 Apache Bench 或 JMeter。这些工具允许进行负载测试，并提供两项重要信息：特定页面的平均加载时间和服务器的最大容量。平均加载时间数据对于监控缓存激活带来的性能改进非常有用。

### 识别缓存部分

启用网页调试工具栏后，页面中的缓存元素会用红色框标识，每个元素左上角都有一个缓存信息框，如图 12-5 所示。如果元素已执行，该框背景为蓝色；如果来自缓存，则背景为黄色。单击缓存信息链接会显示缓存元素的标识符、其生存时间以及自上次修改以来经过的时间。这将帮助你在处理脱离上下文的元素时识别问题，查看元素创建时间以及模板中哪些部分实际可以缓存。

图 12-5 - 页面中缓存元素的标识

![](img/0f886a7f4cbcc3939be96e985ca35ff4_214_0.png)

### HTTP 1.1 和客户端缓存

HTTP 1.1 协议定义了一组头部，通过控制浏览器的缓存系统，这些头部可大大有助于进一步加速应用程序。

万维网联盟（W3C，http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html）的 HTTP 1.1 规范详细描述了这些头部。如果操作启用了缓存，并且使用了 `with_layout` 选项，则可以使用以下部分中描述的一种或多种机制。

即使你网站用户的一些浏览器可能不支持 HTTP 1.1，使用 HTTP 1.1 缓存功能也无风险。接收到不理解的头部的浏览器会直接忽略它们，因此建议你设置 HTTP 1.1 缓存机制。

此外，代理和缓存服务器也能理解 HTTP 1.1 头部。即使用户的浏览器不理解 HTTP 1.1，请求路径中可能存在可以利用它的代理。

### 添加 ETag 头部以避免发送未更改的内容

启用 ETag 功能后，Web 服务器会在响应中添加一个特殊头部，包含响应本身的签名。





```
Listing 12-36
ETag: "1A2Z3E4R5T6Y7U"
```

用户的浏览器会存储此签名，并在下次需要相同页面时，随请求一起再次发送。如果新签名显示页面自首次请求以来未更改，服务器不会发送响应。相反，它只会发送一个 304: 未修改标头。这为服务器节省了 CPU 时间（例如，如果启用了 gzip 压缩）和带宽（页面传输），也为客户端节省了时间（页面传输）。总体而言，带有 ETag 的缓存页面加载速度比不带 ETag 的缓存页面更快。

在 symfony 中，你在 settings.yml 中为整个应用程序启用 ETag 功能。默认的 ETag 设置如下：

```
Listing 12-37
all:
  .settings:
    etag: true
```

对于带布局的缓存动作，响应直接从 cache/ 目录读取，因此过程更快。

## 添加 Last-Modified 标头以避免发送仍有效的内容

当服务器向浏览器发送响应时，可以添加一个特殊标头以指定页面中数据上次更改的时间：

```
Listing 12-38
Last-Modified: Sat, 23 Nov 2010 13:27:31 GMT
```

浏览器可以理解此标头，并在再次请求页面时相应地添加 If-Modified-Since 标头：

```
Listing 12-39
If-Modified-Since: Sat, 23 Nov 2010 13:27:31 GMT
```

然后，服务器可以将客户端保存的值与其应用程序返回的值进行比较。如果两者匹配，服务器将返回一个 304: 未修改标头，节省带宽和 CPU 时间，这与 ETag 的情况相同。

在 symfony 中，你可以像设置其他标头一样设置 Last-Modified 响应标头。例如，你可以在动作中这样使用：

```
Listing 12-40
$this->getResponse()->setHttpHeader('Last-Modified', $this->getResponse()->getDate($timestamp));
```

此日期可以是页面中使用的数据的实际最后更新日期，来源于你的数据库或文件系统。sfResponse 对象的 getDate() 方法将时间戳转换为 Last-Modified 标头所需格式（RFC1123）的格式化日期。

## 添加 Vary 标头以允许页面的多个缓存版本

另一个 HTTP 1.1 标头是 Vary。它定义页面依赖哪些参数，并由浏览器和代理用于构建缓存键。例如，如果页面内容取决于 cookie，你可以按如下方式设置其 Vary 标头：

```
Listing 12-41
Vary: Cookie
```

大多数情况下，在动作上启用缓存比较困难，因为页面可能会根据 cookie、用户语言或其他因素而变化。如果你不介意增加缓存的大小，请正确设置响应的 Vary 标头。这可以针对整个应用程序或按每个动作进行，使用 cache.yml 配置文件或 sfResponse 相关方法，如下所示：

```
$this->getResponse()->addVaryHttpHeader('Cookie');
$this->getResponse()->addVaryHttpHeader('User-Agent');
$this->getResponse()->addVaryHttpHeader('Accept-Language');
```

Symfony 会在缓存中为这些参数的每个值存储页面的不同版本。这会增加缓存的大小，但每当服务器收到匹配这些标头的请求时，响应将从缓存中获取，而不是进行处理。这对于仅根据请求标头而变化的页面是一个很好的性能工具。

## 添加 Cache-Control 标头以允许客户端缓存

到目前为止，即使添加了标头，浏览器在拥有页面缓存版本的情况下仍会不断向服务器发送请求。你可以通过向响应添加 Cache-Control 和 Expires 标头来避免这种情况。这些标头在 PHP 中默认处于禁用状态，但 symfony 可以覆盖此行为，以避免向你的服务器发送不必要的请求。

像往常一样，你通过调用 sfResponse 对象的方法来触发此行为。在动作中，定义页面应缓存的最大时间（以秒为单位）：

```
$this->getResponse()->addCacheControlHttpHeader('max_age=60');
```

你还可以指定页面可在哪些条件下缓存，以便提供商的缓存不会保留私有数据（如银行账号）的副本：

```
$this->getResponse()->addCacheControlHttpHeader('private=True');
```

使用 Cache-Control HTTP 指令，你可以微调服务器与客户端浏览器之间的各种缓存机制。有关这些指令的详细审查，请参阅 W3C Cache-Control 规范。

可以通过 symfony 设置的最后一个标头是 Expires 标头：

```
$this->getResponse()->setHttpHeader('Expires', $this->getResponse()->getDate($timestamp));
```

> 启用 Cache-Control 机制的主要后果是，你的服务器日志将不再显示用户发出的所有请求，而仅显示实际收到的请求。如果性能有所提高，站点在统计中的表面受欢迎程度可能会下降。

## 摘要

缓存系统根据所选缓存类型提供不同程度的性能提升。从最佳收益到最低收益，缓存类型如下：

- 超级缓存
- 带布局的动作缓存
- 不带布局的动作缓存
- 模板中的片段缓存

此外，部分和组件也可以缓存。

如果更改模型或会话中的数据迫使你为了一致性而清除缓存，你可以以细粒度进行操作以获得最佳性能——仅清除已更改的元素，保留其他元素。

请务必格外小心地测试所有启用缓存的页面，因为如果缓存了错误的元素，或在更新底层数据时忘记清除缓存，可能会出现新错误。一个专门用于缓存测试的预发布环境对此非常有用。

最后，利用 symfony 的高级缓存调整功能充分发挥 HTTP 1.1 协议的优势，这些功能将客户端纳入缓存任务，并提供更多性能收益。

# 第 13 章 I18n 和 L10n

如果你曾开发过国际化应用程序，你就会知道处理文本翻译、本地标准和本地化内容的方方面面可能是一场噩梦。幸运的是，symfony 原生自动化了国际化的所有方面。

由于这是一个长单词，开发人员通常将国际化简称为 i18n（数一下单词中的字母数就知道为什么了）。本地化简称为 l10n。它们涵盖多语言 Web 应用程序的两个不同方面。

国际化应用程序包含同一内容的多个版本，采用各种语言或格式。例如，Web 邮件界面可以提供多种语言的相同服务；只有界面会发生变化。

本地化应用程序根据浏览所在国家/地区包含不同的信息。考虑新闻门户的内容：当从美国浏览时，它显示关于美国的最新头条新闻，但当从法国浏览时，头条新闻涉及法国新闻。因此，l10n 应用程序不仅提供内容翻译，而且不同本地化版本之间的内容可能不同。

总的来说，处理 i18n 和 l10n 意味着应用程序可以处理以下内容：

- 文本翻译（界面、资源和内容）
- 标准和格式（日期、金额、数字等）
- 本地化内容（根据国家/地区的给定对象的多个版本）

本章介绍了 symfony 处理这些元素的方式，以及你如何使用它来开发国际化和本地化应用程序。

## 用户区域设置

symfony 中所有内置的 i18n 功能都基于用户会话中的一个名为 culture 的参数。culture 是用户的国家/地区和语言的组合，它决定了文本和依赖于区域设置的信息的显示方式。由于它在用户会话中被序列化，因此区域设置在页面之间是持久的。

## 设置默认区域设置

默认情况下，新用户的区域设置是 default_culture。你可以在 settings.yml 配置文件中更改此设置，如清单 13-1 所示。

清单 13-1 - 设置默认区域设置，在 frontend/config/settings.yml 中



all:
  .settings:
    default_culture: fr_FR

> 在开发过程中，你可能会惊讶地发现，在 settings.yml 文件中更改区域设置并不会改变浏览器中的当前区域设置。这是因为会话中已经保留了来自之前页面的区域设置。如果你想以新的默认区域设置查看应用程序，需要清除域 Cookie 或重启浏览器。

在区域设置中同时保留语言和国家是必要的，因为你可能需要为来自法国、比利时或加拿大的用户提供不同的法语翻译，并为来自西班牙或墨西哥的用户提供不同的西班牙语内容。语言采用两个小写字符编码，遵循 ISO 639-1 标准（例如，en 代表英语）。国家采用两个大写字符编码，遵循 ISO 3166-1 标准（例如，GB 代表英国）。

## 更改用户的区域设置

用户区域设置可以在浏览会话期间更改——例如，当用户决定从应用程序的英文版切换到法文版，或当用户登录应用程序并使用其偏好中存储的语言时。这就是为什么 sfUser 类为用户区域设置提供了获取器和设置器方法。清单 13-2 展示了如何在操作中使用这些方法。

### 清单 13-2 - 在操作中设置和获取区域设置

```
// Culture setter
$this->getUser()->setCulture('en_US');

// Culture getter
$culture = $this->getUser()->getCulture();
=> en_US
```

## URL 中的区域设置

使用 symfony 的本地化和国际化功能时，单个 URL 往往会有不同的页面版本——这完全取决于用户会话。这会阻止你缓存页面或在搜索引擎中索引页面。

一个解决方案是让区域设置出现在每个 URL 中，这样翻译后的页面在外部看来就是不同的 URL。要做到这一点，请在应用程序 routing.yml 的每条规则中添加 :sf_culture 标记：

```
page:
  url: /:sf_culture/:page
  param: ...
  requirements: { sf_culture: (?:fr|en|de) }

article:
  url: /:sf_culture/:year/:month/:day/:slug
  param: ...
  requirements: { sf_culture: (?:fr|en|de) }
```

为了避免在每个 link_to() 中手动设置 sf_culture 请求参数，symfony 会自动将用户区域设置添加到默认路由参数中。这在入站时也适用，因为如果在 URL 中找到 sf_culture 参数，symfony 会自动更改用户区域设置。

## 自动确定区域设置

在许多应用程序中，用户区域设置是在第一个请求期间根据浏览器偏好定义的。用户可以在浏览器中定义可接受语言列表，并且这些数据会随每个请求通过 Accept-Language HTTP 标头发送到服务器。你可以在 symfony 中通过 sfWebRequest 对象检索它。例如，要在操作中获取用户的首选语言列表，请键入以下内容：

```
$languages = $request->getLanguages();
```

HTTP 标头是一个字符串，但 symfony 会自动解析它并将其转换为数组。因此，在前面的示例中，用户的首选语言可以通过 $languages[0] 访问。

在网站主页或所有页面的过滤器中，将用户区域设置自动设置为其首选浏览器语言可能很有用。但是，由于你的网站可能只支持有限的一组语言，因此最好使用 getPreferredCulture() 方法。它通过比较用户首选语言和支持的语言来返回最佳语言：

```
$language = $request->getPreferredCulture(array('en', 'fr')); // the website is available in English and French
```

如果没有匹配项，该方法将返回第一个支持的语言（前面示例中的 en）。

> Accept-Language HTTP 标头并不是非常可靠的信息，因为用户很少知道如何在浏览器中修改它。大多数情况下，首选浏览器语言就是界面语言，而浏览器并非所有语言都可用。如果你决定根据浏览器的首选语言自动设置区域设置，请确保为用户提供一种选择备用语言的方式。

## 标准和格式

Web 应用程序的内部不关心文化特性。例如，数据库使用国际标准来存储日期、金额等。但是，当数据发送给用户或从用户处检索时，需要进行转换。用户不会理解时间戳，并且他们更愿意将母语声明为 Français 而不是 French。因此，你需要根据用户区域设置自动进行转换的帮助。

## 以用户区域设置输出数据

定义区域设置后，依赖于它的辅助函数将自动生成适当的输出。例如，format_number() 辅助函数会根据用户的区域设置自动以用户熟悉的格式显示数字，如清单 13-3 所示。

### 清单 13-3 - 为用户区域设置显示数字

```
<?php use_helper('Number') ?>
<?php $sf_user->setCulture('en_US') ?>
<?php echo format_number(12000.10) ?>
=> '12,000.10'

<?php $sf_user->setCulture('fr_FR') ?>
<?php echo format_number(12000.10) ?>
=> '12 000,10'
```

你不需要显式地将区域设置传递给辅助函数。它们会自行在当前会话对象中查找。清单 13-4 列出了在输出时考虑用户区域设置的辅助函数。

### 清单 13-4 - 依赖区域设置的辅助函数

```
<?php use_helper('Date') ?>
<?php echo format_date(time()) ?>
=> '9/14/10'

<?php echo format_datetime(time()) ?>
=> 'September 14, 2010 6:11:07 PM CEST'

<?php use_helper('Number') ?>
<?php echo format_number(12000.10) ?>
=> '12,000.10'

<?php echo format_currency(1350, 'USD') ?>
=> '$1,350.00'

<?php use_helper('I18N') ?>
<?php echo format_country('US') ?>
=> 'United States'

<?php format_language('en') ?>
=> 'English'

<?php use_helper('Form') ?>
<?php echo input_date_tag('birth_date', mktime(0, 0, 0, 9, 14, 2010)) ?>
=> input type="text" name="birth_date" id="birth_date" value="9/14/10"
size="11" />

<?php echo select_country_tag('country', 'US') ?>
=> <select name="country" id="country"><option
value="AF">Afghanistan</option>
...
<option value="GB">United Kingdom</option>
<option value="US" selected="selected">United States</option>
<option value="UM">United States Minor Outlying Islands</option>
<option value="UY">Uruguay</option>
...
</select>
```

日期辅助函数可以接受一个额外的格式参数以强制使用与区域设置无关的显示，但如果你的应用程序已国际化，则不应该使用它。

## 从本地化输入获取数据

如果有必要以用户的区域设置显示数据，那么在检索数据时，你应尽可能鼓励应用程序的用户输入已国际化的数据。这种方法将使你免于尝试弄清楚如何转换格式各异且地域不确定的数据。例如，谁会在输入框中输入带有逗号分隔符的货币值呢？

你可以通过隐藏实际数据（如在 `select_country_tag()` 中）或将复杂数据的不同组件分隔为多个简单输入来约束用户输入格式。

但是，对于日期，这通常是不可能的。用户习惯于以其文化格式输入日期，并且你需要能够将此类数据转换为内部（和国际）格式。sfI18N 类正是为此而存在。清单 13-5 演示了如何使用此类。

### 清单 13-5 - 在操作中从本地化格式获取日期

```
$date= $request->getParameter('birth_date');
$user_culture = $this->getUser()->getCulture();

// Getting a timestamp
$timestamp = $this->getContext()->getI18N()->getTimestampForCulture($date,
$user_culture);

// Getting a structured date
list($d, $m, $y) =
$this->getContext()->getI18N()->getDateForCulture($date, $user_culture);
```

## 数据库中的文本信息

本地化的应用程序根据用户的区域设置提供不同的内容。例如，一家网上商店可以在全球以相同的价格提供产品，但为每个国家提供自定义描述。这意味着数据库必须能够存储给定数据的不同版本，为此，你需要以特定方式设计架构，并在每次操作本地化模型对象时使用区域设置。





## 创建本地化架构

对于包含本地化数据的每个表，您都应该将表拆分为两部分：一个不包含任何 i18n 列的表，另一个仅包含 i18n 列的表。这两个表通过一对多关系关联。这种设置允许您在需要时添加更多语言，而无需更改模型。让我们考虑一个使用 Product 表的示例。

首先，在 schema.yml 文件中创建表，如清单 13-6 所示。

### 清单 13-6 - 使用 Propel 的 i18n 数据示例架构，在 config/schema.yml 中

```yaml
my_connection:
  my_product:
    _attributes: { phpName: Product, isI18N: true, i18nTable:
      my_product_i18n }
    id:        { type: integer, required: true, primaryKey: true,
                 autoincrement: true }
    price:     { type: float }

  my_product_i18n:
    _attributes: { phpName: ProductI18n }
    id:          { type: integer, required: true, primaryKey: true,
                   foreignTable: my_product, foreignReference: id }
    culture:     { isCulture: true, type: varchar, size: 7, required:
                   true, primaryKey: true }
    name:        { type: varchar, size: 50 }
```

注意第一个表中的 isI18N 和 i18nTable 属性，以及第二个表中的特殊 culture 列。所有这些都是 symfony 特有的 Propel 增强功能。

### 清单 13-7 - 使用 Doctrine 的 i18n 数据示例架构，在 config/doctrine/schema.yml 中

```yaml
Product:
  actAs:
    I18n:
      fields: [name]
  columns:
    price: { type: float }
    name:  { type: string(50) }
```

symfony 的自动化功能可以让编写速度快得多。如果包含国际化数据的表与主表同名，且以 _i18n 作为后缀，并且两个表都通过名为 id 的列关联，那么您可以省略 _i18n 表中的 id 和 culture 列，以及主表中的特定 i18n 属性；symfony 会自动推断它们。这意味着 symfony 将把清单 13-8 中的架构视为与清单 13-6 中的架构相同。

### 清单 13-8 - i18n 数据示例架构，简化版，在 config/schema.yml 中

```yaml
my_connection:
  my_product:
    _attributes: { phpName: Product }
    id:
    price:       float

  my_product_i18n:
    _attributes: { phpName: ProductI18n }
    name:        varchar(50)
```

## 使用生成的 I18n 对象

构建相应的对象模型后（请不要忘记在每次修改 schema.yml 后调用 propel:build --model 任务），您就可以使用带有 i18n 支持的 Product 类，就像只有一个表一样，如清单 13-9 所示。

### 清单 13-9 - 处理 i18n 对象

```php
$product = ProductPeer::retrieveByPk(1);
$product->setName('Nom du produit'); // By default, the culture is the current user culture
$product->save();

echo $product->getName();
=> 'Nom du produit'

$product->setName('Product name', 'en'); // change the value for the 'en' culture
$product->save();

echo $product->getName('en');
=> 'Product name'
```

关于使用 peer 对象进行查询，您可以使用 doSelectWithI18n 方法（而不是通常的 doSelect）将结果限制为具有当前区域设置翻译的对象，如清单 13-10 所示。此外，它将在创建常规对象的同时创建相关的 i18n 对象，从而减少获取完整内容所需的查询次数（有关此方法对性能积极影响的更多信息，请参阅第 18 章）。

### 清单 13-10 - 使用 i18n 条件检索对象

```php
$c = new Criteria();
$c->add(ProductPeer::PRICE, 100, Criteria::LESS_THAN);
$products = ProductPeer::doSelectWithI18n($c, $culture);
// The $culture argument is optional
// The current user culture is used if no culture is given
```

因此，基本上您永远不应该直接处理 i18n 对象，而是在使用常规对象进行查询时，每次都将区域设置传递给模型（或让模型自行推断）。

## 界面翻译

用户界面需要为 i18n 应用程序进行调整。模板必须能够以多种语言显示标签、消息和导航，但保持相同的表现形式。Symfony 建议您使用默认语言构建模板，并在字典文件中为模板中使用的短语提供翻译。这样，您在修改、添加或删除翻译时就不需要更改模板了。

## 配置翻译

模板默认未翻译，这意味着您需要在所有其他操作之前，先在 settings.yml 文件中激活模板翻译功能，如清单 13-11 所示。

### 清单 13-11 - 激活界面翻译，在 frontend/config/settings.yml 中

```yaml
all:
  .settings:
    i18n: true
```

## 使用翻译辅助函数

假设您想创建一个英语和法语网站，以英语为默认语言。在开始之前。因此，用户界面翻译依赖于字典文件。

字典文件采用 XML 本地化交换文件格式（XLIFF）编写，按照 messages.[语言代码].xml 模式命名，并存储在应用程序的 i18n/ 目录中。

XLIFF 是一种基于 XML 的标准格式。众所周知，您可以使用第三方翻译工具来引用网站中的所有文本并进行翻译。翻译公司知道如何处理此类文件，并通过添加新的 XLIFF 翻译来翻译整个网站。

> 除了 XLIFF 标准外，symfony 还支持几种其他用于字典的翻译后端：gettext、MySQL 和 SQLite。有关配置这些后端的更多信息，请参阅 API 文档。

### 清单 13-14 - 一个 XLIFF 字典，在 frontend/i18n/messages.fr.xml 中

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE xliff PUBLIC "-//XLIFF//DTD XLIFF//EN"
"http://www.oasis-open.org/committees/xliff/documents/xliff.dtd" >
<xliff version="1.0">
<file original="global" source-language="en_US" datatype="plaintext">
    <body>
        <trans-unit id="1">
            <source>Welcome to our website.</source>
            <target>Bienvenue sur notre site web.</target>
        </trans-unit>
        <trans-unit id="2">
            <source>Today's date is </source>
            <target>La date d'aujourd'hui est </target>
        </trans-unit>
    </body>
</file>
</xliff>
```

source-language 属性必须始终包含默认区域设置的完整 ISO 代码。每个翻译都写在带有唯一 id 属性的 trans-unit 标记中。

使用默认用户区域设置（设置为 en_US）时，短语不会被翻译，而会显示 __() 调用的原始参数。清单 13-12 的结果然后类似于清单 13-11。但是，如果区域设置更改为 fr_FR 或 fr_BE，则会改为显示 messages.fr.xml 文件中的翻译，结果类似于清单 13-15。

### 清单 13-15 - 一个已翻译的模板

```php
Bienvenue sur notre site web. La date d'aujourd'hui est
<?php echo format_date(date()) ?>
```

如果需要进行其他翻译，只需在同一目录中添加一个新的 messages.XX.xml 翻译文件即可。

> 由于查找字典文件、解析它们以及为给定字符串找到正确翻译需要一些时间，symfony 使用内部缓存来加快此过程。默认情况下，此缓存使用文件系统。您可以在 factories.yml 中配置 i18n 缓存的工作方式（例如，在多个服务器之间共享缓存）（请参见第 19 章）。

## 管理字典

如果您的 messages.XX.xml 文件过长难以阅读，您可以随时将翻译拆分为按主题命名的几个字典文件。例如，您可以将 messages.fr.xml 文件拆分为应用程序 i18n/ 目录中的以下三个文件：

- navigation.fr.xml
- terms_of_service.fr.xml
- search.fr.xml

请注意，一旦在默认的 messages.XX.xml 文件中找不到翻译，您就必须在每次调用 __() 辅助函数时使用其第三个参数声明要使用的字典。例如，要输出在 navigation.fr.xml 字典中翻译的字符串，请编写以下内容：

```php
<?php echo __('Welcome to our website', null, 'navigation') ?>
```



组织翻译字典的另一种方法是按模块拆分。与为整个应用程序编写单个messages.XX.xml文件不同，你可以在每个modules/[module_name]/i18n/目录中编写一个。这样可以使模块与应用程序更加独立，如果你想重用它们（例如在插件中），这是必要的（参见第17章）。

由于手动更新i18n字典非常容易出错，symfony提供了一个任务来自动化该过程。i18n:extract任务会解析symfony应用程序以提取所有需要翻译的字符串。它将应用程序和区域设置作为其参数：

```
$ php symfony i18n:extract frontend en
```

默认情况下，该任务不会修改你的字典，它只输出新旧i18n字符串的数量。要将新字符串追加到你的字典中，可以传递--auto-save选项：

```
$ php symfony i18n:extract --auto-save frontend en
```

你还可以通过传递--auto-delete选项来自动删除旧字符串：

```
$ php symfony i18n:extract --auto-save --auto-delete frontend en
```

> 当前任务有一些已知限制。它只能使用默认的messages字典，并且对于基于文件的后端（XLIFF或gettext），它仅在主文件apps/frontend/i18n/messages.XX.xml中保存和删除字符串。

## 处理其他需要翻译的元素

以下是其他可能需要翻译的元素：

- 图片、文本文档或任何其他类型的资源也可以根据用户区域设置而变化。最佳示例是一段具有特殊格式但实际上是图片的文本。对于这些，你可以创建以用户区域设置命名的子目录：

```
<?php echo image_tag($sf_user->getCulture().'/myText.gif') ?>
```

- 验证文件中的错误消息会由__()自动输出，因此你只需将其翻译添加到字典中，即可使其被翻译。

- 默认的symfony页面（未找到页面、内部服务器错误、访问受限等）使用英文编写，在i18n应用程序中必须重写。你应该在自己的应用程序中创建默认模块，并在其模板中使用__()。请参阅第19章了解如何自定义这些页面。

## 处理复杂的翻译需求

只有当__()的参数是完整句子时，翻译才有意义。但是，由于有时格式或变量与单词混合在一起，你可能会想将句子切分成多个片段，从而在毫无意义的短语上调用助手。幸运的是，__()助手提供了基于标记的替换功能，这将帮助你创建对翻译人员来说更容易处理的、有意义的字典。与HTML格式一样，你也可以将其保留在助手调用中。清单13-16显示了一个示例。

### 清单13-16 - 翻译包含代码的句子

```
// Base example
Welcome to all the <b>new</b> users.<br />
There are <?php echo count_logged() ?> persons logged.
```

```
// Bad way to enable text translation
<?php echo __('Welcome to all the') ?>
<b><?php echo __('new') ?></b><?php echo __('users') ?>.<br />
<?php echo __('There are') ?>
<?php echo count_logged() ?>
<?php echo __('persons logged') ?>
```

```
// Good way to enable text translation
<?php echo __('<b>Welcome to all the <b>new</b> users</b>') ?> <br />
<?php echo __('There are %1% persons logged', array('%1%' =>
count_logged())) ?>
```

在此示例中，标记是%1%，但可以是任何内容，因为翻译助手使用的替换函数是strtr()。

翻译中常见的问题之一是复数形式的使用。根据结果数量，文本会发生变化，但不同语言的变化方式不同。例如，如果count_logged()返回0或1，清单13-16中的最后一句就不正确了。你可以对此函数的返回值进行测试并相应选择要使用的句子，但这需要编写大量代码。此外，不同语言有不同的语法规则，复数的变格规则可能非常复杂。由于这个问题非常常见，symfony提供了一个名为format_number_choice()的助手来处理它。清单13-17演示了如何使用此助手。

### 清单13-17 - 根据参数值翻译句子

```
<?php echo format_number_choice(
 '[0]Nobody is logged|[1]There is 1 person logged|[1,+Inf]There are %1%
persons logged', array('%1%' => count_logged()), count_logged()) ?>
```

第一个参数是文本的多种可能性。第二个参数是替换模式（与__()助手相同）且为可选。第三个参数是用于确定采用哪个文本的测试数字。

消息/字符串选项由管道字符（|）分隔，后跟可接受值的数组，使用以下语法：

- [1,2]: 接受1到2之间的值（包含1和2）
- (1,2): 接受1到2之间的值（不包含1和2）
- {1,2,3,4}: 只接受集合中定义的值
- [-Inf,0): 接受大于或等于负无穷且严格小于0的值
- {n: n % 10 > 1 && n % 10 < 5} pliki: 匹配2、3、4、22、23、24等数字（对于波兰语或俄语等语言有用）

方括号和圆括号分隔符的任何非空组合都是可接受的。

消息需要显式出现在XLIFF文件中，翻译才能正常工作。清单13-18显示了一个示例。

### 清单13-18 - format_number_choice()参数的XLIFF字典

```
...
<trans-unit id="3">
<source>[0]Nobody is logged|[1]There is 1 person logged|(1,+Inf]There are %1% persons logged</source>
<target>[0]Personne n'est connecté|[1]Une personne est connectée|(1,+Inf]Il y a %1% personnes en ligne</target>
</trans-unit>
...
```

## 关于字符集的几句话

在模板中处理国际化内容通常会导致字符集问题。如果你使用本地化字符集，则每次用户更改区域设置时都需要更改它。此外，用给定字符集编写的模板将无法正确显示另一字符集的字符。

这就是为什么，一旦你处理多个区域设置，所有模板都必须以UTF-8保存，并且布局必须使用该字符集声明内容。如果你始终使用UTF-8，就不会有任何不愉快的惊喜，并能避免大麻烦。

Symfony应用程序依赖settings.yml文件中的一个中心设置来确定字符集。更改此参数将更改所有响应的content-type标头。

```
all:
.settings:
charset: utf-8
```

## 在模板外部调用翻译助手

页面中显示的并非所有文本都来自模板。这就是为什么你经常需要在应用程序的其他部分调用__()助手：操作、过滤器、模型类等。清单13-19展示了如何通过上下文单例获取I18N对象的当前实例来在操作中调用助手。

### 清单13-19 - 在操作中调用__()

```
$this->getContext()->getI18N()->__($text, $args, 'messages');
```

## 总结

如果你知道如何处理用户区域设置，Web应用程序中的国际化和本地化就轻而易举。助手会自动将其考虑在内以输出格式正确的数据，数据库中的本地化内容就像简单表的一部分一样被查看。至于界面翻译，__()助手和XLIFF字典确保你以最少的工作获得最大的灵活性。

# 第 14 章

## 管理生成器

许多应用程序基于存储在数据库中的数据，并提供访问数据的界面。Symfony自动化了创建基于Propel或Doctrine对象提供数据操作功能的模块这一重复性任务。如果你的对象模型定义正确，symfony甚至可以自动生成整个站点管理后台。本章描述了管理生成器的使用，它与Propel和Doctrine插件一起提供。它依赖于具有完整语法的特殊配置文件，因此本章的大部分内容描述了管理生成器的各种可能性。

## 基于模型的代码生成

在Web应用程序中，数据访问操作可分为以下一种：

- 创建记录
- 检索记录
- 更新记录（及其列的修改）
- 删除记录

这些操作非常常见，因此有专门的缩写：CRUD。许多页面都可以归约为其中一种。例如，在论坛应用程序中，最新帖子列表是检索操作，而回复帖子对应创建操作。

实现给定表CRUD操作的基本操作和模板在Web应用程序中被反复创建。在symfony中，模型层包含足够的信息以允许生成CRUD操作代码，从而加快后端界面早期部分的开发。

## 示例数据模型

在本章中，清单将基于一个简单的示例演示symfony管理生成器的功能，这会让你想起第8章。这是著名的博客应用程序示例，包含两个BlogArticle和BlogComment类。清单14-1显示了其架构，如图14-1所示。

### 清单14-1 - 示例博客应用程序的Propel架构

```
propel:
  blog_category:
    id:     ~
    name:   varchar(255)
  blog_author:
    id:     ~
    name:   varchar(255)
```





blog_article:
  id:
    ~
  title:
    varchar(255)
  content:
    longvarchar
  blog_author_id:
    ~
  blog_category_id:
    ~
  is_published:
    boolean
  created_at:
    ~
blog_comment:
  id:
    ~
  blog_article_id:
    ~
  author:
    varchar(255)
  content:
    longvarchar
  created_at:
    ~

### 图 14-1 - 示例数据模型

![](img/0f886a7f4cbcc3939be96e985ca35ff4_231_0.png)

在创建 schema 以允许代码生成时，没有特定的规则需要遵循。Symfony 将按原样使用 schema 并解释其属性来生成管理后台。

> 要充分利用本章，你需要亲自实践这些示例。只有查看清单中描述的每一步，才能更好地理解 symfony 生成了什么，以及可以对生成的代码做什么。初始化模型只需调用 propel:build 任务：

### 清单 14-2

```
$ php symfony propel:build --all --no-confirmation
```

由于生成的管理后台依赖一些魔术方法来简化你的工作，请为每个模型类创建 `__toString()` 方法。

### 清单 14-3

```
class BlogAuthor extends BaseBlogAuthor
{
    public function __toString()
    {
        return $this->getName();
    }
}

class BlogCategory extends BaseBlogCategory
{
    public function __toString()
    {
        return $this->getName();
    }
}

class BlogArticle extends BaseBlogArticle
{
    public function __toString()
    {
        return $this->getTitle();
    }
}
```

## 管理后台

Symfony 可以根据 schema.yml 文件中的模型类定义，为你的应用程序的后端生成模块。你可以仅使用生成的管理模块来创建整个站点管理。本节的示例将描述添加到后端应用程序的管理模块。如果你的项目没有后端应用程序，请立即通过调用 generate:app 任务来创建其骨架：

```
$ php symfony generate:app backend
```

管理模块通过一个名为 generator.yml 的特殊配置文件来解释模型，可以修改该文件以扩展所有生成的组件和模块的外观与感觉。此类模块受益于前几章中描述的常规模块机制（布局、路由、自定义配置、自动加载等）。你还可以覆盖生成的操作或模板，以便将自己的功能集成到生成的管理后台中，但 generator.yml 应该处理最常见的需求，并将 PHP 代码的使用仅限于非常特定的情况。

> 尽管大多数常见需求都由 generator.yml 配置文件覆盖，你也可以通过配置类来配置管理模块，我们将在本章后面看到。

## 启动管理模块

使用 symfony，你按模型为基础来构建管理后台。基于 Propel 或 Doctrine 对象使用 propel:generate-admin 任务生成模块：

```
// Propel
$ php symfony propel:generate-admin backend BlogArticle --module=article
```

```
// Doctrine
$ php symfony doctrine:generate-admin backend BlogArticle --module=article
```

> 管理模块基于 REST 架构。propel:generate-admin 任务会自动将此类路由添加到 routing.yml 配置文件中：

```
# apps/backend/config/routing.yml
article:
 class: sfPropelRouteCollection
 options:
 model: BlogArticle
 module: article
 with_wildcard_routes: true
```

你也可以创建自己的路由，并将名称作为参数传递给任务，而不是模型类名：

### 清单 14-7

```
$ php symfony propel:generate-admin backend article --module=article
```

此调用足以在后端应用程序中基于 BlogArticle 类定义创建文章模块，并可通过以下方式访问：

### 清单 14-8

```
http://localhost/backend_dev.php/article
```

生成模块的外观与感觉（如图 14-2 和 14-3 所示）足够精致，可直接用于商业应用。

> 如果你看不到预期的外观与感觉（没有样式表和图像），这是因为你需要通过运行 plugin:publish-assets 任务在项目中安装资源：

### 清单 14-9

```
$ php symfony plugin:publish-assets
```

### 图 14-2 - 后端应用程序中文章模块的列表视图

### 文章列表

| ID | 标题 | 内容 | 博客作者 | 博客分类 | 是否已发布 | 创建时间 | 操作 |
|---|---|---|---|---|---|---|---|
| 1 | Welcome to the symfony weblog! | This is the first post of this weblog. | 1 | 1 | ✓ | 2010 年 4 月 1 日 下午 6:30 | 编辑 删除 |

1 条结果

选择操作：新建

### 图 14-3 - 后端应用程序中文章模块的编辑视图

### 编辑文章

| 标题 | Life is beautiful |
| 内容 | 博客的目的通常是谈论自己的心情。我今天心情很好。你呢？ |
| 博客作者 | Fabien |
| 博客分类 | 社区 |
| 是否已发布 | true |
| 创建时间 | 2010 年 4 月 1 日 16:40 |

## 生成的代码概览

apps/backend/modules/article/ 目录中的文章管理模块代码看起来是空的，因为它只是初始化的。审查此模块生成代码的最佳方法是使用浏览器与其交互，然后检查 cache/ 文件夹的内容。清单 14-2 列出了 cache/backend/ENV/modules/autoArticle/ 中找到的生成操作和模板：

### 清单 14-2 - 生成的管理元素，位于 cache/backend/ENV/modules/autoArticle/

```
// Actions in actions/actions.class.php
index // Displays the list of the records of the table
filter // Updates the filters used by the list
new // Displays the form to create a new record
create // Creates a new record
edit // Displays a form to modify the fields of a record
update // Updates an existing record
delete // Deletes a record
batch // Executes an action on a list of selected records
batchDelete // Executes a delete action on a list of selected records
```

```
// In templates/
- _assets.php
- _filters.php
- _filters_field.php
- _flashes.php
- _form.php
- _form_actions.php
- _form_field.php
- _form_fieldset.php
- _form_footer.php
- _form_header.php
- _list.php
- _list_actions.php
- _list_batch_actions.php
- _list_field_boolean.php
- _list_footer.php
- _list_header.php
- _list_td_actions.php
- _list_td_batch_actions.php
- _list_td_stacked.php
- _list_td_tabular.php
- _list_th_stacked.php
- _list_th_tabular.php
- _pagination.php
- editSuccess.php
- indexSuccess.php
- newSuccess.php
```

这表明生成的管理模块主要由三个视图组成：列表、新建和编辑。如果你查看代码，会发现它非常模块化、可读且可扩展。

## 介绍 generator.yml 配置文件

生成的管理模块依赖于 generator.yml YAML 配置文件中找到的参数。要查看新创建管理模块的默认配置，请打开位于 backend/modules/article/config/generator.yml 目录并在清单 14-3 中复现的 generator.yml 文件：

### 清单 14-3 - 默认生成器配置，位于 backend/modules/article/config/generator.yml

```
generator:
  class: sfPropelGenerator
  param:
    model_class:           BlogArticle
    theme:                 admin
    non_verbose_templates: true
    with_show:             false
    singular:              BlogArticle
    plural:                BlogArticles
    route_prefix:          blog_article
    with_propel_route:     1
    actions_base_class:    sfActions

  config:
    actions: ~
    fields: ~
    list: ~
    filter: ~
    form: ~
    edit: ~
    new: ~
```

此配置足以生成基本管理后台。任何自定义都在 config 键下添加。清单 14-4 显示了典型的自定义 generator.yml。

### 清单 14-4 - 典型完整生成器配置

```
generator:
  class: sfPropelGenerator
  param:
    model_class:          BlogArticle
    theme:                admin
    non_verbose_templates: true
    with_show:            false
    singular:             BlogArticle
    plural:               BlogArticles
    route_prefix:         blog_article
    with_propel_route:    1
    actions_base_class:   sfActions

  config:
    actions:
      _new: { label: "Create a new article" }

    fields:
      author_id:   { label: Article author }
      published_on: { credentials: editor }

    list:
      title:         Articles
      display:       [title, blog_author, blog_category]
      fields:
        published_on: { date_format: dd/MM/yy }
      layout:        stacked
      params:        |
        %%is_published%%<strong>%%=title%%</strong><br />by
        %%blog_author%%
        in %%blog_category%% (%%created_at%%)<p>%%content%%</p>
      max_per_page:  2
      sort:          [title, asc]

    filter:
      display: [title, blog_category_id, blog_author_id, is_published]

    form:
      display:
        "Post":      [title, blog_category_id, content]
        "Workflow":  [blog_author_id, is_published, created_at]
      fields:
        published_at: { help: "Date of publication" }
        title:        { attributes: { style: "width: 350px" } }

    new:
      title: New article

    edit:
      title: Editing article "%%title%%"
```





在此配置中，共有六个部分。其中四个表示视图（list、filter、new 和 edit），另外两个是“虚拟部分”（fields 和 form），仅用于配置目的。
以下各部分将详细说明此配置文件中可用的所有参数。

## 生成器配置

生成器配置文件非常强大，可让你以多种方式修改生成的管理界面。但这种功能需要付出代价：整体语法描述冗长，需要阅读和学习，使得本章成为本书中篇幅最长的章节之一。
本节的示例将基于 BlogComment 类定义，对文章管理模块和评论管理模块进行调整。通过运行 propel:generate-admin 任务来创建后者：

```
Listing 14-13
$ php symfony propel:generate-admin backend BlogComment --module=comment
```

### 图 14-4 - 管理生成器速查表

![](img/0f886a7f4cbcc3939be96e985ca35ff4_237_0.png)

### 字段

默认情况下，列表视图的列是 schema.yml 中定义的列。新建和编辑视图的字段是与模型关联的表单（BlogArticleForm）中定义的字段。通过 generator.yml，你可以选择显示哪些字段、隐藏哪些字段，以及添加自己的字段——即使它们在对象模型中没有直接对应关系。

### 字段设置

管理生成器会为 schema.yml 文件中的每个列创建一个字段。在 fields 键下，你可以修改每个字段的显示、格式化等方式。例如，清单 14-5 中显示的字段设置为 title 字段定义了自定义标签类和输入类型，并为 content 字段定义了标签和提示。以下各部分将详细描述每个参数的工作方式。

### 清单 14-5 - 为列设置自定义标签

```
config:
  fields:
    title:
      label: Article Title
      attributes: { class: foo }
    content: { label: Body, help: Fill in the article body }
```

除了对所有视图的默认定义外，你还可以为特定视图（list、filter、form、new 和 edit）覆盖字段设置，如清单 14-6 所示。

### 清单 14-6 - 按视图覆盖全局设置

```
config:
  fields:
    title: { label: Article Title }
    content: { label: Body }

  list:
    fields:
      title: { label: Title }

  form:
    fields:
      content: { label: Body of the article }
```

这是一个一般原则：在 fields 键下为整个模块设置的任何设置，都可以被特定视图区域覆盖。覆盖规则如下：

- new 和 edit 继承自 form，而 form 继承自 fields
- list 继承自 fields
- filter 继承自 fields

### 将字段添加到显示中

你在 fields 部分中定义的字段，可以在每个视图中以多种方式显示、隐藏、排序和分组。display 键用于此目的。例如，要安排评论模块的字段，请使用清单 14-7 的代码。

### 清单 14-7 - 选择要显示的字段，在 modules/comment/config/generator.yml 中

```
config:
  fields:
    article_id: { label: Article }
    created_at: { label: Published on }
    content: { label: Body }

  list:
    display: [id, blog_article_id, content]

  form:
    display:
      NONE: [blog_article_id]
      Editable: [author, content, created_at]
```

列表随后将显示三列，如图 14-5 所示，而新建和编辑表单将显示四个字段，组合成两组，如图 14-6 所示。

### 图 14-5 - 评论模块列表视图中的自定义列设置

| | Id | 博客文章 | 内容 | 操作 |
|---|---|---|---|---|
| ☐ | 1 | 1 | First！ | 编辑 删除 |
| ☐ | 2 | 1 | 哎太遗憾了，我想抢个第一！ | 编辑 删除 |
| ☐ | 3 | 1 | 这是一个非常棒的博客。 | 编辑 删除 |
| ☐ | 4 | 2 | 精彩故事！ | 编辑 删除 |
| ☐ | 5 | 2 | 你好 Fabien | 编辑 删除 |
| **5 条结果** | | | | |
| 选择操作 ▼ | 执行 | + 新建 | | |

### 图 14-6 - 评论模块编辑视图中的字段分组

### 编辑评论

| 字段 | 值 |
|---|---|
| 博客文章 | 欢迎来到 symfony 博客！▼ |

### 可编辑

| 作者 | Benoît |
| 内容 | 这是一个非常棒的博客。 |

| 发布于 | 04 ▼ / 01 ▼ / 2010 ▼ 17 ▼ : 10 ▼ |

| ✖ 删除 | 返回列表 | 保存 |

你可以以两种方式使用 display 设置：

- 对于列表视图：将字段放入简单数组中，以选择要显示的列及其出现顺序。
- 对于表单、新建和编辑视图：使用关联数组将字段分组，组名作为键，或使用 `NONE` 表示无名称的组。值仍然是有序列名的数组。请务必列出表单类引用的所有必需字段，否则可能会出现一些意外的验证错误（参见第 10 章）。

### 自定义字段

事实上，在 generator.yml 中配置的字段甚至不需要对应 schema 中定义的实际列。如果相关类提供自定义 getter，则可以将其用作列表视图的字段；如果存在 getter 和/或 setter，则也可以在编辑视图中使用。例如，你可以用类似清单 14-8 中的 getNbComments() 方法来扩展 BlogArticle 模型。

*清单 14-8 - 在模型中添加自定义 Getter，在 lib/model/BlogArticle.php 中*

```
public function getNbComments()
{
    return $this->countBlogComments();
}
```

此后，nb_comments 将作为生成模块中的一个字段可用（注意，getter 使用字段名称的 camelCase 版本），如清单 14-9 所示。

*清单 14-9 - 自定义 Getter 为管理模块提供额外列，在 backend/modules/article/config/generator.yml 中*

```
config:
  list:
    display: [title, blog_author, blog_category, nb_comments]
```

文章模块的生成列表视图如图 14-07 所示。

*图 14-07 - 文章模块列表视图中的自定义字段*

![](img/0f886a7f4cbcc3939be96e985ca35ff4_240_0.png)

### 局部字段

模型中的代码必须与表现层独立。先前提到的 getArticleLink() 方法示例不遵循这一分层分离原则，因为一些视图代码出现在了模型层中。事实上，如果尝试使用此配置，链接将默认被转义并显示为 <a> 标签。为了以正确方式实现相同目标，最好将输出自定义字段 HTML 的代码放在一个局部模板中。幸运的是，如果你声明一个以下划线开头的字段名，管理生成器允许这样做。在这种情况下，应按照清单 14-12 的方式修改清单 14-11 中的 generator.yml 文件。

*清单 14-12 - 局部模板可用作额外列——使用 _ 前缀*

```
config:
  list:
    display: [id, _article_link, created_at]
```

要使其工作，必须在 modules/comment/templates/ 目录中创建 _article_link.php 局部模板，如清单 14-13 所示。

### 清单 14-13 - 列表视图的局部模板示例，在 modules/comment/templates/_article_link.php 中

```
<?php echo link_to($BlogComment->getBlogArticle()->getTitle(),
  'blog_article_edit', $BlogComment->getBlogArticle()) ?>
```

请注意，局部字段的局部模板可以通过以类命名的变量访问当前对象（本示例中为 $BlogComment）。

### 图 14-08 - 文章模块列表视图中的局部字段

| | Id | 文章链接 | 内容 | 操作 |
|---|---|---|---|---|
| | 1 | 欢迎来到 symfony 博客！ | First！ | 编辑 删除 |
| | 2 | 欢迎来到 symfony 博客！ | 哎太遗憾了，我想抢个第一！ | 编辑 删除 |
| | 3 | 欢迎来到 symfony 博客！ | 这是一个非常棒的博客。 | 编辑 删除 |
| | 4 | Life is beautiful | 精彩故事！ | 编辑 删除 |
| | 5 | Life is beautiful | 你好 Fabien | 编辑 删除 |

5 条结果

选择操作 执行 新建

已遵循分层分离。如果你习惯于遵循分层分离，最终将获得更易维护的应用程序。

如果需要自定义局部字段的参数，请像处理普通字段一样，在 field 键下进行操作。只是不要在键中包含前导下划线 (_)——示例请参见清单 14-14。

### 清单 14-14 - 局部字段属性可在 fields 键下自定义

```
config:
  fields:
    article_link: { label: Article }
```

如果你的局部模板中逻辑过于臃肿，可能希望将其替换为组件。将 _ 前缀更改为 ~，即可定义组件字段，如清单 14-15 所示。

### 清单 14-15 - 组件可用作额外列——使用 ~ 前缀

```
config:
  list:
    display: [id, ~article_link, created_at]
```

在生成的模板中，这将导致对当前模块的 articleLink 组件进行调用。





> 自定义和部分字段可用于 `list`、`new`、`edit` 和 `filter` 视图。如果对多个视图使用相同的部分，则上下文（list、new、edit 或 filter）将存储在 `$type` 变量中。

## 视图自定义

若要更改 `new`、`edit` 和 `list` 视图的外观，您可能会想要修改模板。但由于它们是自动生成的，这么做并不是个好主意。相反，您应该使用 `generator.yml` 配置文件，因为它可以在不牺牲模块化的前提下完成您所需的几乎所有操作。

### 更改视图标题

除自定义字段集之外，`list`、`new` 和 `edit` 页面还可以使用自定义页面标题。例如，若要自定义 `article` 视图的标题，请参考清单 14-16。生成的 `edit` 视图如图 14-09 所示。

*清单 14-16 - 为每个视图设置自定义标题，位于 backend/modules/article/config/generator.yml*

```
config:
  list:
    title: List of Articles

  new:
    title: New Article

  edit:
    title: Edit Article %%title%% (%%id%%)
```

*图 14-09 - article 模块 edit 视图中的自定义标题*

![](img/0f886a7f4cbcc3939be96e985ca35ff4_243_0.png)

由于默认标题使用类名，因此它们通常足够好——前提是您的模型使用显式类名。

> 在 generator.yml 的字符串值中，可通过字段名（周围带有 %%）来访问字段的值。

### 添加工具提示

在 list、new、edit 和 filter 视图中，您可以添加工具提示来帮助描述显示的字段。例如，要为 comment 模块 edit 视图的 blog_article_id 字段添加工具提示，请按清单 14-17 在字段定义中添加 help 属性。结果如图 14-10 所示。

*清单 14-17 - 在 edit 视图中设置工具提示，位于 modules/comment/config/generator.yml*

```
config:
  edit:
    fields:
      blog_article_id: { help: The current comment relates to this article }
```

*图 14-10 - comment 模块 edit 视图中的工具提示*

![](img/0f886a7f4cbcc3939be96e985ca35ff4_244_0.png)

在 list 视图中，工具提示显示在列标题中；在 new、edit 和 filter 视图中，它们显示在字段标签下方。

### 修改日期格式

一旦使用 date_format 选项，即可使用自定义格式显示日期，如清单 14-18 所示。

*清单 14-18 - 在 list 视图中格式化日期*

```yaml
config:
  list:
    fields:
      created_at: { label: Published, date_format: dd/MM }
```

它采用前一章中描述的 format_date() 辅助函数相同的格式参数。

### 管理模块模板已就绪 i18n

自动生成的管理模块由界面字符串（默认操作名称、分页帮助消息等）和自定义字符串（标题、列标签、帮助消息、错误消息等）组成。

界面字符串的翻译已随 symfony 附带，支持多种语言。但您也可以通过在 i18n 目录中为 sf_admin 目录（catalogue）创建自定义 XLIFF 文件来添加自己的翻译或覆盖现有翻译（apps/frontend/i18n/sf_admin.XX.xml，其中 XX 是语言的 ISO 代码）。

生成模板中找到的所有自定义字符串也会自动国际化（即，包装在对 __() 辅助函数的调用中）。这意味着，您可以通过在 XLIFF 文件中添加短语的翻译（位于 apps/frontend/i18n/ 目录下，如前一章所述），轻松翻译生成的管理模块。

您可以通过指定 i18n_catalogue 参数来更改用于自定义字符串的默认目录（catalogue）：

```yaml
generator:
  class: sfPropelGenerator
  param:
    i18n_catalogue: admin
```

### list 视图特定的自定义

list 视图可以以表格形式显示记录的详细信息，也可以将所有详细信息堆叠在一行中。它还包含过滤器、分页和排序功能。这些功能可通过配置进行更改，如下一节所述。

### 更改布局

默认情况下，list 视图与 edit 视图之间的超链接由主键列承载。如果您参阅图 14-08，会发现 comment 列表中的 id 列不仅显示每条评论的主键，还提供了允许用户访问 edit 视图的超链接。

如果您希望记录详情的超链接出现在另一列上，请在 display 键中给列名加上等号（=）前缀。清单 14-19 演示了如何从 comment 列表的显示字段中移除 id，并将超链接放在 content 字段上。请参阅图 14-11 查看截图。

*清单 14-19 - 将 list 视图中 edit 视图的超链接移至另一列，位于 modules/comment/config/generator.yml*

```
config:
  list:
    display: [ _article_link, =content]
```

*图 14-11 - 在 comment 模块的 list 视图中，将 edit 视图的链接移至另一列*

| 文章链接 | 正文 | 操作 |
|---|---|---|
| 欢迎来到 symfony 博客！ | 抢沙发！ | 编辑 删除 |
| 欢迎来到 symfony 博客！ | 哎太遗憾了，我想抢第一！ | 编辑 删除 |
| 欢迎来到 symfony 博客！ | 这是一个非常好的博客。 | 编辑 删除 |
| 生活很美好 | 精彩故事！ | 编辑 删除 |
| 生活很美好 | 你好 Fabien | 编辑 删除 |

**5 条结果**

选择操作：新建

默认情况下，list 视图使用表格布局，字段以列形式显示，如前所示。但您也可以使用堆叠布局，将字段连接成一个跨越表格整个长度的单个字符串。如果选择堆叠布局，则必须在 params 键中设置定义列表每行值的模式。例如，清单 14-20 为 comment 模块的 list 视图定义了堆叠布局。结果如图 14-12 所示。

*清单 14-20 - 在 list 视图中使用堆叠布局，位于 modules/comment/config/generator.yml*

```
config:
  list:
    layout: stacked
    params: |
      %%content%%<br />
      (sent by %%author%% on %%created_at%% about %%_article_link%%)
    display: [ created_at, author, content]
```

*图 14-12 - comment 模块 list 视图中的堆叠布局*

![](img/0f886a7f4cbcc3939be96e985ca35ff4_246_0.png)

请注意，表格布局要求在 display 键下提供字段数组，而堆叠布局则使用 params 键来为每条记录生成 HTML 代码。不过，在堆叠布局中，display 数组仍用于确定可用于交互式排序的列标题。

### 过滤结果

在 list 视图中，您可以添加一组过滤交互。借助这些过滤器，用户既可以显示更少的结果，也能更快地找到所需结果。在 filter 键下配置过滤器，并提供字段名数组。例如，如清单 14-21 所示，为 comment 列表视图的 blog_article_id、author 和 created_at 字段添加过滤器，以显示类似图 14-13 的过滤框。

*清单 14-21 - 在 list 视图中设置过滤器，位于 modules/comment/config/generator.yml*

```
config:
  list:
    layout: stacked
    params: |
      %%content%% <br />
      (sent by %%author%% on %%created_at%% about %%_article_link%%)
    display: [created_at, author, content]

  filter:
    display: [blog_article_id, author, created_at]
```

*图 14-13 - comment 模块 list 视图中的过滤器*

![](img/0f886a7f4cbcc3939be96e985ca35ff4_247_0.png)

symfony 显示的过滤器取决于架构中定义的列类型，并可在过滤器表单类中自定义：

- 对于文本列（例如 comment 模块中的 author 字段），过滤器是一个文本输入框，允许基于文本的搜索（会自动添加通配符）。
- 对于外键（例如 comment 模块中的 blog_article_id 字段），过滤器是关联表记录的下拉列表。默认情况下，下拉列表的选项由关联类的 __toString() 方法返回。
- 对于日期列（例如 comment 模块中的 created_at 字段），过滤器是一对丰富的日期标签，允许选择时间区间。
- 对于布尔列，过滤器是一个包含 true、false 和 true or false 选项的下拉列表——最后一个值会重置过滤器。

就像 new 和 edit 视图绑定到表单类一样，过滤器使用与模型关联的默认过滤器表单类（例如 BlogArticle 模型对应 BlogArticleFormFilter）。通过为过滤器表单定义自定义类，您可以利用表单框架的强大功能并使用所有可用的过滤器小部件来自定义过滤器字段。这就像在 filter 条目下定义一个类一样简单，如清单 14-22 所示。

*清单 14-22 - 自定义用于过滤的表单类*

```
config:
  filter:
    class: BackendArticleFormFilter
```

> 要完全禁用过滤器，只需将过滤器使用的类指定为 false 即可。

您也可以使用部分过滤器来实现自定义过滤逻辑。每个部分都会接收表单以及呈现表单元素时使用的 HTML 属性。清单 14-23 展示了一个示例实现，它使用部分来模拟默认行为。

*清单 14-23 - 使用部分过滤器*

```
// Define the partial, in templates/_state.php
<?php echo $form['name']->render($attributes->getRawValue()) ?>

// Add the partial filter in the filter list, in config/generator.yml
config:
  filter: [created_at, _state]





## 对列表进行排序

在列表视图中，表格标题是超链接，可用于重新排序列表，如图 14-18 所示。这些标题在表格布局和堆叠布局中均会显示。单击这些链接会带排序参数重新加载页面，从而相应重新排列列表顺序。

图 14-14 - 列表视图的表格标题为排序控件

![](img/0f886a7f4cbcc3939be96e985ca35ff4_248_0.png)

你可以复用语法来指向按某一列直接排序的列表：

```
<?php echo link_to('Comment list by date',
'@blog_comment?sort=created_at&sort_type=desc' ) ?>
```

你还可以直接在 generator.yml 文件中为列表视图定义默认排序顺序。语法遵循清单 14-24 给出的示例。

清单 14-24 - 在列表视图中设置默认排序字段

```
config:
  list:
    sort: created_at
    # Alternative syntax, to specify a sort order
    sort: [created_at, desc]
```

> 仅对应实际列的字段才会转换为排序控件——而非自定义字段或部分字段。

## 自定义分页

生成的后台能够有效处理甚至大型表格，因为列表视图默认使用分页。当表格中实际行数超过每页最大行数时，分页控件会出现在列表底部。例如，图 14-19 显示了表格中包含六条测试评论但每页显示限制为五条评论的评论列表。分页确保了良好的性能，因为只有显示的行会从数据库中实际检索，也确保了良好的可用性，因为即使是包含数百万行的表格也可以由后台模块管理。

图 14-15 - 长列表上会出现分页控件

![](img/0f886a7f4cbcc3939be96e985ca35ff4_249_0.png)

你可以使用 max_per_page 参数自定义每页显示的记录数量：

```
Listing 14-34
config:
  list:
    max_per_page: 5
```

## 使用连接加速页面传递

默认情况下，后台生成器使用简单的 doSelect() 来检索记录列表。但是，如果在列表中使用关联对象，显示列表所需的数据库查询数量可能会迅速增加。例如，如果你想在评论列表中显示文章名称，则列表中的每篇文章都需要额外查询来检索关联的 BlogArticle 对象。因此，你可能希望强制分页器使用 doSelectJoinXXX() 方法来优化查询数量。这可以通过 peer_method 参数指定。

```
Listing 14-35
config:
  list:
    peer_method: doSelectJoinBlogArticle
```

第 18 章更详细地解释了连接的概念。

## 新建和编辑视图的特定自定义

在新建或编辑视图中，用户可以修改新记录或给定记录的每个列的值。默认情况下，后台生成器使用的表单是与模型关联的表单：BlogArticle 模型对应 BlogArticleForm。你可以通过在 form 条目下定义类（如清单 14-25 所示）来自定义要使用的类。

清单 14-25 - 自定义新建和编辑视图中使用的表单类

```
Listing 14-36
config:
  form:
    class: BackendBlogArticleForm
```

使用自定义表单类允许自定义后台生成器使用的所有小部件和验证器。然后可以使用默认表单类，并专门为前端应用程序对其进行自定义。

你还可以直接在 generator.yml 配置文件中自定义表单的标签、帮助消息和布局（如清单 14-26 所示）。

清单 14-26 - 自定义表单显示

```
config:
  form:
    display:
      NONE: [article_id]
      Editable: [author, content, created_at]
    fields:
      content: { label: body, help: "The content can be in the Markdown
format" }
```

## 处理部分字段

部分字段可以在新建和编辑视图中使用，就像在列表视图中一样。

## 处理外键

如果你的架构定义了表关系，生成的后台模块将利用此关系并提供更多自动化控件，从而大大简化关系管理。

## 一对多关系

后台生成器会处理 1-n 表关系。如前文图 14-1 所示，blog_comment 表通过 blog_article_id 字段与 blog_article 表相关联。如果你使用后台生成器初始化 BlogComment 类的模块，编辑视图将自动将 blog_article_id 显示为下拉列表，列出 blog_article 表中可用记录的 ID（再次查看图 14-9 以获取示意图）。

如果你需要在文章模块中显示与文章相关的评论列表（n-1 关系），也是如此。

## 多对多关系

Symfony 也开箱即用地处理 n-n 表关系，如图 14-16 所示。

图 14-16 - 多对多关系

![](img/0f886a7f4cbcc3939be96e985ca35ff4_250_0.png)

通过自定义用于渲染关系的小部件，你可以微调字段的渲染效果（如图 14-17 所示）：

图 14-17 - 多对多关系的可用控件

![](img/0f886a7f4cbcc3939be96e985ca35ff4_251_0.png)

## 添加交互操作

后台模块允许用户执行常规 CRUD 操作，但你也可以添加自己的交互操作或限制视图的可能交互操作。例如，清单 14-27 所示的交互定义授予对文章模块所有默认 CRUD 操作的访问权限。

清单 14-27 - 在 backend/modules/article/config/generator.yml 中为每个视图定义交互操作

```
Listing 14-38
config:
  list:
    title: List of Articles
    object_actions:
      _edit: ~
      _delete: ~
    batch_actions:
      _delete: ~
    actions:
      _new: ~

  edit:
    title: Body of article %%title%%
    actions:
      _delete: ~
      _list: ~
      _save: ~
      _save_and_add: ~
```

在列表视图中，有三个操作设置：每个对象可用的操作（object_actions）、对象选择可用的操作（batch_actions）以及整个页面可用的操作（actions）。清单 14-27 中定义的列表交互操作渲染效果如图 14-18 所示。每一行显示一个编辑记录的按钮和一个删除记录的按钮，此外每行还有一个复选框用于删除选定的记录。在列表底部，有一个按钮允许创建新记录。

图 14-18 - 列表视图中的交互操作

| Id | 博客文章 | 内容 | 操作 |
|---|---|---|---|
| 1 | 1 | 第一！ | 编辑 删除 |
| 2 | 1 | 哎，太糟糕了，我想当第一个！ | 编辑 删除 |
| 3 | 1 | 这是一个非常好的博客。 | 编辑 删除 |
| 4 | 2 | 好故事！ | 编辑 删除 |
| 5 | 2 | 你好 Fabien | 编辑 删除 |

5 条结果

选择操作 新建

在新建和编辑视图中，由于一次只编辑一条记录，因此只需要定义一组操作（在 actions 下）。清单 14-27 中定义的编辑交互操作渲染效果如图 14-23 所示。save 和 save_and_add 操作都会将当前编辑保存到记录中，区别在于 save 操作在保存后显示当前记录的编辑视图，而 save_and_add 操作显示一个新视图以添加另一条记录。save_and_add 操作是一个快捷方式，在快速连续添加多条记录时非常有用。至于删除操作的位置，它与其他按钮分开，以便用户不会误点。

以下划线（_）开头的交互名称告诉 symfony 使用与这些交互对应的默认图标和操作。后台生成器理解 _edit、_delete、_new、_list、_save、_save_and_add 和 _create。

图 14-19 - 编辑视图中的交互操作

文章正文 生活真美好

![](img/0f886a7f4cbcc3939be96e985ca35ff4_252_0.png)

但你也可以添加自定义交互操作，在此情况下，你必须指定一个不以下划线开头的名称，以及当前模块中的目标操作，如清单 14-28 所示。

清单 14-28 - 定义自定义交互操作

```
list:
  title: List of Articles
  object_actions:
    _edit: -
```



```yaml
_delete: -
addcomment: { label: Add a comment, action: addComment }
```

列表中的每篇文章现在都将显示 Add a comment 链接，如图 14-20 所示。单击它会触发对当前模块中 addComment 操作的调用。当前对象的主键会自动添加到请求参数中。

### 图 14-20 - 列表视图中的自定义交互

![](img/0f886a7f4cbcc3939be96e985ca35ff4_253_0.png)

addComment 操作可以按代码清单 14-29 所示实现。

### 代码清单 14-29 - 在 actions/actions.class.php 中实现自定义交互操作

```php
public function executeAddComment($request)
{
    $comment = new BlogComment();
    $comment->setArticleId($request->getParameter('id'));
    $comment->save();

    $this->redirect('blog_comment_edit', $comment);
}
```

批量操作在 ids 请求参数中接收所选记录的主键数组。

关于操作的最后一点：如果您想完全禁止某个类别的操作，请使用空列表，如代码清单 14-30 所示。

### 代码清单 14-30 - 删除列表视图中的所有操作

```yaml
config:
  list:
    title: List of Articles
    actions: {}
```

## 表单验证

验证由 new 和 edit 视图自动使用的表单处理。您可以通过编辑相应的表单类来自定义它。

## 使用凭证限制用户操作

对于给定的管理模块，可用字段和交互可根据登录用户的凭证而有所不同（有关 symfony 安全功能的描述，请参阅第 6 章）。

生成器中的字段可以考虑 credentials 参数，以便仅出现拥有适当凭证的用户。这适用于列表条目。此外，生成器还可以根据凭证隐藏交互。代码清单 14-31 演示了这些功能。

### 代码清单 14-31 - 在 generator.yml 中使用凭证

```yaml
config:
  # The id column is displayed only for users with the admin credential
  list:
    title:       List of Articles
    display:     [id, =title, content, nb_comments]
    fields:
      id:        { credentials: [admin] }

  # The addcomment interaction is restricted to the users with the admin credential
  actions:
    addcomment: { credentials: [admin] }
```

## 修改生成模块的呈现

您可以修改生成模块的呈现，使其匹配任何现有的图形规范，不仅通过应用自己的样式表，还可以通过覆盖默认模板。

### 使用自定义样式表

由于生成的 HTML 是结构化内容，您可以随心所欲地进行呈现。

您可以通过在生成器配置中添加 css 参数，为管理模块定义要使用的替代 CSS，以代替默认 CSS，如代码清单 14-32 所示。

### 代码清单 14-32 - 使用自定义样式表代替默认样式表

```yaml
generator:
  class: sfPropelGenerator
  param:
    model_class:       BlogArticle
    theme:             admin
    non_verbose_templates: true
    with_show:         false
    singular:          BlogArticle
    plural:            BlogArticles
    route_prefix:      blog_article
    with_propel_route: 1
    actions_base_class: sfActions
    css:               mystylesheet
```

或者，您也可以使用模块 view.yml 提供的机制，按视图覆盖样式。

### 创建自定义页眉和页脚

列表、new 和 edit 视图会系统地包含页眉和页脚局部模板。默认情况下，管理模块的 templates/ 目录中没有此类局部模板，但您只需添加一个以下列名称之一的文件，即可使其自动包含：

- _list_header.php
- _list_footer.php
- _form_header.php
- _form_footer.php

例如，如果要为 article/edit 视图添加自定义页眉，请创建名为 _form_header.php 的文件，如代码清单 14-33 所示。它无需进一步配置即可工作。

### 代码清单 14-33 - 示例 edit 页眉局部模板，位于 modules/article/templates/_form_header.php

```php
<?php if ($blog_article->getNbComments() > 0): ?>
<h2>This article has <?php echo $blog_article->getNbComments() ?> comments.</h2>
<?php endif; ?>
```

请注意，edit 局部模板始终可以通过以类命名的变量访问当前对象，而 list 局部模板始终可以通过 $pager 变量访问当前分页器。

### 自定义主题

还有其他从框架继承的局部模板，可以在模块 templates/ 文件夹中覆盖以满足您的自定义要求。

生成器模板被切分成可以独立覆盖的小部分，操作也可以逐个更改。

但是，如果您想以相同的方式覆盖多个模块中的这些内容，您可能应该创建一个可重用的主题。主题是模板和操作的子集，如果在 generator.yml 开头的 theme 值中指定，则可由管理模块使用。使用默认主题时，symfony 使用 sfConfig::get('sf_symfony_lib_dir')/plugins/sfPropelPlugin/data/generator/sfPropelModule/admin/ 中定义的文件。

主题文件必须位于项目树结构中，即 data/generator/sfPropelModule/[theme_name]/ 目录，您可以通过从默认主题（位于 sfConfig::get('sf_symfony_lib_dir')/plugins/sfPropelPlugin/data/generator/sfPropelModule/admin/ 目录中）复制要覆盖的文件来引导新主题：

// Partials, in [theme_name]/template/templates/
- _assets.php
- _filters.php
- _filters_field.php
- _flashes.php
- _form.php
- _form_actions.php
- _form_field.php
- _form_fieldset.php
- _form_footer.php
- _form_header.php
- _list.php
- _list_actions.php
- _list_batch_actions.php
- _list_field_boolean.php
- _list_footer.php
- _list_header.php
- _list_td_actions.php
- _list_td_batch_actions.php
- _list_td_stacked.php
- _list_td_tabular.php
- _list_th_stacked.php
- _list_th_tabular.php
- _pagination.php
- editSuccess.php
- indexSuccess.php
- newSuccess.php

// Actions, in [theme_name]/parts
- actionsConfiguration.php
- batchAction.php
- configuration.php
- createAction.php
- deleteAction.php
- editAction.php
- fieldsConfiguration.php
- filterAction.php
- filtersAction.php
- filtersConfiguration.php
- indexAction.php
- newAction.php
- paginationAction.php
- paginationConfiguration.php
- processFormAction.php
- sortingAction.php
- sortingConfiguration.php
- updateAction.php

请注意，模板文件实际上是模板的模板，即将由特殊实用程序解析以根据生成器设置生成模板的 PHP 文件（这称为编译阶段）。生成的模板在实际浏览期间仍必须包含要执行的 PHP 代码，因此模板的模板使用替代语法来保持首次遍历时 PHP 代码不执行。代码清单 14-34 显示了默认模板的模板的摘录。

### 代码清单 14-34 - 模板的模板语法

```php
<h1>[?php echo <?php echo $this->getI18NString('edit.title') ? ? ></h1>
```

```php
[?php include_partial('<?php echo $this->getModuleName() ?>/flashes') ?]
```

在此清单中，由 <? 引入的 PHP 代码会立即执行（在编译时），由 [? 引入的代码仅在执行时执行，但模板引擎最终会将 [? 标签转换为 <? 标签，使生成的模板如下所示：

```php
<h1><?php echo __('List of all Articles') ?></h1>
```

```php
<?php include_partial('article/flashes') ?>
```

处理模板的模板比较棘手，因此如果您想创建自己的主题，最好的建议是从 admin 主题开始，逐步修改并进行广泛测试。

> 您还可以将生成器主题打包为插件，这使其更加可重用且易于跨多个应用程序部署。有关详细信息，请参阅第 17 章。





## 构建你自己的生成器

管理生成器使用一组 symfony 内部组件，自动在缓存中创建生成的操作和模板，使用主题，以及解析模板的模板。

这意味着 symfony 提供了构建你自己的生成器所需的所有工具，它可以看起来像现有的生成器，也可以完全不同。模块的生成由 sfGeneratorManager 类的 generate() 方法管理。例如，要生成一个后台管理，symfony 内部会调用以下内容：

```php
$manager = new sfGeneratorManager();
$data = $manager->generate('sfPropelGenerator', $parameters);
```

如果你想构建自己的生成器，应该查看 sfGeneratorManager 和 sfGenerator 类的 API 文档，并以 sfModelGenerator 和 sfPropelGenerator 类为例。

## 总结

要自动生成你的后端应用，基础是定义良好的模式和对象模型。对生成的管理模块的自定义大多通过配置来完成。

generator.yml 文件是生成后端编程的核心。它允许完全自定义列表、新建和编辑视图的内容、功能以及外观和感觉。你可以直接在 YAML 中管理字段标签、工具提示、筛选器、排序顺序、页面大小、输入类型、外键关系、自定义交互和凭据，而无需编写一行 PHP 代码。

如果管理生成器原生不支持你需要的功能，部分字段和重写操作的能力提供了完全的可扩展性。此外，你可以通过主题机制重复使用对管理生成器机制的调整。

# 第 15 章 单元测试和功能测试

自动化测试是面向对象编程以来编程领域最伟大的进步之一。它们特别适合开发 Web 应用程序，即使发布频繁，也能保证应用程序的质量。Symfony 提供了多种工具来便于自动化测试，本章将介绍这些工具。

## 自动化测试

任何有 Web 应用开发经验的开发者都深知做好测试所需的时间。编写测试用例、运行它们并分析结果是一项乏味的工作。此外，Web 应用程序的需求往往会不断变化，这导致不断的发布流和持续的代码重构需求。在此背景下，新错误很可能会定期出现。

这就是为什么自动化测试是成功开发环境中建议的（如果不是必须的）部分。一组测试用例可以保证应用程序确实按预期运行。即使内部结构经常被重构，自动化测试也能防止意外的回归。此外，它们迫使开发者以测试框架能够理解的标准化、严格的格式编写测试。

自动化测试有时可以取代开发者文档，因为它们可以清晰地说明应用程序应该做什么。一个好的测试套件显示了一组测试输入所期望的输出，这是解释方法目的的好方法。

Symfony 框架将这一原则应用于自身。框架的内部结构由自动化测试验证。这些单元测试和功能测试未随 PEAR 包一起提供，但你可以从 SVN 仓库检出它们，或在线浏览它们51。

## 单元测试和功能测试

单元测试确认一个单元代码组件对给定输入提供正确的输出。它们验证函数和方法在每个特定情况下的工作方式。单元测试一次处理一个案例，因此例如，如果一个方法在某些情况下的工作方式不同，可能需要多个单元测试。

功能测试验证的不是简单的输入到输出转换，而是一个完整的功能。例如，缓存系统只能通过功能测试来验证，因为它涉及多个步骤：第一次请求页面时，它会被渲染；第二次时，它从缓存中获取。因此，功能测试验证一个过程并需要一个场景。在 Symfony 中，你应该为所有操作编写功能测试。

对于最复杂的交互，这两种类型可能不够。例如，Ajax 交互需要 Web 浏览器来执行 JavaScript，因此自动测试它们需要特殊的第三方工具。此外，视觉效果只能由人来验证。

如果你对自动化测试有广泛的方法，你可能需要结合使用所有这些方法。作为指导方针，请记住保持测试简单且易读。

> 自动化测试通过将结果与预期输出进行比较来工作。换句话说，它们评估断言（如 $a == 2 这样的表达式）。断言的值为真或假，这决定了测试是通过还是失败。“断言”一词在处理自动化测试技术时经常使用。

## 测试驱动开发

在测试驱动开发（TDD）方法论中，测试是在代码之前编写的。先编写测试有助于你在实际开发之前专注于函数应该完成的任务。这是其他方法论（如极限编程 XP）也推荐的良好做法。此外，它考虑到了一个不可否认的事实：如果你不先编写单元测试，你就永远不会编写它们。

例如，假设你必须开发一个文本去除函数。该函数删除字符串开头和结尾的空白字符，将非字母字符替换为下划线，并将所有大写字符转换为小写字符。在测试驱动开发中，你首先会考虑所有可能的情况，并为每个情况提供示例输入和预期输出，如表 15-1 所示。

表 15-1 - 文本去除函数的测试用例列表

| 输入 | 预期输出 |
|---|---|
| " foo " | "foo" |
| "foo bar" | "foo_bar" |
| " - )foo: .=bar?" | "_ foo__ bar_" |
| "FooBar" | "foobar" |
| "Don't foo-bar me!" | "don_t_foo_bar_me_" |

你将编写单元测试，运行它们，并看到它们失败。然后你将添加必要的代码来处理第一个测试用例，再次运行测试，看到第一个通过，并继续这样做。最终，当所有测试用例都通过时，函数就是正确的。

使用测试驱动方法论构建的应用程序最终会有大约与实际代码一样多的测试代码。由于你不想花时间调试测试用例，请保持它们简单。

> 重构方法可能会创造以前未出现过的新错误。这就是为什么在将应用程序的新版本部署到生产环境之前运行所有自动化测试也是一种良好做法——这称为回归测试。

## Lime 测试框架

PHP 世界中有许多单元测试框架，最著名的是 PHPUnit。Symfony 也有自己的框架，称为 lime。它基于 Test::More Perl 库，并且符合 TAP 标准，这意味着测试结果按照 Test Anything Protocol 指定的方式显示，旨在提高测试输出的可读性。

Lime 提供对单元测试的支持。它比其他 PHP 测试框架更轻量，并具有以下几个优点：

- 它在沙箱中启动测试文件，以避免每次测试运行之间出现奇怪的副作用。并非所有测试框架都能为每个测试保证干净的环境。
- Lime 测试非常易读，测试输出也是如此。在兼容的系统上，lime 以智能方式使用彩色输出来区分重要信息。
- Symfony 本身使用 lime 测试进行回归测试，因此可以在 symfony 源代码中找到许多单元和功能测试示例。
- lime 核心由单元测试验证。
- 它是用 PHP 编写的，速度快，代码编写良好，且没有依赖。

接下来描述的各种测试使用 lime 语法。它们与任何 Symfony 安装开箱即用。

![](img/0f886a7f4cbcc3939be96e985ca35ff4_260_0.png)

> 单元测试和功能测试不应在生产环境中运行。它们是开发者工具，因此应该在开发者的计算机上运行，而不是在主机服务器上运行。

## 单元测试

Symfony 单元测试是简单的 PHP 文件，以 `Test.php` 结尾，并位于你的应用程序的 `test/unit/` 目录中。它们遵循简单且易读的语法。

### 单元测试长什么样？

清单 15-1 显示了 `strtolower()` 函数的一组典型单元测试。它从实例化 `lime_test` 对象开始（目前你不需要担心参数）。每个单元测试都是对 `lime_test` 实例的方法的调用。这些方法的最后一个参数始终是一个可选字符串，用作输出。

清单 15-1 - 示例单元测试文件，位于 `test/unit/strtolowerTest.php`

```php
<?php

include dirname(__FILE__).'/../bootstrap/unit.php';

$t = new lime_test(7);

// strtolower()
$t->diag('strtolower()');
$t->isa_ok(strtolower('Foo'), 'string',
    'strtolower() returns a string');
$t->is(strtolower('FOO'), 'foo',
    'strtolower() transforms the input to lowercase');
$t->is(strtolower('foo'), 'foo',
    'strtolower() leaves lowercase characters unchanged');
$t->is(strtolower('12#?@~'), '12#?@~',
    'strtolower() leaves non alphabetical characters unchanged');
$t->is(strtolower('FOO BAR'), 'foo bar',
    'strtolower() leaves blanks alone');
$t->is(strtolower('Foo bAr'), 'foo bar',
    'strtolower() deals with mixed case input');
$t->is(strtolower(''), 'foo',
    'strtolower() transforms empty strings into foo');
```




使用 test:unit 任务从命令行启动测试集。命令行输出非常明确，可帮助您定位哪些测试失败、哪些测试通过。有关示例测试的输出，请参见清单 15-2。

## 清单 15-2 - 从命令行启动单个单元测试

```
$ php symfony test:unit strtolower
1..7
# strtolower()
ok 1 - strtolower() returns a string
ok 2 - strtolower() transforms the input to lowercase
ok 3 - strtolower() leaves lowercase characters unchanged
ok 4 - strtolower() leaves non alphabetical characters unchanged
ok 5 - strtolower() leaves blanks alone
ok 6 - strtolower() deals with mixed case input
not ok 7 - strtolower() transforms empty strings into foo
#   Failed test (.\\batch\\test.php at line 21)
#   got:   ''
#   expected: 'foo'
# Looks like you failed 1 tests of 7.
```

![](img/0f886a7f4cbcc3939be96e985ca35ff4_261_0.png)

清单 15-1 开头的 include 语句是可选的，但它使测试文件成为一个独立的 PHP 脚本，您可以在不使用 symfony 命令行的情况下执行它，只需调用 php test/unit/strtolowerTest.php。

## 单元测试方法

lime_test 对象提供了大量测试方法，如表 15-2 所示。

## 表 15-2 - lime_test 对象的单元测试方法

| 方法 | 说明 |
|---|---|
| diag($msg) | 输出诊断消息但不运行测试 |
| ok($test[, $msg]) | 测试条件，若条件为真则通过 |
| is($value1, $value2[, $msg]) | 比较两个值，若相等（==）则通过 |
| isnt($value1, $value2[, $msg]) | 比较两个值，若不相等则通过 |
| like($string, $regexp[, $msg]) | 将字符串与正则表达式进行测试 |
| unlike($string, $regexp[, $msg]) | 检查字符串不匹配正则表达式 |
| cmp_ok($value1, $operator, $value2[, $msg]) | 使用运算符比较两个参数 |
| isa_ok($variable, $type[, $msg]) | 检查参数的类型 |
| isa_ok($object, $class[, $msg]) | 检查对象的类 |
| can_ok($object, $method[, $msg]) | 检查对象或类中方法的可用性 |
| is_deeply($array1, $array2[, $msg]) | 检查两个数组是否具有相同的值 |
| `include_ok($file[, $msg])` | 验证文件存在且已正确包含 |
| `fail([$msg])` | 始终失败—用于测试异常 |
| `pass([$msg])` | 始终通过—用于测试异常 |
| `skip([$msg, $nb_tests])` | 计为 $nb_tests 个测试—用于条件测试 |
| `todo([$msg])` | 计为一个测试—用于尚未编写的测试 |
| `comment($msg)` | 输出注释消息但不运行测试 |
| `error($msg)` | 输出错误消息但不运行测试 |
| `info($msg)` | 输出信息消息但不运行测试 |

语法非常直观；请注意，大多数方法都将消息作为最后一个参数。当测试通过时，该消息会显示在输出中。实际上，学习这些方法的最佳方式是对其进行测试，因此请查看清单 15-3，它使用了所有这些方法。

## 清单 15-3 - 测试 lime_test 对象的方法，位于 test/unit/exampleTest.php

```
<?php

include dirname(__FILE__).'/../bootstrap/unit.php';

// Stub objects and functions for test purposes
class myObject
{
    public function myMethod()
    {
    }
}

function throw_an_exception()
{
    throw new Exception('exception thrown');
}

// Initialize the test object
$t = new lime_test(16);

$t->diag('hello world');
$t->ok(1 == '1', 'the equal operator ignores type');
$t->is(1, '1', 'a string is converted to a number for comparison');
$t->isnt(0, 1, 'zero and one are not equal');
$t->like('test01', '/test\\d+/', 'test01 follows the test numbering pattern');
$t->unlike('tests01', '/test\\d+/', 'tests01 does not follow the pattern');
$t->cmp_ok(1, '<', 2, 'one is inferior to two');
$t->cmp_ok(1, '!===', true, 'one and true are not identical');
$t->isa_ok('foobar', 'string', '\\'foobar\\' is a string');
$t->isa_ok(new myObject(), 'myObject', 'new creates object of the right class');
$t->can_ok(new myObject(), 'myMethod', 'objects of class myObject do have a myMethod method');
$array1 = array(1, 2, array(1 => 'foo', 'a' => '4'));
$t->is_deeply($array1, array(1, 2, array(1 => 'foo', 'a' => '4')),
'the first and the second array are the same');
$t->include_ok('./fooBar.php', 'the fooBar.php file was properly
included');

try
{
throw_an_exception();
$t->fail('no code should be executed after throwing an exception');
}
catch (Exception $e)
{
$t->pass('exception caught successfully');
}

if (!isset($foobar))
{
$t->skip('skipping one test to keep the test count exact in the
condition', 1);
}
else
{
$t->ok($foobar, 'foobar');
}

$t->todo('one test left to do');
```

在 symfony 单元测试中，您将找到这些方法用法的许多其他示例。

> 您可能会奇怪，为什么在这里使用 is() 而不是 ok()。is() 输出的错误消息要明确得多；它显示了测试的两个成员，而 ok() 仅说明条件失败。

## 测试参数

lime_test 对象的初始化将其第一个参数设置为应执行的测试数量。如果最终执行的测试数量与该数字不同，lime 输出会向您发出警告。例如，清单 15-3 的测试集输出如清单 15-4 所示。初始化规定应运行 16 个测试，但实际上只运行了 15 个，因此输出会指明这一点。

## 清单 15-4 - 已运行测试的计数可帮助您规划测试

```
$ php symfony test:unit example
1..16
# hello world
ok 1 - the equal operator ignores type
ok 2 - a string is converted to a number for comparison
ok 3 - zero and one are not equal
ok 4 - test01 follows the test numbering pattern
ok 5 - tests01 does not follow the pattern
ok 6 - one is inferior to two
ok 7 - one and true are not identical
ok 8 - 'foobar' is a string
ok 9 - new creates object of the right class
ok 10 - objects of class myObject do have a myMethod method
ok 11 - the first and the second array are the same
not ok 12 - the fooBar.php file was properly included
#       Failed test (./test/unit/testTest.php at line 27)
#       Tried to include './fooBar.php'
ok 13 - exception caught successfully
ok 14 # SKIP skipping one test to keep the test count exact in the
condition
ok 15 # TODO one test left to do
# Looks like you planned 16 tests but only ran 15.
# Looks like you failed 1 tests of 16.
```

diag() 方法不计入测试。使用它来显示注释，以便您的测试输出保持井井有条且易于阅读。另一方面，todo() 和 skip() 方法计为实际测试。try/catch 块中的 pass()/fail() 组合计为单个测试。

一个周密的测试策略必须包含预期的测试数量。验证您自己的测试文件时，您会发现这一点非常有用——尤其是在测试在条件或异常中运行的复杂情况下。如果测试在某个点失败，您会很快看到，因为最终运行的测试数量与初始化时给出的数量不匹配。

## test:unit 任务

test:unit 任务用于从命令行启动单元测试，它接受测试名称列表或文件模式。有关详细信息，请参见清单 15-5。

## 清单 15-5 - 启动单元测试

```
// Test directory structure
test/
  unit/
    myFunctionTest.php
    mySecondFunctionTest.php
    foo/
      barTest.php

$ php symfony test:unit myFunction    # Run
myFunctionTest.php
$ php symfony test:unit myFunction mySecondFunction   # Run both tests
$ php symfony test:unit foo/*        # Run barTest.php
$ php symfony test:unit *          # Run all tests
     (recursive)
```

## 存根、测试夹具和自动加载

在单元测试中，自动加载功能默认不启用。您在测试中使用的每个类都必须定义在测试文件中，或作为外部依赖项引入。这就是为什么许多测试文件都以一组 include 行开头，如清单 15-6 所示。

## 清单 15-6 - 在单元测试中包含类

```
<?php

include dirname(__FILE__).'/../bootstrap/unit.php';
require_once sfConfig::get('sf_symfony_lib_dir').'/util/
sfToolkit.class.php';

$t = new lime_test(7);
```


```php
// isPathAbsolute()
$t->diag('isPathAbsolute()');
$t->is(sfToolkit::isPathAbsolute('/test'), true,
    'isPathAbsolute() returns true if path is absolute');
$t->is(sfToolkit::isPathAbsolute('\\test'), true,
    'isPathAbsolute() returns true if path is absolute');
$t->is(sfToolkit::isPathAbsolute('C:\\test'), true,
    'isPathAbsolute() returns true if path is absolute');
$t->is(sfToolkit::isPathAbsolute('d:/test'), true,
    'isPathAbsolute() returns true if path is absolute');
$t->is(sfToolkit::isPathAbsolute('test'), false,
    'isPathAbsolute() returns false if path is relative');
$t->is(sfToolkit::isPathAbsolute('../test'), false,
    'isPathAbsolute() returns false if path is relative');
$t->is(sfToolkit::isPathAbsolute('..\\test'), false,
    'isPathAbsolute() returns false if path is relative');
```

在单元测试中，你需要实例化不仅要测试的对象，还要实例化它所依赖的对象。由于单元测试必须保持单一性，依赖其他类可能会导致如果某个类出错，不止一个测试失败。此外，设置真实对象成本高昂，无论是代码行数还是执行时间。请记住，速度在单元测试中至关重要，因为开发者很快就会对缓慢的过程失去耐心。

每当你开始为单元测试包含许多脚本时，你可能需要一个简单的自动加载系统。为此，sfSimpleAutoload 类（必须手动包含）提供了一个 addDirectory() 方法，该方法期望一个绝对路径作为参数，并且在你需要在搜索路径中包含多个目录时可以被多次调用。该路径下的所有类都将被自动加载。例如，如果你想自动加载位于 sfConfig::get('sf_symfony_lib_dir')/util/ 下的所有类，请按照以下方式启动你的单元测试脚本：

```php
require_once sfConfig::get('sf_symfony_lib_dir').'/autoload/sfSimpleAutoload.class.php';
$autoload = sfSimpleAutoload::getInstance();
$autoload->addDirectory(sfConfig::get('sf_symfony_lib_dir').'/util');
$autoload->register();
```

自动加载问题的另一个良好解决方案是使用存根。存根是一个类的替代实现，其中真实方法被简单的预置数据替换。它模拟真实类的行为，但没有其成本。存根的一个好例子是数据库连接或 Web 服务接口。在清单 15-7 中，映射 API 的单元测试依赖于 WebService 类。与其调用实际 Web 服务类的真实 fetch() 方法，不如测试使用一个返回测试数据的存根。

### 清单 15-7 - 在单元测试中使用存根

```php
require_once dirname(__FILE__).'/../../../lib/WebService.class.php';
require_once dirname(__FILE__).'/../../../lib/MapAPI.class.php';

class testWebService extends WebService
{
  public static function fetch()
  {
    return file_get_contents(dirname(__FILE__).'/fixtures/data/fake_web_service.xml');
  }
}
```

```php
$myMap = new MapAPI();

$t = new lime_test(1, new lime_output_color());

$t->is($myMap->getMapSize(testWebService::fetch()), 100);
```

测试数据可能比字符串或方法调用更复杂。复杂的测试数据通常被称为 fixture。为了代码清晰度，将 fixture 保存在单独的文件中通常更好，特别是如果它们被多个单元测试文件使用。此外，不要忘记 symfony 可以使用 sfYAML::load() 方法轻松地将 YAML 文件转换为数组。这意味着你可以在 YAML 文件中编写测试数据，而不是编写长长的 PHP 数组，如清单 15-8 所示。

### 清单 15-8 - 在单元测试中使用 fixture 文件

```
// In fixtures.yml:
-
  input: '/test'
  output: true
  comment: isPathAbsolute() returns true if path is absolute
-
  input: '\\test'
  output: true
  comment: isPathAbsolute() returns true if path is absolute
-
  input: 'C:\\test'
  output: true
  comment: isPathAbsolute() returns true if path is absolute
-
  input: 'd:/test'
  output: true
  comment: isPathAbsolute() returns true if path is absolute
-
  input: 'test'
  output: false
  comment: isPathAbsolute() returns false if path is relative
-
  input: '../test'
  output: false
  comment: isPathAbsolute() returns false if path is relative
-
  input: '..\\test'
  output: false
  comment: isPathAbsolute() returns false if path is relative
```

```php
// In testTest.php
<?php

include(dirname(__FILE__).'/../bootstrap/unit.php');
require_once sfConfig::get('sf_symfony_lib_dir').'/util/sfToolkit.class.php';
require_once sfConfig::get('sf_symfony_lib_dir').'/yaml/sfYaml.class.php';

$testCases = sfYaml::load(dirname(__FILE__).'/fixtures.yml');

$t = new lime_test(count($testCases), new lime_output_color());
```

```php
// isPathAbsolute()
$t->diag('isPathAbsolute()');
foreach ($testCases as $case)
{
    $t->is(sfToolkit::isPathAbsolute($case['input']),
    $case['output'],$case['comment']);
}
```

## 单元测试 ORM 类

测试 Propel 或 Doctrine 类要复杂一些，因为生成的对象依赖于一长串类级联。此外，你需要为 Propel 提供有效的数据库连接，并且还需要向数据库中填充一些测试数据。

幸运的是，symfony 已经提供了你所需的一切，因此这非常容易：

- 要获得自动加载，你需要初始化一个配置对象
- 要获得数据库连接，你需要初始化 sfDatabaseManager 类
- 要加载一些测试数据，你可以使用 sfPropelData 类

典型的 Propel 测试文件在清单 15-9 中所示。

### 清单 15-9 - 测试 Propel 类

```php
<?php
include dirname(__FILE__).'/../bootstrap/unit.php';

new sfDatabaseManager($configuration);
$loader = new sfPropelData();
$loader->loadData(sfConfig::get('sf_data_dir').'/fixtures');

$t = new lime_test(1, new lime_output_color());

// begin testing your model class
$t->diag('->retrieveByUsername()');
$user = UserPeer::retrieveByUsername('fabien');
$t->is($user->getLastName(), 'Potencier', '->retrieveByUsername() returns the User for the given username');
```

典型的 Doctrine 测试文件在清单 15-10 中所示。

### 清单 15-10 - 测试 Doctrine 类

```php
<?php
include dirname(__FILE__).'/../bootstrap/unit.php';

new sfDatabaseManager($configuration);
Doctrine_Core::loadData(sfConfig::get('sf_data_dir').'/fixtures');

$t = new lime_test(1, new lime_output_color());

// begin testing your model class
$t->diag('->retrieveByUsername()');
$user = Doctrine::getTable('User')->findOneByUsername('fabien');
$t->is($user->getLastName(), 'Potencier', '->findOneByUsername() returns the User for the given username');
```

## 功能测试

功能测试验证你的应用程序的部分功能。它们模拟浏览会话，发出请求，并检查响应中的元素，就像你手动验证一个动作是否按预期工作一样。在功能测试中，你运行与用例相对应的场景。

### 功能测试长什么样？

你可以使用文本浏览器和大量正则表达式断言来运行功能测试，但那将是极大的时间浪费。Symfony 提供了一个特殊对象，称为 sfBrowser，它就像连接到 symfony 应用程序的浏览器，而不需要实际服务器，也不需要 HTTP 传输的延迟。它提供对每个请求的核心对象的访问（请求、会话、上下文和响应对象）。Symfony 还提供了一个专门为功能测试设计的 sfTestFunctional，它接受一个 sfBrowser 对象并添加一些智能断言方法。

功能测试通常从初始化测试浏览器对象开始。该对象向一个动作发出请求，并验证响应中是否存在某些元素。

例如，每次你使用 generate:module 或 propel:generate-module 任务生成模块骨架时，symfony 都会为此模块创建一个简单的功能测试。该测试向模块的默认动作发出请求，并检查响应状态代码、路由系统计算的模块和动作以及响应内容中某个句子的存在。对于 foobar 模块，生成的 foobarActionsTest.php 文件如清单 15-11 所示。

### 清单 15-11 - 新模块的默认功能测试，位于 tests/functional/frontend/foobarActionsTest.php

```php
<?php

include dirname(__FILE__).'/../../../bootstrap/functional.php';

$browser = new sfTestFunctional(new sfBrowser());

$browser->
  get('/foobar/index')->
  with('request')->begin()->
    isParameter('module', 'foobar')->
    isParameter('action', 'index')->
  end()->
  with('response')->begin()->
    isStatusCode(200)->
    checkElement('body', '!/This is a temporary page/')->
  end()
;

```

> 浏览器方法返回一个 sfTestFunctional 对象，因此你可以链式调用方法以提高测试文件的可读性。这被称为对象的流式接口，因为没有任何东西会阻止方法调用的流动。

功能测试可以包含多个请求和更复杂的断言；你将在即将到来的章节中发现所有可能性。




要启动功能测试，请使用 symfony 命令行中的 test:functional 任务，如清单 15-12 所示。此任务需要应用程序名称和测试名称（省略 Test.php 后缀）。

## 清单 15-12 - 从命令行启动单个功能测试

```
Listing 15-13
$ php symfony test:functional frontend foobarActions

# get /comment/index
ok 1 - status code is 200
ok 2 - request parameter module is foobar
ok 3 - request parameter action is index
not ok 4 - response selector body does not match regex /This is a temporary page/
# Looks like you failed 1 tests of 4.
1..4
```

新模块生成的功能测试默认不会通过。这是因为在新建模块中，index 动作会转发到恭喜页面（包含在 symfony 默认模块中），该页面包含句子“This is a temporary page”。只要你不修改 index 动作，该模块的测试就会失败，这保证了你无法使用未完成的模块通过所有测试。

> 在功能测试中，自动加载已激活，因此你无需手动包含文件。

## 使用 sfBrowser 对象进行浏览

浏览器能够发出 GET 和 POST 请求。在这两种情况下，都使用真实 URI 作为参数。清单 15-13 演示了如何编写对 sfBrowser 对象的调用以模拟请求。

## 清单 15-13 - 使用 sfBrowser 对象模拟请求

```
Listing 15-14
include dirname(__FILE__).'/../../bootstrap/functional.php';

// Create a new browser
$b = new sfBrowser();

$b->get('/foobar/show/id/1');       // GET request
$b->post('/foobar/show', array('id' => 1));  // POST request

// The get() and post() methods are shortcuts to the call() method
$b->call('/foobar/show/id/1', 'get');
$b->call('/foobar/show', 'post', array('id' => 1));

// The call() method can simulate requests with any method
$b->call('/foobar/show/id/1', 'head');
$b->call('/foobar/add/id/1', 'put');
$b->call('/foobar/delete/id/1', 'delete');
```

典型的浏览会话不仅包含对特定动作的请求，还包含点击链接和浏览器按钮。如清单 15-14 所示，sfBrowser 对象也能模拟这些操作。

## 清单 15-14 - 使用 sfBrowser 对象模拟导航

```
$b->get('/'); // Request to the home page
$b->get('/foobar/show/id/1');
$b->back(); // Back to one page in history
$b->forward(); // Forward one page in history
$b->reload(); // Reload current page
$b->click('go'); // Look for a 'go' link or button and click
```

浏览器维护一个调用栈，因此 back() 和 forward() 方法的工作方式与真实浏览器相同。

> 浏览器拥有管理会话（sfTestStorage）和 Cookie 的自身机制。

在最需要测试的交互中，与表单相关的交互可能排在第一位。要模拟表单输入和提交，你有三种选择。你可以发送希望发送的参数的 POST 请求，以数组形式作为参数调用 click()，或者逐个填写字段并点击提交按钮。无论如何，它们都会生成相同的 POST 请求。清单 15-15 展示了一个示例。

## 清单 15-15 - 使用 sfBrowser 对象模拟表单输入

```
// Example template in modules/foobar/templates/editSuccess.php
<?php echo form_tag('foobar/update') ?>
<input type="hidden" name="id" value="<?php echo $sf_params->get('id')
?>" />
<input type="text" name="name" value="foo" />
<input type="submit" value="go" />
<textarea name="text1">foo</textarea>
<textarea name="text2">bar</textarea>
</form>
```

```
// Example functional test for this form
$b = new sfBrowser();
$b->get('/foobar/edit/id/1');

// Option 1: POST request
$b->post('/foobar/update', array('id' => 1, 'name' => 'dummy', 'commit' => 'go'));

// Option 2: Click the submit button with parameters
$b->click('go', array('name' => 'dummy'));

// Option 3: Enter the form values field by field name then click the
submit button
$b->setField('name', 'dummy')->
click('go');
```

> 使用第二种和第三种选项时，默认表单值会自动包含在表单提交中，且无需指定表单目标。

当动作通过 redirect() 结束时，浏览器不会自动跟随重定向；你必须使用 followRedirect() 手动跟随，如清单 15-16 所示。

## 清单 15-16 - 浏览器不会自动跟随重定向

```php
// Example action in modules/foobar/actions/actions.class.php
public function executeUpdate($request)
{
  // ...

  $this->redirect('foobar/show?id='. $request->getParameter('id'));
}
```

```php
// Example functional test for this action
$b = new sfBrowser();
$b->get('/foobar/edit?id=1')->
  click('go', array('name' => 'dummy'))->
  followRedirect();   // Manually follow the redirection
```

还有最后一个你应该了解的用于浏览的方法：restart() 重新初始化浏览历史、会话和 Cookie——就像你重新启动了浏览器一样。

在发出第一个请求后，sfBrowser 对象可以访问请求、上下文和响应对象。这意味着你可以检查很多内容，从文本内容到响应头、请求参数和配置：

```php
$request = $b->getRequest();
$context = $b->getContext();
$response = $b->getResponse();
```

## 使用断言

由于 sfBrowser 对象可以访问响应和请求的其他组件，你可以对这些组件进行测试。你可以为此创建一个新的 lime_test 对象，但幸运的是 sfTestFunctional 提供了一个 test() 方法，它返回一个 lime_test 对象，你可以在其中调用之前描述的单元断言方法。查看清单 15-17 了解如何通过 sfTestFunctional 进行断言。

*清单 15-17 - 测试浏览器通过 test() 方法提供测试功能*

```php
$b = new sfTestFunctional(new sfBrowser());
$b->get('/foobar/edit/id/1');
$request = $b->getRequest();
$context = $b->getContext();
$response = $b->getResponse();
```

```php
// Get access to the lime_test methods via the test() method
$b->test()->is($request->getParameter('id'), 1);
$b->test()->is($response->getStatusCode(), 200);
$b->test()->is($response->getHttpHeader('content-type'), 'text/html; charset=utf-8');
$b->test()->like($response->getContent(), '/edit/');
```

> > getResponse()、getContext()、getRequest() 和 test() 方法不返回 sfBrowser 对象，因此你不能在它们之后链式调用其他 sfBrowser 方法。

你可以通过请求和响应对象轻松检查传入和传出的 Cookie，如清单 15-16 所示。

*清单 15-16 - 使用 sfBrowser 测试 Cookie*

```
$b->test()->is($request->getCookie('foo'), 'bar'); // Incoming cookie
$cookies = $response->getCookies();
$b->test()->is($cookies['foo'], 'foo=bar'); // Outgoing cookie
```

使用 test() 方法测试请求元素会导致代码行很长。幸运的是，sfTestFunctional 包含一组代理方法，帮助你保持功能测试的可读性和简洁性——此外，它们本身也会返回一个 sfTestFunctional 对象。

例如，你可以以更快速的方式重写清单 15-15，如清单 15-18 所示。

## 清单 15-18 - 直接使用 sfTestFunctional 进行测试

```
$b = new sfTestFunctional(new sfBrowser());
$b->get('/foobar/edit/id/1')->
with('request')->isParameter('id', 1)->
with('response')->begin()->
isStatusCode()->
isHeader('content-type', 'text/html; charset=utf-8')->
matches('/edit/')->
end();
```

每个代理方法都属于一个测试组。使用测试组需要用 with() 和 end() 方法包裹方法调用。with() 方法接受测试组名称（如 request 和 response）。

状态 200 是 isStatusCode() 期望的参数的默认值，因此你可以不带任何参数调用它来测试成功响应。

代理方法的另一个优势是，你不需要像使用 lime_test 方法那样指定输出文本。消息由代理方法自动生成，测试输出清晰易读。

```
# get /foobar/edit/id/1
ok 1 - request parameter "id" is "1"
ok 2 - status code is "200"
ok 3 - response header "content-type" is "text/html"
ok 4 - response matches "/edit/"
1..4
```

在实践中，清单 15-17 中的代理方法涵盖了大多数常规测试，因此你很少会在 sfTestFunctional 对象上使用 test() 方法。

清单 15-15 显示 sfBrowser 不会自动跟随重定向。这有一个优势：你可以测试重定向。例如，清单 15-19 展示了如何测试清单 15-14 的响应。

## 清单 15-19 - 使用 sfTestFunctional 测试重定向

```
$b = new sfTestFunctional(new sfBrowser());
$b->
get('/foobar/edit/id/1')->
click('go', array('name' => 'dummy'))->
with('request')->begin()->
isParameter('module', 'foobar')->
isParameter('action', 'update')->
end()->
with('response')->begin()->
isStatusCode(200)->
isRedirected() // Check that the response is a redirect
end()->
```


```
followRedirect()-> // Manually follow the redirection
with('request')->begin()->
    isRequestParameter('module', 'foobar')->
    isRequestParameter('action', 'show')->
end()->
with('response')->isStatusCode(200);
```

## 使用 CSS 选择器

许多功能性测试通过检查内容中是否存在文本来验证页面是否正确。借助 matches() 方法中的正则表达式，您可以检查显示的文本、标签的属性或值。但当您想要检查响应 DOM 中深层嵌入的内容时，正则表达式就不太理想了。

这就是 sfTestFunctional 对象支持 getResponseDom() 方法的原因。它返回一个 libXML2 DOM 对象，比纯文本更易于解析和测试。有关使用此方法的示例，请参阅清单 15-20。

## 清单 15-20 - 测试浏览器将响应内容作为 DOM 对象提供

```
Listing 15-20
$b = new sfTestFunctional(new sfBrowser());
$b->get('/foobar/edit/id/1');
$dom = $b->getResponseDom();
$b->test()->is($dom->getElementsByTagName('input')->item(1)->getAttribute('type'), 'text');
```

但是，使用 PHP DOM 方法解析 HTML 文档仍然不够快速和简便。如果您熟悉 CSS 选择器，您就会知道它们是从 HTML 文档中检索元素的更强大方式。Symfony 提供了一个名为 sfDomCssSelector 的工具类，它期望将 DOM 文档作为构造参数。它有一个 getValues() 方法，可根据 CSS 选择器返回字符串数组，还有一个 getElements() 方法，可返回 DOM 元素数组。请参阅清单 15-20 中的示例。

## 清单 15-21 - 测试浏览器将响应内容作为 sfDomCssSelector 对象提供

```
Listing 15-21
$b = new sfTestFunctional(new sfBrowser());
$b->get('/foobar/edit/id/1');
$c = new sfDomCssSelector($b->getResponseDom())
$b->test()->is($c->getValues('form input[type="hidden"][value="1"]'),
    array('');
);
$b->test()->is($c->getValues('form textarea[name="text1"]'), array('foo'));
$b->test()->is($c->getValues('form input[type="submit"]'), array('');
```

在不断追求简洁与清晰的过程中，symfony 为此提供了一个快捷方式：响应测试器组的 checkElement() 代理方法。此方法使清单 15-21 看起来像清单 15-22。

## 清单 15-22 - 测试浏览器通过 CSS 选择器访问响应元素

```
Listing 15-22
$b = new sfTestFunctional(new sfBrowser());
$b->get('/foobar/edit/id/1')->
with('response')->begin()->
    checkElement('form input[type="hidden"][value="1"]', true)->
    checkElement('form textarea[name="text1"]', 'foo')->
    checkElement('form input[type="submit"]', 1)->
end();
```

checkElement() 方法的行为取决于它接收的第二个参数的类型：

- 如果是布尔值，则检查匹配 CSS 选择器的元素是否存在。
- 如果是整数，则检查 CSS 选择器是否返回此数量的结果。
- 如果是正则表达式，则检查 CSS 选择器找到的第一个元素是否与其匹配。
- 如果是以 ! 开头的正则表达式，则检查第一个元素是否不匹配该模式。
- 对于其他情况，它将 CSS 选择器找到的第一个元素与第二个参数作为字符串进行比较。

该方法接受一个可选的第三个参数，形式为关联数组。它允许您不在选择器返回的第一个元素（如果返回多个）上执行测试，而是在某个位置的另一个元素上执行测试，如清单 15-23 所示。

## 清单 15-23 - 使用位置选项匹配特定位置的元素

```
$b = new sfTestFunctional(new sfBrowser());
$b->get('/foobar/edit?id=1')->
with('response')->begin()->
checkElement('form textarea', 'foo')->
checkElement('form textarea', 'bar', array('position' => 1))->
end();
```

选项数组也可以用于同时执行两个测试。您可以测试是否存在匹配选择器的元素以及有多少个，如清单 15-24 所示。

## 清单 15-24 - 使用计数选项计算匹配数量

```
$b = new sfTestFunctional(new sfBrowser());
$b->get('/foobar/edit?id=1')->
with('response')->checkElement('form input', true, array('count' => 3));
```

选择器工具非常强大。它接受大多数 CSS 3 选择器，您可以将其用于复杂查询，如清单 15-25 所示。

## 清单 15-25 - checkElement() 接受的复杂 CSS 选择器示例

```
->checkElement('ul#list li a[href]', 'click me');
->checkElement('ul > li', 'click me');
->checkElement('ul + li', 'click me');
->checkElement('h1, h2', 'click me');
->checkElement('a[class$="foo"][href*="bar.html"]', 'my link');
->checkElement('p:last ul:nth-child(2) li:contains("Some text")');
```

## 测试错误

有时，您的操作或模型会故意抛出异常（例如显示 404 页面）。即使您可以使用 CSS 选择器来检查生成的 HTML 代码中是否存在特定错误消息，但最好还是使用 throwsException 方法来检查是否抛出了异常，如清单 15-26 所示。

## 清单 15-26 - 测试异常

```
$b = new sfTestFunctional(new sfBrowser());
$b->
get('/foobar/edit/id/1')->
click('go', array('name' => 'dummy'))->
throwsException() -> // Checks that the last request
threw an exception
throwsException('RuntimeException') -> // Checks the class of the
exception
throwsException(null, '/error/'); // Checks that the content of the
exception message matches the regular expression
```

## 在测试环境中工作

sfTestFunctional 对象使用设置为测试环境的特殊前置控制器。该环境的默认配置出现在清单 15-27 中。

## 清单 15-27 - 默认测试环境配置，在 frontend/config/settings.yml 中

```
test:
.settings:
error_reporting: <?php echo ((E_ALL | E_STRICT) ^
E_NOTICE)."\n" ?>
cache: false
web_debug: false
no_script_name: false
etag: false
```

在此环境中，缓存和 Web 调试工具栏均设置为 false。但是，代码执行仍会在日志文件中留下痕迹，该日志文件与 dev 和 prod 日志文件不同，因此您可以独立检查它（myproject/log/frontend_test.log）。在此环境中，异常不会停止脚本的执行——因此即使某个测试失败，您也可以运行整个测试集。您可以有特定的数据库连接设置，例如，使用另一个包含测试数据的数据库。

在使用 sfBrowser 对象之前，必须先对其进行初始化。如果需要，您可以为应用程序指定主机名和客户端 IP 地址——也就是说，如果您的应用程序对这两个参数进行控制。清单 15-28 演示了如何执行此操作。

## 清单 15-28 - 使用主机名和 IP 设置浏览器

```
$b = new sfBrowser('myapp.example.com', '123.456.789.123');
```

## test:functional 任务

test:functional 任务可以运行一个或多个功能性测试，具体取决于接收到的参数数量。规则与 test:unit 任务的规则非常相似，只是功能性测试任务始终期望将应用程序作为第一个参数，如清单 15-29 所示。

## 清单 15-29 - 功能性测试任务语法

```
// Test directory structure
test/
functional/
frontend/
myModuleActionsTest.php
myScenarioTest.php
backend/
myOtherScenarioTest.php
## Run all functional tests for one application, recursively
$ php symfony test:functional frontend
## Run one given functional test
$ php symfony test:functional frontend myScenario
## Run several tests based on a pattern
$ php symfony test:functional frontend my*
```

## 测试命名规范

本节列出了一些良好实践，帮助您保持测试井然有序且易于维护。这些技巧涉及文件组织、单元测试和功能性测试。

关于文件结构，您应该使用单元测试所要测试的类的名称来命名单元测试文件，并使用功能性测试所要测试的模块或场景的名称来命名功能性测试文件。示例请参见清单 15-30。如果不遵循这些指南，您的 test/ 目录很快将包含大量文件，长期来看查找测试可能会很困难。

## 清单 15-30 - 文件命名规范示例

```
test/
unit/
myFunctionTest.php
mySecondFunctionTest.php
foo/
barTest.php
functional/
frontend/
myModuleActionsTest.php
myScenarioTest.php
backend/
myOtherScenarioTest.php
```

对于单元测试，良好的做法是按函数或方法对测试进行分组，并以 diag() 调用启动每个测试组。每个单元测试的消息应包含已测试函数或方法的名称，后跟动词和属性，以便测试输出看起来像描述对象属性的句子。清单 15-31 显示了一个示例。

## 清单 15-31 - 单元测试命名规范示例

```
// strtolower()
$t->diag('strtolower()');
$t->isa_ok(strtolower('Foo'), 'string', 'strtolower() returns a string');
$t->is(strtolower('FOO'), 'foo', 'strtolower() transforms the input to lowercase');

# strtolower()
ok 1 - strtolower() returns a string
ok 2 - strtolower() transforms the input to lowercase
```

功能性测试应按页面分组，并以请求开始。清单 15-32 说明了此做法。





## Listing 15-32 - 示例功能测试命名实践

```
$browser->
get('/foobar/index')->
with('request')->begin()->
isParameter('module', 'foobar')->
isParameter('action', 'index')->
end()->
with('response')->begin()->
isStatusCode(200)->
checkElement('body', '/foobar/')->
end()
;
```

```
# get /comment/index
ok 1 - status code is 200
ok 2 - request parameter module is foobar
ok 3 - request parameter action is index
ok 4 - response selector body matches regex /foobar/
```

如果你遵循这一约定，你的测试输出将足够清晰，可用作项目的开发者文档——在某些情况下甚至足以让实际文档变得多余。

## 特殊测试需求

symfony 提供的单元测试和功能测试工具在大多数情况下应已足够。下面列出了一些额外技术，用于解决自动化测试中的常见问题：在隔离环境中启动测试、在测试中访问数据库、测试缓存，以及测试客户端交互。

## 在测试框架中执行测试

test:unit 和 test:functional 任务可以启动单个测试或一组测试。但如果在不带任何参数的情况下调用这些任务，它们将运行 test/ 目录中编写的所有单元测试和功能测试。会涉及一种特殊机制，将每个测试文件隔离在独立的沙箱中，以避免测试之间的污染风险。此外，在这种情况下保持与单个测试文件相同的输出是没有意义的（输出将长达数千行），因此测试结果会被压缩成一个综合视图。这就是为什么执行大量测试文件使用测试框架，即具有特殊功能的自动化测试框架。测试框架依赖于 lime 框架的一个组件，称为 lime_harness。它按文件显示测试状态，并在最后显示通过测试数与总数的概览，如 Listing 15-33 所示。

## Listing 15-33 - 在测试框架中启动所有测试

```
$ php symfony test:all
unit/myFunctionTest.php............ok
unit/mySecondFunctionTest.php......ok
unit/foo/barTest.php.............not ok

Failed Test                                                Stat Total   Fail  List of Failed
------------------------------------------------------------------
unit/foo/barTest.php                                          0     2     2  62 63
Failed 1/3 test scripts, 66.66% okay. 2/53 subtests failed, 96.22% okay.
```

测试执行方式与逐个调用时相同，只是输出被缩短以真正有用。特别是，最终图表关注失败的测试，帮助你定位它们。

你可以使用 test:all 任务一次性启动所有测试，该任务也使用测试框架，如 Listing 15-34 所示。在每次部署到生产环境之前都应该这样做，以确保自最新版本以来未出现回归。

## Listing 15-34 - 启动项目的所有测试

```
$ php symfony test:all
```

## 访问数据库

单元测试通常需要访问数据库。当你首次调用 sfBrowser::get() 时，数据库连接会自动初始化。但是，如果你想在使用 sfBrowser 之前访问数据库，则必须手动初始化 sfDatabaseManager 对象，如 Listing 15-35 所示。

## Listing 15-35 - 在测试中初始化数据库

```
$databaseManager = new sfDatabaseManager($configuration);
$databaseManager->loadConfiguration();

// Optionally, you can retrieve the current database connection
$con = Propel::getConnection();
```

在开始测试前，应该使用固定数据填充数据库。这可以通过 sfPropelData 对象完成。该对象可以从文件加载数据，就像 propel:data-load 任务一样，也可以从数组加载，如 Listing 15-36 所示。

## Listing 15-36 - 从测试文件填充数据库

```
$data = new sfPropelData();

// Loading data from file
$data->loadData(sfConfig::get('sf_data_dir').'/fixtures/test_data.yml');

// Loading data from array
$fixtures = array(
    'Article' => array(
        'article_1' => array(
            'title'   => 'foo title',
            'body'    => 'bar body',
            'created_at' => time(),
        ),
        'article_2'  => array(
            'title'   => 'foo foo title',
            'body'    => 'bar bar body',
            'created_at' => time(),
        ),
    ),
);

$data->loadDataFromArray($fixtures);
```

然后，根据你的测试需求，像在正常应用程序中一样使用 Propel 对象。请记得在单元测试中包含它们的文件（你可以使用 sfSimpleAutoload 类来自动化此过程，如前面本章“桩、固定数据和自动加载”部分的提示中所述）。功能测试中会自动加载 Propel 对象。

## 测试缓存

为应用程序启用缓存时，功能测试应验证缓存的操作是否按预期工作。

首先要做的是为测试环境启用缓存（在 settings.yml 文件中）。然后，如果你想测试页面是来自缓存还是动态生成的，应该使用 view_cache 测试组提供的 isCached() 测试方法。Listing 15-37 演示了此方法。

## Listing 15-37 - 使用 isCached() 方法测试缓存

```
<?php
include dirname(__FILE__).'/../../bootstrap/functional.php';
// Create a new test browser
$b = new sfTestFunctional(new sfBrowser());
$b->get('/mymodule');
$b->with('view_cache')->isCached(true); // Checks that the response comes from the cache
$b->with('view_cache')->isCached(true, true); // Checks that the cached response comes with layout
$b->with('view_cache')->isCached(false); // Checks that the response doesn't come from the cache
```

> 在功能测试开始时不需要清除缓存；引导脚本会为你完成此操作。

## 测试客户端交互

之前描述的技术的主要缺点是它们无法模拟 JavaScript。对于非常复杂的交互，例如 Ajax 交互，你需要能够精确复现用户会进行的鼠标和键盘输入，并在客户端执行脚本。通常，这些测试是手动重现的，但非常耗时且容易出错。

解决方案称为 Selenium52，它是一个完全用 JavaScript 编写的测试框架。它就像普通用户一样，使用当前浏览器窗口在页面上执行一组操作。相对于 sfBrowser 对象，Selenium 的优势在于它能够在页面中执行 JavaScript，因此你可以使用它来测试甚至 Ajax 交互。

Selenium 默认未随 symfony 捆绑。要安装它，需要在 web/ 目录中创建一个新的 selenium/ 目录，并在其中解压 Selenium 存档53 的内容。这是因为 Selenium 依赖 JavaScript，而大多数浏览器中的标准安全设置不会允许它运行，除非它与你的应用程序位于相同的主机和端口上。

> 注意不要将 selenium/ 目录传输到生产服务器，因为任何通过浏览器访问 Web 文档根目录的人都可以访问它。

Selenium 测试用 HTML 编写，并存储在 web/selenium/tests/ 目录中。例如，Listing 15-38 显示了一个功能测试，其中加载主页、单击“click me”链接，并在响应中查找文本“Hello, World”。请记住，为了在测试环境中访问应用程序，你必须指定 frontend_test.php 前置控制器。

## Listing 15-38 - 示例 Selenium 测试，位于 web/selenium/test/testIndex.html

```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<meta content="text/html; charset=UTF-8" http-equiv="content-type">
<title>Index tests</title>
</head>
<body>
<table cellspacing="0">
<tbody>
<tr><td colspan="3">First step</td></tr>
<tr><td>open</td> <td>/frontend_test.php</td>
<td>&nbsp;</td></tr>
<tr><td>clickAndWait</td> <td>link=click me</td>
<td>&nbsp;</td></tr>
<tr><td>assertTextPresent</td> <td>Hello, World!</td>
<td>&nbsp;</td></tr>
</tbody>
</table>
</body>
</html>
```

测试用例由包含三列（命令、目标和值）的表格的 HTML 文档表示。不过，并非所有命令都需要值。在这种情况下，可以留空该列或使用 &nbsp; 使表格看起来更好。有关命令的完整列表，请参阅 Selenium 网站。

你还需要通过在同一目录下的 TestSuite.html 文件的表格中插入新行，将此测试添加到全局测试套件中。Listing 15-39 演示了如何操作。

## Listing 15-39 - 将测试文件添加到测试套件中，位于 web/selenium/test/TestSuite.html

```
...
<tr><td><a href='./testIndex.html'>My First Test</a></td></tr>
...
```

要运行测试，只需浏览至

http://myapp.example.com/selenium/index.html

选择“主测试套件”，单击运行所有测试按钮，然后观察浏览器复现你指示它执行的步骤。

> 由于 Selenium 测试在真实浏览器中运行，它们还允许你测试浏览器不一致性。使用一个浏览器构建测试，然后用单个请求在所有网站预期可用的其他浏览器上进行测试。

由于 Selenium 测试用 HTML 编写，编写 Selenium 测试可能会很麻烦。但得益于 Firefox Selenium 扩展^54，创建测试只需在录制会话中运行一次测试。在录制会话中导航时，你可以


在浏览器窗口中右键单击，并在弹出菜单的“追加 Selenium 命令”下选择相应的检查，以添加断言类型测试。

您可以将测试保存为 HTML 文件，为您的应用程序构建测试套件。Firefox 扩展甚至允许您运行使用它录制的 Selenium 测试。

> 启动 Selenium 测试前，请不要忘记重新初始化测试数据。

## 摘要

自动化测试包括用于验证方法或函数的单元测试以及用于验证功能的功能测试。Symfony 依赖 lime 测试框架进行单元测试，并专门为功能测试提供 sfBrowser 和 sfTestFunctional 类。它们提供许多断言方法，从基础到最先进的（如 CSS 选择器）。使用 symfony 命令行启动测试，可以逐个启动（使用 test:unit 和 test:functional 任务），也可以在测试套件中启动（使用 test:all 任务）。在处理数据时，自动化测试使用测试固定装置（fixtures）和测试桩（stubs），在 symfony 单元测试中很容易实现这一点。

如果您确保编写足够多的单元测试来覆盖应用程序的大部分内容（或许可以使用 TDD 方法论），那么在重构内部代码或添加新功能时，您会更有信心，甚至可能在文档编写任务上节省一些时间。

# 第 16 章

## 应用程序管理工具

在开发和部署阶段，开发人员都需要持续的诊断信息流，以确定应用程序是否按预期运行。这些信息通常通过日志记录和调试实用程序汇总。由于 symfony 等框架在驱动应用程序方面起着核心作用，因此将此类功能紧密集成以确保高效的开发和运维活动至关重要。

在生产服务器上的应用程序生命周期内，应用程序管理员需要重复大量任务，从日志滚动到升级。框架还必须提供工具，尽可能自动化这些任务。

本章将解释 symfony 应用程序管理工具如何满足上述所有需求。

## 日志记录

了解请求执行期间出了什么问题的唯一方法是回顾执行过程的跟踪。幸运的是，正如您将在本节中了解到的，PHP 和 symfony 都倾向于记录大量此类数据。

### PHP 日志

PHP 具有在 php.ini 中定义的 error_reporting 参数，用于指定记录哪些 PHP 事件。Symfony 允许您在 settings.yml 文件中按应用程序和环境覆盖此值，如清单 16-1 所示。

### 清单 16-1 - 设置错误报告级别，位于 frontend/config/settings.yml

```
prod:
  .settings:
    error_reporting: <?php echo (E_PARSE | E_COMPILE_ERROR | E_ERROR |
      E_CORE_ERROR | E_USER_ERROR)."\n" ?>

dev:
  .settings:
    error_reporting: <?php echo (E_ALL | E_STRICT)."\n" ?>
```

为避免生产环境出现性能问题，服务器仅记录关键 PHP 错误。然而，在开发环境中，会记录所有类型的事件，以便开发人员拥有追踪错误所需的所有信息。

PHP 日志文件的位置取决于您的 php.ini 配置。如果您从未定义过此位置，PHP 可能会使用 Web 服务器提供的日志设施（例如 Apache 错误日志）。在这种情况下，您可以在 Web 服务器日志目录下找到 PHP 日志。

### Symfony 日志

除了标准 PHP 日志外，symfony 还可以记录大量自定义事件。您可以在 myproject/log/ 目录下找到所有 symfony 日志。每个应用程序和每个环境都有一个文件。例如，frontend 应用程序的开发环境日志文件名为 frontend_dev.log，生产环境日志文件名为 frontend_prod.log，依此类推。

如果您有运行中的 symfony 应用程序，请查看其日志文件。语法非常简单。对于每个事件，都会向应用程序的日志文件添加一行。每一行都包含事件的精确时间、事件性质、正在处理的对象以及任何其他相关详细信息。清单 16-2 显示了 symfony 日志文件内容的示例。

### 清单 16-2 - symfony 日志文件内容示例，位于 log/frontend_dev.log

```
Nov 15 16:30:25 symfony [info] {sfAction} call
"barActions->executemessages()"
Nov 15 16:30:25 symfony [info] {sfPropelLogger} executeQuery: SELECT
bd_message.ID...
Nov 15 16:30:25 symfony [info] {sfView} set slot "leftbar" (bar/index)
Nov 15 16:30:25 symfony [info] {sfView} set slot "messageblock" (bar/
mes...
Nov 15 16:30:25 symfony [info] {sfView} execute view for template
"messa...
Nov 15 16:30:25 symfony [info] {sfView} render "/home/production/
myproject/...
Nov 15 16:30:25 symfony [info] {sfView} render to client
```

您可以在这些文件中找到许多详细信息，包括发送到数据库的实际 SQL 查询、调用的模板、对象之间的调用链等等。

> 可以通过在 factories.yml 中覆盖 format 和/或 time_format 设置来配置文件日志的格式，如清单 16-3 所示。

### 清单 16-3 - 更改日志格式

```
all:
  logger:
    param:
      sf_file_debug:
        param:
          format:      %time% %type% [%priority%] %message%%EOL%
          time_format: %b %d %H:%M:%S
```

### Symfony 日志级别配置

symfony 日志消息共有八个级别：emerg、alert、crit、err、warning、notice、info 和 debug，与 PEAR::Log 包的级别相同。您可以在每个应用程序的 factories.yml 配置文件中为每个环境配置要记录的最大级别，如清单 16-4 所示。

### 清单 16-4 - 默认日志配置，位于 frontend/config/factories.yml

```
prod:
  logger:
    param:
      level: err
```

默认情况下，在除生产环境外的所有环境中，都会记录所有消息（直到最不重要的级别，即 debug 级别）。在生产环境中，日志记录默认处于禁用状态；如果在 settings.yml 中将 logging_enabled 改为 true，则只有最重要的消息（从 crit 到 emerg）会出现在日志中。

您可以在 factories.yml 文件中为每个环境更改日志记录级别，以限制记录消息的类型。

> 要查看日志记录是否启用，请调用 sfConfig::get('sf_logging_enabled')。

### 添加日志消息

您可以通过使用清单 16-5 中描述的技术之一，从代码中手动向 symfony 日志文件添加消息。

### 清单 16-5 - 添加自定义日志消息

```
// From an action
$this->logMessage($message, $level);

// From a template
<?php use_helper('Debug') ?>

<?php log_message($message, $level) ?>
```

$level 可以采用与日志消息中相同的值。

或者，要从应用程序中的任何位置向日志写入消息，请直接使用 sfLogger 方法，如清单 16-6 所示。可用方法的名称与日志级别相同。

### 清单 16-6 - 从任何位置添加自定义日志消息

```
if (sfConfig::get('sf_logging_enabled'))
{
  sfContext::getInstance()->getLogger()->info($message);
}
```

### 自定义日志记录

Symfony 的日志系统非常简单，但也易于自定义。唯一的前提是日志记录器类必须扩展 sfLogger 类（该类定义了 doLog() 方法）。Symfony 会传递两个参数调用 doLog() 方法：$message（要记录的消息）和 $priority（日志级别）。
myLogger 类使用 PHP 的 error_log 函数定义了一个简单的日志记录器：

```
class myLogger extends sfLogger
{
 protected function doLog($message, $priority)
 {
 error_log(sprintf('%s (%s)', $message,
 sfLogger::getPriorityName($priority)));
 }
}
```

要从现有类创建日志记录器，只需实现 sfLoggerInterface 接口（该接口定义了 log() 方法）。该方法采用与 doLog() 方法相同的两个参数：

```
require_once('Log.php');
require_once('Log/error_log.php');
// Define a thin wrapper to implement the interface
// for the logger we want to use with symfony
class Log_my_error_log extends Log_error_log implements sfLoggerInterface
{
}
```

### 清理和轮转日志文件

请不要忘记定期清理应用程序的 log/ 目录，因为这些文件有个奇怪的习惯，会在几天内增长几个兆字节（当然，这取决于您的流量）。Symfony 为此提供了一个名为 log:clear 的特殊任务，您可以定期手动启动，也可以将其放入 crontab 中。例如，以下命令会擦除 symfony 日志文件：

```
$ php symfony log:clear
```

为了获得更好的性能和安全性，您可能希望将 symfony 日志存储在多个小文件中，而不是一个大文件中。日志文件的理想存储策略是定期备份并清空主日志文件，但仅保留有限数量的备份。您可以启用这样的日志滚动，周期为 7 天，历史记录（备份数量）为 10，如清单 16-7 所示。您将使用一个活动日志文件加上十个备份文件，每个备份文件包含 7 天的历史记录。每当下一个 7 天周期结束时，当前的活动日志文件将转为备份，并删除最旧的备份。

### 清单 16-7 - 启动日志滚动

```
$ php symfony log:rotate frontend prod --period=7 --history=10
```

备份日志文件存储在 logs/history/ 目录中，并以保存日期作为后缀。




## 调试

无论你的编程技巧多么娴熟，最终都会犯错，即使使用 symfony。检测和理解错误是快速应用开发的关键之一。幸运的是，symfony 为开发者提供了多种调试工具。

### Symfony 调试模式

Symfony 具有一种调试模式，有助于简化应用程序的开发和调试。启用后，会发生以下情况：

- 每次请求都会检查配置，因此对任何配置文件的更改都会立即生效，无需清除配置缓存。
- 错误消息以清晰且有用的方式显示完整的堆栈跟踪，以便您可以更高效地找到出错的元素。
- 提供了更多调试工具（例如数据库查询的详细信息）。
- Propel/Doctrine 调试模式也会被激活，因此在调用 Propel/Doctrine 对象时出现的任何错误都将显示通过 Propel/Doctrine 架构的详细调用链。

另一方面，当调试模式关闭时，处理过程如下：

- YAML 配置文件仅被解析一次，然后转换为存储在 `cache/config/` 文件夹中的 PHP 文件。第一次请求之后的每个请求都会忽略 YAML 文件，而改用缓存的配置。因此，请求的处理速度大大加快。
- 如需重新处理配置，必须手动清除配置缓存。
- 请求处理期间发生错误时，将返回代码为 500（Internal Server Error）的响应，不解释问题的内部原因。

调试模式在前端控制器中按应用程序激活。它由传递给 `getApplicationConfiguration()` 方法调用的第三个参数的值控制，如清单 16-8 所示。

*清单 16-8 - 启用调试模式的示例前端控制器，位于 web/frontend_dev.php*

```php
<?php

require_once(dirname(__FILE__).'/../config/ProjectConfiguration.class.php');

$configuration = ProjectConfiguration::getApplicationConfiguration('frontend', 'dev', true);
sfContext::createInstance($configuration)->dispatch();
```

> 在生产服务器上，您不应启用调试模式，也不应保留任何启用了调试模式的前端控制器。调试模式不仅会减慢页面交付速度，还可能泄露应用程序的内部机制。尽管调试工具永远不会泄露数据库连接信息，但异常的堆栈跟踪中包含大量对任何有恶意访问者而言危险的信息。

### Symfony 异常

在调试模式下发生异常时，symfony 会显示一个有用的异常通知，其中包含查找问题原因所需的所有信息。

异常消息编写清晰，并指向问题最可能的原因。它们通常提供修复问题的可能解决方案，对于大多数常见问题，异常页面甚至包含指向 symfony 网站页面的链接，以获取有关异常的更多详细信息。异常页面显示错误发生在 PHP 代码中的位置（带语法高亮显示），并列出完整的方法调用堆栈，如图 16-1 所示。您可以沿着跟踪找到导致问题的第一个调用。传递给方法的参数也会显示。

Symfony 非常依赖 PHP 异常进行错误报告。例如，404 错误可以由 sfError404Exception 触发。

图 16-1 - symfony 应用程序的示例异常消息

![](img/0f886a7f4cbcc3939be96e985ca35ff4_287_0.png)

在开发阶段，symfony 异常在调试应用程序时将非常有用。

### Xdebug 扩展

Xdebug PHP 扩展允许扩展 Web 服务器记录的信息量。Symfony 在其自身的调试反馈中集成了 Xdebug 消息，因此在调试应用程序时激活此扩展是个好主意。扩展安装在很大程度上取决于您的平台；有关详细安装指南，请参阅 Xdebug 网站。

56. http://xdebug.org/

安装 Xdebug 后，需要在 php.ini 文件中手动激活它。对于 *nix 平台，可以通过添加以下行来完成：

```ini
zend_extension="/usr/local/lib/php/extensions/no-debug-non-zts-20041030/xdebug.so"
```

对于 Windows 平台，Xdebug 激活是由以下行触发的：

```ini
extension=php_xdebug.dll
```

清单 16-9 提供了一个 Xdebug 配置示例，也必须添加到 php.ini 文件中。

清单 16-9 - Xdebug 配置示例

```ini
;xdebug.profiler_enable=1
;xdebug.profiler_output_dir="/tmp/xdebug"
xdebug.auto_trace=1          ; enable tracing
xdebug.trace_format=0
;xdebug.show_mem_delta=0     ; memory difference
;xdebug.show_local_vars=1
;xdebug.max_nesting_level=100
```

必须重新启动 Web 服务器才能激活 Xdebug 模式。

> 不要忘记在生产平台上禁用 Xdebug 模式。不这样做会大大减慢每个页面的执行速度。

### Web 调试工具栏

日志文件包含有趣的信息，但不太易读。最基本的任务（即查找针对特定请求记录的行）可能颇为棘手，特别是当多个用户同时使用应用程序且事件历史记录悠久时。这时您就需要一个 Web 调试工具栏了。

该工具栏以半透明盒子的形式叠加在浏览器正常内容上方，位于窗口右上角，如图 16-2 所示。它提供对 symfony 日志事件、当前配置、请求和响应对象的属性、请求发出的数据库查询详细信息以及与请求相关的处理时间图表的访问权限。

图 16-2 - Web 调试工具栏出现在窗口右上角

![](img/0f886a7f4cbcc3939be96e985ca35ff4_288_0.png)

调试工具栏背景的颜色取决于请求期间发出的日志消息的最高级别。如果没有消息超过调试级别，工具栏具有灰色背景。如果单条消息达到 err 级别，工具栏具有红色背景。

不要将调试模式与 Web 调试工具栏混淆。即使调试模式关闭，也可以显示调试工具栏，但在这种情况下，它显示的信息要少得多。

要为应用程序激活 Web 调试工具栏，请打开 settings.yml 文件并查找 web_debug 键。在 prod 和 test 环境中，web_debug 的默认值为 false，因此如果您需要它，必须手动激活。在 dev 环境中，默认配置已将其设置为 true，如清单 16-10 所示。

清单 16-10 - Web 调试工具栏激活，位于 frontend/config/settings.yml

```yaml
dev:
  .settings:
    web_debug: true
```

显示时，Web 调试工具栏提供大量信息/交互：

- 单击 symfony 标志以切换工具栏的可见性。当工具栏缩减时，它不会隐藏页面顶部的元素。
- 单击“config”部分以显示请求、响应、设置、全局变量和 PHP 属性的详细信息，如图 16-3 所示。顶部行总结了重要的配置设置，例如调试模式、缓存以及 PHP 加速器的存在（如果禁用则显示为红色，如果启用则显示为绿色）。

图 16-3 - “config”部分显示请求的所有变量和常量

![](img/0f886a7f4cbcc3939be96e985ca35ff4_289_0.png)

- 启用缓存时，工具栏中会出现一个绿色箭头。单击此箭头可以重新处理页面，无论缓存中存储了什么（但不会清除缓存）。
- 单击“logs”部分以显示当前请求的日志消息，如图 16-4 所示。根据事件的重要性，它们以灰色、黄色或红色行显示。您可以使用列表顶部显示的链接按类别过滤显示的事件。

图 16-4 - “logs”部分显示当前请求的日志消息





![](img/0f886a7f4cbcc3939be96e985ca35ff4_290_0.png)

当当前操作是由重定向产生时，“logs”窗格中仅显示最新请求的日志，因此日志文件对于良好调试仍然必不可少。

- 对于执行 SQL 查询的请求，工具栏中会出现一个数据库图标。单击它以查看查询详细信息，如图 16-5 所示。
- 时钟图标右侧显示处理请求所需的总时间。请注意，Web 调试工具栏和调试模式会减慢请求执行速度，因此请尽量不要单独考虑计时数值，而应关注两个页面执行时间之间的差异。单击时钟图标，按类别查看处理时间的详细信息，如图 16-6 所示。Symfony 显示请求处理特定部分所花费的时间。只有与当前请求相关的时间对优化才有意义，因此 Symfony 核心所花费的时间不会显示。这就是为什么这些时间加起来不等于总时间的原因。
- 单击工具栏右端的红色 X 以隐藏工具栏。

图 16-5 - 数据库查询部分显示当前请求执行的查询

## SQL 查询

- 1. [1.00 ms] SELECT COUNT(ask_question.ID) FROM ask_question, ask_interest WHERE
  ask_interest.CREATED_AT>'2006-11-24 10:47:17' AND ask_interest.QUESTION_ID=ask_question.ID

- 2. [3.53 ms] SELECT ask_question.ID, ask_question.AT, ask_question.USER_ID, ask_question.TITLE,
  ask_question.BODY, ask_question.HTML_BODY, ask_question.INTERESTED_USERS, ask_question.REPORTS,
  ask_question.CREATED_AT, ask_question.UPDATED_AT, ask_user.ID, ask_user.NICKNAME,
  ask_user.FIRST_NAME, ask_user.LAST_NAME, ask_user.EMAIL, ask_user.SHA1_PASSWORD, ask_user.SALT,
  ask_user.IS_ACTIVE, ask_user.IS_ADMIN, ask_user.MODERATOR, ask_user.LAST_LOGIN,
  ask_user.IS_ADMINISTRATOR, ask_user.DELETIONS, ask_user.CREATED_AT AS
  count FROM ask_question, ask_user WHERE ask_question.CREATED_AT>'2006-11-24 10:47:17' AND
  ask_interest.QUESTION_ID=ask_question.ID AND ask_question.USER_ID=ask_user.ID GROUP BY
  ask_question.QUESTION_ID ORDER BY COUNT DESC, ask_question.CREATED_AT DESC LIMIT 10

- 3. [0.49 ms] SELECT ask_answer.ID, ask_answer.QUESTION_ID, ask_answer.USER_ID, ask_answer.BODY,
  ask_answer.HTML_BODY, ask_answer.RELEVANCY_UP, ask_answer.RELEVANCY_DOWN,
  ask_answer.REPORTS, ask_answer.CREATED_AT FROM ask_answer WHERE ask_question.ID=1

- 4. [0.45 ms] SELECT DISTINCT ask_question.TAG_QUESTION_ID, ask_question.TAG_USER_ID,
  ask_question.TAG_CREATED_AT, ask_question.TAG, ask_question.TAG_NORMALIZED_TAG,
  ask_question.TAG_NORMALIZED_TAG FROM ask_question WHERE
  ask_question.TAG_QUESTION_ID=1 GROUP BY ask_question.TAG_NORMALIZED_TAG ORDER BY
  UPPER(ask_question.TAG_NORMALIZED_TAG) ASC

- 5. [0.33 ms] SELECT ask_question.TAG_NORMALIZED_TAG AS tag, COUNT(ask_question.TAG_NORMALIZED_TAG) AS
  count FROM ask_question WHERE ask_question.TAG_QUESTION_ID=1 GROUP BY
  ask_question.TAG_NORMALIZED_TAG ORDER BY COUNT DESC LIMIT 5

- 6. [0.43 ms] SELECT ask_answer.ID, ask_answer.QUESTION_ID, ask_answer.USER_ID, ask_answer.BODY,
  ask_answer.HTML_BODY, ask_answer.RELEVANCY_UP, ask_answer.RELEVANCY_DOWN,
  ask_answer.REPORTS, ask_answer.CREATED_AT FROM ask_answer WHERE ask_question.ID=2

图 16-6 - 时钟图标按类别显示执行时间

## 计时器

| 类型 | 调用次数 | 时间 (ms) |
|---|---|---|
| 配置 | 14 | 60.42 |
| 操作 "question/frontpage" | 1 | 132.43 |
| 数据库 | 9 | 7.56 |
| 视图 "Success" 对 "question/frontpage" | 1 | 243.24 |
| 局部 "question/_question_list" | 1 | 151.49 |
| 局部 "question/_question_block" | 2 | 119.74 |
| 局部 "question/_interested_user" | 2 | 12.99 |
| 局部 "moderator/_question_options" | 2 | 2.80 |
| 组件 "sidebar/default" | 1 | 0.02 |
| 局部 "sidebar_default" | 1 | 25.62 |
| 局部 "tag/_tag_cloud" | 1 | 2.09 |
| 局部 "question/_search" | 1 | 0.97 |
| 局部 "sidebar/_rss_links" | 1 | 3.08 |
| 局部 "sidebar/_moderation" | 1 | 1.32 |
| 局部 "sidebar/_administration" | 1 | 1.85 |

## 添加您自己的计时器

Symfony 使用 sfTimer 类来计算在配置、模型、操作和视图上花费的时间。使用同一个对象，您可以计时自定义进程，并在 Web 调试工具栏中与其他计时器一起显示结果。在进行性能优化工作时，这非常有用。

要初始化特定代码片段的计时，请调用 getTimer() 方法。它将返回一个 sfTimer 对象并开始计时。在此对象上调用 addTime() 方法以停止计时。经过的时间可通过 getElapsedTime() 方法获取，并与其他计时器一起在 Web 调试工具栏中显示。

```
// Initialize the timer and start timing
$timer = sfTimerManager::getTimer('myTimer');

// Do things
...

// Stop the timer and add the elapsed time
$timer->addTime();

// Get the result (and stop the timer if not already stopped)
$elapsedTime = $timer->getElapsedTime();
```

为每个计时器命名的好处是，您可以多次调用它以累加计时。例如，如果 myTimer 计时器用于每个请求被调用两次的实用方法，那么第二次调用 getTimer('myTimer') 方法将从 addTime() 上次调用时计算的点重新开始计时，因此计时将累加到之前的计时上。在计时器对象上调用 getCalls() 将告诉您计时器被启动的次数，这些数据也会在 Web 调试工具栏中显示。

```
// Get the number of calls to the timer
$nbCalls = $timer->getCalls();
```

在 Xdebug 模式下，日志消息要丰富得多。所有 PHP 脚本文件和被调用的函数都会被记录，并且 Symfony 知道如何将这些信息与其内部日志关联起来。日志消息表格中的每一行都有一个双箭头按钮，您可以单击它以查看相关请求的更多详细信息。如果出现问题，Xdebug 模式会提供最大量的详细信息以找出原因。

> 默认情况下，Web 调试工具栏不包含在 Ajax 响应和具有非 HTML 内容类型的文档中。对于其他页面，您可以在操作中通过简单调用 sfConfig::set('sf_web_debug', false) 手动禁用 Web 调试工具栏。

## 手动调试

能够访问框架调试消息固然不错，但能够记录自己的消息则更好。Symfony 提供了可从操作和模板访问的快捷方式，以帮助您在请求执行期间跟踪事件和/或值。

您的自定义日志消息会出现在 Symfony 日志文件以及 Web 调试工具栏中，就像常规事件一样。（清单 16-5 展示了自定义日志消息语法的示例。）例如，自定义消息是从模板中检查变量值的好方法。清单 16-11 展示了如何从模板使用 Web 调试工具栏获取开发者反馈（您也可以从操作中使用 $this->logMessage()）。

## 清单 16-11 - 为了调试目的在日志中插入消息

```
<?php use_helper('Debug') ?>
...
<?php if ($problem): ?>
<?php log_message('{sfAction} been there', 'err') ?>
...
<?php endif ?>
```

使用 err 级别可确保事件在消息列表中清晰可见，如图 16-7 所示。

## 图 16-7 - 自定义日志消息出现在 Web 调试工具栏的“logs”部分中

| # | 类型 | 消息 |
|---|---|---|
| 1 | 上下文 | 初始化 |
| 2 | 控制器 | 初始化 |
| 3 | 路由 | 匹配路由 (default) ?/module/action? |
| 4 | 请求 | 请求参数数组 ( "module" => "article", "action" => "list" ) |
| 5 | 控制器 | 分发请求 |
| 6 | 过滤器 | 执行过滤器 "sfRenderingFilter" |
| 7 | 过滤器 | 执行过滤器 "sfWebDebugFilter" |
| 8 | 过滤器 | 执行过滤器 "sfCommonFilter" |
| 9 | 过滤器 | 执行过滤器 "sfFlashFilter" |
| 10 | 过滤器 | 执行过滤器 "sfExecutionFilter" |
| 11 | 操作 | 调用 "articleActions->executeList()" |
| 12 | Creole | connect( (DSN = array ( "database" => "*****", "encoding" => "*****", "hostspec" => "*****", "password" => "*****", "persistent" => "*****", "phptype" => "*****", "port" => "*****", "username" => "*****" ) ), FLAGS: 0 |
| 13 | Creole | prepareStatement() SELECT blog_article.ID, blog_article.TITLE, blog_article.CONTENT, blog_article.CREATED_AT FROM blog_article |
| 14 | Creole | executeQuery()(0.035 ms) SELECT blog_article.ID, blog_article.TITLE, blog_article.CONTENT, blog_article.CREATED_AT FROM blog_article |
| 15 | 视图 | 为 "article/list" 初始化视图 |
| 16 | 视图 | 渲染 "sf_app_dir/modules/article/templates/listSuccess.php" |
| 17 | 操作 | 到过这里 |
| 18 | 视图 | 使用 "sf_app_dir/templates/layout.php" 装饰内容 |
| 19 | 视图 | 渲染 "sf_app_dir/templates/layout.php" |

## 在 Web 上下文之外使用 Symfony

您可能希望从命令行（或通过 cron 表）执行脚本，并访问所有 Symfony 类和功能，例如启动批量电子邮件作业或通过资源密集型计算定期更新模型。实现此目的的简单方法是创建一个 PHP 脚本，复制前置控制器的初始步骤，以便正确初始化 Symfony。您还可以使用 Symfony 命令行系统，以利用参数解析和自动数据库初始化。

## 批处理文件

初始化 Symfony 只需几行 PHP 代码。您可以通过创建一个 PHP 文件（例如在项目的 lib/ 目录下）来充分利用所有 Symfony 功能，以清单 16-12 所示的行开头。

## 清单 16-12 - 示例批处理脚本，在 lib/myScript.php 中





```php

require_once(dirname(__FILE__).'/../config/ProjectConfiguration.class.php');
$configuration = ProjectConfiguration::getApplicationConfiguration('frontend', 'dev', true);

// Remove the following lines if you don't use the database layer
$databaseManager = new sfDatabaseManager($configuration);

// add code here
```

这强烈看起来像是前端控制器（参见第 6 章）的前几行，因为这些行的作用相同：初始化 symfony，解析项目和应用程序配置。请注意，ProjectConfiguration::getApplicationConfiguration 方法需要三个参数：

- 应用程序名称
- 环境名称
- 布尔值，用于定义是否启用调试功能

要执行你的代码，只需从命令行调用脚本：

```
$ php lib/myScript.php
```

## 自定义任务

使用 symfony 创建自定义命令行脚本的另一种方法是编写 **symfony 任务**。就像 `cache:clear` 和 `propel:build-model` 任务一样，你可以使用 `php symfony` 从命令行启动自己的自定义任务。自定义任务可以解析命令行参数和选项，可以嵌入自己的帮助文本，并且可以扩展现有任务。

自定义任务只是扩展 `sfBaseTask` 并位于 `lib/task/` 目录下的类，可以位于项目根目录下，也可以位于插件目录中。其文件名必须以 `'Task.class.php'` 结尾。清单 16-13 展示了一个示例自定义任务。

清单 16-13 - 示例任务，位于 lib/task/testHelloTask.class.php

```php
<?php

class testHelloTask extends sfBaseTask
{
  protected function configure()
  {
    $this->namespace = 'test';
    $this->name = 'hello';
    $this->briefDescription = 'Says hello';
  }

  protected function execute($arguments = array(), $options = array())
  {
    // your code here
    $this->log('Hello, world!');
  }
}
```

execute 方法中编写的代码可以访问所有 symfony 库，就像之前的批处理脚本一样。区别在于你如何调用自定义任务：

清单 16-22
```bash
$ php symfony test:hello
```

任务名称来自受保护的 namespace 和 name 属性（而不是来自类名，也不是来自文件名）。由于你的任务已集成到 symfony 命令行中，因此当你只输入时，它会出现在任务列表中：

清单 16-23
```bash
$ php symfony
```

与其亲自编写任务骨架，不如使用 symfony generate:task 任务。它会创建一个空任务，并提供大量自定义选项。请务必通过调用以下命令来查看这些选项：

清单 16-24
```bash
$ php symfony help generate:task
```

任务可以接受参数（预定义顺序中的必填参数）和选项（可选且无序的参数）。清单 16-14 展示了一个更完整的任务，充分利用了所有这些功能。

清单 16-14 - 更完整的示例任务，位于 lib/task/mySecondTask.class.php

清单 16-25
```php
class mySecondTask extends sfBaseTask
{
	protected function configure()
	{
		$this->namespace		= 'foo';
		$this->name             = 'mySecondTask';
		$this->briefDescription = 'Does some neat things, with style';
		$this->detailedDescription = <<<EOF
		The [foo:mySecondTask|INFO] task manages the process of achieving things
		for you.
		Call it with:
		[php symfony foo:mySecondTask frontend|INFO]
		You can enable verbose output by using the [verbose|COMMENT] option:
		[php symfony foo:mySecondTask frontend --verbose=on|INFO]
EOF;
		$this->addArgument('application', sfCommandArgument::REQUIRED, 'The
		application name');
		$this->addOption('verbose', null, sfCommandOption::PARAMETER_REQUIRED,
		'Enables verbose output', false);
	}

	protected function execute($arguments = array(), $options = array())
	{
		// add code here
	}
}
```

如果你的任务需要通过 Propel 访问数据库层，则应扩展 sfPropelBaseTask 而不是 sfBaseTask。任务初始化将负责加载额外的 Propel 类。你可以在 execute() 方法中通过以下方式启动数据库连接：
$databaseManager = new sfDatabaseManager($this->configuration);

如果任务配置定义了 application 和 env 参数，则在构建任务配置时会自动考虑它们，因此任务可以使用 databases.yml 中定义的任何数据库连接。默认情况下，通过调用 generate:task 生成的骨架包含此初始化。

有关任务系统功能的更多示例，请查看现有 symfony 任务的源代码。

## 填充数据库

在应用程序开发过程中，开发人员经常面临数据库填充的问题。虽然有些数据库系统有特定的解决方案，但没有任何一种可以直接用于对象关系映射之上。得益于 YAML 和 sfPropelData 对象，symfony 可以自动将文本源中的数据传输到数据库。虽然为数据编写文本文件源可能看起来比使用 CRUD 界面手动输入记录更费时，但从长远来看，它将为你节省时间。你会发现，对于自动存储和填充应用程序的测试数据，这个功能非常有用。

## 固定装置文件语法

Symfony 可以读取遵循非常简单的 YAML 语法的数据文件，前提是它们位于 data/fixtures/ 目录下。固定装置文件按类组织，每个类部分以类名作为标题引入。对于每个类，带有唯一字符串标签的记录由一组字段名: 值 键值对定义。清单 16-15 显示了一个用于数据库填充的数据文件示例。

清单 16-15 - 示例固定装置文件，位于 data/fixtures/import_data.yml

```yaml
Article:
    ## Insert records in the blog_article table
first_post:
    ## First record label
    title:    My first memories
    content: |
        For a long time I used to go to bed early. Sometimes, when I had put
        out my candle, my eyes would close so quickly that I had not even time
        to say "I'm going to sleep".

second_post:
    ## Second record label
    title:    Things got worse
    content: |
        Sometimes he hoped that she would die, painlessly, in some accident,
        she who was out of doors in the streets, crossing busy thoroughfares,
        from morning to night.
```

Symfony 使用 camelCase 转换器将列键转换为 setter 方法（例如 setTitle()、setContent()）。这意味着即使实际表中没有 password 字段，你也可以定义 password 键——只需在 User 对象中定义 setPassword() 方法，即可根据密码填充其他列（例如，密码的哈希版本）。

不需要定义主键列。由于它是自增字段，数据库层知道如何确定它。

同样不需要设置 created_at 列，因为 symfony 知道名为该名称的字段在创建时必须设置为当前系统时间。

### 启动导入

propel:data-load 任务将数据从 YAML 文件导入数据库。连接设置来自 databases.yml 文件，因此运行时需要应用程序名称。可选地，你可以通过添加 --env 选项来指定环境名称（默认为 dev）。

```bash
$ php symfony propel:data-load --env=prod --application=frontend
```

该命令读取 data/fixtures/ 目录下的所有 YAML 固定装置文件，并将记录插入数据库。默认情况下，它会替换现有的数据库内容，但如果添加 --append 选项，则命令不会删除当前数据。

```bash
$ php symfony propel:data-load --append --application=frontend
```

在调用时可以指定另一个固定装置目录。在这种情况下，请添加相对于项目目录的路径。

```bash
$ php symfony propel:data-load --application=frontend data/myfixtures
```

### 使用关联表

你现在知道如何向单个表添加记录，但如何添加带有外键到另一个表的记录呢？由于固定装置数据中不包含主键，你需要一种替代方法来关联记录。

让我们回到第 8 章的示例，其中 blog_article 表与 blog_comment 表相关联，如图 16-8 所示。

图 16-8 - 示例数据库关系模型

![](img/0f886a7f4cbcc3939be96e985ca35ff4_297_0.png)

这时给记录分配的标签就非常有用了。要向 first_post 文章添加 Comment 字段，只需将清单 16-16 中显示的行追加到 import_data.yml 数据文件中即可。

清单 16-16 - 向关联表添加记录，位于 data/fixtures/import_data.yml

```yaml
Comment:
 first_comment:
   article_id:  first_post
   author:      Anonymous
   content:     Your prose is too verbose. Write shorter sentences.
```

propel:data-load 任务将识别你之前在 import_data.yml 中给文章分配的标签，并获取相应 Article 记录的主键来设置 article_id 字段。你甚至看不到记录的 ID；你只需通过标签将它们链接起来——这再简单不过了。

关联记录的唯一约束是，外键中调用的对象必须在文件中更早定义；也就是说，就像你逐个定义它们一样。数据文件是从上到下解析的，记录书写的顺序很重要。




这也适用于多对多关系，其中两个类通过第三个类相关联。例如，一个 `Article` 可以有多个 `Authors`，而一个 `Author` 可以有多个 `Articles`。你通常会使用一个 `ArticleAuthor` 类来实现这一点，它对应一个包含 `article_id` 和 `author_id` 列的 `article_author` 表。清单 16-17 展示了如何编写 fixture 文件来使用此模型定义多对多关系。请注意这里使用的复数表名——这正是触发查找中间类的机制。

清单 16-17 - 向多对多关系关联的表中添加记录，位于 data/fixtures/import_data.yml

```
Author:
  first_author:
    name: John Doe
    article_authors: [first_post, second_post]
```

一个数据文件可以包含多个类的声明。但如果你需要为许多不同的表插入大量数据，你的 fixture 文件可能会变得太长，难以轻松操作。

`propel:data-load` 任务会解析它在 `fixtures/` 目录中找到的所有文件，因此你可以将 YAML fixture 文件拆分成较小的片段。需要牢记的重要一点是，外键会对表的处理顺序施加要求。为了确保它们按正确顺序被解析，请为文件添加序数前缀。

- 100_article_import_data.yml
- 200_comment_import_data.yml
- 300_rating_import_data.yml

> Doctrine 不需要特定的文件名，因为它会自动处理按正确顺序执行 SQL 语句的事项。

## 部署应用程序

Symfony 提供了缩写命令来同步两个版本的网站。这些命令主要用于将网站从开发服务器部署到连接互联网的最终主机。

### 使用 rsync 进行增量文件传输

首次传输时，通过 FTP 发送根项目目录是可行的，但当你需要上传应用程序的更新（只有少数文件发生了更改）时，FTP 并不理想。你要么需要再次传输整个项目，这是浪费时间和带宽的做法，要么前往知道某些文件已更改的目录，只传输修改日期不同的文件。这项工作耗时且容易出错。此外，在传输期间，网站可能会不可用或出现故障。

Symfony 支持的解决方案是通过 SSH 层进行 rsync 同步。Rsync<sup>57</sup> 是一个提供快速增量文件传输的命令行实用程序，并且是开源的。使用增量传输时，只会发送修改过的数据。如果文件未更改，则不会将其发送到主机。如果文件只部分更改，则只会发送差异部分。最大的优势是 rsync 同步只传输少量数据，速度非常快。

Symfony 在 rsync 基础上增加了 SSH 以保护数据传输。越来越多的商业主机支持 SSH 隧道，以在其服务器上保护文件上传，这是避免安全漏洞的良好实践。

Symfony 调用的 SSH 客户端使用 config/properties.ini 文件中的连接设置。清单 16-18 提供了生产服务器的连接设置示例。在进行任何同步之前，请在此文件中写入你自己的生产服务器设置。你还可以定义单个参数设置来提供你自己的 rsync 命令行参数。

清单 16-18 - 服务器同步的连接设置示例，位于 myproject/config/properties.ini

```
name=myproject

[production]
host=myapp.example.com
port=22
user=myuser
dir=/home/myaccount/myproject/
```

> 不要混淆生产服务器（即 project 的 properties.ini 文件中定义的主机服务器）与生产环境（即应用程序配置文件中所引用的生产环境使用的前端控制器和配置）。

通过 SSH 进行 rsync 需要执行多个命令，在应用程序的生命周期中，同步可能会发生很多次。幸运的是，Symfony 只需一个命令即可自动化此过程：

```
$ php symfony project:deploy production
```

此命令以干运行模式启动 rsync 命令；也就是说，它显示哪些文件必须同步，但不会实际执行同步。如果你想执行同步，需要通过添加 --go 选项来明确请求。

```
$ php symfony project:deploy production --go
```

同步后，不要忘记清除生产服务器上的缓存。

> 在将应用程序部署到生产服务器之前，最好先使用 check_configuration.php 检查配置。此实用程序位于 Symfony 的 data/bin 文件夹中。它会将你的环境与 Symfony 要求进行对比检查。你可以从任何位置启动它：

```
$ php /path/to/symfony/data/bin/check_configuration.php
```

尽管你可以从命令行使用此实用程序，但强烈建议通过将其复制到 Web 根目录下从 Web 启动它，因为 PHP 对命令行界面和 Web 可以使用不同的 php.ini 配置文件。

## 你的应用程序准备好了吗？

在将应用程序发布到生产环境之前，你应该确保它已准备好供公众使用。在真正决定部署应用程序之前，请检查以下事项是否已完成：

错误页面应根据你的应用程序的外观和感觉进行自定义。参考第 19 章了解如何自定义错误 500、错误 404 和安全页面，并参考本章中的“管理生产应用程序”部分，了解如何自定义站点不可用时显示的页面。

应从 settings.yml 的 enabled_modules 数组中删除默认模块，以免意外显示 Symfony 页面。

会话处理机制在客户端使用 cookie，此 cookie 默认名为 symfony。在部署应用程序之前，你最好将其重命名，以避免泄露你的应用程序使用 Symfony 的事实。参考第 6 章了解如何在 factories.yml 文件中自定义 cookie 名称。

位于项目 web/ 目录中的 robots.txt 文件默认为空。你应该对其进行自定义，以告知 Web 爬虫和其他 Web 机器人网站的哪些部分可以浏览，哪些应避免。大多数情况下，此文件用于排除某些 URL 空间被索引——例如，资源密集型页面、不需要索引的页面（如错误存档），或机器人可能陷入其中的无限 URL 空间。

现代浏览器在用户首次访问你的应用程序时会请求 favicon.ico 文件，以便在地址栏和书签文件夹中用图标代表应用程序。提供此类文件不仅能使你的应用程序外观和感觉更完整，还能防止大量 404 错误出现在服务器日志中。

## 忽略不相关的文件

如果你将 Symfony 项目与生产主机同步，则有一些文件和目录不应传输：

- 所有版本控制目录（.svn/、CVS/ 等）及其内容仅用于开发和集成。
- 开发环境的前端控制器不得提供给最终用户。通过此前端控制器使用应用程序时可用的调试和日志工具会减慢应用程序速度，并泄露操作的核心变量信息，应将其远离公众。
- 项目的 cache/ 和 log/ 目录在每次同步时不得在主机服务器上删除。这些目录也应被忽略。如果你有 stats/ 目录，最好也以同样的方式处理。
- 用户上传的文件不应传输。Symfony 项目的良好做法之一是将上传文件存储在 web/uploads/ 目录中。这样，你可以通过只指向一个目录来将所有这些文件排除在同步之外。

要从 rsync 同步中排除文件，请打开并编辑 myproject/config/ 目录下的 rsync_exclude.txt 文件。每行可以包含一个文件、一个目录或一个模式。Symfony 的文件结构经过合理组织，旨在最大限度地减少需要手动从同步中排除的文件或目录数量。请参阅清单 16-19 获取示例。

清单 16-19 - rsync 排除设置示例，位于 myproject/config/rsync_exclude.txt




```
# Project files
/cache/*
/log/*
/web/*_dev.php
/web/uploads/*

# SCM files
.arch-params
.bzr
_darcs
.git
.hg
.monotone
.svn
CVS
```

> cache/ 和 log/ 目录不能与开发服务器同步，但它们在生产服务器上至少必须存在。如果 myproject/ 项目树结构中不包含它们，请手动创建。

## 管理生产应用程序

生产服务器中最常用的命令是 cache:clear。每次升级 symfony 或项目（例如，在调用 project:deploy 任务后）以及每次更改生产环境配置时，都必须运行该命令。

```
$ php symfony cache:clear
```

> 如果生产服务器上不可用命令行界面，您仍可通过删除 cache/ 文件夹的内容来手动清除缓存。

您可以暂时禁用应用程序——例如，当您需要升级库或大量数据时。

```
$ php symfony project:disable APPLICATION_NAME ENVIRONMENT_NAME
```

默认情况下，禁用的应用程序显示 sfConfig::get('sf_symfony_lib_dir')/exception/data/unavailable.php 页面，但如果您在项目的 config/ 目录中创建了自己的 unavailable.php 文件，symfony 将改用该文件。

project:enable 任务将重新启用应用程序并清除缓存。

```
$ php symfony project:enable APPLICATION_NAME ENVIRONMENT_NAME
```

> 如果 settings.yml 中未将 check_lock 参数设置为 true，则 project:disable 目前无效。

## 清除缓存时显示不可用页面

如果在 settings.yml 文件中将 check_lock 参数设置为 true，symfony 在清除缓存时会锁定应用程序，并在缓存最终清除之前到达的所有请求重定向到一个说明应用程序暂时不可用的页面。如果缓存很大，清除缓存的延迟可能会超过几毫秒，如果您网站的流量很高，此设置是推荐的。此不可用页面与调用 symfony 禁用任务时显示的页面相同。check_lock 参数默认处于禁用状态，因为它对性能有非常轻微的负面影响。

project:clear-controllers 任务会清除 web/ 目录中所有非生产环境运行的控制器。如果您未在 rsync_exclude.txt 文件中包含开发前置控制器，则此命令可确保后门不会泄露应用程序的内部结构。

```
$ php symfony project:clear-controllers
```

如果使用 SVN 仓库的检出，项目文件和目录的权限可能会被破坏。project:permissions 任务可修复目录权限，例如将 log/ 和 cache/ 的权限更改为 0777（这些目录需要可写，框架才能正确工作）。

```
$ php symfony project:permissions
```

## 摘要

通过结合 PHP 日志和 symfony 日志，您可以轻松监控和调试应用程序。在开发过程中，调试模式、异常和 Web 调试工具栏可帮助您定位问题。您甚至可以在日志文件或工具栏中插入自定义消息，以便更轻松地调试。

命令行界面提供了大量工具，可简化开发和生产阶段中应用程序的管理。其中，数据填充和同步任务等是极大的节省时间的工具。

# 第 17 章
## 扩展 Symfony

最终，您需要修改 symfony 的行为。无论您需要修改某个类的行为方式还是添加自定义功能，这一时刻都将不可避免地到来，因为所有客户端都有特定需求，没有任何框架能够预见。实际上，这种情况如此普遍，以至于 symfony 提供了一种在运行时扩展现有类的机制，而不仅仅是简单的类继承。您甚至可以通过修改 factories 设置来替换核心 symfony 类。一旦构建了扩展，您可以轻松将其打包为插件，以便在其他应用程序或其他 symfony 用户之间重复使用。

## 事件

PHP 不支持多重继承，这意味着一个类不能扩展多个其他类。此外，无法向现有类添加新方法或覆盖现有方法。为了缓解这两个限制并使框架真正可扩展，symfony 引入了一个事件系统，灵感来自 Cocoa 通知中心，并基于 Observer 设计模式⁵⁸。

## 理解事件

在 symfony 某些类的生命周期的不同时刻，它们会“向分发器通知一个事件”。例如，当用户更改其区域设置时，用户对象会通知发生了 change_culture 事件。这就像在项目空间中的一声呼喊，说道：“我正在做这个。你们想怎么做都行。”

当事件触发时，您可以决定做一些特殊的事情。例如，您可以在 change_culture 事件发生时每次将用户区域设置保存到数据库表中。为此，您需要注册一个事件监听器，也就是说，必须声明一个在事件发生时将被调用的函数。清单 17-1 显示了如何在用户的 change_culture 事件上注册监听器。

```
Listing 17-1 - Registering an Event Listener

$dispatcher->connect('user.change_culture', 'changeUserCulture');

function changeUserCulture(sfEvent $event)
{
    $user = $event->getSubject();
    $culture = $event['culture'];
}
```

所有事件和监听器注册都由一个称为 *事件分发器* 的特殊对象管理。该对象可以通过 `ProjectConfiguration` 实例在 symfony 的任何地方使用，并且大多数 symfony 对象都提供 `getEventDispatcher()` 方法来直接访问它。使用分发器的 `connect()` 方法，您可以注册任何 PHP 可调用项（类方法或函数），以便在事件发生时调用。`connect()` 的第一个参数是事件标识符，它是由命名空间和名称组成的字符串。第二个参数是 PHP 可调用项。

从应用程序的任何位置检索事件分发器：

`$dispatcher = ProjectConfiguration::getActive()->getEventDispatcher();`

函数向事件分发器注册后，会一直等待直到事件被触发。事件分发器会记录所有事件监听器，并在事件发生时知道调用哪些监听器。在调用这些方法或函数时，分发器会将一个 `sfEvent` 对象作为参数传递给它们。

事件对象存储有关通知事件的信息。可以通过 `getSubject()` 方法检索事件发送者，并且可以通过将事件对象用作数组来访问事件参数（例如，`$event['culture']` 可用于检索 `sfUser` 在通知 `user.change_culture` 时传递的 *区域设置* 参数）。

总之，事件系统允许您在不使用继承的情况下，在运行时向现有类添加功能或修改其方法。

## 通知事件监听器

就像 symfony 类会通知事件已发生一样，您自己的类可以提供运行时可扩展性并在特定场合通知事件。例如，假设您的应用程序请求多个第三方 Web 服务，并且您编写了一个 `sfRestRequest` 类来封装这些请求的 REST 逻辑。一个好主意是，每次该类发出新请求时触发一个事件。这样将来添加日志记录或缓存功能会更容易。清单 17-2 显示了您需要添加到现有 `fetch()` 方法中的代码，以便它通知事件监听器。

### 清单 17-2 - 通知事件监听器

```
class sfRestRequest
{
    protected $dispatcher = null;

    public function __construct(sfEventDispatcher $dispatcher)
    {
        $this->dispatcher = $dispatcher;
    }

    /**
     * Makes a query to an external web service
     */
    public function fetch($uri, $parameters = array())
    {
        // Notify the dispatcher of the beginning of the fetch process
        $this->dispatcher->notify(new sfEvent($this,
```



```
'rest_request.fetch_prepare', array(
    'uri' => $uri,
    'parameters' => $parameters
)));

// Make the request and store the result in a $result variable
// ...

// Notify the dispatcher of the end of the fetch process
$this->dispatcher->notify(new sfEvent($this,
'rest_request.fetch_success', array(
    'uri' => $uri,
    'parameters' => $parameters,
    'result' => $result
)));

return $result;
}
}
```

事件分派器的 notify() 方法期望一个 sfEvent 对象作为参数；这就是传递给事件监听器的同一个对象。这个对象始终携带对触发器的引用（这就是为什么事件实例在初始化时使用 this）和一个事件标识符。可选地，它接受一个关联数组参数，让监听器可以与触发器的逻辑进行交互。

## 直到监听器处理事件为止通知分派器

使用 notify() 方法，可以确保在要通知的事件上注册的所有监听器都被执行。但是，在某些情况下，你需要允许监听器停止事件并阻止进一步的监听器接收通知。在这种情况下，你应该使用 notifyUntil() 而不是 notify()。分派器将执行所有监听器，直到有一个返回 true，然后停止事件通知。换句话说，notifyUntil() 就像在项目空间中喊叫：“我正在做这件事。如果有人关心，那我就不会再告诉任何其他人了”。清单 17-3 展示了如何将此技术与魔术 __call() 方法结合使用，在运行时向现有类添加方法。

### 清单 17-3 直到监听器返回 true 为止通知事件

```
class sfRestRequest
{
// ...

public function __call($method, $arguments)
{
$event = $this->dispatcher->notifyUntil(new sfEvent($this,
'rest_request.method_not_found', array(
'method' => $method,
'arguments' => $arguments
)));
if (!$event->isProcessed())
{
throw new sfException(sprintf('Call to undefined method %s::%s.',
get_class($this), $method));
}

return $event->getReturnValue();
}
}
}
```

在 `rest_request.method_not_found` 事件上注册的事件监听器可以测试请求的 $method 并决定是否处理它，或者将其传递给下一个事件监听器可调用对象。在清单 17-4 中，你可以看到第三方类如何使用此技巧在运行时向 sfRestRequest 类添加 put() 和 delete() 方法。

### 清单 17-4 - 处理“直到为止”事件类型

```php
class frontendConfiguration extends sfApplicationConfiguration
{
    public function configure()
    {
        // ...

        // Register our listener
        $this->dispatcher->connect('rest_request.method_not_found',
            array('sfRestRequestExtension', 'listenToMethodNotFound'));
    }
}

class sfRestRequestExtension
{
    static public function listenToMethodNotFound(sfEvent $event)
    {
        switch ($event['method'])
        {
            case 'put':
                self::put($event->getSubject(), $event['arguments']);

                return true;
            case 'delete':
                self::delete($event->getSubject(), $event['arguments']);

                return true;
            default:
                return false;
        }
    }

    static protected function put($restRequest, $arguments)
    {
        // Make a put request and store the result in a $result variable
        // ...

        $event->setReturnValue($result);
    }

    static protected function delete($restRequest, $arguments)
    {
        // Make a delete request and store the result in a $result variable
        // ...

        $event->setReturnValue($result);
    }
}
```

在实践中，notifyUntil() 为 PHP 提供了多重继承能力，或者更准确地说是 mixin（从第三方类向现有类添加方法的能力）。现在你可以“注入”新方法到那些无法通过继承来扩展的对象中。并且这发生在运行时。当你使用 symfony 时，不再受限于 PHP 的面向对象能力。

> 由于第一个捕获 notifyUntil() 事件的监听器会阻止进一步的通知，你可能会担心监听器的执行顺序。这个顺序对应监听器注册的顺序——先注册，先执行。在实践中，这种情况很少成为问题。如果你发现两个监听器在特定事件上冲突，也许你的类应该通知多个事件，例如一个在方法执行开始时，另一个在结束时。如果你使用事件向现有类添加新方法，请明智地命名方法，以免其他添加方法的尝试发生冲突。将监听器类名作为前缀附加到方法名是一种好的做法。

## 更改方法的返回值

你大概可以想象，监听器不仅可以使用事件提供的信息，还可以修改它，从而改变触发器的原始逻辑。如果你想允许这种情况，应该使用事件分派器的 filter() 方法，而不是 notify()。此时，所有事件监听器都会带有两个参数被调用：事件对象和要过滤的值。无论监听器是否修改了该值，都必须返回它。清单 17-5 展示了如何使用 filter() 来过滤来自 Web 服务的响应，并转义响应中的特殊字符。

### 清单 17-5 - 通知并处理过滤事件

```
class sfRestRequest
{
    // ...

    /**
     * Make a query to an external web service
     */
    public function fetch($uri, $parameters = array())
    {
        // Make the request and store the result in a $result variable
        // ...

        // Notify of the end of the fetch process
        return $this->dispatcher->filter(new sfEvent($this,
            'rest_request.filter_result', array(
                'uri'    => $uri,
                'parameters' => $parameters,
            )), $result)->getReturnValue();
    }
}

// Add escaping to the web service response
$dispatcher->connect('rest_request.filter_result',
    'rest_htmlspecialchars');

function rest_htmlspecialchars(sfEvent $event, $result)
{
    return htmlspecialchars($result, ENT_QUOTES, 'UTF-8');
}
```

## 内置事件

symfony 的许多类都带有内置事件，允许你在不一定更改类本身的情况下扩展框架。表 17-1 列出了这些事件，以及它们的类型和参数。

### 表 17-1 - Symfony 的事件

| 事件名称（类型） | 触发器 | 参数 |
| :--- | :--- | :--- |
| application.log (notify) | 许多类 | 优先级 |
| application.throw_exception (notifyUntil) | sfException | - |
| autoload.filter_config (filter) | sfAutoloadConfigHandler | - |
| command.log (notify) | sfCommand* 类 | 优先级 |
| command.pre_command (notifyUntil) | sfTask | 参数，选项 |
| command.post_command (notify) | sfTask | - |
| command.filter_options (filter) | sfTask | command_manager |
| configuration.method_not_found (notifyUntil) | sfProjectConfiguration | 方法，参数 |
| component.method_not_found (notifyUntil) | sfComponent | 方法，参数 |
| context.load_factories (notify) | sfContext | - |
| context.method_not_found (notifyUntil) | sfContext | 方法，参数 |
| controller.change_action (notify) | sfController | 模块，动作 |
| controller.method_not_found (notifyUntil) | sfController | 方法，参数 |
| controller.page_not_found (notify) | sfController | 模块，动作 |
| debug.web.load_panels (notify) | sfWebDebug | - |
| debug.web.view.filter_parameter_html (filter) | sfWebDebugPanelView | 参数 |
| doctrine.configure (notify) | sfDoctrinePluginConfiguration | - |
| doctrine.filter_model_builder_options (filter) | sfDoctrinePluginConfiguration | - |
| doctrine.filter_cli_config (filter) | sfDoctrinePluginConfiguration | - |
| doctrine.configure_connection (notify) | Doctrine_Manager | 连接，数据库 |
| doctrine.admin.delete_object (notify) | - | 对象 |
| doctrine.admin.save_object (notify) | - | 对象 |
| doctrine.admin.build_query (filter) | - | |
| doctrine.admin.pre_execute (notify) | - | 配置 |
| form.post_configure (notify) | sfFormSymfony | - |
| form.filter_values (filter) | sfFormSymfony | - |
| form.validation_error (notify) | sfFormSymfony | 错误 |
| form.method_not_found (notifyUntil) | sfFormSymfony | 方法，参数 |
| mailer.configure (notify) | sfMailer | - |





| Event name (Type) | Notifiers | Arguments |
|---|---|---|
| plugin.pre_install (notify) | sfPluginManager | channel, plugin, is_package |
| plugin.post_install (notify) | sfPluginManager | channel, plugin |
| plugin.pre_uninstall (notify) | sfPluginManager | channel, plugin |
| plugin.post_uninstall (notify) | sfPluginManager | channel, plugin |
| propel.configure (notify) | sfPropelPluginConfiguration | - |
| propel.filter_phing_args (filter) | sfPropelBaseTask | - |
| propel.filter_connection_config (filter) | sfPropelDatabase | name, database |
| propel.admin.delete_object (notify) | - | object |
| propel.admin.save_object (notify) | - | object |
| propel.admin.build_criteria (filter) | - | - |
| propel.admin.pre_execute (notify) | - | configuration |
| request.filter_parameters (filter) | sfWebRequest | path_info |
| request.method_not_found (notifyUntil) | sfRequest | method, arguments |
| response.method_not_found (notifyUntil) | sfResponse | method, arguments |
| response.filter_content (filter) | sfResponse, sfException | - |
| routing.load_configuration (notify) | sfRouting | - |
| task.cache.clear (notifyUntil) | sfCacheClearTask | app, type, env |
| task.test.filter_test_files (filter) | sfTestBaseTask | arguments, options |
| template.filter_parameters (filter) | sfViewParameterHolder | - |
| user.change_culture (notify) | sfUser | culture |
| user.method_not_found (notifyUntil) | sfUser | method, arguments |
| user.change_authentication (notify) | sfBasicSecurityUser | authenticated |
| view.configure_format (notify) | sfView | format, response, request |
| view.method_not_found (notifyUntil) | sfView | method, arguments |
| view.cache.filter_content (filter) | sfViewCacheManager | response, uri, new |

你可以在这些事件上自由注册事件监听器。只需确保在注册到 notifyUntil 事件类型时，监听器回调返回布尔值，而在注册到 filter 事件类型时，它们返回过滤后的值。

注意，事件命名空间不一定与类角色匹配。例如，所有 symfony 类在需要将内容输出到日志文件（以及网页调试工具栏）时都会通知 application.log 事件：

```
$dispatcher->notify(new sfEvent($this, 'application.log', array($message)));
```

你自己的类也可以这样做，并在合适的时候通知 symfony 事件。

## 在哪里注册监听器？

事件监听器需要在 symfony 请求生命周期早期注册。实际上，注册事件监听器的正确位置是在应用程序配置类中。该类持有对事件分发器的引用，你可以在 configure() 方法中使用它。清单 17-6 展示了如何在上述示例中的 rest_request 事件之一上注册监听器。

清单 17-6 - 在应用程序配置类中注册监听器，位于 apps/frontend/config/ApplicationConfiguration.class.php

```
class frontendConfiguration extends sfApplicationConfiguration
{
    public function configure()
    {
        // ...

        $this->dispatcher->connect('rest_request.method_not_found',
        array('sfRestRequestExtension', 'listenToMethodNotFound'));
    }
}
```

插件（见下文）可以注册自己的事件监听器。它们应该在插件的 config/config.php 脚本中执行此操作，该脚本在应用程序初始化期间运行，并通过 $this->dispatcher 提供对事件分发器的访问。

## 工厂类

工厂是特定任务的类定义。Symfony 为控制器和会话等核心功能依赖工厂。例如，当框架需要创建新的请求对象时，它会在工厂定义中查找要用于此目的的类名。请求的默认工厂定义是 sfWebRequest，因此 symfony 创建此类的对象来处理请求。使用工厂定义的巨大优势是，修改框架的核心功能非常容易：只需更改工厂定义，symfony 就会使用你的自定义请求类，而不是其自己的类。

工厂定义存储在 factories.yml 配置文件中。清单 17-7 显示了默认工厂定义文件。每个定义由一个自动加载类的名称和（可选）一组参数组成。例如，会话存储工厂（在 storage: 键下设置）使用 session_name 参数来命名在客户端计算机上创建的 cookie，以允许持久会话。

清单 17-7 - 默认工厂文件，位于 frontend/config/factories.yml

```
- prod:
    logger:
      class: sfNoLogger
      param:
        level: err
        loggers: ~

test:
  storage:
    class: sfSessionTestStorage
    param:
      session_path: %SF_TEST_CACHE_DIR%/sessions

response:
  class: sfWebResponse
  param:
    send_http_headers: false

mailer:
  param:
    delivery_strategy: none

dev:
  mailer:
    param:
      delivery_strategy: none

all:
  routing:
    class: sfPatternRouting
    param:
      generate_shortest_url:    true
      extra_parameters_as_query_string: true

view_cache_manager:
  class: sfViewCacheManager
  param:
    cache_key_use_vary_headers: true
    cache_key_use_host_name:    true
```

更改工厂的最佳方法是创建一个继承自默认工厂的新类并向其添加新方法。例如，用户会话工厂被设置为 myUser 类（位于 frontend/lib/），它继承自 sfUser。使用相同的机制来利用现有的工厂。清单 17-8 展示了请求对象的新工厂示例。

### 清单 17-8 - 覆盖工厂

```
// Create a myRequest.class.php in an autoloaded directory,
// For instance in frontend/lib/
<?php

class myRequest extends sfRequest
{
  // Your code here
}

// Declare this class as the request factory in factories.yml
all:
  request:
    class: myRequest
```

## 插件

你可能需要复用为某个 symfony 应用程序开发的代码片段。如果可以将这段代码打包为一个单一的类，那没问题：将该类放入另一个应用程序的某个 lib/ 文件夹中，自动加载器会处理其余事宜。但如果代码分布在多个文件中（例如管理生成器的全新主题，或用于自动实现喜欢的视觉效果的 JavaScript 文件和助手组合），仅仅复制文件并非最佳方案。

插件提供了一种方式，用于打包分布在多个文件中的代码，并在多个项目中复用此代码。在插件中，你可以打包类、过滤器、事件监听器、助手、配置、任务、模块、架构和模型扩展、测试数据、Web 资源等。插件易于安装、升级和卸载。它们可以作为 .tgz 存档、PEAR 包或代码仓库的简单检出来分发。PEAR 打包的插件具有管理依赖项、更易于升级和自动发现的优势。Symfony 的加载机制会考虑插件，插件提供的功能在项目中可用，就好像插件代码是框架的一部分一样。

总而言之，插件是 symfony 项目的打包扩展。借助插件，你不仅可以跨应用复用自己的代码，还可以复用其他贡献者开发的功能，并向 symfony 核心添加第三方扩展。

### 查找 Symfony 插件

Symfony 项目网站包含一个专门针对 Symfony 插件的部分，可通过以下网址访问：

http://www.symfony-project.org/plugins/

列出的每个插件都有自己的页面，包含详细的安装说明和文档。

这些插件中有些来自社区贡献，有些来自核心 Symfony 开发人员。在后者中，你将找到以下插件：

- sfFeed2Plugin：自动处理 RSS 和 Atom 提要
- sfThumbnailPlugin：创建缩略图，例如用于上传的图像
- sfMediaLibraryPlugin：允许上传和管理媒体，包括针对富文本编辑器的扩展，以便在富文本中插入图像
- sfGuardPlugin：在 Symfony 标准安全功能之上提供身份验证、授权和其他用户管理功能
- sfSuperCachePlugin：在 Web 根目录下的缓存目录中写入页面，以便 Web 服务器尽可能快速地提供它们
- sfErrorLoggerPlugin：在数据库中记录每个 404 和 500 错误，并提供一个管理模块来浏览这些错误
- sfSslRequirementPlugin：为操作提供 SSL 加密支持

你应该定期查看 Symfony 插件部分，因为新插件不断被添加，它们为 Web 应用程序编程的许多方面提供了非常有用的快捷方式。

除了 Symfony 插件部分外，分发插件的其他方式还包括提供下载插件存档、在 PEAR 频道中托管，或将其存储在公共版本控制仓库中。

### 安装插件

插件安装过程因打包方式而异。请始终参考随附的 README 文件和/或插件下载页面上的安装说明。

插件按项目基础进行安装。以下各部分中描述的所有方法都会将插件的所有文件放入 myproject/plugins/ pluginName/ 目录中。





## PEAR 插件

symfony 插件部分列出的插件可以打包为 PEAR 包，并通过官方 symfony 插件 PEAR 频道提供：plugins.symfony-project.org。要安装此类插件，请使用带有插件名称的 plugin:install 任务，如清单 17-9 所示。

### 清单 17-9 - 从官方 symfony 插件 PEAR 频道安装插件

```
$ cd myproject
$ php symfony plugin:install pluginName
```

或者，您可以下载插件并从磁盘安装。在这种情况下，使用包存档的路径，如清单 17-10 所示。

### 清单 17-10 - 从下载的 PEAR 包安装插件

```
$ cd myproject
$ php symfony plugin:install /home/path/to/downloads/pluginName.tgz
```

有些插件托管在外部 PEAR 频道上。使用 plugin:install 任务安装它们，不要忘记注册频道并提及频道名称，如清单 17-11 所示。

### 清单 17-11 - 从 PEAR 频道安装插件

```
$ cd myproject
$ php symfony plugin:add-channel channel.symfony.pear.example.com
$ php symfony plugin:install --channel=channel.symfony.pear.example.com
pluginName
```

这三种安装类型都使用 PEAR 包，因此术语“PEAR 插件”将不加区分地用于指代从 symfony 插件 PEAR 频道、外部 PEAR 频道或下载的 PEAR 包安装的插件。

plugin:install 任务还接受一些选项，如清单 17-12 所示。

### 清单 17-12 - 带选项安装插件

```
$ php symfony plugin:install --stability=beta pluginName
$ php symfony plugin:install --release=1.0.3 pluginName
$ php symfony plugin:install --install-deps pluginName
```

> 与所有 symfony 任务一样，您可以通过运行 php symfony help plugin:install 来获取 plugin:install 选项和参数的完整说明。

## 存档插件

有些插件以简单的文件存档形式提供。要安装这些插件，只需将存档解压到项目的 plugins/ 目录中即可。如果插件包含 web/ 子目录，不要忘记运行 plugin:publish-assets 命令，在主 web/ 文件夹下创建相应的符号链接，如清单 17-13 所示。最后，不要忘记清除缓存。

### 清单 17-13 - 从存档安装插件

```
$ cd plugins
$ tar -zxpf myPlugin.tgz
$ cd ..
$ php symfony plugin:publish-assets
$ php symfony cc
```

## 从版本控制仓库安装插件

插件有时有自己的源代码仓库用于版本控制。您可以在 plugins/ 目录中进行简单的检出来安装它们，但如果您的项目本身也在版本控制下，这可能会出现问题。

或者，您可以将插件声明为外部依赖项，以便每次更新项目源代码时也会更新插件源代码。例如，Subversion 将外部依赖项存储在 svn:externals 属性中。因此，您可以编辑此属性并在随后更新源代码来添加插件，如清单 17-14 所示。

### 清单 17-14 - 从源代码版本仓库安装插件

```
$ cd myproject
$ svn propedit svn:externals plugins
pluginName  http://svn.example.com/pluginName/trunk
$ svn up
$ php symfony plugin:publish-assets
$ php symfony cc
```

> 如果插件包含 web/ 目录，则必须运行 symfony plugin:publish-assets 命令，以在项目主 web/ 文件夹下生成相应的符号链接。

## 激活插件模块

有些插件包含整个模块。插件模块与经典模块的唯一区别在于，插件模块不会出现在 myproject/apps/frontend/modules/ 目录中（以便于升级）。它们还需要在 settings.yml 文件中激活，如清单 17-15 所示。

### 清单 17-15 - 激活插件模块，在 frontend/config/settings.yml 中

```
all:
  .settings:
    enabled_modules: [default, sfMyPluginModule]
```

这是为了避免插件模块被错误地提供给不需要它的应用程序，从而可能导致安全漏洞。考虑一个提供前端和后端模块的插件。您只需要在前端应用程序中启用前端模块，仅在后端应用程序中启用后端模块。这就是插件模块默认不被激活的原因。

> 默认模块是默认启用的唯一模块。它其实不是插件模块，因为它位于框架中，在 sfConfig::get('sf_symfony_lib_dir')/controller/default/。这是提供祝贺页面以及 404 和凭据所需错误的默认错误页面的模块。如果您不想使用 symfony 默认页面，只需从 enabled_modules 设置中删除此模块即可。

## 列出已安装的插件

只需查看项目的 plugins/ 目录就能知道安装了哪些插件，而 plugin:list 任务会告诉您更多：每个已安装插件的版本号和频道名称（参见清单 17-16）。

### 清单 17-16 - 列出已安装的插件

```
$ cd myproject
$ php symfony plugin:list

Installed plugins:
sfPrototypePlugin 1.0.0-stable # plugins.symfony-project.com
(symfony)
sfSuperCachePlugin 1.0.0-stable # plugins.symfony-project.com
(symfony)
sfThumbnail 1.1.0-stable # plugins.symfony-project.com
(symfony)
```

## 升级和卸载插件

要卸载 PEAR 插件，请从项目根目录调用 plugin:uninstall 任务，如清单 17-17 所示。如果插件的安装频道不同于默认 symfony 频道，则必须在插件名称前加上其安装频道（使用 plugin:list 任务来确定此频道）。

### 清单 17-17 - 卸载插件

```
$ cd myproject
$ php symfony plugin:uninstall sfSuperCachePlugin
$ php symfony cc
```

要卸载存档插件或 SVN 插件，请手动从项目 plugins/ 和 web/ 目录中删除插件文件，并清除缓存。

要升级插件，可以使用 plugin:upgrade 任务（适用于 PEAR 插件）或执行 svn update（如果您从版本控制仓库获取了插件）。存档插件不容易升级。

## 插件结构

插件使用 PHP 语言编写。如果您能理解应用程序的组织方式，就能理解插件的结构。

## 插件文件结构

插件目录大致与项目目录的组织方式相似。插件文件必须放在正确的目录中，以便在需要时能被 symfony 自动加载。请查看清单 17-18 中的插件文件结构说明。

### 清单 17-18 - 插件的文件结构

```
pluginName/
config/
routing.yml // Routing config file
app.yml // Plugin default settings
*schema.yml // Data schema
*schema.xml
config.php // Specific plug-in configuration
data/
generator/
sfPropelAdmin
*/ // Administration generator themes
template/
skeleton/
fixtures/
*.yml // Fixtures files
lib/
  *.php        // Classes
  helper/
  *.php        // Helpers
  model/
  *.php        // Model classes
  task/
  *Task.class.php   // CLI tasks
  modules/
  */           // Modules
    actions/
    actions.class.php
    config/
    module.yml
    view.yml
    security.yml
    templates/
    *.php
  web/
  *           // Assets
```

## 插件功能

插件可以包含很多内容。它们的内容会在运行时以及通过命令行调用任务时，被您的应用程序自动考虑。但是，为了让插件正常工作，您必须遵守一些约定：

- 数据库架构由 propel- 任务检测。当您在项目中调用 propel:build --classes 或 doctrine:build --classes 时，您会重建项目模型和所有插件模型。请注意，Propel 插件架构必须始终带有 plugins.pluginName.lib.model 形式的 package 属性，如清单 17-19 所示。如果您使用 Doctrine，任务将自动在插件目录中生成类。

### 清单 17-19 - 插件中 Propel 架构声明示例，在 myPlugin/config/schema.yml 中

```
propel:
  _attributes:  { package: plugins.myPlugin.lib.model }
  my_plugin_foobar:
    _attributes:    { phpName: myPluginFoobar }
    id:
    name:         { type: varchar, size: 255, index: unique }
    ...
```

- 插件配置应包含在插件配置类（PluginNameConfiguration.class.php）中。此文件在应用程序和项目配置之后执行，因此 symfony 此时已引导完成。您可以使用此文件，例如，通过事件监听器和行为扩展现有类。

- 位于插件 data/fixtures/ 目录中的固件文件由 propel:data-load 或 doctrine:data-load 任务处理。

- 自定义类就像您放在项目 lib/ 文件夹中的类一样自动加载。

- 当您在模板中调用 use_helper() 时，助手会自动被找到。它们必须位于插件的某个 lib/ 目录的 helper/ 子目录中。





- 如果使用 Propel，myplugin/lib/model/ 中的模型类将特化由 Propel 构建器生成的模型类（位于 myplugin/lib/model/om/ 和 myplugin/lib/model/map/ 中）。它们当然是自动加载的。请注意，你不能在自己的项目目录中覆盖插件生成的模型类。

- 如果使用 Doctrine，ORM 会在 myplugin/lib/model/Plugin*.class.php 中生成插件基类，在 lib/model/myplugin/ 中生成具体类。这意味着你可以轻松地在应用程序中覆盖模型类。

- 插件安装后，任务即可在 symfony 命令行中使用。插件可以添加新任务，也可以覆盖现有任务。最佳实践是使用插件名称作为任务的命名空间。键入 php symfony 以查看可用任务列表，包括插件添加的任务。

- 模块提供可从外部访问的新操作，前提是你在应用程序的 enabled_modules 设置中声明它们。

- Web 资源（图片、脚本、样式表等）将提供给服务器。通过命令行安装插件时，如果系统允许，symfony 会创建指向项目 web/ 目录的符号链接，或者将模块 web/ 目录的内容复制到项目目录中。如果插件是从存档或版本控制仓库安装的，则必须手动复制插件 web/ 目录（如插件随附的 README 中所述）。

### 在插件中注册路由规则

插件可以向路由系统添加新规则，但不建议使用自定义 routing.yml 配置文件来实现。这是因为规则定义的顺序非常重要，symfony 中 YAML 文件的简单级联配置系统会打乱此顺序。相反，插件需要在 routing.load_configuration 事件上注册事件监听器，并在监听器中手动预置规则：

```
// in plugins/myPlugin/config/config.php
$this->dispatcher->connect('routing.load_configuration',
array('myPluginRouting', 'listenToRoutingLoadConfigurationEvent'));

// in plugins/myPlugin/lib/myPluginRouting.php
class myPluginRouting
{
    static public function listenToRoutingLoadConfigurationEvent(sfEvent $event)
    {
        $routing = $event->getSubject();
        // add plug-in routing rules on top of the existing ones
        $routing->prependRoute('my_route', new sfRoute('/my_plugin/:action',
        array('module' => 'myPluginAdministrationInterface')));
    }
}
```

**提示：** 在 config/app.yml 中定义默认设置 插件的默认设置可以在其 config/app.yml 文件中定义。但是，覆盖另一个插件中定义的设置是不安全的，因为最终值将取决于 app.yml 文件的加载顺序。插件代码中可以使用自定义应用程序配置（例如，通过使用 sfConfig::get('app_myplugin_foo)），并且设置可以在应用程序级别覆盖（有关示例，请参阅清单 17-20）。默认值的处理可以通过使用 sfConfig::get() 方法的第二个参数来完成，也可以在插件 app.yml 文件中定义。

## 手动设置插件

有些元素 plugin:install 任务无法自行处理，安装过程中需要手动设置：

- 自定义路由应通过插件代码在 routing.load_configuration 事件上添加，或手动添加到应用程序 routing.yml。
- 自定义过滤器必须手动添加到应用程序 filters.yml。
- 自定义工厂必须手动添加到应用程序 factories.yml。

具有此类手动设置的插件应嵌入一个详细描述安装过程的 README 文件。

## 为应用程序自定义插件

每当你想要自定义插件时，切勿修改 plugins/ 目录中的代码。如果这样做，升级插件时将丢失所有修改。为了满足自定义需求，插件提供自定义设置，并支持覆盖。

设计良好的插件使用可以在应用程序 app.yml 中更改的设置，如清单 17-20 所示。

### 清单 17-20 - 自定义使用应用程序配置的插件

```
// example plug-in code
$foo = sfConfig::get('app_my_plugin_foo', 'bar');

// Change the 'foo' default value ('bar') in the application app.yml
all:
  my_plugin:
    foo:   barbar
```

模块设置及其默认值通常在插件的 README 文件中描述。

你可以通过在自己的应用程序中创建同名模块来替换插件模块的默认内容。这不算真正的覆盖，因为你的应用程序中的元素将用于替代插件中的元素。如果你创建与插件同名的模板和配置文件，这将正常工作。

另一方面，如果插件想要提供一个可覆盖其操作的模块，则插件模块中的 actions.class.php 必须为空并继承自一个自动加载类，以便该类的方法也可以被应用程序模块的 actions.class.php 继承。有关示例，请参见清单 17-21。

### 清单 17-21 - 自定义插件操作

```
// In myPlugin/modules/mymodule/lib/myPlugininmyModuleActions.class.php
class myPlugininmyModuleActions extends sfActions
{
  public function executeIndex()
  {
    // Some code there
  }
}

// In myPlugin/modules/mymodule/actions/actions.class.php

require_once dirname(__FILE__).'/../lib/myPlugininmyModuleActions.class.php';

class mymoduleActions extends myPlugininmyModuleActions
{
}

// Nothing
}

// In frontend/modules/mymodule/actions/actions.class.php
class mymoduleActions extends myPluginInMyModuleActions
{
    public function executeIndex()
    {
        // Override the plug-in code there
    }
}
```

## 自定义插件架构

### Doctrine

构建模型时，Doctrine 会在应用程序和插件的 config/ 目录中查找所有 *schema.yml 文件，因此项目架构可以覆盖插件架构。合并过程允许添加或修改表或列。例如，以下示例展示如何为插件架构中定义的表添加列：

```
#Original schema, in plugins/myPlugin/config/schema.yml
Article:
  columns:
    name: string(50)

#Project schema, in config/schema.yml
Article:
  columns:
    stripped_title: string(50)

# Resulting schema, merged internally and used for model and sql generation
Article:
  columns:
    name: string(50)
    stripped_title: string(50)
```

### Propel

构建模型时，symfony 将为每个现有架构（包括插件架构）查找自定义 YAML 文件，遵循以下规则：

| 原始架构名称 | 自定义架构名称 |
| --- | --- |
| config/schema.yml | schema.custom.yml |
| config/foobar_schema.yml | foobar_schema.custom.yml |
| plugins/myPlugin/config/schema.yml | myPlugin-schema.custom.yml |
| plugins/myPlugin/config/foo_schema.yml | myPlugin_foo-schema.custom.yml |

自定义架构将在应用程序和插件的 config/ 目录中查找，因此一个插件可以覆盖另一个插件的架构，并且每个架构可以有多个自定义。

Symfony 随后将基于每个表的 phpName 合并两个架构。合并过程允许添加或修改表、列和列属性。例如，下一个清单展示了自定义架构如何为插件架构中定义的表添加列：

```
# Original schema, in plugins/myPlugin/config/schema.yml
propel:
  article:
    _attributes:    { phpName: Article }
    title:          varchar(50)
    user_id:        { type: integer }
    created_at:

propel:
article:
  __attributes: { phpName: Article, package: foo.bar.lib.model }
  stripped_title: varchar(50)

# Resulting schema, merged internally and used for model and sql
generation
propel:
article:
  __attributes: { phpName: Article, package: foo.bar.lib.model }
  title: varchar(50)
  user_id: { type: integer }
  created_at:
  stripped_title: varchar(50)
```

由于合并过程使用表的 phpName 作为键，你甚至可以更改数据库中插件表的名称，前提是在架构中保持相同的 phpName。

## 如何编写插件

只有打包为 PEAR 包的插件才能使用 plugin:install 任务安装。请记住，此类插件可以通过 symfony 插件部分、PEAR 频道或简单文件下载分发。因此，如果你要编写插件，最好将其作为 PEAR 包发布，而不是作为简单存档。此外，PEAR 打包的插件更容易升级，可以声明依赖项，并自动在 web/ 目录中部署资源。

## 文件组织

假设你已经开发了一个新功能并希望将其打包为插件。第一步是以逻辑方式组织文件，以便 symfony 加载机制在需要时可以找到它们。为此，你必须遵循清单 17-18 中给出的结构。清单 17-22 显示了 sfSamplePlugin 插件的文件结构示例。

### 清单 17-22 - 作为插件打包的文件列表示例

```
sfSamplePlugin/
README
LICENSE
config/
  schema.yml
  sfSamplePluginConfiguration.class.php
data/
  fixtures/
    fixtures.yml
lib/
  model/
    sfSampleFooBar.php
    sfSampleFooBarPeer.php
  task/
    sfSampleTask.class.php
  validator/
    sfSampleValidator.class.php
modules/
  sfSampleModule/
    actions/
```




actions.class.php
config/
security.yml
lib/
BasesfSampleModuleActions.class.php
templates/
indexSuccess.php
web/
css/
sfSampleStyle.css
images/
sfSampleImage.png

编写时，插件目录（清单 17-22 中的 sfSamplePlugin/）的位置并不重要。它可以位于磁盘上的任何位置。

> 请参考现有插件的示例，在初次尝试创建插件时，尽量复现其命名约定和文件结构。

## 创建 package.xml 文件

插件编写的下一步是在插件目录的根目录下添加 package.xml 文件。package.xml 遵循 PEAR 语法。请查看清单 17-23 中典型的 symfony 插件 package.xml 示例。

## 清单 17-23 - Symfony 插件的 package.xml 示例

```
<?xml version="1.0" encoding="UTF-8"?>
<package packagerversion="1.4.6" version="2.0" xmlns="http://pear.php.net/dtd/package-2.0" xmlns:tasks="http://pear.php.net/dtd/tasks-1.0"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://pear.php.net/dtd/tasks-1.0 http://pear.php.net/dtd/tasks-1.0.xsd http://pear.php.net/dtd/package-2.0.xsd">
<name>sfSamplePlugin</name>
<channel>plugins.symfony-project.org</channel>
<summary>symfony sample plugin</summary>
<description>Just a sample plugin to illustrate PEAR packaging</description>
<lead>
<name>Fabien POTENCIER</name>
<user>fabpot</user>
<email>fabien.potencier@symfony-project.com</email>
<active>yes</active>
</lead>
<date>2006-01-18</date>
<time>15:54:35</time>
<version>
<release>1.0.0</release>
<api>1.0.0</api>
</version>
<stability>
<release>stable</release>
<api>stable</api>
</stability>
<license uri="http://www.symfony-project.org/license">MIT license</license>
<notes>-</notes>
<contents>
<dir name="/" />
<file role="data" name="README" />
<file role="data" name="LICENSE" />
<dir name="config">
<!-- model -->
<file role="data" name="schema.yml" />
<file role="data" name="ProjectConfiguration.class.php" />
</dir>
<dir name="data">
<dir name="fixtures">
<!-- fixtures -->
<file role="data" name="fixtures.yml" />
</dir>
</dir>
<dir name="lib">
<dir name="model">
<!-- model classes -->
<file role="data" name="sfSampleFooBar.php" />
<file role="data" name="sfSampleFooBarPeer.php" />
</dir>
<dir name="task">
<!-- tasks -->
<file role="data" name="sfSampleTask.class.php" />
</dir>
<dir name="validator">
<!-- validators -->
<file role="data" name="sfSampleValidator.class.php" />
</dir>
</dir>
<dir name="modules">
<dir name="sfSampleModule">
<file role="data" name="actions/actions.class.php" />
<file role="data" name="config/security.yml" />
<file role="data" name="lib/BasesfSampleModuleActions.class.php" />
<file role="data" name="templates/indexSuccess.php" />
</dir>
</dir>
<dir name="web">
<dir name="css">
<!-- stylesheets -->
<file role="data" name="sfSampleStyle.css" />
</dir>
<dir name="images">
<!-- images -->
<file role="data" name="sfSampleImage.png" />
</dir>
</dir>
</dir>
</contents>
<dependencies>
<required>
<php>
<min>5.2.4</min>
</php>
<pearinstaller>
<min>1.4.1</min>
</pearinstaller>
<package>
<name>symfony</name>
<channel>pear.symfony-project.com</channel>
<min>1.3.0</min>
<max>1.5.0</max>
<exclude>1.5.0</exclude>
</package>
</required>
</dependencies>
<phprelease />
<changelog />
</package>
```

此处的重点是接下来将要描述的 `<contents>` 和 `<dependencies>` 标签。其余标签与 symfony 无特定关系，有关 package.xml 格式的更多详细信息，请参阅 PEAR 在线手册。

## 内容

`<contents>` 标签是你必须描述插件文件结构的位置。这将告诉 PEAR 要复制哪些文件以及复制到哪里。请使用 `<dir>` 和 `<file>` 标签描述文件结构。所有 `<file>` 标签都必须带有 role="data" 属性。清单 17-23 中的 `<contents>` 部分描述了清单 17-22 中的确切目录结构。

> 使用 `<dir>` 标签并非强制性的，因为你可以在 `<file>` 标签中使用相对路径作为 name 值。但是，建议这样做，以便 package.xml 文件保持可读性。

## 插件依赖项

插件旨在与特定版本的 PHP、PEAR、symfony、PEAR 包或其他插件配合使用。在 `<dependencies>` 标签中声明这些依赖项，可指示 PEAR 检查所需包是否已安装，如果未安装，则引发异常。

你应始终声明对 PHP、PEAR 和 symfony 的依赖项，至少要声明与你自己的安装对应的版本，作为最低要求。如果不知道要填什么，请添加 PHP 5.2.4、PEAR 1.4 和 symfony 1.3 的要求。

此外，还建议为每个插件添加 symfony 的最大版本号。这样，在尝试与更高级版本的框架一起使用插件时，会出现错误消息，并迫使插件作者在再次发布之前确保插件与该版本正确协同工作。与插件静默失败相比，收到警报并下载升级更好。

如果将插件指定为依赖项，用户将能够使用单个命令安装你的插件及其所有依赖项：

```
$ php symfony plugin:install --install-deps sfSamplePlugin
```

## 构建插件

PEAR 组件有一个命令（pear package），用于创建包的 .tgz 归档文件，前提是你从包含 package.xml 的目录中调用清单 17-24 所示的命令。

## 清单 17-24 - 将插件打包为 PEAR 包

```
$ cd sfSamplePlugin
$ pear package

Package sfSamplePlugin-1.0.0.tgz done
```

构建插件后，请按照清单 17-25 所示自行安装，以检查其是否正常工作。

## 清单 17-25 - 安装插件

```
$ cp sfSamplePlugin-1.0.0.tgz /home/production/myproject/
$ cd /home/production/myproject/
$ php symfony plugin:install sfSamplePlugin-1.0.0.tgz
```

根据 `<contents>` 标签中的描述，打包后的文件将最终位于项目的不同目录中。清单 17-26 显示了 sfSamplePlugin 的文件安装后应位于的位置。

## 清单 17-26 - 插件文件安装到 plugins/ 和 web/ 目录

```
plugins/
sfSamplePlugin/
README
LICENSE
config/
schema.yml
sfSamplePluginConfiguration.class.php
data/
fixtures/
fixtures.yml
lib/
model/
sfSampleFooBar.php
sfSampleFooBarPeer.php
task/
sfSampleTask.class.php
validator/
sfSampleValidator.class.php
modules/
sfSampleModule/
actions/
actions.class.php
config/
security.yml
lib/
BasesfSampleModuleActions.class.php
templates/
indexSuccess.php
web/
sfSamplePlugin/    ## Copy or symlink, depending on system
css/
sfSampleStyle.css
images/
sfSampleImage.png
```

在应用程序中测试插件的行为。如果工作正常，你就可以将其分发到各个项目中，或者贡献给 symfony 社区。

## 在 Symfony 项目网站上托管你的插件

当 symfony 插件通过 symfony-project.org 网站分发时，可获得最广泛的受众。即使是你自己的插件，也可以通过这种方式分发，前提是你遵循以下步骤：

- 1. 确保 README 文件描述了安装和使用插件的方法，并且 LICENSE 文件提供了许可证详细信息。使用 Markdown 格式语法对 README 进行格式化。
- 2. 创建 symfony 帐户 (http://www.symfony-project.org/user/new) 并创建插件 (http://www.symfony-project.org/plugins/new)。
- 3. 通过调用 pear package 命令为你的插件创建 PEAR 包，并对其进行测试。PEAR 包必须命名为 sfSamplePlugin-1.0.0.tgz（1.0.0 是插件版本）。
- 4. 上传你的 PEAR 包 (sfSamplePlugin-1.0.0.tgz)。
- 5. 你的插件现在必须出现在插件列表中。

如果你遵循此过程，用户只需在项目目录中键入以下命令即可安装你的插件：

```
$ php symfony plugin:install sfSamplePlugin
```

## 命名约定

为保持 plugins/ 目录的整洁，请确保所有插件名称都采用 camelCase 并以 Plugin 结尾（例如，shoppingCartPlugin、feedPlugin 等）。在为插件命名之前，请检查是否不存在同名的现有插件。

> > 依赖 Propel 的插件名称中应包含 Propel（如果你使用 Doctrine，情况亦然）。例如，使用 Propel 数据访问对象的身份验证插件应命名为 sfPropelAuth。

插件应始终包含描述使用条件和所选许可证的 LICENSE 文件。建议你还添加 README 文件，以说明版本更改、插件用途、其作用、安装和配置说明等。

## 总结

symfony 类会发出事件通知，从而使它们能够在应用程序级别进行修改。事件机制允许在运行时进行多重继承和类覆盖，即使 PHP 的限制禁止这样做也是如此。因此，你可以轻松扩展 symfony 功能，即使为此必须修改核心类——工厂配置正是为此而设。

许多此类扩展已经存在；它们被打包为插件，以便通过 symfony 命令行轻松安装、升级和卸载。创建插件就像创建 PEAR 包一样简单，并提供了跨应用程序的可重用性。

symfony 插件部分包含许多插件，你甚至可以添加自己的插件。因此，既然你已经知道如何操作，我们希望你能用大量有用的扩展来增强 symfony 核心！




# 第 18 章 性能

如果您预期网站会吸引大量访客，那么在开发阶段，性能和优化问题应是主要考虑因素。请放心，性能一直是 symfony 核心开发者的首要关注点。

虽然加速开发过程带来的好处会产生一些开销，但 symfony 核心开发者始终意识到性能要求。因此，每个类和每个方法都经过了仔细检查和优化，以尽可能快地运行。基本开销（可以通过比较使用 symfony 和不使用 symfony 时显示“hello, world”消息所需的时间来衡量）非常小。因此，该框架具有可扩展性，并且对压力测试反应良好。作为最终证明，一些流量极高的网站（即拥有数百万活跃用户和大量会给服务器带来压力的 Ajax 交互的网站）使用 symfony，并对其性能非常满意。

当然，高流量网站通常有能力根据需要扩展服务器场和升级硬件。如果您没有资源这样做，或者想确保框架的全部功能始终可用，可以使用一些调整来进一步加速 symfony 应用程序。本章列出了框架各个层面推荐的性能优化，大多面向高级用户。其中一些在前面章节中已提及，但将它们汇总在一起会很有用。

## 调整服务器

一个优化良好的应用程序应该依赖于一个优化良好的服务器。您应该了解服务器性能的基础知识，以确保 symfony 外部没有瓶颈。以下是一些检查事项，以确保您的服务器没有不必要的缓慢。

在 `php.ini` 中将 `magic_quotes_gpc` 设置为 `true` 会减慢应用程序速度，因为它会要求 PHP 转义请求参数中的所有引号，但 symfony 之后会系统地取消转义它们，唯一后果是时间浪费——以及某些平台上的引号转义问题。因此，如果您可以访问 PHP 配置，请关闭此设置。

使用的 PHP 版本越新越好（PHP 5.3 比 PHP 5.2 快）。因此，请确保升级 PHP 版本以获取最新的性能改进。

62. http://sf.to.org/answers
63. http://sf.to.org/delicious
64. http://sf.to.org/dailymotion

对于生产服务器来说，使用 PHP 加速器（例如 APC、XCache 或 eAccelerator）几乎是必不可少的，因为它可以使 PHP 平均运行速度提高 50%，且没有任何权衡。请确保安装其中一个加速器扩展，以感受 PHP 的真实速度。

另一方面，请确保在生产服务器上禁用任何调试实用程序，例如 Xdebug 或 APD 扩展。

您可能会好奇 mod_rewrite 扩展造成的开销：它可以忽略不计。当然，使用重写规则加载图像比不使用重写规则加载图像要慢，但减速的程度比执行任何 PHP 语句要低几个数量级。

当一台服务器不够用时，您仍然可以添加另一台并使用负载均衡。只要 uploads/ 目录是共享的并且您使用数据库存储会话，symfony 项目在负载均衡架构中将能够无缝运行。

## 调整模型

在 symfony 中，模型层以是最慢的部分而闻名。如果基准测试显示您需要优化此层，以下是一些可能的改进。

## 优化 Propel 或 Doctrine 集成

初始化模型层（核心 ORM 类）需要一些时间，因为需要加载一些类并构建各种对象。然而，由于 symfony 集成这两个 ORM 的方式，这些初始化任务仅在操作实际需要模型时发生——并且尽可能晚。只有当生成的模型对象被自动加载时，ORM 类才会被初始化。这意味着不使用模型的页面不会受到模型层的惩罚。

如果您的整个应用程序不需要使用模型层，还可以通过在 settings.yml 中关闭整个层来保存 sfDatabaseManager 的初始化：

```
all:
  .settings:
    use_database: false
```

## Propel 增强功能

生成的模型类（在 lib/model/om/ 中）已经过优化——它们不包含注释，并且受益于自动加载系统。依赖自动加载而不是手动包含文件意味着只有在真正需要时才会加载类。因此，如果不需要某个模型类，自动加载类将节省执行时间，而使用 include 语句的替代方法则不会。至于注释，它们记录生成方法的用法，但会增加模型文件的长度——在慢速磁盘上会造成轻微开销。由于生成的方法名称非常明确，注释默认是关闭的。

这两个增强功能是 symfony 特有的，但您可以通过更改 propel.ini 文件中的两个设置来恢复 Propel 默认值，如下所示：

```
propel.builder.addIncludes = true     # Add include statements in generated classes
                                      # Instead of relying on the
autoloading system
propel.builder.addComments = true  # Add comments to generated classes
```

## 限制要水合的对象数量

当您使用 Peer 类的方法来检索对象时，您的查询会经过水合过程（即根据查询结果的行创建并填充对象）。例如，要使用 Propel 检索 article 表的所有行，您通常执行以下操作：

```
$articles = ArticlePeer::doSelect(new Criteria());
```

The resulting $articles 变量是 Article 类对象的数组。每个对象都必须被创建和初始化，这需要时间。这有一个主要后果：与直接数据库查询相反，Propel 查询的速度与它返回的结果数量成正比。这意味着您的模型方法应优化为仅返回特定数量的结果。当您不需要 Criteria 返回的所有结果时，应使用 `setLimit()` 和 `setOffset()` 方法进行限制。例如，如果您只需要特定查询的第 10 到 20 行，请按清单 18-1 的方式优化 Criteria。

*清单 18-1 - 限制 Criteria 返回的结果数量*

```
$c = new Criteria();
$c->setOffset(10); // Offset of the first record returned
$c->setLimit(10); // Number of records returned
$articles = ArticlePeer::doSelect($c);
```

可以使用分页器来实现自动化。sfPropelPager 对象会自动处理 Propel 查询的偏移量和限制，以仅水合给定页面所需的对象。

## 使用连接减少查询数量

在应用程序开发期间，您应该留意每个请求发出的数据库查询数量。Web 调试工具栏显示每个页面的查询数量，单击小数据库图标会显示这些查询的 SQL 代码。如果您看到查询数量异常上升，是时候考虑使用连接了。

在解释连接方法之前，让我们回顾一下在遍历对象数组并使用 Propel getter 方法检索相关类详细信息时会发生什么，如清单 18-2 所示。此示例假设您的架构描述了一个 article 表，其中包含指向 author 表的外键。

*清单 18-2 - 在循环中检索相关类的详细信息*

```
// In the action, with Propel
$this->articles = ArticlePeer::doSelect(new Criteria());
// Or with Doctrine
$this->articles = Doctrine::getTable('Article')->findAll();

// Database query issued by doSelect()
SELECT article.id, article.title, article.author_id, ...
FROM article

// In the template
<ul>
<?php foreach ($articles as $article): ?>
<li><?php echo $article->getTitle() ?>,



```
written by <?php echo $article->getAuthor()->getName() ?>
<?php endforeach; ?>
</ul>
```

如果 $articles 数组包含十个对象，getAuthor() 方法将被调用十次，每次调用时都会执行一个数据库查询，以实例化一个 Author 类的对象，如清单 18-3 所示。

### Listing 18-3 - 外键 getter 触发单个数据库查询

```
// In the template
$article->getAuthor()

// Database query issued by getAuthor()
SELECT author.id, author.name, ...
FROM author
WHERE author.id = ?    // ? is article.author_id
```

因此，清单 18-2 的页面总共需要 11 个查询：构建 Article 对象数组所需的 1 个查询，加上逐个构建 Author 对象所需的 10 个查询。仅为了显示文章列表及其作者就需要这么多查询。

## 如何使用 Propel 优化查询

如果你使用的是原生 SQL，你会知道如何通过在同一查询中检索 article 表和 author 表的列，将查询数量减少到只有一个。ArticlePeer 类的 doSelectJoinAuthor() 方法正是如此。它发出的查询比简单的 doSelect() 调用稍微复杂一些，但结果集中的额外列允许 Propel 同时实例化 Article 对象和相关的 Author 对象。清单 18-4 显示的结果与清单 18-2 完全相同，但它只需要一个数据库查询，而不是 11 个，因此速度更快。

### Listing 18-4 - 在同一查询中检索文章及其作者的详细信息

```
// In the action
$this->articles = ArticlePeer::doSelectJoinAuthor(new Criteria());

// Database query issued by doSelectJoinAuthor()
SELECT article.id, article.title, article.author_id, ...
FROM article, author
WHERE article.author_id = author.id

// In the template (unchanged)
<ul>
<?php foreach ($articles as $article): ?>
  <li><?php echo $article->getTitle() ?>,
  written by <?php echo $article->getAuthor()->getName() ?></li>
<?php endforeach; ?></ul>
```

doSelect() 调用和 doSelectJoinXXX() 方法返回的结果没有区别；它们都返回相同的对象数组（示例中为 Article 类）。区别在于之后对这些对象使用外键 getter 时。在 doSelect() 的情况下，它会发出一个查询，并用结果实例化一个对象；在 doSelectJoinXXX() 的情况下，关联对象已经存在，不需要查询，过程快得多。因此，如果你知道以后需要关联对象，请调用 doSelectJoinXXX() 方法来减少数据库查询的数量——从而提高页面性能。

当你调用 propel-build-model 时，由于 article 表和 author 表之间的关系，doSelectJoinAuthor() 方法会自动生成。如果 article 表结构中还有其他外键——例如指向 category 表的外键——生成的 BaseArticlePeer 类将具有其他 Join 方法，如清单 18-5 所示。

### Listing 18-5 - ArticlePeer 类可用 doSelect 方法示例

```
Listing 18-8 // Retrieve Article objects
doSelect()

// Retrieve Article objects and hydrate related Author objects
doSelectJoinAuthor()

// Retrieve Article objects and hydrate related Category objects
doSelectJoinCategory()

// Retrieve Article objects and hydrate related objects except Author
doSelectJoinAllExceptAuthor()

// Synonym of
doSelectJoinAll()
```

Peer 类还包含 doCount() 的 Join 方法。具有 i18n 对应类的类（参见第 13 章）提供 doSelectWithI18n() 方法，其行为与 Join 方法相同，但针对 i18n 对象。要发现模型类中可用的 Join 方法，你应该检查 lib/model/om/ 中生成的 Peer 类。如果你找不到查询所需的 Join 方法（例如，多对多关系没有自动生成的 Join 方法），你可以自己构建并扩展你的模型。

> 当然，doSelectJoinXXX() 调用比 doSelect() 调用稍慢，因此只有在之后使用实例化对象时，才能提高整体性能。

## 使用 Doctrine 优化查询

Doctrine 自带一种称为 DQL（Doctrine Query Language）的查询语言。其语法与 SQL 非常相似，但允许检索对象而不是结果集行。在 SQL 中，你希望在同一查询中返回 article 和 author 表的列。使用 DQL 时，解决方案相当简单，只需在原始查询中添加一个 join 语句，Doctrine 就会相应地实例化你的对象实例。以下代码展示了如何在两个表之间进行 join 操作：

```
Listing 18-9 // in the action
Doctrine::getTable('Article')
->createQuery('a')
->innerJoin('a.Author') // "a.Author" refers to the relation named
"Author"
->execute();

// In the template (unchanged)
<ul>
<?php foreach ($articles as $article): ?>
<li><?php echo $article->getTitle() ?>,
written by <?php echo $article->getAuthor()->getName() ?></li>
```

## 避免使用临时数组

使用 Propel 时，对象已经实例化，因此无需为模板准备临时数组。不熟悉 ORM 的开发人员通常会掉进这个陷阱。他们想要准备一个字符串或整数数组，而模板可以直接依赖现有的对象数组。例如，假设模板显示数据库中所有文章标题的列表。不使用 OOP 的开发人员可能会编写与清单 18-6 所示类似的代码。

### Listing 18-6 - 如果已经有一个数组，在操作中准备数组是无用的

```
// In the action
$articles = ArticlePeer::doSelect(new Criteria());
$titles = array();
foreach ($articles as $article)
{
    $titles[] = $article->getTitle();
}
$this->titles = $titles;

// In the template
<ul>
<?php foreach ($titles as $title): ?>
<li><?php echo $title ?></li>
<?php endforeach; ?>
</ul>
```

这段代码的问题在于，doSelect() 调用（耗时）已经完成了实例化，使得 $titles 数组变得多余，因为你可以编写与清单 18-7 相同的代码。因此，构建 $titles 数组所花费的时间可以节省下来，以提高应用程序性能。

### Listing 18-7 - 使用对象数组可免除创建临时数组

```
// In the action
$this->articles = ArticlePeer::doSelect(new Criteria());
// With Doctrine
$this->articles = Doctrine::getTable('Article')->findAll();

// In the template
<ul>
<?php foreach ($articles as $article): ?>
<li><?php echo $article->getTitle() ?></li>
<?php endforeach; ?>
</ul>
```

如果你觉得确实需要准备临时数组，因为对对象进行某些处理是必要的，那么正确的做是在模型类中创建一个直接返回该数组的新方法。例如，如果你需要一个包含文章标题和每篇文章评论数量的数组，操作和模板应如清单 18-8 所示。

### Listing 18-8 - 使用自定义方法准备临时数组

```
// In the action
$this->articles = ArticlePeer::getArticleTitlesWithNbComments();
```

```
// In the template
<ul>
<?php foreach ($articles as $article): ?>
<li><?php echo $article['title'] ?> (<?php echo $article['nb_comments'] ?>
comments)</li>
<?php endforeach; ?>
</ul>
```

由你自己在模型中构建一个快速处理的 getArticleTitlesWithNbComments() 方法——例如，通过绕过整个对象关系映射和数据库抽象层。

## 绕过 ORM

当你不真正需要对象，而只需要从各种表中获取少数几列（如前一个示例所示）时，你可以在模型中创建完全绕过 ORM 层的特定方法。例如，你可以直接使用 PDO 调用数据库，并返回一个自定义构建的数组。清单 18-9 说明了这一想法。

### Listing 18-9 - 在 lib/model/ArticlePeer.php 中使用直接 PDO 访问优化模型方法

```
// With Propel
class ArticlePeer extends BaseArticlePeer
{
public static function getArticleTitlesWithNbComments()
{
$connection = Propel::getConnection();
$query = 'SELECT %s as title, COUNT(%s) AS nb_comments FROM %s LEFT
JOIN %s ON %s = %s GROUP BY %s';
$query = sprintf($query,
ArticlePeer::TITLE, CommentPeer::TABLE_NAME,
ArticlePeer::TABLE_NAME, CommentPeer::ARTICLE_ID,
ArticlePeer::ID, CommentPeer::ARTICLE_ID,
ArticlePeer::ID
);

$statement = $connection->prepare($query);
$statement->execute();

$results = array();
while ($resultset = $statement->fetch(PDO::FETCH_OBJ))
{
$results[] = array('title' => $resultset->title, 'nb_comments' =>
$resultset->nb_comments);
}

return $results;
}
}
```

```
// With Doctrine
class ArticleTable extends Doctrine_Table
{
public function getArticleTitlesWithNbComments()
{
return $this->createQuery('a')
```





->select('a.title, count(*) as nb_comments')
->leftJoin('a.Comments')
->groupBy('a.id')
->fetchArray();
}
}

当你开始构建此类方法时，可能最终会为每个操作编写一个自定义方法，从而失去层分离的好处——更不用说你还会失去数据库独立性。

## 加速数据库

无论你是否使用 symfony，都有许多特定于数据库的优化技术可供应用。本节简要概述了最常见的数据库优化策略，但要充分发挥模型层的性能，需要具备良好的数据库引擎和管理知识。

> 请记住，web 调试工具栏显示页面中每个查询所耗费的时间，并且应该监控每一次调整，以判断其是否真正提升了性能。

表查询通常基于非主键列。为了提高此类查询的速度，你应该在数据库架构中定义索引。要添加单列索引，请向列定义中添加 index: true 属性，如清单 18-10 所示。

清单 18-10 - 在 config/schema.yml 中添加单列索引

```
# Propel schema
propel:
  article:
    id:
    author_id:
    title: { type: varchar(100), index: true }

# Doctrine schema
Article:
  columns:
    author_id: integer
    title: string(100)
  indexes:
    title:
      fields: [title]
```

你可以使用替代的 index: unique 语法来定义唯一索引，而不是经典索引。你也可以在 schema.yml 中定义多列索引（关于索引语法的更多详细信息，请参阅第 8 章）。你应该强烈考虑这样做，因为这通常是加速复杂查询的一个好方法。

在架构中添加索引后，你也应该在数据库本身中执行同样的操作，可以直接在数据库中执行 ADD INDEX 查询，或者调用 propel-build-all 命令（这不仅会重建表结构，还会删除所有现有数据）。

> 索引往往会使 SELECT 查询更快，但 INSERT、UPDATE 和 DELETE 查询会更慢。此外，数据库引擎每个查询只使用一个索引，并且根据内部启发式规则推断每个查询应使用的索引。添加索引在性能提升方面有时会令人失望，因此请务必衡量改进情况。

除非另有说明，symfony 中的每个请求都使用单个数据库连接，并在请求结束时关闭连接。你可以通过在 databases.yml 文件中设置 persistent: true 来启用持久数据库连接，以使用在查询之间保持打开的数据库连接池，如清单 18-11 所示。

清单 18-11 - 在 config/databases.yml 中启用持久数据库连接支持

```
prod:
  propel:
    class: sfPropelDatabase
    param:
      dsn: mysql:dbname=example;host=localhost
      username: username
      password: password
      persistent: true # Use persistent connections
```

这可能会也可能不会改善整体数据库性能，这取决于众多因素。关于此主题的文档在互联网上非常丰富。请务必在更改此设置前后对应用程序性能进行基准测试，以验证其价值。

### MySQL 特定提示

my.cnf 文件中的许多 MySQL 配置设置可能会改变数据库性能。请务必阅读关于此主题的在线文档 65。

65. http://dev.mysql.com/doc/refman/5.0/en/option-files.html

MySQL 提供的工具之一是慢查询日志。执行时间超过 long_query_time 秒的所有 SQL 语句（这是可在 my.cnf 中更改的设置）都会记录在一个文件中，该文件手动解读相当困难，但 mysqldumpslow 命令能够有用地对其进行总结。这是检测需要优化的查询的绝佳工具。

## 调整视图

根据你设计和实现视图层的方式，你可能会注意到微小的减速或加速。本节描述了替代方案及其权衡。

### 使用最快的代码片段

如果你不使用缓存系统，则需要注意 include_component() 比 include_partial() 稍慢，而 include_partial() 本身又比简单的 PHP include 稍慢。这是因为 symfony 实例化一个视图来包含局部，并实例化 sfComponent 类的对象来包含组件，这两者合计在包含文件所需之外增加了一些微小的开销。

然而，除非在模板中包含大量局部或组件，否则这种开销可以忽略不计。这可能发生在列表或表格中，以及每次在 foreach 语句内部调用 include_partial() 辅助函数时。当你注意到大量局部或组件包含对性能有显著影响时，你可以考虑缓存（参见第 12 章），如果缓存不是选项，则切换到简单的 include 语句。

至于插槽，性能差异是可感知的。设置和包含插槽所需的处理时间可以忽略不计——它相当于变量实例化。插槽始终在包含它们的模板中缓存。

### 加速路由过程

如第 9 章所述，模板中每次调用链接辅助函数都会请求路由系统将内部 URI 处理为外部 URL。这是通过在 URI 和 routing.yml 文件的模式之间查找匹配来完成的。symfony 的做法非常简单：它尝试用给定的 URI 匹配第一条规则，如果不奏效，则尝试下一条，以此类推。由于每次测试都涉及正则表达式，这相当耗时。

有一个简单的解决办法：使用规则名称而不是模块/动作对。这将告诉 symfony 使用哪条规则，路由系统就不会浪费时间尝试匹配所有先前的规则。

具体来说，请考虑在你的 routing.yml 文件中定义的以下路由规则：

```
article_by_id:
  url:   /article/:id
  param: { module: article, action: read }
```

然后，不要以这种方式输出超链接：

```
<?php echo link_to('my article', 'article/read?id='.$article->getId()) ?>
```

你应该使用最快的版本：

```
<?php echo link_to('my article', 'article_by_id', array('id' =>
$article->getId())) ?>
```

当页面包含几十个路由超链接时，差异开始变得明显。

### 跳过模板

通常，响应由一组标头和内容组成。但某些响应不需要内容。例如，某些 Ajax 交互只需要服务器提供的几个数据片段，以供 JavaScript 程序更新页面的不同部分。对于这种简短响应，仅传输一组标头速度更快。如第 11 章所讨论，操作可以只返回 JSON 标头。清单 18-12 复制了第 11 章中的一个示例。

清单 18-12 - 返回 JSON 标头的操作示例

```
public function executeRefresh()
{
  $output = '{"title":"My basic letter","name":"Mr Brown"}';
  $this->getResponse()->setHttpHeader("X-JSON", '('.$output.')');

  return sfView::HEADER_ONLY;
}
```

这跳过了模板和布局，响应可以立即发送。由于它仅包含标头，因此更轻量，传输给用户所需的时间更少。

第 6 章解释了另一种跳过模板的方法，即直接从操作返回内容文本。这打破了 MVC 分离，但可以大大提高操作的响应速度。请参阅清单 18-13 以查看示例。

清单 18-13 - 直接返回内容文本的操作示例

```
public function executeFastAction()
{
    return $this->renderText("<html><body>Hello, World!</body></html>");
}
```

## 调整缓存

第 12 章已经描述了如何缓存响应的部分内容或全部内容。响应缓存会带来重大的性能改进，应该是你首要考虑的优化事项之一。如果你想充分利用缓存系统，请继续阅读，因为本节揭示了一些你可能没有想到的技巧。

### 清除缓存的选择性部分

在应用程序开发过程中，你需要在各种情况下清除缓存：

- 当你创建新类时：将类添加到自动加载目录（项目 lib/ 文件夹之一）不足以让 symfony 在非开发环境中自动找到它。你必须清除自动加载配置缓存，以便 symfony 再次浏览 autoload.yml 文件的所有目录，并引用可自动加载类的位置（包括新类）。

- 当你在生产环境中更改配置时：配置仅在生产环境的第一个请求期间解析。后续请求使用缓存版本。因此，在生产环境中（或任何关闭调试的环境中）更改配置不会生效，直到你清除文件的缓存版本。

- 当你在启用模板缓存的环境中修改模板时：在生产环境中，有效的缓存模板始终用于替代现有模板，因此模板更改会被忽略，直到模板缓存被清除或过期。

- 当你使用 project:deploy 命令更新应用程序时：这种情况通常涵盖上述三种修改。

清除整个缓存的问题是，下一个请求处理时间会相当长，因为需要重新生成配置缓存。此外，未修改的模板也会从缓存中清除，失去之前请求的好处。

这意味着最好只清除真正需要重新生成的缓存文件。使用 cache:clear 任务的选项来定义要清除的缓存文件子集，如清单 18-14 所示。

清单 18-14 - 仅清除缓存的选择性部分

```
// Clear only the cache of the frontend application
$ php symfony cache:clear frontend

// Clear only the HTML cache of the frontend application
$ php symfony cache:clear frontend template
```



```
// Clear only the configuration cache of the frontend application
$ php symfony cache:clear frontend config
```

您也可以手动在 `cache/` 目录中删除文件，或在操作中使用 `$cacheManager->remove()` 方法选择性地清除模板缓存文件，如第 12 章所述。

所有这些技术都将最大限度地减少先前列出的任何更改对性能的负面影响。

> 当您升级 symfony 时，缓存会自动清除，无需手动干预（如果在 `settings.yml` 中将 `check_symfony_version` 参数设置为 true）。

## 生成缓存页面

当您将新应用程序部署到生产环境时，模板缓存为空。您必须等待用户访问一次页面，该页面才会被放入缓存。在关键部署中，页面处理的开销是不可接受的，缓存的好处必须在第一个请求发出时即可获得。

解决方案是在暂存环境（其配置与生产环境相似）中自动浏览应用程序的页面，以生成模板缓存，然后将带有缓存的应用程序转移到生产环境。

要自动浏览页面，一种选择是创建一个 shell 脚本，使用浏览器（例如 curl）浏览外部 URL 列表。但有一个更好、更快的解决方案：使用 `sfBrowser` 对象的 PHP 脚本，已在第 15 章中讨论过。这是一个用 PHP 编写的内部浏览器（sfTestFunctional 用于功能测试也在使用）。它接受外部 URL 并返回响应，但有趣的是，它会像常规浏览器一样触发模板缓存。由于它只初始化一次 symfony 且不经过 HTTP 传输层，这种方法要快得多。

### 清单 18-15 - 生成模板缓存，在 generate_cache.php 中

```
require_once(dirname(__FILE__).'/../config/ProjectConfiguration.class.php');
$configuration =
ProjectConfiguration::getApplicationConfiguration('frontend', 'staging',
false);
sfContext::createInstance($configuration);

// Array of URLs to browse
$uris = array(
  '/foo/index',
  '/foo/bar/id/1',
  '/foo/bar/id/2',
  ...
);

$b = new sfBrowser();
foreach ($uris as $uri)
{
  $b->get($uri);
}
```

## 使用数据库存储系统进行缓存

symfony 中模板缓存的默认存储系统是文件系统：HTML 片段或序列化的响应对象存储在项目的 cache/ 目录下。Symfony 提供了一种替代的缓存存储方式：SQLite 数据库。这样的数据库是一个简单文件，PHP 原生就知道如何非常高效地查询它。

要让 symfony 对模板缓存使用 SQLite 存储而非文件系统存储，请打开 factories.yml 文件，按如下方式编辑 view_cache 条目：

```
view_cache:
class: sfSQLiteCache
param:
database: %SF_TEMPLATE_CACHE_DIR%/cache.db
```

使用 SQLite 存储模板缓存的好处是，当缓存元素数量较大时，读写操作更快。如果您的应用程序大量使用缓存，模板缓存文件最终会分散在深层文件结构中；在这种情况下，切换到 SQLite 存储将提高性能。此外，在文件系统存储上清除缓存可能需要从磁盘删除大量文件；此操作可能持续几秒钟，在此期间您的应用程序不可用。使用 SQLite 存储系统时，缓存清除过程只产生一个文件操作：删除 SQLite 数据库文件。无论当前存储的缓存元素数量如何，该操作都是即时的。

## 绕过 Symfony

也许加速 symfony 的最佳方法是完全绕过它……这只不过是半开玩笑。有些页面不会改变，不需要在每次请求时都由框架重新处理。模板缓存已经用于加速此类页面的交付，但它仍然依赖 symfony。

第 12 章中描述的几个技巧允许您为某些页面完全绕过 symfony。第一个涉及使用 HTTP 1.1 头部请求代理和客户端浏览器自行缓存页面，以便下次需要该页面时不再请求它。第二个是超快速缓存（由 sfSuperCachePlugin 插件自动化），它包括将响应副本存储在 web/ 目录中，并修改重写规则，以便 Apache 在将请求交给 symfony 之前先查找缓存版本。

这两种方法都非常有效，即使它们仅适用于静态页面，也会将处理这些页面的负担从 symfony 上移开，服务器随后将完全可用于处理复杂请求。

## 缓存函数调用结果

如果函数不依赖于上下文敏感值或随机性，那么使用相同参数调用它两次应返回相同结果。这意味着，如果第一次已存储结果，第二次调用完全可以避免。sfFunctionCache 类正是如此。该类具有一个 call() 方法，接受一个可调用对象和一个参数数组作为其参数。调用时，该方法会对其所有参数创建一个 md5 哈希，并在缓存中查找名为该哈希的键。如果找到这样的键，函数将返回缓存中存储的结果。如果没有，sfFunctionCache 将执行函数，将结果存储在缓存中，并返回它。因此，清单 18-16 的第二次执行将比第一次更快。

### 清单 18-16 - 缓存函数调用结果

```php
$cache = new sfFileCache(array('cache_dir' =>
sfConfig::get('sf_cache_dir').'/function'));
$fc = new sfFunctionCache($cache);
$result1 = $fc->call('cos', array(M_PI));
$result2 = $fc->call('preg_replace', array('/\s\s+/', ' ', $input));
```

sfFunctionCache 构造函数期望一个缓存对象。call() 方法的第一个参数必须是可调用对象，因此可以是函数名、类名和静态方法名的数组，或对象名和公共方法名的数组。至于 call() 方法的另一个参数，它是将传递给可调用对象的参数数组。

> 如示例中使用基于文件的缓存对象，最好在 cache/ 目录下提供一个缓存目录，因为它将由 cache:clear 任务自动清理。如果您将函数缓存存储在其他位置，则通过命令行清除缓存时不会自动清除它。

## 在服务器上缓存数据

PHP 加速器提供特殊函数以将数据存储在内存中，从而可以跨请求重复使用。问题是它们都有不同的语法，并且每个执行此任务都有自己的特定方式。symfony 缓存类抽象了所有这些差异，并适用于您使用的任何加速器。请参见清单 18-17 中的语法。

### 清单 18-17 - 使用 PHP 加速器缓存数据

```php
$cache = new sfAPCCache();

// Storing data in the cache
$cache->set($name, $value, $lifetime);

// Retrieving data
$value = $cache->get($name);

// Checking if a piece of data exists in the cache
$value_exists = $cache->has($name);

// Clear the cache
$cache->clear();
```

如果缓存不起作用，set() 方法将返回 false。缓存的值可以是任何内容（字符串、数组、对象）；sfAPCCache 类将处理序列化。如果所需变量在缓存中不存在，get() 方法将返回 null。

> 如果您想深入了解内存缓存，请务必查看 sfMemcacheCache 类。它提供与其他缓存类相同的接口，并可以帮助减少负载均衡应用程序的数据库负载。

## 禁用未使用的功能

默认的 symfony 配置会激活 Web 应用程序最常用的功能。但是，如果您并非需要所有功能，则应禁用它们，以节省每次请求初始化所需的时间。





例如，如果您的应用程序不使用会话机制，或者您希望手动启动会话处理，则应将 factories.yml 文件 storage 键中的 auto_start 设置设为 false，如清单 18-18 所示。

### 清单 18-18 - 禁用会话，位于 frontend/config/factories.yml

```yaml
all:
  storage:
    class: sfSessionStorage
    param:
      auto_start: false
```

数据库功能也是如此（如前文本章“调整模型”一节所述）。如果您的应用程序不使用数据库，可以将其停用以获得少量性能提升，这次是在 settings.yml 文件中（参见清单 18-19）。

### 清单 18-19 - 禁用数据库功能，位于 frontend/config/settings.yml

```yaml
all:
  .settings:
    use_database: false # Database and model features
```

至于安全功能（参见第 6 章），您可以在 filters.yml 文件中将其停用，如清单 18-20 所示。

### 清单 18-20 - 关闭功能，位于 frontend/config/filters.yml

```yaml
rendering: ~
security:
  enabled: false

# generally, you will want to insert your own filters here

cache: ~
execution: ~
```

某些功能仅在开发环境下有用，因此您不应在生产环境中启用它们。默认情况下已经是这样，因为 symfony 的生产环境已针对性能进行了高度优化。在影响性能的开发功能中，调试模式影响最为严重。至于 symfony 日志，该功能在生产环境中也默认关闭。

您可能会想知道，如果禁用了日志记录，如何在生产环境中获取有关失败请求的信息，并认为问题不仅出现在开发环境中。幸运的是，symfony 可以使用 sfErrorLoggerPlugin 插件，该插件在生产环境中后台运行，并将 404 和 500 错误的详细信息记录在数据库中。它比文件日志功能快得多，因为插件方法仅在请求失败时才被调用，而日志机制一旦启用，无论日志级别如何，都会增加不可忽视的开销。请查看安装说明和手册。

> 请务必定期检查服务器错误日志，其中也包含关于 404 和 500 错误的非常有价值的信息。

## 优化您的代码

优化代码本身也可以提升应用程序的运行速度。本节介绍如何实现这一点的相关思路。

### 核心编译

加载十个文件所需的 I/O 操作比加载一个长文件更多，尤其是在慢速磁盘上。加载一个非常长的文件比加载一个较小的文件需要更多资源——尤其是当文件内容中有很大一部分对 PHP 解析器没有用时，注释就是这种情况。

因此，合并大量文件并去除其中的注释是一项能够提升性能的操作。Symfony 已经执行了该优化，称为核心编译。在第一个请求开始时（或清除缓存后），symfony 应用程序会将所有核心框架类（sfActions、sfRequest、sfView 等）合并到一个文件中，通过删除注释和多余空格来优化文件大小，并将其保存在缓存中，文件名为 config_core_compile.yml.php。随后的每个请求只加载这一个优化后的文件，而不是构成它的 30 个文件。

如果您的应用程序中有必须始终加载的类，尤其是包含大量注释的大型类，将它们添加到核心编译文件中可能会有好处。只需在应用程序的 config/ 目录中添加一个 core_compile.yml 文件，并在其中列出要添加的类，如清单 18-21 所示。

### 清单 18-21 - 将您的类添加到核心编译文件中，位于 frontend/config/core_compile.yml

```yaml
- %SF_ROOT_DIR%/lib/myClass.class.php
- %SF_ROOT_DIR%/apps/frontend/lib/myToolkit.class.php
- %SF_ROOT_DIR%/plugins/myPlugin/lib/myPluginCore.class.php
...
```

### project:optimize 任务

Symfony 还提供了另一个优化工具，即 project:optimize 任务。它对 symfony 和应用程序代码应用各种优化策略，可能会进一步加快执行速度。

```bash
$ php symfony project:optimize frontend prod
```

如果您想查看任务中实现的优化策略，请查看任务源代码。

### 总结

Symfony 已经是一个高度优化的框架，能够毫无问题地处理高流量网站。但如果您确实需要优化应用程序的性能，调整配置（无论是服务器配置、PHP 配置还是应用程序设置）都能带来少量提升。您还应遵循最佳实践来编写高效的模型方法；由于数据库通常是 Web 应用程序中的瓶颈，这一点值得您全力关注。模板也可以从一些技巧中受益，但最大的提升始终来自缓存。最后，不妨查看现有的插件，因为其中一些提供了创新技术，可进一步加快网页的传递（sfSuperCache、project:optimize）。

# 第 19 章 掌握 Symfony 的配置文件

既然您已经非常了解 symfony，便可以深入其代码以理解其核心设计并发现新的隐藏能力。但在扩展 symfony 类以满足您自己的需求之前，您应该更仔细地查看一些配置文件。许多功能已内置于 symfony 中，只需更改配置设置即可激活。这意味着您可以在不覆盖其类的情况下调整 symfony 的核心行为。本章将深入探讨配置文件及其强大功能。

## Symfony 设置

frontend/config/settings.yml 文件包含前端应用程序的主要 symfony 配置。您在前面的章节中已经了解了此文件中许多设置的功能，但让我们重新审视一下。

如第 5 章所述，此文件取决于环境，这意味着每个设置可以在每个环境中取不同的值。请记住，此文件中定义的每个参数都可以通过 sfConfig 类在 PHP 代码内部访问。参数名是设置名称加上 sf_ 前缀。例如，如果您想获取 cache 参数的值，只需调用 sfConfig::get('sf_cache')。

## 默认模块和动作

Symfony 为特殊情况提供默认页面。在发生路由错误时，symfony 会执行默认模块的一个动作，该模块存储在 sfConfig::get('sf_symfony_lib_dir')/controller/default/ 目录中。settings.yml 文件定义根据错误执行哪个动作：

- error_404_module 和 error_404_action：当用户输入的 URL 不匹配任何路由或发生 sfError404Exception 时调用的动作。默认值为 default/error404。
- login_module 和 login_action：当未认证的用户尝试访问在 security.yml 中定义为安全的页面时调用的动作（详情请参见第 6 章）。默认值为 default/login。
- secure_module 和 secure_action：当用户没有执行某个动作所需的凭据时调用的动作。默认值为 default/secure。
- module_disabled_module 和 module_disabled_action：当用户请求在 module.yml 中声明为禁用的模块时调用的动作。默认值为 default/disabled。

在将应用程序部署到生产环境之前，您应该自定义这些动作，因为默认模块模板在页面上包含了 symfony 标志。请参见图 19-1，了解其中一个页面（即错误 404 页面）的屏幕截图。

### 图 19-1 - 默认 404 错误页面

![](img/0f886a7f4cbcc3939be96e985ca35ff4_344_0.png)

您可以通过两种方式覆盖默认页面：

- 您可以在应用程序的 modules/ 目录中创建自己的默认模块，覆盖 settings.yml 文件中定义的所有动作（index、error404、login、secure、disabled）以及所有相关模板（indexSuccess.php、error404Success.php、loginSuccess.php、secureSuccess.php、disabledSuccess.php）。
- 您可以更改 settings.yml 文件中的默认模块和动作设置，以使用您应用程序的页面。

另外两个页面也带有 symfony 的外观和感觉，在部署到生产环境之前也需要自定义。这些页面不在默认模块中，因为它们是在 symfony 无法正常运行时被调用的。相反，您可以在 sfConfig::get('sf_symfony_lib_dir')/exception/data/ 目录中找到这些默认页面：

- error.html.php：生产环境中发生内部服务器错误时调用的页面。在其他环境中（调试模式设置为 true 时），发生错误时，symfony 会显示完整的执行堆栈和明确的错误消息（详情请参见第 16 章）。
- unavailable.php：当应用程序被禁用（通过 project:disable 任务）且用户请求页面时调用的页面。在缓存清除期间也会调用该页面（即从调用 cache:clear 任务到该任务执行结束之间）。在缓存非常大的系统上，缓存清除过程可能需要几秒钟。Symfony 无法在缓存部分清除的情况下执行请求，因此在过程结束前接收到的请求会被重定向到此页面。





要自定义这些页面，只需在项目或应用程序的 config/ 目录中创建 error/error.html.php 和 unavailable.php。Symfony 将使用这些模板，而非其自身的模板。

如需在必要时将请求重定向到 unavailable.php 页面，请在应用程序的 settings.yml 中将 check_lock 设置为 true。此检查默认处于禁用状态，因为它会为每个请求带来极少量的额外开销。

## 可选功能激活

settings.yml 文件中的某些参数控制可启用或禁用的可选框架功能。禁用未使用的功能可略微提升性能，因此请务必在部署应用程序之前查看表 19-1 中列出的设置。

## 表 19-1 - 通过 settings.yml 设置的可选功能

| 参数 | 描述 | 默认值 |
| :--- | :--- | :--- |
| use_database | 启用数据库管理器。如果不使用数据库，请将其设置为 false。 | true |
| i18n | 启用界面翻译（参见第 13 章）。如果是多语言应用程序，请将其设置为 true。 | false |
| logging_enabled | 启用 symfony 事件日志。如果要完全关闭 symfony 日志记录，请将其设置为 false。 | true |
| escaping_strategy | 启用输出转义功能（参见第 7 章）。如果要转义传递给模板的数据，请将其设置为 true。 | true |
| cache | 启用模板缓存（参见第 12 章）。如果某个模块包含 cache.yml 文件，请将其设置为 true。仅在启用时，缓存过滤器（sfCacheFilter）才会生效。 | 开发环境为 false，生产环境为 true |
| web_debug | 启用 Web 调试工具栏以便轻松调试（参见第 16 章）。若要在每个页面上显示工具栏，请将其设置为 true。 | 开发环境为 true，生产环境为 false |
| check_symfony_version | 为每个请求启用 symfony 版本检查。框架升级后，若要自动清除缓存，请将其设置为 true。如果升级后始终清除缓存，请保持设置为 false。 | false |
| check_lock | 启用应用程序锁定系统，由 cache:clear 和 project:disable 任务触发（参见上一节）。若要将所有发往已禁用应用程序的请求重定向到 sfConfig::get('sf_symfony_lib_dir')/exception/data/unavailable.php 页面，请将其设置为 true。 | false |
| compressed | 启用 PHP 响应压缩。若要通过 PHP 压缩处理程序压缩传出 HTML，请将其设置为 true。 | false |

## 功能配置

Symfony 使用 `settings.yml` 中的某些参数来更改内置功能（如表单验证、缓存和第三方模块）的行为。

### 输出转义设置

输出转义设置控制模板中变量的访问方式（参见第 7 章）。`settings.yml` 文件为此功能包含两个设置：

- `escaping_strategy` 设置的值可以为 `true` 或 `false`。
- `escaping_method` 设置可以设置为 `ESC_RAW`、`ESC_SPECIALCHARS`、`ESC_ENTITIES`、`ESC_JS` 或 `ESC_JS_NO_ENTITIES`。

### 路由设置

路由设置（参见第 9 章）定义在 `factories.yml` 的 `routing` 键下。清单 19-1 显示了默认路由配置。

### 清单 19-1 - 路由配置设置，位于 frontend/config/factories.yml

```
routing:
  class: sfPatternRouting
  param:
    load_configuration: true
    suffix:               .
    default_module:       default
    default_action:       index
    variable_prefixes:    [':']
    segment_separators:   ['/', '.']
    variable_regex:       '[\w\d_+]'
    debug:                %SF_DEBUG%
    logging:              %SF_LOGGING_ENABLED%
    cache:
      class: sfFileCache
      param:
        automatic_cleaning_factor: 0
        cache_dir:                 %SF_CONFIG_CACHE_DIR%/routing
        lifetime:                  31556926
        prefix:                    %SF_APP_DIR%
```

- `suffix` 参数设置生成 URL 的默认后缀。默认值为句点 (`.`)，即表示无后缀。例如，将其设置为 `.html` 可使所有生成的 URL 看起来像静态页面。
- 当路由规则未定义 `module` 或 `action` 参数时，将改用 `factories.yml` 中的值：
  - `default_module`: 默认模块请求参数。默认值为 `default` 模块。
  - `default_action`: 默认动作请求参数。默认值为 `index` 动作。
- 默认情况下，路由模式通过冒号 (`:`) 前缀识别命名通配符。但如果您希望采用更符合 PHP 习惯的语法编写规则，可以在 `variable_prefixes` 数组中添加美元符号 (`$`)。这样一来，您就可以编写类似 `'/article/$year/$month/$day/$title'` 的模式，而非 `'/article/:year/:month/:day/:title'`。
- 模式路由将在分隔符之间识别命名通配符。默认分隔符为斜杠和句点，但您可以根据需要在 `segment_separators` 参数中添加更多。例如，如果您添加连字符 (-)，可以编写类似 '/article/:year-:month-:day/:title' 的模式。

- 模式路由在生产模式下使用其自身缓存，以加快外部 URL 与内部 URL 之间的转换。默认情况下，此缓存使用文件系统，但您可以使用任何缓存类，前提是在 cache 参数中声明该类及其设置。有关可用缓存存储类的列表，请参见第 15 章。要在生产环境中禁用路由缓存，请将 debug 参数设置为 true。

这些仅是 sfPatternRouting 类的设置。您可以为应用程序路由使用另一个类，可以是您自己的类，也可以是 symfony 的路由工厂之一（sfNoRouting 和 sfPathInfoRouting）。使用这两个工厂中的任何一个，所有外部 URL 都类似于 'module/action?key1=param1'。无法进行自定义——但速度很快。区别在于，第一个使用 PHP 的 GET，第二个使用 PATH_INFO。它们主要用于后端界面。

还有一个与路由相关的附加参数，但该参数存储在 settings.yml 中：

- `no_script_name` 参数用于在生成的 URL 中启用前端控制器名称。`no_script_name` 设置在一个项目中只能为单个应用程序启用，除非您将前端控制器存储在不同目录中并更改默认 URL 重写规则。它通常在主应用程序的生产环境中启用，而在其他环境中禁用。

### 表单验证设置

> > 本节中描述的功能自 symfony 1.1 起已弃用，且仅在启用 sfCompat10 插件时才可用。

表单验证设置控制验证辅助函数输出的错误消息的外观（参见第 10 章）。这些错误包含在 <div> 标签中，并使用 validation_error_class 设置作为 class 属性，并使用 validation_error_id_prefix 设置来构建 id 属性。默认值为 form_error 和 error_for_，因此对名为 foobar 的输入调用 form_error() 辅助函数输出的属性将为 class="form_error" id="error_for_foobar"。

两个设置决定每条错误消息前后的字符：validation_error_prefix 和 validation_error_suffix。您可以更改它们以一次性自定义所有错误消息。

### 缓存设置

缓存设置大多在 cache.yml 中定义，除了 settings.yml 中的两个：cache 启用模板缓存机制，etag 启用服务器端的 ETag 处理（参见第 15 章）。您还可以在 factories.yml 中指定所有缓存系统（视图缓存、路由缓存和 i18n 缓存）使用的存储。清单 19-2 显示了默认视图缓存工厂配置。

### 清单 19-2 - 视图缓存配置设置，位于 frontend/config/factories.yml

```
view_cache:
  class: sfFileCache
  param:
    automatic_cleaning_factor: 0
    cache_dir: %SF_TEMPLATE_CACHE_DIR%
    lifetime: 86400
    prefix: %SF_APP_DIR%/template
```

该类可以是 *sfFileCache*、*sfAPCCache*、*sfEAcceleratorCache*、*sfXCacheCache*、*sfMemcacheCache* 和 *sfSQLiteCache* 中的任何一个。也可以是您自己的自定义类，前提是它扩展 *sfCache* 并提供用于设置、检索和删除缓存中键的相同通用方法。工厂参数取决于您选择的类，但存在常量：

- lifetime 定义缓存部分被移除前的秒数
- prefix 是添加到每个缓存键的前缀（在前缀中使用环境，以便根据环境使用不同的缓存）。如果希望两个应用程序共享缓存，请为它们使用相同的前缀。

然后，对于每个特定的工厂，您都必须定义缓存存储的位置。

- 对于 *sfFileCache*，*cache_dir* 参数指定缓存目录的绝对路径
- *sfAPCCache*、*sfEAcceleratorCache* 和 *sfXCacheCache* 不接受任何位置参数，因为它们使用 PHP 原生函数与 APC、EAccelerator 或 XCache 缓存系统进行通信
- 对于 *sfMemcacheCache*，请在 host 参数中输入 Memcached 服务器的主机名，或在 *servers* 参数中输入主机数组
- 对于 *sfSQLiteCache*，应在 *database* 参数中输入 SQLite 数据库文件的绝对路径

有关其他参数，请查看每个缓存类的 API 文档。

视图并非唯一能够使用缓存的组件。路由和 I18N 工厂都提供 *cache* 参数，您可以在其中设置任何缓存工厂，就像视图缓存一样。例如，清单 19-1 显示路由默认使用文件缓存来实现加速策略，但您可以将其更改为任何想要的缓存。

### 日志设置

两个日志设置（参见第 16 章）存储在 *settings.yml* 中：

- *error_reporting* 指定在 PHP 日志中记录哪些事件。默认情况下，对于生产环境，它被设置为 *E_PARSE | E_COMPILE_ERROR | E_ERROR | E_CORE_ERROR | E_USER_ERROR*（因此记录的事件为 *E_PARSE*、*E_COMPILE_ERROR*、*E_ERROR*、*E_CORE_ERROR* 和 *E_USER_ERROR*），对于开发环境，它被设置为 *E_ALL | E_STRICT*。
- *web_debug* 设置激活 Web 调试工具栏。仅在开发和测试环境中将其设置为 *true*。

### 资源路径

*settings.yml* 文件还存储资源路径。如果您想使用与 symfony 捆绑的不同版本的资源，可以更改这些路径设置：

- 管理生成器所需的文件存储在 *admin_web_dir* 中
- Web 调试工具栏所需的文件存储在 *web_debug_web_dir* 中

### 默认辅助函数

为每个模板加载的默认辅助函数在 *standard_helpers* 设置中声明（参见第 7 章）。默认情况下，这些是 Partial 和 Cache 辅助函数组。如果您在应用程序的所有模板中使用某个辅助函数组，则将其名称添加到 *standard_helpers* 设置中，可免去在每个模板中使用 *use_helper()* 声明的麻烦。





## Activated Modules

由插件或 symfony 核心激活的模块在 enabled_modules 参数中声明。即使插件捆绑了某个模块，除非该模块在 enabled_modules 中声明，否则用户无法请求该模块。默认模块（提供默认 symfony 页面，例如 congratulations、page not found 等）是默认唯一启用的模块。

## Character Set

响应的字符集是应用程序的一般设置，因为框架的许多组件（模板、输出转义器、助手等）都会用到它。在 charset 设置中定义，其默认（且推荐）值为 utf-8。

## Adding Your application settings

settings.yml 文件为应用程序定义 symfony 设置。如第 5 章所述，当要添加新参数时，最佳位置是 frontend/config/app.yml 文件。该文件也依赖于环境，其中定义的设置可通过带有 app_ 前缀的 sfConfig 类访问。

### Listing 19-3

```
all:
  creditcards:
    fake: false        # app_creditcards_fake
    visa: true         # app_creditcards_visa
    americanexpress: true         # app_creditcards_americanexpress
```

您也可以在项目配置目录中编写 app.yml 文件，这提供了一种定义自定义项目设置的方法。配置级联也适用于该文件，因此应用程序 app.yml 文件中定义的设置会覆盖在项目级别定义的设置。

## Extending the Autoloading Feature

自动加载功能在第 2 章中简要说明，如果类位于特定目录中，则无需在代码中手动 require 类。这意味着您可以让框架为您完成这项工作，使其仅在需要且仅在适当的时候加载必要的类。

The autoload.yml file lists the paths in which autoloaded classes are stored. The first time this configuration file is processed, symfony parses all the directories referenced in the file. Each time a file ending with .php is found in one of these directories, the file path and the class names found in this file are added to an internal list of autoloading classes. This list is saved in the cache, in a file called config/config_autoload.yml.php. Then, at runtime, when a class is used, symfony looks in this list for the class path and includes the .php file automatically.

Autoloading works for all .php files containing classes and/or interfaces.

By default, classes stored in the following directories in your projects benefit from the autoloading automatically:

- myproject/lib/
- myproject/lib/model
- myproject/apps/frontend/lib/
- myproject/apps/frontend/modules/mymodule/lib

There is no autoload.yml file in the default application configuration directory. If you want to modify the framework settings—for instance, to autoload classes stored somewhere else in your file structure—create an empty autoload.yml file and override the settings of sfConfig::get('sf_symfony_lib_dir')/config/config/autoload.yml or add your own.

The autoload.yml file must start with an autoload: key and list the locations where symfony should look for classes. Each location requires a label; this gives you the ability to override symfony's entries. For each location, provide a name (it will appear as a comment in config_autoload.yml.php) and an absolute path. Then define if the search must be recursive, which directs symfony to look in all the subdirectories for .php files, and exclude the subdirectories you want. Listing 19-3 shows the locations used by default and the file syntax.

### Listing 19-3 - Default Autoloading Configuration, in sfConfig::get('sf_symfony_lib_dir')/config/config/autoload.yml

```
autoload:
  # plugins
  plugins_lib:
    name: plugins lib
    path: %SF_PLUGINS_DIR%/*/lib
    recursive: true

  plugins_module_lib:
    name: plugins module lib
    path: %SF_PLUGINS_DIR%/*/modules/*/lib
    prefix: 2
    recursive: true

  # project
  project:
    name: project
    path: %SF_LIB_DIR%
    recursive: true
    exclude: [model, symfony]

  project_model:
    name: project model
    path: %SF_LIB_DIR%/model
    recursive: true

  # application
  application:
    name: application
    path: %SF_APP_LIB_DIR%
    recursive: true

  modules:
    name: module
    path: %SF_APP_DIR%/modules/*/lib
    prefix: 1
    recursive: true
```

A rule path can contain wildcards and use the file path parameters defined in the configuration classes (see the next section). If you use these parameters in the configuration file, they must appear in uppercase and begin and end with %.

Editing your own autoload.yml will add new locations to symfony's autoloading, but you may want to extend this mechanism and add your own autoloading handler to symfony's handler. As symfony uses the standard spl_autoload_register() function to manage class autoloading, you can register more callbacks in the application configuration class:

```
class frontendConfiguration extends sfApplicationConfiguration
{
  public function initialize()
  {
    parent::initialize(); // load symfony autoloading first

    // insert your own autoloading callables here
    spl_autoload_register(array('myToolkit', 'autoload'));
  }
}
```

When the PHP autoloading system encounters a new class, it will first try the symfony autoloading method (and use the locations defined in autoload.yml). If it doesn't find a class definition, all the other callables registered with spl_autoload_register() will be called, until the class is found. So you can add as many autoloading mechanisms as you want—for instance, to provide a bridge to other framework components (see Chapter 17).

## Custom File Structure

Each time the framework uses a path to look for something (from core classes to templates, plug-ins, configurations, and so on), it uses a path variable instead of an actual path. By changing these variables, you can completely alter the directory structure of a symfony project, and adapt to the file organization requirements of any client.

> Customizing the directory structure of a symfony project is possible but not necessarily a good idea. One of the strengths of a framework like symfony is that any web developer can look at a project built with it and feel at home, because of the respect for conventions. Make sure you consider this issue before deciding to use your own directory structure.

## The Basic File Structure

The path variables are defined in the sfProjectConfiguration and sfApplicationConfiguration classes and stored in the sfConfig object. Listing 19-4 shows a listing of the path variables and the directory they reference.

### Listing 19-4 - Default File Structure Variables, defined in sfProjectConfiguration and sfApplicationConfiguration

```
sf_root_dir              # myproject/
sf_apps_dir              # apps/
sf_app_dir               # frontend/
sf_app_config_dir        # config/
sf_app_i18n_dir          # i18n/
sf_app_lib_dir           # lib/
sf_app_module_dir        # modules/
sf_app_template_dir      # templates/
sf_cache_dir             # cache/
sf_app_base_cache_dir    # frontend/
sf_app_cache_dir         # prod/
sf_template_cache_dir    # templates/
sf_i18n_cache_dir        # i18n/
sf_config_cache_dir      # config/
sf_test_cache_dir        # test/
sf_module_cache_dir      # modules/
sf_config_dir            # config/
sf_data_dir              # data/
sf_lib_dir               # lib/
sf_log_dir               # log/
sf_test_dir              # test/
sf_plugins_dir           # plugins/
sf_web_dir               # web/
sf_upload_dir            # uploads/
```

Every path to a key directory is determined by a parameter ending with `_dir`. Always use the path variables instead of real (relative or absolute) file paths, so that you will be able to change them later, if necessary. For instance, when you want to move a file to the `uploads/` directory in an application, you should use `sfConfig::get('sf_upload_dir')` for the path instead of `sfConfig::get('sf_root_dir').'/web/uploads'`.

## Customizing the File Structure

You will probably need to modify the default project file structure if you develop an application for a client who already has a defined directory structure and who is not willing to change it to comply with the symfony logic. By overriding the `sf_XXX_dir` variables with `sfConfig`, you can make symfony work for a totally different directory structure than the default structure. The best place to do this is in the application `ProjectConfiguration` class for project directories, or `XXXConfiguration` class for applications directories.

For instance, if you want all applications to share a common directory for the template layouts, add this line to the `setup()` method of the `ProjectConfiguration` class to override the `sf_app_template_dir` settings:

```
sfConfig::set('sf_app_template_dir',
sfConfig::get('sf_root_dir').DIRECTORY_SEPARATOR.'templates');
```

> Even if you can change your project directory structure by calling `sfConfig::set()`, it's better to use the dedicated methods defined by the project and application configuration classes if possible as they take care of changing all the related paths. For example, the `setCacheDir()` method changes the following constants: `sf_cache_dir`, `sf_app_base_cache_dir`, `sf_app_cache_dir`, `sf_template_cache_dir`, `sf_i18n_cache_dir`, `sf_config_cache_dir`, `sf_test_cache_dir`, and `sf_module_cache_dir`.

## Modifying the Project Web Root

All the paths built in the configuration classes rely on the project root directory, which is determined by the `ProjectConfiguration` file included in the front controller. Usually, the root directory is one level above the `web/` directory, but you can use a different structure. Suppose that your main directory structure is made of two directories, one public and one private, as shown in Listing 19-5. This typically happens when hosting a project on a shared host.

### Listing 19-5 - Example of Custom Directory Structure for a Shared Host

```
symfony/  # Private area
apps/
```





config/
...
www/    # Public area
images/
css/
js/
index.php

在这种情况下，根目录是 symfony/ 目录。因此，index.php 前端控制器只需按如下方式包含 config/ProjectConfiguration.class.php 文件，应用即可工作：

```
Listing 19-9
require_once(dirname(__FILE__).'/../symfony/config/ProjectConfiguration.class.php');
```

此外，使用 setWebDir() 方法将公共区域从通常的 web/ 更改为 www/，如下所示：

```
Listing 19-10
class ProjectConfiguration extends sfProjectConfiguration
{
    public function setup()
    {
        // ...

        $this->setWebDir($this->getRootDir().'/../www');
    }
}
```

## 理解配置处理器

每个配置文件都有一个处理器。配置处理器的工作是管理配置级联，并执行配置文件与可在运行时执行的优化 PHP 代码之间的转换。

## 默认配置处理器

默认处理器配置存储在 sfConfig::get('sf_symfony_lib_dir')/config/config/config_handlers.yml 中。该文件根据文件路径将处理器与配置文件关联。清单 19-6 显示了该文件的摘录。

Listing 19-6 - Extract of sfConfig::get('sf_symfony_lib_dir')/config/config/config_handlers.yml

```
Listing 19-11
config/settings.yml:
class:   sfDefineEnvironmentConfigHandler
param:
  prefix: sf_

config/app.yml:
class:   sfDefineEnvironmentConfigHandler
param:
  prefix: app_

config/filters.yml:
class:   sfFilterConfigHandler
modules/*/config/module.yml:
 class: sfDefineEnvironmentConfigHandler
 param:
   prefix: mod_
   module: yes
```

对于每个配置文件（`config_handlers.yml` 通过带通配符的文件路径标识每个文件），处理器类在 `class` 键下指定。

由 `sfDefineEnvironmentConfigHandler` 处理的配置文件的设置可以通过 `sfConfig` 类直接在代码中使用，而 `param` 键包含一个前缀值。

您可以添加或修改用于处理每个配置文件的处理器——例如，使用 INI 或 XML 文件而不是 YAML 文件。

> `config_handlers.yml` 文件的配置处理器是 `sfRootConfigHandler`，显然，它不能更改。

如果您需要修改配置的解析方式，请在应用程序的 `config/` 文件夹中创建一个空的 `config_handlers.yml` 文件，并使用您编写的类覆盖 `class` 行。

## 添加您自己的处理器

使用处理器来处理配置文件有两个重要好处：

- 配置文件被转换为可执行的 PHP 代码，并将此代码存储在缓存中。这意味着在生产环境中仅解析一次配置，性能最佳。

- 配置文件可以在不同级别（项目和应用程序）定义，最终参数值将由级联产生。因此，您可以在项目级别定义参数，并针对每个应用程序进行覆盖。

如果您想编写自己的配置处理器，请遵循框架在 `sfConfig::get('sf_symfony_lib_dir')/config/` 目录中使用的结构示例。

假设您的应用程序包含一个 `myMapAPI` 类，它提供与第三方地图 Web 服务的接口。该类需要使用 URL 和用户名进行初始化，如清单 19-7 所示。

## 清单 19-7 - `myMapAPI` 类初始化示例

```
$mapApi = new myMapAPI();
$mapApi->setUrl($url);
$mapApi->setUser($user);
```

您可能希望将这两个参数存储在名为 `map.yml` 的自定义配置文件中，该文件位于应用程序的 `config/` 目录中。此配置文件可能包含以下内容：

```
api:
  url: map.api.example.com
  user: foobar
```

要将这些设置转换为与清单 19-7 等效的代码，您必须构建一个配置处理器。每个配置处理器都必须扩展 `sfConfigHandler` 并提供一个 `execute()` 方法，该方法期望将配置文件路径数组作为参数，并且必须返回要写入缓存文件的数据。YAML 文件的处理器应扩展 sfYamlConfigHandler 类，该类提供用于 YAML 解析的额外便利功能。对于 map.yml 文件，典型的配置处理器可以如清单 19-8 所示编写。

## 清单 19-8 - 自定义配置处理器，位于 frontend/lib/myMapConfigHandler.class.php

```
<?php

class myMapConfigHandler extends sfYamlConfigHandler
{
    public function execute($configFiles)
    {
        // Parse the yaml
        $config = $this->parseYamls($configFiles);

        $data = "<?php\n";
        $data .= "\$mapApi = new myMapAPI();\n";

        if (isset($config['api']['url']))
        {
            $data .= sprintf("\$mapApi->setUrl('%s');\n", $config['api']['url']);
        }

        if (isset($config['api']['user']))
        {
            $data .= sprintf("\$mapApi->setUser('%s');\n", $config['api']['user']);
        }

        return $data;
    }
}
```

symfony 传递给 execute() 方法的 $configFiles 数组将包含在 config/ 文件夹中找到的所有 map.yml 文件的路径。parseYamls() 方法将处理配置级联。

要将此新处理器与 map.yml 文件关联，必须创建一个包含以下内容的 config_handlers.yml 配置文件：

```
Listing 19-15
config/map.yml:
class: myMapConfigHandler
```

> 该类必须是自动加载的（这里就是这样），或者定义在 param 键下的 file 参数中指定路径的文件中。

与许多其他 symfony 配置文件一样，您也可以直接在 PHP 代码中注册配置处理器：

```
Listing 19-16
sfContext::getInstance()->getConfigCache()->registerConfigHandler('config/map.yml', 'myMapConfigHandler', array());
```

当您需要在应用程序中使用基于 map.yml 文件并由 myMapConfigHandler 处理器生成的代码时，请调用以下行：

```
include sfContext::getInstance()->getConfigCache()->checkConfig('config/map.yml');
```

调用 checkConfig() 方法时，symfony 会在配置目录中查找现有的 map.yml 文件，并使用 config_handlers.yml 文件中指定的处理器对它们进行处理，前提是缓存中不存在 map.yml.php 或 map.yml 文件比缓存更新。

如果要在 YAML 配置文件中处理环境，处理器可以扩展 sfDefineEnvironmentConfigHandler 类，而不是 sfYamlConfigHandler。您不应调用 parseYaml() 方法来检索配置，而应调用 getConfiguration() 方法：$config = $this->getConfiguration($configFiles)。

## 使用现有配置处理器

如果您只需要允许用户通过 sfConfig 从代码中检索值，可以使用 sfDefineEnvironmentConfigHandler 配置处理器类。例如，要使 url 和 user 参数分别可用为 sfConfig::get('map_url') 和 sfConfig::get('map_user')，请按如下方式定义处理器：

```
config/map.yml:
class: sfDefineEnvironmentConfigHandler
param:
  prefix: map_
```

注意不要选择已被其他处理器使用的前缀。现有前缀为 sf_、app_ 和 mod_。

## 摘要

配置文件可以大幅修改框架的工作方式。由于 symfony 甚至为其核心功能和文件加载依赖配置，因此它可以适应比标准专用主机多得多的环境。这种极强的可配置性是 symfony 的主要优势之一。尽管它有时会吓到新来者（他们在配置文件中看到许多需要学习的约定），但它允许 symfony 应用程序与非常大量的平台和环境兼容。一旦您掌握了 symfony 的配置，就没有服务器会拒绝运行您的应用程序！





# 附录

# 附录 A

## 模型层内部 (Propel)

目前为止的讨论大多集中在构建页面以及处理请求和响应上。但 Web 应用程序的业务逻辑主要依赖于其数据模型。Symfony 的默认模型组件基于对象/关系映射层。Symfony 自带了两种最流行的 PHP ORM：Propel 和 Doctrine。在 symfony 应用程序中，您通过对象访问存储在数据库中的数据并对其进行修改；您从不直接操作数据库。这保持了高度的抽象性和可移植性。

本章解释了如何创建对象数据模型，以及在 Propel 中访问和修改数据的方式。它还演示了 Propel 在 Symfony 中的集成。

## 为什么使用 ORM 和抽象层？

数据库是关系型的。PHP 5 和 symfony 是面向对象的。为了在面向对象的上下文中最有效地访问数据库，需要一个将对象逻辑转换为关系逻辑的接口。如第 1 章所述，这个接口称为对象关系映射（ORM），它由提供数据访问并将业务规则封装在自身中的对象组成。

ORM 的主要好处是可重用性，它允许从应用程序的各个部分（甚至不同的应用程序）调用数据对象的方法。ORM 层还封装了数据逻辑——例如，根据论坛用户的贡献数量及其受欢迎程度计算用户评级。当页面需要显示此类用户评级时，它只需调用数据模型的一个方法，而无需担心计算细节。如果计算随后发生变化，您只需修改模型中的评级方法，其余应用程序保持不变。

使用对象代替记录、使用类代替表，还有另一个好处：它们允许您向对象添加新的访问器，而这些访问器不一定对应表中的某一列。例如，如果您有一个名为 client 的表，其中包含 first_name 和 last_name 两个字段，您可能希望只需一个 Name。在面向对象的世界中，只需向 Client 类添加一个新的访问器方法即可，如清单 8-1 所示。从应用程序的角度来看，Client 类的 FirstName、LastName 和 Name 属性之间没有区别。只有类本身可以确定哪些属性对应数据库列。

```
Listing 8-1 - Accessors Mask the Actual Table Structure in a Model Class

public function getName()
{
    return $this->getFirstName().' '.$this->getLastName();
}
```

所有重复的数据访问函数和数据本身的业务逻辑都可以保存在这样的对象中。假设您有一个 ShoppingCart 类，其中保存了 Items（即对象）。为了获取购物车的总金额以供结账，请编写一个自定义方法来封装实际计算，如清单 8-2 所示。

### 清单 8-2 - 访问器掩盖数据逻辑

```
public function getTotal()
{
    $total = 0;
    foreach ($this->getItems() as $item)
    {
        $total += $item->getPrice() * $item->getQuantity();
    }

    return $total;
}
```

在构建数据访问过程时，还需要考虑另一个重要点：数据库厂商使用不同的 SQL 语法变体。切换到另一个数据库管理系统（DBMS）迫使您重新编写为之前系统设计的部分 SQL 查询。如果您使用与数据库无关的语法构建查询，并将实际的 SQL 转换留给第三方组件，您可以无痛切换数据库系统。这就是数据库抽象层的目标。它强制您对查询使用特定语法，并承担符合 DBMS 特性和优化 SQL 代码的繁琐工作。

抽象层的主要好处是可移植性，因为它使得即使在项目中期也可以切换到另一个数据库。假设您需要为一个应用程序编写快速原型，但客户尚未决定哪种数据库系统最适合他的需求。例如，您可以先使用 SQLite 构建应用程序，并在客户准备好做出决定时切换到 MySQL、PostgreSQL 或 Oracle。只需更改配置文件中的一行，即可生效。

Symfony 将 Propel 或 Doctrine 用作 ORM，它们使用 PHP Data Objects 进行数据库抽象。这两个第三方组件（均由 Propel 和 Doctrine 团队开发）已无缝集成到 symfony 中，您可以将它们视为框架的一部分。本章中描述的它们的语法和约定已进行了调整，以便与 symfony 的语法和约定尽可能一致。

> 在 symfony 项目中，所有应用程序共享同一个模型。这就是项目级别的全部意义：将依赖共同业务规则的应用程序组合在一起。这就是模型独立于应用程序的原因，模型文件存储在项目根目录的 lib/model/ 目录中。

## Symfony 的数据库架构

为了创建 symfony 将使用的对象数据模型，您需要将数据库中的关系模型转换为对象数据模型。ORM 需要关系模型的描述来进行映射，这称为架构（schema）。在架构中，您定义表、它们的关系以及列的特性。

Symfony 对架构的语法使用 YAML 格式。schema.yml 文件必须位于 myproject/config/ 目录中。

> Symfony 还理解 Propel 的原生 XML 架构格式，如本章稍后“超越 schema.yml：schema.xml”节中所述。

### 架构示例

如何将数据库结构转换为架构？示例是理解它的最佳方式。假设您有一个包含两个表的博客数据库：blog_article 和 blog_comment，结构如图 8-1 所示。

### 图 8-1 - 博客数据库表结构

![](img/0f886a7f4cbcc3939be96e985ca35ff4_360_0.png)

相关的 schema.yml 文件应如清单 8-3 所示。

### 清单 8-3 - 示例 schema.yml

```
propel:
  blog_article:
    _attributes: { phpName: Article }
    id:
    title: varchar(255)
    content: longvarchar
    created_at: ~
  blog_comment:
    _attributes: { phpName: Comment }
    id: ~
    blog_article_id: ~
    author: varchar(255)
    content: longvarchar
    created_at: ~
```

请注意，数据库名称本身（blog）不会出现在 schema.yml 文件中。相反，数据库是在连接名称下描述的（本示例中为 propel）。这是因为实际连接设置可能取决于应用程序运行的环境。例如，当您在开发环境中运行应用程序时，将访问开发数据库（可能是 blog_dev），但与生产数据库具有相同的架构。连接设置将在本章稍后“数据库连接”节中描述的 databases.yml 文件中指定。架构不包含任何详细的连接设置，只包含一个连接名称，以保持数据库抽象。

### 基本架构语法

在 schema.yml 文件中，第一个键表示连接名称。它可以包含多个表，每个表都有一组列。根据 YAML 语法，键以冒号结尾，结构通过缩进显示（一个或多个空格，但没有制表符）。

表可以具有特殊属性，包括 phpName（将生成的类的名称）。如果您未为表提及 phpName，symfony 将根据表名的 camelCase 版本创建它。

> camelCase 约定从单词中删除下划线，并将内部单词的首字母大写。blog_article 和 blog_comment 的默认 camelCase 版本分别是 BlogArticle 和 BlogComment。此约定的名称来源于长单词内部大写字母的外观，类似于骆驼的驼峰。

表包含列。列值可以以三种不同的方式定义：

- 如果您未定义任何内容（YAML 中的 ~ 相当于 PHP 中的 null），symfony 将根据列名和本章稍后“空列”节中描述的若干约定，推断最佳属性。例如，清单 8-3 中的 id 列无需定义。Symfony 会将其设置为自动递增的整数，即表的主键。blog_comment 表中的 blog_article_id 将被理解为 blog_article 表的外键（以 _id 结尾的列被视为外键，相关表会根据列名的第一部分自动确定）。名为 created_at 的列会自动设置为时间戳类型。对于所有这些列，您无需指定任何类型。这就是 schema.yml 如此易于编写的原因之一。

- 如果您仅定义一个属性，则为列类型。Symfony 了解常见的列类型：boolean、integer、float、date、varchar(size)、longvarchar（例如，在 MySQL 中转换为 text）等等。对于超过 256 个字符的文本内容，您需要使用 longvarchar 类型，该类型没有大小限制（但在 MySQL 中不能超过 65KB）。

- 如果您需要定义其他列属性（如默认值、必填项等），应将列属性编写为一组 key: value。这种扩展架构语法将在本章稍后描述。

列也可以带有 phpName 属性，即名称的大写版本（Id、Title、Content 等），在大多数情况下不需要覆盖。

表还可以包含显式外键和索引，以及一些特定于数据库的结构定义。要了解更多信息，请参阅本章稍后的“扩展架构语法”节。

### 模型类

架构用于构建 ORM 层的模型类。为了节省执行时间，这些类是通过名为 propel:build-model 的命令行任务生成的。

```
Listing A-4
$ php symfony propel:build-model
```

> 构建模型后，您必须记得使用 php symfony cc 清除 symfony 的内部缓存，以便 symfony 找到您新创建的模型。

输入此命令将启动架构的分析，并在项目的 lib/model/om/ 目录中生成基础数据模型类：

- BaseArticle.php
- BaseArticlePeer.php
- BaseComment.php





- BaseCommentPeer.php

此外，实际的数据模型类将在 lib/model/ 中创建：

- Article.php
- ArticlePeer.php
- Comment.php
- CommentPeer.php

您只定义了两个表，却最终得到了八个文件。这没有问题，但有必要加以解释。

## 基类和自定义类

为什么要在两个不同的目录中保留数据对象模型的两个版本？

您可能需要向模型对象添加自定义方法和属性（可以参考清单 8-1 中的 getName() 方法）。但随着项目的发展，您也会添加表或列。每当修改 schema.yml 文件时，都需要通过重新调用 propel:build-model 来重新生成对象模型类。如果将自定义方法编写在实际生成的类中，它们将在每次生成后被擦除。

保存在 lib/model/om/ 目录中的 Base 类是直接从架构生成的。您绝不应修改它们，因为每次重新构建模型都会完全擦除这些文件。

另一方面，保存在 lib/model/ 目录中的自定义对象类实际上继承自 Base 类。在现有模型上调用 propel:build-model 任务时，这些类不会被修改。因此，这是您可以添加自定义方法的地方。

清单 8-4 展示了首次调用 propel:build-model 任务时创建的自定义模型类示例。

### 清单 8-4 - 示例模型类文件，位于 lib/model/Article.php

```
class Article extends BaseArticle
{
}
```

它继承了 BaseArticle 类的所有方法，但对架构的修改不会影响它。

自定义类扩展基类的机制使您可以开始编写代码，即使不知道数据库的最终关系模型。相关的文件结构使模型既可定制又可演进。

## 对象类和 Peer 类

Article 和 Comment 是表示数据库中记录的对象类。它们提供对记录列及相关记录的访问。这意味着您可以通过调用 Article 对象的方法来获取文章标题，如清单 8-5 所示。

### 清单 8-5 - 对象类中可用于记录列的 Getter

```
$article = new Article();
// ...
$title = $article->getTitle();
```

ArticlePeer 和 CommentPeer 是 Peer 类，即包含用于操作表的静态方法的类。它们提供从表中检索记录的方法。它们的方法通常返回相关对象类的对象或对象集合，如清单 8-6 所示。

### 清单 8-6 - Peer 类中可用于检索记录的静态方法

```
// $articles is an array of objects of class Article
$articles = ArticlePeer::retrieveByPks(array(123, 124, 125));
```

> 从数据模型角度来看，不存在 Peer 对象。这就是为什么 Peer 类的方法使用 ::（用于静态方法调用）而不是通常的 ->（用于实例方法调用）来调用。

因此，将对象类和 Peer 类组合为基版本和自定义版本，会根据架构中描述的每个表生成四个类。事实上，lib/model/map/ 目录中还会创建第五个类，其中包含运行时环境所需的表元数据信息。但由于您可能永远不会更改此类，可以将其忽略。

## 访问数据

在 symfony 中，数据通过对象来访问。如果您习惯使用关系模型并使用 SQL 来检索和修改数据，对象模型方法可能看起来复杂。但一旦您体会到面向对象数据访问的强大功能，您很可能会非常喜欢它。

但首先，让我们确保我们使用相同的术语。关系数据模型和面向对象数据模型使用相似的概念，但各自有自己的命名：

| 关系型 | 面向对象 |
| --- | --- |
| 表 | 类 |
| 行，记录 | 对象 |
| 字段，列 | 属性 |

## 检索列值

当 symfony 构建模型时，它会为 schema.yml 中定义的每个表创建一个基对象类。这些类中的每一个都带有基于列定义的默认构造函数、访问器和修改器：new、getXXX() 和 setXXX() 方法有助于创建对象并访问对象属性，如清单 8-7 所示。

### 清单 8-7 - 生成的对象类方法

```
$article = new Article();
$article->setTitle('My first article');
$article->setContent("This is my very first article.\n Hope you enjoy
it!");

$title = $article->getTitle();
$content = $article->getContent();
```

> 生成的对象类名为 Article，即赋予 blog_article 表的 phpName。如果在架构中未定义 phpName，该类将被命名为 BlogArticle。访问器和修改器使用列名的 camelCase 变体，因此 getTitle() 方法检索 title 列的值。

要一次设置多个字段，可以使用为每个对象类生成的 fromArray() 方法，如清单 8-8 所示。

### 清单 8-8 - fromArray() 方法是一个多设置器

```
$article->fromArray(array(
    'Title' => 'My first article',
    'Content' => 'This is my very first article.\n Hope you enjoy it!',
));
```

fromArray() 方法有一个第二个参数 keyType。您可以通过额外传递以下类类型常量之一来指定数组的键类型：BasePeer::TYPE_PHPNAME、BasePeer::TYPE_STUDLYPHPNAME、BasePeer::TYPE_COLNAME、BasePeer::TYPE_FIELDNAME、BasePeer::TYPE_NUM。默认键类型为列的 PhpName（例如 'AuthorId'）。

## 检索相关记录

blog_comment 表中的 blog_article_id 列隐式定义了指向 blog_article 表的外键。每条评论关联一篇文章，一篇文章可以有多条评论。生成的类包含五种以面向对象方式转换此关系的方法，如下：

- $comment->getArticle()：获取相关的 Article 对象
- $comment->getArticleId()：获取相关 Article 对象的 ID
- $comment->setArticle($article)：定义相关的 Article 对象
- $comment->setArticleId($id)：从 ID 定义相关的 Article 对象
- $article->getComments()：获取相关的 Comment 对象

getArticleId() 和 setArticleId() 方法表明，您可以将 blog_article_id 列视为常规列并手动设置关系，但它们并不十分有趣。面向对象方法的优势在其他三种方法中更加明显。清单 8-9 展示了如何使用生成的 setter。

### 清单 8-9 - 外键被转换为特殊的 setter

```
$comment = new Comment();
$comment->setAuthor('Steve');
$comment->setContent('Gee, dude, you rock: best article ever!');

// Attach this comment to the previous $article object
$comment->setArticle($article);

// Alternative syntax
// Only makes sense if the object is already saved in the database
$comment->setArticleId($article->getId());
```

清单 8-10 展示了如何使用生成的 getter。它还演示了如何在模型对象上链式调用方法。

```
// Many to one relationship
echo $comment->getArticle()->getTitle();
=> My first article
echo $comment->getArticle()->getContent();
=> This is my very first article.
Hope you enjoy it!

// One to many relationship
$comments = $article->getComments();
```

getArticle() 方法返回一个 Article 类对象，该对象可使用 getTitle() 访问器。这比自己执行连接要好得多，后者可能需要几行代码（从 $comment->getArticleId() 调用开始）。

清单 8-10 中的 $comments 变量包含一个 Comment 类对象数组。您可以使用 $comments[0] 显示第一个，或使用 foreach ($comments as $comment) 遍历集合。

> 按照惯例，模型对象使用单数命名，现在您可以明白了。blog_comment 表中定义的外键会导致创建一个名为 getComments() 的方法，其名称是在 Comment 对象名称后加上 s。如果您给模型对象命名为复数，生成将导致一个名为 getCommentss() 的方法，这说不通。

## 保存和删除数据

通过调用 new 构造函数，您创建了一个新对象，但 blog_article 表中并没有实际记录。修改对象对数据库也没有影响。要将数据保存到数据库，需要调用对象的 save() 方法。

```
$article->save();
```

ORM 足够智能，能够检测对象之间的关系，因此保存 $article 对象也会保存相关的 $comment 对象。它还知道保存的对象在数据库中是否有现有对应项，因此 save() 调用有时会转换为 SQL INSERT，有时转换为 UPDATE。主键由 save() 方法自动设置，因此保存后，可以使用 $article->getId() 检索新主键。

> 您可以通过调用 isNew() 检查对象是否是新对象。如果您想知道对象是否已修改并值得保存，请调用其 isModified() 方法。

如果您阅读了文章中的评论，可能会改变对在互联网上发布的兴趣。如果您不欣赏文章审稿人的讽刺，可以轻松使用 delete() 方法删除评论，如清单 8-11 所示。

### 清单 8-11 - 使用相关对象上的 delete() 方法从数据库中删除记录

```
foreach ($article->getComments() as $comment)
{
  $comment->delete();
}
```





即使在调用 delete() 方法后，对象在请求结束前仍然可用。要判断对象在数据库中是否已删除，请调用 isDeleted() 方法。

## 通过主键检索记录

如果知道特定记录的主键，请使用同伴类的 retrieveByPk() 类方法来获取相关对象。

```
$article = ArticlePeer::retrieveByPk(7);
```

schema.yml 文件将 id 字段定义为 blog_article 表的主键，因此该语句实际上将返回 id 为 7 的文章。因为你使用了主键，你知道只会返回一条记录；$article 变量包含一个 Article 类的对象。

在某些情况下，主键可能包含多个列。在这些情况下，retrieveByPk() 方法接受多个参数，每个主键列对应一个参数。

你也可以根据主键选择多个对象，方法是调用生成的 retrieveByPks() 方法，它期望以主键数组作为参数。

## 使用条件检索记录

当你想要检索多条记录时，需要调用要检索的对象对应的同伴类的 doSelect() 方法。例如，要检索 Article 类的对象，请调用 ArticlePeer::doSelect()。

doSelect() 方法的第一个参数是 Criteria 类的一个对象，这是一个为实现数据库抽象而不使用 SQL 定义的简单查询定义类。

空的 Criteria 返回该类的所有对象。例如，清单 8-12 中所示的代码检索所有文章。

### 清单 8-12 - 使用 doSelect() 按条件检索记录——空条件

```
$c = new Criteria();
$articles = ArticlePeer::doSelect($c);
```

```
// Will result in the following SQL query
SELECT blog_article.ID, blog_article.TITLE, blog_article.CONTENT,
       blog_article.CREATED_AT
FROM   blog_article;
```

### 数据水合

调用 ::doSelect() 实际上比简单的 SQL 查询强大得多。首先，SQL 针对你选择的 DBMS 进行了优化。其次，传递给 Criteria 的任何值在集成到 SQL 代码之前都会被转义，从而防止 SQL 注入风险。第三，该方法返回对象数组，而不是结果集。ORM 会根据数据库结果集自动创建并填充对象。这个过程称为数据水合。

对于更复杂的对象选择，你需要 WHERE、ORDER BY、GROUP BY 等 SQL 语句的等价物。Criteria 对象拥有处理所有这些条件的方法和参数。例如，要获取 Steve 撰写的所有评论并按日期排序，请按清单 8-13 所示构建 Criteria。

### 清单 8-13 - 使用 doSelect() 按条件检索记录——带条件的 Criteria

```php
$c = new Criteria();
$c->add(CommentPeer::AUTHOR, 'Steve');
$c->addAscendingOrderByColumn(CommentPeer::CREATED_AT);
$comments = CommentPeer::doSelect($c);

// Will result in the following SQL query
SELECT blog_comment.ARTICLE_ID, blog_comment.AUTHOR, blog_comment.CONTENT,
    blog_comment.CREATED_AT
FROM   blog_comment
WHERE  blog_comment.author = 'Steve'
ORDER BY blog_comment.CREATED_AT ASC;
```

传递给 add() 方法作为参数的类常量引用属性名。它们以列名的大写形式命名。例如，要引用 blog_article 表的 content 列，请使用 ArticlePeer::CONTENT 类常量。

> 为什么要使用 CommentPeer::AUTHOR 而不是 blog_comment.AUTHOR？毕竟在 SQL 查询中输出的正是后者。假设你需要在数据库中将 author 字段重命名为 contributor。如果使用了 blog_comment.AUTHOR，你就必须在每次调用模型时都进行修改。另一方面，使用 CommentPeer::AUTHOR，你只需在 schema.yml 文件中更改列名，保持 phpName 为 AUTHOR，然后重建模型即可。

### 表 8-1 - SQL 与 Criteria 对象语法

| SQL | Criteria |
| --- | --- |
| WHERE column = value | ->add(column, value); |
| WHERE column <> value | ->add(column, value, Criteria::NOT_EQUAL); |
| **其他比较运算符** | |
| > , < | Criteria::GREATER_THAN, Criteria::LESS_THAN |
| >=, <= | Criteria::GREATER_EQUAL, Criteria::LESS_EQUAL |
| IS NULL, IS NOT NULL | Criteria::ISNULL, Criteria::ISNOTNULL |
| LIKE, ILIKE | Criteria::LIKE, Criteria::ILIKE |
| IN, NOT IN | Criteria::IN, Criteria::NOT_IN |
| **其他 SQL 关键字** | |
| ORDER BY column ASC | ->addAscendingOrderByColumn(column); |
| ORDER BY column DESC | - |
| | ->addDescendingOrderByColumn(column); |
| LIMIT limit | ->setLimit(limit) |
| OFFSET offset | ->setOffset(offset) |
| FROM table1, table2 WHERE table1.col1 = table2.col2 | ->addJoin(col1, col2) |
| FROM table1 LEFT JOIN table2 ON table1.col1 = table2.col2 | ->addJoin(col1, col2, Criteria::LEFT_JOIN) |
| FROM table1 RIGHT JOIN table2 ON table1.col1 = table2.col2 | ->addJoin(col1, col2, Criteria::RIGHT_JOIN) |

> 了解生成的类中有哪些方法可用的最佳方法，是在生成后查看 lib/model/om/ 文件夹中的 Base 文件。方法名称非常明确，但如果你需要更多关于它们的注释，请在 config/propel.ini 文件中将 propel.builder.addComments 参数设置为 true，然后重建模型。

### 清单 8-14 - 使用 doSelect() 按条件检索记录的另一个示例——带条件的 Criteria

```php
$c = new Criteria();
$c->add(CommentPeer::AUTHOR, 'Steve');
$c->addJoin(CommentPeer::ARTICLE_ID, ArticlePeer::ID);
$c->add(ArticlePeer::CONTENT, '%enjoy%', Criteria::LIKE);
$c->addAscendingOrderByColumn(CommentPeer::CREATED_AT);
$comments = CommentPeer::doSelect($c);
```

```
// Will result in the following SQL query
SELECT blog_comment.ID, blog_comment.ARTICLE_ID, blog_comment.AUTHOR,
       blog_comment.CONTENT, blog_comment.CREATED_AT
FROM   blog_comment, blog_article
WHERE  blog_comment.AUTHOR = 'Steve'
       AND blog_article.CONTENT LIKE '%enjoy%'
       AND blog_comment.ARTICLE_ID = blog_article.ID
ORDER BY blog_comment.CREATED_AT ASC
```

正如 SQL 是一种允许你构建非常复杂查询的简单语言一样，Criteria 对象可以处理任何复杂程度的条件。但由于许多开发者在将条件转换为面向对象逻辑之前会先用 SQL 思考，因此 Criteria 对象初学起来可能比较困难。理解它的最佳方法是从示例和示例应用中学习。例如，symfony 项目网站上有大量 Criteria 构建示例，能从多方面启发你。

除了 doSelect() 方法外，每个同伴类都有一个 doCount() 方法，它只需计算满足作为参数传递的条件的记录数量，并将计数作为整数返回。由于没有对象可返回，在这种情况下不会发生水合过程，且 doCount() 方法比 doSelect() 更快。

同伴类还提供 doDelete()、doInsert() 和 doUpdate() 方法，它们都需要一个 Criteria 作为参数。这些方法允许你向数据库发出 DELETE、INSERT 和 UPDATE 查询。有关这些 Propel 方法的更多详细信息，请查看模型中的生成的同伴类。

最后，如果你只想要返回的第一个对象，请将 doSelect() 替换为 doSelectOne() 调用。当你知道 Criteria 只会返回一个结果时，这可能就是你想要的情况，其优势在于该方法返回一个对象，而不是对象数组。

当 doSelect() 查询返回大量结果时，你可能希望在响应中只显示其中的一部分。Symfony 提供了一个名为 sfPropelPager 的分页器类，可自动处理结果的分页。

## 使用原始 SQL 查询

有时，你不想检索对象，而只想获取数据库计算的合成结果。例如，要获取所有文章的最新创建日期，检索所有文章并遍历数组毫无意义。你更希望让数据库只返回结果，因为这样可以跳过对象水合过程。

另一方面，你不想直接调用用于数据库管理的 PHP 命令，因为那样你将失去数据库抽象带来的好处。这意味着你需要绕过 ORM（Propel），但不能绕过数据库抽象（PDO）。

使用 PHP 数据对象（PDO）查询数据库需要执行以下步骤：

- 1. 获取数据库连接。
- 2. 构建查询字符串。
- 3. 基于它创建语句。
- 4. 遍历语句执行产生的结果集。

如果这些对你来说像天书一样难懂，清单 8-15 中的代码可能会更明确。

### 清单 8-15 - 使用 PDO 的自定义 SQL 查询

```php
$connection = Propel::getConnection();
$query = 'SELECT MAX(?) AS max FROM ?';
$statement = $connection->prepare($query);
$statement->bindValue(1, ArticlePeer::CREATED_AT);
$statement->bindValue(2, ArticlePeer::TABLE_NAME);
$statement->execute();
$resultset = $statement->fetch(PDO::FETCH_OBJ);
$max = $resultset->max;
```

与 Propel 查询一样，刚开始使用 PDO 查询时也很棘手。再次强调，来自现有应用程序和教程的示例将向你展示正确的方法。

如果你想跳过此过程并直接访问数据库，你将面临失去 Propel 提供的安全性和抽象性的风险。采用 Propel 的方式虽然更冗长，但它强制你使用良好的实践，以保证应用程序的性能、可移植性和安全性。对于包含来自不可信源（例如互联网用户）的参数的查询，这一点尤其正确。Propel 会执行所有必要的转义并保护你的数据库。直接访问数据库会使你面临 SQL 注入攻击的风险。

## 使用特殊日期列

通常，当表中有一个名为 created_at 的列时，它用于存储记录创建日期的时间戳。updated_at 列也是如此，每次更新记录本身时，都会将其更新为当前时间。

好消息是 symfony 会识别这些列的名称并为你处理它们的更新。你不需要手动设置 created_at 和 updated_at 列；它们会自动更新，如清单 8-16 所示。命名为 created_on 和 updated_on 的列也是如此。

### 清单 8-16 - created_at 和 updated_at 列会自动处理





```php
$comment = new Comment();
$comment->setAuthor('Steve');
$comment->save();

// Show the creation date
echo $comment->getCreatedAt();
=> [date of the database INSERT operation]
```

此外，日期列的获取器（getters）接受日期格式作为参数：

```php
echo $comment->getCreatedAt('Y-m-d');
```

## 重构到数据层

开发 symfony 项目时，你通常会先在操作（actions）中编写领域逻辑代码。但数据库查询和模型操作不应存储在控制器层。因此，所有与数据相关的逻辑都应移至模型层。每当你需要在操作中的多个位置执行相同的请求时，考虑将相关代码转移到模型中。这有助于保持操作简洁且易读。

例如，假设在博客中需要检索给定标签（作为请求参数传递）的十篇最热门文章的代码。这段代码不应放在操作中，而应放在模型中。事实上，如果你需要在模板中显示此列表，操作应如下所示：

```php
public function executeShowPopularArticlesForTag($request)
{
  $tag = TagPeer::retrieveByName($request->getParameter('tag'));
  $this->forward404Unless($tag);
  $this->articles = $tag->getPopularArticles(10);
}
```

操作从请求参数中创建 Tag 类的对象。然后，查询数据库所需的所有代码都位于该类的 getPopularArticles() 方法中。这使操作更易读，并且模型代码可以轻松在另一个操作中重复使用。

将代码移动到更合适的位置是重构技术之一。如果你经常这样做，你的代码将易于维护，并易于其他开发人员理解。关于何时进行数据层重构的一个好经验法则是，操作中的代码很少应包含超过十行 PHP 代码。

## 数据库连接

数据模型与所使用的数据库独立，但你肯定会使用数据库。symfony 向项目数据库发送请求所需的最少信息是数据库名称、凭据和数据库类型。这些连接设置可以通过将数据源名称（DSN）传递给 configure:database 任务来配置：

```bash
$ php symfony configure:database "mysql:host=localhost;dbname=blog" root mySecret
```

连接设置取决于环境。你可以使用 env 选项为应用程序中的 prod、dev 和 test 环境，或任何其他环境定义不同的设置：

```bash
Listing A-23
$ php symfony configure:database --env=dev
"mysql:host=localhost;dbname=blog_dev" root mySecret
```

此配置还可以按应用程序进行覆盖。例如，你可以使用此方法为前端和后端应用程序设置不同的安全策略，并在数据库中定义多个具有不同权限的数据库用户来处理此问题：

```bash
Listing A-24
$ php symfony configure:database --app=frontend
"mysql:host=localhost;dbname=blog" root mySecret
```

对于每个环境，你可以定义多个连接。每个连接都引用一个标记为相同名称的架构。使用的默认连接名称为 propel，它引用 Listing 8-3 中的 propel 架构。name 选项允许你创建另一个连接：

```bash
Listing A-25
$ php symfony configure:database --name=main
"mysql:host=localhost;dbname=example" root mySecret
```

你也可以手动在 config/ 目录下的 databases.yml 文件中输入这些连接设置。Listing 8-17 展示了此类文件的示例，Listing 8-18 展示了带有扩展表示法的同一示例。

### Listing 8-17 - 数据库连接简写设置

```yaml
Listing A-26
all:
  propel:
    class: sfPropelDatabase
    param:
      dsn: mysql://login:passwd@localhost/blog
```

### Listing 8-18 - 数据库连接示例设置，在 myproject/config/databases.yml 中

```yaml
Listing A-27
prod:
  propel:
    param:
      hostspec: mydataserver
      username: myusername
      password: xxxxxxxx
```

```yaml
all:
  propel:
    class: sfPropelDatabase
    param:
      phptype: mysql     # Database vendor
      hostspec: localhost
      database: blog
      username: login
      password: passwd
      port: 80
      encoding: utf8     # Default charset for table creation
      persistent: true   # Use persistent connections
```

phptype 参数允许的值是 PDO 支持的数据库系统的值：

- mysql
- mssql
- pgsql
- sqlite
- oracle

hostspec、database、username 和 password 是常规的数据库连接设置。

若要按应用程序覆盖配置，需要编辑应用程序特定的文件，例如 apps/frontend/config/databases.yml。

如果使用 SQLite 数据库，hostspec 参数必须设置为数据库文件的路径。例如，如果将博客数据库保存在 data/blog.db 中，databases.yml 文件将如 Listing 8-19 所示。

### Listing 8-19 - SQLite 的数据库连接设置，使用文件路径作为主机

```yaml
all:
  propel:
    class: sfPropelDatabase
    param:
      phptype: sqlite
      database: %SF_DATA_DIR%/blog.db
```

## 扩展模型

生成的模型方法很好，但通常不够。一旦实现自己的业务逻辑，就需要通过添加新方法或重写现有方法来扩展它。

### 添加新方法

你可以将新方法添加到 lib/model/ 目录中生成的空模型类中。使用 $this 调用当前对象的方法，使用 self:: 调用当前类的静态方法。请记住，自定义类从 lib/model/om/ 目录中的 Base 类继承方法。

例如，对于基于 Listing 8-3 生成的 Article 对象，你可以添加一个魔术 __toString() 方法，以便回显 Article 类的对象时显示其标题，如 Listing 8-20 所示。

### Listing 8-20 - 自定义模型，在 lib/model/Article.php 中

```php
class Article extends BaseArticle
{
    public function __toString()
    {
        return $this->getTitle(); // getTitle() is inherited from BaseArticle
    }
}
```

你还可以扩展 peer 类——例如，添加一个按创建日期检索所有文章的方法，如 Listing 8-21 所示。

### Listing 8-21 - 自定义模型，在 lib/model/ArticlePeer.php 中

```php
class ArticlePeer extends BaseArticlePeer
{
    public static function getAllOrderedByDate()
    {
        $c = new Criteria();
        $c->addAscendingOrderByColumn(self::CREATED_AT);

        return self::doSelect($c);
    }
}
```

新方法的使用方式与生成的方法相同，如 Listing 8-22 所示。

### Listing 8-22 - 使用自定义模型方法就像使用生成的方法一样

```php
foreach (ArticlePeer::getAllOrderedByDate() as $article)
{
 echo $article; // Will call the magic __toString() method
}
```

### 重写现有方法

如果 Base 类中的某些生成的方法不符合你的要求，你仍然可以在自定义类中重写它们。只需确保使用相同的方法签名（即相同的参数数量）。

例如，$article->getComments() 方法返回一个按无特定顺序排列的 Comment 对象数组。如果你希望按创建日期对结果进行排序，最新的评论排在前面，则重写 getComments() 方法，如 Listing 8-23 所示。请注意，原始的 getComments() 方法（位于 lib/model/om/BaseArticle.php 中）期望条件值和连接值作为参数，因此你的函数也必须如此。

### Listing 8-23 - 重写现有模型方法，在 lib/model/Article.php 中

```php
public function getComments($criteria = null, $con = null)
{
 if (is_null($criteria))
 {
 $criteria = new Criteria();
 }
 else
 {
 // Objects are passed by reference in PHP5, so to avoid modifying the
 original, you must clone it
 $criteria = clone $criteria;
 }

 $criteria->addDescendingOrderByColumn(CommentPeer::CREATED_AT);

 return parent::getComments($criteria, $con);
}
```

自定义方法最终会调用父类 Base 类的方法，这是良好做法。但是，你可以完全绕过它并返回你想要的结果。

### 使用模型行为

某些模型修改是通用的，可以重复使用。例如，使模型对象可排序以及乐观锁以防止并发对象保存之间冲突的方法，都是可以添加到许多类中的通用扩展。





Symfony 将这些扩展打包为行为。行为是提供额外方法给模型类的外部类。模型类中已包含钩子，而 symfony 知道如何扩展它们。

要在模型类中启用行为，必须修改 config/propel.ini 文件中的一项设置：

```
propel.builder.AddBehaviors = true    // Default value is false
```

symfony 默认未捆绑任何行为，但可以通过插件安装。安装行为插件后，只需一行代码即可将行为分配给类。例如，如果在你的应用中安装了 sfPropelParanoidBehaviorPlugin，可以通过在 Article.class.php 末尾添加以下内容，使用此行为扩展 Article 类：

```
sfPropelBehavior::add('Article', array(
  'paranoid' => array('column' => 'deleted_at')
));
```

重建模型后，被删除的 Article 对象将保留在数据库中，对使用 ORM 的查询不可见，除非你使用 sfPropelParanoidBehavior::disable() 临时禁用该行为。

或者，你也可以直接在 schema.yml 中声明行为，方法是将它们列在 _behaviors 键下（参见下文的清单 8-34）。

在官方仓库中查看 symfony 插件列表，以查找行为。每个插件都有自己的文档和安装指南。

## 扩展架构语法

schema.yml 文件可以很简单，如清单 8-3 所示。但关系模型通常很复杂。这就是为什么架构具有广泛的语法，能够处理几乎所有情况。

### 属性

连接和表可以具有特定属性，如清单 8-24 所示。它们在 _attributes 键下设置。

### 清单 8-24 - 连接和表的属性

```
propel:
  _attributes: { noXsd: false, defaultIdMethod: none, package: lib.model }
  blog_article:
    _attributes: { phpName: Article }
```

你可能希望在代码生成之前验证架构。为此，请禁用连接的 noXSD 属性。连接还支持 defaultIdMethod 属性。如果未提供，则将使用数据库的本机 ID 生成方法——例如，MySQL 的自增，或 PostgreSQL 的序列。另一个可能的值是 none。

package 属性类似于命名空间；它确定存储生成类的路径。它默认为 lib/model/，但你可以更改它以在子包中组织模型。例如，如果你不想将核心业务类和定义数据库存储统计引擎的类放在同一目录中，那么请定义两个架构，分别使用 lib.model.business 和 lib.model.stats 包。

你已经看到了 phpName 表属性，用于设置与表映射的生成类的名称。

包含本地化内容的表（即在相关表中有几个版本的内容，用于国际化）还接受两个额外属性（详情见第 13 章），如清单 8-25 所示。

### 清单 8-25 - i18n 表的属性

```
propel:
  blog_article:
    _attributes: { isI18N: true, i18nTable: db_group_i18n }
```

## 处理多个架构

每个应用程序可以有多个架构。Symfony 会考虑 `config/` 文件夹中所有以 `schema.yml` 或 `schema.xml` 结尾的文件。如果你的应用程序有许多表，或者某些表不共享相同的连接，你会发现这种方法非常有用。

考虑这两个架构：

```
// In config/business-schema.yml
propel:
  blog_article:
    _attributes: { phpName: Article }
    id:
    title: varchar(50)

// In config/stats-schema.yml
propel:
  stats_hit:
    _attributes: { phpName: Hit }
    id:
    resource: varchar(100)
    created_at:
```

两个架构共享相同的连接（propel），`Article` 和 `Hit` 类将在相同的 `lib/model/` 目录下生成。一切都就像你只编写了一个架构一样。

你还可以让不同的架构使用不同的连接（例如 propel 和 propel_bis，需在 `databases.yml` 中定义），并将生成的类组织在子目录中：

```
// In config/business-schema.yml
propel:
  blog_article:
    _attributes: { phpName: Article, package: lib.model.business }
    id:
    title: varchar(50)

// In config/stats-schema.yml
propel_bis:
  stats_hit:
    _attributes: { phpName: Hit, package: lib.model.stat }
    id:
    resource: varchar(100)
    created_at:
```

许多应用程序使用多个架构。特别是，某些插件有自己的架构和包，以避免与你自己的类混淆（详情见第 17 章）。

## 列详情

基本语法为你提供两种选择：让 symfony 根据列名推断列特征（通过给出空值），或使用类型关键字定义类型。清单 8-26 演示了这些选择。

### 清单 8-26 - 基本列属性

```
propel:
  blog_article:
    id: ~ # Let symfony do the work
    title: varchar(50) # Specify the type yourself
```

但你可以为列定义更多内容。如果这样做，则需要将列设置定义为关联数组，如清单 8-27 所示。

### 清单 8-27 - 复杂列属性

```
propel:
  blog_article:
    id: { type: integer, required: true, primaryKey: true,
      autoIncrement: true }
    name: { type: varchar(50), default: foobar, index: true }
    group_id: { type: integer, foreignTable: db_group, foreignReference:
      id, onDelete: cascade }
```

列参数如下：

- * type: 列类型。可选值包括 boolean、tinyint、smallint、integer、bigint、double、float、real、decimal、char、varchar(size)、longvarchar、date、time、timestamp、bu_date、bu_timestamp、blob 和 clob。
- * required: 布尔值。如果希望列为必填，请将其设置为 true。
- * size: 支持该类型的字段的大小或长度。
- * scale: 用于 decimal 数据类型的小数位数（必须同时指定 size）。
- * default: 默认值。
- * primaryKey: 布尔值。对于主键，请将其设置为 true。
- * autoIncrement: 布尔值。对于需要自增值的 integer 类型列，请将其设置为 true。
- * sequence: 使用序列实现 autoIncrement 列的数据库的序列名称（例如，PostgreSQL 和 Oracle）。
- * index: 布尔值。如果希望创建简单索引，请将其设置为 true；如果希望在列上创建唯一索引，请将其设置为 unique。
- * foreignTable: 表名，用于创建指向另一张表的外键。
- * foreignReference: 如果通过 foreignTable 定义外键，则为相关列的名称。
- * onDelete: 确定删除相关表中的记录时要触发的操作。设置为 setnull 时，外键列将设置为 null。设置为 cascade 时，记录将被删除。如果数据库引擎不支持该行为，ORM 将对其模拟。这仅适用于带有 foreignTable 和 foreignReference 的列。
- * isCulture: 布尔值。对于本地化内容表中的文化列，请将其设置为 true（参见第 13 章）。

## 外键

作为 foreignTable 和 foreignReference 列属性的替代方案，你可以在表中 `_foreignKeys:` 键下添加外键。清单 8-28 中的架构将在 user_id 列上创建一个外键，与 blog_user 表中的 id 列匹配。

### 清单 8-28 - 外键替代语法

```
propel:
  blog_article:
    id: ~
    title: varchar(50)
    user_id: { type: integer }
    _foreignKeys:
        -
            foreignTable: blog_user
            onDelete: cascade
            references:
                - { local: user_id, foreign: id }
```

替代语法适用于多引用外键，并可为外键命名，如清单 8-29 所示。

### 清单 8-29 - 应用于多引用外键的外键替代语法

```
_foreignKeys:
    my_foreign_key:
        foreignTable: db_user
        onDelete: cascade
        references:
            - { local: user_id, foreign: id }
            - { local: post_id, foreign: id }
```

## 索引

作为 index 列属性的替代方案，你可以在表中 `_indexes:` 键下添加索引。如果要定义唯一索引，则必须改用 `_uniques:` 标题。对于需要指定大小的列（因为它们是文本列），索引的大小的指定方式与使用括号指定列长度相同。清单 8-30 显示了索引的替代语法。

### 清单 8-30 - 索引和唯一索引的替代语法

```
propel:
    blog_article:
        id:        ~
        title:     varchar(50)
        created_at:
        _indexes:
            my_index:       [title(10), user_id]
            _uniques:
                my_other_index: [created_at]
```

替代语法仅适用于在多个列上构建的索引。

## 空列

当遇到没有值的列时，symfony 会执行一些“魔法”并自行添加一个值。有关添加到空列的详细信息，请参见清单 8-31。

### 清单 8-31 - 从列名推断的列详细信息

```
// Empty columns named id are considered primary keys
id: { type: integer, required: true, primaryKey: true,
      autoIncrement: true }

// Empty columns named XXX_id are considered foreign keys
foobar_id: { type: integer, foreignTable: db_foobar, foreignReference: id
}
```



```
// Empty columns named created_at, updated_at, created_on and updated_on
// are considered dates and automatically take the timestamp type
created_at: { type: timestamp }
updated_at: { type: timestamp }
```

对于外键，symfony 会查找具有与列名开头相同 phpName 的表，如果找到一个，则将此表名作为 foreignTable。

## I18n 表

Symfony 支持关联表中的内容国际化。这意味着当你有需要进行国际化的内容时，它会存储在两个独立的表中：一个包含不变列，另一个包含国际化列。

在 schema.yml 文件中，当你将表命名为 foobar_i18n 时，会隐含所有这些内容。例如，清单 8-32 所示的架构会自动用列和表属性进行补全，以使国际化内容机制正常工作。在内部，symfony 会将其理解为如清单 8-33 所写。第 13 章将介绍更多关于 i18n 的内容。

清单 8-32 - 隐含的 i18n 机制

```
propel:
  db_group:
    id:         ~
    created_at: ~

  db_group_i18n:
    name:       varchar(50)
```

清单 8-33 - 显式 i18n 机制

```
propel:
  db_group:
    _attributes: { isI18N: true, i18nTable: db_group_i18n }
    id:          ~
    created_at:  ~

db_group_i18n:
  id:          { type: integer, required: true, primaryKey:
               true,foreignTable: db_group, foreignReference: id, onDelete: cascade }
  culture:     { isCulture: true, type: varchar(7), required:
               true,primaryKey: true }
  name:        varchar(50)
```

## 行为

行为是由插件提供的模型修饰符，可为你的 Propel 类添加新功能。第 17 章将详细介绍行为。你可以直接在架构中定义行为，即在 _behaviors 键下为每个表列出行为及其参数。清单 8-34 通过将 paranoid 行为扩展到 BlogArticle 类来给出一个示例。

清单 8-34 - 行为声明

```
propel:
  blog_article:
    title:       varchar(50)

_behaviors:
  paranoid: { column: deleted_at }
```

## 超越 schema.yml：schema.xml

实际上，schema.yml 格式是 symfony 内部使用的。当你调用 propel 命令时，symfony 实际上会将此文件翻译为生成的 schema.xml 文件，这是 Propel 实际对模型执行任务所期望的文件类型。

schema.xml 文件包含与其 YAML 等价文件相同的信息。例如，清单 8-3 转换为清单 8-35 所示的 XML 文件。

清单 8-35 - 示例 schema.xml，对应清单 8-3

```
<?xml version="1.0" encoding="UTF-8"?>
<database name="propel" defaultIdMethod="native" noXsd="true"
 package="lib.model">
 <table name="blog_article" phpName="Article">
  <column name="id" type="integer" required="true"
   primaryKey="true"autoIncrement="true" />
  <column name="title" type="varchar" size="255" />
  <column name="content" type="longvarchar" />
  <column name="created_at" type="timestamp" />
 </table>
 <table name="blog_comment" phpName="Comment">
  <column name="id" type="integer" required="true"
   primaryKey="true"autoIncrement="true" />
  <column name="article_id" type="integer" />
  <foreign-key foreignTable="blog_article">
   <reference local="article_id" foreign="id"/>
  </foreign-key>
  <column name="author" type="varchar" size="255" />
  <column name="content" type="longvarchar" />
  <column name="created_at" type="timestamp" />
 </table>
</database>
```

schema.xml 格式的说明可以在 Propel 项目网站的文档和“入门”部分中找到（第 70 页）。

YAML 格式的设计旨在保持架构简单易读易写，但权衡是最复杂的架构无法用 schema.yml 文件描述。另一方面，XML 格式允许完整的架构描述，无论其复杂程度如何，并且包含数据库厂商特定的设置、表继承等等。

symfony 实际上可以理解以 XML 格式编写的架构。因此，如果你的架构对于 YAML 语法来说太复杂，或者你已有现成的 XML 架构，又或者你已经熟悉 Propel XML 语法，那么你无需切换到 symfony YAML 语法。将你的 schema.xml 放在项目 config/ 目录下，构建模型，就大功告成了。

## symfony 中的 Propel

本章介绍的所有细节并非 symfony 特有，而是属于 Propel。Propel 是 symfony 首选的对象/关系抽象层，但你可以选择其他替代方案。不过，symfony 与 Propel 配合得更加无缝，原因如下：

所有对象数据模型类和 Criteria 类都是自动加载类。一旦使用它们，symfony 就会包含正确的文件，你无需手动添加文件引入语句。在 symfony 中，Propel 无需启动或初始化。当对象使用 Propel 时，库会自行启动。某些 symfony 助手使用 Propel 对象作为参数来完成高级任务（例如分页或过滤）。Propel 对象可让你为应用程序快速构建原型并生成后端（第 14 章提供了更多详细信息）。通过 schema.yml 文件编写架构更快。

而且，由于 Propel 与所使用的数据库无关，symfony 也是如此。

### 不要重复创建模型

使用 ORM 的权衡在于你必须定义两次数据结构：一次用于数据库，一次用于对象模型。幸运的是，symfony 提供命令行工具，可以基于另一个生成其中一个，从而避免重复工作。

### 基于现有架构构建 SQL 数据库结构

如果你先编写 `schema.yml` 文件来启动应用程序，symfony 可以生成一个 SQL 查询，直接从 YAML 数据模型创建表。要使用该查询，请进入项目根目录并键入此命令：

清单 A-49

```
$ php symfony propel:build-sql
```

将在 `myproject/data/sql/` 中创建一个 `lib.model.schema.sql` 文件。请注意，生成的 SQL 代码将针对 `propel.ini` 文件中 `phptype` 参数定义的数据库系统进行优化。

你可以直接使用 `schema.sql` 文件来构建表。例如，在 MySQL 中，键入此命令：

清单 A-50

```
$ mysqladmin -u root -p create blog
$ mysql -u root -p blog < data/sql/lib.model.schema.sql
```

生成的 SQL 也有助于在其他环境中重建数据库，或切换到另一个 DBMS。如果你的 `propel.ini` 中正确定义了连接设置，你甚至可以使用 `php symfony propel:insert-sql` 命令自动完成此操作。

> 命令行还提供一个任务，用于基于文本文件向数据库填充数据。有关 `propel:data-load` 任务和 YAML 固定装置文件的更多信息，请参见第 16 章。

### 从现有数据库生成 YAML 数据模型

symfony 可以使用 Propel 从现有数据库生成 `schema.yml` 文件，这得益于内省（数据库确定其正在操作的表结构的能力）。在进行逆向工程时，或者如果你更愿意先处理数据库再处理对象模型时，这特别有用。

为此，你需要确保项目的 databases.yml 文件指向正确的数据库并包含所有连接设置，然后调用 propel:build-schema 命令：

```
$ php symfony propel:build-schema
```

将根据你的数据库结构生成一个全新的 schema.yml 文件，位于 config/ 目录中。你可以基于此架构构建模型。

架构生成命令非常强大，可以向架构添加大量依赖数据库的信息。由于 YAML 格式不处理此类厂商信息，你需要生成 XML 架构才能利用它。你只需在 build-schema 任务中添加 xml 参数即可：

```
$ php symfony propel:build-schema --xml
```

此操作不会生成 schema.yml 文件，而是创建一个与 Propel 完全兼容的 schema.xml 文件，包含所有厂商信息。但请注意，生成的 XML 架构往往非常冗长且难以阅读。

## propel.ini 配置

此文件包含用于配置 Propel 生成器的其他设置，以使生成的模型类与 symfony 兼容。大多数设置是内部的，对用户无关紧要，只有少数例外：

```
// Base classes are autoloaded in symfony
// Set this to true to use include_once statements instead
// (Small negative impact on performance)
propel.builder.addIncludes = false
```

```
// Generated classes are not commented by default
// Set this to true to add comments to Base classes
// (Small negative impact on performance)
propel.builder.addComments = false
```

```
// Behaviors are not handled by default
// Set this to true to be able to handle them
propel.builder.AddBehaviors = false
```

修改 propel.ini 设置后，不要忘记重建模型，以便更改生效。

## 总结

symfony 将 Propel 用作 ORM，将 PHP Data Objects 用作数据库抽象层。这意味着在生成对象模型类之前，你必须先用 YAML 描述数据库的关系架构。然后，在运行时，使用对象类和 peer 类的方法来检索关于单条或多条记录的信息。你可以通过向自定义类添加方法来轻松重写它们并扩展模型。连接设置定义在 databases.yml 文件中，该文件可以支持多个连接。命令行包含特殊任务，以避免重复定义结构。





模型层是 Symfony 框架中最复杂的一层。造成这种复杂性的一个原因是，数据操纵是一件复杂的事情。相关的安全问题对网站至关重要，不应被忽视。另一个原因是，Symfony 更适合企业环境中的中大型应用程序。在这样的应用程序中，Symfony 模型提供的自动化实际上代表了时间上的收益，值得投入精力去学习其内部原理。

所以，不要犹豫，花些时间测试模型对象和方法，以便完全理解它们。您的应用程序的稳健性和可扩展性将是巨大的回报。

# 附录 B

## GNU 自由文档许可证

- 版本 1.2，2002 年 11 月
- 版权所有 © 2000, 2001, 2002 自由软件基金会，Inc.
- 51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA

任何人均获准复制和分发本许可证文件的逐字副本，但不得修改。

### 0. 前言

本许可证的目的是使手册、教科书或其他功能性和有用的文档在“自由”的意义上成为“免费”：确保每个人都有效地享有复制和再分发的自由，无论是否修改，无论是商业还是非商业用途。其次，本许可证为作者和出版商保留了一种为其工作获得认可的方式，同时不因他人所做的修改而承担责任。

本许可证是一种“左版权”，这意味着文档的衍生作品本身也必须以同样的意义成为自由的。它补充了 GNU 通用公共许可证，后者是专为自由软件设计的左版权许可证。

我们设计本许可证是为了将其用于自由软件的手册，因为自由软件需要自由文档：自由程序应附带提供与软件相同自由的手册。但本许可证不仅限于软件手册；它可以用于任何文本作品，无论主题如何或是否以印刷书籍形式出版。我们主要推荐本许可证用于以教学或参考为目的的作品。

### 1. 适用性和定义

本许可证适用于任何介质中的任何手册或其他作品，只要其中包含版权持有人放置的声明，表明该作品可根据本许可证的条款进行分发。此类声明授予一项全球性的、免版税的、期限无限的许可，以在此处所述条件下使用该作品。下文中的“文档”指任何此类手册或作品。公众中的任何成员都是被许可人，并被称为“你”。如果您以需要版权法许可的方式复制、修改或分发该作品，则表示您接受该许可证。

文档的“修改版”指包含文档或其部分的任何作品，无论是逐字复制，还是进行修改和/或翻译成另一种语言。

“附属章节”是指文档中专门处理文档的出版者或作者与文档整体主题（或相关事项）之间关系的命名附录或前置部分，且不包含可能直接属于该整体主题的任何内容。（因此，如果文档部分是数学教科书，附属章节不得解释任何数学。）该关系可能是与主题或相关事项的历史联系，也可能是关于它们的法律、商业、哲学、伦理或政治立场。

“不变章节”是某些附属章节，其标题在声明文档根据本许可证发布的通知中被指定为不变章节。如果一个章节不符合上述附属章节的定义，则不得将其指定为不变章节。文档可能包含零个不变章节。如果文档未标识任何不变章节，则不存在不变章节。

“封面文字”是在声明文档根据本许可证发布的通知中列出的某些简短文本段落，作为封面文字或封底文字列出。封面文字最多可包含 5 个单词，封底文字最多可包含 25 个单词。

文档的“透明”副本是指机器可读的副本，其表示格式的规范向公众开放，适于使用通用文本编辑器（或针对由像素组成的图像使用通用绘图程序，或针对绘图使用一些广泛可用的绘图编辑器）直接修改文档，并适于输入到文本格式化程序或自动翻译成多种适于输入到文本格式化程序的格式。以其他方式为透明文件格式制作的副本，但其标记或标记的缺失已被安排为阻碍或阻止读者随后修改，则不属于透明副本。如果图像格式用于大量文本，则不属于透明格式。不是“透明”的副本称为“不透明”副本。

适用于透明副本的适当格式示例包括无标记的纯 ASCII、Texinfo 输入格式、LaTeX 输入格式、使用公开可用 DTD 的 SGML 或 XML，以及为人工修改设计的符合标准的简单 HTML、PostScript 或 PDF。透明图像格式示例包括 PNG、XCF 和 JPG。不透明格式包括仅可由专有字处理器读取和编辑的专有格式、其 DTD 和/或处理工具通常不可用的 SGML 或 XML，以及某些字处理器仅为输出目的生成的机器生成的 HTML、PostScript 或 PDF。

对于印刷书籍，“标题页”是指标题页本身，加上为清晰容纳本许可证要求出现在标题页上的材料而需要的后续页面。对于没有标题页的格式的作品，“标题页”是指作品标题最突出出现位置附近的文本，位于正文开始之前。

“标题为 XYZ”的章节是指文档的命名子单元，其标题恰好是 XYZ，或包含紧跟在用另一种语言翻译 XYZ 的文本后的括号中的 XYZ。（此处 XYZ 代表下文提到的特定章节名称，例如“致谢”、“献词”、“背书”或“历史”。）当您修改文档时，保留此类章节的“标题”意味着它仍按此定义为“标题为 XYZ”的章节。

文档可以在声明本许可证适用于文档的通知旁边包含免责声明。这些免责声明被视为通过引用包含在本许可证中，但仅限于免除保修：这些免责声明可能具有的任何其他含义均无效，不影响本许可证的含义。

### 2. 逐字复制

您可以以任何介质复制和分发文档，无论是商业还是非商业用途，前提是将本许可证、版权通知以及说明本许可证适用于文档的许可证通知复制在所有副本中，并且您不得向本许可证的条款添加任何其他条件。您不得使用技术手段阻碍或控制您制作或分发的副本的阅读或进一步复制。但是，您可以接受复制品的补偿。如果您分发足够数量的副本，还必须遵守第 3 节的条件。

您还可以在上述相同条件下借出副本，并且可以公开展示副本。

### 3. 大量复制

如果您出版文档的印刷副本（或通常带有印刷封面的介质中的副本），数量超过 100，且文档的许可证通知要求封面文字，则必须将副本装入封面中，封面上要清晰、易读地包含所有这些封面文字：封面文字放在前封上，封底文字放在封底上。两个封面都必须清晰、易读地标明您是这些副本的出版者。前封必须呈现完整的标题，标题中的所有单词都要同样突出且可见。您可以在封面上添加其他材料。

仅对封面进行更改的复制，只要保留文档的标题并满足这些条件，在其他方面可以视为逐字复制。

如果任一封面所需的文本太长而无法清晰容纳，则应将首先列出的文本（尽可能多地合理容纳）放在实际封面上，并将其余部分继续放在相邻页面上。

如果您出版或分发文档的不透明副本，数量超过 100，则必须要么随每个不透明副本附带一份机器可读的透明副本，要么在每个不透明副本中或随其说明一个计算机网络位置，普通网络使用公众可从此位置使用公共标准网络协议下载文档的完整透明副本，且不包含添加的材料。如果您使用后一种选项，则在开始大量分发不透明副本时，必须采取合理谨慎的措施，以确保此透明副本在所述位置保持可访问状态，直到您向公众分发该版本的最后一次不透明副本（直接或通过您的代理人或零售商）后至少一年。

建议但不要求，您在重新分发大量副本之前尽早联系文档的作者，以便他们有机会向您提供文档的更新版本。

### 4. 修改

您可以在上述第 2 节和第 3 节的条件下复制和分发文档的修改版，前提是您根据本许可证发布修改版，由修改版承担文档的角色，从而授予拥有修改版副本的任何人分发和修改修改版的许可。此外，您在修改版中必须做到以下事项：

- 在标题页（以及封面，如果有的话）中使用与文档以及先前版本（如果有的话）不同的标题，（这些先前版本）应当……


listed in the History section of the Document). You may use the same title as a previous version if the original publisher of that version gives permission.

- List on the Title Page, as authors, one or more persons or entities responsible for authorship of the modifications in the Modified Version, together with at least five of the principal authors of the Document (all of its principal authors, if it has fewer than five), unless they release you from this requirement.
- State on the Title page the name of the publisher of the Modified Version, as the publisher.
- Preserve all the copyright notices of the Document.
- Add an appropriate copyright notice for your modifications adjacent to the other copyright notices.
- Include, immediately after the copyright notices, a license notice giving the public permission to use the Modified Version under the terms of this License, in the form shown in the Addendum below.
- Preserve in that license notice the full lists of Invariant Sections and required Cover Texts given in the Document’s license notice.
- Include an unaltered copy of this License.
- Preserve the section Entitled “History”, Preserve its Title, and add to it an item stating at least the title, year, new authors, and publisher of the Modified Version as given on the Title Page. If there is no section Entitled “History” in the Document, create one stating the title, year, authors, and publisher of the Document as given on its Title Page, then add an item describing the Modified Version as stated in the previous sentence.
- Preserve the network location, if any, given in the Document for public access to a Transparent copy of the Document, and likewise the network locations given in the Document for previous versions it was based on. These may be placed in the “History” section. You may omit a network location for a work that was published at least four years before the Document itself, or if the original publisher of the version it refers to gives permission.
- For any section Entitled “Acknowledgements” or “Dedications”, Preserve the Title of the section, and preserve in the section all the substance and tone of each of the contributor acknowledgements and/or dedications given therein.
- Preserve all the Invariant Sections of the Document, unaltered in their text and in their titles. Section numbers or the equivalent are not considered part of the section titles.
- Delete any section Entitled “Endorsements”. Such a section may not be included in the Modified Version.
- Do not retitle any existing section to be Entitled “Endorsements” or to conflict in title with any Invariant Section.
- Preserve any Warranty Disclaimers.

If the Modified Version includes new front-matter sections or appendices that qualify as Secondary Sections and contain no material copied from the Document, you may at your option designate some or all of these sections as invariant. To do this, add their titles to the list of Invariant Sections in the Modified Version’s license notice. These titles must be distinct from any other section titles.

You may add a section Entitled “Endorsements”, provided it contains nothing but endorsements of your Modified Version by various parties—for example, statements of peer review or that the text has been approved by an organization as the authoritative definition of a standard.

You may add a passage of up to five words as a Front-Cover Text, and a passage of up to 25 words as a Back-Cover Text, to the end of the list of Cover Texts in the Modified Version. Only one passage of Front-Cover Text and one of Back-Cover Text may be added by (or through arrangements made by) any one entity. If the Document already includes a cover text for the same cover, previously added by you or by arrangement made by the same entity you are acting on behalf of, you may not add another; but you may replace the old one, on explicit permission from the previous publisher that added the old one.

The author(s) and publisher(s) of the Document do not by this License give permission to use their names for publicity for or to assert or imply endorsement of any Modified Version.

## 5. COMBINING DOCUMENTS

You may combine the Document with other documents released under this License, under the terms defined in section 4 above for modified versions, provided that you include in the combination all of the Invariant Sections of all of the original documents, unmodified, and list them all as Invariant Sections of your combined work in its license notice, and that you preserve all their Warranty Disclaimers.

The combined work need only contain one copy of this License, and multiple identical Invariant Sections may be replaced with a single copy. If there are multiple Invariant Sections with the same name but different contents, make the title of each such section unique by adding at the end of it, in parentheses, the name of the original author or publisher of that section if known, or else a unique number. Make the same adjustment to the section titles in the list of Invariant Sections in the license notice of the combined work.

In the combination, you must combine any sections Entitled “History” in the various original documents, forming one section Entitled “History”; likewise combine any sections Entitled “Acknowledgements”, and any sections Entitled “Dedications”. You must delete all sections Entitled “Endorsements”.

## 6. COLLECTIONS OF DOCUMENTS

You may make a collection consisting of the Document and other documents released under this License, and replace the individual copies of this License in the various documents with a single copy that is included in the collection, provided that you follow the rules of this License for verbatim copying of each of the documents in all other respects.

You may extract a single document from such a collection, and distribute it individually under this License, provided you insert a copy of this License into the extracted document, and follow this License in all other respects regarding verbatim copying of that document.

## 7. AGGREGATION WITH INDEPENDENT WORKS

A compilation of the Document or its derivatives with other separate and independent documents or works, in or on a volume of a storage or distribution medium, is called an “aggregate” if the copyright resulting from the compilation is not used to limit the legal rights of the compilation’s users beyond what the individual works permit. When the Document is included in an aggregate, this License does not apply to the other works in the aggregate which are not themselves derivative works of the Document.

If the Cover Text requirement of section 3 is applicable to these copies of the Document, then if the Document is less than one half of the entire aggregate, the Document’s Cover Texts may be placed on covers that bracket the Document within the aggregate, or the electronic equivalent of covers if the Document is in electronic form. Otherwise they must appear on printed covers that bracket the whole aggregate.

## 8. TRANSLATION

Translation is considered a kind of modification, so you may distribute translations of the Document under the terms of section 4. Replacing Invariant Sections with translations requires special permission from their copyright holders, but you may include translations of some or all Invariant Sections in addition to the original versions of these Invariant Sections. You may include a translation of this License, and all the license notices in the Document, and any Warranty Disclaimers, provided that you also include the original English version of this License and the original versions of those notices and disclaimers. In case of a disagreement between the translation and the original version of this License or a notice or disclaimer, the original version will prevail.

If a section in the Document is Entitled “Acknowledgements”, “Dedications”, or “History”, the requirement (section 4) to Preserve its Title (section 1) will typically require changing the actual title.

## 9. TERMINATION

You may not copy, modify, sublicense, or distribute the Document except as expressly provided for under this License. Any other attempt to copy, modify, sublicense or distribute the Document is void, and will automatically terminate your rights under this License. However, parties who have received copies, or rights, from you under this License will not have their licenses terminated so long as such parties remain in full compliance.

## 10. FUTURE REVISIONS OF THIS LICENSE

The Free Software Foundation may publish new, revised versions of the GNU Free Documentation License from time to time. Such new versions will be similar in spirit to the present version, but may differ in detail to address new problems or concerns. See http://www.gnu.org/copyleft/71.

Each version of the License is given a distinguishing version number. If the Document specifies that a particular numbered version of this License “or any later version” applies to it, you have the option of following the terms and conditions either of that specified version or of any later version that has been published (not as a draft) by the Free Software Foundation. If the Document does not specify a version number of this License, you may choose any version ever published (not as a draft) by the Free Software Foundation.





## 我们为高要求人群出版开源图书

向开源专家学习

![](img/0f886a7f4cbcc3939be96e985ca35ff4_392_0.png)

在 http://books.sensiolabs.com/ 上发现更多书名

## 了解更多开源技术

接受开源专家的培训

![](img/0f886a7f4cbcc3939be96e985ca35ff4_394_0.png)

立即访问 http://trainings.sensiolabs.com/，下次培训节省 10%

**优惠码** `BOOKS305` 优惠有效期至 09/30/2010

