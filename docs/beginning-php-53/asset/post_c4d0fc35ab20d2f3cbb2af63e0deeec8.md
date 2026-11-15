
Next comes checkDateOfBirth(), the callback function to check that the entered date is valid. As you might expect, this uses PHP’s checkdate() function to do the checking. Because the element to be checked contains multiple field values, HTML_QuickForm provides an associative array of the values, keyed by field name. checkDateOfBirth() extracts these three values and passes them to checkdate() for checking, passing checkdate()’s return value (true or false) back to the calling code:

```php
function checkDateOfBirth( $value ) {
    return checkdate( $value["M"], $value["d"], $value["Y"] );
}
```

The last function, calculateDays(), is called when the form is processed. First it creates two timestamps: $currentDate, which stores the current date and time; and $dateOfBirth, which stores the entered birth date. Both timestamps are created using mktime(). The month, day, and year components of the date of birth are extracted from the three-element associative array stored in the form’s dateOfBirth field:

```php
$currentDate = mktime();
$dateOfBirth = mktime( 0, 0, 0, $values["dateOfBirth"]["M"],
    $values["dateOfBirth"]["d"], $values["dateOfBirth"]["Y"] );
```

Now that both dates are stored in timestamps, it’s easy to work out the number of seconds between the two, and hence the number of days:

```php
$secondsOld = $currentDate - $dateOfBirth;
$daysOld = (int) ( $secondsOld / 60 / 60 / 24 );
```

Finally, the function displays the output to the visitor. First it calls PHP’s date() function to display the visitor’s date of birth in a nice format, then it tells the visitor how old he is in days:

```php
echo "<p>You were born on " . date( "l, F jS, Y", $dateOfBirth ) . ".</p>";
echo "<p>You are " . number_format( $daysOld ) . " day" . ( $daysOld != 1 ? "s" : "" ) . " old!</p>";
```

Calculating the difference in days by dividing the difference in seconds by (60 * 60 * 24) is not entirely accurate due to days not always being 24 hours long (at least in time zones that use daylight saving time). However, it’s good enough for the purposes of this script.

## DateTime: The Future of PHP Date/Time Handling

Starting with version 5.2, PHP introduced a couple of useful date and time handling classes:

- DateTime for storing and manipulating dates and times
- DateTimeZone for representing time zones

At the time of writing, these classes were relatively experimental and not feature-complete; however, they are already useful. They provide a number of advantages over the traditional PHP date and time functions, including:

- Elegant handling of time zones
- The ability to store and handle dates before 1901 and after 2038
- Easier date manipulation

For example, the following code creates a new DateTime object representing 13th Feb 1948 in the Los Angeles time zone, then subtracts three months from the date, displaying the result:

```php
$dtz = new DateTimeZone( "America/Los_Angeles" );
$dt = new DateTime( "13-Feb-1948", $dtz );
$dt->modify( "-3 months" );

// Displays "Thu, 13 Nov 1947 00:00:00 -0800"
echo $dt->format( DateTime::RFC2822 );
```

First the code creates a new DateTimeZone object representing the Los Angeles time zone, then it creates a new DateTime object representing midnight, 13th Feb 1948 in that time zone. Next the code calls the DateTime object’s modify() method. This very handy method accepts a modification string in the same format passed to strtotime() and adjusts the date and time accordingly.

Finally, the code calls the DateTime object’s format() method to return the date as a string. format() takes the same type of format string as the date() function. In this case a class constant, DateTime::RFC2822, is used to format the date in RFC2822 format — that is, "D, d M Y H:i:s O". Notice how the time zone offset in the displayed date string is eight hours behind GMT — that is, Los Angeles time.

The DateTime class currently lacks some useful functionality; however, if you prefer the object-oriented approach, or need to work with dates outside the usual 1901–2038 year range, it’s well worth a look. For more information on DateTime and related classes, see http://www.php.net/manual/en/book.datetime.php.

## Working with HTTP

Web servers and browsers talk to each other using HTTP (Hypertext Transfer Protocol), a set of rules that govern how to request and retrieve data from a Web server.

Most of the time, you don’t need to delve into the workings of HTTP, because HTTP communication happens automatically whenever a visitor visits your Web page or PHP script. However, occasionally it can be useful to understand some of the processes involved in HTTP, because PHP lets you have some control over these processes. For example, if you understand how HTTP response headers work, you can use your PHP script to create your own custom response headers allowing the script to display an image, or redirect the browser to a new page, for example.

In the following sections you explore how a Web browser makes an HTTP request to the Web server; how the server then sends an HTTP response back to the browser; and how you can influence the HTTP communication between server and browser.

### Understanding HTTP Requests

Whenever a browser wants to display a Web page or other resource (such as an image file) that is stored on a Web server, the browser first connects to the server (usually via port 80, the HTTP port), and then sends various pieces of information to the server, known as the *request message*. The request message consists of the following sections, in order:

- The request line: This tells the Web server which resource (URL) the browser wants to retrieve
- A list of HTTP headers: These optional lines of text allow the browser to send additional information to the server, such as cookies and which character sets the browser can accept
- An empty line: This is required after the request line and any headers
- An optional message body: This might contain, for example, form data sent via the POST method

Each line in the message must end with a carriage return character followed by a line feed character.

The request line is the most important part of the request, because it tells the server which resource to send back to the browser. Here’s a typical request line:

```
GET /about/index.php HTTP/1.1
```

The request line consists of three parts: The request method (`GET` in this case), the URL to retrieve (`/about/index.php`), and the version of HTTP to use (most modern browsers work with `HTTP/1.1`). Other request methods include `POST` (for sending large amounts of form data) and `HEAD` (similar to `GET` but asks the server to return just the response headers, rather than the actual content).

Many HTTP request headers can be sent from a browser to a server. Here are some common ones:

| Header | Description | Example |
| :--- | :--- | :--- |
| Accept | A list of MIME content types that the browser will accept for the returned content. | Accept: text/html, application/xml |
| Accept-Charset | A list of character sets that the browser will accept for the returned content. | Accept-Charset: ISO-8859-1, utf-8 |
| Accept-Encoding | A list of compression methods that the browser will accept for the returned content. | Accept-Encoding: gzip, deflate |
| Accept-Language | A list of languages that the browser will accept for the returned content. | Accept-Language: en-gb, en |
| Cookie | An HTTP cookie previously sent by this server (see Chapter 10 for more on cookies). | Cookie: name=fred |
| Host | This is the only mandatory header, and then only if making an HTTP/1.1 request. Because most Web server applications can serve Web sites at multiple domains on a single machine, the browser sends a Host header to tell the server which Web site it’s requesting the resource from. | Host: www.example.com |
| Referer | When a visitor clicks a link to view a new page, most browsers send the URL of the page containing the link in the Referer header. The Referer URL is often logged by the Web server along with the URL of the page requested. That way, the Webmaster can look through the server logs to see where their visitors are coming from. | Referer: www.example.com |
| User-Agent | Information about the browser, such as its type and version. (You learned how to access this information in Chapter 15.) | User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-GB; rv:1.9.0.5) Gecko/2008120121 Firefox/3.0.5 |

So a complete browser request (assuming there’s no request body) might look like this:

```
GET /about/index.php HTTP/1.1
Host: www.example.com
Accept: text/html, application/xml
Accept-Charset: ISO-8859-1,utf-8
Accept-Encoding: gzip,deflate
Accept-Language: en-gb,en
Cookie: name=fred
Referer: www.example.com
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-GB;
rv:1.9.0.5) Gecko/2008120121 Firefox/3.0.5
```

### Exploring HTTP Responses

When the Web server receives an HTTP request from the browser, it sends back an HTTP response. Typically this includes the content that the browser requested, along with some information about the content, but it may instead return an error (if the content couldn’t be found, for example).
