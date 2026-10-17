
## 编辑记录 -> 详情

| First Name | Last Name | Number | Date | Time Stamp | Calculation | Record ID | Edit Record |
|---|---|---|---|---|---|---|---|
| Todd | Dulli | 47 | 09/07/2010 | 15:46 | | 48 | |
| Tin | Kramer | 13 | 01/01/2010 | 15:56 | | 54 | |
| Fred | Hutch | 14 | 09/09/2010 | | 59 | |
| Mike | Adams | 37 | 25/25/2010 | | | 81 | |
| Heath | Beil | 21 | 01/01/2010 | 23:26 | | 82 | |
| Kevin | Conrad | 29 | 25/25/2010 | | | 83 | |
| Eme | Emery | 39 | 25/25/2010 | | | 84 | |
| John | Garland | 27 | 25/25/2010 | 21:06 | | 85 | |
| Luke | Greg | 35 | 25/25/2010 | 21:05 | | 86 | |
| Mate | Latos | 38 | 25/25/2010 | 22:07 | | 87 | |

<table>
  <tr>
    <th>姓</th>
    <td><input type="text" name="LastName" value="<?php echo $LastName; ?>" /></td>
  </tr>
  <tr>
    <th>单号</th>
    <td><input type="text" name="Number" value="<?php echo $Number; ?>" /></td>
  </tr>
  <tr>
    <th>日期</th>
    <td><?php echo $Date; ?></td>
  </tr>
  <tr>
    <th>时间戳</th>
    <td><?php echo $TimeStamp; ?></td>
  </tr>
  <tr>
    <th>修改 ID</th>
    <td><?php echo $modID; ?></td>
  </tr>
</table>
<p>
  <input name="save" type="submit" value="保存" />
</p>
<p>
  <?php echo $message; ?> '<a href="MultiUserEditRecord.php">点击此处返回列表页</a>' '
</p>
</body>
</html>

![](img/5a2c5fda68d42e5d65f51850276e49ec_207_0.png)

| 名字 | Todd |
| :--- | :--- |
| 姓 | Dwell |
| 单号 | 57 |
| 日期 | 09/07/2010 |
| 时间戳 | 08/03/2010 15:46:50 |
| 修改 ID | 147 |

点击此处返回列表页

图 7-53：MultiUserEditRecord.php 页面。

## 第 21 ：运行脚本 — 导入 XLS 文件

**目标：** 在本中，你将学习如何将 Excel 文件上传到服务器。然后使用脚本从 Excel 文件中导入记录。我们已经习惯了使用 FileMaker Pro 导入数据。遗憾的是，在 Web 页面上无法实现。导入数据的唯一方法是从存储在服务器上的文件。FileMaker Server 只会从 Documents 文件夹导入记录。该位置不在 Web 根目录内。由于安全问题，PHP 无法将文件移动到根目录之外——你不会希望未知的 Web 用户移动你的服务器或网络。因此，我们需要利用 Trio File 插件将文件从 Web 根目录移动到 FileMaker Documents 文件夹。

这是一个 Apache/OS X 技术。IIS 在运行此 PHP 代码时会抛出太多的通用 500 错误。代码在 IIS 上运行，但在上传完成后仍会显示错误。你需要 Trio File 插件服务器许可来使用此技术。请遵循 Trio 的说明在 FileMaker Server 上安装插件，以便配合 Web 发布引擎使用。你可以从我们的网站 www.trio.com 或提供的示例文件获取 Trio File Plugin 演示。在编写此时，我已经验证了插件第 6 版本的使用。

困难

**示例文件：**
- `PHPFiles/Advanced/Lesson21/Import.php`
- `PHPFiles/Advanced/Lesson21/Trio File Plugin v6.1`
- `PHPFiles/Advanced/Lesson21/Import/sample_import.xls`

页面导航：

![](img/5a2c5fda68d42e5d65f51850276e49ec_208_0.png)

**FileMaker API 方法：**
- `newSqlCommand()`\`execute()`
- `getMessage()`
- `newFindAllCommand()`
- `getLastRecord()`
- `EditRecord()`
- `newEditCommand()`
- `setField()`
- `PerformScriptCommand()`

**代码：**
我已经在之前的示例中使用过导入过程。因此，从 PHP 代码的角度来看，并没有什么真正新东西。此过程中的重要变化在于使用了 Trio File 插件以及通过 FileMaker 脚本将 xls 文件从根目录移动到 FileMaker Server 的 Documents 文件夹。

始终从包含数据库连接开始。

```php
<?php
include("../../Conn/dbaccess.php");
?>
```

创建用于在导入过程中向用户显示的消息变量。

```php
<?php
echo $message;
```
```php
echo $importMessage;
?>
```

创建将文件导入到服务器的表单。点击“导入”运行脚本导入记录。

```html
<p>
  <form action="ImportXLS.php" method="post" enctype="multipart/form-data">
  用于导入的 xls 文件：<input name="xls_file" type="file" />
  <input type="submit" name="import" value="导入" />
  </form>
</p>
```

检查用户是否点击了“导入”按钮。使用 `application/vnd.ms-excel` 验证他们尝试上传的文件是否为 Excel 文件。

> 你**绝不**允许未知用户向你的数据库导入记录。此过程通常应留给内部员工或信任的业务伙伴。

```php
if (isset($_POST['import']) == 'Import') {
  if ($_FILES['xls_file']['type'] == 'application/vnd.ms-excel') {
```

在 Import php 表中添加新记录。在本例中，我使用一个单独的表来跟踪所有用于向数据库导入记录的文件。你可以将其视为日志文件。这样，你就可以排查任何导入失败的文件。

```php
$request = $fm->newAddCommand('Import php');
$request->execute();
```

捕获错误，如果导入成功，你可以从最后记录中获取记录 ID，该记录是由 FileMaker 脚本生成的。当然，如果由于文件不是 Excel 导致验证失败，你应该向用户提供错误消息并停止脚本。

```php
if (FileMaker::isError($result)) {
  $message = "<p>" . $result->getMessage() . "</p>";
  exit;
} else {
  $request = $fm->newfindAllCommand('Import php');
  $result = $request->execute();
  $record = $result->getLastRecord();
  $id = $record->getObjectID();
} else {
  $type = $_FILES['xls_file']['type'];
  die ('Only xls files are allowed to be uploaded: ' . $type);
}
```

```php
// FileMaker 语法: getLastRecord()
$record = $result->getLastRecord();
```

接下来，检查从 `$_FILES` 超局变量返回的任何通用错误。

```php
if ($_FILES['xls_file']['error'] > 0) {
    $error = $_FILES['xls_file']['error'];
    die ('上传文件出错：' . $error);
}
```

定义服务器上的目录。

```php
$import_directory = 'Import/';
```

获取文件的临时名称。

```php
$temporary_file = $_FILES['xls_file']['name'];
```

从文件中获取扩展名。

```php
function extension($filename) {
    $parts = explode(".", $filename);
    $ext = end($parts);
    return $ext;
}
```

将文件移动到服务器。

```php
$move = rename($temporary_file, $import_directory . $filename);
if ($move) {
    $url = $import_directory . $filename;
    $insert = $fm->newEditCommand('Import php');
    $insert->setField('URL', $url);
    $insert->execute();
}
```

最后，向用户提供上传的消息。

```php
$importMessage = '<p>文件上传成功。</p>';
```

```php
echo '<meta http-equiv="refresh" content="3;URL=' . $_SERVER['PHP_SELF'] . '">';
?>
```
![](img/5a2c5fda68d42e5d65f51850276e49ec_211_0.png)

图 7-54：ImportXLS.php 页面。

### PHP 导入记录

FileMaker 脚本从 xls 文件导入记录我创建一个完整的示例。在生产系统中，知道何时发生导入失败以及是哪个文件出错是非常重要的。这样你就可以在成功之前重写你的脚本。它还允许你在夜间安排导入，以减少高峰期对服务器的使用。

有几种免费方法可以将文件从根文件夹移动到 FileMaker Documents 文件夹。我认为 Trio 插件是最好的方法，因为它与 FileMaker 脚本协作工作，并且相对容易使用。此外，该插件对于许多任务非常多功能。唯一的缺点是它不是免费。此过程你需要 Web 许可。

此脚本在 FileMaker Server 和 FileMaker Pro 客户端上的运行方式完全不同。请确保仅从示例网页或 FileMaker Server 计划（Schedule）测试此脚本。

要获取 FileMaker Server Documents 文件夹中的文档列表，可以使用 `Get(DocumentsPathListing)`。要获取 Documents 文件夹的动态路径，可以使用 `Get(DocumentsPath)`。请注意，FileMaker Server 中有两个名为 "Documents" 的文件夹，正确的文件夹位于 `FileMaker Server/Data/Documents`。你还需要更改 Documents 文件夹的文件权限，启用“所有人（everyone） = 读/写（Read/Write）”。然后将其应用于文件夹中的所有文件。如果不执行此步骤，FileMaker 将无法从 xls 文件中导入记录，因为它将无法打开文件读取记录。

| FileMaker Server **仅**从以下位置导入文件： |

| :--- |

| FileMaker Server/Data/Documents/ |

你必须将文件夹权限设置为所有人 = 读/写

![](img/5a2c5fda68d42e5d65f51850276e49ec_212_0.png)

图 7-55：Documents 文件夹权限。所有人 = 读/写。

通过开启“允许用户中止（Allow User Abort）”和“错误捕（Error Capture）”来启动脚本。如果发生任何错误，这将停止脚本并防止任何对话框引起问题。

Allow User Abort [ On ]

Set Error Capture [ On ]

接下来，你可以运行一个脚本，使用许可证提供的密钥来注册 Troi File 插件。出于演示之目的，它在未注册的情况下可以运行几小时。如果你需要更多时间，可以随时重启服务器。目前，脚本中显示此代码以使插件以演示模式运行。

```
Perform Script [ " Register Troi File Plugin ]
```

通过脚本参数设置 `$RecordID`。这是要导入的文件名。

Set Variable [ $RecordID; Value:Get(ScriptParameter) ]

将 `$FilePath` 设置为由 Troi File 插件移动到 Documents 文件夹的文档。文件名将始终与 RecordID 和扩展名 .xls 关联。确保对 macOS 或 Windows 使用正确的路径。

由于 FileMaker Server 12 的初始结果是 Web 发布引擎中的一个已知 bug，它将 Documents 文件夹计算为 `FileMaker Server/Documents`。因此，在修复之前，你必须硬编码正确文件夹路径 `FileMaker Server/Data/Documents`。我已经禁用了数据库脚本中已解决的动态代码。

```
If[Abs(Get(SystemPlatform))>1]
  Set Variable [ $FilePath; Value:filemac:/Macintosh HD/Library/FileMaker\nServer/Data/Documents/" & $RecordID & ".xls"]
else
  Set Variable [ $FilePath; Value:filewin:C:/Program\Files/FileMaker/FileMaker Server/Data/Documents/" & $RecordID & ".xls"]
End If
```

从 Web根设置文档的 `$Source`。然后将文档的 `$Destination` 设置为 FileMakerServer/Data/Documents 文件夹。对于跨平台，检查脚本是否运行在 OS X 或 Windows 上。

```
If[Abs(SystemPlatform)=1]
  Set Variable [ $Source; Value:filemac:/Macintosh\nHD/Library/WebServer/Documents/PHPFiles/Advanced/Lesson21/Import/" & \n$RecordID & ".xls"]
  Set Variable [ $Destination; Value:$FilePath]
else
  Set Variable [ $Source; Value:\n  filewin:C:/input/www/root/PHPFiles/Advanced/Lesson21/Import/" & $RecordID & \n  ".xls"]
  Set Variable [ $Destination; Value:$FilePath]
End If
```

告诉 Troi File 插件将文件从 `$Source` 位置移动到 `$Destination` 位置。请参考 Troi 文档使用其插件的语法。

```
Set Variable [ $TroiFilePlugin; Value:TrFile_MoveFile("-Unused"; $Source \n$Destination) ]
```

记录表中记录的更改。在本示例中，我记录了脚本参数中的 RecordID、最终文件路径以及脚本导入的实际记录数。

Go to Layout [ "Import php" (import) ]

```
Enter Mode [
  Set Field [ import:RecordID; $RecordID ]
  Perform find [
  Set Field [ import:ScriptParameter; $RecordID ]
  Set Field [ import:DocumentsPath; $FilePath ]
```

转到执行操作的布局。

New Window [ Name: "Import" ]

Go to Layout [ "Demo php" (php_demo) ]

捕获表中当前的记录数，以便你可以准确记录导入了多少记录。

Set Variable [ $RecordCount; Value:Get ( TotalRecordCount ) ]
