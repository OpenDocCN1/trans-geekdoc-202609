
what you were thinking if you come back to the code a couple of months after you wrote it.

In PHP, you can indicate comments with two slashes (//), with a hash (#), or by surrounding commented code with /* and */. This last method is particularly helpful for multi-line comments.

Comment all of your functions, what they do, what they are expecting, and what they return. Make sure to make note of any variables that could be tough to track.

As you look through the /functions directory of the CD, you will see that every function has an initial comment that mimics the style used in the PHP manual. For example,

```
int fetch_record (string table name [, mixed key [, mixed value]])
```

Then we provide some description as to what these arguments mean and the significance of the return value. When writing the body of the function, you should comment on anything that would not be intuitive to someone coming to the script at a later date. If you have a series of functions that perform some complex string handling or use lengthy regular expressions, make sure to note exactly what those functions are intended to accomplish. For example, we will reprise this line of code:

```
$file_ext = strtolower(substr($file, strrpos($file,".")));
```

This isn’t especially difficult to figure out, but you could sure help the next person coming to this line with a simple comment.

//get characters following the final dot
//and make lowercase
$file_ext = strtolower(substr($file, strrpos($file,".")));

The other important thing to comment is the overall logic of pages, especially long pages. Often a script will behave differently in varying circumstances. Variables passed from forms, errors, and other factors will effect what portions of script will run. At the top of the page, you can indicate what factors will affect the page’s logic and then as you reach different if blocks, explain where the conditions are coming from and what they mean.

For a brief example, take the confirm_delete.php page from Chapter 8, Guestbook2k:

/*
This script will only run if the user is logged in.
It will be accessed in two circumstances:
  -- The "Delete Entries" button was pressed on
     the edit.php page. (Normally this will be the
     first time to this script). The ids of the
     records to be deleted are passed in the entry_id
array.
-- The "Confirm Delete" button was pressed on this page. This will confirm the deletion and run the delete queries.
*/
include("header.php");
include("authenticate.php");

$page_title = "Confirm Changes";
include("start_page.php");

//if coming from edit_page.php. The first time to
//this script. Print a form with checkboxes that
//the user must check in order to confirm deletion.
if ($submit == "Delete Entries")
{
    //the form contains no action, so it will submit
    //to the same page, and the value of submit will be
    //"Confirm Delete"
    print "<form method=post>\n";
    if (is_array($entry_id))
    {
        while (list($key,$value) = each($entry_id))
        {
            print "<li>Delete entry #$value?\n";
            print "<input type=hidden name=\"entry_id[]\" value=\"$value\">\n";
        }
        print "<br><input type=submit name=submit value=\"Confirm Delete\">\n";
        print "<input type=hidden name=offset value=\"$offset\">\n";
        print "</form>\n";
    }
}

//if the page has been submitted to itself,
//to confirm that the deletion should happen.
elseif ($submit == "Confirm Delete")
{
    //loop through each element in the entry_id array
    //and run a delete query for each item.
    while (list($key,$value) = each($entry_id))
    {
        print "<li>Deleting entry #$value\n";
        $q = "delete from guestbook where entry_id = $value";
```
mysql_query($q) or die("Invalid query:$q");
}
}
else
{
    print "No action to confirm\n";
}
```

We will end this section on a word of caution: don't over comment. Commenting every single line, or making the obvious even more obvious is annoying. For example, the following comments are completely unnecessary and will only make your scripts difficult to read.

//make string lowercase
$str = strtolower($str);
//increase $i by 1
$i++

Commenting calls for good judgement. You don't want to comment too much, you don't want to comment too little. My best advice is to take a look at how many programmers comment their code and pick a style that you like. We use one method for the applications in this book; others have different styles.

The PEAR directory of your PHP installation is a great place to look for tips on good coding style. PEAR stands for PHP Extension and Application Repository. It is a growing set of scripts that contains a series of best practices for programming with PHP. The folks working on PEAR are real pros who write terrific code. We recommend looking through the scripts in that directory to glean some tips on writing quality code.

## Summary

In this chapter we have presented some ways to write clean and organized code. When you look at your scripts, you should ask yourself a few questions. Are there blocks of code that are common to every page? Maybe those blocks should be moved into an include. Are there chunks of code that I'm writing over and over again? Perhaps writing a function would save time. Is the next person who comes to this script going to be able to figure out what I've been doing? If not, make sure that you add enough comments to make things clear.

You will need to decide whether or not an object-oriented approach is good for you and the application you're writing. The fact is that if you're not immediately sure, the answer is probably no. Make sure you are comfortable writing clean procedural code before you jump into classes.

Now that you've done all the required reading, it is time to move into Part III, where we put PHP and MySQL to work.

## Chapter 8

## Guestbook 2000, the (Semi-)Bulletproof Guestbook

## IN THIS CHAPTER

- Learning the power of guestbook 2000
- Organizing your code in a reasonable way
- Writing good, reusable functions

IN THIS CHAPTER WE WILL develop the first of our applications—a guestbook. Guestbooks aren’t complex and they aren’t very exciting. However, this application does give us the chance to introduce some concepts such as validation and put many of the practices discussed earlier in this book to work.

In the Introduction of this book we introduced some code that could be used for the most basic guestbook possible. However, using that code for your guestbook is not a good idea. It’s got all kinds of holes that will allow malicious people out there to mess with your pages. There is another problem with the ultra-basic guestbook: given the way the code is just dumped into one page, there’s not a line that’s reusable. One of the top goals of developing any application is to create chunks of reusable code.

## Determining the Scope and Goals of the Application

The easiest way to get yourself into trouble when coming at an application is to not know exactly what you are trying to achieve. A vital part of the developer’s job is to figure out exactly what is needed in the application. Usually this will involve extensive discussion with the people for whom the application is being developed. During these discussions, it is important to think a step ahead and ask questions that may not have been considered. What if the scope increases in a certain way?

What if additional information but related information needs to be tracked? All of these things will affect the way you design your database and your scripts, and that is why it is best to know the exact scope and goals of your application. Depending on whom you're working with, you may want to get some sketches of pages that need to be developed.

The scope of this application is small and the goals are minimal. The guestbook stores names, addresses and the like. (But, to tell the truth, the goal of this chapter is not so much to show you how to write a guestbook as it is to show you how to write good, reusable, organized code for your applications.) In any case, you should know what guestbook2k looks like before you proceed.

> In this chapter, we're not going to take the notion of creating good functions as far as it can go. In the next chapter we'll present a more extensive set of functions that we'll use throughout the rest of the book.

## Necessary Pages

There are three basic pages: one for signing the guestbook, one for viewing the guestbook, and one for administering the guestbook.

Figure 8-1 shows the page that gives the user the opportunity to sign the guestbook. It's pretty simple, a form with four text fields and one textarea field. Additionally, there is a submit button and a reset button.

![](img/de0823012275cf4ceebdb822a56e6b71_224_0.png)

Figure 8-1: Page for signing the guestbook
