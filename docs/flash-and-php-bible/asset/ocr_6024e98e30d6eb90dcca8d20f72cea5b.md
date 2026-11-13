Either way, the variable passed in to Flash is “resp”. This way you can easily program the ActionScript to handle the response accordingly.

The reason that you use isset( ) in the first if statement is so PHP can’t accidentally send a notice to Flash alerting the variable is not sent. This sort of application is a very good candidate for XML, which is explained in depth in Chapter 3. XML would make it so only the value you are interested in would be returned. For this simple example, you will continue with a standard print-based return.

Now that you have the PHP in place you can move on to the ActionScript. The ActionScript makes a call to the PHP and expects a cookie or error to be returned.

```
```actionscript
var phpFile:String =
	"http://localhost/ch05/cookies/loadCookie.php";

var variables:URLVariables = new URLVariables();
variables.act = 'getcookie';
variables.cookieName = 'sample';

var urlRequest:URLRequest = new URLRequest(phpFile);
urlRequest.method = URLRequestMethod.POST;
urlRequest.data = variables;

var loader:URLLoader = new URLLoader();
loader.addEventListener(Event.COMPLETE, serverHandler);
loader.load(urlRequest);

function serverHandler(e:Event):void
{
	var loader:URLLoader = URLLoader(e.target);
	var variables:URLVariables = new URLVariables(loader.data);

	if(variables.resp == 'cookie_not_found')
	{
		trace("Requested Cookie Not Found");
	}
	else
	{
		trace("Cookie Data: " + variables.resp);
	}
}
```
```

The overall call to the server is similar to other calls in this book. The focus on this call is the variables passed to the PHP and the response. You use the URLVariables class to assign the act and cookieName variables. The act variable tells PHP that your request is valid, and the cookieName variable contains the name of the cookie you are looking for.

```
```actionscript
var variables:URLVariables = new URLVariables();
variables.act = 'getcookie';
variables.cookieName = 'sample';
```
```