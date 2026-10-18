```
<?xml version="1.0"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<meta http-equiv="Content-Script-Type" content="text/javascript"/>
<title>JavaScript day name function</title>
<script type="text/javascript">
<!--
function getDayName()
{
var date=new Date();
var arrDayNames=["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"];
return arrDayNames[date.getDay()]
}
// -->
</script>
</head>
<body>
<!-- File: Example6-13.htm -->
<script type="text/javascript">
<!--
document.write(getDayName());
// -->
</script>
</body>
</html>
```

Figure 6.14 shows the result of loading the page on a Thursday.

# Using external JavaScript files

In all of the examples, we have seen so far, the JavaScript has appeared in the HTML source file. However, if we want to reuse any of our JavaScript functions then they need to be

FIGURE 6.14 A web page displaying the current day using the ‘getDayName’ function

![](bbox=[0.2, 0.78, 0.9, 0.93])