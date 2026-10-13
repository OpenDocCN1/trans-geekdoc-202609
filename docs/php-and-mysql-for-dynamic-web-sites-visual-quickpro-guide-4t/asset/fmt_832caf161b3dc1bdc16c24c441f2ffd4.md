
如果文件已上传但无法移动到最终目标位置，或发生其他错误，该文件仍将保留在服务器的临时位置。要将其删除，请应用 `unlink()` 函数。为保险起见，在应用 `unlink()` 之前，条件语句会检查文件是否存在且是否为文件（因为如果指定项是目录，`file_exists()` 函数将返回 TRUE）。

**11.** 完成 PHP 部分：

```php
} // End of the submitted conditional.

?>
```

**12.** 创建 HTML 表单：

```html
<form enctype="multipart/form-data" action="upload_image.php" method="post">
  <input type="hidden" name="MAX_FILE_SIZE" value="524288" />
  <fieldset>
    <legend>Select a JPEG or PNG image of 512KB or smaller to be uploaded: </legend>
    <p><b>File:</b> <input type="file" name="upload" /></p>
  </fieldset>
  <div align="center"><input type="submit" name="submit" value="Submit" /></div>
</form>
```

该表单非常简单，但包含文件上传所需的三个必要部分：表单的 `enctype` 属性、`MAX_FILE_SIZE` 隐藏输入框和文件输入框。

**13.** 完成 HTML 页面：

```html
</body>
</html>
```

**14.** 将文件保存为 `upload_image.php`，将其放入 Web 目录，并在 Web 浏览器中测试。

![Image](graphics/11_figure_15_k.jpg)
成功上传并移动文件后的结果。

![Image](graphics/11_figure_16_l.jpg)
尝试上传过大文件时的结果。

如果需要，可以通过检查 `uploads` 目录的内容来确认脚本是否正常工作。

***

Tip

省略表单的 `enctype` 属性是导致文件上传神秘失败的常见原因。

***

Tip

也可以使用 `is_uploaded_file()` 函数验证上传文件是否存在。

***

Tip

Windows 用户引用目录时必须使用正斜杠或双反斜杠（即 `C:\\` 或 `C:/`，而非 `C:\`）。这是因为反斜杠是 PHP 中的转义字符。

***

Tip

如果新旧文件同名，`move_uploaded_file()` 函数将在不发出警告的情况下覆盖现有文件。

***

Tip

`MAX_FILE_SIZE` 是浏览器对文件大小的限制，但并非所有浏览器都遵守此限制。PHP 配置文件有其自身的限制。也可以在接收端的 PHP 脚本中验证上传文件的大小。

***

Tip

在 [第 13 章](#ch13.html#ch13) 中，你将学习一种通过更可靠地验证上传文件类型来提高脚本安全性的方法。

***

### PHP 和 JavaScript

尽管 PHP 和 JavaScript 是截然不同的技术，但它们可以结合使用以构建更好的网站。两者最显著的区别在于 JavaScript 主要是客户端技术（在 Web 浏览器中运行），而 PHP 始终是服务端技术。因此，JavaScript 可以检测浏览器窗口大小、创建弹出窗口、实现图像鼠标悬停效果等，而 PHP 无法做到这些。反之，PHP 可以在服务器上与 MySQL 交互，但 JavaScript 不能。

虽然 PHP 无法完成 JavaScript 能做的某些事情，但 PHP 可以用来生成 JavaScript，就像生成 HTML 一样。明确地说，在 Web 浏览器中，JavaScript 通过 HTML 引入并与其交互，但 PHP 可以动态生成 JavaScript 代码，正如你一直用 PHP 动态生成 HTML 那样。

为了演示这一点，将创建一个 PHP 脚本，列出由 `upload_image.php` 脚本上传的所有图像。该 PHP 脚本还将把每个图像名称创建为可点击的链接。这些链接将调用一个 JavaScript 函数，创建一个弹出窗口，在其中显示被点击的图像。此示例绝非对 JavaScript 的详尽讨论，但足以演示 PHP、HTML 和 JavaScript 等技术如何协同工作。在 [第 15 章](#ch15.html#ch15) “[jQuery 简介](#ch15.html#ch15)”中，你将学习如何使用 jQuery JavaScript 框架为基于 PHP 的脚本添加各种功能。

![Image](graphics/11_figure_17_a.jpg)
此 PHP 页面动态创建所有上传图像的列表。

![Image](graphics/11_figure_18_b.jpg)
每个图像的名称均作为调用 JavaScript 函数的链接。函数调用的参数由 PHP 创建。

#### 创建 JavaScript 文件

尽管 JavaScript 和 PHP 是两种不同的语言，但它们足够相似，即使没有接受过正规训练也能涉猎 JavaScript。在为本示例创建 JavaScript 代码之前，我将解释一些基础知识。

首先，JavaScript 代码可以通过两种方式添加到 HTML 页面：内联或通过外部文件。要添加内联 JavaScript，请将 JavaScript 代码放在 HTML `script` 标签之间：

```html
<script type="text/javascript">
  // Actual JavaScript code.
</script>
```

要使用外部 JavaScript 文件，请向 `script` 标签添加 `src` 属性：

```html
<script type="text/javascript" src="somefile.js"></script>
```

HTML 页面可以多次使用 `script` 标签，但每个标签只能包含外部文件或内联 JavaScript 代码，不能两者兼有。

如上所示，JavaScript 文件使用 `.js` 扩展名。该文件应使用与将包含它的 HTML 脚本相同的编码（在文本编辑器或 IDE 中设置）。可以在 `script` 标签中指定文件的编码：

```html
<script type="text/javascript" charset="utf-8" src="somefile.js"> </script>
```

无论将 JavaScript 代码放在 `script` 标签内还是外部文件中，都没有像 PHP 标签那样的 JavaScript 开始和结束标签。

其次，JavaScript 中的变量区分大小写，这与 PHP 相同，但 JavaScript 变量不以美元符号开头。

最后，JavaScript 和 PHP 的主要区别之一是 JavaScript 是一门面向对象编程（OOP）语言。PHP 既可用于过程式方法（本书大部分内容演示的方法），也可用于面向对象方法（见 [第 16 章](#ch16.html#ch16) “[OOP 入门](#ch16.html#ch16)”），而 JavaScript 始终是面向对象语言。这意味着你将看到类似 `something.something()` 或 `something.something.something` 的“点”语法。

基础知识就介绍到这里；在下面的脚本中，我将详细解释每段代码的细节。在接下来的步骤中，你将创建一个单独的 JavaScript 文件，定义一个 JavaScript 函数。该函数接受三个参数——图像的名称、宽度和高度。函数将使用这些值为该图像专门创建一个弹出窗口。

#### 使用 PHP 创建 JavaScript

**1.** 在文本编辑器或 IDE 中创建一个新的 JavaScript 文档，命名为 `function.js`（**[脚本 11.3](#ch11.html#ch11ex03)**）：

```javascript
// Script 11.3 - function.js
```

同样，这里没有开始 JavaScript 标签，你可以直接开始编写 JavaScript 代码。JavaScript 中的注释可以使用单行（`//`）或多行（`/* */`）语法。

**2.** 开始定义 JavaScript 函数：

```javascript
function create_window (image, width, height) {
```
