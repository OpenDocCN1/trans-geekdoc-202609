# Container Bridge File

**Objective:** The ContainerBridge.php is a file that you'll include as is with your solution. There's absolutely nothing to do in this file. It simply works on its own. It is used to convert images in container fields so you can display them on a web page.

> I don't recommend that you display images using container fields. You are much better off storing the images on the server and using a text field with a path to the image. The ContainerBridge.php works. However, you will take a big performance hit. The FileMaker API for PHP is nice that it will work with container images. The XDBC drivers for ASP and JSP do not work with FileMaker's proprietary container field.

Difficulty: Easy

**Sample Files:** PHPFiles/Core/Lesson12/ContainerBridge.php

**Page Navigation:** Include file only.

FileMaker API Methods: N/A

Code:

Since this is already a stand-alone file, rather than going through each line of code I'll describe its intended use. In PHP code you want to display an image from a container you will use the following example code:

```
<img src="ContainerBridge.php?path=' . urlencode($_GET['record']) . ' />
```

The point of this is to do two things. First, define the image source. You can see that the code is passing the image source to ContainerBridge.php with the variable "path" as an urlencoded container field in the database named "Image". If you follow the value passed to the ContainerBridge.php file you will see that it starts by verifying that the path information was set. Next it uses the PHP substr to strip away the path stored in the file to return just the extension of the image. Once the extension is determined it will return the appropriate jpg or gif in the header. Finally, the fm object will use the getContainerData method to retrieve the image from the container field. Again, you dont necessarily need to know why or how. The upcoming lessons will demonstrate exactly how to display an image from a container field both internally and externally. For now, you'll include this file in your web sites "as is" if you intend to display images from a container.

> substr Returns a portion of the string by the start and length parameters. This is very similar to the FileMaker Middle function.

```
http://us.php.net/manual/en/function.substr.php
```

> header Used to draw a raw HTTP header.

```
http://us.php.net/manual/en/function.header.php
```

```
<?php
require_once("../dbaccess.php");
if (isset($_GET['path']))
{
  $url = $_GET['path'];
  $url = substr($url, 0, strpos($url, "?"));

```

*