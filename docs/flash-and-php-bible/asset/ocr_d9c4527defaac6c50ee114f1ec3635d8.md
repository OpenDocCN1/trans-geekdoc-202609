```
if(id == -1) return;
selectedCatID = id;
trace("Load Category ID: " + id);
getVideos();
}
```

```
public function getVideos():void
{
var responder:Responder =
new Responder(videosResHandler, onFault);
gateway = new NetConnection();
gateway.connect(gatewayURL);
gateway.call("Videos.getVideos",
responder,
selectedCatID,
''
);
}
```

```
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
```