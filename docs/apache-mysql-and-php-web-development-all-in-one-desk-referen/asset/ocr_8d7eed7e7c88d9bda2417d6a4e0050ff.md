As you can see, this is identical to the way you send and extract data with the GET method, except that you use the word POST instead of GET. So why would you ever use GET? The advantage to GET is that by carefully constructing a URL, you can “fake out” a .php file and let the PHP code think the data came from a form. This URL can be a direct link in an <a> tag, or it can be in the print statement of a PHP program, or wherever. Here’s an example:

```
print '<a href="mydata.php?info=h1&name=jeff">click</a>';
```

# # Randomly Generate Picture-of-the-Day Images

Some people who have Web sites (especially if they’re “official” sites for movie stars and other famous people) like to have picture-of-the-day images, which are random images from a directory.

Here’s an example that generates a picture of the day. First, I created a directory called picoftheday, and I put three images in that directory, pic1.gif, pic2.gif, and pic3.gif. Then I created a file one directory up called picoftheday.php. Here’s the file:

```
```html
<html><head><title>Pic of the day!</title></head>
<body>
Here’s today’s picture!<p>
<?php
  $num = (time() % 3) + 1;
  $filename = "pic$num.gif";
  print "<img src=\"pic oftheday/$filename\">";
?>
</body></html>
```
```

I take the remainder of the current time divided by 3 (yielding the value 0, 1, or 2) and add 1 (to get 1, 2, or 3). Then I build the filename, and finally, I print out an HTML <img> tag. Easy!

![](bbox=[0.14, 0.715, 0.25, 0.79])

Just for fun, I chose to make my selection based on the current time. Alternatively, you can use the rand function, as I do in the section “Create a Random Link,” later in this chapter.

# # Write Text from a File

Occasionally, you may have some text files you want to write out somewhere inside a Web page. For example, I have a directory on my server called news, where I keep all my latest notes; these notes are simple text