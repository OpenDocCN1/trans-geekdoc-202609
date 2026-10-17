
## 构建 Color 表

在本章前面讨论构建 Pet 表时（参见“构建 Pet 表”），我讨论了不同类型的宠物：独特的宠物（如小狗和马）和非独特的宠物（如金鱼和乌龟）。对于独特的宠物，客户需要看到实际宠物的照片。对于非独特的宠物，客户只需要看到一张通用图片。

在某些情况下，通用宠物有多种颜色，例如蓝色长尾小鹦鹉和绿色长尾小鹦鹉。你可能想为长尾小鹦鹉显示两张图片：一张蓝色长尾小鹦鹉的图片和一张绿色长尾小鹦鹉的图片。但是，由于大多数宠物并非这种通用宠物，你不会希望在主 `Pet` 表中添加颜色列，因为大部分行的该列都会是空白的。相反，你可以创建一个单独的表，只包含有多种颜色的宠物。然后，当目录应用程序显示宠物时，它可以检查 `Color` 表，查看是否有多于一种颜色可用——如果有，就可以显示 `Color` 表中的图片。

`Color` 表在宠物具有不同颜色时指向宠物的图片，以便目录可以显示所有可用颜色的图片。以下 SQL 查询创建 `Color` 表：

```
CREATE TABLE Color (
  petName      CHAR(25)      NOT NULL,
  petColor     CHAR(15)      NOT NULL,
  pix          CHAR(15)      NOT NULL DEFAULT "na.gif",
  PRIMARY KEY(petName,petColor) );
```

每一行代表一种宠物类型。各列如下：

✓ `petName`：宠物的名称，例如狮子、牧羊犬或中国鬃狮蜥。请注意，`petName` 列在 `Pet` 表和此表中的定义相同。这使得表连接成为可能，也更便于匹配两个表中的行。但是，`petName` 在此表中是主键，而在 `Pet` 表中不是。`CREATE` 查询通过以下方式定义 `petName`：

- `CHAR(25)`：此字段中的数据预期为 25 个字符长的字符串。
- `PRIMARY KEY(petName,petColor)`：主键必须是唯一的。对于此表，两列共同组成主键——此列和 `petColor` 列。`MySQL` 不允许输入具有相同 `petName` 和 `petColor` 的两行。
- `NOT NULL`：此定义意味着该字段不能为空，必须有一个值。主键必须始终定义为 `NOT NULL`。

✓ `petColor`：宠物的颜色，例如橙色或紫色。`CREATE` 查询通过以下方式定义 `petColor`：

- `CHAR(15)`：此数据类型将该字段定义为 15 个字符长的字符串。
- `PRIMARY KEY(petName,petColor)`：主键必须是唯一的。对于此表，两列共同组成主键——此列和 `petName` 列。`MySQL` 不允许输入具有相同 `petName` 和 `petColor` 的两行。
- `NOT NULL`：此定义意味着该字段不能为空，必须有一个值。主键必须始终定义为 `NOT NULL`。

✓ `pix`：包含宠物图片的文件名。`CREATE` 查询通过以下方式定义 `pix`：

- `CHAR(15)`：此数据类型将该字段定义为 15 个字符长的字符串。
- `NOT NULL`：此定义意味着该字段不能为空，必须有一个值。你需要为宠物准备一张图片。当网站试图显示一张找不到的图片时，它会在浏览器窗口中原本应显示图形的位置显示一条难看的错误消息。你不会希望你的目录出现这种情况，因此你的数据库应该要求有一个值。在这种情况下，`CREATE` 查询定义了一个默认值，以便该字段始终会被填入一个值。
- `DEFAULT "na.gif"`：如果你没有为 `pix` 提供值，则存储值 `"na.gif"`。这样，`pix` 总是会存储一个值。文件 `na.gif` 可能包含一张内容类似“图片不可用”的图片。

## 向数据库添加数据

你可以通过多种方式向数据库添加数据。你可以使用 SQL 查询将宠物添加到数据库，也可以使用我在本章中描述的应用程序。在开发过程中，我个人最喜欢的方式是从文件读取数据，向目录中添加一些示例项目。然后，每当开发过程中我的数据变得完全混乱时（由于编程错误或我古怪的幽默感），我都可以立刻重新创建数据表。只需 `DROP` 该表，用 SQL 查询重新创建它，然后重新读取示例数据。

例如，`Pet` 表的数据文件可能如下所示：

```
<TAB>Pekinese<TAB>Dog<TAB>Small, cute, energetic. Good alarm system.<TAB>100.00<TAB>peke.jpg
<TAB>House cat<TAB>Cat<TAB>Yellow and white cat. Extremely playful.<TAB>20.00<TAB>catyellow.jpg
<TAB>House cat<TAB>Cat<TAB>Black cat. Sleek, shiny. Likes children.<TAB>20.00<TAB>catblack.jpg
<TAB>Chinese Bearded Dragon<TAB>Lizard<TAB>Grows up to 2 feet long. Fascinating to watch. Likes to be held.<TAB>100.00<TAB>lizard.jpg
<TAB>Labrador Retriever<TAB>Dog<TAB>Black dog. Large, intelligent retriever. Often selected as guide dogs for the blind.<TAB>100.00<TAB>lab.jpg
<TAB>Goldfish<TAB>Fish<TAB>Variety of colors. Inexpensive. Easy care. Good first pet for small children.<TAB>2.00<TAB>goldfish.jpg
<TAB>Shark<TAB>Fish<TAB>Sleek. Powerful. Handle with care.<TAB>200.00<TAB>shark.jpg
<TAB>Asian Dragon<TAB>Dragon<TAB>Long and serpentine. Often gold or red.<TAB>10000.00<TAB>dragona.jpg
<TAB>Unicorn<TAB>Horse<TAB>Beautiful white steed with spiral horn on forehead.<TAB>20000.00<TAB>unicorn.jpg
```

这些是数据文件的规则：

- ✔ `<TAB>` 标签表示真正的制表符——即按 Tab 键创建的那种。
- ✔ 每一行代表一只宠物，并且输入时不能按 Enter 或 Return 键。上面示例中的行显示为折行到多行，以便你能看到整行。然而，在实际文件中，数据行是每行一行。
- ✔ 每行开头出现一个制表符，因为第一个字段不被录入。第一个字段是 `petID`，它是自动录入的；你不需要录入它。但是，你确实需要使用制表符，以便 `MySQL` 知道开头有一个空白字段。

然后，你可以使用 SQL 查询将数据文件读入 `Pet` 表：

```
LOAD DATA LOCAL INFILE "pets" INTO TABLE Pet;
```

任何时候数据表变得异常，你都可以重新创建它并再次读取数据。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_324_0.png)

**图 11-1：** 宠物商店网站的开篇页面。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_324_1.png)

**图 11-2：** 宠物商店网站的宠物类型页面。

## 宠物页面

宠物页面列出所选类型的所有宠物。每只宠物都列出其 `petID`、描述、价格和图片。宠物页面根据目录数据库中的信息以不同格式显示。图 11-3、11-4 和 11-5 展示了一些可能的宠物页面。图 11-3 显示了一个列出目录中三只不同的狗的页面。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_325_0.png)

图 11-3：

此宠物页面显示三只不同的狗。

图 11-4 显示不止一只宠物可以具有相同的宠物名称。请注意，家猫具有不同的 `petID` 编号。

图 11-5 显示了在 `Color` 表中找到宠物时的输出，表明有不止一种颜色可用。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_326_0.png)

**图 11-4：** 此宠物页面显示三只具有相同宠物名称的猫。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_326_1.png)

**图 11-5：** 此宠物页面显示有两种颜色可用的金鱼。

在所有这些页面上，顶部有一行文字为 `Click on any picture to see a larger version`。如果客户点击图片，则会显示该图片的较大版本。

## 将宠物添加到目录

该应用程序包含三个客户看不到的页面；这些页面用于将宠物添加到宠物目录中。这三个页面按顺序工作以添加单个宠物：

- 1. **获取宠物类型页面。** 添加宠物到目录的人员选择宠物类型的单选按钮。用户还可以输入新的宠物类型。
- 2. **获取宠物信息页面。** 用户选择要添加的宠物的单选按钮并填写宠物描述、价格和图片文件名。用户还可以输入新的宠物名称。
- 3. **反馈页面。** 显示一个页面，展示已添加到目录的宠物信息。

## 获取宠物类型页面

第一个页面获取需要添加到目录的宠物的宠物类型。图 11-6 显示了获取宠物类型页面。请注意，目录中当前所有的宠物类型都已列出，并且提供了一个区域，用户可以在需要时输入新的宠物类型。

## 获取宠物信息页面

图 11-7 显示了第二个页面。此页面允许用户输入将进入目录的宠物的信息。此页面列出了所选宠物类型在目录中的所有宠物名称，以便用户可以选择其中一个。它还提供了一个区域，用户可以在需要时输入新的宠物名称。

## 反馈页面

当用户提交宠物信息时，信息将被添加到 `PetCatalog` 数据库中。图 11-8 显示了一个验证已添加到数据库中的信息的页面。用户可以点击链接返回第一页并添加另一只宠物。

## 获取缺失信息页面

应用程序检查数据以查看用户是否输入了所需信息，并提示用户输入任何未输入的信息。例如，如果用户在第一页选择“新类别”，则用户必须输入类别名称和描述。如果用户未输入名称或描述，则会显示一个页面指出问题并请求信息。图 11-9 显示了用户忘记输入类别名称和描述时看到的页面。

图 11-6：

添加宠物到目录的第一页。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_328_0.png)

## 选择要添加的宠物的类别。

如果您要添加的宠物类别未列出，请选择“新类别”并输入该类别的名称和描述。在您完成选择现有类别或输入新类别后，按“提交类别”。

图 11-7：

第二个页面要求输入宠物名称。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_328_1.png)

## 图 11-8：

最后一页提供反馈。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_329_0.png)

以下宠物已添加到宠物目录：

- Category: Dog
- Pet Name: Golden Retriever
- Pet Description: Large, intelligent retriever. Likes people. Often wins obedience trials.
- Price: 100.00
- Picture file: gold.jpg

Add Another Pet

## 图 11-9：

此页面请求新的类别和描述。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_329_1.png)

类别名称或类别描述留空。您必须同时输入两者。

Category name:

Category description:

Enter new category

Return to category page

## 编写程序

在您知道页面将是什么样子以及它们将做什么之后，您就可以编写程序了。一般来说，您为每个页面编写一个程序，尽管有时将程序分离到多个文件或将页面上的程序合并是有意义的。（有关如何组织应用程序的详细信息，请参阅第 10 章。）

正如我在第 10 章中所讨论的，将连接数据库所需的信息保存在单独的文件中，并在所有需要访问数据库的程序中包含该文件。出于安全原因，该文件应存储在安全位置并使用误导性的名称。对于此应用程序，以下信息存储在名为 `misc.inc` 的文件中：

```php
<?php
    $user="catalog";
    $host="localhost";
    $password="";
    $database="PetCatalog";
?>
```

宠物目录应用程序有两个独立的程序集：一组向客户展示宠物目录，另一组将新宠物输入目录。

### 向客户展示宠物

向客户展示宠物目录的应用程序有三个基本任务：

- 显示店面页面。提供目录链接。
- 显示用户选择宠物类型的页面。
- 显示所选宠物类型的宠物页面。

### 显示店面

店面页面不需要任何 PHP 语句。它只显示一个带有链接的网页。HTML 语句足以完成此操作。列表 11-1 显示了描述店面页面的 HTML 文件。

## 列表 11-1：店面页面的 HTML 文件

```php
<?php
  /* Program: PetShopFront.php
   * Desc:    Displays opening page for Pet Store.
   */
?>
```

```html
<html>
<head><title>Pet Store Front Page</title></head>
<body topmargin="0" leftmargin="0" marginheight="0"
      marginwidth="0">
  <table width="100%" height="100%" border="0"
         cellspacing="0" cellpadding="0">
    <tr>
      <td align="center" valign="top" height="30">
        <img src="images/awning-top.gif" alt="awning">
      </td>
    </tr>
    <tr>
      <td align="center" valign="top">
        <img src="images/Name.gif" alt="Pet Store">
        <p style="margin-top: 40pt">
        <img src="images/lizard-front.jpg" alt="animal picture"
             height="186" width="280">
        <p><h2>Looking for a new friend?</h2>
        <p>Check out our <a href="PetCatalog.php">Pet
             Catalog.</a>
        <br> We may have just what you're looking for.
      </td>
    </tr>
  </table>
</body></html>
```

请注意，链接指向名为 `PetCatalog.php` 的 PHP 程序。当客户点击链接时，宠物目录程序（`PetCatalog.php`）开始运行。

## 显示宠物类型

宠物类型页面（参见图 11-2）向客户显示目录中当前所有宠物类型的列表。列表 11-2 显示了生成宠物类型网页的程序。

## 列表 11-2：显示宠物类型的程序

```php
<?php
  /* Program: PetCatalog.php
   * Desc:        Displays a list of pet categories from the
                 PetType table. Includes descriptions.
   *              User checks radio button.
   */
?>
<html>
<head><title>Pet Types</title></head>
<body>
<?php
  include("misc.inc");
```

## 列表 11-2（续）
