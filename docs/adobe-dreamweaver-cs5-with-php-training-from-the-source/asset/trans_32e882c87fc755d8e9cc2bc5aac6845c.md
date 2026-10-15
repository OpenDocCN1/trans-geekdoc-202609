
**7.** 选择一个小于 50 KB 的文件，然后点击“Upload File”。如果勾选了 upload_test 文件夹，应该已经完成传输，但表单没有任何反馈。你需要编写一个在传输成功时能够显示的消息。

**8.** 修改检查传输是否成功的条件语句，如下：

```php
if (!$success) {  
    $messages = $uploader->getMessages();  
} else {  
    $filename = $uploader->getFileName(NULL, FALSE);  
    $messages[] = "$filename uploaded successfully";  
}
```

`getFileName()` 方法可用于单文件和多文件上传。它接受两个可选参数：

- 第一个参数是对文件的引用。若省略或设为 `NULL`，方法会返回单个文件名（字符串）或多个文件名（数组）。
- 第二个参数决定是否包含完整路径。默认是 `TRUE`，设为 `FALSE` 则只返回文件名。

两个参数都是可选的，但不能只设置第二个参数而不设置第一个。`else` 块的第一行代码获取不含路径的文件名并赋值给 `$filename`，因为本次只上传一个文件，所以 `$filename` 为字符串。

`else` 块的第二行代码把 `$filename` 嵌入双引号字符串并追加到 `$messages[]`，空的方括号使其成为数组元素。需要将其设为数组，以便步骤 5 中创建的循环能够正确处理。

**9.** 保存 `process_upload.php`，再次测试表单，选择小于 50 KB 的文件。此次表单应显示文件名以及上传成功的信息。

![Image](graphics/fig09_11.jpg)

**10** 为上传脚本添加一些验证。第一项要检查的就是文件是否超过最大尺寸，以防有人试图绕过表单中的 `MAX_FILE_SIZE` 设置。

因为表单只处理单个文件上传，使用 `FileSize` 或 `Size` 验证类并不重要。但养成使用正确的验证类是个好习惯：`FileSize` 控制一次操作中所有文件的总大小，而 `Size` 只针对单个文件的大小。在此情形下，需要使用 `Size`。

要把上传文件的最大尺寸限制在 50 KB，请在调用 `receive()` 方法之前加入下面的代码（已高亮显示）：

```php
$uploader->setDestination('C:/upload_test');  

**$uploader->addValidator('Size', FALSE, '50kB');**  

$success = $uploader->receive();
```

默认的 ZF 样式使用 `kB`（小写 k）且数字与单位之间不留空格。不过第三个参数是大小写不敏感的，接受数字与单位之间有空格的写法。

**11** 文件上传最常见的用途是上传图片。理想情况下应使用 `IsImage` 验证类来确认上传的文件确实是图片。但在此阶段，它在上传无效文件时会返回空的错误信息。解决办法是改用 `MimeType` 验证类。

添加如下验证器：

```php
$uploader->addValidator('Size', FALSE, '50kB');  

**$uploader->addValidator('MimeType', FALSE, 'image');**  

$success = $uploader->receive();
```

`'image'` 作为第三个参数单独使用时会接受任意类型的图片。

**12** 保存 `process_upload.php`，再次测试表单。如果选择的图片小于 50 KB，会看到上传成功的提示信息；如果选择了其他类型的文件，则会出现类似下面的错误信息：

![Image](graphics/fig09_12.jpg)

对技术熟练的用户而言这已经足够，但对普通用户可能会产生困惑。后续会看到如何自定义错误信息。

**13** 再添加一个验证，用于检查图片的最小高度和宽度，方法如下：

```php
$uploader->addValidator('MimeType', FALSE, 'image');  

**$uploader->addValidator('ImageSize', FALSE, array('minheight' => 500, 'minwidth' => 1000));**  

$success = $uploader->receive();
```

最小高度和宽度的数值通过第三个参数的数组传递，使用区分大小写的键 `‘minheight’` 与 `‘minwidth’`。这里故意把数值设得很高，以确保会触发错误。

**14** 保存 `process_upload.php`，再次测试上传表单。如果选择本书 images 文件夹中的任意文件，应能看到类似下面的错误信息：

![Image](graphics/fig09_13.jpg)

**15** 作为最后一系列测试，将最小高度和宽度改为 **50** 与 **100**，并加入验证器防止上传文件覆盖已存在同名文件。修改后的代码如下：

```php
$uploader->addValidator('ImageSize', FALSE, array('minheight' => **50**,'minwidth' => **100**));  

**$uploader->addValidator('NotExists', FALSE, $destination);**  

$success = $uploader->receive();
```

`NotExists` 验证器的第三个参数是上传文件夹的路径。

**16** 保存 `process_upload.php`，再次测试上传表单以上传图片。只要满足所有条件，就会看到成功消息。如果文件已经上传过，则会出现类似下面的错误信息：

![Image](graphics/fig09_14.jpg)

对技术熟练的用户这已经足够，但对普通用户可能会产生困惑。更好的做法是为文件生成唯一名称并告知用户新名称。你很快将学到如何实现这一点。

你可以把代码与 lesson09/completed 中的 `upload_test_02.php` 以及 `process_upload_02.php` 进行对比。

##### *去除文件名中的空格*

Windows 与 Mac OS X 允许文件名中包含空格。虽然空格让文件名更易阅读，但在 Linux 服务器上会造成问题，因此有必要过滤上传文件名并把空格替换为下划线。即使你的站点托管在 Windows 服务器上，去除空格也是个好习惯，尤其是上传文件将被用于网站时。空格在 URL 中不能直接出现，需要转换为 `%20`，这看起来既丑陋又不够专业。

下面的练习通过在 `process_upload.php` 中去除文件名的空格来改进该脚本。你可以继续使用上一步的文件，或以 `lesson09/completed/process_upload_02.php` 的副本作为起点。

**1.** 在 `process_upload.php` 中找到下面这段代码（大约在第 12–18 行）：

```php
$success = $uploader->receive();  

if (!$success) {  
    $messages = $uploader->getMessages();  
} else {  
    **$filename = $uploader->getFileName(NULL, FALSE);**  
    $messages[] = "$filename uploaded successfully";  
}
```

这段代码负责实际上传并准备成功或失败的提示信息。

**2.** 为了去除文件名中的空格，需要在下面的第一个验证器之前先获取文件名并进行处理。把上一步高亮的那行代码剪下来，放在第一个验证器上方：

```php
$uploader->setDestination($destination);  

**$filename = $uploader->getFileName(NULL, FALSE);**  

$uploader->addValidator('Size', FALSE, '50kB');
```

**3.** 使用 `str_replace()` 可以在字符串中替换字符。该函数最多接受四个参数，前三个是必需的：

- 要替换的字符（或字符串）
- 替换为的字符（或字符串）
- 要操作的目标字符串
-（可选）用于记录替换次数的变量

虽然把去除空格的代码放在下一行（即 `$filename = …` 那行）看起来更直观，但后续还有其他修改要做，所以把它放在 `receive()` 调用之前更合适：

