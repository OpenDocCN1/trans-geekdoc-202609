
```php
{
require_once('views/edit/templates/header_editcarteProduct.html');
}
public function Body($viewmodel)
{
$template_body = new Template();
$template_body->file = "views/edit/templates/body_editcarteProduct.html";
foreach ($viewmodel as $carteProduct)
{
$template_body->set('carteProduct', $carteProduct->carteProduct);
$template_body->set('Productname', $carteProduct->Productname);
$template_body->set('description', $carteProduct->description);
$template_body->set('servingsize', $carteProduct->servingsize);
$template_body->set('price', $carteProduct->price);

$template_body->display();
}
}
public function Footer()
{
require_once('views/edit/templates/footer_editcarteProduct.html');
}
}

?>
```

现在，我们只需要使用对 controllers/edit.PHP 和 models/edit.PHP 文件的引用来更新 index.PHP 文件，我们就可以开始了：

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
require("models/edit.PHP");

//require the controller classes
require("controllers/show.PHP");
require("controllers/add.PHP");
require("controllers/assign.PHP");
require("controllers/edit.PHP");

//create the controller and execute the action
$interpreter = new Interpreter($_GET);
$controller = $interpreter->CreateController();

$controller->ExecuteAction();

?>
```

我相信我已经说明了这个 MVC 应用的范围。例如，你可以添加管理人员、销售票据和库存的功能。关键在于，使用这个框架，你可以快速添加数据库模式和数据模型，基于这种设计模式构建一个完整的餐厅管理系统，而不会干扰我们迄今为止所做的工作。

## 反射 API

![](img/232f65b1c63e7757b6150e92c9cc0d00_107_0.png)

PHP 反射 API 是一组函数集合，允许程序员轻松检查类和接口的内部结构。它使得确定镜像类是否定义了某个方法变得简单，或者类是否声明了指定的属性，以及该属性是 public、protected 还是 private。

```php
$dinner_Carte = new DinnerCarte;
$reflect_dinner_Carte = new ReflectionClass('DinnerCarte');
echo $reflect_dinner_carte->getName();
```

## 输出：

DinnerCarte

如上所示，DinnerCarte 是一个我在从原生的 "ReflectionClass" 类构建新的反射器对象之前作为示例构建的类。这是完整反射 API 构建的基础构建块。它接收要反射的类的名称作为输入参数。在上面的实例中，"ReflectionClass" 类的构造函数传递了文本 "DinnerCarte"。此过程返回一个包含有关类 "DinnerCarte" 的有用信息的反射器对象。

因为我只是讨论反射 API，前面的代码首先调用了一个名为 "getName()," 的方法，该方法返回被反射类的名称。虽然乍一看使用 Reflection 类的 getName() 方法可能是不必要的，因为被反射类的名称已经已知，但可能存在被反射类的名称未知的实例。在这种情况下

```
}
Method [ <internal:Reflection> public method getDocComment ] {
}
Method [ <internal:Reflection> public method getConstructor ] {
}
Method [ <internal:Reflection> public method hasMethod ] {
- Parameters [1] {
Parameter #0 [ <required> $title ]
}
}

Method [ <internal:Reflection> public method getMethod ] {
- Parameters [1] {
Parameter #0 [ <required> $title ]
}
}

Method [ <internal:Reflection> public method getMethods ] {
- Parameters [1] {
Parameter #0 [ <optional> $filter ]
}
}

Method [ <internal:Reflection> public method hasProperty ] {
- Parameters [1] {
Parameter #0 [ <required> $title ]
}
}

Method [ <internal:Reflection> public method getProperty ] {
- Parameters [1] {
Parameter #0 [ <required> $title ]
}
}

Method [ <internal:Reflection> public method getProperties ] {
- Parameters [1] {
Parameter #0 [ <optional> $filter ]
}
}

Method [ <internal:Reflection> public method hasConstant ] {
- Parameters [1] {
Parameter #0 [ <required> $title ]
}
}

Method [ <internal:Reflection> public method getConstants ] {
}

Method [ <internal:Reflection> public method getConstant ] {
- Parameters [1] {
Parameter #0 [ <required> $title ]
}
}

Method [ <internal:Reflection> public method getInterfaces ] {
}

Method [ <internal:Reflection> public method getInterfaceNames ] {
}
```

```
- Parameters [1] {
Parameter #0 [ <required> $interface ]
}
}

Method [ <internal:Reflection> public method getExtension ] {
}

Method [ <internal:Reflection> public method getExtensionName ] {
}
}
}
```

当你滚动浏览所有可访问的方法时，你会看到我们之前回顾过的 getName()、getConstant() 和 getConstants() 方法。自己简单尝试这些方法以更好地理解它们会很有用。它们可以成为单元测试中非常有用且有效的工具，正如你将看到的那样。

```
$ vi ~/.bash_profile
```

确保文件包含以下代码行：

```
PATH=/usr/local/bin:$PATH
```

为了让此修改立即生效，请保存文件并重新启动命令提示符。
然后我们将测试 pear 以查看其是否正常运行。

在终端中执行下面编写的代码：

```
which pear
```

> 上述命令必须响应：“/usr/local/bin/pear。”

## 更新 PHP include 路径

通过将 pear 引入 "/etc/PHP.ini 文件" 内的 PHP include 路径中，你可以告知 PHP PEAR 库的位置。

Mac 不包含上述文件。执行控制台中的相应提示以生成该文件：

```
$ sudo cp /etc/PHP.ini.default /etc/PHP.ini
```

然后，通过 vi 或 TextMate 更新 PHP include 路径。在 /etc/PHP.ini 中，查找以下代码：

```
;include_path = "/PHP/includes"
```

删除代码开头的“分号 ;”，然后将其替换为 PEAR 库路径。

```
include_path = "/usr/local/PEAR:/PHP/includes"
```

保存文件 /etc/PHP.ini。取消选中并重新选中“系统偏好设置/共享/网络共享”以重启 Apache Web 服务器。

然后，在网络浏览器中，导航到 http://localhost/[your user name]/index.PHP。查找 "include path" 并再次检查

路径包含 "/usr/local/PEAR。" 这是因为 PEAR 的安装

## 在 Linux 上安装 PEAR

PEAR 包应安装在用户定义的目标位置。这在 Linux 系统上通常如此，路径位于 usr 文件夹中，打开 local，然后是 lib，在 lib 中你会找到 PHP

在 cmd.exe 上写入此命令：

```
$ pear
```

```
//test_captcha.php --
<?php
require_once 'Text/CAPTCHA/Numeral.php';
$numcap = new Text_CAPTCHA_Numeral;

if (isset($_POST['captcha']) && isset($_SESSION['answer'])) {
if ($_POST['captcha'] == $_SESSION['answer']) {
$errors[] = 'success';
} else {
$errors[] = 'failed';
}
}
if (!empty($errors)) {
foreach ($errors as $error) {
print "$error";
}
}
print '
<form name="capter" action="test_captcha.php?page=example" method="post">
<table>
<tr>
<th>What is this result?: '.$numcap->getOperation().'</th>
<td><input type="text" value="" name="captcha"   /></td>
</tr>
<tr>
<th/>
<td><input type="submit" value="Verify I am Human"   /></td>
</tr>
</form>
';
$_SESSION['answer'] = $numcap->getAnswer();
?>
```
