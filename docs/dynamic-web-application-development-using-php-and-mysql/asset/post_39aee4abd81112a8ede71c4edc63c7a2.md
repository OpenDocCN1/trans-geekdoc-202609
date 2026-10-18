
```
echo "<p>";
while (!feof($fileTextFile)) {
    $strChar = fgetc($fileTextFile);
    echo "$strChar";
}
echo "</p>";

if (!fclose($fileTextFile))
    echo "<p>Error closing file!</p>";
?>
```

In the above example, note the use of the ‘while’ loop and feof() function to control the iteration through the file:

```
while (!feof($fileTextFile)) {
```

The output from the above script is shown in Figure 12.2.

‘Ah, but’ we hear you cry, ‘why is the output in the browser not formatted with each line of the file on a separate line?’ Well, the simple answer is that you haven’t formatted the output in that way. In order to do this you should read a whole line of the file and output this with XHTML <br/> elements so that each line of the file appears on a separate line of the browser. The easiest way to do this is with another function, fgets():

```
string = fgets (filestream, length);
```

Function fgets() requires one parameter, but can accept two. The first parameter is the file stream to read and the second is an integer indicating the maximum number of characters to read in one go. The function reads into a string a number of characters up to the size of length, or until a newline character is read or the end of file marker is encountered. The function returns a string of the characters it has read.

| NOTE | If the length parameter is not specified then the length defaults to 1 kB, or 1024 bytes. |

### FIGURE 12.2 Contents of a file

![](img/b2471264f405d17994ef173e4b9cec92_364_0.png)

### FIGURE 12.3 Formatted contents of a file

![](img/b2471264f405d17994ef173e4b9cec92_365_0.png)

The following script is a modification of the previous one that uses the fgets() function and formats the output of the file to the browser:

```
<?php
// File: example12-4.php
$fileTextFile = fopen ("files/text.txt",'r');

echo "<p>";
while (!feof($fileTextFile) ) {
    $strLine = fgets($fileTextFile);
    echo "$strLine<br/>";
}
echo "</p>";

if (!fclose($fileTextFile) )
    echo "<p>Error closing file!</p>";
?>
```

The output from the above script is illustrated in Figure 12.3.

## Getting the size of a file

The size of a file in bytes can be easily found by using the filesize() function:

```
filesize = filesize (filename);
```

The function returns an integer of the size of the file in bytes. This function is useful if you want to determine the size of a file, for example, to decide if you really want to read it or not.

## Reading an entire file

You can read an entire file by using the fread() function:

```
string = fread (filestream, length);
```

The fread() function consists of two parameters, the first of which is the file stream and the second is the number of characters to read. If this is set to the length of the file

then the whole file is read in one go. The function returns a string of the file contents. The following script illustrates the use of this function:

```
<?php
// File: example12-5.php

$fileTextFile = fopen ("files/text.txt",'r');

$intSize = filesize ("files/text.txt");
$strFile = fread($fileTextFile, $intSize);
echo "<p>$strFile</p>";

if (!fclose($fileTextFile) )
    echo "<p>Error closing file!</p>";
?>
```

The output from the above script is the same as that in Figure 12.3.

## Creating a new file

So far, the examples have shown that files can be read and displayed. However, using PHP file-handling facilities you can also write data to files. The function fwrite() allows strings to be written to a file; its syntax is:

```
fwrite(filestream, stringToWrite);
```

The fwrite() function requires two parameters, the first is the file stream and the second is the data to write to the file. The following script illustrates the use of this function:

```
<?php
// File: example12-6.php

$fileTextFile = fopen ("files/newtext.txt",'w');

$strDataOne = "Simon";
$strDataTwo = "Elizabeth";

fwrite($fileTextFile, $strDataOne);
fwrite($fileTextFile, $strDataTwo);

if (!fclose($fileTextFile) )
    echo "<p>Error closing file!</p>";
else
    echo "<p>Closed Successfully</p>";
?>
```

The above script opens a new file for writing:

```
$fileTextFile = fopen ("files/newtext.txt",'w');
```

Two variables are declared to hold strings which are going to be written to the file:

```
$strDataOne = "Simon";
$strDataTwo = "Elizabeth";
```

### FIGURE 12.4 Contents of the ‘newtext.txt’ file

![](img/b2471264f405d17994ef173e4b9cec92_367_0.png)

The two strings are written to the file:

```
fwrite($fileTextFile, $strDataOne);
fwrite($fileTextFile, $strDataTwo);
```

There is no browser output from the script but if you check the ‘files’ sub-directory, you should find a new file called ‘newtext.txt’ and when viewed should contain the data shown in Figure 12.4.

If you want the data ‘records’ you write to a file to appear on separate lines, you need to include the escaped characters ‘\r\n’ at the end of each line. This is illustrated in the following script which is a simple modification of the one above:

```
<?php
// File: example12-7.php

$fileTextFile = fopen ("files/newertext.txt",'w');

$strDataOne = "Simon\r\n";
$strDataTwo = "Elizabeth";

fwrite($fileTextFile, $strDataOne);
fwrite($fileTextFile, $strDataTwo);

if (!fclose($fileTextFile))
    echo "<p>Error closing file!</p>";
?>
```

The file should now contain the data formatted as shown in Figure 12.5.

## Adding to an existing file

We can also add records to an existing file using the fwrite() function. Consider the following script:

```
<?php
// File: example12-8.php

$fileTextFile = fopen ("files/text.txt",'a');

$strDataOne = "Simon\r\n";
$strDataTwo = "Elizabeth\r\n";

fwrite($fileTextFile, $strDataOne);
fwrite($fileTextFile, $strDataTwo);

if (!fclose($fileTextFile) )
    echo "<p>Error closing file!</p>";
?>
```

After running this script, the ‘text.txt’ file should contain the data formatted as shown in Figure 12.6.

| NOTE | If your file doesn't look exactly the same as the example in Figure 12.6, this could be because there wasn't an extra carriage return and new line on the last line of the original file. |

### FIGURE 12.5 Formatted contents of the ‘newtext.txt’ file

![](img/b2471264f405d17994ef173e4b9cec92_368_0.png)

### FIGURE 12.6 Amended contents of the ‘text.txt’ file

![](img/b2471264f405d17994ef173e4b9cec92_368_1.png)

## Checking if a file exists

To check a file exists, we use the file_exists() function:

```
file_exists (filename);
```

The file_exists() function requires the name of the file to check for and returns true or false depending on whether the file is found. The following is a simple script to check if a file is present:

```
<?php
// File: example12-9.php

if (!file_exists("files/text.txt") )
    echo "<p>File Doesn't exist!</p>";
else
    echo "<p>File Exists!</p>";
?>
```

## 12.2 Cookies

Cookies are a mechanism for a browser to store data on the client computer. Because the cookie is available the next time the web page is visited, cookies can be used to track or identify returning users to a web page. The important thing to remember about cookies is that they are stored on the client computer, as illustrated in Figure 12.7. Cookies are a type of file which is why we have included them in this chapter.

Browsers can control whether cookies can be written and thus you cannot guarantee that they are allowed. This is a major problem with cookies.

### Creating a cookie

To create a cookie we need to use the setcookie() function:

```
setcookie (name, value, expire, path, domain, secure)
```

### FIGURE 12.7 Cookies are stored on the client computer

![](img/b2471264f405d17994ef173e4b9cec92_369_0.png)

### TABLE 12.2 The setcookie() function parameters

| Mode | Description |
|------|-------------|
| Name | Name of the cookie file |
| Value | Data to be stored in cookie file |
| Expire | Date string that defines the valid life time of the cookie |
| Path | Subset of URLs in a domain for which the cookie is valid |
| Domain | The domain for which the cookie is available |
| Secure | If set to '1' the cookie is only transmitted if the communications channel with the host is secure (https) |

With the setcookie() function, all the arguments except ‘name’ are optional. If only the ‘name’ argument is present, a cookie by that name is deleted from the client. You may also replace any argument with an empty string (“”) in order to skip that argument. Table 12.2 lists the setcookie() function arguments and describes their use.

The setcookie() function returns true or false depending on whether the cookie was successfully created.

When using cookies you need to know the following:

- Cookies do not become visible until the next loading of a page for which the cookie is visible. To test if a cookie was successfully set, check for the cookie on a next loading page before the cookie expires. Expiry time is set via the ‘expire’ parameter.
- Cookies must be deleted with the same parameters with which they were set.
- Cookie names can be set as array names and are available to your PHP scripts as arrays but separate cookies are stored on the user’s system. You may wish to consider using the explode() or serialize() functions to set one cookie with multiple names and values.

The following script illustrates the use of the setcookie() function:

```
<?php
// File: example12-10.php

$strValue = "Hello, this is a cookie";

setcookie ("TestCookie", $strValue);

echo "<p>Cookie Set</p>";
?>
```

The above script declares a string variable which it writes to a cookie called ‘TestCookie’. There is no obvious output from the script so to see if we have successfully created a cookie and if we can read its data, then we need to know how to look at and access a cookie.

Cookie creation is part of the HTTP header which defines the (X)HTML script and so the setcookie() function must be called before any output is sent to the browser. If you are
