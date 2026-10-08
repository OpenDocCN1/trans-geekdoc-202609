
# Core PHP Programming

The biggest problem with this approach is the lack of good tools for editing the site. Developers are used to fetching files into an editor via FTP. Asking these same people to start using a database is most likely out of the question. The cost of teaching SQL to anyone who works on the site may eliminate any benefit gained when the content is put into the database. The logical path is to Web-based tools, since coding a desktop application is a major project in itself, especially if Windows and Macintosh users are to be accommodated. As you might guess, Web-based site editors are less ideal. However, with very large sites they become bearable, because the alternative of managing such a large site is a greater evil, so to speak.

# In-Line Debugging

There are times when code produces unexpected results. Examining the code reveals nothing. The best thing to do is to spend in-line debugging. PHP scripts generate HTML to be interpreted by a browser, and HTML has a comment tag. There is a simple matter to write PHP code that reports diagnostic information inside HTML comments.

Often I query database queries dynamically

# Remote Debugging

You may enable remote debugging for all scripts by editing the configuration `php.ini`, or you may use the `debugger_on` function, described in [Chapter 8, "I/O Functions."]. Once enabled, PHP will attempt to connect to a remote host and port each time a script is run.

You will need a port listening program to get the debugging information. There are numerous free port listeners for Windows. I've found Port Listener by Hauke X to work well. Similar programs exist for UNIX as well.

All debugging messages are sent to the listening host, regardless of the error reporting level set in `php.ini`. Messages are sent in a special format

```
date time host(pid) type:message-data
```

followed by a linefeed.

# Core PHP Programming

The date is in the format YYYY-MM-DD. Time is in the format HH:MM:uuuu. The last six digits of time are the seconds and microseconds. The host is the name of the server and pid is the process identifier. The type is a special code described in Table 22-1. The rest of the line is a message terminated with a linefeed.

Using the remote debugger is as simple as executing a PHP script and watching the debug information appear in the port listener output.

| Type | Description |
| --- | --- |
| end | The end of an error message. |
| frames | The number of frames in the call stack. |
| function | The name of the function where the error occurred. |
| location | The filename and line number that generated the error message. |
| message | A PHP error message. |
| start | This type signifies the beginning of a debugging message. The message for this line will be the type of the error. |

# Simulating HTTP Connections

When writing PHP scripts, it is not necessary to understand every detail of the HTTP protocol. I would be straining to include a treatise here, but you ought to have enough understanding so that you could simulate a connection by telnet. You may know that Web servers listen on port 80 by default. HTTP is a text-based protocol, so it's not hard to telnet directly to a Web server and type a simple request. HTTP has several commands that should be familiar; GET and POST are used most often. HEAD is a command that returns just the headers for a request. Browsers use this command to test whether they really want to get an entire document.

It is especially helpful to simulate an HTTP connection when your script sends custom headers. Figure 22-2 is an example showing a request I made to the PHP home page. The text in bold is what I typed. The remote server returned everything.

# Figure 22-2. Simulating an HTTP Connection

```
[1] leon [/export/home/leon] ?> telnet www.php.net 80
Trying 208.247.106.167...
Connected to www.php.net.
Escape character is '^'.
HEAD / HTTP/1.0

HTTP/1.1 200 OK
Date: Sun, 20 Feb 2000 00:53:51 GMT
Server: Apache/1.3.10-dev (Unix) DAV/0.9.15-dev PHP/4.0b4-dev
X-Powered-By: PHP/4.0b4-dev
Last-Modified: Mon, 31 Jan 2000 04:33:04 GMT
Vary:
Connection: close
Content-Type: text/html; charset=iso-8859-1
```

Connection closed by foreign host.

[2] leon [/export/home/leon] ?>

# Appendix A. BACKSLASH CODES

The following codes may be included in strings and have special meaning when printed to the browser or to a file. It is important to note that they do not have special meaning when passed to other functions, such as ones communicating with a database or evaluating a regular expression.

| Code | Description |
| --- | --- |
| \" | Double Quotes |
| \ | Backslash Character |
| \n | New Line |
| \r | Carriage Return |
| \t | Horizontal Tab |
| \x00 - \xFF | Hex Characters |

# Appendix B. ASCII CODES

The following table lists the first 128 characters of the ASCII code. PHP allows for ASCII codes in the range of 0 to 255, but above code 127 the representation differs across operating systems.

| Decimal | Hex | Character | Description |
|---|---|---|---|
| 0 | 00 | | Null |
| 1 | 01 | | Start of Heading |
| 2 | 02 | | End of Text |
| 3 | 03 | | End of Text |
| 4 | 04 | | End of Transmission |
| 5 | 05 | | Enquiry |
| 6 | 06 | | Acknowledge |
| 7 | 07 | | Bell |
| 8 | 08 | | Backspace |
| 9 | 09 | | Character Tabulation |
| 10 | 0A | | Line Feed |
| 11 | 0B | | Line Tabulation |
| 12 | 0C | | Form Feed |
| 13 | 0D | | Carriage Return |
| 14 | 0E | | Shift Out |
| 15 | 0F | | Shift In |
| 16 | 10 | | Datal |
| 17 | 11 | | Device Control |
| 18 | 12 | | Device Two |
| 19 | 13 | | Device Control |
| 20 | 14 | | Device Control |
| 21 | 15 | | Device Control |
| 22 | 16 | | Acknowledge |
| 23 | 17 | | Device Control |
| 24 | 18 | | Device Control |
| 25 | 19 | | Device Control |
| 26 | 1A | | Device Control |
| 27 | 1B | | Device Control |
| 28 | 1C | | Device Control |
| 29 | 1D | | Device Control |
| 30 | 1E | | Device Control |
| 31 | 1F | | Device Control |
| 32 | 20 | | Space |
| 33 | 21 | | Exclamation Mark |
| 34 | 22 | | Quotation Mark |
| 35 | 23 | | # Sign |
| 36 | 24 | | Dollar Sign |
| 37 | 25 | | Percent Sign |
| 38 | 26 | | Ampersand |
| 39 | 27 | | Apostrophe |
| 40 | 28 | | Left Parenthesis |
| 41 | 29 | | Right Parenthesis |
| 42 | 2A | | Asterisk |
| 43 | 2B | | Plus |
| 44 | 2C | | Comma |
| 45 | 2D | | Hyphen-Minus |
| 46 | 2E | | Period |
| 47 | 2F | | Forward Slash |
| 48 | 30 | | Zero |
| 49 | 31 | | One |
| 50 | 32 | | Two |
| 51 | 33 | | Three |
| 52 | 34 | | Four |
| 53 | 35 | | Five |
| 54 | 36 | | Six |
| 55 | 37 | | Seven |
| 56 | 38 | | Eight |
| 57 | 39 | | Nine |
| 58 | 3A | | Colon |
| 59 | 3B | | Semicolon |
| 60 | 3C | | Less-Than |
| 61 | 3D | | Equals |
| 62 | 3E | | Greater-Than |
| 63 | 3F | | Question Mark |
| 64 | 40 | | @ |
| 65 | 41 | | A |
| 66 | 42 | | B |
| 67 | 43 | | C |
| 68 | 44 | | D |
| 69 | 45 | | E |
| 70 | 46 | | F |
| 71 | 47 | | G |
| 72 | 48 | | H |
| 73 | 49 | | I |
| 74 | 4A | | J |
| 75 | 4B | | K |
| 76 | 4C | | L |
| 77 | 4D | | M |
| 78 | 4E | | N |
| 79 | 4F | | O |
| 80 | 50 | | P |
| 81 | 51 | | Q |
| 82 | 52 | | R |
| 83 | 53 | | S |
| 84 | 54 | | T |
| 85 | 55 | | U |
| 86 | 56 | | V |
| 87 | 57 | | W |
| 88 | 58 | | X |
| 89 | 59 | | Y |
| 90 | 5A | | Z |
| 91 | 5B | | [ |
| 92 | 5C | | \ |
| 93 | 5D | | ] |
| 94 | 5E | | ^ |
| 95 | 5F | | _ |
| 96 | 60 | | ` |
| 97 | 61 | | a |
| 98 | 62 | | b |
| 99 | 63 | | c |
| 100 | 64 | | d |
| 101 | 65 | | e |
| 102 | 66 | | f |
| 103 | 67 | | g |
| 104 | 68 | | h |
| 105 | 69 | | i |
| 106 | 6A | | j |
| 107 | 6B | | k |
| 108 | 6C | | l |
| 109 | 6D | | m |
| 110 | 6E | | n |
| 111 | 6F | | o |
| 112 | 70 | | p |
| 113 | 71 | | q |
| 114 | 72 | | r |
| 115 | 73 | | s |
| 116 | 74 | | t |
| 117 | 75 | | u |
