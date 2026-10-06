

# 第三部分：PHP 实践

然而，编写代码时使其不产生任何通知（notices）通常是一个好主意。这有助于确保应用程序的健壮性和安全性。这意味着在使用提交的表单字段之前，你应该检查其是否存在，而不是假定它一定存在。你可以使用 PHP 函数 `isset()` 或 `array_key_exists()` 来实现此点。

```php
<dt>Gender</dt><php if isset( $_POST['gender'] ) echo $_POST['gender'];?></dd>
```

# 处理多值字段

你之前已经了解到，可以创建发送多个值而非单个值的表单字段。例如，下方的表单字段能够向服务器发送多个值：

```html
<label for="favoriteWidgets">你最喜欢的组件有哪些?</label>
<select name="favoriteWidgets" id="favoriteWidgets" size="3"
multiple="multiple">
  <option value="superWidget">The SuperWidget</option>
  <option value="megaWidget">The MegaWidget</option>
  <option value="wonderWidget">The WonderWidget</option>
</select>
```

```html
<label for="newsletterWidgetTimes">你是否想接收我们的
<input type="checkbox" name="newsletter" id="newsletterWidgetTimes"
value="widgetTimes" />
<label for="newsletterFunWithWidgets">你是否想接收我们的
Fun with Widgets'</label>
<input type="checkbox" name="newsletter" id="newsletterFunWithWidgets"
value="funWithWidgets" />
```

第一个表单字段是一个列表框，允许用户选择一个或多个（或不选）选项。第二个两个表单字段是具有相同名称（newsletter）但不同值（widgetTimes 和 funWithWidgets）的复选框。如果用户勾选了这两项，那么值 `widgetTimes` 和 `funWithWidgets` 将被发送到服务器的字段名 newsletter 中。

那么，如何在 PHP 脚本中处理多值字段呢？技巧是在是在 HTML 表单的字段名后添加方括号 `[]`。然后，当 PHP 引擎看到带有方括号的提交表单字段时，它会在 `$_GET` 或 `$_POST` 超全局数组中创建一个嵌套的值数组，而不是单个值。你可以从该嵌套数组中提取出单独的值。你可以如下创建一个多选择控件：

```html
<select name="favoriteWidgets[]" id="favoriteWidgets" size="3"
multiple="multiple" ... </select>
```

然后你可以按照如下方式获取这些字段值：

```php
$favoriteWidgetValuesArray = $_GET["favoriteWidgets"]; // 如果使用 get 方法
$favoriteWidgetValuesArray = $_POST["favoriteWidgets"]; // 如果使用 post 方法
```

# 第 9 章：使用 PHP 处理 HTML 表单

# 带有多值字段的注册表单

这里是你之前创建的注册表单和处理器，但此表单包含一个用于选择“收藏组件”的多选择列表框，以及两个允许用户订阅不同时通讯的复选框。表单处理器会处理这些多值字段，并在网页中显示它们的值。

将以下表单保存为 `registration_multi.html` 并于你的文档根目录中：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/DTD/html1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <title>会员表单</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
  <h1>会员表单</h1>
  <p>感谢选择加入 Widget Club。要注册，请填写您的详情并点击 Details。</p>

  <form action="process_registration_multi.php" method="post">
    <div style="width:300px;">
      <label for="firstName">姓</label>
      <input type="text" name="firstName" id="firstName" value="" />
      <label for="lastName">姓</label>
      <input type="text" name="lastName" id="lastName" value="" />
      <label for="password1">选择密码</label>
      <input type="password" name="password1" id="password1" value="" />
      <label for="password2">再次输入密码</label>
      <input type="password" name="password2" id="password2" value="" />
      <label for="genderMale">你是男性吗...</label>
      <input type="radio" name="gender" id="genderMale" value="M" />
      <label for="genderFemale">还是女性吗...</label>
      <input type="radio" name="gender" id="genderFemale" value="F" />
      <label for="favoriteWidgets">你最喜欢的组件有哪些?</label>
      <select name="favoriteWidgets[]" id="favoriteWidgets" size="3"
      multiple="multiple">
        <option value="superWidget">The SuperWidget</option>
        <option value="megaWidget">The MegaWidget</option>
        <option value="wonderWidget">The WonderWidget</option>
      </select>
      <label for="newsletterTimes">你是否想接收我们的 'Widget Times' 通讯?</label>
      <input type="checkbox" name="newsletter" id="newsletter" value="" />

      <label for="newsletterFunWithWidgets">你是否想接收我们的
      'Fun with Widgets'? 通讯?</label>
      <input type="checkbox" name="newsletter[]" id="newsletterFunWithWidgets"
      value="funWithWidgets" />

      <label for="comments">任何意见?</label>
      <textarea name="comments" id="comments" row="4" cols="50">
      </textarea>

      <div style="color: both;">
        <input type="submit" name="submitButton" id="submitButton"
        value="Send Details" />
        <input type="reset" name="resetButton" id="resetButton"
        value="Reset Form" style="margin-right: 20px;" />
      </div>
    </div>
  </form>
</body>
</html>
```

现在将以下脚本保存为 `process_registration_multi.php` 并于你的文档文件夹中：

```php
<!DOCTYPE PUBLIC "-//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/html1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <title>感谢</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
  <h1>感谢</h1>
  <p>感谢注册。以下是您提交的信息：</p>

  <?php
  $favoriteWidgets = "";
  $newsletters = "";

  if (isset($_POST["favoriteWidgets"])) {
      foreach ($_POST["favoriteWidgets"] as $widget) {
          $favoriteWidgets .= $widget . ", ";
      }
  }
  if (isset($_POST["newsletter"])) {
      foreach ($_POST["newsletter"] as $newsletter) {
          $newsletters .= $newsletter . ", ";
      }
  }

  $favoriteWidgets = preg_replace("/, *$/", "", $favoriteWidgets);
  $newsletters = preg_replace("/, *$/", "", $newsletters);
  ?>

  <dl>
    <dt>姓</dt><php echo $_POST["firstName"];?></dd>
    <dt>姓</dt><php echo $_POST["lastName"];?></dd>
    <dt>密码</dt><php echo $_POST["password1"];?></dd>
    <dt>再次输入密码</dt><php echo $_POST["password2"];?></dd>
    <dt>性别</dt><php echo $_POST["gender"];?></dd>
    <dt>收藏组件</dt><php echo $favoriteWidgets;?></dd>
    <dt>你是否想接收以下通讯?</dt><php echo $newsletters;?></dd>
    <dt>意见</dt><php echo $_POST["comments"];?></dd>
  </dl>
</body>
</html>
```

