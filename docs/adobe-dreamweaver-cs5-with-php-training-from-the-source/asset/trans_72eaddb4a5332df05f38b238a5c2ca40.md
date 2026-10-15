
-   [Dreamweaver 按下 Enter/Return 键后，会自动补全函数名称和左括号。即使该函数在另一页面定义，Dreamweaver 也能识别它并生成代码提示，因为页面之间已建立链接。在开头括号后输入 **$db**，然后从代码提示列表中选择 `$dbRead`。输入右括号和分号。完成的行应如下所示：  

$states = getAllStates($dbRead);

The `getAllStates()` 函数返回的结果来自 SQL 查询，现已存储为多维数组 `$states`。

**5.** 单击 Related Files 工具栏中的 Source Code 以切换到 insert_place.php 中的 HTML 代码，或在另存为标签页时选择页面标签。找到 `<select>` 菜单（大约在第 40–41 行），并在打开和关闭标签之间插入以下 PHP 代码：

<select name="state_id" id="state_id">  

**<?php **  

**foreach ($states as $row) {**  

   **echo "<option value='{$row\['state_id'\]}'";**  

   **if ($errors && $_POST['state_id'] == $row\['state_id'\]) {**  

      **echo 'selected="selected"';**  

   **}**  

   **echo ">{$row\['state_name'\]}</option>";**  

**} **  

**?>**  

</select>

`foreach` 循环遍历 `$states` 数组，将其赋值给临时变量 `$row`。每次循环运行时，`$row` 包含 SQL 查询结果中的一条记录，列名作为数组键使用。因此，`$row[‘state_id’]` 保存当前 `state_id` 的值，`$row[‘state_name’]` 保存同一行的 `state_name`。

`$row[‘state_id’]` 被插入 `value` 属性，`$row[‘state_name’]` 显示在 `<option>` 标签之间。如果 `$errors` 数组为 `TRUE`，条件语句会比较 `$_POST[‘state_id’]` 与 `$row[‘state_id’]`，若相等则在打开的 `<option>` 标签中插入 `selected=”selected”`。

用 plain English 说明，这段代码使用从 `states` 表检索的所有记录来填充 `<select>` 菜单。如果表单提交时出现错误，菜单会自动选中用户选择的值。

**6.** 保存所有相关文件并点击 Live View。你应该能在菜单中看到 Alabama。

![image](graphics/fig10_13.jpg)

点击菜单展开，你会看到 50 个州加上哥伦比亚特区的全部列表。比手动一个一个输入要轻松得多！

### ![image](graphics/tip.jpg)**TIP:**

如果出现问题，请将你的代码与 lesson10/completed/insert_place_02.php 对比，该文件只包含一个稍后将在下一步中修改的微小更改。

**7.** 退出 Live View，并在步骤 5 中插入的 PHP 代码大约第 44 行找到以下语句：

if ($errors && $_POST['state_id'] == $row['state_id']) {

将 `$_POST['state_id']` 中的单引号改为双引号，如下：

if ($errors && $_POST["state_id"] == $row['state_id']) {

这对代码功能没有实质影响，但使用双引号可以在将整个代码块转换为服务器行为时更方便地通过对话框嵌入 `$i`，而无需再进入代码视图。

**8** 保存 insert_place.php，并将修改后的 PHP 块复制到剪贴板。

**9.** 在 Server Behaviors 面板中点击加号按钮，选择 New Server Behavior，命名为 **Zend Select Menu**，然后点击 OK。

**10** 点击 “Code blocks to insert” 旁边的加号，接受 Dreamweaver 建议的名称。

**11** 在 “Code block” 文本框中替换占位文字，粘贴剪贴板中的 PHP 代码。

**12** 将下列变量转换为服务器行为参数：

• `$states`: **`@@Array Variable@@`**

• `$row[‘state_id’]`: `$row[‘`**`@@Value@@`**`’]`

• `$_POST[“state_id”]`: `$_POST[“`**`@@Menu Name@@`**`”]`

• `$row[‘state_name’]`: `$row[‘`**`@@Display@@`**`’]`

修改后的代码应如下所示：

<?php   

foreach (**`@@Array Variable@@`** as $row) {  

  echo "<option value='{$row\['**@@Value@@**'\]}'";  

  if ($errors && $_POST\["**@@Menu Name@@**"\] == $row\['**@@Value@@**'\]) {  

    echo 'selected="selected"';  

  }  

  echo ">{$row\['**@@Display@@**'\]}</option>";  

}   

?>

这些参数将在服务器行为的对话框中作为标签使用，帮助你快速构建动态 `<select>` 菜单。

**13** 在面板底部使用以下选项：

• **Insert code:** Relative to a Specific Tag

• **Tag:** select

• **Relative position:** Before the Closing Tag

选择 “Before the Closing Tag” 可在 `<select>` 菜单内部插入一个静态 `<option>`，位于循环之前。

**14** 点击 Next。Dreamweaver 会提供新服务行为对话框的建议，这些建议基本可接受。选择 Menu Name，使用右上角的上箭按钮将其移至 “select tag” 之上，然后点击 OK。

![image](graphics/fig10_14.jpg)

稍后在完成 insert_photos.php 时，你会再次使用此服务行为。

#### 在 places 表中插入详细信息

insert_place.php 的表单用于插入新地点的信息以及最多三张相关图片和说明。从用户视角来看，整个操作应是一次无缝的动作。实际上，过程分为很多阶段，脚本需要执行的步骤如下：

**1.** 表单提交时，验证文本字段。若出现错误，立即停止处理并重新显示表单，同时在字段中保留已输入内容并显示错误信息。

**2.** 检查数据库中是否已有同名记录。若已存在，停止处理并重新显示表单。

**3.** 上传图片。若任何图片验证失败，则放弃上传过程并重新显示表单。

**4.** 若文本和图片均通过验证，将数据插入 `places` 表。

**5.** 若数据插入成功且未检测到图片，则重新显示表单，并提示“地点已成功插入数据库”。

**6.** 若检测到图片，需查询数据库获取新地点的主键。

**7.** 遍历图片。每次循环执行以下操作：

- 将文件名和说明插入 `photos` 表。

- 查询数据库获取该图片的主键。

- 将两个主键作为一对插入 `place2photo` 表。

**8.** 报告图片上传成功以及新地点插入数据库的消息。

此过程涉及 130 行以上代码。大部分代码在之前的课程中已使用过，因此可以通过编辑已有脚本、复制粘贴来节省时间。如果需要休息，现在也是一个好时机。好消息是，其他脚本大量复用了这段代码，且相对更短。

如果你已经准备好，让我们开始吧。

**1.** 脚本的第一项任务是验证文本字段。由于插入照片的表单和更新现有记录的表单也需要验证，建议创建可重用的自定义函数。在 db_definitions.php 中添加以下函数定义：

function validatePlaceName($name, &$errors) {  

  $val = new Zend\_Validate\_Regex('/^\[a-z\]+\[-\\’a-z \]+$/i’);  

  if (!$val->isValid($name)) {  

    $errors\['name’\] = 'Place name is required: no special characters';  

  }  

}
