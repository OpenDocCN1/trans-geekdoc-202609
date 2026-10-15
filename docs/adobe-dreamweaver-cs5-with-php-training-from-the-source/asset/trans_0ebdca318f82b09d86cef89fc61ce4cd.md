
## 2. 在 db_definitions.php 中创建以下函数，用于查询 `places` 表中每条记录的 `place_id` 和 `name` 列：

function getAllPlaces($read) {  
  
  $sql = 'SELECT place_id, name FROM places ORDER BY name';  
  
  return $read->fetchAll($sql);  
}

此函数类似于之前创建的 `getAllStates()` 函数。它接受一个带有读取权限的 `Zend_Db` 对象作为唯一参数，并返回数据库查询结果作为数组。

## 3. 保存 db_definitions.php，然后切换到 db_insert_photos.php。在 `try` 块内部，调用你刚刚创建的函数，并将结果赋值给 `$places`，如下所示：

try {  
  
  require_once('db_definitions.php');  
  
  **$places = getAllPlaces($dbRead);**  
  
} catch (Exception $e) {  

## 4. 现在可以使用 `$places` 来填充 `<select>` 菜单。在设计视图中选择该菜单，点击服务器行为面板中的加号按钮，选择 Zend Select Menu。在对话框中使用以下设置：

![image](graphics/fig10_22.jpg)

由于 `<select>` 菜单位于循环内部，其“选择标签”菜单中的值包含 PHP 标签和 `$i` 计数器。但是，“菜单名称”应仅为 **place_id{$i}**，因为它将作为 `$_POST` 变量的键使用。

## 5. 关闭 Zend Select Menu 对话框，检查刚刚插入的代码（对话框中输入的值已高亮显示）：

<select name="place_id<?php echo $i; ?>" id="place_id<?php echo $i; ?>">  
  
  <option value="0">-- Select place --</option>  
  
  <?php  
  
  foreach (**$places** as $row) {  
  
    echo "<option value='{$row['**place_id**']}'";  
  
    if ($errors && $_POST["**place_id{$i}**" ] == $row['**place_id**']) {  
      
      echo 'selected="selected"';  
  
    }  
  
    echo ">{$row['**name**']}</option>";  
  
  }  
  
?>  
  
</select>

## 6. 保存页面，点击 Live View 进行测试。依次点击每个 `<select>` 菜单，它们应显示 `places` 表中登记的所有名称。

![image](graphics/fig10_23.jpg)

如果无法正常工作，请将您的代码与 lesson10/completed 中的 insert_photos_02.php、scripts/db_definitions_03.php 和 scripts/db_insert_photos_01.php 进行比较。

## 7. 表单现在已完成。接下来，需要编写处理表单提交点击按钮时的脚本。

提交按钮的 `name` 属性为 `insert`，因此处理脚本需要放在 db_insert_photos.php 中的条件语句内部，并在步骤 3 中添加的代码之后添加：

  
  $places = getAllPlaces($dbRead);  
  
  **if (isset($_POST['insert'])) {**  
  
    // 处理代码放在这里  
  
  }  
  
} catch (Exception $e) {  

## 8. 在条件语句内部，添加验证器以检查标题的长度，并遍历它们。然后，如果没有错误，包含 upload_images.php。代码如下：

$val = new Zend_Validate_StringLength($captionMin, $captionMax);  
for ($num = 1; $num <= $photofields; $num++) {  
  
  validateCaption($_POST["caption{$num}"], $num, $val, $errors);  
}  
  
if (!$errors) {  
  
  require_once('upload_images.php');  
  
}

这与 db_insert_place.php 中的代码相同，无需进一步说明。

## 9. 如果照片已上传，则在上一步的代码之后添加以下代码，循环遍历 upload_images.php 创建的 `$images` 数组，将详细信息插入 `photos` 和 `place2photo` 表：

if (isset($images)) {  
  
  foreach($images as $image) {  
    
    if (!array_key_exists($image['filename'], $errors)) {  
      
      $data = array('filename' => $image['filename'],  
                     'caption' => $image['caption']);  
      
      $dbWrite->insert('photos', $data);  
      
      $photo_id = $dbWrite->lastInsertId();  
      
      if ($image['place_id']) {  
        
        $data = array('place_id' => $image['place_id'],  
                       'photo_id' => $photo_id);  
        
        $dbWrite->insert('place2photo', $data);  
      
      }  
      
    }  
      
  }  
  
}

upload_images.php 中的代码会将文件名、标题和关联的 place 的主键存储在 `$images` 数组中。你刚刚插入的 `foreach` 循环会逐个处理每张图片。

首先，通过检查 `$errors` 数组是否包含文件名作为键来确认图片上传是否成功。如果文件名未作为数组键，说明图片上传正常，代码块内的语句会将值插入 `photos` 表的 `filename` 和 `caption` 列，并使用 `lastInsertId()` 捕获新记录的主键作为 `$photo_id`。

随后，另一个条件语句检查当前图片关联的 `place_id`。如果 `<select>` 菜单保持默认“Select place”，则值为 0，条件失败，不会向 `place2photo` 表添加数据。但如果选择了某个 place，其主键 (`place_id`) 会与照片的主键 (`photo_id`) 一起插入 `place2photo` 表。

## 10. 保存 db_insert_photos.php，并在 insert_photos.php 中测试表单。如果你选择一个已上传的照片，应该会看到它已被重命名的报告。

![image](graphics/fig10_24.jpg)

检查 cms/image_upload 目录中的文件，确认原文件和重命名后的文件都已存在。

如果有问题，请将您的代码与 lesson10/completed 中的 db_insert_photos_02.php 进行比较。

### 回顾项目进展

本课程完成了大量工作，CMS 仍未完全构建。下一课，你将创建列出所有地点和照片的页面，以及更新和删除单个记录的功能。你可能会想，是否可以使用 Dreamweaver 内置的对话框来更轻松地完成这些操作。答案是否定的。那样做需要对自动生成的代码进行大量编辑，导致脚本显著变长。Dreamweaver 没有内置上传文件或在多个表中插入数据的能力。

构建自定义 CMS 需要大量规划，但其优势在于它正好是你想要的。即使你最终决定使用现有的 CMS（如 Drupal、Joomla! 或 WordPress），在构建这个定制管理系统的经验也将让你更好地理解底层原理。这将使你更容易将现有系统适应自身需求。

## 你学到了什么

***在这一课中，你学到了：***

• 为旅游网站规划 CMS（第 345–346 页）

• 定义通过外键关联的表结构（第 346–348 页）

• 创建表单和脚本，用于上传图片并同时将相关数据插入数据库（第 349–374 页）

• 构建服务器行为，从 SQL 查询中填充 `<select>` 菜单（第 355–358 页）

• 使用 `<select>` 菜单插入外键到数据库表（第 371–374 页）

## 第 11 课：更新和删除相关表中的文件

### 你将学习

***在这一课中，你将：***

• 学习 `SELECT` 查询的基本语法

• 学习使用 `INNER JOIN` 和 `LEFT JOIN` 连接表

• 使用 `Zend_Paginator` 显示数据库结果的分页

• 创建服务器行为以配置 `Zend_Paginator`

• 更新和删除存储在多个表中的数据

### 所需时间

本课程约需 3 小时完成。

### 课程文件

***媒体文件：***

与 [第 10 课](#ch10.html#ch10) 相同

***起始文件：***

lesson11/start/delete_photo.php

lesson11/start/delete_place.php

lesson11/start/list_photos.php

