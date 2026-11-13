If we've made it this far, then the upload was successful, and all we need to do is print some HTML to give the user a link:

```
$image_url = "$urlroot/$sname";

/* Display status. */
print "HTML for image:</strong><br><textarea cols=\"80\" rows=\"4\">";
print "<img src=\"$image_url\" $attr alt=\"$upfile_name\" border=\"0\"/>;";
print "</textarea><br>";
print '<a href="upload.html">Upload another image?</a>';?>
```

# Using the Script

This script requires that all target directories in $target_dirs be writeable by PHP. In addition, you need the GD module, a PHP add-in that allows PHP to analyze and create image files. Most servers have this installed by default, but if yours does not, refer back to “#18: Adding Extensions to PHP” on page 27. That’s it; all you need to do is point the browser at upload.html, and PHP will do the rest.

# What Can Go Wrong?

Aside from the usual permissions problems, the biggest issue is security. As it stands, any schmo who has access to this script’s URL can upload as many images as they like and possibly overwrite yours. If this script is outside a firewall, you may want to combine this script with a login function to prevent unauthorized access, as shown in “#63: A Simple Login System” on page 116.

# Hacking the Script

You can impose a cap on the size of any given file by looking at the $_FILES['upfile']['size'] variable. Just put in a line like this:

```
If ($_FILES['upfile']['size'] > $max_size) {
	$_fatal_error = "This file is larger than $max_size bytes.";
}
```

NOTE You may also want to have a look at “#13: Preventing Users from Uploading Large Files” on page 25, which shows you how to set a global upload file size limit.

# #55: Reading a Comma-Separated File

One common programming task is to transform data from Excel spreadsheets into some useful form, such as HTML or rows in a MySQL table. If we all had to work in Excel (XLS) format, then this would be a real problem. Fortunately, in both Excel and OpenOffice.org, you can export an Excel