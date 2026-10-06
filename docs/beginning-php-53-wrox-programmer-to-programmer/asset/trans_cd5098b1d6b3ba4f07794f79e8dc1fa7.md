

## 第 9 章：使用 PHP 处理 HTML 表单

### 编写一个简单的表单处理器

在本示例中，你将创建一个简单的用户注册表单，然后编写一个表单处理器脚本，读取从表单发送的字段并显示在页面上。

首先，创建注册表单。将以下 HTML 代码保存为 `registration.html` 并置于你的文档根文件夹下：

```html
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN">
<html xmlns="http://www.w3.org/1999/xhtml" xml="http://www.w3.org/xhtml" lang="en">
<head>
<title>会员表单</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>会员表单</h1>

<p>感谢选择加入 Widget Club。要进行注册，请填写您的详情并点击“发送详情（Send Details）”。</p>

<form action="process_registration.php" method="post">
<div style="width:300px">

<label for="firstName">名</label>
<input type="text" name="firstName" id="firstName" value="" />

<label for="lastName">姓</label>
<input type="text" name="lastName" id="lastName" value="" />

<label for="password">选择密码</label>
<input type="password" name="password1" id="password1" value="" />
<label for="password2">重复输入密码</label>
<input type="password" name="password2" id="password2" value="" />

<label for="gender">您是男性...</label>
<input type="radio" name="gender" id="gender" value="M" />
<label for="genderFemale">还是女性</label>
<input type="radio" name="genderFemale" id="genderFemale" value="F" />

<label for="favoriteWidget">您最喜欢的 widget 是？</label>
<select name="favoriteWidget" id="favoriteWidget" size="1">
<option value="superWidget">SuperWidget</option>
<option value="megaWidget">MegaWidget</option>
<option value="wonderWidget">WonderWidget</option>
</select>

<label for="newsletter">您想接收我们的时事报吗？</label>
<input type="checkbox" name="newsletter" id="newsletter" value="yes" />

<label for="comments">任何意见？</label>
<textarea name="comments" id="comments" rows="4"></textarea>
</div>
</form>
<div style="clear: both;">
  <input type="submit" name="submitButton" id="submitButton" value="发送详情" />
  <input type="reset" name="resetButton" id="resetButton" value="重置表单" style="margin-right: 20px;" />
</div>
</body>
</html>
```

接下来，将以下脚本保存为 `process_registration.php` 并置于你的文档根目录（你放置 `registration.html` 的文件夹），然后在 Web 浏览器中打开 `registration.html` 的 URL。填写表单中的字段，然后点击“发送详情”。如果一切顺利，你将看到看到一个显示你所输入数据的页面。

```html
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml/xhtml-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
  <title>感谢！</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
  <h1>感谢！</h1>
  <p>感谢您的注册。以下是您提交的信息：</p>
  <dl>
    <dt>名</dt><dd><?php echo $_POST['firstName'];?></dd>
    <dt>姓</dt><dd><?php echo $_POST['lastName'];?></dd>
    <dt>密码</dt><dd><?php echo $_POST['password'];?></dd>
    <dt>重复输入的密码</dt><dd><?php echo $_POST['password2'];?></dd>
    <dt>性别</dt><dd><?php echo $_POST['gender'];?></dd>
    <dt>最喜欢的 widget</dt><dd><?php echo $_POST['favoriteWidget'];?></dd>
    <dt>您想接收我们的时事报吗？</dt><dd><?php echo $_POST['newsletter'];?></dd>
    <dt>意见</dt><dd><?php echo $_POST['comments'];?></dd>
  </dl>
</body>
</html>
```

图 9-3 显示了表单刚提交后的示例，图 9-4 显示了发送表单的结果。

![](img/ede05b7b77968b82cbd9a513122fb183_270_0.png)
图 9-3

![](img/ede05b7b77968b82cbd9a513122fb183_270_1.png)
### 感谢

感谢您的注册。以下是您提交的信息。

图 9-4

233

## 第三部分：在实践中使用 PHP

### 工作原理

如你所见，捕获并显示提交的表单数据实际上非常简单。因为表单是使用 post 方法发送的，脚本从 `$_POST` 超全局数组中提取表单字段值，并使用 `echo()` 显示每个字段的值。

```html
<dt>名</dt><php echo $_POST['firstName']?></dt>
<dt>姓</dt><php echo $_POST['lastName']?></dt>
<dt>密码</dt><php echo $_POST['password']?></dt>
<dt>重复输入的密码</dt><php echo $_POST['password2']?></dt>
<dt>性别</dt><php echo $_POST['gender']?></dt>
<dt>最喜欢的 widget</dt><php echo $_POST['favoriteWidget']?></dt>
<dt>您想接收我们的时事报吗？</dt><php echo $_POST['newsletter']?></dt>
<dt>意见</dt><php echo $_POST['comments']?></dt>
```

顺便说一下，`$_REQUEST` 超全局包含了 `$_GET` 和 `$_POST` 的所有元素，你也可以通过以下方式访问字段值：

```html
<dt>名</dt><php echo $_REQUEST['firstName']?></dt>
```

通常情况下，如果知道数据将来自表单的 get 或 post 方法，使用 `$_REQUEST` 可以避免表单字段之间的冲突。

### 安全地处理表单数据

虽然该脚本只是一个示例，并非用于实际世界，但有一些安全问题值得注意。首先，`process_registration.php` 脚本假设用户填写了所有字段。然而，用户经常忘记填写某些字段。当这种情况发生时，数据不会发送到服务器。下表说明了各种表单控件在未填充时的行为：

| 表单控件 | 未填充或未选中时 |
|---|---|
| 输入字段 (input) | 发送字段名，值为空。 |
| 密码字段 (password) | 发送字段名，值为空。 |
| 复选框 (checkbox) | 都不发送任何内容。 |
| 单选按钮 (radio) | 如果未点击，都不发送任何内容。这可能发生在用户按 Enter/Return 提交表单时。然而，如果表单只有一个提交按钮，大多数浏览器仍会发送按钮的字段名和值。 |
| 重置按钮 (reset) | 都不会发送。 |
| 文件字段 (file) | 发送字段名，值为空。 |
| 隐藏字段 (hidden) | 发送字段名，值为空。 |
| 图片字段 (image) | 行为与提交按钮相同。 |
| 推送按钮 (push) | 都不会发送。 |
| 下拉菜单 (pull-down) | 不可能选择无选项，因此总是发送一个值。 |
| 列表框 (list box) | 都不发送。 |
| 多选框 (multi-select) | 都不发送。 |
| 文本区域 (text area) | 发送字段名，值为空。 |

为什么这很重要？嗯，当某个字段没有发送任何内容时，PHP 不会在 `$_POST`、`$_GET` 或 `$_REQUEST` 数组中为该字段创建元素。如果尝试访问该元素，将产生 PHP 通知，内容类似于：

> PHP Note: Undefined index: gender in process_registration.php on line 18

根据你的错误报告设置，此通知可能会出现在服务器错误日志中或浏览器窗口中。这种通知不会干扰脚本的运行；在刚刚所示的案例中，只是向 `echo()` 语句传递了一个空字符串：

```html
<dt>性别</dt><dd><?php echo $_POST["gender"]?></dd>
```

