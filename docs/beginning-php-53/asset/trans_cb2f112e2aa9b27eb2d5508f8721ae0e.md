

```php
if ( !$member->getValue( $requiredField ) ) {
    $missingFields[] = $requiredField;
}
if ( $missingFields ) {
    $errorMessages[] = '<p class="error">There were some missing fields
in the form you submitted. Please complete the fields highlighted below and
click Send Details to resend the form.</p>';
}
if ( !isset( $_POST["password1"] ) or !isset( $_POST["password2"] ) or
    !$_POST["password1"] || !$_POST["password2"] || ( $_POST["password1"] !=
    $_POST["password2"] ) ) {
    $errorMessages[] = '<p class="error">Please make sure you enter your
password correctly in both password fields.</p>';
}
if ( Member::getByUsername( $member->getValue( "username" ) ) ) {
    $errorMessages[] = '<p class="error">A member with that username
already exists in the database. Please choose another username.</p>';
}
if ( Member::getByEmailAddress( $member->getValue( "emailAddress" ) ) ) {
    $errorMessages[] = '<p class="error">A member with that email address
already exists in the database. Please choose another email address, or
contact the webmaster to retrieve your password.</p>';
}
if ( $errorMessages ) {
    displayForm( $errorMessages, $missingFields, $member );
} else {
    $member->insert();
    displayThanks();
}
function displayThanks() {
    displayPageHeader( "Thanks for registering!" );
?>
<p>Thank you, you are now a registered member of the book club.</p>
<?php
    displayPageFooter();
}
?>
```

再说一遍，你大概能从第9章的registration.php脚本中认出这个脚本的总体结构。主要区别在于，这个脚本包含额外的错误检查，而且它还会创建新成员记录（第9章的脚本只是显示一条感谢消息）。

首先，脚本包含必需的common.inc.php文件，然后检查注册表单是否已提交。如果已提交，它会调用processForm()来处理表单数据。否则，它会通过调用`displayForm()`来显示表单，并传入两个空数组和一个空的`Member`对象。（稍后你就会明白它为什么要这样做。）

`displayForm()`函数，顾名思义，处理注册表单的显示。它期望三个参数：

- `$errorMessages` 是一个数组，包含要显示给用户的任何错误消息
- `$missingFields` 是用户未填写的任何必填字段的列表
- `$member` 是一个`Member`对象，包含用户迄今输入的任何数据，用于在需要显示错误时预填表单字段。（这让你了解面向对象编程的灵活性——脚本不仅将`Member`类用于数据库访问，还用于在表单提交之间保存临时成员数据。）

该函数显示页面页眉，如果`$errorMessages`中包含任何错误消息，则将这些消息显示在页面顶部。否则，会显示一条欢迎消息。

接下来，输出表单本身。这与第9章中的`registration.php`表单工作方式类似。每个字段都会显示，并在适当的时候调用`validateField()`来突出显示缺少的必填字段。通过调用`$member->getValueEncoded()`来检索存储在`$member`对象中的先前输入的值，以预填充字段的值。在性别复选框的情况下，会调用`setChecked()`来预选相应的复选框。对于`favoriteGenre()`下拉菜单，使用`setSelected()`来预选正确的选项。

表单还包含一个隐藏字段`action`，其值为"`register`"。脚本顶部的`if`语句使用它来确定表单是否已提交。

表单显示完毕后，通过调用`displayPageFooter()`输出页面页脚。

`processForm()`处理验证和存储提交的表单数据。首先，该函数设置一个`$requiredFields`数组，用于存储必填表单字段的列表，以及两个空数组：`$missingFields`用于存储用户未填写的任何必填字段，`$errorMessages`用于存储要显示给用户的任何错误消息。

接下来，该函数从`$_POST`数组中读取九个表单字段值——`username`、`password1`、`password2`、`firstName`、`lastName`、`gender`、`favoriteGenre`、`emailAddress`和`otherInterests`——并将其存储在新的`Member`对象中。对于每个字段，它会检查该字段是否存在于`$_POST`数组中；如果存在，则通过适当的正则表达式进行过滤，以删除任何潜在的危险字符，并将其存储在`Member`对象中。如果字段不存在，则改为存储空字符串("")。

*要了解正则表达式，请参阅第18章；要了解输入过滤，请参阅第20章。*

对于`password1`和`password2`字段，脚本检查两个字段是否都已填写且值是否匹配。如果是，则将`password1`的值存储在`Member`对象的`password`字段中。否则，存储空字符串：

```
"password" => ( isset( $_POST["password1"] ) && isset( $_POST["password2"] )
and $_POST["password1"] == $_POST["password2"] ) ? preg_replace( "/[^\\_a-zA-Z0-9]/", "", $_POST["password1"] ) : "",
```

还要注意，`Member`对象的`joinDate`字段已设置：

```
"joinDate" => date( "Y-m-d" )
```

PHP的`date()`函数用于生成表示当前日期的字符串，格式为YYYY-MM-DD。然后将该字符串存储在`joinDate`字段中，反映会员完成注册的日期。

你可以在第16章了解更多关于`date()`的信息。

现在，`Member`对象已创建并用提交的表单数据填充，脚本会对数据执行各种检查。首先，它会遍历必填字段名称列表；如果某个必填字段未填写，则将其字段名称添加到`$missingFields`数组中：

```
foreach ( $requiredFields as $requiredField ) {
    if ( !$member->getValue( $requiredField ) ) {
        $missingFields[] = $requiredField;
    }
}
```

如果遇到任何缺少的字段，则会将适当的错误消息添加到`$errorMessages`数组中：

```
if ( $missingFields ) {
    $errorMessages[] = '<p class="error">There were some missing fields in the
    form you submitted. Please complete the fields highlighted below and click
    Send Details to resend the form.</p>';
}
```

如果输入的密码不匹配，或者输入的用户名或电子邮件地址已被占用，也会创建错误消息。对于用户名检查，会使用输入的用户名调用`Member::getByUsername()`；如果它返回一个`Member`对象，脚本就知道用户名已被占用并生成错误消息。同样，对于电子邮件地址，会调用`Member::getByEmailAddress()`来确定输入的电子邮件地址的会员是否已存在于数据库中。

最后，如果引发了任何错误消息，脚本会调用`displayForm()`向用户重新显示表单，并传入错误消息列表、缺少的字段列表（如果有）以及包含用户已输入数据的已填充`Member`对象，以便在表单中重新显示。另一方面，如果提交的数据正确，则会通过调用`Member`对象的`insert()`方法在members表中创建会员记录：

```
if ( $errorMessages ) {
    displayForm( $errorMessages, $missingFields, $member );
} else {
    $member->insert();
    displayThanks();
}
```

脚本中的最终函数`displayThanks()`只是显示一条感谢消息，感谢会员注册。

## 测试应用程序

创建register.php脚本后，打开Web浏览器并输入脚本的URL来测试注册流程。尝试在表单中输入一些值并提交它，看看会发生什么。图14-1显示了脚本的运行情况；在这个示例中，用户忘记输入电子邮件地址。请注意，脚本还会提示他们重新输入密码（在表单中重新显示已输入的密码永远不是个好主意）。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_454_0.png)

图 14-1

你现在已将图书俱乐部应用程序扩展为允许新会员注册俱乐部。在此过程中，你学习了如何使用PHP和PDO向members表添加新会员记录。

## 创建会员专区

既然会员可以为你的图书俱乐部注册了，你将在网站上为他们提供一个会员专区，他们可以使用它来查看即将举行的活动、查看当前阅读列表等等。出于本章的目的，你的会员专区将只包含一些虚拟页面，但希望

