
### FIGURE 7.3 The text field showing the time in hours, minutes and seconds

![](img/b2471264f405d17994ef173e4b9cec92_213_0.png)

Figure 7.3 shows the modified text field, with the function showing the time in hours, minutes and seconds.

## innerHTML and the DOM

In the previous examples, we used a text field to display the current time. An alternative approach to displaying content in a specific part of the browser is to write to a node of the document. One way of doing this is to use the interfaces of the DOM, but this can be quite complex and different browsers can react in different ways to the same scripts. Another way is to use the ‘innerHTML’ property of HTML elements. This enables us to access text nodes directly and update their contents.

The ‘innerHTML’ property is not part of the formal HTML DOM specification, and was introduced by Microsoft in Internet Explorer 4 in 1997. However due to its popularity it has been incorporated into other browsers, despite not being included in any public standard, and is therefore quite reliable in terms of cross-browser support. There has been much debate about whether using ‘innerHTML’ is wise or not. However, it is simple to use and has been used in many Ajax implementations. One of the objections to the use of ‘innerHTML’ is that it can be used to include structural elements (i.e. mark-up) inside the processes of client-side scripts, which is a poor separation of concerns. It is therefore preferable to restrict the use of ‘innerHTML’ to the manipulation of content rather than using it to dynamically generate mark-up.

In the next example, we modify the ‘showTimer’ function to use the ‘innerHTML’ property. The changes are relatively simple. First, we replace the text input field with a suitable document node, in this case a simple ‘div’ element that contains no text.

```
<div id="clock"></div>
```

Then all we have to do in the JavaScript function is modify the ‘div’ element, accessed using the ‘getElementById’ method, by setting the value of its ‘innerHTML’ property:

```
// File: showinnertimer.js
function showTimer()
{
  var date=new Date();
  document.getElementById("clock").innerHTML=date.getHours() + ":" +
date.getMinutes() + ":" + date.getSeconds();
setTimeout("showTimer()", 1000);
}
```

Otherwise everything looks, and works, pretty much the same as before, except that the time appears in the browser simply as text, and not in a text field component. Here is the full XHTML page, with the ‘div’ element used by the function.

```
<?xml version="1.0"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<meta http-equiv="Content-Script-Type" content="text/javascript"/>
<title>JavaScript clock</title>
<script type="text/javascript" src="showinnertimer.js">
</script>
</head>
<body onload="showTimer()">
<!-- File: example7-5.htm -->
<div id="clock"></div>
</body>
</html>
```

Figure 7.4 shows the output in the browser. The time is no longer in a text field but simply a text node of the document.

## Responding to button events

The events we have used so far, the ‘onload’ event and timer events, are not related to user activity. However, if we want to make web pages more dynamic we need to be able to respond to the user’s actions in the page. One way of doing this is to trigger JavaScript functions with user-instigated events such as buttons being pressed. HTML button components can be linked to JavaScript functions by using their ‘onclick’ event. In our next example, we use button events to call the window object’s ‘resizeTo’ method, which sets the browser window to a specified width and height. The values for the width and height appear in parentheses after the method name, separated by a comma. This example would set the window size to 400 pixels wide and 200 pixels high:

```
window.resizeTo(400,200);
```

### FIGURE 7.4 The current time displayed in a browser using the ‘innerHTML’ property

![](img/b2471264f405d17994ef173e4b9cec92_214_0.png)

Our next script example shows button events being used to resize the window. It also shows how a JavaScript function can be called from more than one place in a script. The function we use is called ‘resizeWindow’, takes two parameters for the width and the height, and sets the size of the window accordingly:

```
// File: resize.js
function resizeWindow(width, height)
{
    window.resizeTo(width,height);
}
```

In the body of the document, there are two buttons, both of which use the ‘onclick’ event to call the ‘resizeWindow’ function. The first button (labelled ‘shrink window’) sets the window to be 400 by 300 pixels. The second uses two properties of the screen (‘availWidth’ and ‘availHeight’) to set the window size to the maximum available. The ‘screen’ object is a property of the window object.

```
<?xml version="1.0"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
    <meta http-equiv="Content-Script-Type" content="text/javascript"/>
    <title>JavaScript window resize</title>
    <script type="text/javascript" src="resize.js">
    </script>
</head>
<body>
    <!-- File: example7-6.htm -->
    <div>
        <input type="button" onclick="resizeWindow(400,300)"
        value="shrink window"/>
        <input type="button"
        onclick="resizeWindow(window.screen.availWidth,
        window.screen.availHeight)" value="restore window"/>
    </div>
</body>
</html>
```

Figure 7.5 shows the window in Mozilla Firefox 2 before the ‘shrink window’ button has been pressed.

| NOTE | Different browsers may give you slightly different behaviours using this function. For example, Opera 9 will only resize the window if it is detached, not if it is part of a tabbed window. |
|------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

```
<body>
    <!-- File: example7-7.htm -->
    <div>
        <a href="javascript:openWindow('about.htm')">open window</a>
    </div>
</body>
</html>
```

The effect of clicking the hyperlink in the page varies from browser to browser. In some cases, a new window is created and in others a new tab appears. Figure 7.6 shows how Internet Explorer 7 responds to the function, opening a new window.

## 7.3 Dynamic style sheets

As well as interacting with the DOM, another important feature of DHTML is the use of style sheets to dynamically change the presentation of the document. A commonly used example of this technique is to apply JavaScript and style sheets to show or hide parts of a page. This technique can be used, for example, to add expandable menus to web pages. To interact with styles inside our scripts, we can use the 'style' property of the elements in the DOM to dynamically apply styles to parts of the document. The CSS style property that we can use to show or hide parts of the page is 'display', which can have the value 'block' to make the content visible, or 'none' to make it invisible. The following function uses an 'if' statement to switch the display style of an element between 'none' and 'block'. In this example, 'element' is a variable that references an element node from the current document, identified by its 'id' attribute.

### FIGURE 7.6 The effect of the 'openWindow' function in Internet Explorer 7, triggered by a JavaScript URL

![](img/b2471264f405d17994ef173e4b9cec92_217_0.png)

```
// File: changedisplay.js
function changeDisplay(id)
{
    var element=document.getElementById(id);
    if(element.style.display=='none')
    {
        element.style.display='block';
    }
    else
    {
        element.style.display = 'none';
    }
}
```

So far in this chapter we have looked at how we can use JavaScript to navigate to nodes in the DOM and to access the properties of these nodes, including the ‘style’ property. We have also looked at the use of events to trigger JavaScript functions. In the next example, we draw all of these techniques together into a DHTML page that shows and hides parts of a page when a JavaScript URL is clicked. The page consists of two sections with titles ‘JavaScript’ and ‘DHTML (Dynamic HTML)’ that are in anchors that use JavaScript URLs. When either of these titles is clicked, the detail text (enclosed in ‘div’ tags with unique ids) switches between shown and hidden. The ids of the ‘div’ elements are passed to the ‘changeDisplay’ function in order to switch their state.

We need to be able to invoke this function in two ways. First, we need to invoke it when the page is loaded, to set the initial state of the page, using the ‘onload’ event. To call more than one function from the ‘onload’ event or, as in this case, to call the same function more than once, the function calls can be put into a comma-separated list, like this:

```
<body onload="changeDisplay('jsdetail'), changeDisplay('dhtmldetail')">
```

Since the display state of the two ‘div’ elements has not been set initially, the first time it is called for a particular element, the function executes the ‘else’ block and sets the display state to ‘none’. From that point onwards, the JavaScript URLs invoke the function when either one of them is clicked and switches the display state. Here is one example of these two URLs:

```
<a href="javascript:changeDisplay('jsdetail')">JavaScript</a>
```

Note how it passes the id of one of the ‘div’ elements to the function. Here is the complete XHTML page:

```
<?xml version="1.0"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
    "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
    <head>
        <meta http-equiv="Content-Script-Type" content="text/javascript"/>
        <title>DHTML show and hide</title>
        <script type="text/javascript" src="changedisplay.js">
        </script>
    </head>
    <body onload="changeDisplay('jsdetail'), changeDisplay('dhtmldetail')">
        <!-- File: example7-8.htm -->
        <div>
```
