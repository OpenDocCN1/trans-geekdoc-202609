
## Writing HTML using the object form of CGI.pm

Although you can simply call the function in CGI.pm— h1("hello"); for example— you can also use a CGI class available from the CGI.pm module. In this case, you include a simpler form of the use statement. Here's an example:

```
#!/usr/bin/perl
use CGI;
$c = new CGI;
```

```
print $c->header;
print $c->start_html("Welcome!\n");
print $c->h1("My Page");
print $c->h2("Page 2...");
print $c->end_html;
```

This isn't all that different from the non-object (or functional) approach, but the option is available if you prefer a more object-oriented approach.

If you want to see all the functions available, take a look at the source code for the CGI.pm module. You can normally find the CGI.pm file in the lib directory of the main installation directory. After you open the file, scroll down (or search) until you find %EXPORT_TAGS. This is the list of functions that are available to users of the CGI.pm file.

The CGI.pm module is huge and has much more functionality than I have room to describe here. In fact, it's so huge that the guy who wrote CGI.pm, Lincoln Stein, has written a book that you might want to pick up called the Official Guide to Programming with CGI.pm (Wiley Publishing, Inc.). Although the book came out in 1998, the information is still relevant. You can also visit the module's official site at stein.cshl.org/WWW/software/CGI/.

## Specifying HTML parameters

Often in HTML code, you need to specify parameters deep down inside the inner sanctums of the HTML tags. For example, an img tag isn't that useful without the src parameter, which specifies the image file. Take a look at this example:

```
#!/usr/bin/perl
use CGI qw(:standard);
print header;
print start_html("Welcome!\n");
print img((-src=>"/mypic.jpg"));
print end_html;
```

The primary line here is the img tag. Notice how I set the parameters:

```
img((-src=>"/mypic.jpg"))
```

I put the parameters inside curly braces; curly braces are how you create an anonymous reference to a hash. I then put the name of the parameter preceded by a minus sign (in this case, -src), an equal sign, and the greater than sign (to make an arrow-looking thing), and then the data. Thus, I have -src=>"/mypic.jpg", which results in this HTML:

```
<img src="/mypic.jpg" />
```

This tag follows the XML standard of putting a closing forward slash to indicate that no closing tag, such as ы, is present.

If you want to have multiple parameters, separate them with commas, as in the following line:

```
print img((-src=>"/mypic.jpg", -alt=>"mypic"));
```

This line results in the following HTML:

```
<img src="/mypic.jpg" alt="mypic" />
```

## Reading form data

The CGI.pm module is great for reading data. Although you can easily write your own HTML, reading CGI form data is difficult without the help of an extra library.

Here's a CGI script that accesses the parameters:

```
#!/usr/bin/perl
use CGI::Carp qw(fatalsToBrowser);
use CGI qw(:standard);
use CGI qw(:cgi-lib);
print header;
print start_html("Welcome!\n");
$params = Vars;
print "All Params:<br>\n";
while (($key,$value) = each %{$params}) {
    print "$key=$value<br>\n";
}
print "Individual Params:<br>\n";
print $params->{'name'};
print br;
print $params->{'email'};
print end_html;
```

Vars is a function that returns a reference to a hash. I save this reference in the $params variable. Then I iterate through the hash using the while construct. (The each function returns the next key and value pair from the hash each time I call it.) Next, I print out the key and value pair.

Then I access the items individually. Remember, $params is a reference to a hash; it's not a hash itself. I have to use $params->{'name'}; (not $params['name']) to access the individual elements.

The preceding example works with both the HTTP-GET and HTTP-POST methods of sending data from a form. Suppose you save the preceding code as cgipm4.pl (which is what I call it on the accompanying CD-ROM). Then you can use this script in response to either of the forms in the sections “Reading from an HTTP-GET” and “Reading from an HTTP-POST,” earlier in this chapter. In both cases, change the action parameter of the form tag to action="/cgi-bin/cgipm4.pl".

## Displaying Errors and Warnings

If you write a CGI script that has errors in it, you receive a rather foreboding message such as this:

Internal Server Error
The server encountered an internal error or misconfiguration and was unable to complete your request.
Please contact the server administrator,
webmaster@cogswell.biz and inform them of the time the error occurred, and anything you might have done that may have caused the error.
More information about this error may be available in the server error log.

When you see this error, you can look in the error.log file found in the logs directory under the main Apache installation. But I have a better way of finding out the errors.

First, to display errors right on the Web page, add this code to the beginning of your CGI script, after the pound-bang line:

```
use CGI::Carp qw(fatalsToBrowser);
```

This mysterious line, which uses a module called CGI::Carp, causes syntax problems and other errors to display right in the browser window. Here’s an example of a bad script:

```
#!/usr/bin/perl
use CGI::Carp qw(fatalsToBrowser);
print "Content-type: text/html\n\n";
asdf3893333&&
```

(Hopefully that last line isn’t your e-mail name because I don’t have a disclaimer at the beginning of the book that all names are fictitious.) If you save this script in your cgi-bin directory and try to run it, here’s what you see in the browser:

```
Software error:
syntax error at cgi-bin/error.pl line 4, at EOF

Execution of cgi-bin/error.pl aborted due to
compilation errors.

For help, please send mail to the webmaster
(webmaster@cogswell.biz), giving this error message and
the time and date of the error.
```

This method of finding errors is better than looking in the error.log file because it shows you the error message. Of course, you generally don’t want visitors to your site to see an error message, but for your own debugging, this can be pretty handy.

You can also have Perl’s built-in warning mechanism write its errors to the HTML as well. To turn on Perl’s warnings, add a -w parameter at the end of your pound-bang line, like so:

```
#!/usr/bin/perl -w
```

This line causes Perl to generate warning messages if you do something it doesn’t like in your code. To see these messages, add this line after the pound-bang line:

```
use CGI::Carp qw(warningsToBrowser);
```

Or, if you want both errors and warnings, add this line:

```
use CGI::Carp qw(fatalsToBrowser warningsToBrowser);
```

Next, include this line:

```
warningsToBrowser(1);
```

Here's a sample script that generates a warning:

```
#!/usr/bin/perl -w
use CGI::Carp qw(warningsToBrowser);
warningsToBrowser(1);
print "Content-type: text/html\n\n";
print $a;
```

Warnings don't appear in the browser window; they appear as comments in the resulting HTML. If you save the preceding script as warning.pl in your cgi-bin directory and then open it in the browser, you see nothing in the browser window. But if you then view the source, here's what you see:

```
<!-- warning: Use of uninitialized value in print at cgi_bin/warning.pl line 5. -->
```

![](img/3f967ab8a8fddc723173059f56621648_235_0.png)

The CGI::Carp module slows down your script a bit. Therefore, I recommend using the module only during your own debugging. After you've worked out the bugs and you go live with the script, remove (or comment out) the use CGI::Carp line.

## Chapter 8: Ten Useful Perl Functions

### In This Chapter

- Sorting and reversing arrays
- Obtaining the length of an array
- Treating an array as a stack or queue structure
- Converting hex to decimal
- Obtaining a random number
- Searching and replacing substrings
- Converting a string to uppercase or lowercase

In this chapter, I show you ten important functions in Perl that will make your job easier. These include functions on dealing with arrays, such as sorting and reversing arrays, and obtaining the length of an array. Additionally, I’ve included a couple ways that you can treat an array as a stack or queue, giving you more power in your data structures. I also include information on random numbers, converting between hex and decimal, and manipulating strings.

## Sorting an Array

If you want to sort an array, you can do so by simply calling sort:

```
@names = ("John", "Jerry", "Jeff", "Julia", "Jessica");
@newarray = sort @names;
foreach (@newarray) {
    print "$_\n";
}
```

As you can see from this code, sort doesn’t actually modify the array; instead, it creates a new array with the members sorted.
