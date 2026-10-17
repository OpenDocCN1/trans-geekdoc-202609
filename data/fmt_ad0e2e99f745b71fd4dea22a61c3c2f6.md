
我们通过在 `use` 句中列出它们使用了两个不同的日志 trait。由于每个 trait 都实现了相同的 `logmessage()` 方法，我们必须指定使用哪一个。如果我们不指定，PHP 将生成致命错误，因为它无法解决冲突。

你可以使用 `insteadof` 关键字来指定使用哪一个，如下例所示：
`fileLogger::logmessage insteadof sysLogger;`

这一行显式地告诉 PHP 使用 `fileLogger` trait 中的 `logmessage()` 方法。然而，在这种情况下，我们也希望访问 `sysLogger` trait 中的 `logmessage()` 方法。为了实现这一点，我们使用该关键字对其重命名，如下：
`sysLogger::logmessage as private logsysmessage;`

该方法现在可以作为 `logsysmessage()` 方法使用了。注意，在这个特定的示例中，我们还更改了方法的可见性。这不是必须的，但在这里展示是为了让你看到这是可能的。

你甚至可以更进一步，构建包含或完全由其他 trait 组成的 trait。要做到，可以在 trait 内部使用 `use` 语句，就像在类内部使用一样。

## 设计类

现在你已经了解了对象和类背后的一些概念以及在 PHP 中实现它们的语法，是时候看看如何设计实用的类了。

你代码中的许多类将代表真实世界对象的类或类别。在 Web 开发中，你可能使用的一些类示例包括页面、用户界面组件、购物车、错误处理、产品分类和客户。

你代码中的对象也可以代表上述类的实例——例如，首页、某个特定的按钮，或者 Fred Smith 在特定时间正在使用的购物车。Fred Smith 可以由类型为 `customer` 的对象表示。Fred 购买的每件物品都可以表示为一个对象，属于某个类别或类。

在上一章中，你使用了简单的包含文件（include files）让虚构公司 TLA Consulting 在你网站的不同页面上具有整洁的外观和感受。使用类和继承节省时间的能力，你可以创建相同内容的更高级版本。

现在，你希望能够为 T 快速创建外观和行为都相同的页面。你应该应该能够修改这些页面以适应网站的不同部分。

出于本示例的考虑，你将创建一个 `Page` 类。该类的主要目标是限制页面页面之间变化的部分，同时自动生成保持不变的元素。该类应该为创建新页面提供一个灵活的框架，并且不应牺牲你的自由。

由于你是通过脚本而不是静态 HTML 生成页面，你可以向其中添加任何数量的内容，包括功能：

- 允许你仅在一处更改页面。如果你更改了版权声明或额外的页脚，你需要在单个页面中进行更改。
- 为面的大部分部分提供默认内容，但根据需要可以修改每个元素，为标题和元标签（metatags）设置自定义值。

## 为你的类编写代码

- 识别正在查看哪个页面并修改导航元素以适应；在首页上设置一个带你回到首页的按钮是没有意义的。
- 允许你为特定页面替换标准元素。例如，如果你希望在网站的不同区域有不同的导航按钮，你应该能够替换标准的按钮。

## 为你的类编写代码

在决定了你希望代码输出成什么样以及你希望它具备的一些功能后，你如何实现它？在书的后半部分，我们将讨论大型项目的设计和项目管理。现在，我们集中在编写面向对象的 PHP 的特定部分。

类需要一个逻辑名称。因为它代表一个页面，你可以将其命名为 `Page`。声明一个名为 `Page` 的类，输入：

```php
class Page
{}
```

类需要一些属性。对于这个示例，将你可能希望从页面到页面更改的元素设置为类的属性。页面的主要内容（HTML 的组合）是 `$content`。你可以在类定义中声明内容：

```php
public $content;
```

你还可以设置属性来存储页面的标题。你可能需要更改标题以显示访问者正在查看哪个页面。你可以提供：

```php
public $title = "TLA Consulting Ltd";
```

大多数商业网页使用元标签（metatags）帮助搜索引擎索引它们。为了有用，元标签应该从页面到页面变化。再次，你可以提供默认值：

```php
public $keywords = "TLA Consulting, Three Letter Abbreviation, of best are search engines";
```

页面上显示的导航按钮应该保持相同，为了方便更改它们，由于按钮的数量可能是变量，你可以使用数组并存储它们指向的 URL：

```php
public $buttons = array(
"Home" => "home.php",
"Contact" => "contact.php",
"Services" => "services.php",
"Site Map" => "map.php"
);
```

为了提供某些功能，类还需要操作。你可以开始通过提供访问器函数来设置和获取属性值：

```php
public function __set($name, $value)
{
    $this->$name = $value;
}
```

`__set()` 函数不包含错误检查（为了简洁），但这种功能可以根据需要轻松添加。由于你不可能从类外部请求这些值，你可以选择不提供 `__get()` 函数，如所示。

该类的主要目的是显示页面，所以你需要一个函数。我们将其命名为 `Display()`，它如下：

```php
public function Display()
{
    echo "<html><head>\n";
    $this->DisplayTitle();
    $this->DisplayKeywords();
    $this->DisplayStyles();
    echo "</head><body>\n";
    $this->DisplayHeader();
    $this->DisplayMenu($this->buttons);
    echo $this->content;
    $this->DisplayFooter();
    echo "</body>\n</html>\n";
}
```

该函数包含了一些显示 HTML 的语句，但主要由对其他函数的调用组成。正如你可能猜到的，这些其他函数显示页面的部分。

这样拆分函数不是强制的。所有这些独立的函数都可以合并成一个大函数。我们拆分它们是有若干原因的。

每个函数应该有一个定义的任务。这个任务越简单，编写和测试该函数就越容易。不要做得过头；如果你将程序拆分成过多的小单元，它将难以阅读。

使用继承，你可以覆盖操作。当你替换一个大型 `Display()` 函数时，你不可能想更改整个页面的显示方式。将显示拆分为几个自包含的任务，并能够覆盖你想要更改的部分将要好得多。

列表 6.1 显示了完整的类，保存为 `page.php`，可在其他文件中通过 `include` 或 `require` 引入。

### 列表 6.1 page.php—Page 类提供了一种简单灵活的创建 TLA 页面的方法

```php
<?php
class Page
{
    // Page 类的属性
    public $content;
    public $title = "TLA Consulting Pty Ltd";
    public $keywords = "TLA Consulting, Three Letter Abbreviation, 
    some of my best friends are search engines";
    public $buttons = array("Home" => "page.php",
        "Contact" => "contact.php",
        "Services" => "services.php",
        "Site Map" => "map.php");
    // Page 类的操作
    public function set($name, $value)
    {
        $this->name = $value;
    }
    public function Display()
    {
        echo "<html><head>\n";
        $this->DisplayTitle();
        $this->DisplayKeywords();
        $this->DisplayStyles();
        echo "</head>\n<body>\n";
        $this->DisplayHeader();
        $this->DisplayMenu($this->buttons);
        echo $this->content;
        $this->DisplayFooter();
        echo "</body>\n<html>\n";
    }
    public function DisplayTitle()
    {
        echo "<title>" . $this->title . "</title>";
    }
    public function DisplayKeywords()
    {
        echo "<meta name='keywords' content='" . $this->keywords . "'/>";
    }
}
```

### 第 6 章 面对象 PHP

```php
public function DisplayStyles()
{
  <link href="styles.css" type="text/css" rel="stylesheet">
  <?php
}
```

```php
public function DisplayHeader()
{
  <!-- page header --
  <header>
    <img src="logo.gif" alt="TLA logo" height="70" width="70" />
    <h1>TLA Consulting</h1>
  </header>
  <?php
}
```

```php
public function DisplayMenu($buttons)
{
  echo "<!-- menu -->";
  <nav>
    while (list($name, $url) = each($buttons)) {
      $this->DisplayButton($name, $url,
        $this->IsUrlCurrentPage($url));
    }
echo "</nav>";
}
```

```php
public function IsUrlCurrentPage($url)
{
  if (strpos($_SERVER['PHP_SELF'],$url)==false) {
    return false;
  } else {
    return true;
  }
}
```

```php
public function DisplayButton($name, $url, $active=true)
{
  if ($active) {
    <div class="menuitem">
      <a href="<?php$url?>"
```

### 编写你的类的代码 181

```php
<img src="s-logo.gif" alt="" height="20" width="20" />
<span class="menutext"><?php=$name?></span></span>
</div>
</div>
<?php
} else { (
  <div class="menutem">
    <img src="side-logo.gif">
    <span class="menutext"><?php=$name?></span>
  </div
<?php
}
public function DisplayFooter() {
  <!-- page footer --
  <footer>
    <p>&copy; TLA Consulting Pty Ltd. /</p>
    Please see our
    <a href="legal.php">legal information page</a>a.</p>
    </footer>
  <?php
}
```

在阅读此类时，请注意 `DisplayStyles()`、`DisplayHeader()` 和 `DisplayFooter()` 需要显示大段的静态 HTML，不需要经过 PHP 处理。因此，你只需要在函数内部使用 PHP 结束标签（`?>`）、你的 HTML，然后通过开启标签（`<?php`）重新进入 PHP。

该类中还定义了另外两个操作。操作 `DisplayButton()` 输出单个菜单按钮。如果按钮指向你当前所在的页面，将显示一个非活动状态的按钮，它看起来略有不同且不链接任何内容。这样，你可以保持页面布局的一致性，并为访问者提供视觉定位。

操作 `IsUrlCurrentPage()` 确定按钮的 URL 是否指向当前页面。你可以使用几种技术来查看此信息。在这里，你使用字符串函数 `strpos()` 来检查 URL 是否包含在服务器变量中。语句 `strpos($_SERVER['PHP_SELF'], $url)` 如果 `$url` 中的字符串包含在全局变量 `$_SERVER['PHP_SELF']` 中，则返回一个数字，否则返回 `false`。

要使用此 `Page` 类，你需要在脚本中包含 `page.php` 并调用 `Display()`。

182 第 6 章 面对象 PHP

列表 6.2 中的代码创建了 TLA Consulting 的页面，并输出与之前图 5.2 生成类似的输出。列表 6.2 中的代码执行了以下操作：

- 1. 使用 `require` 包含 `page.php` 的内容，其中包含了 `Page` 类的定义。
- 2. 创建 `Page` 类的实例。该实例名为 `$homepage`。
- 3. 为页面设置内容，包括一些文本和 HTML 标签。
- 4. 调用 `Display()` 生成输出。

### 列表 6.2 home.php—此页面使用了大部分工作量

```php
<?php
require("page.php");
$homepage = new Page();
$homepage->content = "<section>
<h2>Welcome to TLA Consulting.</h2>
<p>At TLA Consulting, we offer a number of services. 也许如果我们重新重新工程了你们的业务，你们员工的生产力可能会提高。也许你们的业务需要一份全新的使命宣言，或者一批新的流行术语。</p></section>";
$homepage->Display();
?>
```

你从列表 6.2 中看到，生成页面只需要非常少的工作。因为你希望网站与众不同，你使用了继承来创建一个继承自 `Page` 的新类。这意味着你想要更改，但你只重写你修改过的部分。

214

### 列表 6.3 services.php—服务页面继承自 Page 但重写了 Display()

```php
<?php
require("page.php");
class ServicesPage extends Page {
    private $rowbuttons = array(
        "Re-engineering" => "reengineering.php",
        "Standards Compliance" => "standards.php",
        "Buzzword Compliance" => "buzzword.php",
        "Mission Statements" => "mission.php"
    );
    public function Display() {
        echo "<html><head>\n";
        $this->DisplayTitle();
        $this->DisplayKeywords();
        $this->DisplayStyles();
        echo "</head><body>\n";
        $this->DisplayHeader();
        $this->DisplayMenu($this->buttons);
        $this->DisplayMenu($this->rowbuttons);
        echo $this->content;
        $this->DisplayFooter();
        echo "</body></html>\n";
    }
}
$services = new ServicesPage();
$services->content = "<<p>At TLA Consulting, we offer a number of services. 也许如果我们重新工程了你们的业务，你们员工的生产力可能会提高。也许你们的业务需要一份全新的使命宣言，或者一批新的流行术语。</p>";
$services->Display();
?>
```
