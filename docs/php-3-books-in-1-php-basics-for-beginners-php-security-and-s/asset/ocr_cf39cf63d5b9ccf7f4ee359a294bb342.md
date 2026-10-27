```
```php
file("post_comment.txt", "text/plain"); print "<h1>Post Comment</h1>"; ?> <?php $my_file = file("post_image.txt", "text/plain"); print "<h1>Image Post</h1>"; ?> <?php $my_file = file("post_video.txt"); print "<h1>Video Post</h1>"; ?> <?php $my_file = file("post.txt", "text/plain"); print "<h1>Blog Post</h1><br><br>"; ?>
```
```

That script will create a new post and save it to the text/plain directory. The files() function is also useful if you want to save a copy of an already existing file, like if you're editing an existing HTML document and want a backup of the changes.

Saving a file with the files() function is pretty simple:

```
```php
<?php $my_file = files("post.txt", "text/plain"); print "<h1>Post Title</h1>"; ?> <?php $my_file = files("post_comment.txt", "text/plain"); print "<h1>Post Comment</h1><br><br>"; ?> <?php $my_file = files("post_image.txt", "text/plain"); print "<h1>Image Post</h1>"; ?> <?php $my_file = files("post_video.txt"); print "<h1>Video Post</h1><br>"; ?> <?php $my_file = files("post.txt", "text/plain"); print "<h1>Blog Post</h1><br><br>"; ?>
```
```

# ### 3. *Creating and Saving Files to the Root Folder*

The files() function doesn't just create a new file; it can create and save it to a folder on your computer. In the above example (minus the "videoword" file), I'm creating everything and then saving it to the root folder:

```
```php
<?php $my_file = files("post.txt"); print "<h1>Post Title</h1>"; ?> <?php $my_file = files("post_image.txt"); print "<h1>Image Post</h1><br>"; ?> <?php $my_file = files("post_video.txt"); print "<h1>Video Post</h1><br>"; ?> <?php $my_file = files("post_comment.txt"); print "<h1>Comment Post</h1><br><br>"; ?> <?php $my_file = files("blogpost.txt"); print "Blog Post<br><br>"; ?>
```
```

You can also use the files() function to create a new directory using the same syntax as above. Here's an example that does just that:

```
```php
<?php $my_dir = files("blogpost.txt"); print "Created blog post directory " . $my_dir; ?> <?php $my_file = files("blogpost.txt"); print "<h1>Blog Post</h1><br><br>"; ?>
```
```

# ### 4. *Finding the Last Modified Date of a File*

Sometimes you may want to find out the last time that a file was accessed or modified. You can use the files() function, like so:

```
```php
<?php $my_file = files("post.txt"); $time_last_accessed = filemtime($my_file); print "Last time I was accessed: " . $time_last_accessed . "<br>"; ?> <?php $my_file = files("post.txt"); $time_last_modified = filemtime($my_file); print "Last time I was modified: ".$time_last_modified."<br>"; ?>
```
```

The files() function returns the last access and last modification dates for a file.

# ### 5. *Writing to Files*

You can also use the files() function to write data to a file, which is done a little differently than creating and writing to a file. Here's an example:

```
```php
<?php $my_file = files("post.txt"); print "This will be written to the file: ".$my_file."<br>"; ?> <?php $my_file = files("post.txt"); $my_file = $my_file."This will be written to the file: ".$my_file; print "This is what I'm writing: ".$my_file."<br>"; ?>
```
```