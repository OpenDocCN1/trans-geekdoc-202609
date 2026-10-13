
# 代码示例：images.php

```html
TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/
xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="Content-Type"
        content="text/html; charset=utf-8" />
  <title>Images</title>
  <script type="text/javascript" charset=
          "utf-8" src="js/function.js"></script>
</head>
<body>
<p>Click on an image to view it in a
separate window.</p>
<ul>
<?php # Script 11.4 - images.php
// This script lists the images in the
// uploads directory.

$dir = '../uploads'; // Define the
// directory to view.

$files = scandir($dir); // Read all the
// images into an array.

// Display each image caption as a link
// to the JavaScript function:
foreach ($files as $image) {

  if (substr($image, 0, 1) != '.') { //
    // Ignore anything starting with a period.

    // Get the image's size in pixels:
    $image_size = getimagesize
      ("$dir/$image");

    // Make the image's name URL-safe:
    $image_name = urlencode($image);

    // Print the information:
    echo "<li><a href=\"javascript:
      create_window('$image_name',
      $image_size[0],$image_size[1])\">
      $image</a></li>\n";

  } // End of the IF.

} // End of the foreach loop.
?>
</ul>
</body>
</html>
```

---

## 步骤解析

### 3. 完成 HTML 头部并开始 body 部分

```html
</head>

<body>
<p>Click on an image to view it in a separate window.</p>
```

### 4. 开始 HTML 无序列表

```html
<ul>
```

为了简单起见，该脚本将每个图像作为无序列表中的一个项目显示。

### 5. 启动 PHP 代码并通过引用 `uploads` 目录创建图像数组

```php
<?php # Script 11.4 - images.php
$dir = '../uploads';
$files = scandir($dir);
```

该脚本将自动列出并链接存储在 `uploads` 文件夹中的所有图像（推测是由 **`upload_image.php`** 放置的，参见 [Script 11.3](#ch11.html#ch11ex03)）。代码首先将目录定义为一个变量，以便于引用。然后 **`scandir()`** 函数（该函数返回在文件夹中找到的文件和目录的数组）将该信息赋值给名为 **`$files`** 的数组。

### 6. 开始遍历 **`$files`** 数组

```php
foreach ($files as $image) {
  if (substr($image, 0, 1) != '.') {
```

此循环将遍历数组中的每个图像并为其创建一个列表项。在循环内部，有一个条件判断，检查文件名的第一个字符是否为句点。在非 Windows 系统中，隐藏文件以句点开头，当前目录用单个句点表示，两个句点表示父目录。由于所有这些都可能包含在 **`$files`** 中，因此需要将它们剔除。

### 7. 获取图像信息并对其名称进行编码

```php
$image_size = getimagesize ("$dir/$image");
$image_name = urlencode($image);
```

**`getimagesize()`** 函数返回一个包含图像信息的数组（参见 [表 11.3](#ch11.html#ch11table03)）。该函数返回的值将用于设置发送给 JavaScript **`create_window()`** 函数的宽度和高度。

接下来，**`urlencode()`** 函数使字符串可以安全地在 URL 中传递。因为图像名称可能包含 URL 中不允许的字符（并且在调用 **`show_image.php`** 时将在 URL 中传递），所以名称应进行编码。

### 8. 打印列表项

```php
echo "<li><a href=\"javascript: create_window('$image_name', $image_size[0],$image_size[1])\"> $image</a>\n";
```

最后，循环创建 HTML 列表项，由链接的图像名称组成。链接本身是对 JavaScript **`create_window()`** 函数的调用。为了在 HTML 中执行 JavaScript 函数，请在其前面加上 **`javascript:`**。（在 HTML 中调用 JavaScript 还有更多内容，但目前只需使用此语法。）

该函数的三个参数分别是：图像名称、图像宽度和图像高度。因为图像名称是字符串，所以必须用引号括起来。

### 9. 完成 `if` 条件、`foreach` 循环和 PHP 部分

```php
} // End of the IF.
} // End of the foreach loop.
?>
```

### 10. 完成无序列表和 HTML 页面

```html
</ul>
</body>
</html>
```

### 11. 保存文件并测试

将文件保存为 **`images.php`**，将其放在您的 Web 目录中（与 **`upload_image.php`** 位于同一目录），并在 Web 浏览器中测试。

请注意，单击链接目前还不起作用，因为 **`show_image.php`**（弹出窗口尝试加载的页面）尚未创建。

### 12. 查看源代码以查看动态生成的链接

请注意每个函数调用的参数如何适合特定图像。

---

## 提示

不同的浏览器处理窗口大小调整的方式不同。例如，在我的测试中，Google Chrome 始终要求窗口至少具有特定宽度，而 Internet Explorer 9 会在四周填充显示的图像。

---

## 提示

某些版本的 Windows 会在图像文件夹中创建 **`Thumbs.db`** 文件。您可能需要在第 6 步剔除某些返回项的条件判断中检查此值。代码如下：

```php
if ( (substr($image, 0, 1) != '.') && ($image != 'Thumbs.db') ) {
```

---

## 提示

不想过分强调，但 Web 开发人员使用 JavaScript 所做的大多数事情（例如，调整或移动浏览器窗口）都无法使用服务端的 PHP 完成。

---

## 提示

PHP 和 JavaScript 之间*略有*重叠。两者都可以设置和读取 Cookie、创建 HTML 以及进行一些浏览器检测。

---

# 理解 HTTP 头部

刚创建的 **`images.php`** 脚本显示图像名称列表，每个名称都链接到一个 JavaScript 函数调用。该 JavaScript 函数创建一个弹出窗口，加载一个将实际显示图像的 PHP 脚本。这听起来可能是小题大做，但其中自有深意。采用这种方法的一个次要原因是，需要 JavaScript 才能创建一个适合图像大小的窗口（而不是创建任意大小的弹出窗口，其中包含图像）。更为重要的是，因为图像存储在 **`uploads`** 目录中，理想情况下存储在 Web 根目录之外，所以无法在 Web 浏览器中直接使用以下任一方式查看图像：

- `http://www.example.com/uploads/image.png`
- `<img src="image.png" />`

上述两种方式均无效的原因是，根据定义，位于 Web 根目录之外的文件和文件夹无法通过 Web 浏览器访问。这实际上是一件好事，因为它允许您保护内容，仅在适当的时候提供内容。要通过 Web 浏览器使该内容可用，您需要在 PHP 中创建一个*代理脚本*。代理脚本只需履行一个角色，例如提供文件（显示图像实际上就是向浏览器提供文件）。因此，给定代理脚本 **`proxy.php`**，上述示例可以通过以下任一方式工作：

- `http://www.example.com/proxy.php?image=image.png`
- `<img src="proxy.php?image=image.png" />`

![图 11-21：代理脚本能够提供对服务器上原本不可用内容的访问](graphics/11_figure_21_a.jpg)

代理脚本能够提供对服务器上原本不可用内容的访问。
