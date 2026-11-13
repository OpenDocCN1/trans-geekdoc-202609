```
<br>
<input type=submit name=submit value="Confirm Delete">
<input type=hidden name=offset value="$offset">
</form>
EOF;
}
else
{
    // just in case this script is called directly or in some other
    // unanticipated manner
    print "<h4>No action to confirm</h4>\n";
}

// display navigational links and end the page
nav($offset, 'edit.php');
guestbook_end_page();
```

We end this section on a word of caution: don't over-comment. Commenting every single line, or making the obvious even more obvious, is annoying. For example, the following comments are completely unnecessary and only make a script difficult to read:

```
//make string lowercase
$str = strtolower($str);
//increase $i by 1
$i++
```

Commenting calls for good judgment. You don't want to comment too much; you don't want to comment too little. Our best advice is to take a look at how other programmers comment their code and to pick a style that you like. We use one method for the applications in this book; others have different styles.

The PEAR directory of your PHP installation is a great place to look for tips on good coding style. PEAR stands for PHP Extension and Application Repository. It is a growing set of scripts that contains a series of best practices for programming with PHP. The folks working on PEAR are real pros who write terrific code. We recommend looking through the scripts in that directory to glean some tips on writing quality code.

# Summary

In this chapter, we have presented some ways to write clean and organized code. When you look at your scripts, you should ask yourself a few questions.