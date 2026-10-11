
# Localization of Web Based Applications

## Overview

*   Using the specific time zone and date/time format.
*   Using the specific currency and numbering system.

We know that the main task of localization is to communicate with user in the local language. This means that software must present information as characters of the local language, and take information as characters of the local language.

In this part of the book, we will concentrate on presenting and managing information as characters of the local language.

## Character String Traveling Paths

This section describes steps of connection paths that character strings must travel through in a typical Web based application: output characters strings come from PHP files or data base tables and input character strings come from user's Web browser.

In a typical Web based application, character strings will travel from one part of the application to another part. Here are some possible paths character strings may travel through.

### From PHP file to Web browser

The following diagram illustrates steps that character strings must travel through from a PHP file to a browser screen. It also shows the computing technologies that are used at different steps:

```
A1. Key Sequences from keyboard
      |
      |- Text editor
      v
A2. PHP File
      |
      |- PHP CGI engine
      v
A3. HTML Document
      |
      |- Web server
      v
A4. HTTP Response
      |
      |- Internet TCP/IP Connection
      v
A5. HTTP Response
      |
      |- Web browser
      v
A6. Visual characters on the screen
```

### From Database to Web browser

The following diagram illustrates steps that character strings must travel through from a database table to a browser screen. It also shows computing technologies that are used at different steps:

```
B1. Byte sequences in storage
      |
      |- Database server
      v
B2. Byte stream
      |
      |- Database connection driver
      v
B3. Byte stream
      |
      |- PHP Application
      v
B4. HTTP Response
      |
      |- Internet TCP/IP Connection
      v
B5. HTTP Response
      |
      |- Web browser
      v
B6. Visual characters on the Screen
```

### From Web browser to Database

The following diagram illustrates steps that character strings must travel from a Web browser to a database table. It also shows computing technologies that are used at different steps:

```
C1. Key sequences on keyboard
      |
      |- Language input tool (optional)
      v
C2. Byte sequences
      |
      |- Browser input form
      v
C3: HTTP request
      |
      |- Internet TCP/IP Connection
      v
C4. HTTP request
      |
      |- Web server
      v
C5. CGI variables and input stream
      |
      |- PHP Application
      v
C6. PHP variables
      |
      |- Database connection driver
      v
C7. Byte stream
      |
      |- Database server
      v
C8. Byte sequence in storage
```

Since all computing technologies are using ASCII encoding by default, text of ASCII characters can safely travel through those steps without any issues.

However, for non ASCII characters, we have to watch out each steps carefully to make sure that characters are not damaged and are encoded and decoded correctly.

Now I will try to provide some tutorials in this chapter and next 5 chapters to show you how to handle characters correctly in different steps of different connection paths.

## Output ASCII Character Strings from PHP Scripts

This section provides tutorial example on how to include output ASCII character strings in a PHP script file. ASCII characters can be entered directly as string literals in PHP code segments or as text in non-PHP code segments. No special techniques are needed.

As I mentioned earlier, ASCII characters can travel from PHP files to browsers easily without any trouble. Here is a simple PHP file with ASCII characters only:

```php
<?php
#  HelpASCII.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print("<html><body>\n");
   print("<b>Help</b><br/>\n");
   print("This is a very simple help page...<br/>\n");
?>
This is a very simple help page...<br/>
</body></html>
```

If you view this page with a browser, you will get the following output:

```
Help
This is a very simple help page...
This is a very simple help page...
```

Perfect, right? ASCII text entered as a PHP string literal travels through correctly. Text entered as HTML static text outside the PHP block travels through also correctly.

## Using Non-ASCII Characters in HTML Documents

This chapter provides tutorial examples and notes about non-ASCII characters in HTML documents. Topics include basic rules on using non-ASCII characters in HTML documents; examples of using French characters with UTF-8 and ISO-8859-1 encodings; examples of using Chinese characters with UTF-8 and GB2312 encodings.

> [Basic Rules of Using Non-ASCII Characters in HTML Documents](#part0165.xhtml)
>
> [French Characters in HTML Documents - UTF-8 Encoding](#part0166.xhtml)
>
> [French Characters in HTML Documents - ISO-8859-1 Encoding](#part0167.xhtml)
>
> [Chinese Characters in HTML Documents - UTF-8 Encoding](#part0168.xhtml)
>
> [Chinese Characters in HTML Documents - GB2312 Encoding](#part0169.xhtml)
>
> [Characters of Multiple Languages in HTML Documents](#part0170.xhtml)

### Takeaways

*   You can only use one encoding schema in a HTML document. You should use a `<meta>` tag to specify the encoding name.
