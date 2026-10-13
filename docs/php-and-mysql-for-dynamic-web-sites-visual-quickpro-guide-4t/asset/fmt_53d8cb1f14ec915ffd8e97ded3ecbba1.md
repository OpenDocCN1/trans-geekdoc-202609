
![Image](graphics/circle-a.jpg) The revised `images.php` shows two more pieces of information about each image.

### To use the date and time functions

1.  Open `images.php` ([Script 11.4](#ch11.html#ch11ex04)) in your text editor or IDE, if it is not already.

2.  As the first line of code after the opening PHP tag, establish the time zone ([Script 11.6](#ch11.html#ch11ex06)):

    ```
    date_default_timezone_set ('America/New_York');
    ```

    Before calling any of the date and time functions, the time zone has to be established. To find your time zone, see [www.php.net/timezones](http://www.php.net/timezones).

3.  Within the `foreach` loop, after getting the image’s dimensions, calculate its file size:

    ```
    $file_size = round ( (filesize ("$dir/$image")) / 1024) . "kb";
    ```

    The `filesize()` function was first used in the `show_image.php` script. It returns the size of a file in bytes. To calculate the kilobytes of a file, divide this number by 1,024 (there are that many bytes in a kilobyte) and round it off.

4.  On the next line, determine the image’s modification date and time:

    ```
    $image_date = date("F d, Y H:i:s", filemtime("$dir/$image"));
    ```

    To find a file’s modification date and time, call the `filemtime()` function, providing the function with the file, or directory, to be examined. This function returns a timestamp, which can then be used as the second argument to the `date()`, which will format the timestamp accordingly.

    If you’re perplexed by what’s happening here, you can break the code into two steps:

    ```
    $filemtime = filemtime ("$dir/$image");
    $image_date = date("F d, Y H:i:s ", $filemtime);
    ```

5.  Change the echo statement so that it also prints the file size and modification date:

    ```
    echo "<li><a href=\"javascript: create_window('$image_name', $image_size[0],$image_size[1])\"> $image</a> $file_size ($image_date)</li>\n";
    ```

    Both are printed outside of the `A` tag, so they aren’t part of the links.

6.  Save the file as `images.php`, place it in your Web directory, and test it in your Web browser.

***

> **Tip**
>
> The `date()` function has some parameters that are used for informative purposes, not formatting. For example, `date('L')` returns 1 or 0 indicating if it’s a leap year; `date('t')` returns the number of days in the current month; and `date('I')` returns a 1 if it’s currently daylight saving time.

***

> **Tip**
>
> PHP’s date functions reflect the time on the server (because PHP runs on the server); you’ll need to use JavaScript if you want to determine the date and time on the user’s computer.

***

> **Tip**
>
> In [Chapter 16](#ch16.html#ch16), you’ll learn how to use the new `DateTime` class to work with dates and times in PHP.

***

**Script 11.6.** This modified version of `images.php` ([Script 11.4](#ch11.html#ch11ex04)) uses PHP’s date and time functions in order to report some information to the user.

***

```
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/
2       xhtml1-transitional.dtd">
3   <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
4   <head>
5       <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
6       <title>Images</title>
7       <script type="text/javascript" charset="utf-8" src="js/function.js"></script>
8   </head>
9   <body>
10  <p>Click on an image to view it in a separate window.</p>
11  <ul>
12  <?php # Script 11.6 - images.php
13  // This script lists the images in the uploads directory.
14  // This version now shows each image's file size and uploaded date and time.
15
16  // Set the default timezone:
17  date_default_timezone_set ('America/New_York');
18
19  $dir = '../uploads'; // Define the directory to view.
20
21  $files = scandir($dir); // Read all the images into an array.
22
23  // Display each image caption as a link to the JavaScript function:
24  foreach ($files as $image) {
25
26      if (substr($image, 0, 1) != '.') { // Ignore anything starting with a period.
27
28          // Get the image's size in pixels:
29          $image_size = getimagesize ("$dir/$image");
30
31          // Calculate the image's size in kilobytes:
32          $file_size = round ( (filesize ("$dir/$image")) / 1024) . "kb";
33
34          // Determine the image's upload date and time:
35          $image_date = date("F d, Y H:i:s", filemtime("$dir/$image"));
36
37          // Make the image's name URL-safe:
38          $image_name = urlencode($image);
39
40          // Print the information:
41          echo "<li><a href=\"javascript:create_window('$image_name',$image_size[0],
42              $image_size[1])\">$image</a> $file_size ($image_date)</li>\n";
43
44      } // End of the IF.
45
46  } // End of the foreach loop.
47
48  ?>
49  </ul>
50  </body>
51  </html>
```

***

### Review and Pursue

If you have any problems with the review questions or the pursue prompts, turn to the book’s supporting forum ([www.LarryUllman.com/forums/](http://www.LarryUllman.com/forums/)).

#### Review

*   What function is used to send email? What are the function’s arguments? What does the server need in order to send email?
*   Does it make a difference whether `\n` is used within single or double quotation marks?
*   Can you easily know for certain if, or when, a recipient received an email sent by PHP?
*   What debugging steps can you take if you aren’t receiving any email that should be sent from a PHP script?
*   How do folder permissions come into play for handling uploaded files?
*   What two directories are used in handling file uploads?
*   What additional attribute must be made to the opening `form` tag in order to handle a file upload?
*   What is a MIME type?
*   In what ways are PHP and JavaScript alike? How are they different?
*   What tag is used to add JavaScript to an HTML page?
*   What does the `var` keyword mean in JavaScript?
*   What is the concatenation operator in JavaScript?
*   What does the PHP `header()` function do?
*   What do *headers already sent* error messages mean?
*   What is a *proxy script*? When might a proxy script be necessary?
*   What does the `readfile()` function do?

#### Pursue

*   Create a more custom contact form. Have the PHP script also send a more custom email, including any other data requested by the form.
*   Search online using the keywords *php email spam filters* to learn techniques for improving the successful delivery of PHP-sent email (i.e., to minimize the chances of spam filters eating legitimate emails).
*   Make a variation on `upload_image.php` that supports the uploading of different file types. Create a corresponding version of `show_image.php`. Note: You’ll need to do some research on MIME types to complete these challenges.
*   Check out the PHP manual page for the `glob()` function.
*   A lot of information and new functions were introduced in this chapter. Check out the PHP manual for some of them to learn more.

## 12. Cookies and Sessions

In This Chapter

*   [Making a Login Page](#ch12.html#ch12lev1sec1) [368](#ch12.html#ch12lev1sec1)
*   [Making the Login Functions](#ch12.html#ch12lev1sec2) [371](#ch12.html#ch12lev1sec2)
*   [Using Cookies](#ch12.html#ch12lev1sec3) [376](#ch12.html#ch12lev1sec3)
*   [Using Sessions](#ch12.html#ch12lev1sec4) [388](#ch12.html#ch12lev1sec4)
*   [Improving Session Security](#ch12.html#ch12lev1sec5) [396](#ch12.html#ch12lev1sec5)
*   [Review and Pursue](#ch12.html#ch12lev1sec6) [400](#ch12.html#ch12lev1sec6)
