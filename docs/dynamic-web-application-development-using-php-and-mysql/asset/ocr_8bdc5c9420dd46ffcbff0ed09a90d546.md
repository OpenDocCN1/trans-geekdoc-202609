For the sake of the readability and reuse we save this function as the JavaScript file:

```
getxmlhttprequest.js
```

We then load this function in each of our scripts with the JavaScript instruction:

```
<script type="text/javascript" src="getxmlhttprequest.js">
</script>
```

This means that once we have created this function, we can use it again and again in each of our examples without the need to recreate or change it in anyway. In addition to the ‘getxmlhttprequest.js’ file, each of the following examples also has a unique JavaScript file that contains the two functions that open a connection to the PHP script on the server, using an xhr equest.open( ) function, and process the response from the server. These two functions are stored in a single JavaScript file with a name appropriate to the example script, for instance:

+   - example18-1.js
+   - example18-2.js
+   - ...
+   - example18-6.js

The PHP scripts which are invoked by the xhr equest.open( ) function are also given a file name appropriate to the example, for instance:

+   - example18-1.php
+   - example18-2.php
+   - ...
+   - example18-6.php

and the (X)HTML file which wraps everything together and is what the user invokes to start the examples are named:

+   - example18-1.htm
+   - example18-2.htm
+   - ...
+   - example18-6.htm

Therefore, each example consists of four files: two JavaScript files, a PHP server script and an (X)HTML file. We shall begin with our simplest example to illustrate how these files all work together.

# 18.2 A simple calculator

The following example implements a simple calculator. This calculator allows a user to type numbers into a couple of form fields and then, by selecting an operator (add, subject, multiply and divide) from a form select field, perform some basic mathematics on the entered numbers. The following is the (X)HTML script, named ‘example18-1.htm’ which the user invokes from the browser:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
```