
$uploader->addFilter('Rename', array('target' => $no_spaces));

第三个传递给`addValidator()`的参数是一个以逗号分隔的可接受的文件扩展名列表。为了控制后续的操作，会设置一个布尔变量`$recognized`，初始值为`FALSE`。如果文件通过验证，则`$recognized`被重置为`TRUE`；否则，`else`分支会尝试确定文件的MIME类型并添加相应的文件扩展名。

`getMimeType()`方法返回官方的媒体类型格式，例如`image/jpeg`。为了将这种格式转换为文件扩展名，`$acceptable`数组以扩展名为键、对应的媒体类型为值的形式列出每种扩展名。`$mime`变量中的媒体类型和`$acceptable`数组作为参数传递给`array_search()`，该函数在数组中查找并返回第一个匹配值的键。因此，如果`$mime`是`image/jpeg`，则返回`jpg`。

如果MIME类型不在`$acceptable`数组中，`$key`为`FALSE`，并为`$messages[]`赋值错误信息；否则，会在`$no_spaces`后追加一个点号和`$key`。例如，如果上传的文件名为`lasvegas1`且没有扩展名，其MIME类型为`image/jpeg`，则文件名会变为`lasvegas1.jpg`，并将`$recognized`和`$renamed`重置为`TRUE`。

### ![Image](graphics/caution.jpg)**CAUTION!**

点号在双引号字符串内部被视为字面字符。如果省略引号，点号会被视为连接运算符，导致`lasvegas1jpg`而不是`lasvegas1.jpg`。

虽然缺失的扩展名会在文件重命名时添加，但`receive()`方法会自动重新运行验证测试。因此，没有扩展名的文件仍会在此阶段验证失败。调用`clearValidators()`方法可防止重新运行验证测试。

**4** 只有当文件具有已识别的扩展名时才上传。请将剩余代码包装在条件语句中：

$uploader->clearValidators();  

**if ($recognized) {**  

    $uploader->addFilter('Rename', array('target' => $no_spaces));  

    $success = $uploader->receive();  

    if (!$success) {  

      $messages = $uploader->getMessages();  

    } else {  

      $uploaded = "$filename uploaded successfully";  

    if ($renamed) {  

        $uploaded .= " and renamed $no_spaces";  

    }  

    $messages[] = $uploaded;  

    }  

**}**

} catch (Exception $e) {

**5.** 现在您已拥有不含空格的文件名以及有效的扩展名，可以检查文件名是否重复，并在必要时构建新文件名。相关代码应放在您刚才创建的条件语句顶部。代码相对简短，因此不必逐行构建，而是一次性添加全部代码。代码已注释，帮助您理解其工作原理。

if ($recognized) {  

  // 获取已有文件的名称  

**$existing = scandir($destination);**  

  // 检查上传文件名是否已在数组中  

**if (in_array($no_spaces, $existing)) {**  

    // 获取最后一个点号的位置  

    // 使用它来获取基名和扩展名  

**$dot = strrpos($no_spaces, '.');**  

    $base = substr($no_spaces, 0, $dot);  

    $extension = substr($no_spaces, $dot);  

    // 初始化计数器  

**$i = 1;**  

    // 使用循环在基名后添加计数器  

    // 检查新名称是否已存在于数组中  

**$do {**  

      $no_spaces = $base . '_' . $i++ . $extension;  

    } while (in_array($no_spaces, $existing));  

    // 设置$renamed为TRUE  

**$renamed = TRUE;**  

**}**  

  $uploader->addFilter('Rename', array('target' => $no_spaces));

`scandir()`函数检查目录并返回包含该目录中所有文件和文件夹名称的数组。因此，第一行高亮代码将`upload_test`文件夹的内容存储在`$existing`中。

条件语句使用`in_array()`判断上传文件名（`$no_spaces`）是否已存在于现有文件数组中。如果文件名不存在，则后续高亮代码被跳过，文件直接上传且文件名保持不变。

如果文件名已存在，则执行`if`块内的代码。代码首先使用`strrpos()`查找上传文件名中最后一个点号的位置。

### ![Image](graphics/caution.jpg)**CAUTION!**

请注意`strrpos()`中间的双“r”，它用于查找字符串中最后出现的字符位置。它容易与`strpos()`（查找首次出现的字符）混淆。记忆方式是第二个“r”代表“reverse”（逆向）。

随后，点号的位置用`substr()`将文件名分为两部分：`$base`和`$extension`。例如，若`$no_spaces`的值为`las_vegas1.jpg`，则`$base`为“las_vegas”，`$extension`为“.jpg”。

`do… while`循环（见“使用do… while循环”在[Lesson 3](#ch03.html#ch03)）会递增`$i`计数器并构建新文件名：

$no_spaces = $base . '_' . $i++ . $extension;

这仅仅是将文件名重新组合，在基名后加上下划线和数字。因此，第一次循环运行时，`$no_spaces`变为`las_vegas1_1.jpg`。循环的`while`条件再次使用`in_array()`检查新名称是否已存在于上传目录中。如果存在，循环继续；否则，循环停止，并将`$renamed`设置为`TRUE`。

**6.** 保存`process_upload.php`，然后再次测试上传表单，选择已上传的图片。此次会提示文件已上传并重命名。

![Image](graphics/fig09_17.jpg)

如果再次尝试，会看到数字在基名后递增。还可以尝试在上传前删除文件扩展名。脚本会重命名文件并添加正确的扩展名。

**7** 在资源管理器（Explorer）或查找器（Finder）中检查`upload_test`文件夹的内容。应能看到文件已正确转移并重命名。

您可以将代码与`process_upload_04.php`（位于lesson09/completed/scripts）进行比较。

##### *Adding an option to overwrite files*

如果您不希望为文件命名新名称，而是希望直接覆盖已有文件，只需在脚本的重写部分包裹一个条件语句，并在上传表单中添加一个选项以指示要执行哪种操作。

继续使用相同的文件。或者，您可以使用`process_upload_04.php`的副本作为起点。

**1.** 在`upload_test.php`的设计视图中，点击“浏览”按钮右侧，按回车键插入一个新段落。

**2.** 在新段落中输入**Overwrite existing file?**，按回车键插入另一个空段落。

**3.** 在空段落中，选择**插入 > 表单 > 单选按钮组**以打开单选按钮组对话框。

**4** 在“名称”字段中输入**overwrite**，并创建两个单选按钮，分别为**Yes**和**No**，对应的值为**y**和**n**。保持“排版方式”默认设置为“换行符（<br>标签）”，点击确定。

![Image](graphics/fig09_19.jpg)

**5.** 在设计视图中，选中“否”单选按钮，将“初始状态”属性设置为“已选中”。

![Image](graphics/fig09_20.jpg)

**6.** 保存`upload_test.php`，然后切换到`process_upload.php`。

**7.** 在`try`语句之前添加以下条件语句：

require_once('library.php');  

**$overwrite = FALSE;**  

**if (isset($_POST['overwrite']) && $_POST['overwrite'] == 'y') {**  

    $overwrite = TRUE;  

**}**

