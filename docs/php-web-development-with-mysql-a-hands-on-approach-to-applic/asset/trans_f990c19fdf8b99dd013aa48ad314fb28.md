
## 19. 处理文件和对现有代码的功能添加

在向服务器上传图像文件时，我们需要考虑两件事：

- 1. 我们希望允许哪些类型的图像文件，
- 2. 以及我们希望允许的文件有多大。

出于安全考虑，我们希望确保用户只上传图像文件（我们支持的图像类型），以免用户上传任何可执行文件。此外，我们还希望限制大小，以免用完存储空间并且 Web 服务器崩溃。在将上传的文件保存到我们的 images/ 文件夹之前，我们应该验证文件是否符合这些考虑，并且文件上传没有错误。$_FILES 超全局变量包含有关上传文件的全部信息。

通常使用表单来上传文件。有关文件的所有信息，包括文件本身，都包含在 $_FILES 超全局变量中。$_FILES 超全局变量是一个二维关联数组。第一维设置为文件输入元素的 name 属性，在本例中为 movie_image_file。PHP 将第二维设置为有关上传文件的不同属性。

| 属性名称 | 属性含义 | 属性值 |
| --- | --- | --- |
| `$_FILES['movie_image_file']['name']` | 文件名 | serenity_movie.jpg |
| `$_FILES['movie_image_file']['type']` | 图像类型 | image/jpg |
| `$_FILES['movie_image_file']['size']` | 图像大小（字节） | 214480 |
| `$_FILES['movie_image_file']['tmp_name']` | 服务器上文件的临时存储位置 | /tmp/phpV9CAHI |
| `$_FILES['movie_image_file']['error']` | 文件上传的错误代码；0 表示正常 | 0 |

> [1] PHP 文档对上传文件后可在 $_FILES['movie_image_file']['error'] 中找到的所有错误代码有完整说明，详见： https://php.net/features.file-upload.errors

## 验证上传的电影图像文件

如前所述，我们希望限制上传图像文件的大小和图像类型。我们希望将图像限制为 JPEG、PNG 或 GIF。我们还希望确保文件上传没有错误。由于我们经常会引用大小限制，因此最好为此最大文件大小创建一个常量并将其放在其他脚本可以包含的单独文件中。

创建一个名为 movielistingfileconstants.php 的新 PHP 脚本并添加以下代码：

```php
<?php
// Movie Listing File Constants
define('ML_MAX_FILE_SIZE', 524288);
```

> 在 php.ini 配置文件中，有几个设置会影响文件上传。默认情况下，这些设置应该已经启用：
> 
> - post_max_size = (some number)M
> - upload_max_filesize = (some number)M
> - file_uploads = TRUE
> 
> post_max_size 控制 post 请求的总大小，而 upload_max_filesize 控制每个上传文件的最大大小。文件大小的总和不能超过 post 请求的最大大小。M 后缀表示兆字节。
> 
> 在 apache2.conf 配置文件中确保以下设置已正确启用：
> - LimitRequestBody 设置了 post 请求可以有多大。
> 
> 因此，为了使 PHP 脚本的上传正常工作，这三个数字必须设置正确：LimitRequestBody = post_max_size > upload_max_filesize

接下来，创建一个名为 movieimagefileutil.php 的另一个新 PHP 脚本。此文件是我们放置处理电影图像文件的函数的地方。

将以下 require_once() 语句添加到 movieimagefileutil.php 以包含 movielistingfileconstants.php：

```php
<?php
require_once 'movielistingfileconstants.php';
```

## 19. 处理文件和对现有代码的功能添加

现在，让我们创建一个名为 validateMovieImageFile() 的函数：

```php
<?php
require_once 'movielistingfileconstants.php';

function validateMovieImageFile()
{
}
```

### PHP DocBlocks

虽然不是必需的，但标准做法是在函数开头添加 PHP DocBlock 注释。这是一种记录函数工作原理的好方法，这对使用和维护函数的开发人员很有帮助。这也是完善函数设计的好方法，并在实现时充当路线图。根据上面关于我们如何验证上传的电影图像文件的描述，这里是此函数的一个好的 Doc Block 应该是什么样子：

/**
 * Purpose:      Validates an uploaded movie image file
 *
 * Description:  Validates an uploaded movie image file is not greater than ML_MAX_FILE_SIZE (1/2 MB),
 *               and is either a jpg or png image type, and has no errors. If the image file
 *               validates to these constraints, an error message containing an empty string is
 *               returned. If there is an error, a string containing constraints the file failed
 *               to validate to are returned.
 *
 * @return string Empty if validation is successful, otherwise error string containing
 *                constraints the image file failed to validate to.
 */
function validateMovieImageFile()
{
}
```

> 此函数没有参数。但是，如果你不使用类型提示，参数会使用 @param 标签进行说明，每个参数一个。有关更多信息，请参阅 PHP 中的 Docblocks[2] 及其正确用法。

### 处理错误

我们知道如果有错误将返回包含错误消息的字符串，如果没有错误则返回空字符串。让我们在函数开始时创建一个名为 error_message 的变量并将其初始化为空字符串。在函数末尾返回它：

```php
function validateMovieImageFile()
{
    $error_message = "";
    // ...
    return $error_message;
}
```

在我们可以对上传的文件做任何事情之前，我们需要检查两个顶级条件。我们需要检查 $_FILES 超全局变量是否存在——如果用户选择不选择要上传的文件，则它不存在。此外，我们需要检查文件上传时没有错误。我们可以在单个 if 语句中组合这些检查，使用逻辑 AND (&&) 将它们连接起来。在 $error_message = "" 之后添加以下代码：

```php
$error_message = "";

// Check for $_FILES being set and no errors.
if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
{
    // ...
}
```

如果上面的 if 条件为 false，我们需要检查的另一个 elseif 条件。我们需要检查文件上传时是否出现错误。由于我们不知道条件失败是因为 $_FILES 超全局变量未设置还是因为错误不等于 UPLOAD_ERR_OK，因此在检查文件上传时是否出现错误之前，我们需要检查 $_FILES 是否已设置。我们还需要检查用户是否确实上传了文件。同样，我们可以将所有这些组合成一个 elseif 条件检查，使用 && 组合这些子句。PHP 提供了几个常量来描述文件错误。对于我们的目的，我们可以通过测试 $_FILES 数组中的 'error' 是否不等于 UPLOAD_ERR_OK 来捕获所有错误条件。如果我们进入此 elseif 条件，则是因为图像文件上传时出现错误。如果是这样，我们需要将 error_message 设置为适当的错误消息，说明上传电影图像文件时出现错误：

```php
elseif (isset($_FILES) && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_NO_FILE
    && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_OK)
{
    $error_message = "Error uploading movie image file.";
}
```

因此，我们的函数目前看起来像清单 19.2。

[2] PHP 中的 Docblocks： https://docs.phpdoc.org/guides/docblocks.html

## 添加文件上传功能

错误消息会根据上传的文件是否也超过最大文件大小而略有不同。将清单 19.4 中的代码添加到你刚刚添加的最大文件大小条件代码之后。

### 清单 19.4.

```php
1. // Check for $_FILES being set and no errors.
2. if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
3. {
4.    // ...
5.    $image_type = $_FILES['movie_image_file']['type'];
6.
7.    if ($image_type != 'image/jpg' && $image_type != 'image/jpeg' && $image_type != 'image/pjpeg'
8.        && $image_type != 'image/png' && $image_type != 'image/gif')
9.    {
10.       if (empty($error_message))
11.       {
12.          $error_message = "The movie file image must be of type jpg, png, or gif.";
13.       }
14.       else
15.       {
16.          $error_message .= ", and be an image of type jpg, png, or gif.";
17.       }
18.    }
19. }
```

我们的已完成 validateMovieImageFile() 函数看起来像清单 19.5。

### 清单 19.5.

```php
1. function validateMovieImageFile()
2. {
3.    $error_message = "";
4.
5.    // Check for $_FILES being set and no errors.
6.    if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
7.    {
8.       // Check for uploaded file < Max file size AND an acceptable image type
9.       if ($_FILES['movie_image_file']['size'] > ML_MAX_FILE_SIZE)
10.       {
11.          $error_message = "The movie file image must be less than " . ML_MAX_FILE_SIZE . " Bytes";
12.       }
13.
14.       $image_type = $_FILES['movie_image_file']['type'];
15.
16.       if ($image_type != 'image/jpg' && $image_type != 'image/jpeg' && $image_type != 'image/pjpeg'
17.           && $image_type != 'image/png' && $image_type != 'image/gif')
18.       {
19.          if (empty($error_message))
```
