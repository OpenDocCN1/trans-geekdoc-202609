
Sometimes you might have a problem with your e-mail. PHP has a configuration setting that must be correct before the mail function can connect to your system e-mail software. The default is usually correct, but if your e-mail doesn't seem to be getting to its destination, check the PHP configuration mail setting by looking for the following in the output of phpinfo():

| Sendmail_path | (on Unix/Linux) |
|---|---|
| SMTP | (on Windows) |

It might be set incorrectly. You can change the setting by editing the php.ini file. Look for the following lines:

```
[mail function]
; For Win32 only.
SMTP = localhost

; For Win32 only.
sendmail_from = me@localhost.com

; For Unix only.
;sendmail_path =
```

Windows users need to change the first two settings. The first setting is where you put the name of your outgoing mail server. However you send e-mail — LAN at work, a cable modem at home, an ISP via a modem — you send your mail with an SMTP server, which has an address that you need to know.

If you send directly from your computer, you should be able to find the name of the outgoing mail server that you're using in your e-mail software. For instance, in Microsoft Outlook Express, choose Tools→Accounts→Properties and then select the Servers tab. Look for the name of your outgoing mail server. If you can't find its name, you can ask your e-mail administrator for the name. If you use an ISP, you can ask the ISP. The name is likely to be in a format similar to the following:

```
mail.ispname.net
```

The second setting is the return address that is sent with all your e-mail. Change the setting to the e-mail address that you want to use for your return address, as follows:

```
sendmail_from = Janet@Valade.com
```

The third setting is for Unix users. The default is usually correct. If it doesn't work, you need to talk to your system administrator about the correct path to your outgoing mail server. This usually refers to Linux as well.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_386_0.png)

Don't forget to remove the semicolon at the beginning of the lines. The semicolon makes the line into a comment, so the setting isn't active until you remove the semicolon.

## Use PHP Sessions

The functions to open or close a session follow. I explain all these functions in Chapter 9.

```
session_start();    session_destroy()
```

## Stop Your Program

Sometimes you just want your program to stop, cease, and desist. There are two functions for this: exit() and die(). Actually, these are two different names for the same function. Exit is probably accurate, but sometimes it's just more fun to say die. Both functions will print a message when they stop if you provide one. The format is

```
exit("message string");
```

When exit executes, the message string is output.

## Handle Arrays

Arrays are very useful in PHP, particularly for getting the results from database functions and for form variables. I explain the following array functions elsewhere in the book, mainly in Chapter 7:

```
array();      extract();      sort();      asort();
rsort();      arsort();      ksort();      krsort();
```

Here are some other useful functions:

- array_reverse($varname): Returns an array with the values in reverse order.
- array_unique($varname): Removes duplicate values from an array.
- `in_array("string",$varname)`: Looks through an array `$varname` for a string `"string"`.
- `range(value1,value2)`: Creates an array containing all the values between `value1` and `value2`. For instance, `range('a','z')` creates an array containing all the letters between `a` and `z`.
- `explode("sep","string")`: Creates an array of strings in which each item is a substring of `string`, separated `sep`. For example, `explode(" ",$string)` creates an array in which each word in `$string` is a separate value. This is similar to the `split` function in Perl.
- `implode("glue",$array)`: Creates a string containing all the values in `$array` with `glue` between them. For instance, `implode(", ",$array)` creates a string: `value1,value2,value3`, and so on. This is similar to the `join` function in Perl.

And there are many more useful array functions. PHP can do almost anything you can think of that you want to do with an array.

## Check for Variables

Sometimes you just need to know whether a variable exists. The following functions can be used to test whether a variable is currently set:

```
isset($varname); // true if variable is set
!isset($varname); // true if variable is not set
empty($varname); // true if value is 0 or is not set
```

## Format Values

Sometimes you need to format the values in variables. In Chapter 6, I explain how to format numbers into dollar format by using `number_format()` and `sprintf()`. In Chapter 6, I also discuss `unset()`, which removes the values from a variable. In this section, I describe additional capabilities of `sprintf()`.

The function `sprintf()` allows you to format any string or number, including variable values. The general format is

```
$newvar = sprintf("format",$varname1,$varname2,...);
```

## Change the Case of Strings

Changing uppercase letters to lowercase and vice versa is not so easy. Bless PHP for providing functions to do this for you:

- `strtolower($varname)`: Changes any uppercase letters in the string to lowercase letters
- `strtoupper($varname)`: Changes any lowercase letters in the string to uppercase letters
- `ucfirst($varname)`: Changes the first letter in the string to uppercase
- `ucwords($varname)`: Changes the first letter of each word in the string to uppercase

## Chapter 14

## Ten PHP Gotchas

## In This Chapter

- Recognizing common PHP errors
- Interpreting error messages

I guarantee that you will do all the things that I mention in this chapter. It’s not possible to write programs without making these mistakes. The trick is to find out how to recognize them, roll your eyes, say, “Not again,” and then fix them. One error message that you will see many times is

```
Parse error: parse error in c:\test.php on line 7
```

This is PHP’s way of saying, “Huh?” It means it doesn’t understand something. This message helpfully points to the file and the line number where PHP got confused. Sometimes it’s directly pointing at the error, but sometimes PHP’s confusion results from an error earlier in the program.

## Missing Semicolons

Every PHP statement ends with a semicolon (;). PHP doesn’t stop reading a statement until it reaches a semicolon. If you leave out the semicolon at the end of a line, PHP continues reading the statement on the following line. For instance, consider the following statement:

```
$test = 1
echo $test;
```

Of course, the statement doesn’t make sense to PHP when it reads the two lines as one statement, so it complains with an error message, such as the annoying

```
Parse error: parse error in c:\test.php on line 2
```

Before you know it, you’ll be writing your home address with semicolons at the end of each line.

## Not Enough Equal Signs

When you ask whether two values are equal in a comparison statement, you need two equal signs (==). Using one equal sign is a common mistake. It's perfectly reasonable because you have been using one equal sign to mean equal since the first grade when you discovered that 2 + 2 = 4. This is a difficult mistake to recognize because it doesn't cause an error message. It just makes your program do odd things, like infinite loops or if blocks that never execute. I'm continually amazed at how long I can stare at

```
$test = 0;
while ( $test = 0 )
{
    $test++;
}
```

and not see why it's looping endlessly.

## Misspelled Variable Names

This is another PHP gotcha that doesn't result in an error message, just odd program behavior. If you misspell a variable name, PHP considers it a new variable and does what you ask it to do. Here's another clever way to write an infinite loop:

```
$test = 0;
while ( $test == 0 )
{
    $Test++;
}
```

**Remember:** To PHP, $test is not the same variable as $Test.

## Missing Dollar Signs

A missing dollar sign in a variable name is really hard to see, but at least it usually results in an error message so that you know where to look for the problem. It usually results in the old familiar parse error:

```
Parse error: parse error in test.php on line 7
```
