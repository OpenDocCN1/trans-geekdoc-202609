The service browser adds a text field for each argument; in this case there are three. Type a string in the first text field, choose one of the words from that string as the needle, and then enter that into the second TextField. Finally, type the replacement into the third text field. After all three text fields are filled in, you can click the Call button and see the output in the Results tab.

Assuming you use the string "hello world" with the needle of "world" and a replacement of "earth", you should see the following result. The word is replaced and the first letter of each word is capitalized using the upperCaseWords method.

```
"Hello Earth"
```

Now that you have thoroughly tested the AMFPHP services, you can move on to installing the necessary classes required for Flash to actually be able to make use of this setup. That process is explained in the next section.

# Using AMFPHP in Flash

Unlike previous versions, ActionScript 3 has all of the necessary classes for remoting and interacting with AMFPHP already installed. You simply load those Classes and write in the ActionScript, which is all fairly simple. This section walks you through the process of building a simple Flash application to better understand the process of working with AMFPHP in Flash.

# Loading the remoting classes

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
```