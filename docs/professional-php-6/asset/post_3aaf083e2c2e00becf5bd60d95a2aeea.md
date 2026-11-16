
## class.Event_Handler.php

The parent event handler class is really more of a utility class specifying how to handle lower-level events that may occur in your application. In this specific example, it creates a database connection. The common_db.inc file contains a db_connect() function that creates a database connection — pretty straightforward stuff, and the implementation of such a method is left to you. However, if you are creating an application of any serious magnitude, the best way to approach such a challenge is to make use of a database abstraction layer, as explored in Chapter 6.

Of course, you may consider adding any number of appropriate methods here, depending on the nature of the problem you are solving. For now, here’s the code for a simple class.Event_Handler.php:

```php
<?php
require_once ("interface_Handled.php");
require_once('common_db.inc');

abstract class Event_Handler
{
    function dbconn(){
        $link_id = db_connect('sample_db');
        return $link_id;
    }

    abstract function handled_event();
}
?>
```

Because you are unlikely to know what each event is going to do, you declare the handled_event() function abstract so that the descendent handler classes can each implement it as they see fit. In order to allow this, you will notice that the whole class has been declared abstract. This has no real bearing on the application itself, because you will never directly instantiate this class — the dispatcher will figure out which descendent event handler to instantiate, and do so directly.

## class.Handler_View.php

This descendant handler gives a quick demonstration of the type of code you can usefully execute within a typical handler. Notice how you are forced to give an implementation of handled_events(), as this has been declared as an abstract method in the parent handler class. The following code shows how to view a few records pulled straight from a database:

```php
<?php
require_once('class.Event_Handler.php');

class Handler_View extends Event_Handler
{
    private $handle;

    function __construct($event_handle){
        $this->handle = $event_handle;
    }

    function handled_event(){
        echo "The event, $this->handle, is now handled. <BR>
It is, I promise!<BR><BR>Your records are as follows: <BR> <BR>";
        $id = parent::dbconn();
        $result = pg_query($id, "SELECT * FROM user");
        while($query_data = pg_fetch_row($result)) {
            echo $query_data[1], " is a ", $query_data[4], "<br>";
        }
    }
}
?>
```

Of course, the actual data being pulled out of here is irrelevant — this is just an example. If you want to try it out, however, simply hook this up to an example database of your own and query it as you like, changing the SQL statement.

Note that, in the constructor, the handler still holds onto the event handle passed to it, by saving it into a local private member variable. It’s not actually used in this example, but it does demonstrate that you can get such parameters through to the handlers, if necessary.

## class.Handler_Edit.php

Let’s take a look at another descendent handler. This demonstration of an edit handler simply returns a message to the user when invoked:

```php
<?php
require_once('class.Event_Handler.php');
class Handler_Edit extends Event_Handler {
    private $handle;
    function __construct($event_handle) {
        $this->handle = $event_handle;
    }
    function handled_event() {
        echo "This is event $this->handle, which is now handled - no kidding! <BR>";
    }
}
?>
```

As usual, you capture the event handle and store it locally. In this case, the handler does actually use it as part of its event processing. Admittedly, the handled_event() method implementation is nothing special; it simply returns a message confirming that the event has been dealt with.

That’s about it for setting things up. Let’s now explore how easy it is to modify the application and get great results with little effort.

## Implementing Security

Assume that you wanted to limit the functionality of the application depending on who was using it — which is not an uncommon requirement. An application with such a requirement could be something like a wiki, which should allow certain trusted sources to edit whatever they like, but limit others to only read (and not change) the content.

First, have the application create a new session after you have successfully validated the user. You can then populate the session variable with relevant details concerning who the user is. In this case, you use a session variable that contains the user’s name. This means that you now have access to the current user’s details from virtually anywhere in your application, including from within your event handlers. You can use this information to determine whether or not to allow the event to take place at all.

Add the following method to each of the descendant event handler classes whose use you wish to restrict. As you can see, the method simply checks the author’s name currently held in the session, and if the name being offered isn’t acceptable, the method will consider the user unauthorized to perform the requested action:

```php
function secure_handler() {
    if ($_SESSION['name'] == "David") {
        $this->handled_event();
    } else {
        echo "Sorry ${_SESSION['name']} you are not authorized!";
    }
}
```

You need to change one line in the dispatcher to ensure that only the secure method is used when handling the event. Open the file and find the following line:

```php
$response = $handler_obj->handled_event();
```

Change the preceding line as follows:

```php
$response = $handler_obj->secure_handler();
```

You also need to ensure that you keep to the design principles you first set out by ensuring that the existence of this method in the children handlers is enforced via the use of the interface. This means that the parent handler must at least contain an abstract representation of the `secure_handler()` function.

Add the following line to the interface:

```php
abstract function secure_handler();
```

There is no way to know precisely what level of permission each event will require; it may well differ from event to event. Accordingly, the parent event handler does not directly implement the secure handler itself. Instead, much in the same way as the regular handler method previously discussed, it passes responsibility for its implementation to its children, by again declaring the method abstract:

```php
abstract function secure_handler();
```

Each descendant event handler is now required to implement both a handled_event() and secure_handler() method as specified by the interface. To determine whether to allow the event to take place, each event handler's secure_handler() method could retrieve its own permission setting from a file held by the administrator. This file would, of course, be encrypted (or at least held somewhere secure), and would most likely be editable by the wiki administrator, such that he or she could change which handlers were available to which users.

Here is a little example user interface that would make use of the secure, event-oriented application:

```php
<?php
require_once ('class.Dispatcher.php');
session_start();
?>
<html>
<head>
<title>Secure, Event Driven Record Viewer!</title>
</head>
<body>
<form method="GET" ACTION="?=<?=$_SERVER['PHP_SELF']?>">
<input type="submit" name="event" value="View" />
<input type="submit" name="event" value="Edit" />
</form>
</body>
</html>
<?php
function handle() {
$event = $_GET['event'];
$disp = new dispatcher($event);
$disp->handle_the_event();
}
$_SESSION['name'] = "Horatio";
handle();
?>
```

The session variables would normally be set during the user's login, but for brevity's sake, let's assume that Horatio wants in — hence the reason this has been hard-coded. By way of example, let's check whether you can allow Horatio to use the edit function. You quite rightly expect the output shown in Figure 8-3 if Horatio clicks the Edit button.
