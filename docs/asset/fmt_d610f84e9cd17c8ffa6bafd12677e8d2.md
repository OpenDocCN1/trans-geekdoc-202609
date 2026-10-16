
## 19. 处理文件与现有代码的功能添加

### 清单 19.5

```php
function validateMovieImageFile()
{
    $error_message = "";

    // Check for $_FILES being set and no errors.
    if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
    {
        // Check for uploaded file < Max file size AND an acceptable image type
        if ($_FILES['movie_image_file']['size'] > ML_MAX_FILE_SIZE)
        {
            $error_message = "The movie file image must be less than "
                        . ML_MAX_FILE_SIZE . " Bytes";
        }

        $image_type = $_FILES['movie_image_file']['type'];

        if ($image_type != 'image/jpg' && $image_type != 'image/jpeg'
            && $image_type != 'image/pjpeg' && $image_type != 'image/png'
            && $image_type != 'image/gif')
        {
            if (empty($error_message))
            {
                $error_message = "The movie file image must be of type jpg, png, or gif.";
            }
            else
            {
                $error_message .= ", and be an image of type jpg, png, or gif.";
            }
        }
    }
    elseif (isset($_FILES) && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_NO_FILE
        && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_OK)
    {
        $error_message = "Error uploading movie image file.";
    }

    return $error_message;
}
```

### 考虑阻止上传 `generic_movie.jpg`

在上述实现中，没有任何机制阻止用户上传名为 `generic_movie.jpg` 的图片。较好的做法是通过检查上传文件的名称来防止这种情况发生。否则，任何人都可能覆盖我们用于电影的默认图片。一般来说，你应该小心处理文件上传，并考虑他人可能如何滥用它们。我将此留作你的练习。

### 考虑使用 `in_array()` 检查图片类型

在清单 19.5 的代码中，我们有以下用于验证合法图片类型的 `if` 子句：

```php
if ($image_type != 'image/jpg' && $image_type != 'image/jpeg' && $image_type != 'image/pjpeg'
    && $image_type != 'image/png' && $image_type != 'image/gif')
```

这种代码会变得杂乱且难以维护。挑选合法图片类型的更好解决方案是使用 PHP 内置函数 `in_array()`[3]。要使用它，请创建允许的图片类型数组，然后检查设置的图片类型是否出现在数组中：

```php
$allowed_image_types = [
    'image/jpg', 'image/jpeg', 'image/pjpeg', 'image/png', 'image/gif'
];

if (in_array($image_type, $allowed_image_types))
{
    // ...
}
```

[3] `in_array()` 函数：https://php.net/in-array

### 移动图片文件

假设上传的电影图片文件通过验证，我们需要将该文件从 Web 服务器上的临时位置移动到我们的 `images/` 文件夹。完成后，我们应该返回文件的路径位置，以便与数据库中的其他电影详情一起存储。如果用户未上传文件——或上传文件时出错——我们为路径位置返回空字符串。这个空字符串稍后用作显示默认文件图标的指示。

由于我们会经常引用 `images/` 文件夹，最好为此上传路径创建一个常量，并将其放在一个可被其他脚本包含的单独文件中。因此，请将 `define('ML_UPLOAD_PATH', 'images/');` 添加到 `movielistingfileconstants.php`。我们还需要一个默认图片文件的常量，以防用户未上传图片。完整的常量文件现在应如下所示：

```php
<?php
// Movie Listing File Constants

define('ML_UPLOAD_PATH', 'images/');

define('ML_MAX_FILE_SIZE', 524288);

define('ML_DEFAULT_MOVIE_FILE_NAME', 'generic_movie.jpg');
```

务必为函数使用描述性名称，一个好的名称是：`addMovieImageFileReturnPathLocation()`。在 `validateMovieImageFile()` 函数下面，让我们创建新函数，并附带一个描述性良好的 DocBlock，如清单 19.6 所示。

### 清单 19.6

```php
/**
 * Purpose:        Moves an uploaded movie image file to the ML_UPLOAD_PATH (images/)
 *                 folder and return the path location.
 *
 * Description:    Moves an uploaded movie image file from the temporary server location
 *                 to the ML_UPLOAD_PATH (images/) folder IF a movie image file was uploaded
 *                 and returns the path location of the uploaded file by appending the file
 *                 name to the ML_UPLOAD_PATH (e.g. images/movie_image.png). IF a movie image
 *                 file was NOT uploaded, an empty string will be returned for the path.
 *
 * @return string  Path to movie image file IF a file was uploaded AND moved to the
 *                 ML_UPLOAD_PATH (images/) folder, otherwise an empty string.
 */

function addMovieImageFileReturnPathLocation()
{
}
```

由于我们知道要返回包含路径位置的字符串，或者在没有文件上传或存在错误时返回空字符串，请创建一个名为 `$movie_file_path` 的变量，将其设置为空字符串并返回：

```php
function addMovieImageFileReturnPathLocation()
{
    $movie_file_path = "";
    // ...
    return $movie_file_path;
}
```

在移动上传文件之前，我们需要检查用户是否确实上传了文件且没有错误。请在 `$movie_file_path = "";` 之后添加以下代码：

```php
$movie_file_path = "";

// Check for $_FILES being set and no errors.
if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
{
    // ...
}
```

如果我们进入此条件，就可以开始构建路径。请在 `if` 条件正下方添加以下代码：

```php
if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
{
    $movie_file_path = ML_UPLOAD_PATH . $_FILES['movie_image_file']['name'];
}
```

接下来，我们需要将文件从 Web 服务器上的临时位置移动到我们的 `images/` 文件夹。我们使用 `move_uploaded_file()`[4] 函数来完成。该函数接受两个参数：

1. 第一个参数是我们想要移动的文件的源路径位置。
2. 第二个参数是我们想要将文件移动到的目标路径位置。

[4] `move_uploaded_file()` 函数：https://php.net/move_uploaded_file

### 添加上传文件功能

注意，文件路径位置也必须包含文件名。`move_uploaded_file()` 成功时返回 `true`，否则返回 `false`。我们将调用放在 `if` 条件中，并在失败时将 `$movie_file_path` 重置为空字符串。请在我们之前设置 `$movie_file_path` 的代码行下方添加以下代码：

```php
$movie_file_path = ML_UPLOAD_PATH . $_FILES['movie_image_file']['name'];

if (!move_uploaded_file($_FILES['movie_image_file']['tmp_name'], $movie_file_path))
{
    $movie_file_path = "";
}
```

上述代码将上传的电影图片文件从 Web 服务器的临时位置移动到 `images/` 文件夹。完整的 `addMovieImageFileReturnPathLocation()` 函数如清单 19.7 所示。

### 清单 19.7

```php
function addMovieImageFileReturnPathLocation()
{
    $movie_file_path = "";

    // Check for $_FILES being set and no errors.
    if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK) {
        $movie_file_path =
            ML_UPLOAD_PATH . $_FILES['movie_image_file']['name'];

        if (!move_uploaded_file($_FILES['movie_image_file']['tmp_name'], $movie_file_path)) {
            $movie_file_path = "";
        }
    }

    return $movie_file_path;
}
```

### 完整的电影图片文件脚本

我们完整的 `movieimagefileutil.php` 脚本，包括 `validateMovieImageFile()` 和 `addMovieImageFileReturnPathLocation()` 函数，如清单 19.8 所示。

### 清单 19.8

```php
<?php
require_once 'movielistingfileconstants.php';

/**
 * Purpose:    Validates an uploaded movie image file
 *
 * Description: Validates an uploaded movie image file is not greater than
 *              ML_MAX_FILE_SIZE (1/2 MB), and is either a jpg or png image type, and
 *              has no errors. If the image file validates to these constraints,
 *              an error message containing an empty string is returned. If
 *              there is an error, a string containing constraints the file failed
 *              to validate to are returned.
 *
 * @return string  Empty if validation is successful, otherwise error string containing
 *                 constraints the image file failed to validate to.
 */

function validateMovieImageFile()
{
    $error_message = "";

    // Check for $_FILES being set and no errors.
    if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
    {
        // Check for uploaded file < Max file size AND an acceptable image type
        if ($_FILES['movie_image_file']['size'] > ML_MAX_FILE_SIZE)
        {
            $error_message = "The movie file image must be less than "
                        . ML_MAX_FILE_SIZE . " Bytes";
        }

        $image_type = $_FILES['movie_image_file']['type'];

        if ($image_type != 'image/jpg' && $image_type != 'image/jpeg'
            && $image_type != 'image/pjpeg' && $image_type != 'image/png'
            && $image_type != 'image/gif')
        {
            if (empty($error_message))
            {
                $error_message = "The movie file image must be of type jpg, png, or gif.";
            }
            else
            {
                $error_message .= ", and be an image of type jpg, png, or gif.";
            }
        }
    }
    elseif (isset($_FILES) && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_NO_FILE
        && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_OK)
    {
        $error_message = "Error uploading movie image file.";
    }

    return $error_message;
}

/**
 * Purpose:        Moves an uploaded movie image file to the ML_UPLOAD_PATH (images/)
 *                 folder and return the path location.
 *
 * Description:    Moves an uploaded movie image file from the temporary server location
 *                 to the ML_UPLOAD_PATH (images/) folder IF a movie image file was uploaded
 *                 and returns the path location of the uploaded file by appending the file
 *                 name to the ML_UPLOAD_PATH (e.g. images/movie_image.png). IF a movie image
 *                 file was NOT uploaded, an empty string will be returned for the path.
 *
 * @return string  Path to movie image file IF a file was uploaded AND moved to the
 *                 ML_UPLOAD_PATH (images/) folder, otherwise an empty string.
 */

function addMovieImageFileReturnPathLocation()
{
    $movie_file_path = "";

    // Check for $_FILES being set and no errors.
    if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK) {
        $movie_file_path =
            ML_UPLOAD_PATH . $_FILES['movie_image_file']['name'];

        if (!move_uploaded_file($_FILES['movie_image_file']['tmp_name'], $movie_file_path)) {
            $movie_file_path = "";
        }
    }

    return $movie_file_path;
}
```
