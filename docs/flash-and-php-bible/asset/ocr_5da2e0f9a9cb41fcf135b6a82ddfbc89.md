```
import flash.display.MovieClip;
import flash.text.TextField;
import flash.events.Event;
import flash.events.MouseEvent;
```

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

# VideoListItem constructor

The constructor in this class simply sets the alpha of the item to 50 percent, but because alpha is a 0 to 1 value, the 50 percent is actually 0.5.

```
function VideoListItem()
{
    alpha = 0.5;
}
```

# setItem method

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
```