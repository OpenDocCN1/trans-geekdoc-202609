
另一种内容管理方法是让用户使用公告板代码（BBCode）来格式化文本。BBCode 是一种标记语言，被许多公告板和留言板系统使用。它与 HTML 相似，但具有简化的语法，使用方括号（[ ]）而不是尖括号（< >）。

由于 BBCode 不允许用户输入 HTML 标签，因此比 HTML 更安全。因此，它适用于面向任何人的 Web 应用程序，例如公告板。然而，熟悉 HTML 的用户比熟悉 BBCode 的用户更多。因此，允许使用 HTML 适用于用户为可信赖的管理员用户的 Web 应用程序，他们不会输入包含恶意代码的 HTML 标签。要获取有关 BBCode 的更多信息，您可以搜索互联网。

## 如何向文本添加 HTML 标签

图 20-2 显示了存储在 util 目录中的 tags.php 文件的 PHP 代码。该文件定义了一个名为 add_tags 的函数，该函数向大量文本添加 <p>、<ul> 和 <li> 标签，如前一图所示所述。

add_tags 函数首先搜索文本并将 Windows 和 Mac 系统的换行字符转换为 Unix 系统的换行字符。这是必要的，因为 Windows 系统使用回车和换行字符（“\r\n”）来标记新行，而 Mac 系统使用单个回车字符（“\r”）来标记新行。相比之下，Unix 系统仅使用单个换行字符（“\n”）来标记新行。执行此代码后，您可以确信无论使用什么操作系统，文本中每个新行都包含单个换行字符（“\n”）。

设置换行字符后，此代码使用 explode 函数将文本拆分为段落数组，并将该数组存储在名为 $paragraphs 的变量中。在这里，每个段落由两个换行字符（“\n\n”）分隔。然后，此代码清空 $text 变量并使用循环处理每个段落。

在循环内，第一条语句会从段落左侧修剪任何空白。然后，代码获取段落中的第一个字符。如果该字符是星号（*），则此代码向段落添加适当的 <ul> 和 <li> 标签。否则，此代码向段落添加适当的 <p> 标签。无论哪种情况，段落都会附加到 $text 变量的末尾。

循环结束后，此函数返回 $text 变量。此时，$text 变量包含标记段落和无序列表的 HTML 标签。它还包含存储在此数据库中的任何 HTML 标签。

在审阅此代码时，请注意它可以很容易地扩展以考虑其他 HTML 标签。例如，如果您想插入链接，可以自动检查以“http://”和“www.”开头的任何文本并添加适当的 <a> 标签。或者，如果您想提供有序列表，可以检查段落中的第一行是否以数字开头，并添加适当的 <ol> 和 <li> 标签。

**util/tags.php 文件**

```php
<?php
function add_tags($text) {

    // Convert return characters to the Unix new lines
    $text = str_replace("\r\n", "\n", $text);    // convert Windows
    $text = str_replace("\r", "\n", $text);      // convert Mac

    // Get an array of paragraphs
    $paragraphs = explode("\n\n", $text);

    // Add tags to each paragraph
    $text = '';
    foreach ($paragraphs as $p) {
        $p = ltrim($p);

        $first_char = substr($p, 0, 1);
        if ($first_char == '*') {
            // Add <ul> and <li> tags
            $p = '<ul>' . $p . '</li></ul>';
            $p = str_replace("*", '<li>', $p);
            $p = str_replace("\n", '</li>', $p);
        } else {
            // Add <p> tags
            $p = '<p>' . $p . '</p>';
        }
        $text .= $p;
    }

    return $text;
}
?>
```

**使用 add_tags 函数的代码**

```php
<?php
$description = add_tags($description);
?>
```

**说明**

- 要向数据库中某一列的文本添加 HTML 标签，可以使用第 9 章中介绍的 PHP 字符串函数解析代码，并在必要时添加标签。

## 吉他商店网站的包含文件

本章的其余部分介绍了第 5 章中介绍的吉他商店应用程序的增强版本。首先，它介绍了网站的 *包含文件*。这些文件在整个网站中使用，并且这些文件同时被吉他商店网站的 Product Catalog 和 Product Manager 应用程序使用。要在需要的地方包含这些文件，可以使用 include 和 require 函数。

为了更好地了解包含文件的工作原理，图 20-3 的第 1 部分显示了吉他商店网站的 Home 页面和目录结构。然后，接下来的三个部分显示了一些包含文件。

### 主页

图中此主页在用户访问网站时显示。此页面显示一些特色产品，并允许用户通过单击侧边栏中的类别链接来浏览产品。请注意，此侧边栏的代码存储在包含文件中。

同样请注意，侧边栏中的 Home 和 Admin 链接不会包含在生产应用程序中。然而，在应用程序的开发和测试阶段，像这样的链接使开发人员和测试人员在 Product Catalog 和 Product Manager 应用程序之间跳转变得更容易。

同时请记住，这些应用程序的重点是开发和测试应用程序的 PHP 代码。稍后，当所有代码都正常工作时，您或网页设计师可以增强 HTML 和 CSS，以便图形和导航适合最终用户。例如，页眉可能包括徽标、标语和包含指向主页链接的导航栏。

### 目录结构

此图还展示了此应用程序的目录结构。在这里，model 和 view 目录包含在网站多个部分中使用的模型和视图的文件。名为 admin、cart 和 catalog 的目录包含网站内应用程序的 PHP 文件。images 目录包含网站使用的所有图像。errors 目录包含用于处理错误的 PHP 文件。util 目录包含可在整个网站中使用的通用文件。

在应用程序的根目录中，当用户在其浏览器中访问网站时，会运行 index.php 文件。此文件包含主页使用的所有 util 和 model 文件。然后，它在包含 home_view.php 文件以显示主页之前进行一些处理。

**吉他商店网站的主页**

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_680_0.png)

**从 htdocs/book_apps 开始的网站目录结构**

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_680_1.png)

**应用程序根目录中的文件**

```text
index.php
home_view.php
main.css
```

**说明**

- *包含文件* 包含在整个网站中使用的代码。然后，可以在需要时包含这些文件。
- 对于吉他商店网站，包含文件存储在 util、model、view 和 errors 子目录中。这些文件通常被驱动网站应用程序的文件使用，例如 admin、cart 和 catalog 目录中的文件。

**util/main.php 文件**

```php
<?php
// Get the document root
$doc_root = filter_input(INPUT_SERVER, 'DOCUMENT_ROOT');

// Get the application path
$uri = filter_input(INPUT_SERVER, 'REQUEST_URI');
$dirs = explode('/', $uri);
$app_path = '/' . $dirs[1] . '/' . $dirs[2] . '/';

// Set the include path
set_include_path($doc_root . $app_path);
?>
```

**view/header.php 文件**

```html
<!DOCTYPE html>
<html>
<!-- the head section -->
<head>
    <title>My Guitar Shop</title>
    <link rel="stylesheet" type="text/css"
          href="<?php echo $app_path ?>main.css" />
</head>

<!-- the body section -->
<body>
<header>
    <h1>My Guitar Shop</h1>
</header>
<main>
```

**说明**

- 如图 20-2 中的 tags.php 文件之类的通用文件通常称为 *实用文件*，因为它们可被许多应用程序使用。
- 如本图所示的 header.php 和 sidebar.php 文件之类的视图文件会被多个其他视图文件包含。

图 20-3    吉他商店网站的包含文件（第 2 部分，共 4 部分）
