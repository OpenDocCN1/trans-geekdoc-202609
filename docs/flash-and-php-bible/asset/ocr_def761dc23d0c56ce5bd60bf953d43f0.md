```
urlRequest.data = urlVariables;

var urlLoader:URLLoader = new URLLoader();
urlLoader.addEventListener(Event.COMPLETE,
loadedResultsHandler);
urlLoader.load(urlRequest);
});
```

You might have noticed this method has been made public. This is done so other applications can use the searching ability, because that is what reusability is all about. Of course, if you allow others to call this method directly, you would most likely want to place another term check to make sure bad data isn’t going to be sent.

Once the Web server returns the data, it is sent to the loadedResultsHandler() method. The response is sent in XML format and, using a for..each loop each element is pulled out and sent to a unique BookItem class instance.

```
var xml:XML = new XML(urlLoader.data);

for each(var item in xml.book)
...
```

The BookItem is referencing a movieclip in the library. This movieclip is prefilled with dummy entries that are populated with the real data before they are displayed on the Stage.

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

The completed event handler follows:

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
```