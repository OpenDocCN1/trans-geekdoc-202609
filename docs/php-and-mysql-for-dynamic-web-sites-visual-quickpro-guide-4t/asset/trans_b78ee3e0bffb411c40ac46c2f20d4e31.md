

## 14. 开始艺术家下拉菜单

**艺术家：**

```html
<select name="artist">
  <option>Select One</option>
```

艺术家下拉菜单将使用此 PHP 代码，根据存储在 `artists` 表中的记录动态生成。

## 15. 检索每一位艺术家

```php
<?php
$q = "SELECT artist_id, CONCAT_WS(' ', first_name, middle_name, last_name) FROM artists ORDER BY last_name, first_name ASC";
$r = mysqli_query($dbc, $q);

if (mysqli_num_rows($r) > 0) {
    while ($row = mysqli_fetch_array($r, MYSQLI_NUM)) {
        echo "<option value=\"$row[0]\"";
        // 检查粘性：
        if (isset($_POST['existing']) && ($_POST['existing'] == $row[0])) echo ' selected="selected"';
        echo ">$row[1]</option>\n";
    }
} else {
    echo '<option>Please add a new artist first.</option>';
}

mysqli_close($dbc); // 关闭数据库连接。
?>
</select>
```

此查询从数据库中检索每位艺术家的姓名和 ID（它未使用预处理语句，因为实际上并不需要）。MySQL `CONCAT_WS()` 函数——即 *concatenate with separator*（使用分隔符连接）的缩写——用于将艺术家的全名作为单个值检索。如果您对查询的语法感到困惑，请在 mysql 客户端或其他界面中运行它以查看结果。

如果数据库中没有现有的艺术家，则该下拉菜单将没有任何选项，因此会显示一条添加艺术家的提示。

由于希望使下拉菜单具有粘性，这段原本基础的代码变得复杂起来。要使任何 `select` 菜单具有粘性，必须向适当的选项添加 `selected="selected"`。因此，`while` 循环中的代码会检查 `$_POST['existing']` 是否已设置，如果已设置，则检查其值是否与正在添加到菜单中的当前艺术家 ID 相同。

## 16. 完成 HTML 表单

```html
<p><b>Price:</b> <input type="text" name="price" size="10" maxlength="10" value="<?php if (isset($_POST['price'])) echo $_POST['price']; ?>" /> <small>Do not include the dollar sign or commas.</small></p>
<p><b>Size:</b> <input type="text" name="size" size="30" maxlength="60" value="<?php if (isset($_POST['size'])) echo htmlspecialchars($_POST['size']); ?>" /> (optional)</p>
<p><b>Description:</b> <textarea name="description" cols="40" rows="5"><?php if (isset($_POST['description'])) echo $_POST['description']; ?></textarea> (optional)</p>
</fieldset>
<div align="center"><input type="submit" name="submit" value="Submit" /></div>
</form>
```

关于每个表单元素的细节，例如描述为可选项，或价格不应包含美元符号，有助于管理员正确填写表单。

## 17. 完成 HTML 页面

```html
</body>
</html>
```

## 18. 将文件保存为 `add_print.php`。

## 19. 如果尚未在服务器上创建必要的目录，请创建它们。

此管理页面需要创建两个新目录。一个我将其称为 `admin`（参见参考），用于存放管理文件本身。在实际网站上，最好给管理目录起一个不那么显眼的名称。

第二个目录 `uploads` 应放置在 Web 文档目录之下，并修改其权限，以便 PHP 可以将文件移入其中。有关更多信息，请参阅 [第 10 章](#ch10.html#ch10)。

## 20. 将 `add_print.php` 放置在您的 Web 目录中（在管理文件夹内），并在 Web 浏览器中测试它。

## 脚本 19.3. 头部文件创建初始 HTML 并启动 PHP 会话。

---

### 创建公共模板

在着手处理公共端的核心部分之前，应先创建必需的 HTML 头部和尾部文件。我将快速过一遍这些内容，因为到本书此处，所涉及的技术应该已是熟悉的领域。

#### 创建 header.html

**1.** 在文本编辑器或 IDE 中开始一个新的 PHP 文档，命名为 `header.html`（**[脚本 19.3](#ch19.html#ch19ex03)**）：

```php
<?php # Script 19.3 - header.html
```

**2.** 启动会话：

```php
session_start();
```

在每个页面上维护用户的会话非常重要，因此会话将在头部文件中启动。如果在某个页面上丢失了会话，则后续页面将开始一个新会话，用户的历史记录——购物车的内容——将会丢失。

**3.** 创建 HTML 头部：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <title><?php echo (isset($page_title)) ? $page_title : 'Welcome!'; ?></title>
</head>
```

与该脚本的所有其他版本一样，页面标题将作为 PHP 变量设置，并打印在 `title` 标签内。以防在包含此页面之前未设置标题，也提供了一个默认标题。

**4.** 创建表格的顶行：

```html
<body>
<table cellspacing="0" cellpadding="0" border="0" align="center" width="600">
  <tr>
    <td align="center" colspan="3"><img src="images/title.jpg" width="600" height="61" border="0" alt="title" /></td>
  </tr>
  <tr>
    <td><a href="index.php"><img src="images/home.jpg" width="200" height="39" border="0" alt="home page" /></a></td>
    <td><a href="browse_prints.php"><img src="images/prints.jpg" width="200" height="39" border="0" alt="view the prints" /></a></td>
    <td><a href="view_cart.php"><img src="images/cart.jpg" width="200" height="39" border="0" alt="view your cart" /></a></td>
  </tr>
```

此布局将使用图像为公共页面创建链接。

![Image](graphics/19_figure_16_a.jpg)

由头部文件创建的横幅。

**5.** 开始中间行：

```html
<tr>
  <td align="left" colspan="3" bgcolor="#ffffcc"><br />
```

每个单独页面的所有内容都将放在中间行中；头部文件开始此行，尾部文件将关闭它。

