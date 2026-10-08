Right, the time has come to write a PHP program. If you haven't already installed PSPad, you'll need to follow the instructions on page 162 and do so. With PSPad installed, launch the program. Click the FTP tab on the left hand side of the screen, then click the Connect FTP icon in the row below it, and choose your site name from the list that appears. Then double-click on the public_html folder, or whatever your host uses to store your web-accessible files.

In the white space below the list of files and folders on the left hand side, right-click and choose New File. In the box where you're asked to choose a file name, type demo.php and click the OK button. You should see your new file appear in the list in the left-hand panel.

Now double-click your demo.php file to open it for editing. Look at the blue title bar at the top of the screen, the text of which should end with demo.php rather than new1.txt to indicate that you're editing the correct file. If not, double-click it again.

You can now start typing your first PHP program. Enter the following:

```
```PHP
<?php
echo "<HTML>";
echo "<body>";
echo "This is some PHP";
echo "</body>";
echo "</HTML>";
?>
```
```

The screen should now look like this: