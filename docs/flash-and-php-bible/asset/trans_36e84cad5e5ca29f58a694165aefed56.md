
->Item[$i]->ItemAttributes->ListPrice
->FormattedPrice . "]]></price>";
$xml .= "<t\t<thumb>" . $xmlResponse->Items->Item[$i]
 ->SmallImage->URL . "</thumb>";
$xml .= "</book>";

**注意** 生成 XML 的数据是每个 $xml 变量一行；换行是为了适应此页面，这可能会破坏你的代码。

本示例中 PHP 的最后一部分会创建一个头部类型，以便 XML 读取器了解正在发送的格式，然后将其输出到屏幕上。

```
header ("content-type: text/xml");
print $xml;
```

该应用程序所需的 Flash (ActionScript) 全部位于外部类中。这么做是因为这样更易于日后管理和维护。

**交叉引用** 如果你需要更深入地了解类，我强烈建议你阅读第 9 章。

此应用程序的 Flash 文件 (FLA) 包含一个带有搜索框和按钮的简单设计。主类 BookSearch 被指定为文档类，负责管理整个应用程序。以下是类骨架，可让你了解创建此应用程序所使用的方法和属性。

```
package
{
import flash.display.MovieClip;
import flash.events.*;
import flash.net.*;

public class BookSearch extends MovieClip
{
public var webServiceURL:String;
private var bookItems:Array;
private var bookItemsContainer:MovieClip;

public function BookSearch() {}

public function searchHandler(e:MouseEvent):void {}

public function loadSearchResults(terms:String):void {}

public function loadedResultsHandler(e:Event):void {}

private function removeOldResults():void {}
}
}
```

构造方法用于初始化数组、创建容器影片剪辑，并向搜索按钮添加事件监听器。

```
public function BookSearch()
{
    bookItems = new Array();
    bookItemsContainer = new MovieClip();
    bookItemsContainer.y = 100;
    searchBtn.addEventListener(MouseEvent.CLICK, searchHandler);
}
```

构造方法的最后一步是将新的书籍容器添加到显示列表中，从而使其可见。

```
public function BookSearch()
{
    bookItems = new Array();
    bookItemsContainer = new MovieClip();
    bookItemsContainer.y = 100;
    searchBtn.addEventListener(MouseEvent.CLICK, searchHandler);
    addChild(bookItemsContainer);
}
```

接下来要关注的方法是 searchHandler()。当用户单击搜索按钮时会调用此方法。调用此方法时，它首先会检查搜索框中数据的长度，以确保能进行有效搜索。如果值长度有效，则会调用删除旧搜索结果的操作。

```
public function searchHandler(e:MouseEvent):void
{
    if(searchTxt.text.length > 0)
    {
        removeOldResults();
        loadSearchResults(searchTxt.text);
    }
}
```

一旦找到有效的搜索词，下一步就是设置并调用 PHP，该 PHP 负责与 AWS 交互。本示例中使用的调用与之前的示例非常相似。首先设置变量对象，将其分配给 URLRequest，创建一个新的加载器实例，最后分配一个事件监听器。

```
public function loadSearchResults(terms:String):void
{
    var urlVariables:URLVariables = new URLVariables();
    urlVariables.terms = terms;

    var urlRequest:URLRequest = new URLRequest(webServiceURL);
    urlRequest.data = urlVariables;

    var urlLoader:URLLoader = new URLLoader();
    urlLoader.addEventListener(Event.COMPLETE,
    loadedResultsHandler);
    urlLoader.load(urlRequest);
}
```

你可能已经注意到此方法已设为 public。这么做是为了让其他应用程序可以使用搜索功能，因为这就是可重用性的含义。当然，如果你允许其他人直接调用此方法，那么你很可能还需要放置另一个术语检查，以确保不会发送错误数据。

Web 服务器返回数据后，会将其发送到 loadedResultsHandler() 方法。响应以 XML 格式发送，使用 for..each 循环逐个提取元素，并将其发送到唯一的 BookItem 类实例。

```
var xml:XML = new XML(urlLoader.data);

for each(var item in xml.book)
...
```

BookItem 引用库中的一个影片剪辑。此影片剪辑预先填充了虚拟条目，这些条目会在显示到舞台上之前用实际数据填充。

```
var bookItem:BookItem = new BookItem();
bookItem.setValues(
item.title,
item.author,
item.price,
item.thumb
);
bookItem.y = (bookItems.length * (bookItem.height + 30));
bookItems.push(bookItem);
bookItemsContainer.addChild(bookItem);
```

完成的事件处理程序如下：

```
public function loadedResultsHandler(e:Event):void
{
var urlLoader:URLLoader = URLLoader(e.target);
var xml:XML = new XML(urlLoader.data);

for each(var item in xml.book)
{
var bookItem:BookItem = new BookItem();
bookItem.setValues(
item.title,
item.author,
item.price,
item.thumb
);

bookItem.y = (bookItems.length * (bookItem.height + 30));
bookItems.push(bookItem);
bookItemsContainer.addChild(bookItem);
}
}
```

文档类的最后一个方法用于删除现有的书籍项实例。每次新搜索开始时都会调用此方法，以确保数据不会意外堆积。

```
private function removeOldResults():void
{
if(bookItems.length > 0)
{
bookItems = new Array();
removeChild(bookItemsContainer);
bookItemsContainer = new MovieClip();
bookItemsContainer.y = 100;
addChild(bookItemsContainer);
}
}
```

方法的第一部分会检查是否有有效条目，因为应用程序第一次运行时舞台上不会有现有产品。

```
if (bookItems.length > 0)
{
...
}
```

如果存在现有项，则会创建一个新数组来清除现有对象。然后，使用 removeChild 清除旧容器并创建一个新容器。这么做是为了释放资源并删除现有产品。

```
bookItems = new Array();
removeChild(bookItemsContainer);
bookItemsContainer = new MovieClip();
```

最后一步是将新的书籍容器添加到显示列表中，具体做法是调用 addChild() 并将容器的新实例作为参数传递。

```
addChild(bookItemsContainer);
```

现在你可以继续创建 BookItem 类，该类用于添加到舞台上的每个产品。它负责存储产品数据并加载书籍缩略图。

在开始开发类之前，最好先查看类骨架，如之前的示例所示。这样做能让你更好地理解其预期工作方式。

```
package
{
    import flash.display.MovieClip;
    import flash.text.TextField;
    import flash.display.Loader;
    import flash.net.URLRequest;

    public class BookItem extends MovieClip
    {
        public function BookItem() { }
        public function setValues(t:String, a:String, p:String,
        i:String):void {}
        public function loadThumb():void {}
        public function getValues():Object {}
    }
}
```

大多数类中的第一个方法是构造方法，这个类也不例外，只不过这个构造方法是空的。下一个方法是 setValues，负责存储传递的值。这些值将是从 Amazon 检索到的书籍数据。你也可以将此信息作为对象传递，但就本示例而言，使用独立变量更易于理解。

```
public function
setValues(t:String,a:String,p:String,i:String):void
{
    title = t;
    author = a;
    price = p;
    thumb = i;

    titleTxt.text = title;
    authorTxt.text = author;
    priceTxt.text = price;

    loadThumb();
}
```

存储完所有变量后，会调用 loadThumb，它负责检索书籍封面的缩略图。使用 Loader 类时，可以将其传递给 addChild，这样就不需要事件监听器了，更重要的是，它会自行加载，因为书籍封面不是必需的。你还可以创建一个可视化加载器来告知用户正在加载内容。方法的其余部分只是一个标准的 URLRequest，这应该与之前的示例中你所熟悉的一样。
