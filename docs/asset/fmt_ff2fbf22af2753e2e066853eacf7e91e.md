
许多服务器行为（如“插入记录”）使用自处理表单。与其将表单提交到另一页面，服务器行为会重新加载当前页面，并通过 PHP 条件语句仅在表单提交时执行代码。当表单首次加载到浏览器时，条件语句为假，插入数据库的代码被忽略；当表单提交时，条件语句为 `TRUE`，插入操作继续。

你刚刚插入的代码工作方式相同，它使用 PHP `isset()` 函数判断 `$_POST['password']` 是否存在。如果存在，则将该值传递给 `sha1()` 进行加密，并重新赋值给 `$_POST['password']`。

如在 第 3 课 说明，`$_POST` 数组会被 PHP 自动创建，但 `$_POST['password']` 仅在使用 `POST` 方法提交包含名为 `password` 的输入框表单时才存在。因此，当页面首次加载时，`$_POST['password']` 不存在，这段代码被跳过；当表单提交时，`$_POST['password']` 通过 `sha1()` 函数加密，得到 40 位十六进制字符串。

`4.` 选中刚刚插入的代码，复制到剪贴板。

`5.` 打开 `login.php`，将代码粘贴到与 `add_user.php` 相同的位置（即服务器行为代码上方）。页面的前六行应如下所示：

```
<?php require_once('../../Connections/cs5read.php'); ?>  

<?php  

if (isset($_POST['password']) {  

  $_POST['password'] = sha1($_POST['password']);  

}  

if (!function_exists("GetSQLValueString")) {
```

`6.` 保存 `add_user.php` 和 `login.php`，并在浏览器中打开 `add_user.php`。

`7.` 使用不同的用户名和密码创建新用户，点击“Sign me up!” 按钮。

`8.` 当登录表单出现时，使用新用户名和密码登录。功能应与在对 `add_user.php` 和 `login.php` 进行修改之前的行为相同。

`9.` 点击“Log out”链接，再使用第一个用户名和密码尝试登录。此次应失败，因为第一个用户的密码在存储时未加密。

`10.` 打开 phpMyAdmin，浏览到 `users` 表。应能看到第二个用户的密码已以加密形式存储。

![Image](img/fig06_26.jpg)

已修改的文件副本位于 `lesson06/completed/add_user_encrypt.php` 和 `lesson06/completed/login_encrypt.php`。代码还已调整，使页面之间以及到 `members_only_encrypt.php` 的跳转得到改进。

### 显示、更新和删除记录

要从数据库中更新或删除记录，首先需要定位记录。Dreamweaver 用于查找数据库记录的服务器行为称为 Recordset，它会生成一个 `SELECT` 查询来查找所有匹配的记录，并将数据库结果作为资源保存，以便后续使用。该资源可用于显示结果集中每行每列的信息，随后可通过主键识别需要更新或删除的记录。

#### 使用 Recordset 服务器行为检索记录

下面的步骤演示如何使用 Recordset 对话框的“Simple”模式，检索 `users` 表的全部记录：

`1.` 在工作文件夹中复制 `lesson06/start/user_list.php`，并在设计视图中打开它。页面包含一个 HTML 标题和一个包含两行四列的骨架表格，如下图所示：

![Image](img/fig06_27.jpg)

`2` 在“服务器行为”面板中点击加号按钮，选择 Recordset 打开 Recordset 对话框。

![Image](img/fig06_28.jpg)

### NOTE:

如果 Recordset 对话框的选项与这里所示不同，请点击右侧的 “Simple” 按钮（位置与前一张截图中的 “Advanced” 按钮相同），切换到简化模式。

`3.` Dreamweaver 会自动在 “Name” 字段中填充 `Recordset1`。该值用于生成多个 PHP 变量，建议将其替换为更具意义的名称。由于它将作为变量使用，名称中不能包含空格或特殊字符，也不能以数字开头。

将 Name 字段中的 `Recordset1` 替换为 `getUsers`。

`4.` Recordset 服务器行为不修改记录，请在 Connection 菜单中选择 `cs5read`。

`5.` 当 Dreamweaver 填充完 Table 列表后，选择 `users`。此时 Columns 部分会显示表的列名。默认选中 “All”，因此列名呈灰色。

`6.` 点击 “Selected” 单选按钮激活 Columns 部分，然后按住 Shift 并点击选择除 `password` 之外的所有列。

`7.` 为了检索表中所有记录，保持 Filter 的默认值为 None。

`8.` 为按家族姓氏排序，从 Sort 菜单中选择 `family_name`。系统会自动将右侧设为 Ascending（升序）。如果选择 Descending（降序），则返回的结果顺序相反。

Recordset 对话框的设置应如下图所示：

![Image](img/fig06_29.jpg)

`9.` 点击 Test 按钮，查看 Dreamweaver 在后台生成的 SQL 查询结果。只要表中有记录，你应能看到类似下面的内容：

![Image](img/fig06_30.jpg)

如果出现错误信息，请检查 Recordset 对话框中的设置。

`10` 点击 OK 关闭 Test SQL Statement 面板，然后在 Recordset 对话框中再次点击 OK。

`11` 保存 `user_list.php`。若在 Live View 或浏览器中测试该页面，将不会出现明显变化。Recordset 服务器行为从数据库获取结果，使用方式由你自行决定。

保持 `user_list.php` 打开，为下一部分做准备——在那里你将在表格的第二行显示第一条记录。

#### 使用 Bindings 面板显示数据库结果

Recordset 服务器行为生成的代码会从数据库中提取第一行结果，以便直接显示。只需从 Bindings 面板中拖动这些值即可：

`1.` 保持 `user_list.php` 打开，打开 Bindings 面板（点击其标签页，或选择 Window > Bindings (Ctrl+F10/Cmd+F10)）。

`2` 你应在面板中看到 `getUsers` 记录集。如果需要，点击记录集名称旁的加号或三角形以展开所选 `users` 表的列名。

![Image](img/fig06_31.jpg)

`3.` 在 Bindings 面板中选择 `first_name`，并在设计视图的表格第二行第一列拖动它。这样会插入一个动态文本对象，如下图所示：

![Image](img/fig06_32.jpg)

动态文本对象会标识记录集和列名，便于辨认。

### TIP:

如果拖放操作困难，可在设计视图中定位光标，然后在 Bindings 面板中选中列名，点击面板右下角的 Insert 按钮。

4. 单击动态文本对象右侧，然后按空格键一次，在其旁边插入一个空格。

5. 从绑定面板中拖动 `family_name`，并将其放在 `first_name` 动态文本对象旁边。或者，只需在绑定面板中选择 `family_name`，然后点击插入按钮。

6. 使用任一方法在第二个单元格中插入 `username` 的动态文本对象。页面应如下所示：

![Image](img/fig06_33.jpg)

不要担心 `first_name` 和 `family_name` 动态文本对象叠在一起。动态文本对象是占位符，在 Live View 或浏览器中查看页面时不会指示它们的显示效果。在此情况下，每个动态文本对象代表一个单词，但在博客或产品目录中，动态文本对象可能代表多段文字。

7. 保存页面，然后点击 Live View。您应在 Live View 中看到数据库查询的第一条结果，它将取代动态文本对象的位置。

![Image](img/fig06_34.jpg)

关闭 Live View，保持 `user_list.php` 打开并准备好在下一部分进行编辑，届时您将修改页面以显示数据库的所有结果。

如果您想检查当前代码，请与 `lesson06/completed/user_list01.php` 进行比较。

### 使用重复区服务器行为显示多条记录

重复区服务器行为会创建一个 `do… while` 循环（见 第 3 课），用于遍历数据库查询的多条结果。该服务器行为提供了显示所有结果或限制最大记录数的选项：

1. 在第二个表格行的任何位置点击，然后在文档窗口底部的标签选择器中点击 `<tr>` 以选中整行。

![Image](img/fig06_35.jpg)

### TIP:

使用标签选择器是最准确选择 HTML 元素的方法。如果您拖动选择表格单元格，可能无法选中底层代码中的 `<tr>` 标签。未能正确选择完整的行会导致在应用重复区服务器行为时页面崩溃。

2. 在服务器行为面板中点击加号按钮，选择 `Repeat Region` 以打开以下对话框。

![Image](img/fig06_36.jpg)

页面上只有一组数据集，Dreamweaver 会自动选择正确的记录集值。

单选按钮让您选择显示的记录数量。默认值为 10，但您可以自行修改。也可以选择显示所有记录。

3. 目前 `users` 表中只有少量记录，因此保持默认设置并点击 `OK`。

4. 在设计视图中，您应看到第二个表格行的灰色边框，左上角有一个标签指示这是重复区。

5. 保存页面，然后点击 Live View。您应能看到两条记录均显示。

![Image](img/fig06_37.jpg)

如果操作不慎，表格可能会出现如下情况：

![Image](img/fig06_38.jpg)

这正是未能正确选择整行就应用重复区服务器行为时的结果。

您可以将您的代码与 `lesson06/completed/user_list02.php` 进行对比。

### 创建链接以选择特定记录

要更新或删除记录，需要过滤结果以定位目标记录。正如 第 5 课 所述，数据库中的每条记录都应有一个主键作为唯一标识符。您使用主键来定位特定记录：

1. 将 `lesson06/start/update_user.php` 和 `lesson06/start/delete_user.php` 复制到工作文件夹。

2. 继续使用 `user_list.php`（前一练习）。在设计视图中，选中第二个表格行中的文本 `EDIT`。这将成为指向 `update_user.php` 的链接。

3. 点击属性检查器中的“浏览文件夹”图标，在“选择文件”对话框中选择 `update_user.php`。不要点击 `OK`，因为您需要在 URL 末尾添加查询字符串。

4. 点击 URL 字段旁的 `Parameters` 按钮，打开 `Parameters` 对话框。

![Image](img/fig06_39.jpg)

5. 在对话框左侧的 `Name` 字段中输入 `user_id`。

6. 点击 `Value` 字段旁的灯泡图标（如下图所示），点击该图标打开 `Dynamic Data` 对话框。

![Image](img/fig06_40.jpg)

### CAUTION!

这是很多人出错的地方。灯泡图标会在每个字段被选中时出现。务必点击 `Value` 字段右侧的灯泡图标，而不是 `Name` 字段。

7. 如有必要，展开 `getUsers` 记录集，并选择 `user_id`。

![Image](img/fig06_41.jpg)

8. 点击 `OK` 关闭 `Dynamic Data` 对话框，然后点击 `OK` 关闭 `Parameters` 和 `Select File` 对话框。

9. 切换到代码视图，检查生成的链接，应类似于以下内容（约在第 76 行）：

```
<a href="update_user.php?user_id=<?php echo $row_getUsers['user_id']; ?>">EDIT</a>
```

查询字符串和 PHP 代码已被高亮显示。这表示在文件名后添加 `?user_id=`，随后的 PHP 代码插入当前记录的 `user_id`。

如果代码不符合此格式，请删除链接并重复步骤 2–8 进行修正。如果此部分错误，后续所有操作均无效。

10. 回到设计视图，选中第二行第四个单元格中的文本 `DELETE`，并按照相同方式为其创建指向 `delete_user.php` 的链接，并添加查询字符串。链接代码应如下所示：

```
<a href="delete_user.php?user_id=<?php echo $row_getUsers['user_id']; ?>">DELETE</a>
```

11. 保存 `user_list.php`，点击 `Live Code` 按钮进行测试。这将同时打开 Live View 和 Split 视图，显示 PHP 代码的输出。您应看到类似以下内容：

![Image](img/fig06_42.jpg)

查询字符串显示 `user_id=` 后跟每条记录的主键值，该值将用于标识要更新或删除的记录。

12. 点击 Live View 以关闭 Live Code 和 Live View。

您可以将代码与 `lesson06/complete/user_list03.php` 进行对比。

### 将记录加载到更新表单中

更新记录的过程包括以下步骤：

1. 使用 Recordset 服务器行为检索记录，并用其填充更新表单的输入字段。

2. 在表单中进行必要的修改。

3. 提交表单以更新数据库。

因此，您需要先使用 Recordset 服务器行为。本次使用查询字符串传递的值作为过滤条件。

1. 打开 `update_user.php`，在服务器行为面板中点击加号按钮，选择 `Recordset`。

2. 在 `Recordset` 对话框中使用以下设置。

![Image](img/fig06_43.jpg)

Recordset 服务器行为仅需要 `SELECT` 权限，但稍后将添加 `Update Record` 服务器行为，因此使用 `cs5write` 连接。

前面课时使用的 `sha1()` 函数对密码进行单向加密，也就是说无法解密，因此无需在更新表单中显示密码。

通过查询字符串传递的 `user_id` 用于选择正确的记录，因此 `Filter` 设置应将 SQL 查询的 `user_id` 列与 URL 参数 `user_id` 匹配。

由于只会选择一条记录，因此 `Sort` 设置为 `None`。

3. 点击 `OK` 关闭 `Recordset` 对话框。接下来需要将记录集的结果填充到表单字段中。

4. 在设计视图中选择“First name”文本字段。打开绑定面板，并在 `getUser` 记录集中选择 `first_name`。确保绑定面板底部的“Bind to”设置为 `input.value`（这应该会自动完成），然后点击绑定。

![Image](img/fig06_44.jpg)

这会在 `first_name` 的文本输入框中插入一个动态文本对象。

![Image](img/tip.jpg)

**TIP:**

如果你擅长拖放操作，可以在设计视图中从绑定面板拖动值并放在文本输入框上。Dreamweaver 会自动将动态文本对象绑定到 `<input>` 标签的 `value` 属性。

5. 重复步骤 4，对“Family name”（姓氏）和“Username”（用户名）文本字段进行操作，分别在绑定面板中选择 `family_name` 和 `username`。此时前三个文本字段中应已出现动态文本对象。

![Image](img/fig06_45.jpg)

6. 保存 `update_user.php`，然后切换到 `user_list.php`。

7. 启动 Live View，按住 Ctrl/Cmd 键，点击任意 EDIT 链接。应该看到更新表单，前三个字段的内容已从数据库中填充。

![Image](img/fig06_46.jpg)

注意：浏览器地址栏中的 Address 字段显示的查询字符串末尾包含 `user_id`。

8. 关闭 Live View。如果目前为止一切正常，即可在下一节中应用“更新记录”服务器行为。

你可以将你的代码与 `lesson06/completed/update_user01.php` 中的代码进行对比。

### 使用“更新记录”服务器行为

使用“更新记录”服务器行为与“插入记录”服务器行为非常相似。但需要手动处理密码。如果密码文本框为空，则使用已有的值；否则，对新密码进行加密后使用。

1. 需要在表单中保存主键的值，以便“更新记录”服务器行为知道要更新哪条记录。

在 `update_user.php` 设计视图中，将插入点置于表单内部任意位置，选择 `Insert > Form > Hidden field`（插入 > 表单 > 隐藏字段）。

2. 在属性检查器中，将隐藏字段的名称改为 `user_id`，然后点击值旁边的闪电图标打开“动态数据”对话框。

3. 从 `getUser` 记录集中选择 `user_id`，点击 `OK`。此过程与之前为 EDIT 和 DELETE 链接创建查询字符串时相同。

4. 在“服务器行为”面板中点击 `plus` 按钮，选择 `Update Record` 打开“更新记录”对话框。

需要使用 `cs5write` 连接，并选择 `users` 表。与“插入记录”服务器行为一样，需要将 `family_name` 列的值设置为 `FORM.surname`。

关键区别在于“更新记录”服务器行为会从隐藏字段获取主键。在“列”部分选择 `user_id`，并确认它使用 `FORM.user_id` 来定位记录。

将“更新后转到”设置为 `user_list.php`。

检查值是否与下面的截图一致，然后点击 `OK`。

![Image](img/fig06_47.jpg)

在此阶段保存页面很有必要，以防后续操作出错。

5. 切换到代码视图，剪切下面的代码行到剪贴板。仅用截图中的行号作参考；代码位置可能略有不同。

![Image](img/fig06_48.jpg)

这是记录集服务器行为生成的代码。它必须位于“更新记录”服务器行为代码之前，因为在将密码重新插入数据库时需要 `password` 列的值。

6. 向上滚动到下面的位置，在闭合大括号 `}` 与 `$editFormAction` 所在行之间的空白行上粘贴代码。

![Image](img/fig06_49.jpg)

7. 在粘贴代码后另起一行，添加以下内容：

```php
```
