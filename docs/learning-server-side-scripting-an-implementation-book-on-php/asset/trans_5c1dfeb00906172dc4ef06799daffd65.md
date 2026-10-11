

![6-4-6](Images/image00283.jpeg)

7. 就这样，第一张表准备好了！

**表-1：** `instructors`

![6-4-7](Images/image00284.jpeg)

你可以继续从此界面创建第二张表，或者通过点击左侧面板 `onlinecourse` 下的 **新建** 来创建。

8. 点击表名 `instructors`：

![6-4-8](Images/image00285.jpeg)

点击“浏览”标签旁边的 **结构** 标签

![6-4-9](Images/image00286.jpeg)

这将显示表的完整结构。因此，从这里开始，我将分享每个表的输入字段截图和上述结构。请务必遵循步骤，成功创建表！

**表-2：** `courses`

当你在左侧面板 `onlinecourse` 数据库下点击 **新建** 时，将直接进入此页面：

![6-4-10](Images/image00287.jpeg)

你可以添加列数并点击 **执行**（如标记所示）来增加列。

*   当你将某字段标记为 `A_I`（自动增长）时，它会自动将该字段设为主键。
*   当你在 **索引** 列将某字段标记为 **唯一** 时，会显示一个类似于主键的弹窗。只需像处理主键弹窗那样进行相同操作即可。

![6-4-11](Images/image00288.jpeg)

当你保存表时，它会自动带你进入结构标签页，如下所示：

![6-4-12-table2](Images/image00289.jpeg)

**表-3：** `contents`

*   我们将只在数据库中存储内容的路径。内容文件将单独存储。
*   这里无需显式提及外键。当我们在此表中插入记录时，我们的应用程序会处理该操作。

![6-4-13](Images/image00290.jpeg)

![6-4-14-table3](Images/image00291.jpeg)

**表-4：** `learners`

![6-4-15](Images/image00292.jpeg)

![6-4-16-table4](Images/image00293.jpeg)

**表-5：** `enroll`

*   对于此表，我们将为 `learn_start` 字段包含一个名为 `CURRENT_TIMESTAMP` 的默认值，这将在插入新记录时自动插入当前日期。
*   当你在服务器上执行此操作时，请检查服务器时区，因为 MySQL 会以服务器时区插入日期/时间！

![6-4-17](Images/image00294.jpeg)

![6-4-18-table5](Images/image00295.jpeg)

**表-6：** `record`

此表没有主键。如果你愿意，可以创建一个单独的字段，但在插入记录时要小心，你必须包含三个值。我在这里避免使用主键，因为当学习者不断完成内容时，会插入一条记录。在检索时，我们会通过 `learn_mail` 字段和 `content_id` 字段提取详细信息，以了解哪位学习者完成了什么内容。

![6-4-19](Images/image00296.jpeg)

![6-4-20-table6](Images/image00297.jpeg)

由于未定义主键，因此未创建索引！

**表-7：** `userlogin`

![6-4-21](Images/image00298.jpeg)

我们将存储密码的哈希值，因此我们给该字段分配了更大的长度。

![6-4-22-table7](Images/image00299.jpeg)

最后，点击左侧面板中的 `onlinecourse`：

![6-4-23-alltables](Images/image00300.jpeg)

因此，应用程序所需的所有表均已创建！

---

### 6.5 Web 应用程序模板

---

**什么是模板？**

它是一个现成的网页，包含布局、字体、图像和其他待包含的元素。当你准备好模板后，可以确保整个应用程序（所有网页）具有统一的设计。

**为什么要使用模板？**

很简单，它为所有页面提供统一的设计！

**你应该将此模板放在哪里？**

请记住，我们正在使用 `xampp` 服务器。

希望你已经在 `C:/xampp/htdocs` 中创建了一个名为 **onlinecourse** 的文件夹。

*   如果你尚未创建，请在 `C:/xampp/htdocs` 路径下创建一个名为 `onlinecourse` 的文件夹。这是我们的项目文件夹。
*   在 `onlinecourse` 文件夹内创建一个新文件 `index.php`
*   在 `onlinecourse` 文件夹内创建一个名为 `css` 的新文件夹
*   在 `css` 文件夹内创建一个新文件 `style.css`

**包含的文件：**

*   `index.php`
*   `css` 文件夹 - `style.css`

![1-1-0](Images/image00301.jpeg)

**初始代码：**

你可以将下面的代码片段放入 `index.php` 文件中

```html
<!-- index.php -->
<!DOCTYPE html>
<html>
<head>
<title> Template </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>

<main>
<section>
<h3>Welcome to Online Course System!</h3>
<p style='text-align:left;'>In this web application, we will develop user-friendly application to enroll to courses. We primarily have 2 major users for this application: </p>
<ul  style='text-align:left;'>
<li>Instructor - the one who develops course materials </li>
<li>Learner - the one who studies those developed course materials </li>
</ul>
<p style='text-align:left;'>
The instructors develop course materials and upload the same in this website. Once the course is published, they appear in the search list. The learners browse through the course list and sneek into every detail. nce they are 
comfortable with a course, they enroll into it. Once they enroll, they can view the course materials. A progress track will be there to specify how far they have completed the course. When progress reaches 100%, it marks the course to be completed.
</p>
<p>
For this application, we keep all courses free of cost!
</p>
</section>
<article class="artclass">
<div>
<h3>Courses with enrollments</h3>
<p>Course Name 1      Enrollment Nos</p> 
<p>Course Name 2      Enrollment Nos</p> 
<p>Course Name 3      Enrollment Nos</p> 
</div>
<div>
<h3>Instructors List</h3>
<p>Instructor 1</p> 
<p>Instructor 2</p> 
<p>Instructor 3</p> 
</div>
</article>
</main>

<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

你可以将下面的代码片段放入 `style.css` 文件中

