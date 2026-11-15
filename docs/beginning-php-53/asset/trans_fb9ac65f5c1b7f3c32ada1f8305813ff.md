

```php
function displayForm( $missingFields ) {
?>
<h1>Membership Form</h1>

<?php if ( $missingFields ) { ?>
<p class="error">There were some problems with the form you submitted.
Please complete the fields highlighted below and click Send Details to
resend the form.</p>
<?php } else { ?>
<p>Thanks for choosing to join The Widget Club. To register, please
fill in your details below and click Send Details. Fields marked with an
asterisk (*) are required.</p>
<?php } ?>

<form action="registration.php" method="post">
<div style="width: 30em;">

<label for="firstName"<?php validateField( "firstName",
$missingFields ) ?>>First name *</label>
<input type="text" name="firstName" id="firstName"
value="<?php setValue( "firstName" ) ?>" />

<label for="lastName"<?php validateField( "lastName",
$missingFields ) ?>>Last name *</label>
<input type="text" name="lastName" id="lastName" value=
"<?php setValue( "lastName" ) ?>" />

<label for="password1"<?php if ( $missingFields ) echo
' class="error" ?>>>Choose a password *</label>
<input type="password" name="password1" id="password1" value="" />
<label for="password2"<?php if ( $missingFields ) echo
' class="error" ?>>>Retype password *</label>
<input type="password" name="password2" id="password2" value="" />

<label><?php validateField( "gender", $missingFields ) ?>>Your
gender: *</label>
<label for="genderMale">Male</label>
<input type="radio" name="gender" id="genderMale" value=
"M"<?php setChecked( "gender", "M" )?> />
<label for="genderFemale">Female</label>
<input type="radio" name="gender" id="genderFemale" value=
"F"<?php setChecked( "gender", "F" )?> />

<label for="favoriteWidget">What's your favorite widget? </label>
<select name="favoriteWidget" id="favoriteWidget" size="1">
<option value="superWidget"<?php setSelected( "favoriteWidget",
"superWidget" ) ?>>The SuperWidget</option>
```

```php
<option value="megaWidget"<?php setSelected( "favoriteWidget",
"megaWidget" ) ?>>The MegaWidget</option>
<option value="wonderWidget"<?php setSelected( "favoriteWidget",
"wonderWidget" ) ?>>The WonderWidget</option>
</select>

<label for="newsletter">Do you want to receive our newsletter?
</label>
<input type="checkbox" name="newsletter" id="newsletter" value="yes"
<?php setChecked( "newsletter", "yes" ) ?> />

<label for="comments">Any comments?</label>
<textarea name="comments" id="comments" rows="4" cols="50"><?php
setValue( "comments" ) ?></textarea>

<div style="clear: both;">
<input type="submit" name="submitButton" id="submitButton" value=
"Send Details" />
<input type="reset" name="resetButton" id="resetButton"
value="Reset Form" style="margin-right: 20px;" />
</div>

</div>
</form>
<?php
}
?>
function displayThanks( ) {
?>
<h1>Thank You</h1>
<p>Thank you, your application has been received.</p>
<?php
}
?>
</body>
</html>
```

在 Web 浏览器中打开脚本的 URL。你将看到一个空白的注册表单。尝试点击“发送详细信息”提交一个空表单。你应该会看到一条错误消息，其中突出显示了缺少的必填字段。如果你填写了一些值并重新提交，脚本会继续检查你是否填写了必填字段。如果没有，它会重新显示表单，包括你已经输入的任何数据，并突出显示缺少的字段，如图 9-7 所示。

最后，尝试填写所有必填字段并再次点击“发送详细信息”。这一次，你应该会看到感谢消息。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_283_0.png)

图 9-7

## 工作原理

脚本以标准的 XHTML 页面页头开始。它包含一个用于红色错误框的额外 CSS 类：

```html
<style type="text/css">
.error { background: #d33; color: white; padding: 0.2em; }
</style>
```

接下来，脚本检查表单是否已提交。它通过查找 submitButton 字段是否存在来实现。如果存在，表示已点击“发送详细信息”按钮并且表单已收到，脚本会调用 processForm() 函数来处理表单数据。但是，如果表单尚未显示，它会调用 displayForm() 来显示空白表单，并传入一个空数组（稍后将详细说明）：

```php
if ( isset( $_POST["submitButton"] ) ) {
    processForm();
} else {
    displayForm( array() );
}
```

接下来，脚本定义了一些辅助函数。validateField() 在表单中使用，如果必填字段未填写，则在表单字段标签周围显示一个红色错误框。它接收一个字段名，以及所有未填写的必填字段列表。如果字段名在列表中，它将显示错误框的标记：

```php
function validateField( $fieldName, $missingFields ) {
    if ( in_array( $fieldName, $missingFields ) ) {
        echo ' class="error"';
    }
}
```

setValue() 用于预填表单中的文本输入字段和文本区域字段。它期望接收一个字段名。然后它在 $_POST 超全局数组中查找该字段名，如果找到，则输出该字段的值：

```php
function setValue( $fieldName ) {
    if ( isset( $_POST[$fieldName] ) ) {
        echo $_POST[$fieldName];
    }
}
```

setChecked() 是通过将 checked 属性插入元素标签来预选复选框和单选按钮的。同样，setSelected() 是通过 selected 属性在下拉列表中预选一个选项的。这两个函数都会在 $_POST 数组中查找提供的字段名，如果找到该字段且其值与提供的字段值匹配，则预选该控件：

```php
function setChecked( $fieldName, $fieldValue ) {
    if ( isset( $_POST[$fieldName] ) && $_POST[$fieldName] == $fieldValue ) {
        echo ' checked="checked"';
    }
}
```

```php
function setSelected( $fieldName, $fieldValue ) {
    if ( isset( $_POST[$fieldName] ) && $_POST[$fieldName] == $fieldValue ) {
        echo ' selected="selected"';
    }
}
```

接下来是表单处理函数 processForm()。它设置一个必填字段名数组，并初始化一个数组来存放未填写的必填字段：

```php
function processForm() {
    $requiredFields = array( "firstName", "lastName", "password1", "password2",
                             "gender" );
    $missingFields = array();
}
```

现在，函数会遍历必填字段名，并在 `$_POST` 数组中查找每个字段名。如果字段名不存在，或存在但其值为空，则将该字段名添加到 `$missingFields` 数组中：

```php
foreach ( $requiredFields as $requiredField ) {
    if ( !isset( $_POST[$requiredField] ) or !$_POST[$requiredField] ) {
        $missingFields[] = $requiredField;
    }
}
```

如果发现了缺少的字段，函数会调用 `displayForm()` 来重新显示表单，并传入缺少的字段名数组，以便 `displayForm()` 可以突出显示相应的字段。否则，会调用 `displayThanks()` 来感谢用户：

```php
if ( $missingFields ) {
    displayForm( $missingFields );
} else {
    displayThanks();
}
```

`displayForm()` 函数本身向用户显示 HTML 表单。它期望接收一个包含所有缺少必填字段名的数组。如果该数组为空，则表单大概是第一次显示，因此 `displayForm()` 显示欢迎消息。但是，如果数组中有元素，则是因为有错误而重新显示表单，因此函数会显示相应的错误消息：

```php
function displayForm( $missingFields ) {
?>
<h1>Membership Form</h1>

<?php if ( $missingFields ) { ?>
<p class="error">There were some problems with the form you submitted.
Please complete the fields highlighted below and click Send Details to resend
the form.</p>
<?php } else { ?>
<p>Thanks for choosing to join The Widget Club. To register, please fill
in your details below and click Send Details. Fields marked with an asterisk
(*) are required.</p>
<?php } ?>
```

接下来，显示表单本身。表单使用 post 方法，其 `action` 属性指回脚本的 URL：

```html
<form action="registration.php" method="post">
```

然后，使用 HTML 标记创建每个表单控件。请注意，`validateField()`、`setValue()`、`setChecked()` 和 `setSelected()` 函数在标记中被调用，以便向元素插入适当的属性。

对于密码字段，在页面中重新显示用户的密码是不明智的，因为查看 HTML 源代码就可以轻松读取密码。因此，这两个密码字段始终

