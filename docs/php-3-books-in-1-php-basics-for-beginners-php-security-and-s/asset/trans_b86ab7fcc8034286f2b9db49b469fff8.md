
```
"carteProductname"=>"Tea",
"carteProductprice"=>"1.2",
"carteProductdescription"=>"black tea"));
$stub->expects($this->any())
->method('get_All_Carte_Products')
->will($this->returnValue($output));
$this->assertNotNull($stub->get_All_Carte_Products('1'));
}
}
?>
```

执行前例中的 PHPUnit_Framework_TestCase 方法 getMock()，要模拟一个类我们必须提供标题“carte。该方法构建一个类，然后从中动态构造一个实例。之后，mock 对象被保存到 $stub 中。我们重写函数 getAllCarteProducts。这些几行代码至关重要：

```
<?PHP
$stub->expects($this->any())
->method(' get_Carte_All_Carte_Products ')
->will($this->returnValue($output));
?>
```

上面这些代码行，也称为流畅接口，指示 stub 对象每当调用 getAllCarteProducts 方法时，应返回 $result 中的值而不是原值。expect() 方法包含在 PHPUnit 自动创建的 Mock（和 Stub）对象中，如上所示。expects() 方法需要一个匹配器对象。匹配器指定特定方法必须被调用的次数或期望的基数。any() 便捷方法在相关方法被调用零次或多次时通知 expect() 方法匹配失败。这对于返回值的 stub 实例而无需进行调用测试非常有用。

以下是一些 TestCase 匹配器方法：

| 测试用例 | 方法描述 |
|---|---|
| never() | 相关过程未被调用。 |
| any() | 相关方法被调用零次或多次。 |
| atLeastOnce() | 相关方法被调用一次或多次。 |
| exactly($num) | 相关过程被调用 $num 次。 |
| Once() | 相关方法仅被调用一次。 |

我们将展示如何在不使用任何插件的情况下从 Eclipse 中执行 PHPUnit。开始时，启动 Eclipse。对我们的餐厅 carte 项目进行单元测试。将餐厅项目的代码文件保存在项目工作区中的名为 "source" 的文件夹中。同样，在项目工作区内为单元测试创建一个文件夹并命名为 "test"。PHPUnit 可执行文件通常位于 Mac 上的 /usr/local/bin/PHPunit.exe 目录中。

在此我们让读者熟悉 PHPUnit 及其一些重要功能。有关更多详细信息，请参考官方 PHPUnit 资料：http://www.PHPunit.de/manual/current/en/PHPunit-book.pdf。此外，该书籍在 www.PHPunit.de 上也有法语和日语版本。

现在让我们将此应用程序添加到存储库中。输入您的提示，将 ' your_user_name ' 替换为您的个人用户名：

```
$ svn import carte_proj file:///Users/user_name/svnrepos/carte_proj -m "Initial import"
```

**output:**

添加 Staff.PHP

已提交修订版本 1。

这完成了将文件夹 'proj_restaurant' 导入到存储库 'svnrepos' 的操作。“revision” 是标识存储库中每个版本的唯一编号。始终包含对存储库所做更改的简要描述（'-m'）。从 Subversion 检出文件 现在让我们从存储库中检索或“检出”一份文件副本以进行工作：

```
$ svn checkout file:///Users/user_name/svnrepos/carte_proj-copy
```

结果将列出已上传（'A'）到我们工作副本的所有内容：A **proj_restaurant-copy/Employee.PHP** Revision 1. 已被检出。通过输入以下内容导航工作副本的目录：

```
$ cd carte_proj-copy
```

然后，在终端中，双重检查工作副本的数据：

```
$ ls -a1
```

这将返回目录以及任何隐藏文件：

+   - .
+   - ..
+   - .svn
+   - Staff.PHP

请记住隐藏目录 '.svn'。它存储 Subversion 的某些元数据，例如存储库的名称，因此之后您无需再次输入。

## 更新和提交代码更改

是时候更新我们的文档并将其保存回存储库了。使用您选择的文本编辑器，从工作副本中打开 'Staff.PHP' 并在文件中插入以下文本：

```
<?PHP
Class Staff{}
?>
```

然后可以使用 Subversion 比较存储库与您副本之间的差异：

```
$ svn status
```

[输入一条类似“Taking a snapshot of the release we're turning in.”的消息]
发送 tags/release_1.0.0...
已提交修订版本 4。
$ ls trunk/

Timecard.PHP # <-- 你的工作代码；继续在此开发

```
$ ls tags/
release_1.0.0/
$ ls tags/release_1.0.0/
Timecard.PHP # <-- this version is frozen in time
$ svn export file:///Users/user_name/svnrepos/carte_proj -copy
```

此变体已受保护，可在互联网上使用。因为此文件夹不是工作副本，所以您无法从中对存储库进行修改。

## PHP 安全简介

现代世界在很大程度上依赖于互联网，所有跨国公司及其产品详情肯定都在互联网上可用。

我们将在本书中讨论我们的数据为何不安全以及互联网上的敏感数据如何容易受到攻击。攻击者是谁，他们打算如何访问我们的敏感数据？在整本书中，将揭示几种安全攻击方式，以及为保护我们的数据已采取了哪些步骤以及必须执行哪些操作。本书的整体主题是讨论数据获取的各种威胁、PHP 安全在此领域的功能以及 PHP 安全为处理此问题所采取的关键措施。在第一章中，我们将介绍数据安全的最常见威胁和最基本的处理方法。这里出现的基本问题是，它们安全吗？采取了哪些具体的安全相关措施？

对网站和电子邮件帐户的攻击正成为真正的威胁。网络钓鱼的兴起，网络用户被骗向罪犯透露其详细信息。这是通过使用看似来自受信任来源的假文件来完成的，例如银行对账单或信用卡对账单。它们通过电子邮件发送，这些电子邮件试图看起来像发送它们的真正邮件。

这些可能包括政府机构的链接以及来自他人垃圾邮件列表的垃圾邮件/垃圾邮件。这些黑客入侵了您的系统并获得了您甚至不知道存在的敏感信息或文件，因此当您收到此类某人的电子邮件或收到短信时，发送此消息的不是那个人，而是将所有这些消息放到网络上的计算机病毒文件。这些所有事情都清楚地表明，我们的专业和，更重要的是，大数据并不安全，但让我们看看我们的数据，我们在社交网络上分享的个人事物是否足够安全？这个问题确实令人震惊。因为我们分享的数据大多数时候会被其他人访问，他们甚至可以操纵它。这给人一种印象，好像有什么不妥或危险的东西潜伏在你的网页后面。您的电子邮件地址及其所有详细信息都存储在这些相同的文件中，使您容易受到任何可以自由访问您私人数据的人的攻击，无论那个人想出于任何目的使用这些文件。我们的所有事务在互联网上主要是不安全的，我们是否曾意识到谁在拿走我们珍贵的数据，有不同的人在不同的层面上工作，他们有足够的权力访问我们的数据，我们将在此看到攻击我们数据的主要攻击者类型。主要攻击者类型称为“恶意 URL”攻击。这意味着目标已点击某个不需要的链接以到达恶意站点。因此，如果您收到黑客发来的电子邮件，告诉您点击他提供的链接，他的目标是窃取
