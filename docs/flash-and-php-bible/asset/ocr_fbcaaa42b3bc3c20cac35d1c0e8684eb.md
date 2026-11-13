```
var gateway:NetConnection;
var gatewayURL:String = "http://localhost/amfphp/gateway.php";
```

The original example did the username validation directly within the Flash file. While this was functional, it wasn't very practical because only one login or password can be used.

# loginHandler method

This new system modifies the existing loginHandler function by adding a remoting service call, sending the username and password that was captured by the login window component.

```
function loginHandler(e:Event):void
{
    trace("Do Login");
    trace("Username: " + login.data.username);
    trace("Password: " + login.data.password);

    var responder:Responder = new Responder(loginRespHandler,
    onFault);
    gateway = new NetConnection();
    gateway.connect(gatewayURL);
    gateway.call("User.login", responder,
    login.data.username,
    login.data.password
    );
}
```

The Responder class needs a response handler defined, so the next function handles this service response. For this example, the service will either return a Boolean for whether the user is logged in or not, or an error if something goes wrong.

```
function loginRespHandler(o:Object):void
{
    ...
}
```

A simple conditional statement is used to determine if the user is logged in based on the response from the remoting service.

# Handling the login response

If the user is logged in, a call to the close method of the login component is made to hide the login window and enable the application interface.

```
function loginRespHandler(o:Object):void
{
    if(o.response == true)
    {
    login.close();
    }
}
```