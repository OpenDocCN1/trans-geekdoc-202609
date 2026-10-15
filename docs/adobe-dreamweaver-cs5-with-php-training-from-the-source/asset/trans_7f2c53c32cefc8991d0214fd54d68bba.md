
你也可以在我的 Adobe TV 视频的最后部分中遵循这些步骤，该视频讲解了 PHP 代码提示在 Dreamweaver CS5 中的使用（[http://tv.adobe.com/watch/learn-dreamweaver-cs5/using-php-code-hinting-in-dreamweaver-cs5](http://tv.adobe.com/watch/learn-dreamweaver-cs5/using-php-code-hinting-in-dreamweaver-cs5)）。

# 1. 在 Dreamweaver 文件面板中，选择 PHP CS5 站点。

# 2. 确保文档窗口中激活的文件属于当前站点，或者关闭所有文件。

# 3 选择“站点 > 针对站点的代码提示”。

# 4. 确保“结构”菜单设置为 `<New from Blank>`。

# 5. 点击“子根文件夹”文本框旁边的图标，导航到位于 Zend 文件夹上一级的库文件夹。

![Image](graphics/note.jpg)NOTE:

子根文件夹必须高于你希望扫描的所有文件或文件夹至少一级。

![Image](graphics/fig07_03.jpg)

点击“确定”。

# 7. 点击“文件”区域上方的加号 (+) 按钮，打开“添加文件/文件夹”对话框。

![Image](graphics/fig07_04.jpg)

# 8. 点击“选择文件夹”图标，并在“文件/文件夹”文本框旁边的图标中选择 Zend 文件夹。

# 9. “递归”复选框指示 Dreamweaver 是否扫描所有子文件夹。如果选中 Zend 文件夹的复选框，则会为整个框架启用代码提示。由于 ZF 包含大量文件和文件夹，扫描全部并不合适，因此请保持复选框未选中。

# 10. 为了提高扫描效率，点击“扩展名”区域上方的加号按钮，并在高亮部分输入 **.php**。这告诉 Dreamweaver 仅扫描 `.php` 文件。

![Image](graphics/fig07_05.jpg)

# 11. 点击“添加”，然后重复步骤 7–10，添加以下子文件夹（均为 Zend 的子文件夹）：Auth、Captcha、Db、File、Loader、Mail、Paginator、Validate。为每个文件夹选择“递归”复选框，并在扩展名列表中添加 `.php`。

你还需要添加 Service 文件夹及其子文件夹 ReCaptcha。Service 文件夹包含许多子文件夹，因此仅为 ReCaptcha 子文件夹选中“递归”复选框。

![Image](graphics/fig07_06.jpg)

如果忘记选中“递归”复选框或添加 `.php` 文件扩展名，可以在“针对站点的代码提示”对话框底部的复选框和按钮中进行修改。

# 12. 点击对话框右上角的“保存结构”图标 ![Image](graphics/save_structure.jpg) 来保存配置。

# 13. 在“名称”文本框中输入 **Zend**（除 Custom、Drupal、Joomla 或 WordPress 外的任何名称均可），然后点击“保存”。

# 14. 点击“确定”关闭“针对站点的代码提示”对话框。此操作会在站点根目录中插入一个名为 `dw_php_codehinting.config` 的文件。Dreamweaver 使用此文件扫描 ZF 文件夹并为选定组件创建代码提示。

### ![Image](graphics/tip.jpg)TIP:

每次启动 Dreamweaver 时，文件夹会按倒序字母顺序扫描。此过程通常不会拖慢程序，但如果选择整个框架，可能需要几分钟才能准备好所有代码提示供使用。

## 改进注册表单

在 [第 6 课](#ch06.html#ch06) 中创建的注册表单存在严重缺陷。没有对每个输入字段的值进行控制。如果你在未填写任何字段的情况下提交表单，MySQL 会阻止提交，但服务器端代码会给出这个无用的提示，并且没有提供返回表单的方法。

![Image](graphics/fig07_07.jpg)

这是 MySQL 表示 `first_name` 是必填字段的方式，但你需要更好的方式向用户传达该信息。

此外，一系列空格也被视为有效输入，因此可能会出现完全空白的记录。还有用户名重复的问题，更别提为密码设置最小长度了。注册表单需要在尝试将数据插入数据库之前检查所有用户输入，并在验证失败时重新显示表单并显示错误信息，如下图所示。

![Image](graphics/fig07_08.jpg)

此外，还需考虑忘记密码的情况。在 [第 8 课](#ch08.html#ch08) 中，你将学习如何向用户发送电子邮件来重置密码，因此需要在 `users` 表中添加额外列——一个用于存储电子邮件地址，另一个用于安全令牌。

此事项众多。让我们先从更新 `users` 表开始。

### 为 `users` 表添加唯一索引

唯一索引防止在数据库列中插入重复值。在 phpMyAdmin 中为列添加索引既快速又简单。

# 1. 打开 phpMyAdmin，并选择 `phpcs5` 数据库中的 `users` 表。

# 2. 如果存在重复用户名的记录，点击相应记录旁的删除图标 ![Image](graphics/mysql_delete.jpg) 删除你想删除的记录。请保留至少一条记录，因为后续需要用于测试。

# 3. 点击左上角的“结构”标签以显示 `users` 表的定义。

# 4. 在 `username` 行的“操作”部分点击唯一索引图标 ![Image](graphics/mysql_unique.jpg)。页面刷新后，应看到已为 `username` 添加索引的确认信息。SQL 命令会立即显示在下方，确保其包含 `ADD UNIQUE`。

![Image](graphics/fig07_09.jpg)

如果误点其他图标创建了不同类型的索引或在错误列上创建了唯一索引，请点击页面底部的“Details”链接，展开“索引”部分，删除刚创建的索引，然后重复步骤 4 为 `username` 添加唯一索引。

保持 phpMyAdmin 打开并保持“结构”标签选中，以便继续后续步骤。

### 为 `users` 表添加额外列

在 phpMyAdmin 中为表添加列只需几分钟。虽然更改数据库结构很简单，但通常只应在开发阶段进行。一旦开始填充数据库记录，就有丢失数据或出现不完整记录的风险。

# 1. 在 phpMyAdmin 的 `users` 表“结构”标签页中，向下滚动至底部的“添加字段”区域。在文本框中输入 **2**，保持“表尾”单选按钮选中，然后点击“确定”。

![Image](graphics/fig07_10.jpg)

![Image](graphics/note.jpg)NOTE:

其他单选按钮允许你指定新列的插入位置。如果选择“之后”单选按钮，phpMyAdmin 会在选定列之后插入新列。

这将呈现一个矩阵，用于定义两个新列。由于只有两列，选项垂直排列，更易观察。

# 2. 对于 `email` 列，在“字段”列中输入 **email**，将类型设为 `VARCHAR`，长度/值设为 **100**。

令牌将是一个随机生成的固定长度字符串。对于另一列，在“字段”列中输入 **token**，将类型设为 `CHAR`，长度/值设为 **32**，并勾选“可为空”复选框使该列可选。

![Image](graphics/fig07_11.jpg)

# 3. 点击“保存”。修改后的表结构应如下所示：

![Image](graphics/fig07_12.jpg)

### ![Image](graphics/caution.jpg)CAUTION!

如果点击“确定”而非“保存”，phpMyAdmin 会为另一列添加选项。为该列输入占位名称，并将类型设为 `INT`。保存后，通过点击删除图标 ![Image](graphics/mysql_delete.jpg) 删除不需要的列。

无需更新 `users` 表中的现有记录。删除记录可在后续测试脚本时进行。

#### 加载 ZF 类文件

