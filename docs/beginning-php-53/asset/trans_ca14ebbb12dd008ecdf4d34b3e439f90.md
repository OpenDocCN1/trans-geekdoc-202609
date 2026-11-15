

你可能从第 9 章认出这些函数（尽管它们已略作修改）。validateField() 检查提供的字段名是否在用户忘记填写的字段列表中。如果是，则会输出 class="error" 属性，该属性会将缺失字段以红色突出显示。

与此同时，setChecked() 和 setSelected() 分别输出用于预选复选框和预选菜单中选项的标记。这两种方法都期望一个派生自 DataObject 类的对象（例如 Member 对象）、要查找的字段名称以及要比较的值。如果提供的值与对象中字段的值匹配，则会输出标记。这些函数在注册表单中用于帮助预填表单字段，如你稍后将看到。

## 增强 Member 类

接下来要做的是向 Member 类添加更多功能。首先，添加几个额外方法用于从数据库中检索 Member 对象。getByUsername() 检索提供的用户名对应的成员，getByEmailAddress() 检索给定电子邮件地址对应的成员。这些方法将用于确保潜在成员不会意外注册已存在于数据库中的用户名或电子邮件地址。

打开在第 13 章中创建的 Member.class.php 文件，并在现有的 getMember() 方法之后将以下代码添加到文件中：

```php
public static function getByUsername( $username ) {
$conn = parent::connect();
$sql = "SELECT * FROM ". TBL_MEMBERS . " WHERE username = :username";
try {
$st = $conn->prepare( $sql );
$st->bindValue( ":username", $username, PDO::PARAM_STR );
$st->execute();
$row = $st->fetch();
parent::disconnect( $conn );
if ( $row ) return new Member( $row );
} catch ( PDOException $e ) {
parent::disconnect( $conn );
die( "Query failed: " . $e->getMessage() );
}
}
public static function getByEmailAddress( $emailAddress ) {
$conn = parent::connect();
$sql = "SELECT * FROM ". TBL_MEMBERS . " WHERE emailAddress = :emailAddress";
try {
$st = $conn->prepare( $sql );
$st->bindValue( ":emailAddress", $emailAddress, PDO::PARAM_STR );
$st->execute();
$row = $st->fetch();
parent::disconnect( $conn );
if ( $row ) return new Member( $row );
} catch ( PDOException $e ) {
parent::disconnect( $conn );
die( "Query failed: " . $e->getMessage() );
}
}
```

这些方法不言自明。你可以看到，它们的工作方式与你在上一章中创建的 getMember() 大致相同。

接下来，添加一个简短的 getGenres() 方法，它只检索私有 $_genres 数组属性中的值。这将用于显示一个供潜在成员选择的类型列表。将其插入到类文件中现有 getFavoriteGenreString() 方法的正下方：

```php
public function getGenres() {
return $this->_genres;
}
```

到目前为止，该类包含用于从成员表中检索成员记录的方法。现在你将添加一个新方法 insert()，它将向表中添加一个新成员。将以下代码添加到类文件末尾，就在关闭类的花括号之前：

```php
public function insert() {
$conn = parent::connect();
$sql = "INSERT INTO ". TBL_MEMBERS . " (
username,
password,
firstName,
lastName,
joinDate,
gender,
favoriteGenre,
emailAddress,
otherInterests
) VALUES (
:username,
:password,
:firstName,
:lastName,
:joinDate,
:gender,
:favoriteGenre,
:emailAddress,
:otherInterests
)";
try {
$st = $conn->prepare( $sql );
$st->bindValue( ":username", $this->data["username"], PDO::PARAM_STR );
$st->bindValue( ":password", $this->data["password"], PDO::PARAM_STR );
$st->bindValue( ":firstName", $this->data["firstName"], PDO::PARAM_STR );
$st->bindValue( ":lastName", $this->data["lastName"], PDO::PARAM_STR );
$st->bindValue( ":joinDate", $this->data["joinDate"], PDO::PARAM_STR );
$st->bindValue( ":gender", $this->data["gender"], PDO::PARAM_STR );
$st->bindValue( ":favoriteGenre", $this->data["favoriteGenre"],
PDO::PARAM_STR );
$st->bindValue( ":emailAddress", $this->data["emailAddress"],
PDO::PARAM_STR );
$st->bindValue( ":otherInterests", $this->data["otherInterests"],
PDO::PARAM_STR );
$st->execute();
parent::disconnect( $conn );
} catch ( PDOException $e ) {
parent::disconnect( $conn );
die( "Query failed: " . $e->getMessage() );
}
}
```

如果你一直跟随前面几章和本章的内容，这里应该不会有任何意外。insert() 构建一个 SQL 语句，将当前 Member 对象中存储的数据插入数据库。请注意，该语句不尝试为 id 字段插入值，因为该值由 MySQL 自动生成。

然后该方法使用 PDO::prepare() 准备语句，将每个占位符绑定到 Member 对象的 $data 数组属性中的相应值，并通过调用 PDOStatement::execute() 执行语句。如果插入过程中出现任何问题，则会捕获并显示异常，且应用程序退出。

## 创建注册脚本

现在你已将所需功能添加到公共代码文件和 Member 类文件中，可以构建注册脚本本身了。将以下代码保存为 book_club 文件夹中的 register.php：

```php
<?php

require_once( "common.inc.php" );

if ( isset( $_POST["action"] ) and $_POST["action"] == "register" ) {
processForm();
} else {
displayForm( array(), array(), new Member( array() ) );
}

function displayForm( $errorMessages, $missingFields, $member ) {
displayPageHeader( "Sign up for the book club!" );

if ( $errorMessages ) {
foreach ( $errorMessages as $errorMessage ) {
    echo $errorMessage;
}
} else {
?>
<p>Thanks for choosing to join our book club.</p>
<p>To register, please fill in your details below and click Send Details.</p>
<p>Fields marked with an asterisk (*) are required.</p>
<?php } ?>
<form action="register.php" method="post" style="margin-bottom: 50px;">
<div style="width: 30em;">
<input type="hidden" name="action" value="register" />
<label for="username"<?php validateField( "username", $missingFields ) ?>>Choose a username *</label>
<input type="text" name="username" id="username" value="<?php echo $member->getValueEncoded( "username" ) ?>" />
<label for="password"<?php if ( $missingFields ) echo ' class="error" ' ?>>Choose a password *</label>
<input type="password" name="password1" id="password1" value="" />
<label for="password2"<?php if ( $missingFields ) echo ' class="error" ' ?>>Retype password *</label>
<input type="password" name="password2" id="password2" value="" />
<label for="emailAddress"<?php validateField( "emailAddress", $missingFields ) ?>>Email address *</label>
<input type="text" name="emailAddress" id="emailAddress" value="<?php echo $member->getValueEncoded( "emailAddress" ) ?>" />
<label for="firstName"<?php validateField( "firstName", $missingFields ) ?>>First name *</label>
<input type="text" name="firstName" id="firstName" value="<?php echo $member->getValueEncoded( "firstName" ) ?>" />
<label for="lastName"<?php validateField( "lastName", $missingFields ) ?>>Last name *</label>
<input type="text" name="lastName" id="lastName" value="<?php echo $member->getValueEncoded( "lastName" ) ?>" />
<label<?php validateField( "gender", $missingFields ) ?>>Your gender: *</label>
<label for="genderMale">Male</label>
<input type="radio" name="gender" id="genderMale" value="m"<?php setChecked( $member, "gender", "m" ) ?> />
<label for="genderFemale">Female</label>
<input type="radio" name="gender" id="genderFemale" value="f"<?php setChecked( $member, "gender", "f" ) ?> />
<label for="favoriteGenre">What's your favorite genre?</label>
<select name="favoriteGenre" id="favoriteGenre" size="1">
<?php foreach ( $member->getGenres() as $value => $label ) { ?>
<option value="<?php echo $value ?>"<?php setSelected( $member, "favoriteGenre", $value ) ?>><?php echo $label ?></option>
<?php } ?>
</select>

<label for="otherInterests">What are your other interests?</label>
<textarea name="otherInterests" id="otherInterests" rows="4" cols="50"><?php echo $member->getValueEncoded( "otherInterests" ) ?></textarea>

<div style="clear: both;">
<input type="submit" name="submitButton" id="submitButton" value="Send Details" />
<input type="reset" name="resetButton" id="resetButton" value="Reset Form" style="margin-right: 20px;" />
</div>

</div>
</form>
<?php
displayPageFooter();
}
```

```php
function processForm() {
$requiredFields = array( "username", "password", "emailAddress",
    "firstName", "lastName", "gender" );
$missingFields = array();
$errorMessages = array();

$member = new Member( array(
    "username" => isset( $_POST["username"] ) ? preg_replace( "/[^\ \-\_a-zA-Z0-9]/", "", $_POST["username"] ) : "",
    "password" => isset( $_POST["password1"] ) and isset( $_POST["password2"] ) and $_POST["password1"] == $_POST["password2"] ) ? preg_replace( "/[^\ \-\_a-zA-Z0-9]/", "", $_POST["password1"] ) : "",
    "firstName" => isset( $_POST["firstName"] ) ? preg_replace( "/[^\ \-\_a-zA-Z0-9]/", "", $_POST["firstName"] ) : "",
    "lastName" => isset( $_POST["lastName"] ) ? preg_replace( "/[^\ \-\_a-zA-Z0-9]/", "", $_POST["lastName"] ) : "",
    "gender" => isset( $_POST["gender"] ) ? preg_replace( "/[^mf]/", "", $_POST["gender"] ) : "",
    "favoriteGenre" => isset( $_POST["favoriteGenre"] ) ? preg_replace( "/[^a-zA-Z]/", "", $_POST["favoriteGenre"] ) : "",
    "emailAddress" => isset( $_POST["emailAddress"] ) ? preg_replace( "/[^\ \@\.\\_a-zA-Z0-9]/", "", $_POST["emailAddress"] ) : "",
    "otherInterests" => isset( $_POST["otherInterests"] ) ? preg_replace( "/[^\ \'\,\.\-\a-zA-Z0-9]/", "", $_POST["otherInterests"] ) : "",
    "joinDate" => date( "Y-m-d" )
) );

foreach ( $requiredFields as $requiredField ) {

