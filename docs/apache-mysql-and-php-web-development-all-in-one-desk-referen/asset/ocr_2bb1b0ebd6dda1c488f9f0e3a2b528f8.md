You see the contents of test.txt appear on the screen. The first line in the code uses a while loop to grind through each line in the file. The strange <> inside parentheses instructs the Perl interpreter to read the name of the file from the command-line arguments (in this case, test.txt).

Inside the braces (you use braces to delimit blocks of text in Perl), the line print $_; prints out the value of the default variable. The default variable is called $_ in Perl, and inside this while loop, the default variable contains the single line of text.

In Book III, Chapter 4, I tell you more about the while loop, as well as the other kinds of control structures you can use in Perl.

# Running as a CGI script

Because this book is about creating Web sites, you’ll be happy to know that you can use Perl scripts in your cgi-bin directory, where you have your CGI scripts. A CGI script is a program that runs in response to an HTTP request. For example, if you open your browser and visit www.jeffcogswell.com/cgi-bin/dummies.cgi, you see a Perl script run, which prints out the following text:

```
<h1>Hello readers!</h1>
```

This, of course, is HTML-speak for the string Hello readers in Header 1 text.

Here’s the Perl script, which I saved as filename dummies.cgi:

```
#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "<h1>Hello readers!</h1>\n";
```

The first line is a special line that instructs the Web server where to find the Perl interpreter. I talk more about that line — called a pound-bang line — in Book III, Chapter 7.

The next two lines are print statements. When the program operates as a CGI program, these two lines don’t print to the console. Instead, they print out to the Web server and ultimately become the .html file.

The first of the print statements is required when you’re writing an .html file. The next line is the source of the .html file, which is a level-1 header. Nice and sweet.

I talk all about CGI scripts in Book III, Chapter 7.