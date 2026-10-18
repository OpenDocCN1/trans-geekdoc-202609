A function may return a value, representing the end result of the function, using the reserved word ‘return’ followed by the variable or value that is being returned:

```
```html
<script type="text/javascript">
function functionname(parameters) {
...
    return value
}
</script>
```
```

If it is included, the line that returns the value is normally the last line in the function. This is because nothing after a return statement is executed; the function terminates at that point. This behaviour can also be used to deliberately ‘short circuit’ a function in cases where we want to exit from the function before executing all the code, perhaps because of some error condition or because we already have the result we need.

The following script shows a simple function that uses the same array of day names that we saw in an earlier script example. The difference is that instead of writing the day name out to the document, the function returns the name of the day.

```
```html
<script type="text/javascript">
<!--
function getDayName()
{
    var date=new Date();
    var arrDayNames=["Sunday","Monday","Tuesday","Wednesday",
    "Thursday","Friday", "Saturday"];
    return arrDayNames[date.getDay()]
}
// -->
</script>
```
```

# Defining functions outside the body element

So far, we have been embedding our scripts into the body of the document, which means that the JavaScript will run as soon as the page is loaded. However, once we start using functions, we can put them into the head element of the document or outside the document altogether, and invoke them from another script or an event.

In the following example, we see how a function (in this case added to the head of the document) can be invoked from a script in the body of the document. Because the script in the body is invoked when the document is loaded, the function is called at the same time. A JavaScript function is called simply by using its name and passing any required parameters. Unlike an object method, there is nothing that needs to precede the name of the function. If the function returns a value, it can be used by the code that invokes the function. In this XHTML page, a script invokes the ‘getDayName’ function. There are no parameter values to be passed, but the string that is returned from the function is written out to the document.