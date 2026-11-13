```
function resetHandler(e:MouseEvent):void
{
    bodyTxt.text = storedFileData;
}
```

The last method needed in this application is responsible for saving the edited content. Before the data is saved, it is cached, which eliminates the need to reload the data.

```
function saveHandler(e:MouseEvent):void
{
    var body:String = bodyTxt.text;
    storedFileData = body;
    ...
}
```

The variables passed to the PHP define the action, the name of the file, and raw contents that will replace the existing file data. The name of the file is gathered from the ComboBox by accessing the selectedItem object.

```
var variables:URLVariables = new URLVariables();
variables.file = filelistCombo.selectedItem.data;
variables.action = "save";
variables.fileContents = body;
```

This particular URLRequest does not require an event listener because the saving process happens on its own and is completed once PHP receives all of the fileContents.

NOTE In a remote application it is a good idea to notify the user of the saving process because a large file may take time to save.

```
var urlRequest:URLRequest = new URLRequest(phpFile);
urlRequest.data = variables;
```

```
var urlLoader:URLLoader = new URLLoader();
urlLoader.load(urlRequest);
```

The last task of the ActionScript is to register the events for the buttons and make a call to the populateFileList() function to prefill the file ComboBox.

```
// Register Events
loadFileBtn.addEventListener(MouseEvent.CLICK, loadFile);
saveBtn.addEventListener(MouseEvent.CLICK, saveHandler);
resetBtn.addEventListener(MouseEvent.CLICK, resetHandler);
populateFileList();
```