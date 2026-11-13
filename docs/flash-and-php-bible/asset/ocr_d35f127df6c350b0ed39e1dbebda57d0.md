```
{
    login.redraw();
}

function loginHandler(e:Event):void
{
    trace("Do Login");
    trace("Username: " + login.data.username);
    trace("Password: " + login.data.password);

    var responder:Responder = new Responder(loginRespHandler, onFault);
    gateway = new NetConnection();
    gateway.connect(gatewayURL);
    gateway.call("User.login", responder,
        login.data.username,
        login.data.password
    );
}

function loginRespHandler(o:Object):void
{
    trace("Response: " + o.response);

    if(o.response == true)
    {
        trace("user logged in");
        login.close();
    }
    else
    {
        login.responseString = "username and password incorrect";
    }
}

function onFault(responds:Object):void
{
    trace("Debug::Error");
    for(var i in responds)
    {
        trace(" " + responds[i]);
    }
}

stage.dispatchEvent(new Event(Event.RESIZE));
```

# Finalizing the Video Player

The last section of this chapter is finalizing the video player. You will implement the login component you built in the previous section and learn how to use an external library.