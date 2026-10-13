
JavaScript `create_window()` 函数将接受三个参数：图像的名称、宽度和高度。当用户点击链接时，这些参数中的每一个都将被传递给该函数。图像名称、宽度和高度的确切值将由 PHP 确定。

在 JavaScript 中创建函数的语法与 PHP 中的用户定义函数非常相似，只是变量前没有初始的美元符号。

### 3. 将接收到的 `width` 和 `height` 值各增加十个像素：

```javascript
width = width + 10;
height = height + 10;
```

将向宽度和高度值添加一些像素，以创建一个比图像本身稍大的窗口。JavaScript 中的数学运算使用的运算符与几乎所有语言中的相同。

### 4. 如果弹出窗口已打开，则调整其大小：

```javascript
if (window.popup && !window.popup.closed) {
  window.popup.resizeTo(width, height);
}
```

**脚本 11.3。** `function.js` 脚本定义了一个用于创建弹出窗口的 JavaScript 函数，该窗口将显示单个图像。

---

```javascript
1  // 脚本 11.3 - function.js
2
3  // 创建弹出窗口函数：
4  function create_window(image, width,
      height) {
5
6      // 向宽度和高度添加一些像素：
7      width = width + 10;
8      height = height + 10;
9
10     // 如果窗口已经打开，
11     // 将其调整为新尺寸：
12     if (window.popup && !window.popup.
      closed) {
13         window.popup.resizeTo(width, height);
14     }
15
16     // 设置窗口属性：
17     var specs = "location=no,
      scrollbars=no, menubars=no,
      toolbars=no, resizable=yes,
      left=0, top=0, width=" + width + ",
      height=" + height;
18
19     // 设置 URL：
20     var url = "show_image.php?image=" +
      image;
21
22     // 创建弹出窗口：
23     popup = window.open(url, "ImageWindow",
      specs);
24     popup.focus();
25
26 } // 函数结束。
```

---

稍后在函数中，将创建一个窗口并与 `popup` 变量关联。如果用户点击一个图像名称，创建了弹出窗口，然后在未关闭第一个弹出窗口的情况下点击另一个图像的名称，新图像将显示在一个尺寸不合适的窗口中。为防止这种情况，此处的一段代码首先检查弹出窗口是否存在以及是否未关闭。如果这两个条件均为 TRUE（即窗口已打开），则将根据新图像的尺寸调整窗口大小。这是通过调用 `popup` 对象的 `resizeTo()` 方法来实现的（*方法* 是面向对象编程中对函数的称呼）。

### 5. 确定弹出窗口的属性：

```javascript
var specs = "location=no, scrollbars=no, menubars=no, toolbars=no, resizable=yes, left=0, top=0, width=" + width + ", height=" + height;
```

此行创建一个名为 `specs` 的新 JavaScript 变量。变量名前的 `var` 关键字是在函数内创建变量的首选方式（具体来说，它创建一个*局部于*该函数的变量）。请注意，`image`、`width` 和 `height` 变量未使用此关键字，因为它们是作为函数的参数创建的。

此变量将用于确定弹出窗口的属性。该窗口将没有地址栏、滚动条、菜单或工具栏；它应该是可调整大小的；它将位于屏幕的左上角；并且其宽度为 `width`，高度为 `height` ![Image](graphics/circle-c.jpg)。

![Image](graphics/11_figure_19_c.jpg)

![Image](graphics/circle-c.jpg)由 JavaScript 创建的弹出窗口。

在 JavaScript 中，字符串使用加号进行连接（而 PHP 使用句点）。

### 6. 定义 URL：

```javascript
var url = "show_image.php?image=" + image;
```

此代码设置弹出窗口的 URL，即指定窗口应加载的页面。该页面是 `show_image.php`，将在本章后面创建。`show_image.php` 脚本期望在 URL 中接收图像的名称，因此 `url` 变量的值是 `show_image.php?image=` 加上连接在末尾的图像名称 ![Image](graphics/circle-d.jpg)。

![Image](graphics/11_figure_20_d.jpg)

![Image](graphics/circle-d.jpg)弹出窗口的地址显示了图像值如何在 URL 中传递。

### 7. 创建弹出窗口：

```javascript
popup = window.open(url, "ImageWindow", specs);
popup.focus();
```

最后，使用 `window` 对象的 `open()` 方法创建弹出窗口。`window` 对象是由浏览器创建的全局 JavaScript 对象，用于引用打开的窗口。`open()` 方法的第一个参数是要加载的页面，第二个是赋予窗口的标题，第三个是属性列表。请注意，此窗口的创建被赋值给了 `popup` 变量。因为该变量的创建不以关键字 `var` 开头，所以 `popup` 将是一个全局变量。这是必需的，以便该函数的多次调用能够引用同一个变量。

最后，将焦点给予新窗口，意味着它应出现在当前窗口之上。

### 8. 将脚本另存为 `function.js`。

### 9. 将该脚本或其副本放置在 Web 目录的 `js` 文件夹中。

JavaScript 与 CSS 一样，在整理 Web 目录时应当分离出来。通常，外部 JavaScript 文件放置在名为 `js`、`javascript` 或 `scripts` 的文件夹中。

## 创建 PHP 脚本

现在，页面所需的 JavaScript 代码已创建完毕，是时候创建 PHP 脚本本身了（它将输出调用 JavaScript 函数的 HTML）。该脚本的目的是列出所有已由 `upload_image.php` 上传的图像。为此，PHP 需要动态检索 `uploads` 目录的内容。这可以通过 `scandir()` 函数完成。它返回一个数组，列出给定目录中的文件（该函数在 PHP 5 中添加）。

PHP 脚本必须将显示的每个图像名称链接为对刚才定义的 JavaScript 函数的调用。该函数期望接收三个参数：图像的名称、宽度和高度。为了让 PHP 找到后两个值，脚本将使用 `getimagesize()` 函数。它返回给定图像的信息数组（**[表 11.3](#ch11.html#ch11table03)**）。

### 表 11.3. `getimagesize()` 数组

![Image](graphics/11tab03.jpg)

## 使用 PHP 创建 JavaScript

### 1. 在文本编辑器或 IDE 中开始一个新的 PHP 文档，命名为 `images.php`（**[脚本 11.4](#ch11.html#ch11ex04)**）：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
  <title>Images</title>
```

### 2. 包含 JavaScript 文件：

```html
<script type="text/javascript" charset="utf-8" src="js/function.js"></script>
```

你可以在 HTML 页面的任何位置使用 `script` 标签，但外部文件的引入通常在文档的 head 部分进行。对 `function.js` 的引用假设该文件将在 `js` 目录中找到，而 `js` 目录位于当前脚本所在的同一目录中（参见 ![Image](graphics/graycircle-d.jpg)“[处理文件上传](#ch11.html#ch11lev1sec2)”下）。

**脚本 11.4。** `images.php` 脚本使用 JavaScript 和 PHP 创建指向存储在服务器上的图像的链接。图像将通过 `show_image.php`（[脚本 11.5](#ch11.html#ch11ex05)）查看。

---

```html
1  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
      1.0 Transitional//EN" "http://www.w3.org/
2  1.0 Transitional//EN" "http://www.w3.org/
```
