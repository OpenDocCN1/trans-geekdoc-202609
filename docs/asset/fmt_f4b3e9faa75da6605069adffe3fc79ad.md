
```php
VALUES ('$petName','$petColor','$pix')";

$result = mysql_query($query)
    or die ("Couldn't execute query.");

echo "<li>Color: $petColor\n";

}
}

echo "</ul>";

echo "<a href='ChoosePetCat.php'>Add Another Pet</a>\n";

?>
</body></html>
```

请注意清单 11-11 中行尾作为注释显示的行号。以下列表中的编号对应于清单中的行号。我仅记录以下列表中的部分行，因为诸如连接数据库等许多常见任务已在本章前面的程序中记录过。

- 7. 检查用户是否点击了 `Cancel` 按钮。如果是，则返回第一页。
- 18 启动一个 `if` 块，仅当用户为宠物名称选择了 `new` 时执行。如果新名称为空，则重复显示一个表单，要求输入新的宠物名称（第 20 行），直到用户输入为止。填写新名称后，`$petName` 被设置为新名称（第 25 行）。
- 31 如果未输入图片文件名，则将其设置为默认图片。
- 38 第 38-55 行将新宠物添加到数据库。数据在添加前会被清理。
- 57 开始输出反馈页面。
- 66 启动一个 `if` 块，仅当填写了颜色时执行。颜色仅针对鹦鹉和金鱼存储。会检查 `Color` 表中是否已存在名称和颜色。如果不存在，则将其添加到 `Color` 表中。该 `if` 块在第 85 行结束。

此程序引入一个 HTML 文件，如果用户忘记输入宠物名称，则创建表单提示用户输入。清单 11-12 显示了被包含的文件：`NewName_form.inc`。

### 清单 11-12：提示用户输入新宠物名称的 HTML

```php
<?php

/* Program: NewName_form.inc
 * Desc:      Displays form to collect a pet name
 */

?>
<b>You must type a pet name.</b>

<form action="AddPet.php" method="post">

<table><tr>

<td align="right">Pet name:</td>

<td><input type="text" name="newName"
value="<?php echo $newName ?>"
size="25" maxlength="25">
</td></tr>
</table>

<input type="hidden" name="category"
value="<?php echo $category ?>">

<input type="hidden" name="petName"
value="<?php echo $petName ?>">

<input type="hidden" name="petDescription"
value="<?php echo $petDescription ?>">

<input type="hidden" name="price"
value="<?php echo $price ?>">

<input type="hidden" name="pix" value="<?php echo $pix ?>">

<input type="hidden" name="petColor"
value="<?php echo $petColor ?>">

<p><input type="submit" name="newbutton"
value="Enter new pet name">
<input type="submit" name="newbutton" value="Cancel">
</form>
```

该文件创建了一个表单，当用户忘记输入新宠物名字时显示。它与清单11-7中当用户忘记输入新类别时显示的程序非常相似。请注意，两个隐藏字段用于传递 `$category` 和 `$petName` 的值。当表单填写完毕后，需要这两个变量的值来存储宠物信息。

最后，该程序提供一个指向首页的链接，以便用户在需要时可以向目录中添加另一只新宠物。

# 第12章 构建会员专享网站

## 本章内容

- 设计会员专享网站
- 为成员目录构建数据库
- 设计会员专区的网页
- 编写用于登录会员专区的程序

许多网站都要求用户登录。有时，用户不输入密码就无法查看任何网页；有时，网页只有一部分需要登录。以下是您可能希望要求用户登录的一些原因：

- **信息是机密。** 你不希望除少数授权人员以外的任何人看到这些信息。或者，也许只应该让你自己的员工看到这些信息。
- **信息或服务用于出售。** 你的网站提供的信息或服务就是你想要收费的产品。例如，你可能垄断了研究人员愿意付费购买的一些调查数据。例如，AAA Automobile Club（美国汽车协会）免费提供部分信息，但你必须成为会员才能查看其酒店评级。
- **你可以提供更好的服务。** 如果你知道客户是谁，或者拥有他们的一些信息，就能简化他们与网站的交互。例如，如果你在 Barnes & Noble.com 或 Gap 拥有账户并登录其网站，他们会使用你存储的收货地址，这样你就不必再次输入。

## 构建数据库

数据库是此应用程序的核心和目的所在。它保存客户信息，这正是会员专区要实现的目标。它还保存会员ID和密码，以便用户登录会员专区。

会员专享应用的数据库包含两个表：

- 会员表
- 登录表

构建登录应用的第一步是构建数据库。如果没有一个可以测试程序的可用数据库，那么编写程序几乎不可能。首先设计数据库；然后构建它；再添加一些示例数据，供开发程序时使用。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_353_0.png)

在第3章中我为宠物商店网站的会员专享受限区域设计的数据库做了一些修改。开发和测试常常会导致改动。也许你会发现设计中未考虑某些因素，或者设计的某些元素不适用于真实数据，或难以编程。在应用程序开发过程中设计不断演进是完全正常的，只需确保在设计变更时同步修改文档即可。

### 构建会员表

在登录应用的设计中，主表是会员表。它保存客户输入的所有信息，包括客户个人信息（姓名、地址、电话号码等）以及会员ID和密码。以下SQL查询创建会员表：

```sql
CREATE TABLE Member (
    loginName      VARCHAR(20)    NOT NULL,
    createDate     DATE           NOT NULL,
    password       VARCHAR(255)   NOT NULL,
    lastName       VARCHAR(50),
    firstName      VARCHAR(40),
    street         VARCHAR(50),
    city           VARCHAR(50),
    state          CHAR(2),
    zip            CHAR(10),
    email          VARCHAR(50),
    phone          CHAR(15),
    fax            CHAR(15),
    PRIMARY KEY(loginName));
```

每一行代表一位会员。各列如下：

- **loginName：** 会员登录时使用的会员ID。登录名由客户选择并输入。`CREATE` 查询以如下方式定义 `loginName`：
  - `CHAR(20)`：此数据类型将该字段定义为长度为20个字符的字符串。该字段始终占用20个字符的存储空间，如果实际存储的字符串少于20个字符，则填充空格。如果存储的字符串超过20个字符，则丢弃第20个字符之后的字符。
  - `PRIMARY KEY(loginName)`：主键标识行且必须唯一。MySQL 不允许两行具有相同的 `loginName`。
  - `NOT NULL`：此定义表示该字段不能为空，必须有一个值。主键必须始终设置为 `NOT NULL`。

- **createDate：** 将该行添加到数据库的日期，也就是客户创建账户的日期。查询将 `createDate` 定义为：
  - `DATE`：这是一个按日期处理的字符串。日期以 YYYY-MM-DD 格式显示。可以按该格式或一些类似格式输入，例如 YY/M/D 或 YYYYMMDD。
  - `NOT NULL`：此定义表示该字段不能为空，必须有一个值。因为日期是由程序而不是用户创建并存储的，所以它永远不会为空。

- **password：** 会员登录时使用的密码。密码由客户选择并输入。`CREATE` 查询以如下方式定义 `password`：
  - `VARCHAR(255)`：此语句将该字段定义为可变字符串，长度最多为255个字符。该字段按实际长度存储。你并不期望密码有255个字符长。事实上，你期望它相当短。然而，你打算使用 MySQL 的 `password` 函数对其进行加密，而不是明文存储。加密后字符串会变长，所以要为更长的字符串留出空间。
  - `NOT NULL`：此语句表示该字段不能为空，必须有一个值。在此应用中，你不允许空密码。

- **lastName：** 客户输入的姓氏。`CREATE` 查询将该字段定义为：
  - `VARCHAR(50)`：此数据类型将该字段定义为可变字符串，长度最多为50个字符。该字段按实际长度存储。

- **firstName：** 客户输入的名字。`CREATE` 查询将该字段定义为：
  - `VARCHAR(40)`：此数据类型将该字段定义为可变字符串，长度最多为40个字符。该字段按实际长度存储。

- **street：** 客户输入的街道地址。`CREATE` 查询将该字段定义为：
  - `VARCHAR(50)`：此数据类型将该字段定义为可变字符串，长度最多为50个字符。该字段按实际长度存储。

- **city：** 客户地址中的城市，由客户输入。`CREATE` 查询将该字段定义为：
  - `VARCHAR(50)`：此数据类型将该字段定义为可变字符串，长度最多为50个字符。该字段按实际长度存储。

- **state：** 客户地址中的州。该字符串是两位字母的州代码。客户从包含所有州的下拉列表中选择数据。`CREATE` 查询将该字段定义为：
  - `CHAR(2)`：此数据类型将该字段定义为长度为两个字符的字符串。该字段始终占用两个字符的存储空间，如果实际存储的字符串少于两个字符，则填充空格。

- **zip：** 客户输入的邮政编码。`CREATE` 查询将该字段定义为：
  - `CHAR(10)`：此数据类型将该字段定义为长度为十个字符的字符串。该字段始终占用十个字符的存储空间，如果实际存储的字符串少于十个字符，则填充空格。该字段足够长，可容纳 ZIP+4 代码，例如 12345-1234。

- **email：** 客户输入的电子邮件地址。`CREATE` 查询将该字段定义为：
  - `VARCHAR(50)`：此数据类型将该字段定义为可变字符串，长度最多为50个字符。该字段按实际长度存储。

- **phone：** 客户输入的电话号码。`CREATE` 查询将该字段定义为：
  - `CHAR(15)`：此数据类型将该字段定义为长度为15个字符的字符串。该字段始终占用15个字符的存储空间，如果实际存储的字符串少于15个字符，则填充空格。

- **传真**：客户输入的传真号码。`CREATE` 查询将该字段定义为
  - `CHAR(15)`：此数据类型将该字段定义为长度为 15 个字符的字符串。该字段始终占用 15 个字符的存储空间，如果实际存储的字符串少于 15 个字符，则会进行填充。

请注意，有些字段是 `CHAR`，有些是 `VARCHAR`。`CHAR` 字段速度更快，而 `VARCHAR` 字段在磁盘空间利用方面更高效。你的决策将取决于在你的环境中，对应用程序而言，磁盘空间和速度哪个更重要。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_356_0.png)

一般来说，较短的字段应使用 `CHAR`，因为较短的字段不会浪费太多空间。例如，如果你的 `CHAR` 长度为 5 个字符，最多可能浪费的空间是 4 个字符。但如果你的 `CHAR` 长度为 200，则可能浪费 199 个字符。因此，对于短字段，使用 `CHAR` 可以获得速度，同时浪费的空间极少。

## 构建 Login 表

`Login` 表通过记录每位会员每次登录的日期和时间来跟踪会员登录情况。由于每位会员有多次登录记录，因此登录数据需要单独的表。用于构建 `Login` 表的 `CREATE` 查询如下：

```sql
CREATE TABLE Login (
    loginName    VARCHAR(20) NOT NULL,
    loginTime    DATETIME    NOT NULL,
    PRIMARY KEY(loginName,loginTime) );
```
