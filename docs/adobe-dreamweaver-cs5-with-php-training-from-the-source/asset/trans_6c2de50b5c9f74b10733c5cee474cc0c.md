
-   [上传失败时，错误信息会被添加到 `$errors` 数组中，而不是 `$messages` 数组。为了防止问题文件的详细信息被插入数据库，使用 `$no_spaces` 作为数组键来标识。

-   另一个更改是：如果上传成功，文件名、说明文字以及对应的 `place_id` 会被添加到一个新数组 `$images` 中。顶级数组的每个元素包含单张图片的详细信息。例如，第一个数组元素包含以下子数组：`$images[0]['filename']`、`$images[0]['caption']` 和 `$images[0]['place_id']`。

**12** 保存 `upload_images.php`，并在 `db_insert_place.php` 中，`checkDuplicatePlacename()` 的条件语句之后加入以下条件语句：

```php
if (!$errors) {  

    checkDuplicatePlacename($dbRead, $_POST['name'], $errors);  

}  

if (!$errors) {  

    require_once('upload_images.php');  

}
```

你可以与 lesson10/completed/scripts 中的 `upload_images.php`、`db_definitions_02.php` 和 `db_insert_place_02.php` 进行对比。

**插入地点和照片数据**

在验证数据并成功上传照片后，需要分别向 `places`、`photos` 和 `place2photo` 表插入数据。SQL `INSERT` 查询无法一次性处理多个表，因此必须分别处理。同时需要查询数据库以获取每条记录的主键，以便在 `place2photo` 表中作为外键使用。此操作使用 `Zend_Db lastInsertId()` 方法，但必须在插入记录后立即调用。

其余代码相对简短且易于理解。

**1.** 在 `db_insert_place.php` 中，再添加一个条件语句，确保照片上传无错误：

```php
if (!$errors) {  

    require_once('upload_images.php');  

}
```

所有剩余代码均需放在此条件语句内部。

**2.** 创建要插入 `places` 表的值数组：

```php
$data = array(
    'name'        => $_POST['name'],
    'state_id'    => $_POST['state_id'],
    'description' => $_POST['description'],
    'link_name'   => str_replace(' ', '', $_POST['name']),
    'created'     => new Zend_Db_Expr('NOW()')
);
```

`name`、`state_id` 和 `description` 列的值直接来自表单。`link_name` 列的值来自表单的 `name` 字段，经过 `str_replace()` 处理，去掉所有空格（如 "San Francisco" 变为 "SanFrancisco"），因为 URL 中不应包含空格。

`updated` 列无需手动设置，因为它会自动初始化为当前时间戳。但需要在 `created` 列显式设置值，使用 MySQL 的 `NOW()` 函数，通过 `Zend_Db_Expr` 类包装该函数。

**3.** 使用 `insert()` 方法插入数据：

```php
$inserted = $dbWrite->insert('places', $data);
```

**4.** 若有照片上传，需要获取新记录在 `places` 表中的主键，并将其信息插入 `photos` 与 `place2photo` 表。若未上传任何照片，则无需额外操作，只需显示相应的结果消息。

`insert()` 方法的返回值保存在 `$inserted` 中。若 `upload_images.php` 生成的 `$images` 数组包含元素，则说明已上传照片。使用 `$inserted` 与 `$images` 两个值判断是否需要获取新记录的主键。在下一行添加以下代码：

```php
if ($inserted && isset($images)) {  

    $place_id = $dbWrite->lastInsertId();  

}
```

此代码获取 `places` 表的主键并存储到 `$place_id` 变量中。

**5.** 现在可以遍历 `$images` 数组，为每张图片在 `photos` 表中插入文件名和说明文字。插入数据后，立即使用 `lastInsertId()` 方法获取主键，并将 `places` 表和 `photos` 表的主键分别插入 `place2photo` 表。相关循环代码如下：

```php
if ($inserted && isset($images)) {  

    $place_id = $dbWrite->lastInsertId();  

    foreach ($images as $image) {  

        $data = array(
            'filename' => $image['filename'],
            'caption'  => $image['caption']
        );  

        $dbWrite->insert('photos', $data);  

        $photo_id = $dbWrite->lastInsertId();  

        $data = array(
            'place_id'  => $place_id,
            'photo_id'  => $photo_id
        );  

        $dbWrite->insert('place2photo', $data);  

    }  

}
```

无需检查图片上传是否出错，因为在第 1 步中添加的条件语句已确保若出现问题，脚本不会继续执行。

**6.** 剩余工作是准备用于报告处理结果的消息。下面的代码应放在处理图片的条件语句之后：

```php
if ($inserted) {  

    $messages[] = $_POST['name'] . ' is now listed in the database';  

} else {  

    $errors[] = $_POST['name'] . ' could not be inserted';  

}
```

**7.** 保存 `db_insert_place.php`，并通过在“Place name”和“Description”字段输入值、选择州，然后浏览到 images 文件夹选择几张图片并添加说明，最后点击“Insert Place”。如果代码和数据库结构正确，顶部会显示一系列成功消息。

![image](graphics/fig10_18.jpg)

**8.** 检查 `image_upload` 文件夹，选中的照片副本应已添加到该文件夹。同时在 phpMyAdmin 中检查 `places`、`photos` 和 `place2photo` 表，确认首次插入的数据已存在。

![image](graphics/fig10_19.jpg)

![image](graphics/fig10_20.jpg)

![image](graphics/fig10_21.jpg)

如果出现问题，请仔细对比所有文件与 lesson10/completed 中的 `insert_place_02.php`，以及 lesson10/completed/scripts 中的 `db_definitions_02.php`、`db_insert_place_03.php` 和 `upload_images.php`。同时检查数据库结构，并从 lesson10/start/scripts/cms_structure.sql 加载结构。由于脚本复杂，可能存在许多潜在错误点。

在继续下一部分之前，向数据库中添加两三条记录。images 文件夹中包含亚利桑那州、加利福尼亚州、内华达州和犹他州共十张地点的照片，但无需局限于这些。并非每个地点都需要配图，说明文字也是可选的。CMS 设计用于以后添加和编辑照片详情。

**单独插入照片**

此管理页面的所有繁重工作已完成。`upload_images.php` 脚本负责验证并上传图片。主要任务是编写插入图片详情到数据库的脚本。

**1.** 打开 `insert_photos.php`。`<select>` 菜单需要填充已在数据库中注册的地点列表，这与插入地点时的州 `<select>` 菜单用法相同，用于存储每个地点的主键，以便在 `place2photo` 表中作为外键插入。
