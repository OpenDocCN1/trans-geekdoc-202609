
#### 代码逻辑说明

我们定义了 `$titleval`、`$describeval`、`$outcomeval`、`$eligibleval` 变量来保存从数据库查询到的值，这些值用于填充表单中的 HTML 元素。

```php
if (isset($_POST['editcourse'])) {
    $title = $_POST['txtcourse'];
    $describe = $_POST['txtdesc'];
    $outcome = $_POST['txtoutcome'];
    $eligible = $_POST['txteligible'];
}
```

这 4 个变量用于保存更新时通过表单提交的值。

```php
if ($title != $titleval) {
    $update1 = mysqli_query($con, "UPDATE courses SET course_title = '$title' WHERE course_code = $course");
    $titleval = $title;
}

if ($describe != $describeval) {
    $update2 = mysqli_query($con, "UPDATE courses SET course_description = '$describe' WHERE course_code = $course");
    $describeval = $describe;
}

if ($outcome != $outcomeval) {
    $update3 = mysqli_query($con, "UPDATE courses SET course_outcome = '$outcome' WHERE course_code = $course");
    $outcomeval = $outcome;
}

if ($eligible != $eligibleval) {
    $update4 = mysqli_query($con, "UPDATE courses SET course_eligible = '$eligible' WHERE course_code = $course");
    $eligibleval = $eligible;
}
```

我们设置了 4 个条件判断：

*   如果数据库中的课程标题值与表单字段值不匹配，则对课程标题字段执行更新操作
*   如果数据库中的课程描述值与表单字段值不匹配，则对课程描述字段执行更新操作
*   如果数据库中的课程成果值与表单字段值不匹配，则对课程成果字段执行更新操作
*   如果数据库中的课程资格值与表单字段值不匹配，则对课程资格字段执行更新操作
*   我们将提交的字段值赋给 `$titleval`、`$describeval`、`$outcomeval`、`$eligibleval`，因为这些变量将保存字段中更新后的值。

#### 为什么要逐个字段检查而不是使用 4 条更新语句？

每一次数据库更新操作都是昂贵的。这意味着你需要检索字段、执行编辑并将其更新回数据库。为了最小化数据库复杂度并优化服务器资源，我们逐个字段进行检查。实际上，我们从不每次都修改所有字段。我们仅在字段需要修改时才更新。因此，作为开发人员遵循这种方法是一种良好的实践。

```php
if ($update) {
    echo "<script>alert('Course Updated!');</script>";
}
```

我们定义了一个布尔变量 `$update` 并初始化为 `false`。每当发生更新操作时，它会变为 `true`。如果为 `true`，则提示用户已执行更新。

显示错误相关消息并非总是必要。在开发阶段错误消息可能有帮助，但上线（实时环境）时，除非必要，否则尽量减少它们是良好的推荐做法。

#### 操作演示

你已经在浏览器中打开了表单。

修改最后一个字段——资格：

> Anyone can enroll to this course, You should know English language to learn this

![7-6-2](img/image00328.jpeg)

点击 **Update Course** 按钮。

![7-6-3](img/image00329.jpeg)

当你按下确定后，页面将显示更新后的值。

至此，本节结束！下一节我们将学习删除数据。

---

#### 7.5 检索数据 - II

---

现在我们将学习如何为课程页面提供搜索功能。

##### 搜索课程

正如讨论的那样，我们将提供一个搜索框和一个提交按钮。我们将使用 SQL 运算符来筛选结果。

我们将继续操作 `courses.php` 文件。

*   在 `<main>` 标签内部，`<h3>` 标签下方，我们将放置一个包含搜索框的 `<div>`
*   我们将放置一个按钮以启用搜索
*   添加相应的 PHP 代码片段

用以下代码替换 `<main>` 标签元素：

```html
<main>
<?php
$pattern = '';
$patternexist = false;

if (isset($_POST['searchcourse'])) {
    $pattern = $_POST['txtsearch'];
    $patternexist = true;
}
?>

<section>
<h3>Courses</h3>

<div>
<form method="post" name="frmsearch">
<p><input type="search" name="txtsearch" size="60" value="<?php if ($patternexist) { echo $pattern; } ?>"></p>
<p><input type="submit" name="searchcourse" class="frmbtn" value="Search Courses"></p>
</form>
</div>

<?php
require('connect.php');

$query = "SELECT * FROM courses";

if ($patternexist) {
    $query = "SELECT * FROM courses WHERE course_title LIKE '%$pattern%' OR course_description LIKE '%$pattern%'";
}

$select_courses = mysqli_query($con, $query);

while ($selected = mysqli_fetch_row($select_courses)) {
    echo "<div class='cl'>";
    echo "<h4><a href='details.php?search=$selected[0]'>" . $selected[1] . "<a/></h4>";
    echo "<p>" . $selected[3] . "</p>";
    echo "</div>";
}
?>
</section>
</main>
```

###### 新增代码段解释

```php
<?php
$pattern = '';
$patternexist = false;

if (isset($_POST['searchcourse'])) {
    $pattern = $_POST['txtsearch'];
    $patternexist = true;
}
?>
```

我们初始化两个变量：`$pattern` 用于存储搜索短语，一个布尔值 `$patternexist` 用于检查搜索短语是否存在。我们对搜索按钮使用 `isset()` 检查按钮是否被点击。如果被点击，将短语赋值给变量 `$pattern` 并将 `$patternexist` 设为 `true`，表示存在搜索短语。

```html
<div>
<form method="post" name="frmsearch">
<p><input type="search" name="txtsearch" size="60" value="<?php if ($patternexist) { echo $pattern; } ?>"></p>
<p><input type="submit" name="searchcourse" class="frmbtn" value="Search Courses"></p>
</form>
</div>
```

这是搜索框的设计部分。`value` 属性中包含一段 PHP 代码。该部分逻辑为：如果搜索短语存在（`$patternexist = true`），则在搜索框中显示该短语。如果不存在搜索短语，则搜索框为空。

```php
$query = "SELECT * FROM courses";

if ($patternexist) {
    $query = "SELECT * FROM courses WHERE course_title LIKE '%$pattern%' OR course_description LIKE '%$pattern%'";
}
```

该查询用于从 `courses` 表中选择所有记录。

*   如果搜索框中存在搜索模式，我们使用 SQL 语法中的 `LIKE` 运算符，选择 `course_title` 或 `course_description` 字段包含搜索短语的记录。

无论是第一个查询还是这个查询将会被执行，`while` 循环的工作方式与之前相同。它将显示所有课程或仅显示包含该模式的选定课程。

##### 进入执行部分

1. 访问 `http://localhost/onlinecourse/courses.php` 并提供搜索词：`feature`

![7-5-1](img/image00330.jpeg)

从上图可以看到，单词 feature 出现在第二门课程的描述中。因此，点击搜索按钮时将显示一门课程。

2. 点击搜索按钮

![7-5-2](img/image00331.jpeg)

所以，我们的 PHP 代码和 SQL 查询工作正常！

3. 点击课程 2 链接，显示课程详情。

![7-5-3](img/image00332.jpeg)

你可以在 URL 中找到参数 `search=2`，因为我们点击了第二门课程。

我们已为应用程序提供了搜索课程和获取课程详情功能。

你对 SQL 语法越熟悉，将这些功能应用到应用程序中就越容易。

---

#### 7.7 删除数据

---

目前在应用程序中，我们不提供删除用户账户、删除课程的功能。但我们将为应用程序提供删除内容功能。

如果我们提供内容编辑功能，则必须删除上传的文件或更改内容标题。我们不这样做，而是给讲师一个选项来删除内容（包括标题和文件）并上传新内容。

我们将要处理的页面显然是 `uploadcontent.php`。

##### 本节将做什么？

*   我们将首先在该页面检索上传的内容
*   我们将提供删除链接以删除特定内容
*   如果尝试删除，我们必须同时删除数据库条目和上传的文件

好的，让我们回到文件中。

#### 检索上传的内容

在页面顶部，`require` 语句下方添加以下代码：

```php
require('connect.php');
$course = 1;
```

`$course` 变量将保存从应用程序中上一页传递的参数。目前，我们将其初始化为课程代码 1（第一门课程）。

在 `main` 标签元素中，`section` 元素结束后，我们将包含另一个 `section`。

添加以下代码：

```php
<section>
<h3> Uploaded Contents </h3>
<?php
$fetch_contents = mysqli_query($con, "SELECT * FROM contents WHERE course_code = $course");
$fetch_num = mysqli_num_rows($fetch_contents);

if ($fetch_num == 0) {
    echo "No contents uploaded in this course!";
} else {
    echo "<table style='margin: 0 10px; text-align:left;'>";
    echo "<tr>";
    echo "<th style='width: 50%'> Content Title </th>";
    echo "<th style='width: 40%'> Content File Path </th>";
    echo "<th style='width: 10%'> Delete Content </th>";
    echo "</tr>";
}

while ($fetched = mysqli_fetch_row($fetch_contents)) {
    echo "<tr>";
    echo "<td>" . $fetched[1] . "</td>";
    echo "<td>" . $fetched[3] . "</td>";
    echo "<td><a href='uploadcontent.php?delete=$fetched[0]'>Delete</a></td>";
    echo "</tr>";
}
echo "</table>";
?>
</section>
```

这次我们以表格形式显示记录。我们在第三列放置了一个带有 `delete` 参数变量的链接。`delete` 变量将保存内容 ID 的值。

让我解释一下代码片段的新部分：

```php
$fetch_contents = mysqli_query($con, "SELECT * FROM contents WHERE course_code = $course");
$fetch_num = mysqli_num_rows($fetch_contents);

if ($fetch_num == 0) {
    echo "No contents uploaded in this course!";
} else {
    echo "<table style='margin: 0 10px; text-align:left;'>";
    echo "<tr>";
    echo "<th style='width: 50%'> Content Title </th>";
    echo "<th style='width: 40%'> Content File Path </th>";
    echo "<th style='width: 10%'> Delete Content </th>";
    echo "</tr>";
}
```

`mysqli_num_rows()` 将获取查询检索到的记录数。如果记录数为零，我们将显示一条消息，表明该课程没有上传内容。如果至少有一条记录，将从 `else` 块显示表格格式。

执行 `http://localhost/onlinecourse/uploadcontent.php`

![7-7-1](img/image00333.jpeg)

现在，我们将进行下一部分工作——删除过程！

#### 删除内容

我们将在现有 PHP 代码片段的开头添加几行代码。

不要替换任何内容，必须在 `if(isset($_POST['upload'])) {}` 块之前添加此代码：

```php
require('connect.php');
$course = 1;

if (isset($_REQUEST['delete'])) {
    $id = $_REQUEST['delete'];
    $url = '';
    $getpath = mysqli_query($con, "SELECT * FROM contents WHERE content_id = $id");
    if ($path = mysqli_fetch_row($getpath)) {
        $url = $path[3];
    }
    $delete1 = mysqli_query($con, "DELETE FROM contents WHERE content_id = $id");
```
