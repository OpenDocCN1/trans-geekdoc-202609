
```
<?php
$photofields = 3;
```

**7** 从 `lesson10/start/scripts` 复制 `db_insert_photos.php` 到 `cms/scripts`。该文件包含你在之前课程中已经熟悉的骨架代码：

```
<?php  

$errors = array();  

require_once('library.php');  

try {  

} catch (Exception $e) {  

    echo $e->getMessage();  

}
```

**8** 在 `try` 块内使用 `require_once()` 包含 `db_definitions.php`：

```php
try {

    require_once('db_definitions.php');

} catch (Exception $e) {
```

**9** 保存 `db_insert_photos.php`，并在此文件夹中再复制四份，分别保存为 `db_delete_place.php`、`db_insert_place.php`、`db_update_photo.php` 和 `db_update_place.php`。所有这五个脚本都使用将在 `db_definitions.php` 中定义的内容。

**10** 关闭除 `db_definitions.php` 和 `insert_photos.php` 之外的所有文件。

**11** 选择 `insert_photos.php` 的标签，并在 `DOCTYPE` 声明上方使用 `require_once()` 包含 `scripts/db_insert_photos.php`。这将间接包含 `db_definitions.php`，从而让你能够使用 `$photofields` 控制循环以重复表单字段。

**12** 在设计视图中，选择“Caption 1”的文本输入框，并应用在 Lesson 7 中创建的“错误时重新显示”服务器行为。在“字段名称”字段中输入 `caption1`。

**13** 切换到代码视图，并用 `for` 循环包围文件域、文本输入框以及 `<select>` 菜单，方式如下：

```
<?php for ($i = 1; $i <= $photofields; $i++) { ?>

<p>

    <label for="photo1">Photo 1:</label>

    <input type="file" name="photo1" id="photo1" />

</p>

<p>

    <label for="caption1">Caption for photo 1</label>

    <input value="<?php if ($POST && $errors) {

        echo htmlentities($POST['caption1'], ENT_COMPAT, 'UTF-8');

    }?>" type="text" name="caption1" id="caption1" />

</p>

<p>

    <label for="place_id1">Associate photo 1 with:</label>

    <select name="place_id1" id="place_id1">

        <option value="0">-- Select place --</option>

    </select>

</p>

<?php } ?>
```

![image](img/caution.jpg)CAUTION!

每个表单元素都被 `<p>` 标签包裹。确保在循环中包含第一个开头标签和最后一个结束标签。提交按钮应保持在循环之外。

**14** 保存页面并在此“实时预览”或浏览器中测试。你现在应该有三组输入字段。问题是它们都指向“Photo 1”。

**15** 使用 `for` 循环的原因是利用计数器 `$i`，它从 1 开始初始化，而不是从 0，这样照片在屏幕上会显示为 1、2、3。顺便说明，循环的第二个参数使用 `$i <= $photofields`，如果使用 `$i < $photofields`，循环只会运行两次。

与其手动输入所有代码，请选择“编辑 > 查找并替换”或按 `Ctrl+F`/`Cmd+F` 打开“查找并替换”对话框。

**17** 点击“查找下一项”两次。前两个实例位于表单的打开标签中，你不想修改它们。

下一次点击“查找下一项”时，Dreamweaver 会高亮下一行中的 `1`：

`<label for="photo1">Photo 1:</label>`

点击“替换”。Dreamweaver 将代码更改为：

`<label for="photo<?php echo $i; ?>">Photo 1:</label>`

更改代码后，Dreamweaver 会跳转到下一个实例。再次点击“替换”，并继续这样操作，直到 Dreamweaver 到达表单的末尾。查找并替换对话框应报告找到 11 项，其中 9 项已被替换。

**18** 在关闭查找并替换对话框前，选中“替换”字段中的 PHP 代码（不包括双引号），按 `Ctrl+C`/`Cmd+C` 将其复制到剪贴板。

**19** 在代码视图中，按 `Ctrl+V`/`Cmd+V` 粘贴代码，替换三个 `<label>` 标签中的数字 1。第一个 `<label>` 标签应如下所示：

`<label for="photo<?php echo $i; ?>">Photo <?php echo $i; ?>:</label>`

**20** 仍需修复一个实例，它位于由“错误时重新显示”服务器行为创建的代码中（约在第 40 行）：

`echo htmlentities($_POST['caption1'], ENT_COMPAT, 'UTF-8');`

查找并替换对话框没有找到它的原因是服务器行为使用了单引号。此外，此行代码已经在 PHP 块内部，无法粘贴之前用于其他实例的代码。将 `$_POST['caption1']` 中的单引号改为双引号，并嵌入 `$i`，如下：

`echo htmlentities($_POST["caption{$i}"], ENT_COMPAT, 'UTF-8');`

使用双引号并用大括号包裹 `$i`，可以生成 `$_POST["caption1"]`、`$_POST["caption2"]` 等。

**21** 保存 `insert_photos.php` 并在此“实时预览”或浏览器中测试。你现在应该有三组照片输入字段。

![image](img/fig10_11.jpg)

**22** 点击 Dreamweaver 的“实时代码”或检查浏览器的源代码。`for`、`name` 和 `id` 属性应全部以正确的数字结尾。

`<select>` 菜单目前不可用，但稍后会处理。你可以将代码与 `lesson10/completed/insert_photos_01.php` 进行比较。

**23** 关闭 `insert_photos.php`，打开 `insert_place.php`。你需要以同样的方式为照片输入字段创建循环。

首先，在 `DOCTYPE` 声明上方使用 `require_once()` 包含 `scripts/db_insert_place.php`。

**24** 在这页中，只有两个字段与照片相关：文件域和用于说明的文本输入框。将它们包裹在 `for` 循环中，方式如下：

```
<?php for ($i = 1; $i <= $photofields; $i++) { ?>

<p>

    <label for="photo1">Photo 1:</label>

    <input type="file" name="photo1" id="photo1" />

</p>

<p>

    <label for="caption1">Caption for photo 1:</label>

    <input value="<?php if ($POST && $errors) {

        echo htmlentities($POST['caption1'], ENT_COMPAT, 'UTF-8');

    }?>" type="text" name="caption1" id="caption1" />

</p>

<?php } ?>
```
