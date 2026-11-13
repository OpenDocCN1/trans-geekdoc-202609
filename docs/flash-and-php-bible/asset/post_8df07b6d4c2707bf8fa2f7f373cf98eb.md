
That is all the code that is needed to develop a fully functional contact form using Flash and PHP. You can expand on this example and give the contact form a lot more functionality. A few things to think about adding would be a more robust validation process, more form fields, and possibly more informative responses to the user.

## Keep security in mind

One very important element to note about this contact form example is the code does not honor security procedures and actually lets the user pass any data to PHP. A more robust and live example would require a much stronger level of security; however, for demonstration purposes overall security has been left out.

## Login Module in Flash

More often than not you will want to have a secure portion to a Web site. A very popular example of this would be a review section for a photographer where a client can log in and look at the photos.

The form portion of this application is almost identical to the contact form. You need a Username and Password box and a Submit button to fire off the login handler routine.

Here is a sample layout that can be found in the starting file, or you can create it from scratch.

The instance names for this example are displayed in Table 5.1.

| Form Component | Description |
| :--- | :--- |
| usernameTxt | Username to be logged in |
| passwordTxt | Password to be attempted |
| resetBtn | Reset button, clears the fields |
| loginBtn | Login button, fire the loginHandler |

Now that you have the form visually complete you can move on to the ActionScript, which makes the form functional.

## Code skeleton

In previous examples, you looked at all of the code in one long section, but sometimes that can be overwhelming. Looking at the skeleton of code offers a quick way to evaluate the program variables, functions, and other elements.

Here is the code skeleton for the login module:

```actionscript
stop(); // stop the playhead

var phpFile:String = "http://localhost/ch04/login.php";
var form:MovieClip = loginMC;
var loggedIn:Boolean = false;

function loginHandler(e:MouseEvent):void {...}
function resetHandler(e:MouseEvent):void {...}
function clearIndicators():void {...}
function sendHandler(e:Event):void {...}

form.usernameTxt.tabIndex = 1;
form.passwordTxt.tabIndex = 2;
form.resetBtn.tabIndex = 3;
form.loginBtn.tabIndex = 4;

form.passwordTxt.displayAsPassword = true;
form.resetBtn.addEventListener(MouseEvent.CLICK, resetHandler);
form.loginBtn.addEventListener(MouseEvent.CLICK, loginHandler);
```

## Login event handlers

Similar to the contact form example, you need to assign event handlers that handle the login, clearing, and UI changes for the login module.

The first event handler is the loginHandler, which is responsible for calling the server and ensuring valid data is passed to the server. Its last task is to assign the handler for the result event.

```actionscript
function loginHandler(e:MouseEvent):void
{
    clearIndicators();

    var user:String = form.usernameTxt.text;
    var pass:String = form.passwordTxt.text;
    var allFields:Boolean = true;

    if(user.length < 2)
    {
        allFields = false;
        form.userRequiredIndicator.alpha = 1.0;
    }

    if(pass.length < 2)
    {
        allFields = false;
        form.passRequiredIndicator.alpha = 1.0;
    }

    if(!allFields)
    {
        form.statusTxt.htmlText= "<font color=\"#FF0000\">Username"
        + " and Password required!</font>";
        return;
    }

    var variables:URLVariables = new URLVariables();
    variables.user = user;
    variables.pass = pass;

    var urlRequest:URLRequest = new URLRequest(phpFile);
    urlRequest.method = URLRequestMethod.POST;
    urlRequest.data = variables;

    var loader:URLLoader = new URLLoader();
    loader.addEventListener(Event.COMPLETE, sendHandler);
    loader.load(urlRequest);
}
```

This handler starts off by assigning the username and password fields to internal variables. Those new variables are then checked for valid length, which if correct sets the allFields variable. This allFields variable is used to determine if the error message should be displayed and the function should be exited. If allFields is not set you can continue setting up the call to the server. This portion is identical to the contact form example. In fact, you will quickly notice that ActionScript has a very similar format for all types of loading and sending of data.

The next handler you will focus on is the clearHandler, which is assigned to the resetBtn. Its job is to clear all of the form fields and make a call to the clearIndicators function, which you look at in a moment.

```actionscript
function resetHandler(e:MouseEvent):void
{
    form.usernameTxt.text = "";
    form.passwordTxt.text = "";
    form.statusTxt.htmlText = "";

    clearIndicators();
}
```

The clearIndicators function changes the alpha opacity of the icons that can be found to the right of the username and password TextInput components in the starter file. If you are creating this module from scratch you would most likely omit this function and the call to it in the resetHandler.

```actionscript
function clearIndicators():void
{
    form.userRequiredIndicator.alpha = 0;
    form.passRequiredIndicator.alpha = 0;
}
```

The last handler needed for this module is the sendHandler, which is called when the PHP code sends back a response.

```actionscript
function sendHandler(e:Event):void
{
    var loader:URLLoader = URLLoader(e.target);
    var variables:URLVariables = new URLVariables(loader.data);

    if(variables.resultCode == "LOGGED_IN")
    {
        loggedIn = true;
        gotoAndStop(2);
    }
    else if(variables.resultCode == "NOT_LOGGED_IN")
    {
        form.statusTxt.htmlText = "<font color=\"#FF0000\">"+
        "Username/Password not correct.</font>";
    }
}
```

The response passed from PHP is evaluated to determine if the user is valid and whether or not the secure page should be displayed.

```actionscript
if(variables.resultCode == "LOGGED_IN")
{
    loggedIn = true; // user logged in,
    gotoAndStop(2); // sample has secure page on frame 2
}
else if(variables.resultCode == "NOT_LOGGED_IN")
{
    form.statusTxt.htmlText = "<font color=\"#FF0000\">"+
    "Username/Password not correct.</font>";
}
```

Assuming the user is logged in, you set a loggedIn variable and move to the second frame, which in the example is a top-secret section, as shown in Figure 5.2. Your example will most likely have a more important reason to be logged in, but maybe not.

## FIGURE 5.2

Example secure page that is only visible if the user is logged in

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_131_0.png)

## Server integration for login module

The PHP code for the login module is the next part in the process.

```php
<?php

error_reporting(0); // disable all error reporting

$user = $_POST['user'];
$pass = $_POST['pass'];

// sample password response, normally
// would be sent from database
$storedPassword = "83e4a96aed96436c621b9809e258b309";

if(!empty($_POST))
{
	if($user == "guest" && md5($pass) == $storedPassword)
	{
		print "resultCode=LOGGED_IN";
	}
	else
	{
		print "resultCode=NOT_LOGGED_IN";
	}
}
?>
```

Your focus in this section is on the $_POST data and conditional check to determine if the password is correct or not. This result is then sent back to Flash where it is used to set logged-in status and whatever else a valid user would see.

A more robust example would have the PHP be evaluated against a database instead of a static string. The $storedPassword variable has an md5( ) hashed string. MD5 is a hashing algorithm that is available in many programming languages, one of which is PHP and is most frequently used when storing passwords in a database. You will look at MD5 a little more in depth in the security chapter, but for now the most important thing to note is that hashed string is your password.

You now have a complete login module using Flash and PHP. You could easily expand this example to include database integration and more importantly, an added level of security.

## Summary

In this chapter you learned how to build forms in Flash and how to make them interactive using PHP. As a more advanced project you then created a login component utilizing the previous information you learned about form development overall.
