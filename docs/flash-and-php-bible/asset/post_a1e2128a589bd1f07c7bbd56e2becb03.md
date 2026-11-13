
An else option is added to handle the incorrect login attempts by updating the response message of the login component.

```
function loginRespHandler(o:Object):void
{
	if(o.response == true)
	{
		login.close();
	}
	else
	{
		login.responseString = "username and password incorrect";
	}
}
```

## Handling response errors

The last function required for the login system is the onFault, which handles errors in the service calls. For example, if the script managed to attempt a login check with no username or password, the SQL would fail. This error will be raised by the PHP class and sent back to Flash, assuming it is properly handled.

```
function onFault(responds:Object):void
{
	trace("Debug::Error");
	for(var i in responds)
	{
		trace(" " + responds[i]);
	}
}
```

Now that the remoting code has been added to the previous example login component, you can test it, and you really shouldn't notice any difference. The only change would be the ability to use more than one username, as long as it is found in the users table that you created at the beginning of this section.

Here is the login component example with the proper remoting code included:

```
var gateway:NetConnection;
var gatewayURL:String = "http://localhost/amfphp/gateway.php";

var login:LoginWindow = new LoginWindow();
login.addEventListener(LoginWindow.LOGIN_ATTEMPT, loginHandler);

addChild(login);

stage.align = StageAlign.TOP_LEFT;
stage.scaleMode = StageScaleMode.NO_SCALE;
stage.addEventListener(Event.RESIZE, stageResizeHandler);

function stageResizeHandler(e:Event):void
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

## Finalizing the Video Player

The last section of this chapter is finalizing the video player. You will implement the login component you built in the previous section and learn how to use an external library.

## Using an external library

The advantage to using an external library is you only have to update one location and all instances of that library usage are also updated.

For example, imagine you have a logo with a specific color on it and suddenly the company decides that it wants to recolor the logo. Rather than opening every instance of that logo and editing it, you can open the master FLA, edit that, and then update the instances, which automatically reflect the changes.

You can use this concept for much more than a simple logo, because you will be loading the login component from the example file you built in the previous section.

## Adding the login component

Start by opening the VideoPlayer.fla file if it isn't already opened. Then choose File Import Open External Library.

In this dialog box, you can navigate to the directory where the login component is stored and select that file. With the file selected, click Open.

Drag the LoginWindowMC from this library into the library of the VideoPlayer FLA. You should now see two new MovieClips in the library of your VideoPlayer file. This is because the LoginWindowMC has a supporting file that contains all of the design, which is automatically copied when you drag the parent.

Now that the login component is added, you can modify the existing VideoPlayer class file to add this new functionality. To start, add the component creation, but forget about the login logic.

The new code should be added to the constructor function, similar to the following:

```
function VideoPlayer()
{
    gatewayURL = "http://localhost/amfphp/gateway.php";
    getCategories();

    videoPlayer.visible = false;
    videoListCombo.enabled = false;

    var login:LoginWindow = new LoginWindow();
    login.addEventListener(LoginWindow.LOGIN_ATTEMPT,
    loginHandler);

    addChild(login);
    login.redraw();
}
```

Before you test the code, add the loginHandler method to avoid any runtime errors. You can add this method at any point in the code. I recommend somewhere toward the bottom of the class to maintain the overall flow of the file.

```
private function updateTrackingHandler(response:Object):void
{
    ...
}
```

```
private function loginHandler(response:Object):void
{
    ...
}
```

The last step is to import the LoginWindow class so the static property can be loaded for the event handler.

```
package
{
    import flash.display.MovieClip;
    import flash.events.Event;
    import flash.net.*;
    import LoginWindow;

    public class VideoPlayer extends MovieClip
    {
        ...
    }
}
```

When you test the application you should immediately see the login window. Because you didn't add any logic at this point, there is no way to close the login window, but you can see it is working, so you can continue.

The logic, which is responsible for calling the remoting service, needs to be added to the existing loginHandler method.

```
function loginHandler(e:Event):void
{
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

The next step is to copy the loginRespHandler and add it below the loginHandler in the VideoPlayer class.

```
function LoginRespHandler(o:Object):void
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
```

The proper code has now been added to the VideoPlayer class; however, there is one final modification needed before the login component will function properly.

The login variable that is defined in the constructor needs to be a global property, because as it stands right now, no other method in this class has access to it.

```
package
{
    ...

    public class VideoPlayer extends MovieClip
    {
        ...

        private var selectedCatID:Number;
        private var login:LoginWindow;

        function VideoPlayer()
        {
            ...

            login = new LoginWindow();
        }
    }
}
```

Now that the login variable is properly defined, you can test the application, as shown in Figure 17.7. You should be able to type a valid username and password, and the login component should disappear when you do so.

## FIGURE 17.7 Final video player with login box visible

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_506_0.png)

As you can see, the login component being built this way really makes it possible to add it to any existing project. To extend on this example, you could add a shared object that would preserve the session and make it so the user doesn't need to log in each time.

You should now have a great understanding of building and working with advanced, real-world applications. I am sure you are thinking of many various applications to build after seeing how they function in depth.

The following is a table outlining the names of files and where they should be stored for this complete application. The path is based on the project directory which should be in your Apache home directory in order for the application to run properly.

## Application Source File Locations

| File Name | Save Path |
| :--- | :--- |
| LoginWindow.swf | / |
| LoginWindow.fla | / |
| LoginWindow.as | / |
| VideoListItem.as | / |
| VideoPlayer.as | / |
| SkinOverPlayStopSeekMuteVol.swf | / |
