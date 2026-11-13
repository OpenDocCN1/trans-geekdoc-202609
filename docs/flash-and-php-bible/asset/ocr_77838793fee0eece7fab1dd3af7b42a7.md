```
catch (e:Error)
{
    // handle error here
}
```

Here is a sample request that would be sent to the server. As you can see, the Content and POST elements have the information that was sent. The remaining parts of the request are standard data attributes and are not specific to this example.

```
POST /callLink.php HTTP/1.1
Accept-Language: en
Accept-Encoding: gzip, deflate
Cookie: login=usernames;session-id=1206701
Referer: http://www.example.org/
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en)
AppleWebKit/522.11.1 (KHTML, like Gecko) Version/3.0.3
Safari/522.12.1
**Content: id=1004%2Fuser=James**
Content-Type: application/x-www-form-urlencoded
Accept: text/xml, text/html;q=0.9, text/plain;q=0.8, image/png
Pragma: no-cache
Content-Length: 327
Connection: keep-alive
Host: www.example.org
```

# Two-way communication

In some cases, you will want to receive a response when you send data. One would be when attempting to load a specific user's data from a database. You would pass a user id and expect to receive some data type containing that user's information.

The response of a two-way communication is handled by assigning an event listener and attaching a handler function.

```
var serverFile:String = "http://localhost/callLink.php";
var variables:URLVariables = new URLVariables();
variables.id = 1004;
variables.user = "James";
var urlRequest:URLRequest = new URLRequest(serverFile);
urlRequest.method = URLRequestMethod.POST;
urlRequest.data = variables;
var urlLoader:URLLoader = new URLLoader();
urlLoader.addEventListener(Event.COMPLETE, userResponseHandler);
try {
    urlLoader.load(urlRequest);
} catch (e:Error) {
    //handle error here
}
```