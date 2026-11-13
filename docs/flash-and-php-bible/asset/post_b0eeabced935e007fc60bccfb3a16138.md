

increments the `failedAttempts` variable, but also determines if all future checks should be stopped based on the current failure count.

```
public function get attempts():uint
{
    return failedAttempts;
}

public function set attempts(num:uint):void
{
    if(num == undefined)
    {
        failedAttempts++;
    }
    else
    {
        failedAttempts = num;
    }

    if(failedAttempts == MAX_ATTEMPTS)
    {
        statusMC.gotoAndStop(1);
        stopChecking();
    }
}
```

If `failedAttempts` equals the `MAX_ATTEMPTS` constant, a call to `stopChecking()` is made and the status indicator moves to the first frame displaying a red circle.

At this point the `SiteMonitorItem` class is now complete and the Flash movie can be tested to ensure it works properly with the PHP code written before.

Following is the completed class file `SiteMonitorItem` that is attached to the movieclip of the same name:

```
package
{
    import flash.display.MovieClip;
    import flash.net.*;
    import flash.events.*;
    import flash.text.TextField;

    public class SiteMonitorItem extends MovieClip
    {

        public var phpFile:String;
        public var siteURI:String;

        private var stopCheck:Boolean = false;
        private var failedAttempts:uint = 0;
        private const MAX_ATTEMPTS:uint = 3;

        public function SiteMonitorItem() { }

        public function checkSite():void
        {
            var urlRequest:URLRequest = new URLRequest(siteURI);
            var urlLoader:URLLoader = new URLLoader();
            urlLoader.addEventListener(Event.COMPLETE, siteRespondedHandler);
            urlLoader.addEventListener(IOErrorEvent.IO_ERROR, noResponse);
            urlLoader.load(urlRequest);
        }

        private function noResponse(event:IOErrorEvent):void
        {
            attempts = attempts + 1;
        }

        private function siteRespondedHandler(e:Event):void
        {
            failedAttempts = 0;
        }

        private function stopChecking():void
        {
            stopCheck = true;
        }

        public function get attempts():uint
        {
            return failedAttempts;
        }

        public function set attempts(num:uint):void
        {
            if(num == undefined)
            {
                failedAttempts++;
            }
            else
            {
                failedAttempts = num;
            }

            if(failedAttempts == MAX_ATTEMPTS)
            {
                statusMC.gotoAndStop(1);
                stopChecking();
            }
        }
    }
}
```

## Using Flash to Develop a Video Player

Video players, such as the one illustrated in Figure 13.5, are becoming more and more popular as the Internet continues to get faster. The idea behind this section is to develop a video player that is interfaced with PHP to load in the video list, as well as keep track of the play count.

Flash already ships with a pretty versatile video player component, but you can still expand upon it, which is exactly what this section will help you achieve.

The application is constructed of a `VideoPlayer` and `ComboBox` component that has already been placed on the Stage. The start file ({START_FILE}) is provided so you can focus on the development and can quickly test as you go.

### FIGURE 13.5

A video player with a video loaded and playing

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_380_0.png)

NOTE You need an FLV video file in order to test this application. One is included with the source material found on the book's Web site.

Many of the applications you develop in Flash will consist of some ActionScript. The complexity of the ActionScript will be determined based on what the application will be. In this example you will be using an external class to develop the video player.

The first part of the application to be developed is the ActionScript code, which is broken up in classes for greater scalability. The main ActionScript will be attached to the application using the Document class.

To start, look at the class skeleton, which will give you a better idea of how the application will flow.

```
package
{
    public class VideoPlayer extends MovieClip
    {
        public function VideoPlayer() {
        }
        public function loadData():void {
        }

        private function dataLoaded(e:Event):void {}
        private function comboHandler(e:Event):void {}
    }
}
```

The constructor method of the Document class is responsible for assigning the VideoPlayer instance. It is also the point where the necessary event listeners are defined.

```
_player = this['player'];
this['videoListCombo'].addEventListener(Event.CHANGE, comboHandler);
```

The last part of the constructor method is to call the loadData method and gather the XML data.

```
loadData();
```

The loadData() method is for loading the video data, which is returned in XML format.

```
public function loadData():void
{
    var urlVariables:URLVariables = new URLVariables();
    urlVariables.a = "getvideos";

    var urlRequest:URLRequest = new URLRequest(phpFile);
    urlRequest.data = urlVariables;

    var urlLoader:URLLoader = new URLLoader();
    urlLoader.addEventListener(Event.COMPLETE, dataLoaded);
    urlLoader.load(urlRequest);
}
```

Here is a sample of the XML response, which has the attributes populated instead of nodes.

```
<videos>
<video name="Sample Video 1" src="color1.flv" playCount="7" />
<video name="Sample Video 2" src="color2.flv" playCount="3" />
<video name="Sample Video 3" src="color3.flv" playCount="5" />
<video name="Sample Video 4" src="color4.flv" playCount="4" />
<video name="Sample Video 5" src="color5.flv" playCount="1" />
<video name="Sample Video 6" src="color6.flv" playCount="2" />
</videos>
```

After the XML data object is loaded, a call to dataLoaded() is made, which is responsible for populating the ComboBox. A for..each loop is used to parse the video data, which is then added to the ComboBox component.

```
this['videoListCombo'].addItem({label:'Choose Video...', data:-1});
for each(var item in xml.video)
{
    var name:String = item.attribute('name');
    var src:String = item.attribute('src');
    this['videoListCombo'].addItem({label:name, data:src});
}
```

The last method of the Document class is an event handler for the ComboBox component.

```
private function comboHandler(e:Event):void
{
    if(e.target.selectedItem.data == -1) return;
    trace("Load Video: " + e.target.selectedItem.data);
    _player.source = 'videos/' + e.target.selectedItem.data;
}
```

This event handler method is used to load the video file, but only if a valid data value is found. A simple if statement is used to determine if the label is selected.

```
if(e.target.selectedItem.data == -1) return;
```

That is all there is to this class. Here is the completed Document class:

```
package
{
    import flash.display.MovieClip;
    import flash.events.*;
    import flash.net.URLVariables;
    import flash.net.URLRequest;
    import flash.net.URLLoader;
    import flash.media.Video;

    public class VideoPlayer extends MovieClip
    {
        public var phpFile:String =
            "http://localhost/ch12/VideoPlayer/videoManager.php";

        private var _player:FLVPlayback;

        public function VideoPlayer()
        {
            _player = this['player'];
            this['videoListCombo'].addEventListener(
                Event.CHANGE, comboHandler);
            loadData();
        }

        public function loadData():void
        {
            var urlVariables:URLVariables = new URLVariables();
            urlVariables.a = "getvideos";

            var urlRequest:URLRequest = new URLRequest(phpFile);
            urlRequest.data = urlVariables;

            var urlLoader:URLLoader = new URLLoader();
            urlLoader.addEventListener(Event.COMPLETE, dataLoaded);
            urlLoader.load(urlRequest);
        }

        private function dataLoaded(e:Event):void
        {
            var urlLoader:URLLoader = URLLoader(e.target);
            var xml:XML = new XML(urlLoader.data);

            this['videoListCombo'].addItem({
                label:'Choose Video...', data:-1});
            for each(var item in xml.video)
            {
                var name:String = item.attribute('name');
                var src:String = item.attribute('src');

                this['videoListCombo'].addItem({
                    label:name, data:src});
            }
        }

        private function comboHandler(e:Event):void
        {
            if(e.target.selectedItem.data == -1) return;
            trace("Load Video: " + e.target.selectedItem.data);
            _player.source = 'videos/' +
                e.target.selectedItem.data;
        }
    }
}
```

The next step is to develop the PHP code that is used to return an XML object. For this example,
the video data is a static array, but you can easily update it to use a MySQL database similar to the
previous examples.

```
$videos = array(
  array("Sample Video 1", "color.flv", 0),
  array("Sample Video 2", "color.flv", 0),
  array("Sample Video 3", "color.flv", 0),
  array("Sample Video 4", "color.flv", 0),
  array("Sample Video 5", "color.flv", 0),
  array("Sample Video 6", "color.flv", 0)
);
```

This example only has one action, which is to retrieve the video list and build an XML object to be
passed back to Flash.

```
if($action == "getvideos")
{
  $xml = "<videos>";
  for($i = 0; $i < count($videos); $i++)
  {
    $xml .= "<video>";
    $xml .= " name=\"" . $videos[$i][0] . "\"";
    $xml .= " src=\"" . $videos[$i][1] . "\"";
    $xml .= " playCount=\"" . $videos[$i][2] . "\"";
    $xml .= "/>\n";
  }
  $xml .= "</videos>";
}
```

After the XML object is created, a header type of XML is outputted; the last step is to output the
actual XML code.

```
header("Content-type: text/xml");
print $xml;
```

