```
variables.subject = subjectStr;
variables.msg = messageStr;

var urlRequest:URLRequest = new URLRequest(phpFile);
urlRequest.method = URLRequestMethod.POST;
urlRequest.data = variables;

var loader:URLLoader = new URLLoader();
loader.addEventListener(Event.COMPLETE, sendHandler);
loader.load(urlRequest);
}
```

```
function sendHandler(e:Event):void
{
var loader:URLLoader = URLLoader(e.target);
var variables:URLVariables = new URLVariables(loader.data);

if(variables.resultCode == "SENT")
{
 // message sent
 form.statusTxt.htmlText = "<font color=\"#009933\">Email"+
 " sent, thank you.</font>";
}
else if(variables.resultCode == "ERROR")
{
 // message not sent
 form.statusTxt.htmlText = "<font color=\"#FF0000\">Email"+
 " not sent, please try again.</font>";
}
else
{
 // unknown response
 form.statusTxt.htmlText = "<font color=\"#FF0000\">Unknown"
 + " ERROR</font>";
}
}
form.sendBtn.addEventListener(MouseEvent.CLICK, sendMessage);
```

The focus of this section will be on the sendMessage and sendHandler functions. The sendMessage function assigns the variables that are passed to the PHP, instantiates the necessary Classes, and sets up the event listeners.

```
function sendMessage(e:MouseEvent):void
{
...

var variables:URLVariables = new URLVariables();
variables.name = nameStr;
variables.subject = subjectStr;
variables.msg = messageStr;
```