

表单包含一个文本输入框、一个下拉菜单和两个多行文本域。文本输入框和多行文本域将使用 create_form_input() 函数创建。

## 15. 添加类别菜单：

```
<p><label for="category"><strong>Category</strong></label><br />
<select name="category"<?php if (array_key_exists('category',
$_add_page_errors)) echo ' class="error"'; ?>>
<option>Select One</option>
<?php // Retrieve all the categories and add to the pull-down menu:
$q = "SELECT id, category FROM categories ORDER BY category ASC";
$r = mysqli_query ($dbc, $q);
while ($row = mysqli_fetch_array ($r, MYSQLI_NUM)) {
echo "<option value="$row[0]">";
// Check for stickiness:
if (isset($_POST['category']) && ($_POST['category'] == $row[0]))
echo ' selected="selected"';
echo "$row[1]</option>\n";
}
?>
</select><?php if (array_key_exists('category', $_add_page_errors))
echo '<span class="error">' . $_add_page_errors['category'] .
'</span>'; ?><?php</p>
```

> 对于查询和查询结果，
> 我偏好使用简短的变量名——
> $q 和 $r，分别对应，但你
> 可能希望使用更
> 详细的名称，例如 $query
> 和 $result。

create_form_input() 函数并未设计用于处理下拉菜单。部分原因是它们与输入框和多行文本域差异较大，部分原因是网站上只有一个下拉菜单。因此，此代码必须复制该函数的所有逻辑，包括使表单保持粘性和显示错误（图 5-5）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_127_0.png)

图 5-5

## 16. 完成表单：

```
<p><label for="description"><strong>Description</strong></label>
</label><br /> <?php create_form_input('description', 'textarea',
$_add_page_errors); ?></p>
<p><label for="content"><strong>Content</strong></label>
<br /> <?php create_form_input('content', 'textarea',
$_add_page_errors); ?> </p>
<p><input type="submit" name="submit_button" value="Add This
Page" id="submit_button" class="formbutton" /></p>
</fieldset>
</form>
```

![](img/4f47e47c67bd619ac73250f11c9fc7ce_128_0.png)

这两个多行文本域也由 create_form_input() 函数生成，尽管多行文本域会在多行文本域框之前显示其错误（图 5.6），而文本输入框则是在之后显示错误。

- 17. 完成页面：
- <?php
- include('./includes/footer.html');
- ?>

- 18. 保存文件并在 Web 浏览器中加载它。
- 此时，表单将看起来与图 5.3 中的一样，只是 content 多行文本域将看起来像 description 的多行文本域。

## 添加所见即所得编辑器

如今基于 Web 的所见即所得编辑器非常常见，选择众多。要创建所见即所得编辑器，你需要在站点上安装编辑器代码，在表单中创建一个多行文本域，然后指定该编辑器应用于该多行文本域。目前最常见的两个所见即所得编辑器大概是 CKEditor（www.ckeditor.com，曾名为 FCKEditor，尽管 FCKEditor 仍可用）和 TinyMCE（http://tinymce.moxiecode.com）。我在不同项目中使用过这两者，它们大致相似。所有这些编辑器都使用 JavaScript 编写，是开源的，并拥有大量插件，用于添加拼写检查或花哨列表等功能。这些项目的文档尚可，如果你能遵循其中概述的正确语法，安装和自定义这些工具应该毫无问题。

> 提示
> 有可用的免费第三方文件管理插件，但我发现它们不如商业插件好。

所见即所得编辑器可以轻松创建样式化和格式化的 HTML，可包含任何有效标签，从列表到链接再到字体相关元素。所见即所得编辑器也可以轻松添加各种媒体，最常见的是图片和视频。不过，TinyMCE 和 CKEditor 都需要插件来管理文件上传，且在这两种情况下，插件均由同一家公司创建，是商业产品。因此，我未将该功能集成到此示例中。当你需要此功能时，只需查看所选所见即所得编辑器的相关文档即可。

- 1. 从 http://tinymce.moxiecode.com 下载 TinyMCE 的最新版本。

- 2. 从下载中提取文件。

- 3. 将提取的文件中的 tiny_mce 文件夹复制到你的 Web 根目录。

在执行步骤 2 提取文件后，结果将是一个名为 tinymce 的文件夹。其中包含 examples 和 js/scripts 文件夹。在 js/scripts 中是包含你实际需要的文件的 tiny_mce 文件夹。

- 4. 如果尚未打开，请在文本编辑器或 IDE 中打开 add_page.php。

- 5. 在表单结束标签之后，添加：

```
<script type="text/javascript" src="/tiny_mce/tiny_mce.js"></script>
```

首先需要包含主 tiny_mce.js 文件，这正是这一行所做的。

> 提示
> 如果将 JavaScript 放在文档末尾，网页加载速度会更快。

- 6. 在下一行，开始自定义 TinyMCE：

```
<script type="text/javascript">
tinyMCE.init({
// General options
mode : "exact",
elements : "content",
theme : "advanced",
width : 800,
height : 400,
```

这段 JavaScript 代码将把一个多行文本域转换为所见即所得编辑器。为此，将调用 tinyMCE 类的 init() 函数，并向其传递多个名称-值对。当然，你可以在 TinyMCE 文档中找到所有这些内容的详细说明，但我将重点介绍最重要的几点。exact 模式表示仅转换特定的多行文本域，而不是页面上的所有多行文本域。elements 值 content 指示应转换 id 值为 content 的多行文本域。这与已赋予 content 多行文本域的 name 和 id 值匹配。theme 决定使用哪些按钮和其他配置。你可以在文档和 examples 文件夹中查看不同的主题；此页面将使用 advanced 主题。width 和 height 属性更改编辑器的大小。

> 提示
> 不能使用同一个 <SCRIPT> 标签既包含单独的 JavaScript 文件，又编写内联 JavaScript 代码。

> 提示
> 你可以使用全局配置文件或在特定脚本中单独使用时自定义 TinyMCE 的行为。

- 7. 确定要使用的插件：

```
plugins : "advlink,advlist,autoresize,autosave,contextmenu,fullscreen,
iespell,inlinepopups,media,paste,preview,safari,searchreplace,
visualchars,wordcount,xhtmlxtras",
```

TinyMCE 拥有大量插件。这里我选择启用 16 个。

**提示**

将 `strip_tags()` 函数中允许的标签与编辑器中的按钮匹配。

- 8. 自定义编辑器的按钮：
-
- theme_advanced_buttons1 : "cut,copy,paste,pastetext,pasteword,l,
- undo,redo,removeformat,l,search,replace,l,cleanup,help,code,
- preview,visualaid,fullscreen",
- theme_advanced_buttons2 : "bold,italic,underline,strikethrough,l,
- justifyleft,justifycenter,justifyright,justifyfull,l,formatselect,l,bullist,
- numlist,l,outdent,indent,blockquote,l,sub,sup,cite,abbr",
- theme_advanced_buttons3 : "hr,l,link,unlink,anchor,image,l,charmap,
- emotions,iespell,media",
-

每一行表示在编辑器中创建的一行按钮（图 5.7）。TinyMCE 使用特定名称来创建特定按钮，其中大多数都很明显。使用管道字符（|）可以在一行内创建分隔符，以便你对相关按钮进行分组。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_130_0.png)

图 5.7

- 9. 完成自定义：
-
- theme_advanced_toolbar_location : "top",
- theme_advanced_toolbar_align : "left",
- theme_advanced_statusbar_location : "bottom",
- theme_advanced_resizing : true,
-

前三个设置决定工具栏和状态栏的位置和对齐方式。第四个表示编辑器应随内容增长而调整大小，这是一个不错的细节。

- 10. 完成脚本块：
-
- content_css : "/css/style.css",
- });
- </script>
-

你可以将站点的 CSS 文件与编辑器关联，以便在其中创建的内容在站点页面中显示时看起来相同。这正是这一行所做的。对 CSS 文件的引用可以是绝对路径，如本例所示，也可以是相对使用 TinyMCE 的页面的路径（而非相对 TinyMCE 文件夹）。

**提示**

如果编辑器未显示或未反映你的自定义设置，请确保刷新浏览器。如果问题仍然存在，原因可能是 JavaScript 中的语法错误。

- 11. 保存文件。

- 12. 在浏览器中重新加载网页以查看结果（见图 5-3）。

