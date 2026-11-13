
The service browser adds a text field for each argument; in this case there are three. Type a string in the first text field, choose one of the words from that string as the needle, and then enter that into the second TextField. Finally, type the replacement into the third text field. After all three text fields are filled in, you can click the Call button and see the output in the Results tab.

Assuming you use the string "hello world" with the needle of "world" and a replacement of "earth", you should see the following result. The word is replaced and the first letter of each word is capitalized using the upperCaseWords method.

```
"Hello Earth"
```

Now that you have thoroughly tested the AMFPHP services, you can move on to installing the necessary classes required for Flash to actually be able to make use of this setup. That process is explained in the next section.

## Using AMFPHP in Flash

Unlike previous versions, ActionScript 3 has all of the necessary classes for remoting and interacting with AMFPHP already installed. You simply load those Classes and write in the ActionScript, which is all fairly simple. This section walks you through the process of building a simple Flash application to better understand the process of working with AMFPHP in Flash.

### Loading the remoting classes

The first step to working with AMFPHP in Flash is to load the classes. This is required for any AMFPHP project you build as it contains the core of the remoting system.

```
import flash.net.*;
```

When the classes are loaded, you can define a variable that points to the AMFPHP gateway file.

```
var gatewayURL:String =
"http://localhost/flashservices/gateway.php";
```

The next step is to create the NetConnection instance, which is assigned to the gateway variable. At this point, you can also set up the method events that are called when a button is clicked.

```
var gateway:NetConnection;
getDateBtn.addEventListener(MouseEvent.CLICK, getDate);
searchBtn.addEventListener(MouseEvent.CLICK, searchAndReplace);
upperCaseWordsBtn.addEventListener(MouseEvent.CLICK, upperCaseWords);
debugTxt.wordWrap = false;
```

Here is the skeleton for the button handlers that will be created in the next portion. Each of these functions makes a call to the AMFPHP service.

```
function getDate(e:MouseEvent):void
{
    ...
}
function searchAndReplace(e:MouseEvent):void
{
    ...
}
function upperCaseWords(e:MouseEvent):void
{
    ...
}
```

The first method on which to focus is getDate, which will make a call to the server with no arguments and receives a string of the current date. The Responder class is used to handle the object response for both the success and failure calls.

```
var responder:Responder = new Responder(onResult, onFault);
```

The next portion of the function assigns a new instance of the NetConnection class. A call to the connect method is called passing in the gateway url variable. Once the connection is established, a call is made where the first argument is the service name and method. The second variable is a reference to the Responder class instance.

```
gateway = new NetConnection();
gateway.connect(gatewayURL);
gateway.call("Example.getDate", responder);
```

Here is the complete getDate function responsible for establishing the AMFPHP connection and calling the requested service.

```
function getDate(e:MouseEvent):void
{
    var responder:Responder = new Responder(onResult, onFault);

    gateway = new NetConnection();
    gateway.connect(gatewayURL);
    gateway.call("Example.getDate", responder);
}
```

The other two functions are very similar with the exception of the method name and arguments passed to the service.

The searchAndReplace function accepts three arguments.

- arg1: The string to search in
- arg2: The word to search for
- arg3: The replacement word

The service located in the AMFPHP setup is responsible for running the `searchAndReplace` method, but also makes a call to the `uppercase` method before returning the string.

```actionscript
function searchAndReplace(e:MouseEvent):void
{
    var responder:Responder = new Responder(onResult, onFault);
    
    gateway = new NetConnection();
    gateway.connect(gatewayURL);
    gateway.call("Example.searchAndReplace", responder,
        "hello world",
        "world",
        "earth"
    );
}
```

The final function is `upperCaseWords`, which takes one argument and returns a new string with the first letter of each word converted to uppercase. The rest of the function is the same as the previous two. This is a good example of AMFPHP being able to accomplish something that is not native to ActionScript, which, of course, is the uppercase portion.

```actionscript
function upperCaseWords(e:MouseEvent):void
{
    var responder:Responder = new Responder(onResult, onFault);
    
    gateway = new NetConnection();
    gateway.connect(gatewayURL);
    gateway.call("Example.upperCaseWords", responder, "hello
    world");
}
```

Once the three functions responsible for calling the services are defined, the next part is the debugging and result functions that are called when the service returns a valid response.

The `onResult` function is called when a successful message is received. In this simple example, the raw contents of the output are sent to the `TextArea` component located on the Stage. You can also replace the `TextArea` portion of the code with simple `trace()` statements for quicker testing.

```actionscript
function onResult(responds:Object):void
{
    debugTxt.text = "Response: " + responds;
}
```

If an error occurs, the `onFault` function is called, which contains the specific error. To better view the error, the contents of the object are run through a `for..in` loop, which displays each item. This function also clears the `TextArea` to ensure the old data is not mixed in, which could cause confusion while trying to debug an application.

The appendText method is the AS3 replacement to the "+=" way of concatenating strings in older versions of ActionScript. This method is much faster, which means quicker execution of code.

```
function onFault(responds:Object):void
{
    debugTxt.text = "";
    debugTxt.appendText("Debug : Error\n");
    for(var i in responds)
    {
    debugTxt.appendText(" " + responds[i] + "\n");
    }
}
```

Figures 9.4, 9.5, and 9.6 show example responses from sample applications within AMFPHP. You can expand on these examples to build a more complete application, which is done in the next section.

The first example is displaying the response from the getDate method of the sample AMFPHP classes. This example will return the current date in string format.

### FIGURE 9.4

Here is a sample response from the first AMFPHP service method.

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_229_0.png)

The second example accepts one argument and replaces the text. All of this is a simple example, showing the process of working with arguments in AMFPHP.

### FIGURE 9.5

Here is a sample response from the second AMFPHP service method.

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_230_0.png)

The third and final example is a carbon response. It basically takes the passed-in string and returns it exactly as it was sent.

### FIGURE 9.6

Here is a sample response from the third AMFPHP service method.

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_231_0.png)

## Building a Real-World Application Using AMFPHP

Now that you have seen AMFPHP service usage and how to implement it in Flash, you can continue by building a real-world application. A good example of a real-world application is a Flash-based album listing applications, which is explained in the next sections.

The database used for this example is the same one that is created in Chapter 2. If you haven't completed that chapter at this point, I recommend starting here.

### AMFPHP services

The AMFPHP services needed for this example are responsible for querying the database based on passed-in arguments. This also requires a database connection system that will need to be secure. This means methods will not be exportable or viewable by AMFPHP.
