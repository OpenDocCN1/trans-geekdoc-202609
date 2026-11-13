```
```
for each(var item in xml.photo)
{
    images.push({name:'', src:item.attribute('src')});
    ...
}
```
```

Here is the object by itself and an alternative, more readable method of creating the object.

```
```
{ name:'', src:item.attribute('src') }
```
```

Here is the alternative method to define the object.

```
```
var obj:Object = new Object();
obj.name = '';
obj.src = item.attribute('src');
```
```

The last task of the imagesLoaded function is to set the currentImage variable and make a call to the displayImage function passing the image source. The image source is loaded from the images array using currentImage as the array index.

```
```
function imagesLoaded(e:Event):void
{
    ...
    currentImage = 0;
    displayImage(images[currentImage].src );
}
```
```

Here is the complete imagesLoaded function:

```
```
function imagesLoaded(e:Event):void
{
    var loader:URLLoader = URLLoader(e.target);
    var xml:XML = new XML(loader.data);
    images = new Array();
    for each(var item in xml.photo)
    {
        images.push({name:'', src:item.attribute('src')});
    }
    currentImage = 0;
    displayImage(images[currentImage].src );
}
```
```

With the categories and images loaded, you can display the image. This is done by assigning a URLRequest built of the image directory, current category id, and the photo's name. The loader class is placed directly into an addChild call, which handles the displaying of the image once it is fully loaded. You won't notice any loading time locally, but you might online.