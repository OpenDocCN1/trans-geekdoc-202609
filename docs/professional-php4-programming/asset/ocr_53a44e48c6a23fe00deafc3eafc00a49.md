GTK is event-driven. This means that every PHP-GTK program has a main loop running throughout the lifetime of the application. The main loop consists of a stream of **events**, that is, messages from the interface regarding changes in its environment such as a widget's first appearance on screen, the movement of a mouse pointer, or the pressing of a key.

When an event occurs that has relevance to a widget, control is passed via a **signal** emitted by the widget to the appropriate function to handle that event. This signal and the function it calls could be internal to GTK, such as the shift in color seen when the mouse pointer enters a sensitive widget's screen area, or it could be the connection of a signal to a function written by the PHP-GTK programmer.

> **Note:** These signals are not the same as UNIX system signals, and are not implemented using them, although the terminology is almost identical.

To make a button perform an action, we set up a signal connection to an appropriate function, known as a signal handler or callback function. This is achieved using the `connect()` method:

```
$button->connect('clicked', 'my_function');
```

The first parameter of the `connect()` method is the name of the signal you wish to respond to, in this case the `clicked` signal. The second parameter is the function that will be called when the signal is emitted. The `connect()` method passes the calling object to the callback function as the function's first parameter. It is possible to add further custom parameters to the connection and the callback in order to pass further objects. There is no limitation on the number of custom parameters that can be passed in this way.

```
function myFunction($button)
{
    print("The button was clicked\n");
}
```

With these concepts behind us, we can now define the life cycle of a widget. This has five main parts.

# ## Object Creation

The general syntax is:

```
$widget = &new GtkWidget(parameters);
```

You would normally define the widget at this stage too by setting its size, color, text, or other properties as appropriate.

# ## Signal Connection

This is a step for setting up callback functions for use. The syntax is:

```
$widget->connect("signal-name", "functionName");
```

where `signal-name` is a predefined state such as `clicked` and `functionName` is the name of the callback function.