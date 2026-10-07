
# 第四部分：不简单的应用程序

当你允许文件上传时，你就让自己面临了拒绝服务（DoS）攻击的风险。如果你不小心，有人可能会同时向你的系统发送数兆的文件，这可能导致你的机器崩溃停止。对于这个 `input` 标签，你可以做属。首先是在 `type="file">` 之前放置一个隐藏字段。该隐藏字段应该如下：

```
<INPUT TYPE="hidden" name="MAX_FILE_SIZE" value="1000">
```

其中 `value` 是允许的最大大小，单位为字节。这是一个合理的初步步骤，可以帮助阻止那些不知道你设置了大小限制的人。然而，这无法阻止任何具有敌意的人。他们只需要查看你页面的源代码并进行必要的更改即可。`php.ini` 文件包含 `upload_max_filesize` 。如果你有对 `php.ini` 的访问权限，可以将其设置为你认为合理的数字。默认情况下，`php.ini` 允许 2 MB 的上传。

当指定了文件并提交此表单时，PHP 会自动创建几个变量。你将获得：

- `$filename`: 存储在服务器临时目录中的的文件名
- `$image_name`: 文件在用户机器上的原始文件名
- `$image_size`: 文件的大小，单位为字节
- `$image_type`: mime 类型，在此例中为 image/gif、image/png、image/jpg

图像将存储在 `php.ini` 文件中指定的临时目录中；如果 `php.ini` 中没有指定临时目录，则将使用操作系统的默认目录。

`php.ini` 中的 `Paths and Directories` 类别控制着许多文件上传选项。

## 访问外部实用

对于此应用程序，我们需要每张图像的缩略图。应用程序可以要求用户同时包含完整尺寸图像和缩略图。但这并不是必要的，因为开源世界为我们所有开发者提供了一个能够强大且方便地处理图像的工具。它被称为 PBMplus。

![](img/245156cc770929860a3ede93c01f9981_293_0.png)

你可以在随书附的 CD-ROM 上找到 PBMplus 程序包。

PBMplus 包含了两种基本形式的几种工具。其中一种工具用于在图像与中间格式之间传输。因此，无论你拥有 gif、jpg 还是 png，都必须将其转换为中间格式 `pbm`。另一组工具用于修改 `pbm` 文件。这些工具可以执行各种操作：请查看 README 文件和随 PBMplus 附带的页面了解详情。一旦你制作了 `.pbm` 文件，就可以将其转换为所需的任何格式。要使用这些工具，你需要从 PHP 脚本中运行 shell 命令。就本应用程序而言，`system()` 函数将是最佳选择。更多内容我们将在代码部分介绍。

![](img/245156cc770929860a3ede93c01f9981_293_1.png)

> 使用运行 shell 命令的函数存在潜在危险。如果从用户提供的任何信息被传输到 shell 命令中，你应该非常小心地确保不会执行破坏性的命令。`escapeshellcmd()` 函数将帮助通过 http://www.php.net/manual/function.escapeshellcmd.php 检查 shell 命令。在本应用程序中，只有登录的用户才能接触访问 shell 的命令。

![](img/245156cc770929860a3ede93c01f9981_293_2.png)

如果你希望将 PBMplus 工具的结果直接输出到浏览器，请使用 `passthrough()` 函数。

### 代码详解

在面向对象编码中，良好的文档是你的最好的朋友，因为正如前面所说的，类如何工作并不重要。你只需要知道它们完成了你的任务。

#### 理论中的对象

例如，如果我们告诉你有一个名为 `Category` 的类，我们只需要告诉你以下内容：

`Class Category`:
继承 `Base`
Properties:
- `products`

Methods:
- `LoadCategory`: 根据唯一的 `category_id` 将所有分类表加载到对象属性中。
- `SaveCategory`: 将新的或更新的分类写入数据库。
- `FetchCategory`: 根据唯一的 `category_id` 将该行的所有列分配给属性。
- `DeleteCategory`: 从数据库中删除分类。
- `PrintCategory`: 将分类写入浏览器。

了解这些并对此一无所知，我们就可以编写一个显示分类的新脚本。下面的脚本假设 `category_id` 是通过查询字符串或 POST 传递的。

```php
<?php
$c = new Category;
$c -> LoadCategory($category_id);
$c -> PrintCategory();
```

但如果只此此，学习体验将只有预期的一部分。当然，我们将深入分析所有代码。在此之前，我们应该观察对象是如何构造的。

#### 实践中的对象

到为止，在书中你看到了各种形状的变量。有字符串、整数、数组、关联数组以及各种有趣的内容。然而，我们的变量将变得复杂一些。看看这两行代码，我们已经解释过了：

```
$c = new Category;
$c -> LoadCategory($category_id);
```

如果你阅读了之前的章节，你就知道这创建了一个带有子对象的对象。通过视觉表示会更容易理解。图 10-11 显示了一个示例 Category 对象

```
[product] => Plain
[description] => Old standby
[price] => 10.00
```

```
[1] => product Object (
[product_id] => 2
[category_id] => 1
[product] => Oops!
[description] => A sentiment we can all share
[price] => 10.00
)
```

图 10-11：示例分类对象

在图 10-11 中，你可以看到对象不仅包含属性。它的一个属性（`products`）包含其他对象的数组。为了明确这一点，下面的代码将打印出。“没问题”。

```php
<?php
$c = new Category;
$c -> LoadCategory($category_id);
if(is_array($c->products))
{
```
```php
if(is_object($c->products[0]))
{
  echo "You Bet";
}
```

类中的方法将被构造好，以获取这些子对象。执行管理任务的需要考虑这种结构。
在查看其他类时，也请记住这一点。`Products` 对象可能包含一个包含样式（styles）子对象的数组，而 `Styles` 对象将包含一个包含子样式（sub-styles）子对象的数组。

### 类

我们在设计应用程序类时，使得大多数类在外观和行为上都相似。当你查看这些类时，你会发现除了 Base 类外，所有类都具有名称相似的方法。我们希望你理解其中一个类后，其他类的工作原理就会显而易懂。因此，我们将在本章中详细介绍两个类。请注意，每个类中的方法在 CD 中都有详尽的注释。所以，如果你对某段代码有特定的疑问，可能会在注释中找到解释。

在接下来的页面中，我们将分析 `Base` 和 `Product` 这两个类中的代码。对于其他类，我们只描述如何使用它们的方法和属性。但一旦你理解了 `Product` 类，其他类（`Product`、`Style` 和 `Sub-style`）应该就足够理解。

这些类非常多；将它们全部倒到一个文件中会让生活变得不必要的。更好的做法是创建一个名为 `classes.php` 的文件，其中包含所有的类。以下是 `classes.php` 的内容：

```php
include "base_class.php";
include "category_class.php";
include "product_class.php";
include "style_class.php";
include "substyle_class.php";
```

> 请在阅读本节之前，确保你已经掌握了第 7 章的概念。

将类拆分为包含文件还允许我们在需要时选择性地复用特定的类。这在第 14 章中变得很重要，当时我们在创建购物车时复用了这些类中的一些。

## 第 10 章：目录

### BASE

始终有一个用于构建派生类的基类（尽管名字并不一定叫 Base）。在本应用程序中，`Base` 将包含一组所有其他类都会使用的工具方法。该类的声明语句如下：

```php
class Base
{
```

现在来看属性。只有三个默认属性。在处理图像和缩略图时，以下三个属性会起作用。

- `$image_src`;
- `$thumb_src`;
- `$thumb_width`

其他属性将在方法的执行过程中动态创建。

### 方法 `SQL_FORMAT()`

该方法帮助构建更新和插入插入查询语句。

```php
function sql_format ($field)
{
    if (empty($this->$field))
    {
        return "null";
    }elseif(is_numeric($this->$field))
    {
        return $this->$field;
    }else
    {
        return "'.'.$this->$field.''";
    }
}
```

为了构建查询，变量可能是空、数值数量或文本字符串。每种数据类型在查询中都需要略有不同的格式。字符串必须被单引号括起来。数值可以没有引号，而对于空，此方法将返回字符串 `"null"`——不带任何单引号。

### 方法 `SET_IMAGE_SRC()`

该方法既将上传的图像保存到文件系统，又创建缩略图。

### 第四部分：不那么简单的应用程序

逐节拆解已经足够复杂了。首先记住 `$file_src` 是方法调用的唯一参数。`$file_src` 是一个包含图像路径的字符串。大多数情况下，`$file_src` 是类似 `"images/image_product_8_style"` 这样的字符串。

```php
function set_src($file_src="") {
    if (empty($this->imagefile) && $this->imagefile != "none") {
        if ($file_src === "") {
            $file_src = "images/*.uniqid("image_")";
        }
        umask(2);
    }
    $sizearr = GetClientSize($this->imagefile);
```

在这里，image 是用户上传的文件。如果文件存在但 `$file_src` 参数没有指定文件名，则创建一个名为 `$file_src` 的变量。使用 `uniqid()` 函数，我们创建了一个以 `"image_"` 开头并包含随机字符的文件名。我们想要确保文件是唯一的，这样就不会覆盖现有文件。在设置 `umask` 之后（请参阅 Unix man 手页了解 umask 的描述），我们使用了 `getimagesize` 函数。该函数返回一个包含四个元素的数组：第一个是图像高度，第二个是宽度，第三个是图像类型（1 = GIF, 2 = JPG, 3 = PNG, 4 = SWF），第四个是准备用于 `<img>` 标签的字符串格式的高宽。这些信息非常有用，因为即使提供的文件名扩展名错误或没有名称，脚本也能分配正确的扩展名。

```php
if ($sizearr[2] == 1) { $file_ext = ".gif"; }
elif ($sizearr[2] == 2) { $file_ext = ".jpg"; }
elif ($sizearr[2] == 3) { $file_ext = ".png"; }
else {
    $file_ext = strtolower(
        substr($this->imagefile_name,
            strrpos($this->imagefile_name,".*")
    );
}
```

使用数组第三个元素中的信息，我们确定合适的扩展名。如果文件类型不匹配 `getimagesize()` 返回的任何可能值，我们就解析包含上传文件的字符串。我们取最后一个点开始的字符，将其转换为小写，并赋值给 `$file_ext`。

```php
$thumb_src = $file_src."$thumb".$file_ext;
$file_src = $file_ext;
copy($this->imagefile, $file_src);
```

现在我们有了唯一文件名和正确的扩展名，就可以为主文件和我们要制作的缩略图组合文件名。源文件从其临时位置复制到文件系统的完整路径，如 `$file_src` 所示。

```php
if ($file_ext == ".jpg") {
    $cmd = "../catalog/makeimagthumb $file_src $thumb_src";
}
```

如果图像是 jpg，我们将调用一个脚本。该脚本的输出传递给 pnmmargin，它会添加黑色边框。最后，cjpeg 将图像转换为新格式。这是该 shell 脚本的内容：

```bash
#!/bin/sh
PATH=/path/to/pmbmplus/
djpeg=$PATH/djpeg;
pnmscale=$PATH/pnmscale;
pnmmargin=$PATH/pnmmargin;
cjpeg=$PATH/cjpeg;
$cmd="$djpeg $file_src | $pnmscale -xsize 50 50 | $pnmmargin | $cjpeg > $thumb_src";
$out = system($cmd, $err);
```

```php
if ($err) { 
    print "<h4>cmd=$cmd\nerr=$err\nout=$out</h4>\n"; 
} else {
    copy($file_src, $thumb_src);
    $this->image_src = $file_src;
    $this->thumb_src = $thumb_src;
} else {
    $this->set_thumb_src();
}
```

# 第 10 章：目录

);

}

**METHOD BASE** 这是该类的构造方法。如你所见，它几乎没做什么，只是调用了一个名为 Construct 的方法。

```
function Base ($parent="",$atts="")
{
    $this->Construct(get_object_vars($parent));
    $this->Construct($atts);
}
```

注意对 `get_object_vars()` 的使用。这是一个非常有用的函数，它可以将对象的所有属性转换为关联数组。因此，如果向此方法传递一个对象（通过第一个实例），则该对象可以作为数组被传递给 Construct。

**METHOD CONFIRM_DELETE_FORM()** 此方法会打印一个表单，强制目录管理员确认他们是否想要继续删除操作。当对一个包含相关子元素的项目指示进行删除操作时，该方法就会生效。例如，如果管理员指示要删除某个类别，但该类别仍包含产品，则会打印此表单。

```
confirm_delete_form($message="",$label="")
{
    $warning = "<b>Please confirm your delete request?</b>";
    if (empty($message)) {
        $warning = " - " . $message;
    }
    $output = <<EOQ
<p>
<form method="post">
$warning
<input type="hidden" name="confirm" value="Confirm Delete">
<input type="submit" name="submit" value="$label">
</form>
</p>
EOQ;
    return $output;
}
```

# 274 第四部分：并不简单的应用程序

METHOD CONSTRUCT() 此方法期望一个关联数组。在应用程序运行过程中，该关联数组通常是 `mysqli_fetch_array()` 的结果。数组中的每个键将成为当前对象的属性。注意，我们必须运行 `set_thumb_src()` 属性，因为 `thumb_src` 没有存储在数据库中。

```php
function Construct ($atts="")
{
    if (is_array($atts))
    {
        while (list($name,$value) = each($atts))
        {
            if (!empty($value) && !is_array($value))
            {
                $this->$name = $value;
            }
        }
    }
    if (!empty($this->image_src))
    {
        $this->set_thumb_src();
    }
}
```
