stored separately from HTML pages. In the previous example, we used a function called ‘getDayName’. Simple as it is, this function might be reusable in multiple pages, so instead of putting it into the HTML document’s header, we could put it into a separate file. Files that contain JavaScript code are usually given a ‘.js’ extension, so in this example we assume a file called ‘dayname.js’. Note that when JavaScript is stored separately from the XHTML source file, there is no ‘script’ element, just the JavaScript source code. The script element remains in the web page to specify the file that contains the JavaScript function.

```
// File: dayname.js
function getDayName()
{
    var date=new Date();
    var arrDayNames=
    ["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday",
    "Saturday"];
    return arrDayNames[date.getDay()]
}
```

To use functions defined in external files, the script element needs to include the ‘src’ attribute, which specifies the path and filename of the JavaScript source file

```
<script type="text/javascript" src="path/filename.js"></script>
```

It is important to note that the script element is never an empty element, in other words it always has separate opening and closing tags, even though nothing appears between them. This is necessary because some browsers cannot process the script element unless it has both start and end tags.

Here is an XHTML page that uses the ‘getDayName’ function by referencing the external JavaScript file using the script element’s ‘src’ attribute.

```
<?xml version = "1.0"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
    <meta http-equiv="Content-Script-Type" content="text/javascript"/>
    <title>JavaScript day name function</title>
    <script type="text/javascript" src="dayname.js">
    </script>
</head>
<body>
    <script type="text/javascript">
        <!--
            document.write(getDayName() );
        // -->
    </script>
</body>
</html>
```