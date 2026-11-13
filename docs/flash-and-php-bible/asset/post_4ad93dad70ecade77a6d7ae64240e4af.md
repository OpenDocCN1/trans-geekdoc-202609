
import flash.display.MovieClip;
import flash.text.TextField;
import flash.events.Event;
import flash.events.MouseEvent;

The class also needs to have some default properties defined, which will be modified later in the class. Most of the properties are basic string definitions. However, the last property, ITEM_CLICK, is a special public constant that is used in the event handler. This is made public so that the variable can be accessed outside of the class.

```
public var videoObj:Object;

private var _id:uint;
private var _title:String;
private var _desc:String;
private var _thumb:String;
private var _src:String;

public static const ITEM_CLICK:String = "onItemClick";
```

## VideoListItem constructor

The constructor in this class simply sets the alpha of the item to 50 percent, but because alpha is a 0 to 1 value, the 50 percent is actually 0.5.

```
function VideoListItem()
{
    alpha = 0.5;
}
```

## setItem method

The first custom method in this class is setItem. This method is called on the creation of a new instance and sets the id, thumb, and video source parameters. For this example, the thumb option is not used, but you can expand the example because it has already been added.

```
function setItem(id:uint, thumb:String, src:String)
{
    _id = id;
    _thumb = thumb;
    _src = src;
}
```

The second part of the setItem method assigns the event listeners for the mouse object. This is also where you enable the mouse pointer icon when the user rolls the mouse over the video item.

```
function setItem(id:uint, thumb:String, src:String)
{
    _id = id;
    _thumb = thumb;
    _src = src;

    buttonMode = true;
    useHandCursor = true;
    addEventListener(MouseEvent.ROLL_OVER, overHandler);
    addEventListener(MouseEvent.ROLL_OUT, outHandler);
    addEventListener(MouseEvent.CLICK, clickHandler);
}
```

## Mouse handler methods

The mouse handler methods are used to modify the alpha value of the video item. In this example, they basically set the alpha to fully visible or partially visible. You could easily add a tween to this property and have the alpha property smoothly change.

```
private function overHandler(e:MouseEvent):void
{
	e.currentTarget.alpha = 1.0;
}
```

```
private function outHandler(e:MouseEvent):void
{
	e.currentTarget.alpha = 0.5;
}
```

The clickHandler method fires the ITEM_CLICK event that alerts any listening objects of the click. In this case, the event would notify the VideoPlayer and that specific video would be loaded.

```
private function clickHandler(e:MouseEvent):void
{
	dispatchEvent(new Event(ITEM_CLICK));
}
```

The remaining methods in the VideoListItem class are for getting and setting the properties previously defined. For example, the title can be retrieved by calling get title, such as:

```
public function get title():String
{
	return _title;
}
```

You can also set the title property by calling set title and passing in the title of the video.

```
public function set title(val:String):void
{
	_title = val;
	titleTxt.text = val;
}
```

## Defining the getter and setter methods

The remaining getter/setter methods appear in the following code and also are in the completed class available in the book's source code:

```
public function get id():uint
{
    return _id;
}

public function get source():String
{
    return _src;
}

public function get desc():String
{
    return _desc;
}
public function set desc(val:String):void
{
    _desc = val;
    descTxt.text = val;
}
```

That is all there is to the VideoListItem class. As you can see, it is mostly self-contained, which makes this little object reusable in other applications. In this example, you are building a video player, but you could easily change that to a product viewer, document viewer, or anything else you can think of.

Here is the completed VideoListItem class, which you can study or simply copy and paste it from the book's Web site.

```
package
{
    import flash.display.MovieClip;
    import flash.text.TextField;
    import flash.events.Event;
    import flash.events.MouseEvent;

public class VideoListItem extends MovieClip
{

    public var videoObj:Object;

    private var _id:uint;
    private var _title:String;
    private var _desc:String;
    private var _thumb:String;
    private var _src:String;

    public static const ITEM_CLICK:String = "onItemClick";

    function VideoListItem()
    {
        alpha = 0.5;
    }

    function setItem(id:uint, thumb:String, src:String)
    {
        _id = id;
        _thumb = thumb;
        _src = src;

        buttonMode = true;
        useHandCursor = true;
        addEventListener(MouseEvent.ROLL_OVER, overHandler);
        addEventListener(MouseEvent.ROLL_OUT, outHandler);
        addEventListener(MouseEvent.CLICK, clickHandler);
    }

    private function overHandler(e:MouseEvent):void
    {
        e.currentTarget.alpha = 1.0;
    }

    private function outHandler(e:MouseEvent):void
    {
        e.currentTarget.alpha = 0.5;
    }

    private function clickHandler(e:MouseEvent):void
    {
        dispatchEvent(new Event(ITEM_CLICK));
    }

    public function get id():uint
    {
        return _id;
    }

    public function get source():String
    {
        return _src;
    }

    public function get title():String
    {
        return _title;
    }
    public function set title(val:String):void
    {
        _title = val;
        titleTxt.text = val;
    }
    public function get desc():String
    {
        return _desc;
    }
    public function set desc(val:String):void
    {
        _desc = val;
        descTxt.text = val;
    }
}
}
```

At this point you have completed the Flash and PHP video player. You can now test the application, and you will see the same interface you started with. The difference is, if you select a category, the ScrollPane will be populated with the videos from that category.

You can then click on a video item and that video will begin to play. As it stands, the video player is a pretty robust application that can be expanded.

In the next section you will do just that by adding some basic tracking. Then, in a later section, you add a user login component that results in a truly real-world application while maintaining the original functionality the player has now.

## Working with Video Tracking

In the previous section, you built a complete Flash-based video player that has PHP allowing for a dynamic result. This application allows the owner to simply update the database, and the Flash application reflects those updates the next time it loads.

A problem comes in when the owner wants to know which videos are popular. You want the project to help him determine which video content is popular so he can add more of that similar content.

The solution is to develop video tracking that logs how many times a video has been viewed. This is done by having a column in the database that holds the active count. You then add the necessary support to the PHP classes and finally update the Flash to display the count.

The database does not need to be updated because the count column was added in the previous section even though it wasn’t used. Adding more columns than you will use to start is common so the application has the ability to grow. Extra columns may also be a result of temporarily removing a feature from an application after the database schema is created.

## Updating the video class

The videos service class was created in the previous section. All you have to do now is add the new method used to modify the video count:

```
public function updatePlayCount($vid)
{
	$link = $this->getConnection();
	...
}
```

This method accepts one parameter, which is an id referencing the video that should be updated. The first part of this method creates a link to the database using the existing database class you built in the previous section. This $link variable is passed into all future SQL actions in this method.

The second part of the method is to create an SQL query that grabs the current play count of the desired video.

```
public function updatePlayCount($vid)
{
	$link = $this->getConnection();

	$query = sprintf("SELECT count FROM videos WHERE id=%d", $vid);
	$result = mysql_query($query, $link);
}
```

## Checking for valid records

After the value is loaded, the next step is to check for a valid record using the familiar mysql_num_rows function.

```
public function updatePlayCount($vid)
{
	$link = $this->getConnection();

	$query = sprintf("SELECT count FROM videos WHERE id=%d", $vid);
	$result = mysql_query($query, $link);

	if(mysql_num_rows($result) > 0)
	{
		...
	}
}
```
