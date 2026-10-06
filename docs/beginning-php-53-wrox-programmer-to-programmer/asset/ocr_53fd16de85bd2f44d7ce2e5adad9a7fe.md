# Chapter 5: Strings

When displaying floating-point numbers, you can use a *precision* specifier to indicate how many decimal places to round the number to. To add a precision specifier, insert a period (.), followed by the number of decimal places to use, before the type specifier:

```
printf("%f<br", 123.4567); // Displays "123.4567" (default precision)
printf("%.2f<br", 123.4567); // Displays "123.46"
printf("%.0f<br", 123.4567); // Displays "123"
printf("%.10f<br", 123.4567); // Displays "123.4567000000"
```

You can use a padding specifier with a precision specifier, in which case the number is padded to the required length (which includes digits after the decimal point, as well as the decimal point itself);

```
echo \<pre>";
printf("%.2f<br", 123.4567); // Displays "123.46"
printf("%.012.2f<br", 123.4567); // Displays "000000123.46"
printf("%.12.4f<br", 123.4567); // Displays "123.4567"
echo \<pre>";
```

By way, if you use a precision specifier when formatting a string, *printf()* limits the string to that many characters:

```
printf("%.8s\n", "Hello, world!"); // Displays "Hello, w"
```

# Swapping Arguments

As you've properly noticed, the order of the additional arguments passed to *printf()* must match the order of the conversion specifications within the format string. Normally this isn't a problem, but occasionally you might need to change the order of the conversion specifications without being able to change the order of the arguments.

For example, if your format string is stored in a text file, rather than being embedded in your PHP code. This is handy if you want to change how your script displays its output — for example, if you're creating a "skin" for your application, or if you're creating English, French, and German versions of your application. Imagine the following format string is saved in a file called template.txt:

You have %d messages in your Inbox, of which %d areunread.

Your PHP code could use this template.txt file to display a message to a user (in a real-world example the $mailbox, $totalMessages, and $unreadMessages would probably be pulled from a database):

```
$mailbox = "Inbox";
$totalMessages = 36;
$unreadMessages = 4;
printf("file_get_contents( "template.txt" ), $totalMessages, $mailbox,
$unreadMessages ");
```

This code would display the following message:

You have 36 messages in your Inbox, of which 4 are unread.