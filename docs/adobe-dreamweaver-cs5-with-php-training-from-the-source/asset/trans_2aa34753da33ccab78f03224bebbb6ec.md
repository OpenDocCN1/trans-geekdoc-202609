
-   [排序规则](https://wiki.example.org/feynmans_learning_method)在处理非英文语言时非常重要。如果你只使用英文，可以完全忽略它——几乎可以。当 phpMyAdmin 显示数据库或表结构时，你会看到“排序规则”列被设置为 `latin1_swedish_ci`。为什么是瑞典语设置？MySQL 最初是在瑞典开发的，因此其默认排序规则是瑞典语，同时也使用与英文完全相同的排序顺序。

然而，在某些语言中，传统的排序顺序与字母顺序不同。例如，在西班牙语中，*LL* 被视为独立字符，且在排序时位于字母 *L* 之后。下面的截图展示了差异。

![Image](graphics/fig05_12.jpg)

在传统西班牙语排序顺序中，*llamar* 排在 *loco* 之后。但按字母顺序排列时，*llamar* 却排在 *loco* 之前。左侧截图的排序规则为 `utf8_spanish2_ci`，右侧截图的排序规则为默认的 `latin1_swedish_ci`。

排序规则可在整个数据库、表级或单个字段上设置。如果在数据库或表级别设置，该设置将成为整个数据库或表的默认值，但可以为单个表或字段覆盖默认值。

可用的排序规则取决于 MySQL 的配置，但命名规则易于理解。每个名称由以下三个用下划线分隔的元素组成：

-   编码  
-   语言  
-   区分大小写：`bin` 表示二进制（区分大小写），`ci` 表示不区分大小写，`cs` 表示区分大小写  

### ![Image](graphics/note.jpg)**NOTE:**

排序规则不影响 MySQL 中存储数据的字符编码。它仅关注排序顺序。

#### **定义 users 表**

用于用户注册系统的 `users` 表至少需要五个字段：

-   `user_id`  
-   `first_name`  
-   `family_name`  
-   `username`  
-   `password`  

你可以稍后添加其他字段（例如存储用户的电子邮件地址），但当前只需这些。

**1.** 如果你在确认创建 `phpcs5` 数据库的页面上仍保持 phpMyAdmin 打开，直接跳到下一步。

如果需要重新启动 phpMyAdmin，在左侧数据库列表中选择 `phpcs5`，这将打开该数据库的 Structure 标签页，并显示创建新表的文本框。

**2.** 在“在数据库 phpcs5 中创建新表”部分，于“名称”文本框中输入 **users**，在“字段数量”处输入 **5**，然后点击 **Go**。

![Image](graphics/fig05_13.jpg)

**3.** 一个巨大的矩阵出现，用于定义表的每个字段。由于矩阵宽度较大，需要水平滚动才能在屏幕上完整查看，但填写内容相对简单。

![Image](graphics/fig05_14.jpg)

### ![Image](graphics/tip.jpg)**TIP:**

当你创建只有三个字段的表时，phpMyAdmin 会以垂直布局呈现矩阵，便于查看所有选项。

**4.** 在第一行，于“字段”文本框中输入 **user_id**。

**5.** 将“类型”菜单设置为 `INT`。前两个字段应如下所示：

![Image](graphics/fig05_15.jpg)

**6.** 主键不能为负数，因此将“属性”设置为 `UNSIGNED`。

**7.** `user_id` 将作为主键，从“索引”菜单中选择 `PRIMARY`。

**8.** 为确保主键自动递增，勾选 `A_I` 复选框。

步骤 6–8 设置后，值应如下所示：

![Image](graphics/fig05_16.jpg)

**9.** 其余列相对简单。使用以下截图中显示的值：

![Image](graphics/fig05_17.jpg)

由于你不清楚 `first_name`、`family_name` 或 `username` 的值可能有多长，因此数据类型应为 `VARCHAR`。使用该类型时，需要在“长度/值”文本框中指定列宽。建议适当留出更大的空间，以免数据在数据库中被截断。

为什么使用固定长度字符类型 `CHAR` 为 `password` 并设置宽度为 40？毕竟没有人会有这么长的密码！

密码不应以明文存储，因此会被加密为 40 位十六进制数字。

**10** 在矩阵下方中间的菜单栏中，确保“存储引擎”设置为 MyISAM（在 XAMPP 和 MAMP 中为默认）。

![Image](graphics/fig05_18.jpg)

更多信息请参见侧边栏“选择正确的存储引擎”。

**11** 将其余字段保持空白或使用默认值，然后点击右下角的 **Save** 按钮。

![Image](graphics/fig05_19.jpg)

### ![Image](graphics/caution.jpg)**CAUTION!**

确保点击 **Save** 按钮。若误点 **Go** 按钮，会在矩阵中额外添加一列。若此类错误发生，请在“字段”文本框中输入占位名称，将“类型”菜单设为 `INT`，随后点击 **Save**。这将添加一个占位列，稍后删除即可。

**12** 保存表结构后，phpMyAdmin 会显示新表的设置页面。请核对以下截图中的值。

![Image](graphics/fig05_20.jpg)

#### **选择正确的存储引擎**

在 MySQL 中选择存储引擎决定了数据的存储与检索方式。MySQL 支持多种存储引擎，但最常用的是 MyISAM 和 InnoDB。自 MySQL 3.23 起，MyISAM 成为默认引擎，但 2010 年 4 月宣布新版 InnoDB 将在 MySQL 5.5 中成为默认。MySQL 5.5 当时仍为 beta 版，且许多托管公司不支持 InnoDB。因此，本书的所有练习均使用 MyISAM 表。好在选择存储引擎的决定并非不可逆。你可以在 phpMyAdmin 的 **Operations** 标签页中选择新引擎，位于“表选项”区域。

存储引擎的主要区别在于 InnoDB 增加了事务和外键约束的支持。

-   **事务**：事务是一系列数据库命令，必须作为一个整体执行。若执行过程中任何部分失败，事务会自动撤销已完成的改动。这在金融数据库中至关重要——若从一个账户转账到另一个账户失败，资金会自动退回原账户。

-   **外键约束**：用于跟踪表之间的关系，防止删除记录时其主键仍被其他表的外键引用。

如果你安装了 MySQL 的 Windows Essentials 版并选择“多功能数据库”选项，则默认使用 InnoDB。可以通过编辑 `C:\\Program Files\\MySQL\\MySQL Server 5.x\\my.ini`（以管理员身份运行记事本）并将以下行：

```
default-storage-engine=INNODB
```

改为：

```
default-storage<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk>
