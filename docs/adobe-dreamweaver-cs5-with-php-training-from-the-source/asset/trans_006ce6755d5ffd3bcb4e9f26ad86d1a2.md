
-   [记住，有些人会关闭 JavaScript。即使你的页面看起来不够好，也应该在关闭 JavaScript 的情况下仍能正常工作。不要只依赖 Ajax 来提供内容，要提升大多数用户的体验。]

#### `# Preparing for the exercises`

为了确保你在前两课中已经在数据库中拥有足够的内容，本课的文件包含一个 `.sql` 文件，用于填充表格。使用以下指示来准备本课的练习：

**1.** 该 `.sql` 文件会删除 `phpcs5` 数据库中 `photos`、`place2photo`、`places` 和 `states` 表中的所有现有内容。如果你愿意清空数据库，继续执行第 2 步。

如果你已经录入了想要保留的数据，请按照“使用 phpMyAdmin”（见 [Lesson 13](#ch13.html#ch13)）的说明，先创建一个 `.sql` 备份文件，然后再继续后续步骤。

**2.** 打开 phpMyAdmin，并以 root 用户登录（如有需要）。

**3.** 选择 `phpcs5` 数据库，点击页面顶部的 **Import** 标签。

**4.** 在 “File to import” 区域点击 **Browse**，选择 `phpcs5-lesson12.sql`（位于 lesson12/start/scripts），然后点击 **Go**。phpMyAdmin 会提示导入成功。

**5** 点击左侧表格列表中的 `places` 链接。列表中共有 11 个地点。有些地点的 `link_name` 已被缩短。你会发现这些地点既不是按字母顺序排列，也不是按州分组。

![Image](graphics/fig12_02.jpg)

### ![Image](graphics/note.jpg)**NOTE:**

不要担心图片中看起来像乱码的拉斯维加斯描述列内容。这是 phpMyAdmin 无法正确处理的破折号（emdash），在最终页面中会显示正常。

**6.** 将 `cms_complete/image_upload` 目录中的全部 20 张图片复制到 `cms/image_upload` 目录。即使该目录里已有其他图片，也要确保已复制所有在更新后的数据库表中记录的图片。

**7.** 将 `gallery.php` 与 `details.php` 从 lesson12/start 复制到 lesson12/workfiles。如果 Dreamweaver 提示更新链接，请点击 **Don’t Update**。

**8.** 将 `db_definitions.php` 从 lesson12/start/scripts 复制到 lesson12/workfiles/scripts 目录。同时，确保在该目录中也有你的 `library.php` 文件的副本。

#### `# Introducing Adobe Widget Browser`

网络上有大量优秀的 JavaScript 小部件免费提供。但许多设计师的主要障碍是将这些小部件自定义以匹配自己的网页，通常需要扎实的 JavaScript 与 CSS 知识。Adobe Widget Browser 通过提供可视化界面，改变已选小部件的外观和行为，来帮助克服这一问题。

Adobe Widget Browser 默认未安装，但它与 Dreamweaver CS5 深度集成。安装好 Widget Browser 后，你可以通过它在 Adobe Exchange 预览小部件。找到喜欢的小部件后，可下载并自定义，保存的修改会自动插入 Dreamweaver 站点。所有小部件均免费，只需使用 Adobe ID 登录 Adobe Exchange 即可下载。

Widget Browser 采用 OpenAjax Alliance（[www.openajax.org](http://www.openajax.org)）制定的规范，该组织由软件公司、开源项目和个人组成，致力于推广开放且可互操作的 Ajax 技术。因此，Adobe Exchange 上的小部件不局限于使用 Spry 框架（Adobe 的 Ajax 实现），许多小部件（包括本课选中的小部件）基于 jQuery（[http://jquery.com/](http://jquery.com/)），这是最流行的 JavaScript 库，专为简化跨浏览器脚本开发而设计。

#### `# Launching the Widget Browser`

虽然 Widget Browser 是独立应用，但最便捷的访问方式是通过 Dreamweaver。

**1.** 确保已连接 Internet，点击 Application Bar 中的 **Extend Dreamweaver** 图标 ![Image](graphics/extend.jpg)，然后选择 **Widget Browser**。

![Image](graphics/fig12_03.jpg)

在 Mac 上若看不到 Extend Dreamweaver 图标，请选择 **Window > Application Bar**（在 Windows 上该栏不可隐藏）。

**2.** 若 Widget Browser 已安装，它会直接启动，跳过本节，进入下一节 “Choosing widgets from the Adobe Exchange”。如果出现下面的提示框，请继续后续步骤。

![Image](graphics/fig12_04.jpg)

**3** 点击 **OK**，这会打开默认浏览器并跳转到 Widget Browser 在 Adobe 网站上的页面。

**4.** 点击下载 Widget Browser 的链接。此时可能会提示使用 Adobe ID 登录，这通常是你的电子邮件地址。

如果没有 Adobe ID，请点击 **Create an Adobe Account**，注册过程只需几分钟。

在下载页面，若已安装 Flash Player，点击 **Install Now**；否则点击下载链接。

**5.** 在弹提示时，选择 **Open**。

**6.** 当系统询问是否确认安装时，点击 **Install**，如有需要输入计算机管理员密码。

**7.** 系统会提示选择安装位置，完成选择后点击 **Continue**（可接受默认位置）。

**8.** 安装完成后，Widget Browser 会自动启动。点击 **Accept** 同意许可协议。

#### `# Choosing widgets from the Adobe Exchange`

Widget Browser 让你在决定下载之前先观看小部件的实际效果。本节你将登录 Adobe Exchange，选择用于 `gallery.php` 的小部件。

**1.** 要预览并下载小部件，需先登录 Adobe Exchange。点击 Widget Browser 顶部右侧的 **Sign In**。

**2.** 输入 Adobe ID 与密码。若希望避免每次登录，可在点击 **Sign In** 前勾选 **“Stay signed in”** 复选框。

**3.** Widget Browser 会显示小部件的缩略图，并附带简要信息，包括作者姓名和用户评分。

![Image](graphics/fig12_05.jpg)

可以使用标题栏的 **Sort By** 菜单对缩略图进行排序，也可以在 **Filter** 框中输入关键字进行过滤。

**4.** 本课使用的小部件是 **LightBox Gallery Widget**（作者 Andres Cayon）。它位于前一张截图的左下角，也可以直接在 **Filter** 框中输入 “Andres” 快速定位。点击缩略图可查看其使用的框架、浏览器兼容性以及许可证。

**5.** 若想更 closely 观察该小部件，点击右上角的 **Preview** 按钮。这会打开 Live View，你可以通过悬停缩略图并点击其中一个来进行测试。

![Image](graphics/fig12_06.jpg)

Preview 页面还提供 **Code** 标签页，可查看小部件插入页面的代码。该小部件提供多种 preset，本例包含橙色配色方案以及白色垂直版本。

**6.** 点击右下角的 **Add to My Widgets**。

**7.** 下载完成后，点击 **Go to My Widgets**。

如果误点 **Close**，会返回到小部件描述页面。此时点击左上角的 **Adobe Exchange**，再点 **My Widgets** 即可查看已下载的小部件。

**8.** 保持 Widget Browser 打开，以便继续下一节内容。

### `Configuring a Widget`

