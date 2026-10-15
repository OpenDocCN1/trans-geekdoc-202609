
1. 在 update_place.php 中，使用 require_once() 在 DOCTYPE 声明上方引入 scripts/db_update_place.php。你在上一课中已经在 cms/scripts 文件夹中创建了该文件的副本。

2. 当在 list_places.php 中点击 EDIT 链接时，查询字符串会以如下方式传递要更新的记录主键：

http://phpcs5/cms/update_place.php**?place_id=2**

主键用于检索要更新的记录的详细信息。如果查询字符串缺失或包含错误的变量，应将用户重定向到 list_places.php。这同样适用于删除页面以及照片的更新和删除页面；如果查询字符串中缺少 `photo_id` 主键，应将用户重定向到 list_photos.php。

为了避免在四个页面中编写几乎相同的脚本，你可以创建一个函数来提取主键并在缺失时进行重定向。在 db_definitions.php 中添加以下函数定义：

function checkId ($id, $location) {  

  if (isset($\_GET\[$id\]) && is_numeric($\_GET\[$id\])) {  

    return intval($\_GET\[$id\]);  

  } elseif (isset($\_POST\[$id\]) && is_numeric($\_POST\[$id\])) {  

    return intval($\_POST\[$id\]);  

  } else {  

    header("Location: $location");  

    exit;  

  }  

}

checkId() 函数接受两个参数：要从查询字符串中提取的主键（如 place_id 或 photo_id）以及在出现问题时用户应被重定向的页面。

当更新页面首次加载时，主键应出现在查询字符串中。因此，第一个条件语句检查 `$_GET` 数组是否包含 `$_GET[‘place_id’]` 或 `$_GET[‘photo_id’]`。如果存在，`is_numeric()` 检查它是否为数字。若通过两项检查，`intval()` 将其转换为整数并返回。

如果第一个条件语句失败，`elseif` 子句对 `$_POST` 数组进行相同的检查并返回整数值。若仍然失败，`header()` 函数会重定向用户，`exit` 结束脚本执行。

**3.** 保存 db_definitions.php，并在 db_update_place.php 中使用新的 checkId() 函数为 $place_id 主键赋值，如下所示：

try {  

  require_once('db_definitions.php');  

  **$place_id = checkId('place_id', 'list_places.php');**  

} catch (Exception $e) {

**4.** 保存 db_update_place.php，并在浏览器中打开它。你应该会被重定向到 list_places.php。

![image](graphics/fig11_13.jpg)

**5.** 更新页面需要显示 `places` 表中要更新的记录详情。在 db_definitions.php 中创建一个函数来执行 SELECT 查询并返回结果数组。代码如下：

function getPlace($read, $place_id) {  

  $sql = "SELECT name, places.state_id, state_name, description, link_name  

          FROM places  

          INNER JOIN states USING (state_id)  

          WHERE place_id = $place_id";  

  return $read->fetchRow($sql);  

}

该函数接受两个参数：一个具有读取权限的 `Zend_Db` 对象和要获取的记录主键。

在 SELECT 查询中，需要将 `state_id` 列修饰为 `places.state_id`，以避免与 `states.state_id` 发生冲突，因为两个表都使用了相同的列名。直接将 `$place_id` 注入查询是安全的，因为 `checkId()` 函数已确保它是整数，无需使用 `quoteInto()`。虽然在更新表单中不需要 `state_name`，但在删除表单中会用到它。

只会返回一条记录，因此最后一行使用 `fetchRow()`，它返回一个关联数组，键为列名。

**7.** 保存 db_definitions.php，然后切换到 db_update_place.php。要在更新页面填充数据，需要选中记录的详情、所有状态的完整列表（用于 `<select>` 菜单）以及与该地点相关的照片。在 try 块中添加以下三行：

try {  

  require_once('db_definitions.php');  

  $place_id = checkId('place_id', 'list_places.php');  

  **$place = getPlace($dbRead, $place_id);**  

  **$states = getAllStates($dbRead);**  

  **$photos = getRelatedPhotos($dbRead, $place_id);**  

} catch (Exception $e) {

**8.** 更新记录后，应将用户返回到他们来源的页面。将用户返回到 list_places.php 会让他们回到列表的第一页，这对从深层列表开始的用户来说很不方便。

超全局变量 `$_SERVER[‘HTTP_REFERER’]` 存储指代页面的 URL。不幸的是，并非所有服务器都支持它，因此需要检查其存在情况并设置默认值。在你刚刚插入的代码后，于 try 块内添加以下代码：

if (isset($\_SERVER\['HTTP_REFERER’])) {  

  $returnto = $\_SERVER\['HTTP_REFERER’];  

} else {  

  $returnto = 'list_places.php';  

}

**NOTE:** HTTP_REFERER 是正确的，不要多加一个 R。

**9.** 保存 db_update_place.php，并切换到 update_place.php。在打开的 `<form>` 标签的 action 属性中使用 `$_SERVER[‘PHP_SELF’]`。正如第 8 课所学，这会去除 URL 中的查询字符串，因为提交表单时不需要它：

<form action="**<?php echo $­SERVER['PHP_SELF']; ?>**" method="post" name="form1" id="form1">

**10** 开始添加代码，将记录的详情（存储在 `$place` 和 `$photos` 数组中）填充到表单中。文本输入框和文本区域可以通过 `echo` 输出 `$place[‘name’]`、`$place[‘description’]` 和 `$place[‘link_field’]` 来填充。但如果验证失败，需要保留用户已做的更改。像下面这样编辑 name 文本输入框的 name 属性：

<input type="text" name="name" id="name" value="**<?php if (!$errors) {**  

**  echo $place['name'];**  

**} else {**  

**  echo $­_POST['name'];**  

**}?>**" />

页面首次加载时，`$errors` 数组为空，因此条件语句使用数据库结果 `$place['name']`。如果用户在提交表单时出错，`$errors` 为 TRUE，则显示 `$_POST['name']`，从而保留用户的编辑。

**11** 同样，使用 `link_name` 作为数组键，编辑 `link_name` 文本输入框的 `value` 属性。

**12** 由于 `<textarea>` 标签没有 `value` 属性，需要在打开和关闭标签之间使用相同的 PHP 块，并以 `description` 作为数组键进行填充。

