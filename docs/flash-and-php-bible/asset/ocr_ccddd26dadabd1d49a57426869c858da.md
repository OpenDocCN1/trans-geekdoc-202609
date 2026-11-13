# FIGURE 3.2

Here is the completed design of the sample application you will be working with.

![](bbox=[0.105, 0.178, 0.74, 0.56])

This function creates URLLoader and URLRequest instances. The phpFile is passed in to the URLRequest to create the object. Finally, the event listener is attached to the loader variable making reference to the serverResponse, which is the function that is called when the data is loaded.

```
function serverResponse(e:Event):void
{
   var loader:URLLoader = URLLoader(e.target);
   var variables:URLVariables = new URLVariables(loader.data);
   timeTxt.text = variables.returnValue;
}
```

The server handler function serverResponse() is responsible for capturing the data passed back from the PHP file. After that data is properly loaded, it is passed into the URLVariables class to generate a dynamic object.

This dynamic object holds the response data passed from the server, so a simple object call is all that is required to load the sample data. In this example, that sample data will be the UNIX timestamp captured and returned by PHP.

The last part is a simple button handler that calls the callServer function when a user clicks the button.