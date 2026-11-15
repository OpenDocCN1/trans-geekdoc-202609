# Actual versus Virtual Paths

To determine the actual path of the current script, there is a very simple trick: Use the __FILE__ constant (two underscores before and after FILE). You can see the output of the following code in Figure 25.6:

```
<?php
echo "The current script is called " . __FILE__;
?>
```

![](bbox=[0.16, 0.26, 0.84, 0.37])

**Figure 25.6** The Complete File Name via "__FILE__"

With the dirname() PHP function, you will then receive the directory. Instead of $d = dir("."), you can also use the following to start in the current directory:

```
$d = dir(dirname(__FILE__));
```

You can obtain the name of the current directory even more briefly using the __DIR__ constant. PHP also offers a function that converts a virtual path (i.e., a web server path such as /php/dir/php) into an absolute path (such as /usr/htdocs/php/dir.php): realpath(). It should be noted that the path or file must exist; otherwise, no conversion can be performed and realpath() returns false.

# 25.3 Application Examples

So much for the first insight into the most important techniques for working with files in PHP. It's time to put this into practice.

# 25.3.1 Guestbook

A guestbook is a welcome opportunity on mainly private websites to leave messages for the webmaster and to exchange information with each other. This is particularly easy to implement with a database—so easy, in fact, that the entire database section of this book (see Part IV) contains a complete guestbook example. But it can also be real- ized with files, although not quite as conveniently.

The aim is clear: A user should be able to enter messages in a guestbook. The guestbook data is stored in a text file. To make it as easy as possible to read out later, we use the