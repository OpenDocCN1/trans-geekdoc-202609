
Regardless of whether this is the first pass of the redraw method or not, the blocking clip needs to be repositioned. The login window is placed dead center, which means you can calculate the padding around it, multiply this to create a negative number, and place the blocking clip using that calculation.

```
// reverse the offset to position blocker
blocker.y = y * -1;
blocker.x = x * -1;
```

When all the calculations are complete, you can add the blocker MovieClip to the DisplayList, which makes it visible in the application.

```
addChild(blocker);
```

> NOTE Making all the position-based calculations before the clip is added to the display list minimizes flickering and jumping objects in your application.

## Swapping placement of two MovieClips

ActionScript 3 does not have any depth management like what is found in ActionScript 2 and its predecessors. The equivalent is taking the id of a clip and swapping it with another clip. This appears to be depth management, except for the very important fact that ActionScript takes care of the reordering when the children are swapped.

In this example, you want to make sure the login box is above the blocking clip because if it is placed below it, the user is not able to interact or log in to the application:

```
container.swapChildren(loginMC, blocker);
```

## Centering a MovieClip

The last step of the redraw method is to center the login box on the Stage to ensure it is always in the middle. This is constantly updated when the redraw method is called because resizing the stage would make the login box sit at a noncentered position.

```
loginMC.x = (stage.stageWidth / 2) - (loginMC.width / 2);
loginMC.y = (stage.stageHeight / 2) - (loginMC.height / 2);
```

The calculation uses the stage dimensions and login box dimensions to determine the middle point. This is where the loginMC MovieClip is placed when the calculation is completed.

## close method

The close method has one task: to remove the current login box and allow the application to be used once again. The removal process is achieved by removing the container child, which contains the login box and blocking MovieClip.

```
public function close():void
{
	container.parent.removeChild(container);
}
```

## resetHandler method

The resetHandler method is called whenever the Reset button is clicked. This method clears all of the status messages and empties the login and password fields.

```
private function resetHandler(e:MouseEvent):void
{
    loginMC.username.text = "";
    loginMC.password.text = "";
    loginMC.responseTxt.text = "";
}
```

## loginHandler method

The loginHandler method is attached to the CLICK event of the loginBtn. This method is called whenever the loginBtn is clicked by the mouse.

```
private function loginHandler(e:MouseEvent):void
{
    ...
}
```

This method is responsible for checking the username and password fields for valid data. If one of these fields is empty, the function is exited and a response message is displayed below the password field.

```
loginMC.responseTxt.text = "";

if(loginMC.username.text == "" || loginMC.password.text == "")
{
    loginMC.responseTxt.text = "username & password required";
    return;
}
```

If the username and password fields are found to have acceptable values, those values are stored in the data property, which will be read by the calling script in a custom event handler.

```
data = {
    username:loginMC.username.text,
    password:loginMC.password.text
};
```

The last part of this method is to fire off a custom event, alerting the calling script that a username and password have been captured and need to be validated.

```
dispatchEvent(new Event(LOGIN_ATTEMPT));
```

This component has been developed to separate the display and security logic, which means the component can be reused because nothing is hardcoded into the actual login logic.

The last real method is a setter, which is used to externally set the response string. This would be called from the loginHandler if the validation failed and you want to show the user so that he or she can attempt another password or username.

```
public function set responseString(s:String):void
{
    loginMC.responseTxt.text = s;
}
```

The dummyHandler method does not have any functionality. It is used to block any mouse events that occur on the blocking MovieClip. This method is required because an event handler needs a valid function, and if you define an anonymous one, it creates a slow memory leak.

```
private function dummyHandler(e:MouseEvent):void
{
    // no action
}
```

At this point you have completed the LoginWindow class and can move to the next step, which is to create some simple ActionScript to test the component. When that is properly tested you can create the PHP service and make the login component interact with the database to actually look for real users attempting to log in.

Here is the complete LoginWindow class.

```
package
{
    import flash.display.MovieClip;
    import flash.geom.Rectangle;
    import flash.events.Event;
    import flash.events.MouseEvent;
    import flash.net.*;

    public class LoginWindow extends MovieClip
    {
        public var data:Object;

        private var _visible:Boolean = false;
        private var container:MovieClip;
        private var blocker:MovieClip = null;

        public static var LOGIN_ATTEMPT:String = "onLoginAttempt";

        function LoginWindow()
        {
            container = this;

            loginMC.resetBtn.addEventListener(MouseEvent.CLICK,
                resetHandler);
        }

        loginMC.loginBtn.addEventListener(MouseEvent.CLICK,
            loginHandler);
    }

    public function redraw():void
    {
        if(blocker == null)
        {
            blocker = new MovieClip();
            blocker.alpha = 0.5;
            blocker.graphics.beginFill(0x000000);
            blocker.graphics.drawRect(
                0,
                0,
                stage.stageWidth,
                stage.stageHeight
            );
            blocker.addEventListener(
                MouseEvent.ROLL_OVER,
                dummyHandler
            );
            blocker.addEventListener(
                MouseEvent.ROLL_OUT,
                dummyHandler
            );
            blocker.addEventListener(
                MouseEvent.CLICK,
                dummyHandler
            );
        }
        else
        {
            blocker.width = stage.stageWidth;
            blocker.height = stage.stageHeight;
        }
        // reverse the offset to position blocker
        blocker.y = y * -1;
        blocker.x = x * -1;

        addChild(blocker);

        container.swapChildren(loginMC, blocker);

        loginMC.x = (stage.stageWidth / 2) -
            (loginMC.width / 2);

        loginMC.y = (stage.stageHeight / 2) -
            (loginMC.height / 2);
        _visible = true;
    }

    public function close():void
    {
        container.parent.removeChild(container);
    }

    private function resetHandler(e:MouseEvent):void
    {
        loginMC.username.text = "";
        loginMC.password.text = "";
        loginMC.responseTxt.text = "";
    }

    private function loginHandler(e:MouseEvent):void
    {
        loginMC.responseTxt.text = "";

        if(
            loginMC.username.text == "" ||
            loginMC.password.text == "")
        {
            loginMC.responseTxt.text =
                "username & password required";
            return;
        }

        data = {
            username:loginMC.username.text,
            password:loginMC.password.text
        };
        dispatchEvent(new Event(LOGIN_ATTEMPT));
    }

    public function set responseString(s:String):void
    {
        loginMC.responseTxt.text = s;
    }

    private function dummyHandler(e:MouseEvent):void
    {
        //
    }
}
```

## Testing the login component

The next step is to test the login component to make sure everything is working properly. The first step is to create a new instance of the LoginWindow component in a stand-alone FLA, or you can use the sample file found with the book's source code.

```
var login:LoginWindow = new LoginWindow();
```

Once the instance is created, the next step is to assign an event handler for the custom LOGIN_ATTEMPT event that is called when the user types data into both the username and password fields and then clicks the Login button.

```
login.addEventListener(LoginWindow.LOGIN_ATTEMPT, loginHandler);
```

After the Login window component loads and the proper event handler is assigned, the next step is to add it to the display list, which makes it visible.

```
addChild(login);
```

## Assigning a stage event handler

You want to make sure any modification to the stage redraws the login component, or items that are being blocked can accidentally reposition themselves beyond the blocking MovieClip.

```
stage.align = StageAlign.TOP_LEFT;
stage.scaleMode = StageScaleMode.NO_SCALE;
stage.addEventListener(Event.RESIZE, stageResizeHandler);
```

After the event is assigned to the stage object, you need to create the function that is being referenced in the event listener. For this application, the handler simply makes a call to the redraw method of the login component. In a real-world application you may have more functionality in this event, but for now this is fine for testing.

```
function stageResizeHandler(e:Event):void
{
login.redraw();
}
```

## Handling the login attempt

The next function is used to handle login attempts. For simplicity, this function has a predefined username and password that is later replaced with a remoting service in the next section.

If a valid login is reached, the close method of the login component is called. This removes the Login box and enables the application for that session.

```
function loginHandler(e:Event):void
{
if(login.data.username == "guest" && login.data.password ==
"pass")
