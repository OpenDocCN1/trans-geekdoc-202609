This example uses a Document class to handle the majority of the loading and displaying process. In fact, the bulk of this class is similar to the previous example. If you completed that example you can copy those class files and make the changes as needed.

Here is the class skeleton, which will give you a better idea of how the class will work.

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

The first method is actually the constructor, which in this application handles the creation of a new container and also initializes the element array.

```
public function PhotoGallery()
{
    photos = new Array();
    photosContainer = new MovieClip();
    photosContainer.y = 75;
}
```

After the new movieclip is created, it needs to be added to the display list, and an event handler needs to be assigned to the Search button located on the Stage.

```
searchBtn.addEventListener(MouseEvent.CLICK, searchHandler);
addChild(photosContainer);
```

The next method to focus on is the searchHandler().When this method is called it first checks for a valid search term. If the value is valid, a call to remove the old images is made.

```
public function searchHandler(e:MouseEvent):void
{
    if(searchTxt.text.length > 0)
```