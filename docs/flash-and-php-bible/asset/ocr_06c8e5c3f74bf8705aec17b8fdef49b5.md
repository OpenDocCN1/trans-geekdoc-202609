The list items load the body text when clicked, so create the function that handles this event. The ListEvent is passed from the ITEM_CLICK event, which contains the item property. The item property is where the data property is stored. In this example, that data is the RSS body, so you can simply pass that data directly to the feedBody TextArea.

```
```actionscript
function listClickhandler(e:ListEvent):void
{
    feedBody.htmlText = e.item.data;
}
```
```

The last function in the RSS application is the button handler, which is called any time the Button component is clicked. This function simply makes a call to the loadFeeds function.

```
```actionscript
function submitHandler(e:Event):void
{
    loadFeeds();
}
```
```

As you can see, the ActionScript is fairly simple for this example. XML really speeds up development of Web-enabled applications, and this is a perfect example of it.

Here is the RSS application code in its entirety for reference:

```
```actionscript
import fl.events.ListEvent;

var phpPath:String = "http://localhost/ch10/rssReader/";
var phpFile:String = phpPath + "rss.php";

function loadFeeds():void
{
    var urlRequest:URLRequest = new URLRequest(phpFile);
    var urlloader:URLLoader = new URLLoader();
    urlLoader.addEventListener(Event.COMPLETE, feedHandler);
    urlLoader.load(urlRequest);
}

function feedHandler(e:Event):void
{
    var loader:URLLoader = URLLoader(e.target);
    var xml:XML = new XML(loader.data);

    for each(var item in xml..entry)
    {
        topicsList.addItem({label:item.name, data:item.desc});
        topicsList.addEventListener(ListEvent.ITEM_CLICK,
            listClickhandler);
    }
}

function listClickhandler(e:ListEvent):void
```
```