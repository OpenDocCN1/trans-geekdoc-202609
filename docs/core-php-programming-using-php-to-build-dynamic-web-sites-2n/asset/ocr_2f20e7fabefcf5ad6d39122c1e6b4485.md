# Core PHP Programming

equivalent to whitespace. It is ignored. Comments can be used to document how your code works. Even if you maintain your code you will find comments necessary for all but simple scripts.

In addition to the opening and closing comment statements, PHP provides two ways to build a single-line comment. Double-slashes or a pound sign will cause everything after them to the end of the line to be ignored by the parser.

After skipping over the whitespace and the comment in Listing 1.2, the PHP parser encounters the first word: print. This is one of PHP's functions. A function collects code into a unit you may invoke with its name. The print function sends text to the browser. The contents of the parentheses will be evaluated, and if it produces output, print will pass it along to the browser.

Where does the line end? Unlike BASIC and JavaScript, which use a line break to denote the end of a line, PHP uses a semicolon. On this issue PHP takes inspiration from C.

The contents of the line between print and ; is a call to a function named date. The text between the opening and closing parentheses is the parameter passed to date. The parameter date in what form you want the date to appear. In this case we've used the codes for the weekday name, the full month, the day of the month, and the four-digit year. The current date is formatted and passed to the print function.

The string of characters beginning and ending with double quotes is called a string constant or string literal. PHP knows when quotes surround characters you intend to be treated as text. Without the quotes, PHP will assume you are naming a function or some other part of the language itself. In other words, the first quote is telling uppercase letter. PHP keeps hands off until it finds another quote.

Notice that print is typed completely in lowercase letters, yet date has a leading uppercase letter. I did this to illustrate that PHP takes a very lenient attitude towards the names of its built-in functions. Print, PRINT, and PrInt are all valid calls to the same function. However, for the sake of readability, it is customary to write PHP's built-in functions using lowercase letters only.

# Saving Data for Later

Often it is necessary to save information for later use. PHP, like most programming languages, offers the concept of variables. Variables give a name to the information you want to save and manipulate. Listing 1.3 expands on our example by using variables.

+   Listing 1.3 Assigning Values to Variables