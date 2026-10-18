
For the sake of the readability and reuse we save this function as the JavaScript file:

```
getxmlhttprequest.js
```

We then load this function in each of our scripts with the JavaScript instruction:

```
<script type="text/javascript" src="getxmlhttprequest.js">
</script>
```

This means that once we have created this function, we can use it again and again in each of our examples without the need to recreate or change it in any way. In addition to the ‘getxmlhttprequest.js’ file, each of the following examples also has a unique JavaScript file that contains the two functions that open a connection to the PHP script on the server, using an xhrRequest.open() function, and process the response from the server. These two functions are stored in a single JavaScript file with a name appropriate to the example script, for instance:

- example18-1.js
- example18-2.js
- ...
- example18-6.js

The PHP scripts which are invoked by the xhrRequest.open() function are also given a file name appropriate to the example, for instance:

- example18-1.php
- example18-2.php
- ...
- example18-6.php

and the (X)HTML file which wraps everything together and is what the user invokes to start the examples are named:

- example18-1.htm
- example18-2.htm
- ...
- example18-6.htm

Therefore, each example consists of four files: two JavaScript files, a PHP server script and an (X)HTML file. We shall begin with our simplest example to illustrate how these files all work together.

## 18.2 A simple calculator

The following example implements a simple calculator. This calculator allows a user to type numbers into a couple of form fields and then, by selecting an operator (add, subtract, multiply and divide) from a form select field, perform some basic mathematics on the entered numbers. The following is the (X)HTML script, named ‘example18-1.htm’ which the user invokes from the browser:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
```
```html
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title>Calculator Script</title>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />

<script type="text/javascript" src="getxmlhttprequest.js">
</script>
<script type="text/javascript" src="example18-1.js">
</script>
</head>
<body>
<!-- File: example18-1.htm -->

<h2>Simple Calculator:</h2>
<form action="" method="post">
<p>
<input type="text" name="intValue1" id="intValue1"
onchange="startJS();" />
<select name="strOperator" id="strOperator" onchange="startJS();">
<option value="1">+</option>
<option value="2">-</option>
<option value="3">/</option>
<option value="4">*</option>
</select>
<input type="text" name="intValue2" id="intValue2"
onchange="startJS();"/>
<input type="button" value="=" onclick="startJS();" />
<input type="text" name="intResult" id="intResult" />
</p>
</form>
</body>
</html>
```

After the initial document declaration and heading information the script begins by including the 'getxmlhttprequest.js' and 'example18-1.js' JavaScript files which are going to be used to form an XMLHttpRequest object and to process the user events (entering the numbers and selecting the operation to be performed):

```
```html
<script type="text/javascript" src="getxmlhttprequest.js">
</script>
<script type="text/javascript" src="example18-1.js">
</script>
```
```

Next, a form is declared which consists of five form elements. These elements are the two input text fields where the user enters the numbers to use in the calculation, a select element to enable selection of a mathematical operator, an input button to force the calculation to be updated (by clicking on it) and an input text field where the sum of the calculation is displayed:

```
```html
<form action="" method="post">
<p>
<input type="text" name="intValue1" id="intValue1"
onchange="startJS();" />
```
```
```
<select name="strOperator" id="strOperator" onchange="startJS();">
<option value="1">+</option>
<option value="2">-</option>
<option value="3">/</option>
<option value="4">*</option>
</select>
<input type="text" name="intValue2" id="intValue2"
onchange="startJS();"/>
<input type="button" value="=" onclick="startJS();" />
<input type="text" name="intResult" id="intResult" />
</p>
</form>
```

Note that three ‘onchange’ events have been included on certain form elements which invoke function startJS() whenever an input text field or select field is changed. An onclick event also invokes function startJS() if the button is clicked.

Function startJS() as well as another function changePage() are defined within the ‘example18-1.js’ file and are as follows:

```
function startJS() {
  xhrRequest = null;
  try {
    xhrRequest = getXMLHttpRequest();
  }
  catch(error) {
    document.write("Cannot run Ajax code using this browser");
  }

  if(xhrRequest != null) {
    // get form values
    var intValue1 = document.getElementById("intValue1").value;
    var intValue2 = document.getElementById("intValue2").value;
    var strOperator = document.getElementById("strOperator").value;
    var strUrl = "example18-1.php?intValue1=" + intValue1 + "&intValue2=" +
                intValue2 + "&strOperator=" + strOperator;

    xhrRequest.onreadystatechange = changePage;
    xhrRequest.open("GET", strUrl, true);
    xhrRequest.send(null);
  }
}
```

```
function changePage() {
  if (xhrRequest.readyState == 4 && xhrRequest.status == 200) {
    var intResponse = xhrRequest.responseText;
    document.getElementById("intResult").value = intResponse;
  }
}
```

Function startJS() begins by determining whether the browser supports Ajax by trying to create a getXMLHttpRequest object by invoking the getXMLHttpRequest() function in the ‘getxmlhttprequest.js’ file. If an error is generated a message is displayed and the operation terminates:

```
```javascript
xhrRequest = null;
try {
  xhrRequest = getXMLHttpRequest();
}
catch(error) {
  document.write("Cannot run Ajax code using this browser");
}
```
```

If all is well then the values in the two input text form field values and the operator from the select field are obtained and stored in separate variables:

```
```javascript
if(xhrRequest != null) {
  // get form values
  var intValue1 = document.getElementById("intValue1").value;
  var intValue2 = document.getElementById("intValue2").value;
  var strOperator = document.getElementById("strOperator").value;
}
```
```

Next, a string defining the connection to the PHP script on the server is created. This consists of the name of the script and the three variables created from the data obtained from the calculator form:

```
```javascript
var strUrl = "example18-1.php?intValue1=" + intValue1 +
  "&intValue2=" + intValue2 + "&strOperator=" + strOperator;
```
```

Finally, three methods of the XMLHttpRequest object are invoked:

```
```javascript
xhrRequest.onreadystatechange = changePage;
xhrRequest.open("GET", strUrl, true);
xhrRequest.send(null);
```
```

These methods define what function should be invoked when the PHP script has done something, open a connection to the PHP script and send the form data to the script. In this example, when the PHP script does something, this is handled by the JavaScript function changePage() which is also included within the ‘example18-1.js’ file:

```
```javascript
function changePage() {
  if (xhrRequest.readyState == 4 && xhrRequest.status == 200) {
    var intResponse = xhrRequest.responseText;
    document.getElementById("intResult").value = intResponse;
  }
}
```
```

Function changePage() simply determines if the PHP script has finished executing and if so stores the output from the script in variable intResponse. This value is then injected into the form text result field, thus displaying the answer to the calculation to the user.

## **FIGURE 18.1** Simple calculator

![](img/b2471264f405d17994ef173e4b9cec92_550_0.png)

The PHP script, ‘example18-1.php’, which is invoked and does the calculation is as follows:

```
```php
<?php
// File: example18-1.php
$intValue1 = $_GET["intValue1"];
$intValue2 = $_GET["intValue2"];
$strOperator = $_GET["strOperator"];

switch ($strOperator){
    case 1: echo $intValue1 + $intValue2;
        break;
    case 2: echo $intValue1 - $intValue2;
        break;
    case 3: echo $intValue1 / $intValue2;
        break;
    case 4: echo $intValue1 * $intValue2;
}
?>
```
```

The script obtains the values of the three variables passed to it via the GET method and uses a ‘switch’ statement to output the result of the mathematical calculation using an ‘echo’ construct.

The output from the above example is illustrated in Figure 18.1.

So, to summarize, the example creates a simple web form and waits for a user to trigger an event. When an event is triggered, an Ajax connection is formed and a PHP script is invoked. When the PHP script finishes, the output from the script is displayed on the form.

## 18.3 A simple database stock example

This example illustrates a simple dynamic database stock check and demonstrates that Ajax can be used to run PHP scripts that obtain up-to-the-minute information stored on a database. The advantage of using Ajax for this example is that the database is queried when the user interacts with the application thus ensuring that the information displayed is accurate but the user is not inconvenienced by a page reload:

```
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
    "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
```
