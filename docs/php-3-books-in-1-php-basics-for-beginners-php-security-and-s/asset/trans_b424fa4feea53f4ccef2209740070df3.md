
```
require_once('views/add/templates/body_addcarteProduct.html');
}
public function Footer()
{
require_once('views/add/templates/footer_addcarteProduct.html');
}
}
?>
```

现在只剩下将新模型和控制器的引用插入到 index.PHP 文件中的问题了：

```
<?PHP
ini_set('display_errors',1);
error_reporting(E_ALL);

//require the general classes
require("helperclasses/Interpreter.PHP");
require("helperclasses/BaseController.PHP");
require("helperclasses/Template.PHP");
require_once("helperclasses/Database.PHP");

//require the data model
require("models/CarteModel.PHP");

//require the model classes
require("models/show.PHP");
require("models/add.PHP");

//require the controller classes
require("controllers/show.PHP");
require("controllers/add.PHP");

//create the controller and execute the action
$interpreter = new Interpreter($_GET);
$controller = $interpreter->CreateController();

$controller->ExecuteAction();
?>
```

现在，我们可以通过用户界面将新的 Carte Product 添加到数据库中了。此外，我们还需要一种让用户将新的 Carte Product 分配给一个或多个可用 Carte 的方法，所以让我们来创建实现此功能的页面标记：

```
<html>
<head>
<title>Assign Carte Products to Cartes</title>
</head>
<body>
<form method="POST" action="index.PHP/assign/Save">
<table>
<tr><td>Select a Single Carte Product:</td></tr>
<tr>
<td>
<select name="carteProductid">
<option value="{carteProductid}">{Productname}</option>
</select>
</td>
```

```
<!-- body_assigncarteProduct1.html -->
<option value="{carteProductid}">{Productname}</option>
<!-- ------------ -->

<!-- body_assigncarteProduct2.html -->
</select>
</td>
</tr>
<tr><td>&nbsp;</td></tr>
<tr><td>Choose the Cartes you want to add the Carte Product to</td></tr>
<tr><td>
<select name="carteid" multiple="multiple">
<!-- ------------ -->

<!-- body_assigncarteProduct3.html -->
<option value="{carteid}">{cartename}</option>
<!-- ------------ -->

<!-- footer_assigncarteProduct1.html -->
</select>
</td>
</tr>
</table>
<br>
<br>
<input type="submit" value="UPDATE">
</form>
<br>
<br>
<br>
<br>
<br>
<center>
<table width="100%">
<tr>
<td><a href="index.PHP/show/Display">View Carte</a></td>
<td><a href="index.PHP/add/Display">Add New CarteProduct</a></td>
<td><a href="index.PHP/assign/Display">Assign Product to Carte</a></td>
</tr>
</table>
</center>
</body>
</html>
</body>
</html>
<!-- ------------ -->
```

现在，页脚中包含了指向“Assign CarteProduct to Carte”（将 CarteProduct 分配到 Carte）页面的链接。让我们首先为分配功能开发一个控制器，并将其保存到 controllers 目录下的 assign.PHP 文件中。

## Assign CarteProduct-to-Carte 功能的控制器

```
<?PHP
// controllers/assign.PHP

class Assign extends BaseController {
protected function Display() {
$viewmodel = new AssignModel();
$this->ReturnView($viewmodel->Display());
}
}
```

## Assign CarteProduct-to-Carte 视图的显示管理器

视图的 Display 类中相关的 Display() 方法将使用嵌套的 foreach 循环来解包来自 AssignModel 的层级数组，从而使数据能够按照伴随模板文件中所使用的标记语言推荐的方式显示。我们将像处理 Show 和 Add 功能那样，在 views/assign/Display.PHP 中创建一个 Display() 类，并将 AssignModel 打包好的数据传递给 Body() 方法，由该方法解包这些数据：

```
<?PHP

$display = new Display();
$display->Header();
$display->Body($viewmodel);
$display->Footer();

class Display{

public function Header()
{
require_once('views/assign/templates/header_assigncarteProduct.html');
}
public function Body($viewmodel)
{

$template_body1 = new Template();
$template_body1->file = "views/assign/templates/body_assigncarteProduct1.html";

foreach ($viewmodel as $selectlist)
{
foreach ($selectlist['carteProduct'] as $carteProduct)
{
$template_body1->set('carteProductid', $carteProduct->carteProductid);
$template_body1->set('Productname', $carteProduct->Productname);
$template_body1->display();
}
}

require('views/assign/templates/body_assigncarteProduct2.html');

$template_body3 = new Template();
$template_body3->file = "views/assign/templates/body_assigncarteProduct3.html";

foreach ($viewmodel as $selectlist)
{
foreach ($selectlist['carte'] as $carteid => $cartename)
{
$template_body3->set('cartename', $cartename);
$template_body3->set('carteid', $carteid);
$template_body3->display();
}
}
public function Footer()
{
require_once('views/assign/templates/footer_assigncarteProduct.html');
}
}
?>
```

我们在 Body() 方法中两次实例化了 Template 类的对象，因为我们将动态加载两个选择列表。Header()、Body() 和 Footer() 函数协同工作，创建一个包含数据库数据的完整视图。剩下的工作就是通过 index.PHP 文件将其集成到应用程序中，这需要模型和控制器文件：

```
```php
<?PHP
ini_set('display_errors',1);
error_reporting(E_ALL);

//require the general classes
require("helperclasses/Interpreter.PHP");
require("helperclasses/BaseController.PHP");
require("helperclasses/Template.PHP");
require_once("helperclasses/Database.PHP");

//require the data model
require("models/CarteModel.PHP");

//require the model classes
require("models/show.PHP");
require("models/add.PHP");
require("models/assign.PHP");

//require the controller classes
require("controllers/show.PHP");
require("controllers/add.PHP");
require("controllers/assign.PHP");

//create the controller and execute the action
$interpreter = new Interpreter($_GET);
$controller = $interpreter->CreateController();

$controller->ExecuteAction();

?>
```
```

最后，我们将添加编辑和删除 Carte Product 的功能。如果你查看 ModelCarte.PHP 文件中的 DBMapper 类，就会注意到我们已经构建了可用于修改现有数据库记录的 Erase() 和 Save() 方法。因此，我们的“Edit”控制器的 EditModel 类将需要调用这些 DBMapper 方法的方法，以及一个在模型和视图之间传递通信的 Display() 方法。

这一次，为了说明在给应用程序开发新功能时不必从视图开始，我们将根据之前对其需要执行操作的假设，先构建控制器。让我们首先向 BaseController 类添加 Display()、Save() 和 Erase() 方法。如果用户希望立即被重定向到 Edit 页面以确保编辑/删除操作成功，我们将在 Save() 和 Erase() 方法中提供重定向命令。

## Edit/Delete CarteProduct 功能的控制器

```
```php
<?PHP
// controllers/edit.PHP
```
```

```
```html
</head>
<body>
<table>
<tr>
<th>ID</th>
<th>Product Name</th>
<th>Description</th>
<th>Price</th>
<th>Serving Size</th>
<th>&nbsp;</th>
<th>&nbsp;</th>
<form method="POST" action="index.PHP/edit/Save">
<tr>
<td><input type="hidden" name="carteProductid" value="{carteProductid}">{carteProductid}</td>
<td><textarea cols="35" rows="1" name="Productname">{Productname}</textarea></td>
<td><textarea cols="55" rows="1" name="description">{description}</textarea></td>
<td><input type="text" name="price" value="{price}"></td>
<td><input type="text" name="servingsize" value="{servingsize}"></td>
<td><input type="submit" value="UPDATE"></td>
<td><a href="index.PHP/edit/Erase/{carteProductid}">DELETE</a></td>
</tr>
</form>
</table>
<br>
<br>
<center>
<table width="100%">
<tr>
<td><a href="index.PHP/show/Display">View Carte</a></td>
<td><a href="index.PHP/edit/Display">Edit Carte</a></td>
<td><a href="index.PHP/add/Display">Add New CarteProduct</a></td>
<td><a href="index.PHP/assign/Display">Assign Product to Carte</a></td>
</tr>
</table>
</center>
</body>
</html>
</body>
</html>
```
```

导航栏中有一个指向 Edit Carte 页面的链接。这个页脚部分应被复制并粘贴到其他视图的页脚部分中，以保持一致性。我们已经获取了键，并在上面的 HTML 中包含了 UPDATE 和 DELETE 控件。UPDATE 功能将用户所做的更改 POST 到 index.PHP，让 Edit 控制器处理 $_POST 数据。DELETE 功能加载 index.PHP 文件，并指示 Edit 控制器对 URL 提供的 carteProductid 调用 Erase() 方法。

## ***编辑 CarteProduct 功能的视图模板***

让我们将 Edit 视图的 HTML 拆分为三个模板文件，这些文件将保存到 views/edit/templates 目录中：

```
```html
<!-- HEADER TEMPLATE -->
<!-- header_editcarteProduct.html -->
<html>
<head>
<title>Edit Carte Products</title>
</head>
```
```

