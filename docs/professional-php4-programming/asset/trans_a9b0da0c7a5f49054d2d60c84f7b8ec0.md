

这段代码中有许多错误，要么会导致无法解析，要么更糟的是，虽然能运行但行为不正常。在前三行中，我们未能设置 $car 对象的 $requiredKey 成员，因为构造函数并未执行此操作。

直到我们真正启动汽车时才需要密钥，因此这不会导致错误。所以代码的前几行看起来一切正常。顺便提一下，让我们看看构建 Engine 对象的那一行。如果我们改写成 $car->Engine = new Engine() 会怎样呢（注意单词 Engine 中的大写 "E"）？汽车将无法启动，因为发动机也不会被初始化。当然，你可以很容易地捕捉到这些错误，但它们本就不应该发生。接下来我们尝试启动汽车：

```php
$car->speed = 400; // should have been $car->setSpeed(400); to cause
                // a failure
$car->start($myKey);
```

当汽车启动时，它会向前行驶并加速到 400km/h。这可能会引发事故，导致道路上（或道路外）许多人丧生。这显然不是我们想要看到的。

另外，汽车如何知道启动所需的密钥类型？它将把我们正确构造的密钥与一个根本不存在的变量进行比较（结果为 0），最终无法启动发动机。这样的比较会绕过解释器检查，因为检查相等性的是输入 $key，而不是成员。对于汽车车主来说，买下新车却发现经销商提供的钥匙根本无法使用，这相当奇怪。让我们看看如果将发动机设置为 0 来停止汽车时会发生什么：

```php
$car->engine = 0;
$car->stop();
```

当调用 stop() 方法时，我们会遇到运行时错误，因为 Engine 对象根本不存在，我们将其强制设置为整数值 0。正如你所见，从类外部设置成员可能会导致很多问题。在一个项目中有多名程序员协作的世界里，你必须预期其他人会阅读，并且很可能使用你的代码。

那么从这个例子中我们学到了什么教训？在对象外部使用成员（对象违规）会：

- 破坏对象提供的服务将按预期工作的保证。
- 以以下任一方式破坏对象数据成员（或对象状态）的完整性：
  - 违反数据规则
  - 避免初始化成员
- 创建比实际需要更复杂的接口。
- 增加程序员的负担，让他们需要记住更多关于对象及其数据与服务交互方式的内容。
- 当需要复用对象时，你可能不得不再次修改成员。有时，出于健忘，你会在下一个项目中创建新错误。这正是我们想要避免的。

一个经验法则是设计你的类，使其拥有完成你打算对对象进行的所有操作的服务。永远不要访问类外部的成员，并且始终正确封装你的类，以获益于信息隐藏。有些语言提供了将成员设为仅类私有（或受保护）以完全禁止访问成员的能力。目前 PHP 没有此功能，但遵循良好的编码实践肯定有帮助。

## 继承

现在我们已经讨论了面向对象程序的基本构建块以及一些良好的经验法则，让我们开始利用面向对象为我们提供的功能，以帮助创建解决复杂问题的整洁策略。

假设我们想要组织和管理一个类似 amazon.com 的互联网媒体商店。我们可能想要销售光盘、软件、VHS、DVD 以及图书。在使用传统的函数式编程时，我们可能希望创建一个传统结构来保存这些媒体数据，如下所示：

| 媒体 |
|---|
| ID |
| 名称 |
| 类型 |
| 库存 |
| 价格 |
| 评级 |

显然，图书、电影、CD 和软件之间存在许多差异，因此我们可能希望创建一些额外的结构来存储特定媒体类型的数据。

| CD | 软件 | 电影 | 图书 |
|---|---|---|---|
| 序列号 | 序列号 | 序列号 | ISBN |
| 艺术家 | 出版商 | 时长 | 作者 |
| 曲目数量 | 平台 | 导演 | 页数 |
| 曲目名称 | 要求 | 演员 | |
| | | 类型 (dvd/vhs) | |

现在，如果我们想要编写一个程序，将数组中的所有媒体项打印到屏幕上，我们会这样做：

```php
<?php
// create a small array filled with 2 records
$mediaItems = array();
$books   = array();
$cds     = array();

$item->id    = 1;
$item->type  = "book";
$item->name  = "Professional PHP 4";
$item->inStock = 33;
$item->price = 49.95;
```

```php
$item->rating = 5;
$mediaItems[] = $item;

$book->isbn      = 1246534343443;
$book->author    = "Ken Egervari, et. al. ";
$book->numberOfPages = 500;
$books[$item->id] = $book;

$item->id        = 2;
$item->type      = "cd";
$item->name      = "This Way";
$item->inStock   = 120;
$item->price     = 16.95;
$item->rating    = 4;
$mediaItems[] = $item;

$cd->serialNo    = 323254354;
$cd->artist      = "Jewel";
$cd->numberOfTracks = 13;
$cds[$item->id] = $cd;

// Display the media items to the screen
foreach ($mediaItems as $item) {
    echo("Name: " . $item->name . "<br>");
    echo("Items in stock: " . $item->inStock . "<br>");
    echo("Price: " . $item->price . "<br>");
    echo("Rating: " . $item->rating . "<br>");

    switch ($item->type) {
    case 'cd' :
        echo("Serial No: " . $cds[$item->id]->serialNo . "<br>");
        echo("Artist: " . $cds[$item->id]->artist . "<br>");
        echo("# of Tracks: " . $cds[$item->id]->numberOfTracks . "<br>");
        break;

    case 'software' :
        // echo software specific items
        break;

    case 'movie' :
        // echo movie specific items
        break;

    case 'book' :
        // echo book specific items
        break;
    }
}
```

如果我们要添加另一种媒体类型怎么办？我们必须回到这段代码中，在 switch 语句中添加另一个 case 块，并且可能还要更新程序中的其他各处（我们可能会有许多类似的代码）。OOP 提供了一种称为 **继承** 的功能，我们可以将类似类型对象的细节放在各自的位置，并将相似之处汇总到基对象中。借助此功能，我们可以完全避免使用 switch 语句。

在我们的媒体商店示例中，我们可以将所有媒体类型之间的相似之处封装在一个媒体对象中。这个对象被称为 **基类**、**父类** 或 **超类**。它形成了最抽象的实现（数据和方法），适用于我们稍后想要包含的任何媒体项。以下是 Media 类的虚构实现：

```php
<?php
define("MIN_RATING", 0);
define("MAX_RATING", 5);

// Media.php
class Media
{
    var $id;
    var $name;
    var $inStock;
    var $price;
    var $rating;

    function Media($id, $name, $inStock, $price, $rating)
    {
        if ($inStock < 0) $inStock = 0;
        if ($price < 0) $price = 0;
        if ($rating < MIN_RATING) $rating = MIN_RATING;
        if ($rating > MAX_RATING) $rating = MAX_RATING;

        $this->id = $id;
        $this->name = $name;
        $this->inStock = $inStock;
        $this->price = $price;
        $this->rating = $rating;
    }

    function buy()
    {
        $this->inStock--;
    }

    function display()
    {
        echo("Name: " . $this->name . "<br>");
        echo("Items in stock: " . $this->inStock . "<br>");
        echo("Price: " . $this->price . "<br>");
        echo("Rating: " . $this->rating . "<br>");
    }

    // more methods
}
?>
```

现在我们有了基类，可以使用 `extends` 关键字来继承 Media 类的属性，并添加一些与特定媒体项（如图书或电影）相关的专用成员和方法。父类的专用类称为 **子类** 或 **派生类**。以下是 Media 类的 Book 子类。其余类可以以类似方式实现。

