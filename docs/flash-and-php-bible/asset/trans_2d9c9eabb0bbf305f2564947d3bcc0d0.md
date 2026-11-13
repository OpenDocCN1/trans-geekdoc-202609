

## getVideos 方法

当找到有效类别时，会调用 getVideos 方法。此方法用于向远程服务发起初始调用，该服务将根据先前方法中存储的类别加载正确的视频列表。

此方法与 getCategories 方法的唯一不同之处在于传递给 call 方法的参数以及分配给 Responder 的成功函数。

```
public function getVideos():void
{
    var responder:Responder = new Responder(
        videosResponseHandler,
        onFault
    );

    gateway = new NetConnection();
    gateway.connect(gatewayURL);
    gateway.call("Videos.getVideos", responder, selectedCatID, '');
}
```

您可以创建一个主连接处理程序并传入这些不同的属性，但为了简单起见，使用了多个方法。

## videosResponseHandler 方法

该应用程序中最大的方法之一必然是 videosResponseHandler。

```
private function videosResponseHandler(response:Object):void
{
    ...
}
```

这是因为该方法负责加载视频列表，并用自定义 VideoListItem 资源填充 ScrollPane 组件。这些资源可以在此项目的 Flash 库中找到，因为它们已经为您完成。稍后在本项目中，您将开发附加到这些资源上的 ActionScript。

此方法的第一部分是定义 nextY 变量，以偏移每个视频列表项并创建一个空 MovieClip，该 MovieClip 将分配给 ScrollPane 实例的 source 属性。

```
var nextY:uint = 5;

var listItem:MovieClip = new MovieClip();
videoList.source = listItem;
```

此方法的大部分内容位于 for..each 循环中。该循环遍历视频列表响应中的每个项目。

```
for each(var item in response)
{
    ...
}
```

循环的每次迭代都会创建一个新的 `VideoListItem` 实例。这些实例会被分配一个事件处理程序，并使用先前定义的 `nextY` 变量在列表中获得唯一的位置。

```
var videoListItem:MovieClip = new VideoListItem();
videoListItem.y = nextY;
videoListItem.x = 2;

videoListItem.addEventListener(VideoListItem.ITEM_CLICK,
    listItemHandler);
```

循环的下一部分设置 `videoListItem` 的自定义属性，用于定义点击项时要加载的标题、描述和视频。

```
videoListItem.title = item.name;
videoListItem.desc = item.description;
videoListItem.videoObj = item;
videoListItem.setItem(item.vid, ' ', item.src);
```

现在 `VideoListItem` 实例已完成，下一步是将其添加到 `listItem` 显示列表中，从而使其在 `ScrollPane` 中可见。

```
listItem.addChild(videoListItem);
```

循环的每次迭代都会递增 `nextY` 变量，以确保每个视频项位于唯一位置。该值是通过将当前视频项的高度加上一点内边距添加到现有 `nextY` 变量来确定的。

```
nextY += videoListItem.height + 2;
```

`videosResponseHandler` 方法的最后一步是通过调用 `update` 方法来刷新 `ScrollPane` 组件。如果不调用此方法，`ScrollPane` 中的滚动条将不会反映添加的视频项。

```
videoList.update();
```

可以看出，`videosResponseHandler` 方法负责视频列表中的许多功能，尽管它只是整个应用程序的一部分。要正确创建它确实需要大量自定义代码。

## listItemHandler 方法

每当 `ScrollPane` 中的任何视频项被单击时，都会调用 `listItemHandler` 方法。

```
private function listItemHandler(e:Event):void
{
... 
}
```

此方法更新视频播放器下方 videoMetaInfo MovieClip 中的当前视频信息。

```
videoMetaInfo.titleTxt.text = e.currentTarget.videoObj.name;
videoMetaInfo.categoryTxt.text = e.currentTarget.videoObj.cat;
videoMetaInfo.viewsTxt.text = e.currentTarget.videoObj.count;
videoMetaInfo.descTxt.text =
e.currentTarget.videoObj.description;
```

它还负责替换视频播放器的源并播放新视频。

```
videoPlayer.visible = true;
videoPlayer.source = e.currentTarget.source;
videoPlayer.play();
```

## 处理远程响应中的错误

VideoPlayer 类的最后一个方法是远程服务错误的处理程序。除非您希望以不同方式处理每个错误，否则此方法不需要是唯一的。我倾向于在开发期间显示错误内容，因为，如您可能记得，PHP 中的 trigger_error 调用会返回用户错误消息。

```
private function onFault(responds:Object):void
{
    trace("Debug:Error");
    for(var i in responds)
    {
        trace(" " + responds[i]);
    }
}
```

对于此应用程序，错误消息在开发期间被跟踪，在实际运行时被完全忽略。本章稍后，您将创建一个类似于流行视频共享网站上所见的现实错误处理程序。

您现在已完成整个 VideoPlayer 类，它是视频应用程序的大部分，至少对于项目的 ActionScript 部分而言是如此。

以下是 VideoPlayer 类的完整内容，以便您轻松查看每个方法如何相互交互。此源代码也可在本书的网站上供您剪切和粘贴。

```
package
{
    import flash.display.MovieClip;
    import flash.events.Event;
    import flash.net.*;

    public class VideoPlayer extends MovieClip
    {
        private var gatewayURL:String;
        private var gateway:NetConnection;
        private var selectedCatID:Number;

        function VideoPlayer()
        {
            gatewayURL = "http://localhost/amfphp/gateway.php";
            getCategories();

            videoPlayer.visible = false;
            videoListCombo.enabled = false;
        }

        public function getCategories():void
        {
            var responder:Responder =
                new Responder(categoryRespHandler, onFault);

            gateway = new NetConnection();
            gateway.connect(gatewayURL);
            gateway.call("Categories.getCategories", responder);
        }

        private function categoryRespHandler(response:Object):void
        {
            videoListCombo.enabled = true;
            videoListCombo.addItem(
                {label:'Choose a Category...', data:-1}
            )
            for each(var item in response)
            {
                videoListCombo.addItem(
                    {label:item.name, data:item.id}
                );
            }

            videoListCombo.addEventListener(Event.CHANGE,
                categoryHandler);
        }

        private function categoryHandler(e:Event):void
        {
            var id:Number = e.currentTarget.selectedItem.data;

            if(id == -1) return;
            selectedCatID = id;
            trace("Load Category ID: " + id);
            getVideos();
        }

        public function getVideos():void
        {
            var responder:Responder =
                new Responder(videosRespHandler, onFault);
            gateway = new NetConnection();
            gateway.connect(gatewayURL);
            gateway.call("Videos.getVideos",
                responder,
                selectedCatID,
                ''
            );
        }

        private function videosRespHandler(response:Object):void
        {
            var nextY:uint = 5;
            var listItem:MovieClip = new MovieClip();
            videoList.source = listItem;
            for each(var item in response)
            {
                var videoListItem:MovieClip =
                    new VideoListItem();
                videoListItem.addEventListener(
                    VideoListItem.ITEM_CLICK,
                    listItemHandler
                );
                videoListItem.y = nextY;
                videoListItem.x = 2;
                videoListItem.title = item.name;
                videoListItem.desc = item.description;
                videoListItem.videoObj = item;
                videoListItem.setItem(item.vid, '', item.src);
                listItem.addChild(videoListItem);
                nextY += videoListItem.height + 2;
                videoList.update();
            }
        }

        private function listItemHandler(e:Event):void
        {
            var info:Object = e.currentTarget.videoObj;
            videoMetaInfo.titleTxt.text = info.name;
            videoMetaInfo.categoryTxt.text = info.cat;
            videoMetaInfo.viewsTxt.text = info.count;
            videoMetaInfo.descTxt.text = info.description;

            videoPlayer.visible = true;
            videoPlayer.source = e.currentTarget.source;
            videoPlayer.play();
        }

        // Error Handler
        private function onFault(responds:Object):void
        {
            trace("Debug:Error");
            for(var i in responds)
            {
                trace(" " + responds[i]);
            }
        }
    }
}
```

## 构建 VideoListItem 类

在您测试应用程序之前，下一步是构建 VideoListItem 类。如果您尝试以当前形式运行应用程序，您不仅会收到错误，而且还将无法加载任何视频，因为目前这些项无法单击。

第一步是在您喜欢的编辑器中创建一个新的 ActionScript 文件。将此文件保存为 VideoListItem.as，保存到与 FLA 文件相同的目录中。创建文件后，您需要构建类文件的骨架，它需要扩展 MovieClip 类，因为它附加到库中的 MovieClip 实例。

```
package
{
   import flash.display.MovieClip;
   public class VideoListItem extends MovieClip
   {
   }
}
```

除了导入 MovieClip 类之外，您还必须导入其他一些类，以便正确开发此类。这些其他类处理视频项实例的文本、事件和鼠标部分。

