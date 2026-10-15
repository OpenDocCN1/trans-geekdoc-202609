
-   [检查是否通过查询字符串传递了名为`place`的变量。如果传递了，则将该值传递给步骤2中创建的函数，并将结果赋值给`$place`。否则，`$place` 设置为`NULL`。  
    `#` 在 `<title>` 标签中显示地点名称：  
    `<title>Destinations West: <?php if ($place) { echo $place\['name'\]; } ?>`

    条件语句用于防止`$place` 为`NULL`。

    `##` 向下滚动到主内容 `<div>`（约在第21行），并用条件语句包裹 `<h2>` 标题，如果`$place` 等同于`FALSE`则显示“No result found”。在`else` 分支中，显示地点名称和州名，如下：

    `<div id="maincontent">  

  <?php if (!$place) { >  
    <h2>No record found</h2>  

  <?php } else { >  
    <h2><?php echo $place\['name'\] . ', ' . $place\['state_name'\]; ?></h2>  

  <?php } >  

</div>`

    `##` 保存`details.php`，点击“Live View”进行测试。应看到“No record found.”。退出“Live View”，切换到`gallery.php`。

    点击`gallery.php`的“Live View”，并按住`Ctrl`/`Cmd`选择其中一个“Learn more”链接。应看到选中地点的名称和州名。

    ![image](graphics/fig12_20.jpg)

    退出“Live View”，返回`details.php`。

    `##` 描述字段的文本在插入表单时通过连续按两次回车/换行已被分成段落，但这并不插入`<p>`标签。由于 HTML 忽略代码中的换行，文本会显示为连续块。常见的解决办法是将文本传递给`nl2br()`函数，它会将换行转换为 HTML `<br />` 标签。但这并不能解决在每个段落中插入图片的问题。你需要动态构建 HTML 结构。第一步是将文本拆分为数组。

    在`details.php`，在“Related Files”工具栏中选择`db_definitions.php`，并添加以下函数定义：

    ```php
    function splitParas($string) {  
        return preg_split('/\[\\r\\n\]+/', $string);  
    }
    ```

    该函数使用`preg_split()`，通过正则表达式匹配一个或多个换行符或回车符，将字符串拆分为数组元素（详见“构建验证脚本（1）”在[Lesson 7](#ch07.html#ch07)的解释）。

    `##` 保存`db_definitions.php`，在“Related Files”工具栏中选择“Source Code”返回`details.php`。使用你刚创建的函数将描述字段的内容转换为段落，并用`for`循环构建 HTML（新代码放在之前只包含右大括号的 PHP 代码块内）：

    ```php
    <h2><?php echo $place\['name’\] . ', ' . $place\['state_name’\]; ?></h2>  

    <?php   

    $paras = splitParas($place['description']);  

    for ($i = 0, $num_paras = count($paras your text here... 

    