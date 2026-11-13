
## 12 INTERMEDIATE PROJECTS 155

- #74: A User Poll .................................................................... 156
- Creating a Ballot Form ........................................................... 157
- Processing the Ballot .............................................................. 159
- Getting Poll Results ................................................................. 160
- Hacking the Script ..................................................................... 162
- #75: Electronic Greeting Cards ................................................ 162
- Choosing a Card ......................................................................... 164
- Sending the Card ........................................................................ 165
- Viewing the Card ........................................................................ 169
- Hacking the Script ..................................................................... 171
- #76: A Blogging System .............................................................. 171
- Creating Blog Entries ................................................................. 172
- Displaying an Entry ..................................................................... 174
- Adding Comments ......................................................................... 178
- Creating a Blog Index ................................................................... 178
- Hacking the Script ..................................................................... 181

## APPENDIX 183

## INDEX 185

## INTRODUCTION

![](img/19183d2b75bf6b509317c631c0e7b817_14_0.png)

This book is for the developer who has stumbled on to PHP and wants to know how to get things done. You should know the basics of programming, and chances are you’ve seen many online code samples. But you may be wondering why some examples are much more complicated than others when they do the same thing.

Care has been taken to keep the examples in this book as simple as possible and to explain as much as possible about every piece of code. To keep client and server code confusion to a minimum, there isn’t much JavaScript here. Everyone’s impatient, so Chapter 1, “The FAQs of Life—The Scripts Every PHP Programmer Wants (or Needs) to Know,” contains quick solutions to everyone’s favorite little tasks and problems. After you calm down, take a look at Chapter 2, “Configuring PHP,” to find out how you should install and configure PHP—quite a large number of problems arise from misconfiguration. Continuing in this vein, Chapter 3, “PHP Security,” deals with keeping your scripts secure.

Chapter 4, “Working with Forms,” returns to basics—specifically, how to get user input from forms and other dynamic input sources. Chapter 5, “Working with Text and HTML,” shows how to process text and strings with a number of tools, including regular expressions. Chapter 6, “Working with Dates,” discusses how to work with times and dates in PHP and MySQL, and Chapter 7, “Working with Files,” deals with file manipulation.

With these fundamentals covered, Chapter 8, “User and Session Tracking,” covers the details of session tracking and management. With multiple users on a complex website, it’s important to keep track of what each user is doing so that one user’s session doesn’t interfere with another’s.

Chapter 9, “Working with Email,” and Chapter 10, “Working with Images,” cover email and image manipulation, respectively. These tasks are often ill-suited for webserver scripts, so the chapters describe relatively lightweight tasks that can add significant value to your site.

In Chapter 11, “Using cURL to Interact with Web Services,” you’ll learn how to make your server interact with web services on other sites via XML.

Finally, Chapter 12, “Intermediate Projects,” contains three fun little projects that can be incorporated into larger websites. These projects build on what you’ve learned elsewhere in the book.

## 1

### THE FAQs OF LIFE—THE SCRIPTS EVERY PHP PROGRAMMER WANTS (OR NEEDS) TO KNOW

![](img/19183d2b75bf6b509317c631c0e7b817_16_0.png)

The scripts contained in this chapter answer several questions that clog PHP forums and discussion groups all over the world. They include the following:

- How do I add Previous/Next links to my shopping cart?
- Is there an easy way to make every other row in my table a different color?
- I have a big array that I need to sort—help!
- What's the best templating system to make the same HTML enclose my data on every page?

Although there are more complicated scripts later in this book, and many others that you may find more valuable, these scripts answer the questions that I see again and again. The only thing these beginning scripts have in common is that they're either the things that everyone should know or the things that everyone wants to know. Hand this chapter to a beginning PHP programmer you love. She'll thank you for it.

**NOTE** If you're not afraid to start rooting around on your webserver, Chapter 2 will also help the beginning PHP scripter and can make life a lot easier for the midlevel PHP programmer. You might want to go there next.

### #1: Including Another File as a Part of Your Script

Most serious applications have a core library of variables and scripts that are used on almost every page. For example, if you're writing a shopping cart that connects to a MySQL database, you could declare the MySQL login name and password on each page of your cart. But what if you need to change the password? Changing and uploading every file in your shopping cart could become a huge issue.

Rather than declaring the password in each of your page scripts, you can store that name and password in a separate file. You can then include that file as a part of your script, and whatever variables you declare in that file will be declared in your script!

Furthermore, you can store long scripts or functions in a separate file and include them only when you need them. For example, the function that gets real-time UPS shipping quotes is 24KB worth of XML processing goodness, but you use it only when someone chooses UPS as a shipping option. Why not store it in ups_ship_quotes.php and call it only when necessary?

In fact, almost all heavy-duty PHP applications have a file called something like config.php, which declares the critical variables that every page needs to know, such as the MySQL name and password. Those same applications also store frequently used scripts in different directories. Programmers then mix and match, taking the check-to-see-if-a-user-is-logged-in script from one directory, including the get-the-relevant-data-from-the-database script from another directory, and writing a central script that screens the data based on whether the user is logged in or not.
And here's how to do it.

```
<?php
require_once("/path/to/file.php");
?>
```

The file that you give to require_once() is now a part of your script, exactly as if you had cut and copied the contents of the file into your script. You can even include HTML files to create a crude templating system.

No matter what you name the file, PHP tries to read it as if it were valid PHP. As with any PHP file, you need the <?php and ?> markers around the PHP code in your included file; otherwise, PHP simply prints the entire file (even if it's a binary).

You can use require_once() just like any other statement, so feel free to embed it into control structures.

```
if ($we_need_this_file === true) {
    require_once("needed_file.php");
}
```

### What Can Go Wrong?

Several things can go awry when you’re including a file.

**The path to the script is wrong.**

If this happens, the script returns a fatal error and dies. If you’d like to ensure that the script will run even if it can’t find an include file, use include_once() instead of require_once().

**The path to the script is correct, but the script is in a forbidden directory.**

This can happen if you’ve configured the open_basedir setting to restrict the directories that PHP can access. Web developers restrict access to important files and directories for security purposes. We’ll show you how to change directory permissions in “#16: Restricting the Files that PHP Can Access” on page 26.

**The include file has a blank line or space before or after the code in the PHP script.**

If your script sets cookies or does anything else to create a nonstandard HTTP, it must do so before sending any output to the browser. Remember, PHP prints anything outside of its <?php and ?> markers in an include file. Therefore, if you have a blank line before or after these markers, that line will be sent to the browser just as if it was plain HTML, and once HTML is sent to the browser, cookies cannot be set and sessions cannot be started. If you’re including a script, make sure it has no whitespace outside the PHP tags. Be especially careful of spaces after the ?> end marker, because you normally can’t see them when editing.

**NOTE** Cookies are used for tracking users and storing hidden information. See Chapter 8 for more details.

**The include file can be viewed by non-PHP methods.**

You can store PHP variables in any file regardless of its filename, but if you don’t specifically configure Apache to make those files unreadable, Apache can serve them up as plaintext to anyone who asks. Therefore, anyone who knows the names of your include files can read everything in them if you’re not careful.

Needless to say, storing your MySQL passwords and master account names in a place where anyone with Internet Explorer can see them is not considered good security practice.
