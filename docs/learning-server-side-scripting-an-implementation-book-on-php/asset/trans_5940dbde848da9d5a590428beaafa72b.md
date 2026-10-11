
无论是第一个查询还是这个查询将会被执行，while 循环的工作方式与之前相同。

它将显示所有课程或仅显示包含该模式的选定课程。

## 进入执行部分

1. 访问 `http://localhost/onlinecourse/courses.php` 并提供搜索词：`feature`

![7-5-1](Images/image00330.jpeg)

从上图可以看到，单词 feature 出现在第二门课程的描述中。因此，点击搜索按钮时将显示一门课程。

2. 点击搜索按钮

![7-5-2](Images/image00331.jpeg)

所以，我们的 PHP 代码和 SQL 查询工作正常！

3. 点击课程 2 链接，显示课程详情。

![7-5-3](Images/image00332.jpeg)

你可以在 URL 中找到参数 `search=2`，因为我们点击了第二门课程。

我们已为应用程序提供了搜索课程和获取课程详情功能。

你对 SQL 语法越熟悉，将这些功能应用到应用程序中就越容易。

---

### 7.7 删除数据

---

目前在应用程序中，我们不提供删除用户账户、删除课程的功能。但我们将为应用程序提供删除内容功能。

如果我们提供内容编辑功能，则必须删除上传的文件或更改内容标题。我们不这样做，而是给讲师一个选项来删除内容（包括标题和文件）并上传新内容。

我们将要处理的页面显然是 `uploadcontent.php`。

#### 本节将做什么？

*   我们将首先在该页面检索上传的内容
*   我们将提供删除链接以删除特定内容
*   如果尝试删除，我们必须同时删除数据库条目和上传的文件

好的，让我们回到文件中。

#### 检索上传的内容：

在页面顶部，require 语句下方添加以下代码：

```
require('connect.php');
$course = 1;
```

`$course` 变量将保存从应用程序中上一页传递的参数。目前，我们将其初始化为课程代码 1（第一门课程）。

在 main 标签元素中，section 元素结束后，我们将包含另一个 section。

添加以下代码：

```
<section>
<h3> Uploaded Contents </h3>
<?php
$fetch_contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
$fetch_num = mysqli_num_rows($fetch_contents);
if($fetch_num == 0){
 echo "No contents uploaded in this course!";
}
else{
 echo "<table style='margin: 0 10px; text-align:left;'>";
 echo "<tr>";
 echo "<th style='width: 50%'> Content Title </th>";
 echo "<th style='width: 40%'> Content File Path </th>";
 echo "<th style='width: 10%'> Delete Content </th>";
 echo "</tr>";
} 
while($fetched = mysqli_fetch_row($fetch_contents)){
 echo "<tr>";
 echo "<td>".$fetched[1]."</td>";
 echo "<td>".$fetched[3]."</td>";
 echo "<td><a href='uploadcontent.php?delete=$fetched[0]'>Delete</a></td>";
 echo "</tr>";
}
echo "</table>";
?>
</section>
```

这次我们以表格形式显示记录。我们在第三列放置了一个带有 delete 参数变量的链接。delete 变量将保存内容 ID 的值。

让我解释一下代码片段的新部分：

```
$fetch_contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
$fetch_num = mysqli_num_rows($fetch_contents);
if($fetch_num == 0){
 echo "No contents uploaded in this course!";
}
else{
 echo "<table style='margin: 0 10px; text-align:left;'>";
 echo "<tr>";
 echo "<th style='width: 50%'> Content Title </th>";
 echo "<th style='width: 40%'> Content File Path </th>";
 echo "<th style='width: 10%'> Delete Content </th>";
 echo "</tr>";
} 
```

`mysqli_num_rows()` 将获取查询检索到的记录数。如果记录数为零，我们将显示一条消息，表明该课程没有上传内容。如果至少有一条记录，将从 else 块显示表格格式。

执行 `http://localhost/onlinecourse/uploadcontent.php`

![7-7-1](Images/image00333.jpeg)

现在，我们将进行下一部分工作——删除过程！

#### 删除内容：

我们将在现有 PHP 代码片段的开头添加几行代码。

不要替换任何内容，必须在 `if(isset($_POST['upload'])) {}` 块之前添加此代码

```
require('connect.php');
$course = 1;
if(isset($_REQUEST['delete']))
{
  $id = $_REQUEST['delete'];
  $url = '';
  $getpath = mysqli_query($con,"SELECT * FROM contents WHERE content_id = $id");
  if($path = mysqli_fetch_row($getpath)){
    $url = $path[3];
  }
  $delete1 = mysqli_query($con, "DELETE FROM contents WHERE content_id = $id");
  $delete2 = unlink($url);
  if($delete1 and $delete2){
    echo "<script>alert('Content deleted!');</script>";
  }
}
```

让我解释这部分：

我们首先使用 `content_id` 获取内容的路径

```
$delete1 = mysqli_query($con, "DELETE FROM contents WHERE content_id = $id");
```

我们从数据库中删除内容记录

```
$delete2 = unlink($url);
```

我们从服务器（`onlinecoourse/uploads` 文件夹）删除文件。`$url` 保存文件的路径。

当 `$delete1` 和 `$delete2` 都成功时，我们通过弹窗向用户显示一条消息。

执行：`http://localhost/onlinecourse/uploadcontent.php`

让我们上传一个名为 `file3.ppt` 的新文件

![7-7-2](Images/image00334.jpeg)

![7-7-3](Images/image00335.jpeg)

让我们也检查一下 uploads 文件夹：

![7-7-4](Images/image00336.jpeg)

现在，我们将删除名为 Content 3 的内容，点击 Content 3 所在行的 Delete 链接。

![7-7-5](Images/image00337.jpeg)

![7-7-7](Images/image00338.jpeg)

让我们再次检查 uploads 文件夹：

![7-7-6](Images/image00339.jpeg)

希望你喜欢这种通过应用程序操作数据的方法。

至此，本章结束！下一章将把所有这些部分整合成一个连贯且可工作的应用程序。

---

# 第 8 章：使用应用程序

---

*   [8.1 注册和登录](#part0050.xhtml)
*   [8.2 用户仪表板](#part0051.xhtml)
*   [8.3 修改个人资料](#part0052.xhtml)
*   [8.4 管理课程和内容](#part0053.xhtml)
*   [8.5 报名和课程访问](#part0054.xhtml)
*   [8.6 主页](#part0055.xhtml)
*   [8.7 应用程序演示](#part0056.xhtml)

---

### 8.1 注册和登录

---

使用任何应用程序的第一步是注册。创建账户后，你将能够登录。每当你想要访问时，都需要登录。

本节将指导你完成注册和登录流程。

我们已经完成了用户详细信息的注册。我们尚未完成登录表单。让我为你描述一下流程：

注册 -> 登录 -> 用户仪表板

完成注册后，你将被带到登录页面。当你成功登录时，你将被带到相应的用户仪表板页面。仪表板是你可以从中访问用户相关页面的地方。我们显然会有 2 种类型的仪表板：一种供讲师使用，另一种供学习者使用。

我们需要 3 个页面：

*   `register.php`
*   `login.php`
*   `dashboard.php`

我们必须从注册页面重定向到登录页面，同样从登录页面重定向到仪表板页面。在登录页面，我们将创建一个指向注册页面的链接。我们将逐个完成。在此之前，先创建另外 2 个页面 `login.php` 和 `dashboard.php`。

让我再次提醒你，要么创建文件并复制内容，要么使用“另存为”选项来创建这 2 个文件。只有创建文件后，我们才能从 `register.php` 重定向到 `login.php`。如果没有名为 `login.php` 的页面，重定向时将会遇到 404 页面未找到错误。

