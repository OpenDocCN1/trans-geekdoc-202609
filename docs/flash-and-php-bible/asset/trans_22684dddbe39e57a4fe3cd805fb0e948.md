

public function loadThumb():void
{
   var thumbLoader:Loader = new Loader();
   var thumbURL:String = thumb;
   var thumbURLRequest:URLRequest = new URLRequest(thumbURL);
   thumbLoader.load(thumbURLRequest);
   thumbLoader.x = 10;
   addChild(thumbLoader);
}

最后一个方法用于返回在前面方法中填充的 BookItem 数据。

```
public function getValues():Object
{
   return {title:title, author:author, price:price};
}
```

至此，您已使用 PHP 和 Flash 完成了一个 Amazon 搜索应用程序。您也获得了关于 AWS 系统的大量信息，并且应该跃跃欲试，构建自己的支持 Web 服务的应用程序。

几个可构建的潜在项目包括 CD 搜索应用程序、流派匹配系统，甚至是一个使用本地 iTunes 或类似音乐播放器的库来构建您已听音乐的可视化云的图库。查看本书的网站，了解使用 Amazon AWS 系统构建的其他应用程序示例。

## 使用 flickr 开发照片库

照片库是一个非常流行的应用程序，通常使用 Flash 构建。它提供了一种非常独特的方式来展示您的作品，或者在某些情况下被用作信息传递应用程序，例如在游戏和新闻网站上。

在本节中，您将学习使用 Yahoo 提供的 flickr 照片服务开发照片库。Flash 应用程序将调用 PHP，PHP 将与 flickr Web 服务交互，最后将数据返回给 Flash 进行显示。

在开始开发应用程序之前，请注册 flickr API 密钥，这是一个两步过程。第一步是访问 www.flickr.com/signup/ 注册页面创建 flickr 帐户。

一旦您有了 flickr 帐户，请访问 www.flickr.com/services/api/keys/apply/ 申请 API。

如果您选择“非商业”选项，您的请求将几乎立即获得授权。

此示例使用 Document 类来处理大部分加载和显示过程。实际上，此类的大部分内容与前面的示例相似。如果您完成了那个示例，可以复制那些类文件并根据需要进行更改。

这是类骨架，它将让您更好地了解类的工作原理。

```
package
{
    import flash.display.MovieClip;
    import flash.events.*;
    import flash.net.*;

    public class PhotoGallery extends MovieClip
    {
        public var webServiceURL:String;
        private var photos:Array;
        private var photosContainer:MovieClip;

        public function PhotoGallery() {}
        public function searchHandler(e:MouseEvent):void {}
        public function loadSearchResults(terms:String):void {}
        public function loadedResultsHandler(e:Event):void {}

        private function removeOldPhotos():void {}
    }
}
```

第一个方法实际上是构造函数，在此应用程序中，它处理新容器的创建，并且还初始化元素数组。

```
public function PhotoGallery()
{
    photos = new Array();
    photosContainer = new MovieClip();
    photosContainer.y = 75;
}
```

创建新的电影剪辑后，需要将其添加到显示列表中，并且需要为舞台上的 Search 按钮分配事件处理程序。

```
searchBtn.addEventListener(MouseEvent.CLICK, searchHandler);
addChild(photosContainer);
```

接下来要关注的方法是 searchHandler()。调用此方法时，它首先检查是否有有效的搜索词。如果值有效，则调用删除旧图像。

```
public function searchHandler(e:MouseEvent):void
{
    if(searchTxt.text.length > 0)
    {
        removeOldPhotos();
        loadSearchResults(searchTxt.text);
    }
}
```

下一个方法用于调用 PHP，PHP 负责与 flickr 交互。tags 变量从搜索处理程序传入，并通过 GET 请求发送到 PHP。

```
public function loadSearchResults(tags:String):void
{
    var urlVariables:URLVariables = new URLVariables();
    urlVariables.tags = tags;

    var urlRequest:URLRequest = new URLRequest(webServiceURL);
    urlRequest.data = urlVariables;

    var urlLoader:URLLoader = new URLLoader();
    urlLoader.addEventListener(Event.COMPLETE,
        loadedResultsHandler);
    urlLoader.load(urlRequest);
}
```

PHP 被配置为返回一个 XML 结果集，它是 flickr 返回内容的精简版本。这与 Amazon 示例非常相似，因为 Web 服务往往会返回大量对于此类应用程序不需要的信息。

XML 数据首先加载到 XML 对象中，以便能够正确解析。一旦创建了 XML 对象，它将运行 for..each 循环以提取每个 photo 节点。

```
public function loadedResultsHandler(e:Event):void
{
    var urlLoader:URLLoader = URLLoader(e.target);
    var xml:XML = new XML(urlLoader.data);

    for each(var item in xml..photo)
    {
        ...
    }
}
```

使用每个 photo 节点，您需要创建一个 PhotoItem 实例， flickr 图像将在此处加载。可以将此实例视为每个图像的容器。此实例也是存储图像数据以供将来使用的地方。

```
var photoItem:PhotoItem = new PhotoItem();
photoItem.setValues(item..title, item..thumb);
```

创建新的 `PhotoItem` 实例后，需要在容器中对齐它。该位置通过获取 photos 数组的长度并将其乘以新 `photoItem` 的高度来确定。然后将该值增加 50 像素，以允许缩略图间距。

```
photoItem.y = (photos.length * (photoItem.height + 50));
```

另一种更优雅的解决方案是创建一个事件处理程序，在图像加载后对齐照片。这提供了支持多种尺寸图像并更具动态性的能力。

此方法的最后一项任务是将新实例添加到 photos 数组中，最后显示它。

```
photos.push(photoItem); photosContainer.addChild(photoItem);
```

每次执行新搜索时，都会调用 `removeOldPhotos` 方法。该方法负责删除现有图像并确保数据不会交叉。

```
private function removeOldPhotos():void
{
    if(photos.length > 0)
    {
        photos = new Array();
        removeChild(photosContainer);
        photosContainer = new MovieClip();
        photosContainer.y = 75;
        addChild(photosContainer);
    }
}
```

此方法设置为 private，以便其他代码不会意外删除图像。如果您想允许外部删除图像，可以创建一个检查某些授权级别的委托方法。如果请求有效，则允许删除图像。

现在 `Document` 类已完成，下一个要创建的类是 `PhotoItem`。此类保存从 flickr 加载的每个图像的信息。它还负责加载缩略图并将实例定位到舞台上。

```
package
{
    import flash.display.MovieClip;
    import flash.text.TextField;
    import flash.display.Loader;
    import flash.net.URLRequest;

    public class PhotoItem extends MovieClip
    {
        private var title:String;
        private var thumb:String;

        public function PhotoItem() { }
    }
}
```

创建此类的新实例时，将调用 setValues 来存储图像数据。此方法接受两个参数：title 和缩略图路径。这两个变量都存储在私有变量中，因此不会意外访问和修改。

```
title = t;
thumb = i;
```

加载数据后，标题将附加到电影剪辑中位于的 titleTxt 组件。标题也会移出，以便为缩略图腾出空间。

```
titleTxt.text = title;
titleTxt.x = 100;
```

最后一步是调用 loadThumb 方法。

```
loadThumb();
```

loadThumb 方法负责加载在 XML 文档中找到的图像。

```
public function loadThumb():void
{
var thumbLoader:Loader = new Loader();
var thumbURL:String = thumb;
var thumbURLRequest:URLRequest = new URLRequest(thumbURL);
thumbLoader.load(thumbURLRequest);
thumbLoader.x = 10;
addChild(thumbLoader);
}
```

最后一个方法负责传回图像信息。

```
public function getValues():Object
{
return {title:title};
}
```

您可能已经注意到，缩略图加载器与图书搜索示例中使用的代码相同。您可能还注意到，本书中加载器代码非常相似。这应该告诉您，应该构建一个类来处理这一任务，简单的导入将替换应用程序中重复的十行代码。

对于较小的应用程序，这其实不太明显，但如果您正在开发大型项目，则会很明显。第 9 章将更详细地介绍类可重用性。但基本上，当您能够使某物模块化时，最好这么做。

