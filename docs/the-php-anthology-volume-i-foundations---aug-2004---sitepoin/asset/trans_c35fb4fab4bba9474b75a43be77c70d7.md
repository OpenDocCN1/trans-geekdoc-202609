

- `$_FILES['fieldname']['type']`: 文件的 MIME 类型[8]
- `$_FILES['fieldname']['tmp_name']`: 文件上传时 PHP 创建的临时名称和位置
- `$_FILES['fieldname']['error']`: 如果一切正常则为 0（错误代码请参见 PHP 手册[9]）
- `$_FILES['fieldname']['size']`: 文件的大小（字节）

下面是 PHP 的 print_r 函数生成的文件上传信息数组示例：

```
Array
(
    [name] => php_logo.gif
    [type] => image/gif
    [tmp_name] => /tmp/php1B1B.tmp
    [error] => 0
    [size] => 3872
)
```

掌握这些知识后，让我们来看一个简单的脚本，它接受 GIF 文件上传并将其复制到当前目录的 files 子目录中：

```
<?php
// Include Magic Quotes filter
require_once 'MagicQuotes/strip_quotes.php';

// If the form has been submitted...
if (isset($_POST['submit'])) {

    // If the file is a GIF image...
    if ($_FILES['image']['type'] == 'image/gif') {

        // Copy the file from temporary storage to final destination
        copy($_FILES['image']['tmp_name'], "./files/" . $_FILES['image']['name'])
or die("Could not copy");

// Display some information about the file
echo "File Upload Complete<br />\n";
echo "Name: " . $_FILES['image']['name'] . "<br />\n";
echo "Size: " . $_FILES['image']['size'] . "<br />\n";
echo "Type: " . $_FILES['image']['type'] . "<br />\n";
echo "<img src=\"\\files/" . $_FILES['image']['name'] . "\\" />";
}

// ... otherwise display the form
} else {
?>
<form method="POST"
    action="?<?php echo $_SERVER['PHP_SELF']; ?>"
    enctype="multipart/form-data">
Upload a GIF image: <input type="file" name="image" />
<input type="submit" name="submit" value="Submit" />
</form>
<?php
}
?>
```

搞定，即时文件上传！请参见图 9.5 查看结果。

### 图 9.5. PHP 徽标上传成功

![](img/5b6cdf7cf4cf53e30b19e047895dc464_303_0.png)

### 确保是上传的文件

也许你有一个更复杂的脚本，在其中你将临时文件名传递给了另一个 PHP 变量，进行了各种操作，然后忘了代码里留了个漏洞——这个漏洞允许用户用另一个文件名修改 PHP 变量的内容！在对上传的文件做任何操作（例如将其复制到其他人可以看到的公共目录）之前，值得使用 PHP 函数 `is_uploaded_file` 双重检查上传的文件确实是正确的文件。过去，有人诱使 PHP 脚本将包含密码的文件（而不是实际上传的图像）复制到公共目录。与其后悔，不如谨慎。

### 使用 QuickForm 进行文件上传

让我们再次启用我们的老朋友 QuickForm，并学习如何将文件存储在 MySQL 中。

表单的构建与“如何在 PHP 中处理 HTML 表单？”中的示例非常相似：

```
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

// Include the QuickForm class
require_once 'HTML/QuickForm.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// A function to apply mysql_real_escape_string
function escapeValue($value)
{
    return mysql_real_escape_string($value);
}

// Instantiate QuickForm
$form = new HTML_QuickForm('imageUpload', 'POST');

// The file upload field
$form->addElement('file', 'image', 'Select Image:');
$form->addRule('image', 'The maximum file size is 56KB',
    'maxfilesize', 57344);
$form->addRule('image', 'The file must be an image', 'mimetype',
    array('image/gif', 'image/jpeg', 'image/pjpeg',
    'image/png'));
$form->addRule('image', 'No file selected.', 'uploadedfile', NULL,
    'client');

// The submit button
$form->addElement('submit', 'submit', 'Upload');
```

请注意，我们已应用 mimetype 规则，这允许我们传递一个用户可以上传的允许 MIME 类型数组³。

³请注意，JPEG 文件可能会根据浏览器被报告为 image/jpeg 或 image/pjpeg；因此，两者都包含在可接受类型列表中。

虽然调用 applyFilter 方法会转义提交到表单的所有文本值，但它不会转义与文件上传关联的值。因此，我们必须在从 $form 对象检索这些值时（包括二进制文件数据）对每个值应用 escapeValue 函数：

```
if ($form->validate())
{
    // Apply the escape filter to all fields
    $form->applyFilter('__ALL__', 'escapeValue');

    // Instantiate the MySQL class
    $db = &new MySQL($host, $dbUser, $dbPass, $dbName);

    // Fetch the details of the file
    $name = escapeValue($form->_submitFiles['image']['name']);
    $size = escapeValue($form->_submitFiles['image']['size']);
    $type = escapeValue($form->_submitFiles['image']['type']);

    // Fetch file data
    $contents = file_get_contents(
        $form->_submitFiles['image']['tmp_name']);

    // Escape binary data
    $contents = escapeValue($contents);

    $sql = "INSERT INTO image SET
        name='$name',
        size='$size',
        type='$type',
        contents='$contents'";

    // Perform the query
    $result = $db->query($sql);

    // If all went well, say thanks
    if (!$result->isError()) {
        echo 'File Uploaded Successfully';
    } else {
        $form->display();
    }
} ?>
```

请注意，在获取文件详细信息时，我们直接访问了 QuickForm 的一个属性（_submitFiles），在使用对象时这在技术上属于不良做法（如果在将来的 QuickForm 版本中变量名发生更改，这将导致我的脚本出错）。不幸的是，QuickForm 目前没有提供访问此信息的机制，因此我们不得不采用这个变通方法。

既然我们已经上传了一些文件并将它们存储在数据库中，那么显示它们呢？

```
File: 10.php
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

$Host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

$db =& new MySQL($Host, $dbUser, $dbPass, $dbName);

// Define SQL statement to fetch image information
// but NOT CONTENTS!!!
$sql = "SELECT image_id, name, size, type FROM image
    ORDER BY name";

// Fetch the result object
$result = $db->query($sql);

// A loop for each row of the result set
while ($row = $result->fetch()) {
    echo '<img src="11.php?id=' . $row['image_id'] . '" /> <br />';
    echo $row['name'] . ': ' . $row['size'] . ' : ' .
        $row['type'] . '<br />';
}
?>
```

上述代码列出了数据库中的图像。然后它生成一些 HTML，使用 img 标签指定另一个 PHP 脚本，正是该脚本实际显示图像。请注意，我们谨慎地没有选择图像的内容——只选择每个图像所需的信息。否则，这将非常迅速地耗尽 PHP 的内存。

它生成的 HTML 如下：

```
<img src="11.php?id=2" /><br />
mysql.png : 1107 : image/png<br />
<img src="11.php?id=1" /><br />
php_logo.gif : 3872 : image/gif<br />
<img src="11.php?id=3" /><br />
sitepoint_arrow.gif : 508 : image/gif<br />
```

现在，查看 11.php，它显示了用于生成图像的代码：

```
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// Instantiate the MySQL class
$db =& new MySQL($host, $dbUser, $dbPass, $dbName);

// If there's not image, die
if (!isset($_GET['id'])) {
	die('No image selected');
}

// Escape the string, for good practice
$_GET['id'] = mysql_real_escape_string($_GET['id']);

// An SQL statement to get the contents and MIME type of the image
$sql = "SELECT * FROM image WHERE image_id='" . $_GET['id'] . "'";

// Fetch the data
$result = $db->query($sql);
$row = $result->fetch();

// Use a header to tell the browser what MIME type the image is
header('content-disposition: inline; filename=' . $row['name']);
header('content-type: ' . $row['type']);
header('content-length: ' . $row['size']);

// Display the contents
echo $row['contents'];
?>
```

