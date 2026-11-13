# Building the Flash

The Flash portion of this application is responsible for loading the data and looping through it to print each album. For simplicity, this application is all ActionScript, which means the display of the data is done in the Output panel.

A more complete application would take this loaded data and display it in a list or another custom data component.

The first step is to define the PHP file that will be called, which would look similar to this, depending on how your system is set up:

```
var phpFile:String = "http://localhost/getAlbums.php";
```

When the PHP variable is defined, the next step is to build the function that calls the server.

```
function loadHandler():void
{
... 
}
```

This function first sets up the URLRequest instance, passing the PHP variable as an argument.

```
var urlRequest:URLRequest = new URLRequest(phpFile);
```

The URLLoader is used to create an event listener and to start the loading process at the completion of this function. The urlRequest variable is passed in to the load function of the URLLoader class instance, which is required for any type of data loading.

```
var urlLoader:URLLoader = new URLLoader();
urlLoader.addEventListener(Event.COMPLETE, callServerHandler);
urlLoader.load(urlRequest);
```

The next function to define is the callServerHandler, which is called once the data is sent back from the PHP file written in the previous section. This function is passed an Event reference that contains the loaded data.

```
function callServerHandler(e:Event):void
{
... 
}
```

The first step in this function is to create the URLLoader instance, which is used to capture the loaded data. The event instance contains a target property, which is used here by passing it into a new URLLoader.

The result is stored in the local loader variable, which will be used in the remainder of this function.

```
var loader:URLLoader = URLLoader(e.target);
```