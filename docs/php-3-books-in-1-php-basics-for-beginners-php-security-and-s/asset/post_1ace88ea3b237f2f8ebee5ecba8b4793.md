
To draw a triangle in PHP, you first need to set up some variables. Here's an example:

```
$x1 = 0; $y1 = 0; $x2 = 220; $y2 = 20; $color = 'rgba(255,0,0,1)';
$black_polygon_image=imagecreatefrompng('blacktriangle.png');
$red_polygon_image=imagecreatefrompng('color.png');
$orange_polygon_image=imagecreatefromgif('orange.gif');
$green_polygon_image=imagecreatefrompng('green.png'); $blue_polygon_image=imagecreatefrompng('blue.png');
$yellow_polygon_image=imagecreatefrompng('yellow.png');
$red_color=imagecolorallocate($red_polygon_image, 255,255,0);
$orange_color=imagecolorallocate($orange_polygon_image, 0, 100,100);
$green_color=imagecolorallocate($green_polygon_image, 0, 100, 100); $blue_color=imagecolorallocate($blue_polygon_image, 0, 255, 0); $yellow_color=imagecolorallocate($yellow_polygon_image, 255, 0, 0);
imagecopy($black_polygon_image, $red_polygon_image, 220 - 40, 220 - 40, 0 - 40, 240 - 80, $x1, $y1);
imagecopy($black_polygon_image, $green_polygon_image, 220 - 40, 220 - 40, 0 - 40, 240 - 80 + 130 + 50 + 15);
echo 'Red Polygons';
```

The first lines set the variables needed. In this example, x1 is the starting point, and y1 is the height of the first triangle. Similarly, x2 is the ending point, and y2 is the height of the second triangle. Each of these triangles is joined together on one side. The next lines set up some variables to be used in creating and laying out an image. The $color variable contains which color to use to draw each pixel on your image, which in this example will be white. The $black_polygon_image variable holds onto a reference to an image that will be created later. The last lines copy the data from the black triangle image to the color image. The code above lays out an image of a triangle, or in this case, a filled triangle.

## Files

![](img/232f65b1c63e7757b6150e92c9cc0d00_342_0.png)

The files function is one of the most important parts of any PHP script. This function allows you to store a copy of your shiny new blog post, for example, to a file on your hard drive.

This function is used to create files that can be used to permanently save data, and they are also often used as a temporary storage space. When you remove a file from your computer, it is no longer accessible, but it can still be viewed in the recycle bin. In this tutorial, we'll discuss how to use this handy function in your PHP scripts!

The first argument of the files() function is required, and it specifies the name of the file that you want to create or open. The second input is optional and specifies the location of the file on your system. By default, the file will be saved to your Documents or Desktop folder, but you can specify an alternate directory if you need to. The third argument is also optional, and it specifies how long the file should be kept available. It gives a timestamp that's used to tell when the last access was made.

Here's a brief example of how the files function works:

```php
<?php $my_file = file("file.txt"); print "The file contains the following text: "; print $my_file; ?>
```

### PHP File Function Syntax

The syntax for the files function is:

```
function( $name , $type = "" , $dir = "." , $exclude = "" , $keep_last_access = false )
```

Below I'll go into the details of each of those arguments in a little more detail.

- $name - The name of the file that you're creating is required, and it can't be changed after you've created your file. Suppose you don't specify the $name argument, then the file will be saved to your system under the same name as your script.
- $type - The type of file you want to create. This is optional, and if it isn't specified, then PHP will use a default value of 'text/plain.' Supported values include: text, HTML, php, and xml.
- $dir - The directory that you want to save your file in; if this isn't specified, then it'll be saved to your "Documents" folder.
- $exclude - This option may be used to tell the PHP interpreter not to save certain files to the directory. For example, maybe you want certain images and CSS files saved to a different location than your other files. Use this option if you want to specify an alternate directory that should be excluded from saving.
- $keep_last_access - You can use this argument in order to specify how long (in seconds) a file should be kept around after it's been deleted. This is useful for debugging purposes. If it's set to 'true,' then you'll be able to find out when the file was last accessed.

### Uses of the Files Function

#### 1. Generating a New File

The most obvious use of the files function is to create a new file, but it can also be used to rename an existing file or remove an existing file. These are useful if you want to easily move your blog posts around then they can make it easier! Here's a quick example:

```
<html><body><?php $my_file = file("file.txt"); print "New file name: ".$my_file.".<br>"; ?> <h1>Post Name</h1> <?php $my_file = file("post.txt", "text/plain"); print "<p>New post name: ".$my_file."</p><br><br>"; ?> </body> </html>
```

Building a file structure like this is pretty easy, but if you don't have many files saved to your system, you may want to consider using a more reliable program to do it for you.

#### 2. Creating and Saving Files

You can create new files and then save them to your system with the files() function. In the example below, I'm going to create a new set of blog posts by first creating a file:

```php
<?php $my_file = file("post.txt", "text/plain"); print "<h1>Post Title</h1>"; ?> <?php $my_file = file("post_comment.txt", "text/plain"); print "<h1>Post Comment</h1>"; ?> <?php $my_file = file("post_image.txt", "text/plain"); print "<h1>Image Post</h1>"; ?> <?php $my_file = file("post_video.txt"); print "<h1>Video Post</h1>"; ?> <?php $my_file = file("post.txt", "text/plain"); print "<h1>Blog Post</h1><br><br>"; ?>
```

That script will create a new post and save it to the text/plain directory. The files() function is also useful if you want to save a copy of an already existing file, like if you're editing an existing HTML document and want a backup of the changes.

Saving a file with the files() function is pretty simple:

```php
<?php $my_file = files("post.txt", "text/plain"); print "<h1>Post Title</h1>"; ?> <?php $my_file = files("post_comment.txt", "text/plain"); print "<h1>Post Comment</h1><br><br>"; ?> <?php $my_file = files("post_image.txt", "text/plain"); print "<h1>Image Post</h1>"; ?> <?php $my_file = files("post_video.txt"); print "<h1>Video Post</h1><br>"; ?> <?php $my_file = files("post.txt", "text/plain"); print "<h1>Blog Post</h1><br><br>"; ?>
```

#### 3. Creating and Saving Files to the Root Folder

The files() function doesn't just create a new file; it can create and save it to a folder on your computer. In the above example (minus the "videoword" file), I'm creating everything and then saving it to the root folder:

```php
<?php $my_file = files("post.txt"); print "<h1>Post Title</h1>"; ?> <?php $my_file = files("post_image.txt"); print "<h1>Image Post</h1><br>"; ?> <?php $my_file = files("post_video.txt"); print "<h1>Video Post</h1><br>"; ?> <?php $my_file = files("post_comment.txt"); print "<h1>Comment Post</h1><br><br>"; ?> <?php $my_file = files("blogpost.txt"); print "Blog Post<br><br>"; ?>
```

You can also use the files() function to create a new directory using the same syntax as above. Here's an example that does just that:

```php
<?php $my_dir = files("blogpost.txt"); print "Created blog post directory " . $my_dir; ?> <?php $my_file = files("blogpost.txt"); print "<h1>Blog Post</h1><br><br>"; ?>
```

#### 4. Finding the Last Modified Date of a File

Sometimes you may want to find out the last time that a file was accessed or modified. You can use the files() function, like so:

```php
<?php $my_file = files("post.txt"); $time_last_accessed = filemtime($my_file); print "Last time I was accessed: " . $time_last_accessed . "<br>"; ?> <?php $my_file = files("post.txt"); $time_last_modified = filemtime($my_file); print "Last time I was modified: ".$time_last_modified."<br>"; ?>
```

The files() function returns the last access and last modification dates for a file.

#### 5. Writing to Files

You can also use the files() function to write data to a file, which is done a little differently than creating and writing to a file. Here's an example:

```php
<?php $my_file = files("post.txt"); print "This will be written to the file: ".$my_file."<br>"; ?> <?php $my_file = files("post.txt"); $my_file = $my_file."This will be written to the file: ".$my_file; print "This is what I'm writing: ".$my_file."<br>"; ?>
```
