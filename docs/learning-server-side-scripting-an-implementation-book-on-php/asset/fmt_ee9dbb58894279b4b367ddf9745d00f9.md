
请勿立即检查运行情况！我们没有名为 `elist.php` 的文件，这将导致 404 文件未找到错误。

我们将创建一个包含注册列表的文件，然后执行注册流程。此页面或多或少将类似于 `clist.php`。

### 列出注册信息

使用“另存为”选项创建 `elist.php`。将 `title` 标签内容更改为 Enrollments。

在文件开头包含以下代码：

```php
<?php
include ('check.php');
if($category == 'instructor'){
  header('logout.php');
}
?>
```

此处，我们检查讲师是否误通过 URL 进入此页面，并重定向到 `logout.php` 页面。只有学习者可以访问此页面。

替换 `main` 标签内容为：

```php
<main>
<section>
<?php 
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='logout.php'>Logout<a/></p>";
$fetch_enrolls = mysqli_query($con,"SELECT * FROM enroll WHERE learn_mail = '$usersession'");
if(mysqli_num_rows($fetch_enrolls) == 0){
 echo "No enrollments so far!";
}
else{
 echo "<table style='margin: 0 5%;text-align:left;'>";
 echo "<tr>";
 echo "<th style='width:30%;'> Course Title </th>";
 echo "<th style='width:15%;'> Start Date </th>";
 echo "<th style='width:15%;'> Completion Date </th>";
 echo "<th style='width:15%;'> Access Content </th>";
 echo "<th style='width:15%;'> Progress </th>";
  echo "</tr>";
} 
while($fetched = mysqli_fetch_row($fetch_enrolls)){
 echo "<tr>";
 $get_coursetitle = mysqli_query($con,"SELECT * FROM courses WHERE course_code = $fetched[0]");
 $coursetitle = mysqli_fetch_array($get_coursetitle);
  echo "<td>".$coursetitle['course_title']."</td>";
 echo "<td>".$fetched[3]."</td>";
 if($fetched[4] == NULL){
   echo "<td>Not completed</td>";
 }
 else{
   echo "<td>".$fetched[4]."</td>";
 }
 echo "<td>";
 echo "<form method='post' action='contents.php'><input type='hidden' name='txtcourse' value='$fetched[2]'>";
 echo "<input type='submit' name='access' value='View' class='frmbtn'></form>";
  echo "</td>"; 
 echo "<td><progress id='progress' value='".get_progress($con,$fetched[0])."' max='100'></progress> ".get_progress($con,$fetched[0])."%</td>";
 echo "</tr>";
}
echo "</table>";
?>
</section>
</main>
```

*   我们在显示检索字段时进行了一项检查。

    我们检查 `$fetched[4] = NULL`（即完成日期为 NULL）。

    如果为 null，意味着课程正在进行中，因此显示“not completed”消息。

    如果不为 null，则显示课程完成日期。

*   我们通过表单的 POST 方法提供内容访问权限。只要课程是免费的，这不是问题。但涉及付费课程学习时，这会成为一个问题。所以，为了安全起见，我们使用 POST 方法表单。

*   我们还在表单中提供了 `action` 属性。因此，`contents.php` 将处理通过此表单提交的值。

现在，让我以学习者身份登录，然后注册其中一门课程。

*这是一个 GIF 图像。请确保您的设备支持 GIF。*

![1604666907-enroll-course](Images/image00351.gif)

下一项工作是查看课程内容！

---

### 访问课程内容

我们必须设计一个页面来查看课程内容——即讲师上传的文件。

*   我们将使用下拉选择框显示内容标题。根据标题选择，将显示相应的内容文件。

*   由于我们有不同的文件类型，我们将使用 `iframe` 标签来显示它们。

首先，使用“另存为”并将文件命名为 **contents.php**。

没有特定的设计要求。所以，像往常一样，让我们从页面开头要放置的 PHP 片段开始。

```php
<?php
include ('check.php');
$course = 0;
$contents = 0;
if(isset($_POST['access'])){
  $course = $_POST['txtcourse'];
}
?>
```

我们还有一些内容要添加。我们将在完成 `main` 标签片段后添加。`$course` 将在整个学习过程中保存课程代码。`$contents` 将保存要显示的内容 ID。

替换 `main` 标签内容为：

```php
<main>
<section>
<?php 
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='elist.php'>Back to Enrollments</a></p>";
echo "<p>";
echo "<form method='post'>";
echo "<input type='hidden' name='txtcourse' value='$course'>";
echo "<select name='txtcontent'>";
echo "<option value='999'>Choose the content title</option>";
$fetch_contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
while($fetched = mysqli_fetch_row($fetch_contents)){
 echo "<option value='$fetched[0]'>".$fetched[1]."</option>";
}
echo "</select>";
echo "<input type='submit' name='getcontent' value='Go' class='frmbtn'>";
echo "</form>";
echo "</p>";
?>
</section>
</main>
```

如果未选择内容标题，我们将提交表单，其中“Choose the content title”选项的值为 999。我们将在后面部分使用这一点。

转到 `elist.php` 并点击 View（课程名称 1 的 View 链接）

![8-5-2](Images/image00352.jpeg)

您可以在下拉列表中找到课程的内容标题。根据此选择，我们将在 `iframe` 标签中显示内容。

在文件开头添加几行代码：

```php
<?php
include ('check.php');
$course = 0;
$contents = 0;
if(isset($_POST['access'])){
  $course = $_POST['txtcourse'];
}
if(isset($_POST['getcontent'])){
  $course = $_POST['txtcourse'];
  $contents = $_POST['txtcontent'];
}
?>
```

我们在表单提交时将课程代码赋值给 `$course`，将内容 ID 赋值给 `$contents` 变量。

我们将在表单下方显示内容文件。我们将向 `main` 标签元素添加另一个 `section` 元素。已经有一个 `section` 元素。将其放置在 `</section>` 和 `</main>` 之间：

```php
<section>
<?php
if(($contents == 999) || ($contents == 0)){
 echo "Please choose a content title!";
}
else{
 $fetch_content = mysqli_query($con,"SELECT * FROM contents WHERE content_id = $contents");
 if($fetch = mysqli_fetch_row($fetch_content)){
   echo "<h4>".$fetch[1]."</h4>";
   $filestring = explode('.',$fetch[3]);
   $file_ext= strtolower(end($filestring));
   $exts = array('doc','docx','ppt','pptx');
   if(in_array($file_ext,$exts)){
     echo "<p>The content will be downloaded!</p>";
   }
   echo "<p><iframe src='$fetch[3]' height='auto' width='80%' height='500px' frameborder='0'></iframe></p>";
  }
}
?>
</section>
```

此处，我们检查 `$contents` 值是否等于 0 或 999，然后显示“Please choose a content title!”消息。这意味着，每当未选择内容标题时，将显示此消息。

像往常一样，我们查找文件的扩展名，如果它是 doc、docx、ppt、pptx 之一，则无法在 HTML 文件中显示。因此，我们打印一条消息，提示文件将被下载，当 `iframe` 标签加载时下载将开始。如果文件扩展名是 pdf、mp4、txt、rtf 之一，则通过 `iframe` 标签显示。

尝试选择一个内容，查看相应文件是显示还是下载。

现在，还有一项待办任务！

### 记录学习者进度

此进度也将在同一页面中记录。

我们需要在 `iframe` 标签下方包含插入记录表的代码：

替换上面的 if 代码块：
