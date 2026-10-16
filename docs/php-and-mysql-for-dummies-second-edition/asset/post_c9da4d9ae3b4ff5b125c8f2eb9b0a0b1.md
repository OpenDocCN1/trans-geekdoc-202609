
## Troubling Quotes

You can have too many, too few, or the wrong kind of quotes. You have too many when you put quotes inside of quotes, such as

```
$test = "<table width="100%">";
```

PHP will see the second double quote (") — before 100 — as the ending double quote (") and read the 1 as an instruction, which makes no sense. Voilà! Another parse error. The line must be either

```
$test = "<table width='100%'>";
```

or

```
$test = "<table width=\"100%\">";
```

You have too few quotes when you forget to end a quoted string, such as

```
$test = "<table width='100%'>;
```

PHP will continue reading the lines as part of the quoted string until it encounters another double quote ("), which might not occur for several lines. This is one occasion when the parse error pointing to where PHP got confused is not pointing to the actual error. The actual error occurred some lines previously, when you forgot to end the string.

You have the wrong kind of quotes when you use a single quote (') when you meant a double quote (") or vice versa. The difference between single and double quotes is sometimes important, and I explain it in Chapter 6.

## Invisible Output

Some statements, such as the header statement, must execute before the program produces any output. If you try to use such statements after sending output, they fail. The following statements will fail because the header message isn't the first output:

```
<html>
<?php
  header("Location: http://company.com");
?>
```

<html> is not in a PHP section and is therefore sent as HTML output. The following statements will work:

```
<?php
    header("Location: http://company.com");
?>
<html>
```

The following statements will fail:

```
 <?php
    header("Location: http://company.com");
?>
<html>
```

because there's one single blank space before the opening PHP tag. The blank space is output to the browser, although the resulting Web page looks empty. Therefore, the header statement fails because there is output before it. This is a common mistake and difficult to spot.

## Numbered Arrays

PHP believes the first value in an array is numbered zero (0). Of course, humans tend to believe that lists start with the number one (1). This fundamentally different way of viewing lists results in us humans believing an array isn't working correctly when it's working just fine. For instance, consider the following statements:

```
$test = 1;
while ( $test <= 3 )
{
    $array[] = $test;
    $test++;
}
echo $array[3];
```

Nothing is displayed by these statements. I leap to the conclusion that there's something wrong with my loop. Actually, it's fine. It just results in the following array:

```
$array[0]=1
$array[1]=2
$array[2]=3
```

And doesn't set anything into $array[3].

## Including PHP Statements

When a file is read in using an include statement in a PHP section, it seems reasonable to me that the statements in the file will be treated as PHP statements. After all, PHP adds the statements to the program at the point where I include them. However, PHP doesn't see it my way. If a file named file1.inc contains the following statements:

```
if ( $test == 1 )
    echo "Hi";
```

and I read it in with the following statements in my main program:

```
<?php
$test = 1;
include ("file1.inc");
?>
```

I expect the word Hi to appear on the Web page. However, the Web page actually displays this:

```
if ( $test == 1 ) echo "Hi";
```

Clearly, the file that is included is seen as HTML. To send Hi to the Web page, file1.inc needs to contain the following statements:

```
<?php
if ( $test == 1 )
    echo "Hi";
?>
```

## Missing Mates

Parentheses and curly brackets come in pairs and must be used that way. Opening with a ( that has no closing ) or a { without a } will result in an error message. One of my favorites is using one closing parenthesis where two are needed, as in the following statement:

```
if ( isset($test)
```

This statement needs a closing parenthesis at the end. It’s much more difficult to spot that one of your blocks didn’t get closed when you have blocks inside of blocks inside of blocks. For instance, consider the following.

```
while ( $test < 3 )
{
if ( $test2 != "yes" )
{
if ( $test3 > 4 )
{
echo "go";
}
}
```

You can see there are three opening curly brackets and only two closing ones. Imagine that 100 lines of code are inside these blocks. It can be difficult to spot the problem — especially if you think the last closing bracket is closing the while loop, but PHP sees it as closing the if loop for $test2. Somewhere later in your program, PHP might be using a closing bracket to close the while loop that you aren’t even looking at. It can be difficult to trace the problem in a large program.

Indenting blocks makes it easier to see where closing brackets belong. Also, I often use comments to keep track of where I am, such as

```
while ( $test < 3 )
{
if ( $test2 != "yes" )
{
if ( $test3 > 4 )
{
echo "go";
} // closing if block for $test3
} // closing if block for $test2
} // closing while block
```

## Confusing Parentheses and Brackets

I'm not sure whether this is a problem for everyone or just a problem for me because I refuse to admit that I can't see as well as I used to. Although PHP has no trouble distinguishing between parentheses and curly brackets, my eyes are not so reliable. Especially while staring at a computer screen at the end of a ten-hour programming marathon, I can easily confuse ( and {. Using the wrong one gets you a parse error message.

## Part VI

### Appendixes

### The 5th Wave

By Rich Tennant

![](img/d82df0828cfbc6d6be1e9a991861f3b7_397_0.png)

### In this part...

This part provides instructions for installing MySQL and PHP. Appendix C provides installation and configuration information that could be helpful if you need to install Apache.

## Appendix A

### Installing MySQL

Although MySQL runs on many platforms, I describe how to install it on Linux, Unix, Windows, and Mac, which together account for the majority of Web sites on the Internet. Be sure to read the instructions all the way through before beginning the installation.

MySQL can be installed most easily from binaries — precompiled, ready-to-install packages. Binaries are available for most operating systems: Linux, Windows, Mac, FreeBSD, many flavors of Unix, and others. If such a package is available for your operating system, use it. Only install MySQL from source if it’s totally necessary, such as when there’s no binary for your operating system or you need some functionality that’s not compiled into the binaries (for example, a different character set).

If you have trouble starting the MySQL server after installing it, check the error log for useful information. The error log is located in the data directory and has the extension .err.

### On Windows

In most cases, when you download and install MySQL, the server is started automatically. If it isn’t or if you need to stop and start it for another reason, you can start it manually using the WinMySQLadmin utility that is installed with MySQL, as I describe in the upcoming section, “Starting the MySQL server.” You can also use WinMySQLadmin to set up MySQL so that it starts every time your computer starts.

### Downloading and installing MySQL

To install MySQL on Windows, follow these steps:

- 1. **Point your Web browser to www.mysql.com, the MySQL home page.**
- 2. **Click the Production version number link.**
  - Look for the section under the heading Database Server. As of this writing, the production release is 4.0.17.
  - MySQL 4.0.x is supported by PHP 4 or 5. Support for MySQL 4.1.x is provided beginning with PHP 5.
- 3. **Scroll down the screen until you come to the Windows Downloads heading.**
- 4. **Click the download link for the Windows binary labeled Windows 95/98/NT/2000/XP/2003.** This binary includes an installer.
  - A dialog box opens.
- 5. **Select the option to save the file.**
  - A dialog box opens that lets you select where you want the file saved.
- 6. **Navigate to where you want to save the file (for example, c:\downloads). Then click Save.**
  - After the download, you see a Zip file in the download location (for example, c:\downloads) containing the MySQL files. The file is named mysql-, followed by the version number and -win.zip — for instance, mysql-4.0.17-win.zip.
- 7. **Use your favorite Zip utility to unzip the files and save them in a temporary location (for example, c:\downloads\mysql).**
  - Two popular Zip utilities are PKZIP at www.pkware.com and WinZip at www.winzip.com.
- 8. **Navigate to the temporary directory where the unzipped files are stored. Then double-click setup.exe.**
  - *Note:* If you’re installing from a Windows NT/2000/XP system, be sure that you’re logged into an account with administrative privileges.
  - The opening screen shown in Figure A-1 is displayed.
- 9. **Click Next.**
  - The license is displayed.
- 10. **Click the I Agree button to continue.**
  - You see a screen showing the directory where MySQL will be installed.
