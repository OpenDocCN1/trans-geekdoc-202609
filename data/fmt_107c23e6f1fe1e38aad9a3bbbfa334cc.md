
取消按钮的 `name` 属性已设为 `cancel`。`isset()` 函数检查 `$_POST` 数组是否包含 `cancel`，只有在点击取消按钮时才会为真。若为真，`header()` 会将页面重定向到 `user_list.php`，`exit` 防止脚本继续执行。

![Image](img/caution.jpg)**CAUTION!**

此重定向必须位于“删除记录”服务器行为之前，否则记录仍会被删除。

8. 在浏览器或 Live View 中测试页面，启动 `user_list.php` 并点击任意 DELETE 链接（Live View 需要按住 Ctrl/Cmd）。应能在 `delete_user.php` 中看到记录详情。

9. 点击取消按钮。重定向回 `user_list.php` 后，记录仍然列在列表中。

### 10 单击 DELETE 链接再次，然后单击确认。当你被重定向到 user_list.php 时，记录不再列出。如果你在 phpMyAdmin 中检查，你会发现它已不再在数据库中。

你可以将你的代码与 `lesson06/completed/delete_user.php` 进行比较。

## 使用 Show Region 服务器行为

此时，你应该在 `users` 表中只剩下一条记录。但如果你删除最后一条记录会发生什么？尝试一下。你会得到一个空表。

![Image](img/fig06_52.jpg)

这看起来很奇怪。如果你能显示一条“无记录”消息会更好。Show Region 服务器行为可以帮助你实现。

1. 在 `user_list.php` 设计视图中打开，在表格右侧点击，按 Enter/Return 插入一个新段落，然后输入 No records found。

2. 在文档窗口底部的 Tag 选择器中点击 `<p>` 以选中整个段落。

3. 段落仍然选中状态下，在 Server Behaviors 面板中点击加号按钮，选择 Show Region > Show If Recordset Is Empty。

4. 这会弹出一个对话框，要求你选择记录集。页面上只有一个记录集，所以直接点击 OK。段落会被灰色边框包围，并在左上角出现一个 Show If 选项卡。

5. 点击表格内部，然后在 Tag 选择器中点击 `<table>` 以选中整个表格。

6. 表格选中后，在 Server Behaviors 面板中点击加号按钮，选择 Show Region > Show If Recordset Is Not Empty。

7. 再次弹出对话框，要求选择记录集。页面上只有一个，所以直接点击 OK。表格会被灰色边框包围，并在左上角出现一个 Show If 选项卡。

8. 测试页面。如果 `users` 表中没有记录，你应该看到：

![Image](img/fig06_53.jpg)

9. 如果你在 `users` 表中添加另一条记录，则“无记录”消息会隐藏，并显示新用户。

你可以将你的代码与 `lesson06/completed/user_list_showif.php` 进行比较。

## 评估服务器行为

如果你没有 PHP 经验且使用数据库，服务器行为会让你印象深刻。它们让你用最小的努力构建数据库驱动站点。本节课覆盖了主要的服务器行为。唯一被遗漏的重要行为是 Recordset Navigation Bar，它在单个操作中插入八个独立的服务器行为。它允许你将长系列的数据库结果分布在多个页面上，并在它们之间来回导航。

![Image](img/note.jpg)NOTE:

Recordset Navigation Bar 不在 Server Behaviors 面板的菜单中。要插入它，请选择 Insert > Data Objects > Recordset Paging > Recordset Navigation Bar。对话框只有两个选项：要使用的记录集和用于导航链接的文本或图像的选择。插入导航条后，需要用 CSS 对其进行样式设置。

使用服务器行为和本节课所教授的技术，你可以实现很多事情。例如，EDIT 和 DELETE 链接使用的技术与产品列表相同。通过在链接中加入产品的主键，你可以加载页面来显示产品详情。与将详情加载到更新表单不同，你可以将它们加载到普通页面并使用动态文本对象显示。事实上，`delete_user.php` 正是这样做的。要显示图片，将文件名存储在数据库中，并将动态文本对象绑定到 `<img>` 标签的 `src` 属性上。

虽然服务器行为很强大，但它们也有相当大的缺点，使用时间越长，这些缺点就越明显。以下是主要问题：

- 只有一个验证服务器行为，即 Check New Username，且它不够用户友好。

- 用户身份验证服务器行为不支持密码加密。

- 每次加载页面时，即使不需要也会与数据库建立连接。

- 记录集经常在不需要时被创建。

- 代码与 HTML 在同一页面中，这使得设计师和程序员难以同时在站点的不同方面工作。

- 每页都包含大量相同的代码，使用外部文件会更高效。

- 大量代码僵硬，缺乏灵活性。一旦想要做不同的事情，就需要自定化代码或编写新代码。

- 服务器行为与 MySQL 绑定，无法适配其他数据库。

也许服务器行为的最大问题是它们会产生不切实际的期望。能够在不修改底层代码的情况下创建基本数据库驱动站点让初学者期望服务器行为能做所有事情。他们随后尝试弄清楚如何完成某项操作，却碰到墙。这导致对改进服务器行为的需求，以执行更高级的操作，如服务器端验证、文件上传和发送电子邮件。事实上，Adobe Dreamweaver Developer Toolbox (ADDT) 套件（直至 2009 年 4 月下架）曾提供许多高级服务器行为，深受热情粉丝欢迎，但其生成的代码僵硬且难以编辑。

服务器行为的难点在于它们必须预测用户会想要哪些选项。选项范围越广，代码越复杂。为保持代码可管理，服务器行为只提供基本功能。鉴于取消 ADDT 并未在 Dreamweaver CS5 中添加新服务器行为的决定，服务器行为的作用可能会逐渐下降。它们适合快速制作数据库驱动站点的原型或非常简单的站点。除此之外，你需要更强大的解决方案。剩余的课程将使用 Zend Framework 展示如何构建更高级的解决方案，而无需编写大量代码。

![Image](img/tip.jpg)TIP:

如果想了解如何自定义 Dreamweaver 的 PHP 服务器行为，我的书 *The Essential Guide to Dreamweaver CS4 with CSS, Ajax, and PHP*（friends of ED, 2008, ISBN: 978-1-4302-1610-0）提供了深入的覆盖。虽然它是针对 Dreamweaver 之前的版本编写的，但服务器行为在 Dreamweaver CS5 中的工作方式相同。

### 你学到了什么

***在本节中，你学到了：***

- 创建 MySQL 连接文件（第 171–177 页）

- 使用 Insert Record 服务器行为在 `users` 表中插入记录（第 177–183 页）

- 使用 Log In User 服务器行为创建登录系统（第 183–187 页）

- 使用 Restrict Access To Page 服务器行为保护页面（第 187–188 页）

- 创建站点受保护部分的退出链接（第 188–190 页）

- 加密密码（第 190–192 页）

- 使用 Recordset 服务器行为选择记录（第 192–194 页）

- 使用 Bindings 面板显示记录集的结果（第 194–196 页）

- 在重复区域中显示多个结果（第 196–197 页）

- 创建链接以选择特定记录（第 198–200 页）

- 更新和删除记录（第 200–206 页）

- 隐藏页面部分，并在记录集为空时显示消息（第 206–207 页）

### 本节课你将学习

***在本节中，你将学习：***

- 安装 Zend Framework 并设置站点特定的代码提示

- 为 `users` 表添加唯一索引和额外列，修改数据库表结构

- 使用 Zend\_Validate 在服务器端验证用户输入

- 在验证失败时保留用户输入并显示错误信息

• 使用 Dreamweaver 的服务器行为构建器创建可重用代码

• 检查重复的用户名

• 使用 Zend\Db 将用户输入插入数据库

• 使用 Zend\Auth 创建登录系统

### 大约所需时间

本课程大约需要 3 小时完成。

### 课程文件

***媒体文件：***

`styles/users.css`

`styles/users_wider.css`

***起始文件：***

`lesson07/start/add_user.php`

`lesson07/start/login.php`

`lesson07/start/members_only.php`

***已完成文件：***

`lesson07/completed/add_user.php`

`lesson07/completed/add_user01.php`

`lesson07/completed/add_user02.php`

`lesson07/completed/add_user03.php`

`lesson07/completed/login.php`

`lesson07/completed/members_only.php`

`lesson07/completed/scripts/library.php`

`lesson07/completed/scripts/library_magic_quotes.php`

`lesson07/completed/scripts/restrict_access.php`

`lesson07/completed/scripts/user_authentication.php`

`lesson07/completed/scripts/user_authentication01.php`

`lesson07/completed/scripts/user_registration.php`

`lesson07/completed/scripts/user_registration01.php`

`lesson07/completed/scripts/user_registration02.php`

`lesson07/completed/scripts/user_registration03.php`

仅使用 JavaScript 进行验证是不够的，因为只需几秒钟即可在浏览器中关闭 JavaScript，从而使验证脚本失效。在将用户输入插入数据库之前，必须使用服务器端语言（如 PHP）对其进行验证。

在本课程中，借助强大的第三方脚本库——Zend Framework，你将创建一个强大的用户注册系统，该系统在服务器上验证输入。这需要编写自己的 PHP 代码，而不是依赖 Dreamweaver 自动生成。任何不便都被更大的功能所补偿，并且通过站点特定的代码提示简化了流程。

你还将使用 Dreamweaver 的服务器行为构建器加速常用 PHP 代码的插入。

*注册表单在将详细信息插入数据库之前会提示用户出现错误。*

![Image](img/fig07_01.jpg)

### 介绍 Zend Framework

Zend Framework（ZF）是一个庞大的开源 PHP 脚本库。ZF 1.10 的“最小”版本包含超过 2,700 个文件，分布在近 500 个文件夹中，体积超过 22 MB。当然，体积并非一切。你可能会疑惑，为什么需要如此多的文件来执行几项基本任务，如在数据库中插入和更新记录、上传文件和发送邮件。

框架提供了大量选项，其中很多可能你永远不会用到。例如，ZF 有 14 个组件，用于访问不同的电子商务服务（如 [Amazon.com](http://Amazon.com)）。大多数开发者从不使用它们，但在拥有 Amazon 附属账户时，它们是必不可少的。与其编写复杂而乏味的脚本，你可以用几行代码就查询 Amazon 数据库。

大多数教程假设你希望使用 MVC（模型-视图-控制器）设计模式来构建 Web 应用，该模式将数据处理（模型）、输出（视图）和条件逻辑（控制器）分别交给独立脚本处理。除非你已经具备相当的 PHP 经验，否则 MVC 设计模式可能会让人困惑，因此本书采用不同的方法，提供更温和的入门。

ZF 是一个 *松耦合* 框架，这意味着每个部分都设计为与其他部分的依赖最小化。你可以只使用其中几个组件而无需学习整个框架。如果以后决定采用 MVC，你对关键 ZF 组件的了解将加速向 MVC 的过渡。

在剩余课程中，你将使用的主要组件包括：

• `Zend_Auth` 用于检查用户凭证

• `Zend_Db` 用于与数据库通信

• `Zend_File` 用于上传文件

• `Zend_Loader` 用于自动加载 ZF 类

• `Zend_Mail` 用于发送邮件和附件

• `Zend_Paginator` 用于分页长系列的数据库结果

• `Zend_Service_ReCaptcha` 用于防止垃圾输入

• `Zend_Validate` 用于验证用户输入

练习仍然使用 MySQL，但 `Zend_Db` 使代码更具灵活性。只需修改一两行即可切换到 Microsoft SQL Server、PostgreSQL 或其他数据库系统。

ZF 的其他优势包括：

• 其主要赞助商是 Zend Technologies，由 PHP 核心贡献者创立并运营。

• 诸如 Adobe、Google 和 Microsoft 等领先软件公司已为其贡献组件或重要功能。Adobe 贡献了 `Zend_Amf`，它充当 PHP 与 Flash Player 之间的桥梁，使用二进制的 Action Message Format（AMF）。

• ZF 从一开始就设计用于 PHP 5 的面向对象编程。许多框架最初是为兼容 PHP 4 而设计的，而 PHP 4 的效率较低。

• ZF 的下一个主要版本正在设计，以增强与其他框架（如 Symfony）的互操作性。

### ![Image](img/tip.jpg)**TIP:**

ZF 是面向对象的框架。如果你不熟悉 PHP 的面向对象编程，现在是回顾“使用对象和资源”（Lesson 3）的好时机。

#### **安装 Zend Framework**

本书随附的光盘包含 `ZendFramework-1.10.6-minimal.zip`。也可以从 [`framework.zend.com/download/latest`](http://framework.zend.com/download/latest) 下载最新版本。选择最小化版本，它包含你所需的所有文件。部分下载链接需要你建立 Zend 账户，这是免费的，且不附带任何义务。

安装 ZF 非常简单，只需解压文件到硬盘合适的位置。为提高效率，建议将其放在 `phpcs5` 站点根目录之外，以便所有站点在 Dreamweaver 中都能访问。在 Windows 上，在 C 盘的根目录下创建名为 `php_library` 的文件夹；在 Mac 上，在用户主目录下创建同名文件夹，然后解压 ZF 到该文件夹。

压缩包内包含两个文件夹：`bin` 和 `library`。框架位于 `library` 的子文件夹 `Zend` 中，每个组件都有一个对应的 `.php` 文件以及专门的文件夹。

无需打开这些文件，但如果你打开它们，会发现每个文件都经过大量注释，这也解释了框架的庞大体积。随着经验的增长，你会在注释中发现大量有用信息，有时能够解释文档中未完全说明的功能。

![Image](img/fig07_02.jpg)

### ![Image](img/tip.jpg)**TIP:**

ZF 的文档在 [`framework.zend.com/manual/en/`](http://framework.zend.com/manual/en/)，内容丰富且包含许多示例。遗憾的是，大部分文档假设你使用 MVC 设计模式，并且已经具备扎实的 PHP 基础。不过，文档已作出 considerable 努力以改进可读性。

#### **为 ZF 设置站点特定的代码提示**

在第 4 课（Lesson 4）中，你学习如何为 WordPress、Drupal 和 Joomla! 创建站点特定的代码提示。Dreamweaver 自动识别这些 CMS 的结构。对于其他框架（包括 ZF），你需要告诉 Dreamweaver 在哪里找到文件以及哪些文件需要被扫描以生成代码提示。本节将展示如何为 ZF 单独设置结构，替换现有的 `dw_php_codehinting.config`（在 `phpcs5` 站点中），但你可以通过在“站点特定代码提示”对话框的“结构”菜单中选择不同的配置来在不同项目之间切换。

![Image](img/tip.jpg)**TIP:**

你也可以在我的 Adobe TV 视频的最后部分中遵循这些步骤，该视频讲解了 PHP 代码提示在 Dreamweaver CS5 中的使用（[`tv.adobe.com/watch/learn-dreamweaver-cs5/using-php-code-hinting-in-dreamweaver-cs5`](http://tv.adobe.com/watch/learn-dreamweaver-cs5/using-php-code-hinting-in-dreamweaver-cs5)）。

# 1. 在 Dreamweaver 文件面板中，选择 PHP CS5 站点。

# 2. 确保文档窗口中激活的文件属于当前站点，或者关闭所有文件。

# 3 选择“站点 > 针对站点的代码提示”。

# 4. 确保“结构”菜单设置为 `<New from Blank>`。

# 5. 点击“子根文件夹”文本框旁边的图标，导航到位于 Zend 文件夹上一级的库文件夹。

![Image](img/note.jpg)NOTE:

子根文件夹必须高于你希望扫描的所有文件或文件夹至少一级。

![Image](img/fig07_03.jpg)

点击“确定”。

# 7. 点击“文件”区域上方的加号 (+) 按钮，打开“添加文件/文件夹”对话框。

![Image](img/fig07_04.jpg)

# 8. 点击“选择文件夹”图标，并在“文件/文件夹”文本框旁边的图标中选择 Zend 文件夹。

# 9. “递归”复选框指示 Dreamweaver 是否扫描所有子文件夹。如果选中 Zend 文件夹的复选框，则会为整个框架启用代码提示。由于 ZF 包含大量文件和文件夹，扫描全部并不合适，因此请保持复选框未选中。

# 10. 为了提高扫描效率，点击“扩展名”区域上方的加号按钮，并在高亮部分输入 **.php**。这告诉 Dreamweaver 仅扫描 `.php` 文件。

![Image](img/fig07_05.jpg)

# 11. 点击“添加”，然后重复步骤 7–10，添加以下子文件夹（均为 Zend 的子文件夹）：Auth、Captcha、Db、File、Loader、Mail、Paginator、Validate。为每个文件夹选择“递归”复选框，并在扩展名列表中添加 `.php`。

你还需要添加 Service 文件夹及其子文件夹 ReCaptcha。Service 文件夹包含许多子文件夹，因此仅为 ReCaptcha 子文件夹选中“递归”复选框。

![Image](img/fig07_06.jpg)

如果忘记选中“递归”复选框或添加 `.php` 文件扩展名，可以在“针对站点的代码提示”对话框底部的复选框和按钮中进行修改。

# 12. 点击对话框右上角的“保存结构”图标 ![Image](img/save_structure.jpg) 来保存配置。

# 13. 在“名称”文本框中输入 **Zend**（除 Custom、Drupal、Joomla 或 WordPress 外的任何名称均可），然后点击“保存”。

# 14. 点击“确定”关闭“针对站点的代码提示”对话框。此操作会在站点根目录中插入一个名为 `dw_php_codehinting.config` 的文件。Dreamweaver 使用此文件扫描 ZF 文件夹并为选定组件创建代码提示。

### ![Image](img/tip.jpg)TIP:

每次启动 Dreamweaver 时，文件夹会按倒序字母顺序扫描。此过程通常不会拖慢程序，但如果选择整个框架，可能需要几分钟才能准备好所有代码提示供使用。

### 改进注册表单

在 第 6 课 中创建的注册表单存在严重缺陷。没有对每个输入字段的值进行控制。如果你在未填写任何字段的情况下提交表单，MySQL 会阻止提交，但服务器端代码会给出这个无用的提示，并且没有提供返回表单的方法。

![Image](img/fig07_07.jpg)

这是 MySQL 表示 `first_name` 是必填字段的方式，但你需要更好的方式向用户传达该信息。

此外，一系列空格也被视为有效输入，因此可能会出现完全空白的记录。还有用户名重复的问题，更别提为密码设置最小长度了。注册表单需要在尝试将数据插入数据库之前检查所有用户输入，并在验证失败时重新显示表单并显示错误信息，如下图所示。

![Image](img/fig07_08.jpg)

此外，还需考虑忘记密码的情况。在 第 8 课 中，你将学习如何向用户发送电子邮件来重置密码，因此需要在 `users` 表中添加额外列——一个用于存储电子邮件地址，另一个用于安全令牌。

此事项众多。让我们先从更新 `users` 表开始。

### 为 `users` 表添加唯一索引

唯一索引防止在数据库列中插入重复值。在 phpMyAdmin 中为列添加索引既快速又简单。

# 1. 打开 phpMyAdmin，并选择 `phpcs5` 数据库中的 `users` 表。

# 2. 如果存在重复用户名的记录，点击相应记录旁的删除图标 ![Image](img/mysql_delete.jpg) 删除你想删除的记录。请保留至少一条记录，因为后续需要用于测试。

# 3. 点击左上角的“结构”标签以显示 `users` 表的定义。

# 4. 在 `username` 行的“操作”部分点击唯一索引图标 ![Image](img/mysql_unique.jpg)。页面刷新后，应看到已为 `username` 添加索引的确认信息。SQL 命令会立即显示在下方，确保其包含 `ADD UNIQUE`。

![Image](img/fig07_09.jpg)

如果误点其他图标创建了不同类型的索引或在错误列上创建了唯一索引，请点击页面底部的“Details”链接，展开“索引”部分，删除刚创建的索引，然后重复步骤 4 为 `username` 添加唯一索引。

保持 phpMyAdmin 打开并保持“结构”标签选中，以便继续后续步骤。

### 为 `users` 表添加额外列

在 phpMyAdmin 中为表添加列只需几分钟。虽然更改数据库结构很简单，但通常只应在开发阶段进行。一旦开始填充数据库记录，就有丢失数据或出现不完整记录的风险。

# 1. 在 phpMyAdmin 的 `users` 表“结构”标签页中，向下滚动至底部的“添加字段”区域。在文本框中输入 **2**，保持“表尾”单选按钮选中，然后点击“确定”。

![Image](img/fig07_10.jpg)

![Image](img/note.jpg)NOTE:

其他单选按钮允许你指定新列的插入位置。如果选择“之后”单选按钮，phpMyAdmin 会在选定列之后插入新列。

这将呈现一个矩阵，用于定义两个新列。由于只有两列，选项垂直排列，更易观察。

# 2. 对于 `email` 列，在“字段”列中输入 **email**，将类型设为 `VARCHAR`，长度/值设为 **100**。

令牌将是一个随机生成的固定长度字符串。对于另一列，在“字段”列中输入 **token**，将类型设为 `CHAR`，长度/值设为 **32**，并勾选“可为空”复选框使该列可选。

![Image](img/fig07_11.jpg)

# 3. 点击“保存”。修改后的表结构应如下所示：

![Image](img/fig07_12.jpg)

### ![Image](img/caution.jpg)CAUTION!

如果点击“确定”而非“保存”，phpMyAdmin 会为另一列添加选项。为该列输入占位名称，并将类型设为 `INT`。保存后，通过点击删除图标 ![Image](img/mysql_delete.jpg) 删除不需要的列。

无需更新 `users` 表中的现有记录。删除记录可在后续测试脚本时进行。

### 加载 ZF 类文件

在使用 `ZF` 类和对象之前，需要在每个页面中包含定义文件。由于框架非常大，单独在每个页面中包含每个文件会很繁琐，因此 `ZF` 提供了自动加载器。该加载器只加载当前脚本所需的类定义。为了使其工作，你需要将库文件夹添加到你的 `include_path`，PHP 在此路径中查找要包含的文件。

1. 创建一个新的 PHP 文件，并将其保存为 `lesson07/workfiles/scripts` 中的 `library.php`。

2. 切换到代码视图，删除所有的 HTML 代码。文件应完全为空白。

3. 在文件顶部添加一个打开的 PHP 标签，**不要**添加对应的关闭 PHP 标签。

4. 在下一行，为 `$library` 赋值为库文件夹的绝对路径。该路径取决于你的操作系统以及你保存 `ZF` 的位置。

- 在 Windows 上，路径类似于：

  `$library = 'C:/php_library/ZendFramework/library';`

  你可以使用正斜杠或反斜杠，但更常用正斜杠。

- 在 Mac OS X 上，路径类似于：

  `$library = '/Users/username/php_library/ZendFramework/library';`

  路径以正斜杠开头，请将 **username** 替换为你自己的 Mac 用户名。

> ![Image](img/note.jpg)**NOTE:**  
> 上传站点到远程服务器时需要修改此路径，但只涉及一个文件，所以不是大问题。

5. `include_path` 的值在 `php.ini` 中指定，但在共享主机上可能无法直接访问 `php.ini`，因此可以使用 `set_include_path()` 函数在运行时动态修改它。在下一行添加以下代码：

```
set_include_path(get_include_path() . PATH_SEPARATOR . $library);
```

与直接覆盖 `include_path` 的值不同，这里是向已有值追加 `$library`。使用 `get_include_path()` 获取当前值。每个路径之间需要使用分号（Windows）或冒号（Mac/Linux）分隔。为了实现跨平台的便利，常量 `PATH_SEPARATOR` 会自动插入合适的分隔符，所有路径通过连接符（点号）拼接。

> ![Image](img/tip.jpg)**TIP:**  
> 按 **Ctrl+space** 调用代码提示，可加快该行代码的编写并确保准确性。

6. 要使用自动加载器，需要显式加载 `Zend_Loader_Autoloader` 类文件：

```
require_once('Zend/Loader/Autoloader.php');
```

这是唯一需要显式加载的 `ZF` 文件。由于前一步已经把库文件夹加入 `include_path`，因此无需使用完整的 Zend 文件夹路径。

7. 通过以下方式实例化自动加载器：

```
$loader = Zend_Loader_Autoloader::getInstance();
```

从技术上讲，不必将结果赋值给变量，但这样做有助于验证加载是否成功。

8. 为验证当前脚本的运行情况，添加以下代码：

```
if ($loader) {  
    echo 'OK';  
} else {  
    echo 'We have a problem';  
}
```

9. 保存 `library.php`，然后切换到 Live View 测试页面。若一切正常，页面应显示 **OK**。若出现 “We have a problem”，请查看错误信息。最常见的原因是库文件夹的路径错误，同时检查所有函数的拼写，并确保 `PATH_SEPARATOR` 全部大写。

10. 当一切正常后，删除步骤 8 中添加的条件语句。你也可以删除步骤 7 中的 `$loader` 变量。此时页面代码应如下（`$library` 的值取决于你的环境）：

```php
```
