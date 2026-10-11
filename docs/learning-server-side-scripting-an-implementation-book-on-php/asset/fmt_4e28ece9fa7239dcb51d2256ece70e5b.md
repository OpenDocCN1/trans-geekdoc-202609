
# 课程管理页面实现

## 主页面结构

```php
<main>
<section>
<?php 
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='dashboard.php'>Dashboard</a>&emsp;<a href='logout.php'>Logout<a/></p>";
echo "<h4><a href='newcourse.php'>Add New Course</a></h4>";
$fetch_courses = mysqli_query($con,"SELECT * FROM courses WHERE course_instruct = '$usersession'");
if(mysqli_num_rows($fetch_courses) == 0){
 echo "No courses created so far!";
}
else{
 echo "<table style='margin:0 10%;width:80%;;text-align:left;'>";
 echo "<tr>";
 echo "<th style='width:40%;'> Course Title </th>";
 echo "<th style='width:10%;'> Edit Details </th>";
 echo "<th style='width:10%;'> Manage Content </th>";
 echo "<th style='width:20%;'> Learners Count </th>";
 echo "</tr>";
} 
while($fetched = mysqli_fetch_row($fetch_courses)){
 echo "<tr>";
 echo "<td>".$fetched[1]."</td>";
 echo "<td><a href='editcourse.php?cid=$fetched[0]'>Edit</td>";
 echo "<td><a href='uploadcontent.php?cid=$fetched[0]'>Add</td>";
 $get_enrols = mysqli_query($con,"SELECT * FROM enroll WHERE course_code=$fetched[0]");
 echo "<td>";
 echo mysqli_num_rows($get_enrols);
 if (mysqli_num_rows($get_enrols) > 0){
  echo "&emsp;<a href='reports.php?cid=$fetched[0]'>View";
 }
 echo "</td>"; 
 echo "</tr>";
}
echo "</table>";
?>
</section>
</main>
```

## 功能说明

- 我们以表格形式显示课程详情，仅显示标题字段。
- 我们提供了创建新课程的链接。
- 为了编辑课程，我们提供了带有参数 `cid = coursecode` 的链接。
- 为了上传内容，我们提供了带有参数 `cid` 的链接。
- 为了查看学习者列表和进度，我们使用了相同的参数 `cid`。

以讲师身份登录，点击仪表盘中的 Courses：

![8-4-1](Images/image00348.jpeg)

我们传递了携带课程代码值的参数 `cid`。接下来的任务是：在 3 个页面中检索该参数——`editcourse.php`、`uploadcontent.php` 和 `reports.php`。

我们现在进行适当的更改：

---

## newcourse.php

我们在此不传递任何参数，但必须指示 PHP 使用 `$usersession` 值作为讲师 ID。

从表单中移除以下行：

```html
<input type='hidden' name='txtinstruct' value='instructor1@onlinecourse.com'>
```

将 PHP 片段修改为：

```php
<?php
include('check.php');
if(isset($_POST['newcourse'])){
 $title = $_POST['txtcourse'];
 $describe = $_POST['txtdesc'];
 $instruct = $usersession;
 $outcome = $_POST['txtoutcome'];
 $eligible = $_POST['txteligible'];
 $insert = mysqli_query($con,"INSERT INTO courses VALUES (NULL,'$title','$instruct','$describe','$outcome','$eligible')");
 if($insert){
 echo "<script>alert('New Course created!');window.location.replace('clist.php');</script>";
 }
 else {
 echo "<script>alert('Sorry, try again!');</script>";
 }
}
?>
```

我们做了三项更改：

- 将 `connect.php` 替换为 `check.php`。
- 将 `$instruct` 变量赋值为 `$usersession`，而非表单提交的值。
- 显示“新课程创建成功”弹窗后，重定向页面至 `clist.php` 以显示课程列表。

请逐项进行更改，以便更好地理解！

---

## editcourse.php

下一个要处理的文件是 `editcourse.php`，需包含参数 `cid`。

### 表单设计调整

在表单设计中，移除以下行：

```html
<input type="hidden" name="txtinstruct" value="<?php echo $instructor;?> ">
```

由于代码片段较大，此处仅给出需替换的部分：

**替换前：**

```php
require('connect.php');  
$course = 1;  
$instructor = 'instructor1@onlinecourse.com';
```

**替换后：**

```php
include('check.php');
$course = '';
$instructor = $usersession;
if(isset($_REQUEST['cid'])){
  $course = $_REQUEST['cid'];
}
```

我们做了 4 项更改：

- 引入 `check.php` 文件。
- 将 `$course` 初始化为空字符串。
- 将请求参数 `cid`（课程代码）的值赋给 `$course` 变量。
- 将 `$usersession` 的值赋给 `$instructor` 变量。

请尝试逐项更改！这将让你更清晰地了解修改内容！

由于讲师已登录，我们将从 `$usersession` 变量检索值，在 `if(isset($_POST['editcourse'])){}` 中移除一行：

```php
$instructor = $_POST['txtinstruct'];
```

同样，再做一项更改。更新后，必须重定向页面至 `clist.php`：

在 PHP 片段中，找到打印课程更新消息的 `if($update)` 块并替换为：

```php
if($update){
  echo "<script>alert('Course Updated!');window.location.replace('clist.php');</script>";
 }
```

我们仅在此处包含重定向代码及弹窗显示。至此，编辑课程功能完成。

---

## uploadcontent.php

下一个要处理的文件是 `uploadcontent.php`，共有 4 项更改。

### Change 1 - 修改代码开头部分

**替换前：**

```php
require('connect.php');  
$course = 1;
```

**替换后：**

```php
include('check.php');
$course = '';
if(isset($_REQUEST['cid'])){
  $course = $_REQUEST['cid'];
}
```

我们做了相同的更改。必须添加返回课程列表的链接。因为在该页面我们添加和删除内容，重定向到课程页面将体验极佳！

### Change 2 - 在主标签内容中添加返回链接

在第一个 `section` 元素内的 `h3` 标签下方添加链接：

```html
<h3> Add Content to Course </h3>
<p><a href='clist.php'>Back to Courses</a></p>
```

这将在添加/移除内容后显式提供返回 Courses 页面的链接。

### Change 3 - 修改课程隐藏字段

在表单设计中修改两项内容，第一项是课程隐藏字段。

**替换前：**

```html
<input type='hidden' name='txtcourse' value='1'>
```

**替换后：**

```html
<input type="hidden" name="txtcourse" value="<?php echo $course; ?>">
```

否则，无论添加什么内容，都会被添加到课程 1。

### Change 4 - 在删除链接中添加额外参数

第二项修改是在删除链接中添加额外参数。

实际上我们通过 `delete` 参数发送内容 ID：

```php
echo "<td><a href='uploadcontent.php?delete=$fetched[0]'>Delete</a></td>";
```

修改该行为：

```php
echo "<td><a href='uploadcontent.php?delete=$fetched[0]&&course=$course'>Delete</a></td>";
```

因为课程值必须在内容的添加/删除过程中保持不变。

相应地，修改 `if(isset($_REQUEST['delete']))` 为：

**替换前：**

```php
if(isset($_REQUEST['delete']))
{
  $id = $_REQUEST['delete'];
  $url = '';
```

**替换后：**

```php
if(isset($_REQUEST['delete']))
{
  $id = $_REQUEST['delete'];
  $course = $_REQUEST['course'];
  $url = '';
```

---

## reports.php

最后要处理的页面是 `reports.php`。

在仪表盘/任意页面使用“另存为”选项创建 `reports.php`。

该文件也需要 PHP 片段的开头代码：

创建 `reports.php` 文件后，确保在文件开头放置以下代码：

```php
<?php
include('check.php');
$course = 0;
if(isset($_REQUEST['cid'])){
  $course = $_REQUEST['cid'];
}
?>
```

你可以直接将此代码保存到文件中。下一节注册课程后，我们可以检查该页面的显示效果！

替换主标签内容为：
