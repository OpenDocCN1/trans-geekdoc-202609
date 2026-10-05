   

Table of Contents

 

 
|   || [Overview](#part0000_split_001.html#Overview) |
| --- | --- |
| 1 || [Introduction - First Program](#part0000_split_002.html#Introduction) |
| 2 || [HTML & PHP Form](#part0000_split_004.html#HTMLandPHP) |
| 3 || [Control & Loops](#part0000_split_006.html#Control) |
| 4 || [Arrays](#part0000_split_007.html#Arrays) |
| 5 || [Web Application components](#part0000_split_008.html#WebApplications) |
| 6 || [Files & Directories](#part0000_split_009.html#Files) |
| 7 || [Intro to Database](#part0000_split_010.html#Databases) |
| 8 || [PHP for MySQL database](#part0000_split_011.html#PHPMySQL) |
| 9 || [PHP for Oracle database](#part0000_split_015.html#PHPOracle) |
| 10 || [Regular Expression](#part0000_split_017.html#Regularexp) |
|   || [Appendix-I - Workshop](#part0000_split_018.html#Appendix1) |
|   || [Appendix II - Installing Oracle](#part0000_split_020.html#Appendix2) |
|   || [Appendix III- PHP WAMP configuration  -version 5 PHP](#part0000_split_021.html#Appendix3) |
|   || [Appendix IV- Easy PHP interface  -version 7 PHP](#part0000_split_022.html#Appendix4) |

# Overview

 

PHP is a programming language to develop dynamic pages for the world wide web. HTML or hypertext markup language is the base for developing web pages but pages created in HTML are static. PHP allows these HTML pages to interact with a database and do things like adding data or retrieving data from one.

 

In addition, PHP can be used to create the ability to verify user input and provide protection to pages. The prerequisite to understanding PHP is HTML. JavaScript allows dynamism on web pages however, JavaScript is not server based. It works within the client browser. PHP on the other hand is server based. The fact is one needs HTML, JavaScript and scripting language like PHP to complete a professional looking and working page.

 

This book is about PHP. One may want to consider my book on JavaScript if they need a refresher on that subject.

 

The webpage for this book is located at: http://beamto.fjtbooks

 

Before we start:

 

To run a PHP script which is a server based script one will need the following:

 

A note pad editor or similar to save files with the extention ".php".  and

 

A location to put the script when complete. This can be a hosted site of which there are many (free or inexpensive web hosting sites) that allow PHP scripts. On a standalone computer it is possible to download a free PHP editor software. The code for this book was developed using the EasyPHP editor (version 17) and server which can be downloaded and installed for free at the time of writing this book. PHP has different versions and the current version is 7. This book is written for both version 5 and 7. There are some significant differences between these two versions. However, many hosting sites are still using version 5 series.

 

The default database that is included in most hosting sites for PHP is MySQL and the free editors such as the one mentioned above also come with such a database. In addition to this database this book will explore connection to the Oracle database. The Oracle database being used with this book is the stand alone windows version 11.2g Express version which can be downloaded for free at http://www.oracle.com.

# Chapter 1. Introduction

 

The first program by an unwritten tradition in any language is "Hello World". The way to do that in PHP is as follows:

 

Using notepad with a file extention ".php" create a file called hello (hello.php). Put the following lines in that file.

 
| <?php  print "Hello World!!!";?> |
| --- |

 

 

 

 

 

The print can also be replaced by the word echo.

 

Now if one wants to wrap this within HTML tags that is fine such as:

 

 
| <html><body><?php  print "Hello World!!!";?></body></html> |
| --- |

 

 

 

 

 

 

 

 

 

The <? starts the PHP part of the code and ?> ends it. Both of them are mandatory.  If this code is put on a server that does not have PHP, every line of this code will be visible to the user.

 

This is actually the first program in PHP in this book.

 

 
| <html><body><?php  phpinfo();?></body></html> |
| --- |

 

 

 

 

 

 

 

 

 

The above code will give the PHP configuration information for the php installation on the client's PHP server.

 

All settings will be displayed starting with the version number. Most free or inexpensive hosting sites at the time of writing have version 5.4 or higher for PHP on their servers. Backward compatibility is an important part of programming and even though the current version of PHP is higher than this knowledge of features in the old and new is very important.

 

![](images/00001.jpeg)

 

If the current version of PHP which is seven (7) is used the sample output from phpinfo() will be as follows:

 

![](images/00002.jpeg)

 

It is advised to write code in small letters unless a function is specific about letters. Keep in mind that the default setting of keyboards is small letters. The hello.php file can be modified to print the same words "Hello World" in red and in bold, italic and underlined. Note that all HTML code can be passed through the PHP file.

 

 
| <html><body><?php  print"<font color= red> <b><i><u>Hello World!!</u></i></b></font>?></body></html> |
| --- |

 

 

 

 

 

 

 

 

 

 

 

Clarity of code can be enhanced by putting spaces between code lines or between modules of similar code by function.

 

Comments can be added to scripts. There are two types of comments. One for single line and the other for multiple lines.

 

The one for single line is: //

 

The one for multiple line is: /\* ...... \*/

 

Always comment a code in which ever language the program is written. 

 

Variables:

 

Like any programming language PHP is not exempt from variables and like the other languages variables are containers of data. Popular x, y and z taking on different values is also available in PHP.

 

Variables should be given reasonable names that identify what they stand for or what is expected. No reserved words of PHP can be used as a variable.

 

Variable names are case sensitive. Following the $ sign which is required for a variable name in PHP the name must begin with a letter (A-Z or a-z) or an underscore (\_). The name cannot start with a number. This rule is not new many languages have this but the $ sign requirement is a must in PHP. No spaces are allowed within the name except for the underscore.

 

There are four main categories of variables in PHP - numbers, strings, arrays and objects.

 

Number variables consist of the following:

 

Integer - 1,2,3, -1, -2etc

 

Floating point - 1.0, -19.2 etc

 

Date types in PHP consist of numbers and strings are not specifically defined as a variable type.

 

Strings: 

 

A variable is a string if it consists of characters enclosed within a pair of either single or double quotation marks.

 

Example:  "Hello World"

 

"Hello, $name"

 

 " 1"

 

"21.07.17"

 

"2017"

 

Arrays:

 

Arrays by definition store data in index format. The data is entered using keys and retrieved using these keys. The arrays can be single or of multiple dimensions.

 

Example:

 

 
| John || Adam || Smith || Mary || Sally |
| --- | --- | --- | --- | --- |

 

Where John is at index or key 0 and Adam at key 1 and so forth until Sally who is at index at 4. The size of this single dimension array is 5 (0-4). 

 

The arrays that uses numbers for their keys is called a indexed array. An array that uses strings as keys is called an associative array.

 

Arrays are an important part of any programming language.

 

Object:

 

Objects are considered as an advanced feature.  To define an object, its structure called the class has to be defined. Then instances of that structure are created. 

 

The concept of object oriented programming as seen in C++ or Java etc is an example of this type of variable.

 

For example: if there is a variable called car then car. length is an example of the feature of car object.

 

Values are assigned to variables in PHP using the "=" assignment operator.

 

Example:

 

$x = 1.5;

 

$y ="John ";

 

To print out the result we use the print function.

 

Example:

 

print "The number is $x";

 

Now let us create a PHP program that will print the name and address of a person by the name John.

 

 
| <html><head> <title>Address</title></head><body><?php$name = "John";$street= "101, Orchard Lane";$city ="Columbia";$state ="SC";$zip =29208;print "The address of $name  |
| --- |

 

 
| is:<br>$street <br>$city<br>$state<br>$zip";?></body></html> |
| --- |

 

The result will be shown in the browser that is attached to the PHP editor that is being used. In the case of this book, the EasyPHP (http://www.easyphp.org) editor has been used and the output using that editor is as follows:

 

# ![](images/00003.jpeg)

#  

The location of the script will vary according to the editor. Even in EasyPHP editor it is possible to run this script under the projects folder in the older versions (12 through 14) or in the eds-www folder if in version 17. 

 

If an error occurs and it will from time to time-- read the error message, go back to the code written in notepad or editor and correct the code in and around the line number given in the error message.

 

Single quotes mean that the item within them should be taken literally. Double quotes means that the values of the item within the quotes should be taken.

 

For example:

 

$name = 'John' and $name = "John" will give the same result.

 

but 

 

$name = "$firstname" and $name ='$firstname' will give two results.

 

Value of firstname= John and $firstname.

 

It is possible to assign to a variable the value of another variable as:

 

$name =$firstname;

 

It is best to use double quotes and that is what will be used throughout the rest of this book. In addition to the print function there is another function called echo() which will print results or messages to the screen.

 

If one is using the EasyPHP editor version (17) which has PHP 7 in it along with PHP 5.6 the interface will look like this.

 

![](images/00004.jpeg)

 

The two options above are for starting the apache server. The settings icon under HTTP server will allow one to switch between PHP 5.6 and PHP 7.1.3 in this case just by selecting the version from the drop down menu and clicking restart. 

 

At the time of writing this book most hosting websites - especially the low cost and free ones still have PHP version 5 on their servers.  This book will show the output of both versions and highlight where there are significant changes in the new version of PHP.

 

Unless otherwise stated the code seen in this book will work for both old and new versions of PHP.

# Chapter 2. HTML and PHP Form

 

HTML is required to put PHP to full use. PHP programs can have HTML within it and HTML script can have PHP embedded in it.

 

The first script in this chapter will request the name and phone number of a person. The form will have a box to enter the name and phone number and some radio buttons to choose the title of the person's name.

 

The way it works is like this:

 

An HTML form/page requests the user to input data. It then requests the PHP script on the server to process the data request which ultimately will be added to a database.

 

HTML or a webpage has limited capability to interact with the server when it comes to data processing.  It transfers this task using the <form action = </form> method.

 

Let us now write the html code first for the html webpage.

 

 
| <html><head><title>Feedback form</title></head><body><form action="feedback.php"> Mr.<input type="radio" name="title" value="Mr."/>Mrs.<input type="radio" name="title" value="Mrs."/>Ms.<input type="radio" name="title" value="Ms."/><br>Please complete the feedback form</p><p>Name: <input type="text" name="name" size="20"><p>Phone:<input type="text" name="name" size="20"><p><input type ="submit" name="submit" value="Send my response"></form></body></html> |
| --- |

 

The output of this HTML file is as follows: Please note that the feedback.html file and its associated feedback.php file is kept in the same location. However, this is not a requirement. If the files are in separate folders the path to the PHP file must be included in the <form action > statement.

 

![](images/00005.jpeg)

 

So the feedback html file has three parts- selection of title, name and phone. The <form action> statement tells that this file will connect to a script file for further processing. The <form action> is closed by a </form> Now that this html file is transferring data to a PHP file- the PHP file must be able to capture the data being transferred.

 

Observe the <form action> statement. It is missing a method. There are two methods- get and post. What is the difference between the two methods?

 

The GET method sends all the data gathered as a part of the URL. The POST method transmits the data invisibly. Thus choosing GET method might make some vital information visible when the submit button is clicked. There is also a limitation on the amount of data that can be send with GET.

 

The method of transfer from the feedback.html file will be POST. The following change must be made to the feeback.html code in the previous page.

 

<form action ="feedback.php" method="post">

 

The following is the code for the feedback.php file:

 
| <?php$title=$\_POST\['title'\];$name=$\_POST\['name'\];$phone=$\_POST\['phone'\];print"Thank you,$title $name for your feedback.";print"<p> Your phonenumber,$phone has been added to our database.";?> |
| --- |

 

Note that in the feedback.php file above there should be receiving variables to take on the values that are being send from the feedback.html file.

 

In the case above the variable names are the same as that of the data being received but this is not a requirement. The names of the fields could x, y or z.

 

Note that feedback.php has no HTML code. This code can be modified as follows to include HTML code.

 

 
| <html><head><title>Feedback</title></head><body><?php$title=$\_POST\['title'\];$name=$\_POST\['name'\];$phone=$\_POST\['phone'\];print"Thank you,$title $name for your feedback.";print"<p> Your phonenumber,$phone has been added to our database.";?></body></html> |
| --- |

 

More advanced HTML can be used to create response page that is more appealing. But our emphasis here is on the PHP code. 

 

Note that HTML code can be included within the print function and in advanced PHP scripts HTML is usually used dynamically.

 

The output from the feedback.php file is as follows:

 

# ![](images/00006.jpeg)

# If the, get method is used in the feedback.html file to transfer data to the feedback.php form then to retrieve the data the $\_GET\['fieldname'\] method should be used. Older versions of PHP such as those before version 4.1 used to use $HTTP\_POST\_VARS and $HTTP\_GET\_VARS.

 

Let us now look at another HTML file. This HTML page will request the price, quantity, discount and unfortunately the tax of three different items of a supplier. Let us call these different items as widget1, widget2 and widget3.  The HTML code looks as follows:

 

 
| <html><head><title>Price Checker</title></head><body><form action="price.php" method="post"> Widget1.<input type="radio" name="item" value="Widget1."/>Widget2.<input type="radio" name="item" value="Widget2."/>Widget3.<input type="radio" name="item" value="Widget3"/><p>Quantity: <input type="text" name="quantity" size="20"><p>Price:<input type="text" name="price" size="20"><p>Discount:<input type="text" name="discount" size="20"><p>Tax:<input type="text" name="tax" size="20"><input type ="submit" name="submit" value="Send my response"></form> </body></html> |
| --- |

 

The associated php file called price.php is as follows:

 

 
| <?php$item=$\_POST\['item'\];$quantity=$\_POST\['quantity'\];$price=$\_POST\['price'\];$discount=$\_POST\['discount'\];$tax=$\_POST\['tax'\];$tax = ($tax/100);$taxrate =1+$tax;$total = ($quantity \* $price)-$discount;$final=$total\*$taxrate;print"You have chosen $item";print"<p>The quantity ordered is $quantity, at $price$.";print"<p>The discount is $discount$.";print"<p>The tax is $tax.";print"<p>The final cost is $final$";print"<p>Thank you.";?> |
| --- |

 

The resulting pages look as follows:

 

![](images/00007.jpeg)

The above is the price.html page. The values entered are widget1 at quantity 10 and a price of $20 with no discount and tax at 5%.

 

Here the 5 is divided by 100 and then 1 is added to get the tax rate. The total is calculated by multiply quantity with price and subtracting the discount. In this case the discount is 0.

 

Final cost is calculated by multiplying the tax rate and total cost above. The output of the price.php file is as follows:

 

![](images/00008.jpeg)

 

In the example above we have seen the use of numbers in a PHP program and the mathematical operations on them. The example above also illustrated the use of brackets to take into account the mathematical precedence order.

 

Numbers can be formatted using many number functions in PHP. Some of the most used number functions are:

 

round() -

 

Example:

 

round(4.5)= 4

 

round(4.567,2) = 4.57  means rounding to two places after decimal

 

$x = 200.152

round($x,2);  (will give 200.15)

 

number\_format() -

 

Example:

 

number\_format(400.43567,2)  = 400.44

 

number\_format(450,2); = 450.00

 

number\_format(567890321) = 567,890,321

 

This last example cannot be done by round().

 

rand() -

 

Example:

 

$x = rand();  will give a random number

 

if there is a preference for a range of random numbers then:

 

$x = rand(0, 1000) will give numbers within the 0 to 1000 range.

 

The rand() function works in version of PHP which are 4.2 or higher. Older version than 4.2 had srand() function instead.

 

getrandmax() -

 

will get the largest possible random number that can be created using rand().

 

ciel() -

 

This function is part of the rand() function and rounds every number to the next highest integer. (PHP 5)

 

floor() -

 

This function rounds every number to the next lowest integer.

 

abs()-

Example:

 

$x = abs(-25); will give 25

 

$x = abs(25); will give 25

 

PHP supports trigonometry, exponent, base conversion and logarithmic functions. 

 

Let us modify our feedback form that we used earlier in this chapter. This time we are going to have a first name and last name box in addition to the rest.

 

The code for this is a follows:

 

 
| <html><head><title>Feedback form</title></head><body><form action="feedback.php" method="post"> Mr.<input type="radio" name="title" value="Mr."/>Mrs.<input type="radio" name="title" value="Mrs."/>Ms.<input type="radio" name="title" value="Ms."/><br>Please complete the feedback form</p><p> First Name: <input type="text" name="firstname" size="20"><p> Last Name:<input type="text" name="lastname" size="20"><p>Phone:<input type="text" name="phone" size="20"><p><input type ="submit" name="submit" value="Send my response"></form></body></html> |
| --- |

 

Notice the title of the form remains as feedback. The only differences are:

 

1\. Addition of last name and first name text boxes.

 

2\. The name value for each of the name boxes have been changed. These name values will be transferred in the post method to the PHP file.

 

The feedback webpage looks like this now:

 

![](images/00009.jpeg)

 

Now let us modify the feedback.php form to match the webpage above. The code will look like this.

 

 
| <?php$title=$\_POST\['title'\];$firstname=$\_POST\['firstname'\];$lastname=$\_POST\['lastname'\];$phone=$\_POST\['phone'\];print"Thank you,$title $firstname $lastname for your feedback.";print"<p> Your phonenumber,$phone has been added to our database.";?> |
| --- |

 

The code is not much different than the original feedback.php file. We have two names first and last name and in the first print function we have put $firstname $lastname. If a dot is required between names a dot can be put in formatting reasons.

 

We want a full name so we put have to add together the first and last name. PHP does allow the same effect without using the usual dot between two string variables. This is because of the way PHP deals with variables.

 

The result of the code above when using the new feedback.html web page is as follows.

 

![](images/00010.jpeg)

 

 

![](images/00011.jpeg)

 

In PHP there is a term known as magic quotes. If it is turned on in the settings-(check phpinfo() as shown earlier) then these magic quotes will automatically escape problematic characters. This means that single and double quotation marks in strings are preceded by a backlash.

 

The three types of magic quotes are:

 

GPC magic quotes that affect data transmitted via the get or post method and data stored in cookies.

 

Runtime magic quotes that affect data retrieved from databases and command line actions.

 

Sybase magic quotes are a special type and are less of an issue.

 

The default setting is to have magic quotes off. To resolve this, use the following function:

 

stripslashes() in the following manner.

 

$string = stripslashes($string);

 

In the feedback.php file above this could be used as follows:

 

$firstname = ($\_POST\['firstname'\];

$firstname = stripslashes($firstname);

 

Using this function without knowing the settings will not affect the PHP script.

 

Some of the string functions that may be useful are as follows:

 

urlencode() -

 

Example:

 

$string = urlencode($string);

 

Used to encode a string before passing it in a get or post method to a PHP file.

 

urldecode() -

 

Used to decode an encoded string passed.

 

str\_replace() -

 

Parts of a string can be replaced. This is similar to substrings.

 

Example:

$name = str\_replace($x, $y,$z);

 

If 

$x = "E.";

$y = "Edward";

$z =" John E. Smith";

 

Then the "E." will be replaced by the word Edward in the original name of John E.Smith.

 

The new name will be John Edward Smith.

 

The function can be used to catch those words in a response or feedback form that might be considered offensive.

 

strlen() -

 

This returns the number of characters in a string. This will include punctuation and spaces.

 

str\_ireplace() -

 

This is the same as the str\_replace except that it is a case sensitive version of the same.

 

str\_word\_count() -

 

This returns the number of words in a given string using space as a delimiter. Note that this function is available in PHP version 4.3 and higher only.

 

strstr() -

 

This searches a string for the first occurrence of the search pattern given to the function.

 

strpos() -

 

This searches a string and returns the numeric position of the search pattern given to the function.

 

strcmp() -

This is used to compare two strings by returning a whole number.

 

strnatcmp() -

 

This is similar to strcmp() but considered to be more precise linguistically.

 

strcasecmp() and stratcasecmp() -

 

These are the case insensitive companions of strcmp() and strnatcmpt().

 

trim()-

 

Example:

 

$firstname =trim($\_POST\['firstname'\]); It is usually set when the register\_globals setting is set to off. Check phpinfo() settings as shown earliers.

 

But using this function when not knowing the settings will not hurt the PHP script. 

 

trim() function can be further divided into two functions - rtrim() which removes spaces found at the end of a string variable and ltrim() which handles spaces at the beginning the string variable.

 

This is used to remove spaces before and after the text.

 

ucfirst() -

 

Makes first letter of the string capital.

 

ucwords() -

 

Makes the first letter of words in a string capital.

 

strtoupper() -

 

Makes an entire string uppercase.

 

strtolower() -

 

Makes an entire string to lowercase.

# Chapter 3. Control & Loops

 

In every programming language there is a control and loop structure. The IF statement is the most common one.

 

The basic structure of an IF statement in PHP is as follows:

 

if (condition)

{

statement(s);

}

 

The IF condition can be further enhanced by the use of the else in the following manner.

 

if (condition)

{

statement(s);

} else {

other statement(s);

}

 

Let us look at an example. The HTML file for the user login page is as follows.

 

 
| <html><head><title>User Login Form</title></head><body><form action="userlogin.php" method="post"> <p>Please login. </p><p> Username: <input type="text" name="username" size="20"><p> Password:<input type="password" name="password" size="20"><p><input type ="submit" name="submit" value="Send my details"></form></body></html> |
| --- |

In the code above, a user to has to enter his/her username and associated password. The password is kept hidden. The HTML file above will call upon a PHP file by the name user login. The name of the HTML file is userlogin.html.  The page will look like this.

 

![](images/00012.jpeg)

 

Now let us assume that the username should not be less than ten (10) characters and the password also should not be less than ten (10) characters. Further, let the password for administrator username be administrator. 

 

The logic behind this code will be as follows:

 

1\. User types in administrator for username.

 

2\. User types in administrator for password.

 

3\. If username and password length is greater than 10 then the code will check if the username and password matches.

 

4\. The code accepts inputs and thanks the user.

 

5\. If the username and password does not match then a message stating that login is a failure is shown.

 

A point to note is that here the password is hardcoded. In real life the username and password will be stored in a database.

The PHP code for userlogin.php is below.

 

 
| <?php$username=$\_POST\['username'\];$password=$\_POST\['password'\];$x = strlen($username);$y = strlen($password);if (($x < 10) || ($y < 10)){print"The username/password entered is incorrect";} else {if (($username=="administrator") && ($password =="administrator")){print"Thank you for loging in, $username.";}else { print"Wrong username or password";}}?> |
| --- |

 

In the code above the lines:

 

$x = strlen($username);

$y = strlen($password);

if (($x < 10) || ($y < 10))

 

checks to see the length of the string is 10 or more. If not the username and password is wrong. 

 

The else statement goes to check the password and username values if the length of both of them are correct.

 

The second else statement writes a message that the username or password is wrong if the values of the two variables do not match the hard coded combination.

 

IF statements can be nested just like else statements. The example above illustrates the ability to control the flow of logic in a PHP code. 

 

It is similar to the many well known languages such as C++, Java etc.

The previous example also shows in commercial terms that the username and password values have to come from a stored location such as a database.

 

The && and || are known as comparison operators. The "==" is also a comparison operator. It is not the same as "=" which assigns a value to a variable.

 

The comparison operators in PHP are:

 

 
| Operator || Usage |
| --- | --- |
| \== || Equality |
| != || Inequality |
| < || Less than |
| \> || Greater than |
| <= || Less than or equal to |
| \>= || Greater than or equal to |
| ! || Negation |
| And || And |
| && || And |
| Or || Or |
| || || Or |
| XOR || Or not |

 

When using comparison operators, the brackets are very important. The simple rule in programming is if one opens a bracket make sure to close it however lower in the code that may be.

 

PHP has a elseif control structure also. This should not be confused with the following in the above code:

 

else {if (($username=="administrator") && ($password =="administrator"))

{

print “Thank you for logging in, $username.";

}

 

The choice of just writing if statements or with an else statement as in the above case depends on the programmer. Most students learning programming first time are comfortable with just if statements.

 

The above code can be rewritten using the elseif control structure.

 

 
| <?php$username=$\_POST\['username'\];$password=$\_POST\['password'\];$x = strlen($username);$y = strlen($password); if (($x < 10) || ($y < 10)){print"The username/password entered is incorrect";} elseif(($username=="administrator") && ($password =="administrator")){print"Thank you for loging in, $username.";}else { print"Wrong username or password";}?> |
| --- |

 

Like the IF statement, the switch condition is an example of a control structure. The switch condition takes only one possible condition, which is the value of a variable. For example:

 

switch ($variable) {

case "value1":

statement(s);

break;

case "value2":

statement(s);

break;

case "value3":

statement(s);

break;

}

 

This is the same as saying if the value is value 1 in that case do the statements that follow the ":" if not if the value is value 2 then do the statements after that ":" etc. The break tells PHP to exit after finding the correct case match.

 

Look at the following PHP code.

 

 
| <?php$x =$\_POST\['choice'\];switch($x){case 1:If ($x ==1){print "You have chosen item 1.";}break;case 2:If ($x==2) {print "You have chosen item 2.";}break;}print"You have not chosen anything!";?> |
| --- |

 

In the above code a switch is used instead of an if statement to select one of two items. The items will be selected from an HTML page similar to the one below.

 

 
| <html><head><title>Switch</title></head><body><form action="switch.php" method="post"> Please complete the feedback form</p><p> Your choice: <select name="choice"><option value="1">Item 1</option><option value="2">Item 2</option><p><input type ="submit" name="submit" value="Send the choice"></form></body></html> |
| --- |

 

The above HTML page will give a drop down selection option called choice. Choice will have two options. Item 1 and Item 2. A more descriptive name or option can be given in a more elaborate example.

For now, the web page will allow the user to select one of two chooses and click the submit button.

 

The switch.php file will be called by the form action statement in the HTML page and the PHP file will take the value of choice supplied and choose between item 1 and item 2 to display.

 

Notice that in the HTML file for each option a value is given in the option statement.

It is this value that is being sent as a choice to the PHP file.

 

The selection option in HTML is very handy. However, its limitation is that an extensive list of options might be annoying when displayed on the web browser screen.

 

A loop in PHP repeats a certain set of statements until the condition is not true anymore. The for loop is an example of a looping control structure in PHP. The structure of a for loop is as follows:

 

for ($x =1; $x<=10; $x++) {

print $x;

}

 

Here in the for loop there is a initial point which is $x =1 and then a condition that is $x<=10 (less than equal to 10). If the condition is met, then increment by 1 the value of x and print the value of x each time.

 

Thus the numbers will go from 1 through 10 inclusive.

 

The while loop is designed to work as long as the condition is true. The condition is checked in every iteration just like in the for loop.

 

In a do... while loop the statements are executed are executed at least one time.

 

Let us look at some PHP scripts that use the above loops. 

 

 
| <?phpfor($x=0;$x<10;$x++)print "$x<br>";?> |
| --- |

 

In this code the value of $x could be obtained from a form if an associated web page was made. 

 

The output of this with <br> or break in place is as follows.

 

 

![](images/00013.jpeg)

 

Now if we make a webpage for the above PHP script, the code could look like the one in the table below.

 

The PHP script will be modified as in the table that follows the one below to accept the incoming values for x and then to print the values. 

 

The example here shows steps of 2 instead of 1. 

 

The variable names used in the PHP file could have been descriptive so keep this in mind will choosing variable names.

 

We have three variables here and they are: xmin, xmax and xstep.

 
| <html><head><title>loop form</title></head><body><form action="loop.php" method="post"><p> Value for X starting point: <input type="text" name="xmin" size="20"><p> Value for maximum value of X:<input type="text" name="xmax" size="20"><p>Increment step for each value of X:<input type="text" name="xstep" size="20"><p><input type ="submit" name="submit"></form></body></html> |
| --- |

 

The PHP code is as follows:

 

 
| <?php$x =$\_POST\['xmin'\];$y =$\_POST\['xmax'\];$z =$\_POST\['xstep'\];for($x=$x;$x<$y;$x=$x+$z)print "$x<br>";?> |
| --- |

 

The webpage will look as follows:

 

![](images/00014.jpeg)

The following PHP code demonstrates the while loop.

 

 
| <?php$x=0;while ($x<10){$x=$x+1;print"$x";}?> |
| --- |

 

The while loop has the initial point outside the while loop and the increment steps within its statement body. 

 

The loop continues until condition is not true. The output of this 1...10.

 

The following code demonstrates the do...while loop.

 

 
| <?php$x=0;do{$x=$x+1;print"$x";}while ($x<10);?> |
| --- |

 

The output will be the same as the while loop. 1...10.

 

In addition to the break statement in PHP there is an Exit and die statement.  The break statement was seen in the switch. 

 

Instead of exiting the current structure, the Exit and die language constructs terminate the execution of the PHP script.

 

All PHP code after the instance of either Exit or die will never be executed. HTML code after the use of these two constructs will not be send to the web browser.

 

The die construct will be used frequently in code that accesses files and databases. Exit is used often with the header() function.

# Chapter 4. Arrays

 

An Array was mentioned as a variable type in the beginning of the book. An array can consist of numbers and or strings. The array is given a name similar to a variable and the it has the ability to hold more than one value. 

 

Example: An array can be made to include a list of cars as shown below.

 

$car1 = ' Toyota';

 

$car2 = 'GM';

 

$car3 = 'Ford';

 

$car4 = 'Nissan';

 

Array variable naming is as follows:

 

1\. Start with a $ sign.

 

2\. Continue with a letter or underscore.

 

3\. Finish with any combination of letters or numbers or the underscore.

 

An array variable has an index system. An array stands out from other variables with the presence of the \[\] brackets. Thus, $car\[\] is an array variable.

 

The $car\[3\] stands for a specific element of the array at index position 3.

 

To create an array in PHP using the cars example do as follows:

 

$car = array ('Toyota', 'GM' , 'Ford' , 'Nissan');

 

The indexes are automatically assigned by PHP server. Here the model Toyota is indexed at 0. Array indexation automatically starts with 0. This can be changed if needed.

 

In the car array example, we can specifically put the model Toyota at index position 1 by doing the following.

 

$car = array(1=> 'Toyota', 2=>'GM' , 3=>'Ford', 4=>'Nissan');

 

For most purposes leaving the PHP server to index the values in the default manner will be sufficient.

 

 
| <?phpprint"This script will print an array of cars";$car = array ('Toyota', 'GM' , 'Ford' , 'Nissan');print "$car <p>";print\_r($car);?> |
| --- |

 

The output from running this code will be as follows:

 

![](images/00015.jpeg)

 

The output above tells the following:

 

1\. Array values cannot be printed using the print() function used in the previous chapters.

 

2\. Array values can be printed using the print\_r() function instead.

 

3\. When using the print\_r() function the array prints out with its index position shown in number format. 

 

There is no requirement that index positions should be numbers. Words can be used. Let us modify the above PHP code to illustrate this.

 

 
| <?phpprint"This script will print an array of cars";$car = array ('Yaris'=>'Toyota', 'Spark'=>'GM' , 'Escort'=>'Ford' ,'Pathfinder'=> 'Nissan'); print\_r($car); ?> |
| --- |

The output of this code will be as follows:

 

![](images/00016.jpeg)

 

The output is more descriptive as the models are attached to the various car companies in this output.  The models have become the index values. In the default setting for an array the elements of the array are referred to by the index number as follows:  $car\[2\].

 

The range()function can be used to create an array of items based on a range of values. For example:

 

$num = range(1,20);

 

$alp = range('a', 't');

 

The range function will allow for steps such as:

 

$num = range(1,20,2);

 

The var\_dump() function when used with an array the values and structure of the array will be shown. Let us look at a code that will demonstrate these two functions next.

 

 
| <?phpprint"This script will print an array of cars";$car = array ('Yaris'=>'Toyota', 'Spark'=>'GM’, 'Escort'=>'Ford' ,'Pathfinder'=> 'Nissan');var\_dump($car);print"<br>";$num= range(10,20,2);print"<br>";$alp= range('a','z',2);print\_r($num);print"<br>";print\_r($alp);?> |
| --- |

The output will be as follows:

 

![](images/00017.jpeg)

 

An array whose keys are numbers is called an indexed array and those with keys that are strings is called associative array.  These two types have been illustrated in the two examples above.

 

It is possible to add more elements to an array. In the above two examples the car array was used. Once an array is defined in PHP it is possible to add more elements by using the equal to sign and the name of the array with the \[\] brackets.

 

Example:

 

$car\[\] ='Mazda';

 

$car\[\] ='Hyundai';

 

If a key is not specified in the brackets, then each new entry or element of the array will be appended to the existing list. If a key is mentioned in the brackets any value at that key index will be removed and the new element added to that location.

 

 
| <?phpprint"This script will print an array of cars";$car = array ('Toyota', 'GM' , 'Ford' , 'Nissan');$car\[\] = 'Mazda';$car\[\] ='Hyundai';print\_r($car);?> |
| --- |

 

 

![](images/00018.jpeg)

The output will add the new car companies to end of the list as shown above. Let us modify the above script as follows.

 

 
| <?phpprint"This script will print an array of cars";$car = array ('Toyota', 'GM' , 'Ford' , 'Nissan');$num1= count($car);print "The original array has $num1 elements.<p>";$car\[\] = 'Mazda';$car\[\] ='Hyundai';print\_r($car);$num2 =count($car);print"<p>The new array has $num2 elements. <br>";?> |
| --- |

 

The output of the code is as follows.

 

![](images/00019.jpeg)

 

The additional function in the above code is count() which is used to count the number of elements in the car\[\] array.

 

To delete an individual element from an array use the unset() function. 

 

For example:

 

unset($car\[4\]);

 

unset($xyz\['name'\]);

 

If applied to the entire array the whole array will be deleted. To reset an array- that is to empty it without deleting the array variable altogether) use the array() function.

 

For example:

 

$car =array();

Let us look at the following code.

 

 
| <?phpprint"This script will print an array of cars";$car = array ('Toyota', 'GM' , 'Ford' , 'Nissan');unset($car\[2\]);print\_r($car);?> |
| --- |

 

![](images/00020.jpeg)

 

The value at index value 2 is now deleted.

 

PHP has a function to merge two arrays. The function array\_merge($array1,$array2) can be used for this purpose. The names of the two arrays have to be entered into the brackets of the function.

  
For Example:

 

$car1\[\] =('Toyota','GM','Ford');

 

$car2\[\] =('Nissan','Mazda','VW','Hyundai');

 

Writing the code in the following manner will merge the two arrays.

 

 
| <?phpprint"This script will print an array of cars";$car1\[\] =('Toyota','GM','Ford');$car2\[\] =('Nissan','Mazda','VW','Hyundai');$car3 =array\_merge($car1,$car2);print\_r($car3);?> |
| --- |

 

The above merge of two arrays can also be achieved by writing as follows.

 

$car3 = $car1 + $car2;

 

There is only one way to retrieve an array element that is by indicating the key index value. If all elements of an array has to be printed a loop will be needed. 

 

For example:

 

 
| <?php$salary = array ('Adam'=>1000, 'Smith'=> 2000, 'Mary'=> 2500, 'Sally'=>1800);print"The original array looks like this. <br>";foreach($salary as $emp => $amount){print"$emp:$amount<br>";}?> |
| --- |

 

The output for this code will look like this.

 

![](images/00021.jpeg)

 

The loop is a special version of for.  Notice in this example the key is a word and the value is a number unlike the earlier example of car models where both key and value were text.

 

If the output expected is the values of the array and not the index or key along with it then the above code can be modified as in the table below.

 

The difference is in the foreach loop where the index reference is dropped and the value is mentioned.

 

The print is only of the amount and not the index value. Note if the array has no shown index such as $name = array ('Tom','Harry','Smith','Adam'); Then also this method shown below will work.

 

 

 
| <?php$salary = array ('Adam'=>1000, 'Smith'=> 2000, 'Mary'=> 2500, 'Sally'=>1800);print"The original array looks like this. <br>";foreach($salary as $amount){print"$amount<br>";}?> |
| --- |

 

Let us look at an example without a key shown.

 

 
| <?php$name = array ('Tom','Harry','Smith','Adam');print"The original array looks like this. <br>";foreach($name as $emp){print"$emp<br>";}?> |
| --- |

 

The output is as follows.

 

![](images/00022.jpeg)

 

 

Sorting arrays can be done by using the following functions.

 

sort() - This sorts by values but does not maintain the key values.

 

rsort() - This reverses the values and does not maintain the key values.

 

asort() - These sorts by values and does maintain the key values.

 

arsort() - The values are sorted in inverse manner and it does maintain the key values.

 

ksort() - The sorting is done by keys and it maintains the key values.

 

krsort() - Sorting is by keys in inverse and it maintain the key values.

 

Let us look at an example:

 

 
| <?php$salary = array ('Adam'=>1000, 'Smith'=> 2000 , 'Mary'=> 2500, 'Sally'=>1800);print"The original array looks like this.<br>";foreach($salary as $emp => $amount){print"$emp:$amount<br>";}print"The sort using sort() looks like this:<br>";sort($salary);foreach($salary as $emp => $amount){print"$emp:$amount<br>";}print"The sort using rsort() looks like this:<br>";rsort($salary);foreach($salary as $emp => $amount){print"$emp:$amount<br>"; }?> |
| --- |

 

The output will be as follows.

 

![](images/00023.jpeg)

The code for the other sort functions is below.

 

 
| <?php$salary = array ('Adam'=>1000, 'Smith'=> 2000, 'Mary'=> 2500, 'Sally'=>1800);print"The sort using asort() looks like this:<br>";asort($salary);foreach($salary as $emp => $amount){print"$emp:$amount<br>";}print"The sort using arsort() looks like this:<br>";arsort($salary);foreach($salary as $emp => $amount){print"$emp:$amount<br>";}?> |
| --- |

 

The output is as follows.

 

![](images/00024.jpeg)

 

To sort by keys, we use the last two sort functions listed earlier as follows.

 
| <?php$salary = array ('Adam'=>1000, 'Smith'=> 2000, 'Mary'=> 2500, 'Sally'=>1800);print"The sort using ksort() looks like this:<br>";ksort($salary);foreach($salary as $emp => $amount){print"$emp:$amount<br>";}print"The sort using krsort() looks like this:<br>";krsort($salary);foreach($salary as $emp => $amount){print"$emp:$amount<br>";}?> |
| --- |

 

The output will be as follows.

 

![](images/00025.jpeg)

 

The shuffle() function randomly reorganizes the order of an array. 

 

The following code can be used to see its working.

 

 
| <?php$salary = array ('Adam'=>1000, 'Smith'=> 2000, 'Mary'=> 2500, 'Sally'=>1800);print"The shuffle() looks like this:<br>";shuffle($salary);foreach($salary as $emp => $amount){print"$emp:$amount<br>";}?> |
| --- |

 

The output looks like this.

 

![](images/00026.jpeg)

 

If the code is run again another order will be seen. In other words, it shuffles randomly and reorganizes the order of an array.

 

There are times when one of the following has to be done:

 

1\. Convert an array into a string to pass its values to a URL.

 

2\. Convert an array into a string to store the information in a database.

 

3\. Convert a string into an array to convert comma delimited text field into separate parts.

 

There are two functions explode and implode to do these above things. Let us look at an example.

 

In this example we will create two files. One is an HTML file that will send the second file which is in PHP a bunch of words to alphabetize. The words will be separated by a coma. The separator can be something other than a coma also, say for example just empty space.

 

The HTML file code looks like this.

 
| <html><body>Enter some words separated by commas. <br><p><form action="array.php" method="post"><input type="text" name="words" size="100"><p><input type="submit" name="submit" value="Submit"></form></body></html> |
| --- |

 

The webpage will look like this.

 

![](images/00027.jpeg)

The associated PHP file is as follows:

 

 
| <?php$words=explode(',',$\_POST\['words'\]);sort($words);$string = implode('<br>',$words);print"<p> The alphabetized version of the list entered is:<br> $string<p>";?> |
| --- |

 

The output of running this code is as follows.

 

![](images/00028.jpeg)

The words are received from the HTML page and then converted into an array which is sorted. The sorting done here is without a need to maintain a key value association. One may try to other sorts as an experiment.

 

Then a new string is created from the sorted array and the string is then printed.

 

Let us look at an example of an HTML code below.

 

 
| <html><head><title>Price Checker</title></head><body><form action="array.php" method="post"> Widget1.<input type="radio" name="item\[\]" value="Widget1."/>Widget2.<input type="radio" name="item\[\]" value="Widget2."/>Widget3.<input type="radio" name="item\[\]" value="Widget3"/><p><input type ="submit" name="submit" value="Send my response"></form></body></html> |
| --- |

 

The output of this is as follows.

 

![](images/00029.jpeg)

The code is not new. The difference here is the item\[\] used in the check box options. This will create an associated array in the PHP file being called. The code for the associated PHP file is as follows.

 

 
| <?phpprint"This is to demonstrate the use of arrays in a form. <p>";$w=$\_POST\['item'\];foreach ($w as $item){print"$item<br>";}?> |
| --- |

 

The output of the PHP file is as follows.

 

![](images/00030.jpeg)

In itself the purpose of these two codes is to show how an array can be created from a form.

 

Lastly, arrays can be multidimensional. These can be simple and naturally some can be more complex. The purpose of such an array is to provide more information than a standard array.

 

Let us create a multidimensional array.

 

$programming =array('C++','Java');

 

$hardware = array('Networking','Security');

 

Here we have two arrays one for programming and one for hardware subjects.

Both being books on two different subjects can be kept under a second array called books.

 

$books = array ( 'Software' =>$programming, 'Hardware' => $hardware);

 

Thus we have created a multidimensional array.

 

To point to an element in an array within array is at best the same way as done for a single dimensional array by using the index or key number.

 

So a command print "Print the second book in programming is {$books\['Software'\]\[1\]";

 

will print the word Java.

 

Let us look at the full PHP code.

 

 
| <?php$programming =array('C++','Java');$hardware = array('Networking','Security');$books = array (  'Software' =>$programming, 'Hardware' => $hardware);print "The second book in programming is {$books\['Software'\]\[1\]}<p>";print "The first book in networking is{$books\['Hardware'\]\[0\]}";?> |
| --- |

 

The output will be as follows.

 

![](images/00031.jpeg)

Let us modify the above script to use the print\_r () seen in the beginning of this chapter or var\_dump() function to print out the entire multidimensional array.

 

The code is as follows.

 

 
| <?php$programming =array('C++','Java');$hardware = array('Networking','Security');$books = array (  'Software' =>$programming, 'Hardware' => $hardware);print "The second book in programming is {$books\['Software'\]\[1\]}<p>";print "The first book in networking is{$books\['Hardware'\]\[0\]}";print\_r($books);print"<p>";var\_dump($books);?> |
| --- |

 

The output is as follows.

 

 

![](images/00032.jpeg)

# Chapter 5.  Web Application Components

 

The subject of PHP needs knowledge of HTML in the minimum. In addition to this knowledge of Cascading Style Sheets (CSS), Java script and Structured Query Language can greatly enhance the ability to create dynamic, rich looking web pages.

 

This book does not go into development of CSS or Java Script in detail. However, an essential background will be given in SQL in the database part of this book. 

 

In this chapter some important components of making a web application will be looked at. 

 

External files may be used in a PHP program. For example, to create a header or footer for a page. To do this first create a header.html and footer.html file or the files can be PHP files too.

 

These external files can be included in a PHP program by using one of two functions- include() and require().

 

They are used in the following manner.

 

include('footer.html')

 

or 

 

include('footer.php')

or 

 

require('header.html')

 

or 

 

require('header.php')

 

The code will be executed at the point where these functions are called. After execution the code will continue from the line below the include or require function.

The difference between the two functions is that when using include() if there is an error the PHP server will generate a warning but will continue to run other code lines. 

 

In the case of require() if the execution of the included file fails the program terminates.

 

Note the example above assumes that the PHP program using include () or require() is in the same folder as the file being called. If not the absolute or relative paths to the file must be provided within the brackets of the function.

 

An example of a relative path is - require('./footer.html');

 

An example of an absolute path is - require('c:\\users\\desktop\\header.php');

 

 
| <html><body><center><b>Welcome to my page</b></center></body></html> |
| --- |

 

Assume a header.html file as shown above. The associated PHP program calling this header is as follows.

 

 
| <?phpinclude('header.html');print"This is my homepage.";?> |
| --- |

 

The output is as follows.

 

![](images/00033.jpeg)

 

These two functions can come in handy to reduce duplication of work.  

 

Date and time can be displayed in PHP by using the date() function. This function returns date and time information in a format based on the arguments given to it.

 

The options available are as follows.

 

 

Y - means year in 4-digit format.

y - means year in 2-digit format.

 

n - means month as one or two digits such as 4.

 

m - means month as two digits such as 05.

 

F - means month in full form of the name of the month such as August.

 

M - mean month in three letter format such as Aug.

 

j - means day of the month in 1 or 2 digits such as 8.

 

d - means the day of the month in 2-digit format such as 08.

 

l - means the day of the week such as Sunday.

 

D - means the day of the week in three letter format such as - Sun.

 

w - means the day of the week as a single digit - such as 0 for Sunday.

 

z - means day of the year from 0 to 365.

 

t - means the number of days in the month - 31 (for August).

 

S - means the English ordinal suffix for a day as 2 characters - rd.

 

g - means the hour in 12-hour format as 1 or 2 digits such as - 6.

 

G - means the hour in 24-hour format as 1 or 2 digits such as 14.

 

h - means the hour in 12-hour format as 2 digits such as 08.

 

H - means hour in 24-hour format as 2 digits such as 14.

 

i - means minutes such as 35.

 

s - means seconds such as 15.

 

a - means am or pm.

 

A - means AM or PM.

U - means seconds since epoch such as 1048623008.

 

Let us look at this PHP code.

 

 
| <?php$x =date('l,F,Y');$y = date('h:i:s');print "$x<p>$y";?> |
| --- |

 

The output will be as follows.

 

![](images/00034.jpeg)

 

It is also possible to write print date('l,F,Y'); to get a result.

 

A timestamp in PHP is a number representing how many seconds have elapsed since midnight of January 1 1970. The time() function returns a timestamp for the current moment. The mktime() function can return a timestamp for a particular date and time.

 

For example:

 

$x =mktime(06,12,30); where 6 is the hour, 12 the minutes and 30 is the seconds. 

 

An important function in PHP programs for the web is the ability to send email. Sending mail in PHP is done by the mail() function. The PHP function works in tandem with the servers email application such as the sendmail on Unix or a SMTP(Simple Mail Transfer Protocol) server to send out emails.

 

mail('mailto','subject','body of message', 'From: email address of Sender');

 

It is important to check with the host service before using a send mail service. There may be additional requirements from the host service especially if the service package is a shared one.

 

 
| <?php$x = $\_POST\['email'\];$y = $\_POST\['password'\]$body="Thank you for registering at my webpage. Your email address is $x and the password you entered is $y".mail( $x,'Registration complete',$body,'From:admin@yyy.com');?> |
| --- |

 

This is a sample code of sending mail. It is assumed here that a form or HTML page will supply the email and password of the user. The body thanks the user for the registration and send the email with the admin's email as sender’s email. Use of mail on shared servers for websites should be used with caution. It is possible to have a server or domain marked as a source of spam affecting legitimate emails.

 

Cookies are way for a server to store information about the user. Many websites require cookies to be enabled before the contents are displayed. 

 

Cookies have to be sent from the server to the client machine before any other information.

 

Cookies are sent using the setcookie() function. For example:

 

setcookie('Cookiename', 'This is a test cookie');

 

There may be a limit of the number of cookies that can be sent from a server to a single user. Cookie names should follow the naming rules of PHP.

 

 
| <?php$cookies=false;setcookie('color',$\_POST\['color'\]);$cookies=true;if($cookies) { print"Your preference has been saved."; }?> |
| --- |

 

The HTML code for the above PHP file is as follows.

 

 
| <html><head><title>Cookie Example</title></head><body><form action="cookie.php" method="post"> Yellow<input type="radio" name="color" value="Yellow"/>Red<input type="radio" name="color" value="Red"/>Blue<input type="radio" name="color" value="Blue"/><br>Please complete the feedback form and send your preference of color. </p><p><input type ="submit" name="submit" value="color"></form></body></html> |
| --- |

 

The HTML page will call the cookie.php file and pass on to it the preference of the user.

 

The resulting output is as follows.

 

![](images/00035.jpeg)

To retrieve a value from a cookie, use the $\_COOKIE\['cookiename'\] method.

 

 

 
| <?phpprint $\_COOKIE\['color'\];?> |
| --- |

 

The output will be red since I had chosen red.

 

Next we look into adding some parameters to the cookie. The parameters to be added are expiration, path, domain and term secure. 

 

setcookie('color',$\_POST\['color'\], time()+60,' ',' ',1);

 

This follows the format: setcookie('name','value',expiration,'path','domain',secure);

 

The path and domain are used to limit a cookie to a specific folder in a website or to a specific domain such as www.xyz.com. The path could be something like this '/userpages/’.

 

In the example above both path and domain has been disregarded. Look at the code below.

 

 
| <?php$cookies=false;setcookie('color',$\_POST\['color'\], time()+60,' ',' ',0);$cookies=true;if($cookies) {print"Your preference has been saved.";}?> |
| --- |

 

and using the same html file as before (reproduced here for convenience).

 

 
| <html><head><title>Cookie Example</title></head><body><form action="cookie.php" method="post"> Yellow<input type="radio" name="color" value="Yellow"/>Red<input type="radio" name="color" value="Red"/>Blue<input type="radio" name="color" value="Blue"/><br>Please complete the feedback form and send your preference of color. </p><p><input type ="submit" name="submit" value="color"></form></body></html> |
| --- |

 

The output is as follows.

 

![](images/00036.jpeg)

 

![](images/00037.jpeg)

![](images/00038.jpeg)

So the duration of this cookie is 60 seconds from the current time. If 1 hour is needed then it will be time() +3600 and so forth. The number 0 for secure means that cookie is not send over a secure connection. The alternative is 1 for HTTPS connection.

 

After 60 seconds or 1 minute if the cookie is read using the $\_COOKIE\['color'\] option no value will be found. An error message will be displayed.

 

To delete a cookie the setcookie() can be used in the following manner.

 

setcookie('cookiename',' ');

 

setcookie('cookiename', ' ', time()-60);

 

which is like stating an expiration date in the past.

 

Let us look at this code.

 

 
| <?php$cookies=false;if(isset($\_POST\['submit'\])){setcookie('color',$\_POST\['color'\], time()+60,' ',' ',0);$cookies=true;}?><html><head><title>Cookie Example</title></head><body><form action="cookie.php" method="post"> Yellow<input type="radio" name="color" value="Yellow"/>Red<input type="radio" name="color" value="Red"/>Blue<input type="radio" name="color" value="Blue"/><br>Please complete the feedback form and send your preference of color.</p><p><input type ="submit" name="submit" value="color"></form><?phpif($cookies) {print"Your preference has been saved.";}?></body></html> |
| --- |

 

Basically the code above is a combination of the cookie PHP file and its HTML page. The only addition is the line if(isset($\_POST\['submit'\])){ } this condition and function in PHP allows us to write a PHP file for the cookies as a single file instead of two different files.

 

The isset() function checks if the submit button in the HTML form has been clicked or not. If yes it will continue with the lines inside the bracket which is the creation of the cookie. Most hosting sites of websites will allow for this kind of mix of PHP and HTML in a single PHP file. It is also possible to have PHP within HTML files. Check with the hosting service before signing up or after on any configurations they may require. This advice is for those who use shared hosting.

 

A session provides a way to track data for a user over a number of pages. Cookie stores data on the client and a session stores it on the server. In addition to this a session has the following characteristics.

 

1\. They are more secure, as the data is on the server only.

 

2\. They allow for storage of more information than a cookie. 

 

3\. They can be made to work even if cookies are not accepted by the user of the website.

 

A session is like the English meaning of the word (a period of time-like a class session). A random session ID is created when a session starts. This is a reference to that particular session and its stored data.

 

The session ID is sent to the web browser as a cookie and following PHP pages will use this cookie to get the session ID to access its data.

 

To start or create a session in PHP we start with the session\_start() function. This function must be one of the first lines on every PHP page that uses sessions.

 

The cookie which is sent to the browser will have a name such as PHPSESSID and a value such as 3bcc37dc87cb4b54d63f99da23fb41f1.

 

Once the session has started one can record data to it by assigning values to the 

 \_SESSIONarray.

 

$\_SESSION\['color’\] ='Yellow';

 

$\_SESSION\['age’\] =35;

 

The data is written to a temporary file stored on the server. Let us look at the following code.

 

This code is for a login box.

 

 
| <?phpif(isset($\_POST\['submit'\])){if (($\_POST\['username'\]=='admin') && ($\_POST\['password'\]=='admin')){session\_start();$\_SESSION\['username'\] ='admin';$\_SESSION\['login'\] =time();print"You are logged in";exit();}}?><html><head><title>Session Example</title></head><body><form action="session.php" method="post"> <p>Username:<input type="text" name="username" size="20"><p>Password:<input type="text" name="password" size ="20"><p><input type ="submit" name="submit" value="Submit"></form></body></html> |
| --- |

 

The login box will look as follows.

 

![](images/00039.jpeg)

This code starts with the isset function seen in the last cookie example. This checks if the submit button is hit or not.

 

The next if statement checks if the password and username are as required. If it is it will print a message and exit() function will stop execution of any further code. Alternatively if there is a welcome page to be directed to one can use the header () function as follows- header('Location:welcome.php'); followed by exit(); Make the change in the above code.

 

If the username and password entered is incorrect the program will display an empty form for further login attempt.

 

So now we have started the session for login page. To access session variables let us first create the welcome.php file so that once the user logs in they will get this page.

From this page we will access the logged in period of the user.

 

The welcome page looks like this in terms of code.

 

 
| <?phpsession\_start();print"Welcome to my webpage!!<p>";print ($\_SESSION\['username'\]);print"<p>You have logged in since:<p>";print date('g:i a',$\_SESSION\['login'\]);print "<p><a href=logout.php>Logout</a>";?> |
| --- |

 

This code will print the welcome message with the username and the state the time and given an option to logout.  The output of this code is as follows.

 

![](images/00040.jpeg)

 

The logout page script look as follows.

 

 
| <?phpprint"You have logged out!!<p>";?> |
| --- |

 

The logout script will be changed shortly. The last point in sessions is how to delete a session. 

 

To do this start with session\_start() and then delete the session variables which in our example is username and login time using the unset() function. 

 

unset($\_SESSION);

 

Finally the data is removed from the server using the session\_destroy() function. Therefore, the above logout script will look as follows.

 

 
| <?phpsession\_start();unset($\_SESSION);session\_destroy();print"You have logged out!!<p>";print"Thank you for visiting my page.";?> |
| --- |

 

After you see the logout page try to hit the back button and see what happens.

 

The output is as follows:

 

![](images/00041.jpeg)

 

A point to note is that sessions might be implemented slightly differently on web hosting where hosting is of shared type. Thus it is important to check with the web host faq table or technical support on how it is configured for such kind of hosting.

 

Functions in PHP can be user made. The functions seen thus far have been already defined in PHP.

 

A user defined functions is useful when there is no known function that does a particular task. Function like in all programming languages decrease repetition of code and actually decreases the size the overall lines of code.  

 

The format of making a function is a follows:

 

function function\_name()  {

statements;

}

 

The function names follow the same rules of variable names except there is no $ sign for a function. The statements within the {} can be any valid PHP statement.

 

Let us now look a user made function. This one is called make\_car\_menu and from the name it should be obvious that this function is related to cars. 

 

 
| <?phpfunction make\_car\_menu (){$car =array(1=>'Nissan',2=>'GM',3=>'Ford',4=>'Toyota',5=>'Mazda',6=>'Tesla',7=>'Mitsubishi',8=>'Hyundai',9=>'VW',10=>'BYD');print"<select name='car'>";foreach ($car as $key=>$value){print"<option value=$key>$value</option>";}print"<select>";}//end of functionprint"<form action='' method='post'>";make\_car\_menu();print"</form>";?> |
| --- |

 

The function make\_car \_menu is defined a car array variable and using the foreach loop we are printing out the menu items for the select option. Notice an important part of this code- 1) It is written in a single PHP file. 2) Whenever there are two "" in a print or PHP statement the outer quotations should be "" but inner quotations have to be single( ' )type. 

 

The output of this code is a single selection option drop down list as shown below.

 

![](images/00042.jpeg)

As usual in programming never forget to close the brackets that are opened. The form action here is used to create a form to display the option as this program does not have a complete web page.

 

Now let us write a new program. This program will display a certain number of years based on the current year. The program is different in the sense that arguments will be passed via a function to create a select list starting with the current year and going for three years hence.

 

The following code is how arguments can be passed to a function in PHP.

 

 
| <?phpfunction make\_year\_menu ($startyear,$num){print"<select name='year'>";for ($y=$startyear;$y<=($startyear+$num);$y++){print"\\n<option value=\\'$y'\\>$y</option>";}print"</select>";}print"<form action='' method='post'>";$startyear=date('Y');make\_year\_menu($startyear,3);print"</form>";?> |
| --- |

 

The output of the above code is as follows:

 

![](images/00043.jpeg)

 

The code finds the current year through the line $startyear =date('Y'); It is also possible to modify this code further to ask how many years hence has to be displayed. A for loop is used to create the select options. Arguments are passed to the function from outside the function in the form part of the program.

 

Functions can return a value. In the following program the sum of two numbers will be calculated. The program is written as a single PHP file.

 

The inputs are taken from two text boxes in the form inside the PHP file.

 
| <?phpfunction sum ($num1,$num2){$sum =$num1 +$num2;return $sum;}if (isset($\_POST\['submit'\])){$sum=sum($\_POST\['num1'\],$\_POST\['num2'\]);print"<p>The sum of these numbers is <b>$sum</b><p>";}print"<form action='function.php' method='post'><p>";print"First Number:<input type='text' name='num1' size='5'><p>";print"Second Number:<input type='text' name='num2' size='5'><p>";print"<input type='submit' name='submit' value='ADD'>";print"</form>";?> |
| --- |

 

The isset function has been used before. When a single file of PHP code is written with a form and a button the isset function can be used to see if the submit button has been clicked.

 

The function sum has two parameters num1 and num2. The names can be anything meaningful. The form passes the values of the variables num1 and num2 as input by the user. The sum is calculated in the function and then displayed using the print statement in isset function.

 

The output will look like this.

 

![](images/00044.jpeg)

Variables have a feature called scope. This is very important when defining variables. The scope is based on the location of the variables in the code.

 

Scope of a variable is defined as the realm in which it exists.

 

Variables defined in a function exist only within that function. In the same manner a variable outside a function can only be referenced by the function by passing it as an argument as was seen in the last two examples or by using the global statement.

 

Let us modify the example of adding two numbers to calculate the price of two items and find the final price after a tax rate of 5%.

 

 
| <?php$tax =5;function sum ($price1, $price2) {global $tax;$sum =$price1 + $price2;$taxrate =($tax/100) +1;$sum = $sum \* $taxrate;return $sum;}if (isset($\_POST\['submit'\])){$sum=sum($\_POST\['price1'\],$\_POST\['price2'\]);print"<p>The total price of these two items is <b>$sum</b><p>";}print"<form action='function.php' method='post'><p>";print"First Item price:<input type='text' name='price1' size='5'><p>";print"Second Item price:<input type='text' name='price2' size='5'><p>";print"<input type='submit' name='submit' value='Calculate'>";print"</form>";?> |
| --- |

 

The code here takes from the user the price of two items and add them. After adding the prices, it then calculates the taxrate based on the global variable tax. 

 

Taxrate is multiplied with sum to display the final price. An important part of defining variables is its location and hence its scope. 

  

 Chapter 6. Files and Directories

 

The first step to understanding the importance of a database is files and directories. There are two ways to store data with PHP and with most programming languages. They are files & directories or a database.

 

In a web hosting environment especially one that is shared the settings by the host provider might be a little strict when it comes to files.

 

A file such as a text file (.csv,.dat, .txt) have certain permission settings on the web host. The directory also will have these permissions. 

 

The permission options are read, write and executable. In addition to these options can be set in three different ways based on the user. The owner gets automatic write and read rights whereas others and groups are given only read permission.

 

Irrespective of the type of hosting (Unix or Windows) the hosting service might limitations for security reasons on allowing access to write on files and directories in the case of shared hosting. This needs to be studied upfront before spending time creating a PHP program based on files and directories for storage and retrieval. 

 

As mentioned in the previous line files, directories and a database basically store data and allow them to be retrieved.

 

To write to a file using PHP the following functions can be used:

 

fopen() to open a file for writing in a particular mode.

 

fwrite() to actually write the data to the file.

 

fclose() to close the connection to the file.

 

fopen() function has several modes of opening a file to write. They are:

 

r - for reading only. The reading will start at the beginning of the file.

 

r+ - for reading or writing. Either will start at the beginning of the file.

 

w - for writing only. If the file does not exist, then it will be created and overwrite any existing content.

w+ - for reading or writing. If the file does not exist, then it will be created and 

overwrite any existing contents when writing.

 

a - for writing only. The file will be created if it does not exist and new data will be appended to the end of the file.

 

a+ - for reading or writing. The file will be created if it does not exist and new data will be appended to the end of the file.

 

x - for writing only. The file will be created if it does not exist but if the file exists then nothing will be done.

 

x+ - for reading or writing. The file will be created if it does not exist but nothing will be done if the file already exists.

 

If the file is not in the same location as the PHP file, the path to the file should be included in the code. Let us look at the following code where some data will be written to a text file called data.txt.

 

 
| <html><body><?phpif (isset($\_POST\['submit'\])) {if($fx = fopen('data.txt','ab')) {$data=$\_POST\['data'\];fwrite($fx,"$data\\n");fclose($fx);}}?><form action="file.php" method="post"><p><textarea name="data" rows="5" columns="30"> Enter your data here. </textarea><p><input type="submit" name="submit" value="Write the data"></form></body></html> |
| --- |

 

In the code above the text area box allows for data to be entered. The data entered as an example is - This is a statement.

 

The data.txt file is created since it did not exist and writing was in the form of an append. The 'ab' means append using binary mode. The 'b' is optional.

 

The result is as follows:

 

![](images/00045.jpeg)

 

 

![](images/00046.jpeg)

The code can be made more accurate by using $data=trim($\_POST\['data'\]);

and using the empty function in the following manner.

 

if(!empty($\_POST\['data'\]). 

 

Let us rewrite the code shown above to include these two statements. The second one will make sure that there is some data in the text area box to be written or appended to the data file.

 
| <html><body><?phpif (isset($\_POST\['submit'\])) {if(!empty($\_POST\['data'\])){if($fx = fopen('data.txt','ab')) {$data=trim($\_POST\['data'\]);fwrite($fx,"$data\\n");fclose($fx);}}}?><form action="file.php" method="post"><p><textarea name="data" rows="5" columns="30"></textarea><p><input type="submit" name="submit" value="Write the data"></form></body></html> |
| --- |

 

This code is the same as the one seen before but adds an empty text area box. If the box is left empty nothing will be appended to the file. However, if the data is written in the text area box it will be written to the data.txt file. The line if(!empty($\_POST\['data'\])) checks if the data is present in the text area box.

 

If two users were submitting data to the single file, there could be some problems. Thus an important of writing to a file is locking. This is not issue when using databases because they have their own in built locking mechanisms.

 

The lock type has to be mentioned after the fopen() statement. The lock types are as follows:

 

LOCK\_SH - shared lock for reading purposes.

 

LOCK\_EX - Exclusive lock for writing purposes.

 

LOCK\_UN - Release of a lock.

 

LOCK\_NB - Non blocking lock.

 

So the above writing script to data.txt file can be modified as follows:

 

 
| <html><body><?phpif (isset($\_POST\['submit'\])) {if(!empty($\_POST\['data'\])){if($fx = fopen('data.txt','ab')) {$data=trim($\_POST\['data'\]);flock($fx,LOCK\_EX);fwrite($fx,"$data\\n");flock($fx,LOCK\_UN);fclose($fx);}}}?><form action="file.php" method="post"><p><textarea name="data" rows="5" columns="30"></textarea><p><input type="submit" name="submit" value="Write the data"></form></body></html> |
| --- |

 

In terms of writing there will be no difference in the data.txt file. The lock used here is an exclusive lock. Another user cannot write to data.txt while you submit the data. The locks have to be unlocked to allow others to use the same file.

 

Reading a file is as important as writing to it. The function that can be used to read files in a single swoop is file().

 

The file() function uses an array to enter data read from the file. Let us look at the code to read the data entered into the data.txt file used so far in this chapter. This data .txt file has three statements entered into it using the script above for writing.

 

The statements are: This is the first statement. This is the second statement. This is the third statement.

 

The code is as follows:

 

 
| <?php$data =file('data.txt');$n =count($data);foreach ($data as $key=>$value) {print"$value<p>";}?> |
| --- |

 

Please note that the variable $data is an array and we are printing out the result as shown in the chapter on arrays.

 

The output is as follows:

 

![](images/00047.jpeg)

Creating a directory in PHP is done using the mkdir function. The format for this function is as follows:

 

mkdir('directory-name', permissions);

 

Permissions are ignored on Windows based servers.  Please note the policy of the web host before creating directories or using files for storing and retrieving data. 

It is my strong opinion that these functions in a professional setting be done using a database.

 

Let us create a code that will ask for the directory name and file name to be created and then put some text in the file in that directory. The code for that is as follows:

 

 
| <html><body><?phpif(isset($\_POST\['submit'\])){$dirname=trim($\_POST\['dirname'\]);mkdir("$dirname",0777);$filename=trim($\_POST\['filename'\]);$data=trim($\_POST\['data'\]);if($fx = fopen("C:\\Program Files (x86)\\EasyPHP-DevServer-14.1VC9\\data\\localweb\\scripts/$dirname/$filename","ab")){fwrite($fx,"$data\\n");fclose($fx);}}?><form action="file.php" method="post"><p>Directory name: <input type="text" name="dirname" size ="20"><p>File name:<input type="text" name="filename" size="20"><p>Text to be entered into file:<input type="text" name="data" size="50"><p><input type="submit" name="submit" value="Write the data"></form></body></html> |
| --- |

 

This code will create the directory using mkdir(). The path to the file needs to be carefully entered. A wrong/or \\ will cause problems with the code.

# Chapter 7. Intro to Databases

 

The database that comes with PHP developer kit or in free or shared hosting is the MySQL database. There are exceptions. In this chapter we will look into the basics of the SQL (Structured Query Language) needed to operate any database. 

 

SQL has four important commands with respect to manipulating data kept in tables in a database. These four commands are:

 

Select - to retrieve data from the tables of a database.

 

Insert - to add data to a table in a database.

 

Update - to change data in a table of the database.

 

Delete – to remove data in a row of a table of the database.

 

Further to these there are commands for creating a database, table, view, index, procedure.

 

In web hosting sites there is a control panel to create a database and the tables associated with them. In Unix/Linux hosting the most popular control panel currently in the market is the C-Panel. It may look like the one below.

 

![](images/00048.jpeg)

 

The administration of the databases in the case of Unix/Linux based C-Panels is done using the PHPMyAdmin option. In all cases of hosting always be familiar with the faq’s of the hosting being used.

 

In the grades table below we insert as follows:

 

 
| sid || name || prelim || midterm || final |
| --- | --- | --- | --- | --- |
| 100 || Albert || 100 || 78 || 89 |
| 101 || Robert || 98 || 93 || 85 |

 

Insert into grades values ('100','Albert',100,78,89);

 

The alphanumeric/char characters need to be within single quotes. 

 

Numbers do not have be within quotes.

 

It is very important in an insert statement to follow the same sequence of fields as in the table. 

 

One can skip a particular field or leave the value for a particular field blank as follows:

 

Insert into grades values ('100,'Albert’, null,78,89);

 

The value of the prelim in the example above can be later filled in using the update statement as follows:

 

update grades set prelim=100 

where sid = '100';

 

Let us add one more row into the table.

 

insert into grades values ('101','Robert',98,93,85);

 

To delete a table or row of the table we use the following command:

 

delete grades were sid='100';

 

This will delete only the row where sid = 100 and no other row. Deleting should be used carefully.

 

delete grades;

 

will result in all rows being deleted. Another way to remove all data in a table is truncate.

 

truncate table grades;

 

To completely remove the table from the database- including structure and values use the drop command as follows:

 

drop table grades;

 

These commands (drop, truncate, delete) must be used with caution in real life when working in a company or organization. The following is a summary of the commands that one needs to use a database.

 

DDL: Data Definition language

 

 
| Create  || Creates a new table. |
| --- | --- |
| Alter || Modifies an object such as a table. |
| Drop || Deletes a table. |
| Truncates || Removes the values of the fields of a table but leaves the structure of the table intact. |

 

DML: Data Manipulation language

 

 
| Select || Retrieves parts of a table in response to a user’s query. |
| --- | --- |
| Insert || Puts values into a table. |
| Update || Modifies rows in a table.  |
| Delete || Removes rows from a table. |

 

DCL: Data control language

 

 
| Grant || Gives a privilege to a user such as permission to view or modify a table in a database. |
| --- | --- |
| Revoke || Removes a privilege from a user. |

Look at the table below: The name of the table is staff.

 

 
| sid || name || job || salary || location |
| --- | --- | --- | --- | --- |
| 100 || Robert || Manager || 8000 || Atlanta |
| 101 || Albert || Administrator || 3000 || Atlanta |
| 102 || Sally || Secretary || 2000 || Atlanta |
| 103 || Martha || Receptionist || 1500 || Atlanta |
| 104 || John || Accountant || 5000 || Atlanta |
| 105 || Sandy || Trainee || 1000 || Atlanta |

 

In this table all fields are of type text except for salary which is of type number. Let us run some select against this table.

 

select \* from staff;

 

This will give the all values of the table staff.

 

select sid, name, job from staff;

 

 
| sid || name || job |
| --- | --- | --- |
| 100 || Robert || Manager |
| 101 || Albert || Administrator |
| 102 || Sally || Secretary |
| 103 || Martha || Receptionist |
| 104 || John || Accountant |
| 105 || Sandy || Trainee |

 

select sid, name job from staff 

where 

salary > 3000;

 

 
| sid || name || job |
| --- | --- | --- |
| 100 || Robert || Manager |
| 104 || John || Accountant |

 

If salary of 3000 is to be included the select query will look like this:

 

select sid, name job from staff 

where 

salary >= 3000;

 

The comparison operators are therefore:

 

 
| \=  || to compare values of two variables. |
| --- | --- |
| != || Not equal to. |
| \> || Greater than. |
| < || Less than. |
| \>= || Greater than and equal to. |
| <= || Less than and equal to. |

 

 
| < || Not less than. |
| --- | --- |
| !> || Not greater than. |
| <> || Compares two values are equal or not. If values are not equal then  condition becomes true. |

 

Logical operators in SQL are as follows:

 

 
| AND || Multiple conditions each of which has to be satisfied. |
| --- | --- |
| OR || Any of the conditions need to be satisfied. |
| ALL || Used to compare a value to all values in anothervalue set. |
| ANY || Used to compare a value to any applicable value inthe list as per the condition |
| BETWEEN || Used to search for values that are within a set of values, given the minimum value and the maximum value. |
| EXISTS || Used to search for the presence of a row in aspecified table that meets a certain criterion. |
| IN || Used to compare a value to a list of literal values thathave been specified. |
| LIKE || Used to compare a value to similar values using wildcard operators. |
| NOT || Used with other logical operators to negate the effect the logical operator. |
| IS NULL || To compare and find if a value is null. |
| UNIQUE || searches each row of table foruniqueness. |

 

Let us look at some examples using the following table: The name of the table is staff.

 

 
| sid || name || job || salary || location |
| --- | --- | --- | --- | --- |
| 100 || Robert || Manager || 8000 || Atlanta |
| 101 || Albert || Administrator || 3000 || Atlanta |
| 102 || Sally || Secretary || 2000 || Atlanta |
| 103 || Martha || Receptionist || 1500 || Chicago |
| 104 || John || Accountant || 5000 || Chicago |
| 105 || Sandy || Trainee || 1000 || Miami |
| 106 || James || Lawyer || 7000 || Miami |

 

select name from staff 

where

salary > 7000

and location = 'Atlanta';

 

The only person would be: Robert 

 
|   name |
| --- |
| Robert |

 

If the “and” was replaced by “or” the result would be different. 

 

 
| name |
| --- |
| Robert |
| Albert |
| Sally |

 

The reason is that only one condition has to be satisfied. Robert does make more than 7000 and is located in Atlanta but both Albert and Sally are also located in the same place but they do not make a monthly salary greater than 7000.

 

select name from staff

where

salary is null;

 

In the example above the query is searching for a null value in salary column. Null means nothing. In a database nothing is something and that something is called Null.  The query will not find any names as there is no name with null salary values.

 

Let us repeat the staff table here for convenience:

 

 
| sid || name || job || salary || location |
| --- | --- | --- | --- | --- |
| 100 || Robert || Manager || 8000 || Atlanta |
| 101 || Albert || Administrator || 3000 || Atlanta |
| 102 || Sally || Secretary || 2000 || Atlanta |
| 103 || Martha || Receptionist || 1500 || Chicago |
| 104 || John || Accountant || 5000 || Chicago |
| 105 || Sandy || Trainee || 1000 || Miami |
| 106 || James || Lawyer || 7000 || Miami |

 

select \* from staff 

where 

location in ('Miami', 'Chicago');

 

Notice that when values are text –they have to be enclosed within single quotes. Numbers do not have to. If we change the last line of this query to location not in ('Miami', 'Chicago') then only names of those located in cities other than Miami or Chicago will be shown. The result of this query will be info on those located in two cities.

 

 
| sid || name || job || salary || location |
| --- | --- | --- | --- | --- |
| 103 || Martha || Receptionist || 1500 || Chicago |
| 104 || John || Accountant || 5000 || Chicago |
| 105 || Sandy || Trainee || 1000 || Miami |
| 106 || James || Lawyer || 7000 || Miami |

 

Let us look at this query:

 

select \* from staff

where

salary > 3000

and salary < 6000;

 

The query is requesting those who have a salary between 3000 and less than 6000. The query will produce the following result:

 

 
| sid || name || job || salary || location |
| --- | --- | --- | --- | --- |
| 101 || Albert || Administrator || 3000 || Atlanta |
| 104 || John || Accountant || 5000 || Chicago |

 

The same query could be written as follows:

 

select \* from staff

where

salary between 3000 and 6000;

 

The following query takes a look at the “like” operator:

 

Select \* from staff

Where

Name like 'R%';

 

This will give the following result:

 

 
| sid || name || job || salary || location |
| --- | --- | --- | --- | --- |
| 100 || Robert || Manager || 8000 || Atlanta |

 

It is the only name that starts with an R. Martha too has the alphabet “r” but it is not at the starting position.

 

It is possible to call a select query from another query. The following is an example that shows this along with the use of the “Exists” operator.

 

select name from staff 

where exists

(select name from staff where salary > 5000); The result will be:

 

 
| name |
| --- |
| Robert |
| Albert |
| Sally |
| Martha |
| John |
| Sandy |
| James |

 

If we change the query slightly and try the query below, we will get no responses.

 

select name from staff 

where exists

(select name from staff where salary > 8000);

 

An example of the use of the “ALL” operator:

 

select \* from staff

where 

location = all (select location from staff where salary = 3000);

 

 
| sid || name || job || salary || location |
| --- | --- | --- | --- | --- |
| 100 || Robert || Manager || 8000 || Atlanta |
| 101 || Albert || Administrator || 3000 || Atlanta |
| 102 || Sally || Secretary || 2000 || Atlanta |

 

The result will be the info for all the staff in the location of Atlanta.

 

An example of the use of the “ANY” operator:

 

select \* from staff

where 

location = any (select location from staff where salary = 3000);

 

 
| sid || name || job || salary || location |
| --- | --- | --- | --- | --- |
| 100 || Robert || Manager || 8000 || Atlanta |
| 101 || Albert || Administrator || 3000 || Atlanta |
| 102 || Sally || Secretary || 2000 || Atlanta |

 

When using any database, it is best to use small letters for field names and queries. 

 

Change the query as follows:

 

select \* from staff

where 

location = any (select location from staff where salary > 3000);

 

Each location with a salary greater than 3000 will be found. In this case all three cities have at least one person having a salary greater than 3000. Thus the first part of the query will print all the rows in the table. There will be seven rows.

 

The commands given thus far can work in the databases such as MySQL, Oracle and Microsoft’s Access.

 

If an editor is being used to develop PHP scripts on your computer before uploading to the website, then the first thing to do is to find if it comes with PHPMyadmin module or not.

 

The examples in this book were developed using the EasyPHP editor which is available at the following website- [http://www.easyphp.org](http://www.easyphp.org). The current version of PHP at the time of writing this book version 7 and its interface was shown in chapter 1. The interface below is for PHP version 5 series.

 

![](images/00049.jpeg)

 

Click on the MySQL Administration-PHPMyAdmin module or in version 7 start database first before clicking on PHPMyAdmin in the middle of the interface page.

 

A page that looks like this will appear.

 

![](images/00050.jpeg)

 

As can be seen the databases can be created using the new link on the left hand side above. C-Panel on all Unix/Linux based web hosting will give a similar screen also.

 

The menu on top of the above picture lets one list databases associated with their account or installation in addition to running SQL commands. Export and import allows for back up databases and input of bulk data.

 

Thus using a developer software such as EasyPHP one can mimic a real hosting environment. The most important part of this is to find the path of the database. This will be different slightly on the host and in the developer software. The database path method will be given in the host's technical faqs sheet. To create a table such as staff click on the structure tab and put in the name and number of columns as shown below.

 

![](images/00051.jpeg)

 

To complete the table creation, enter the data types and field lengths of each field of the staff table and select sid as the primary key. Primary key is a field whose value does not repeat and is required. The fields of the staff table introduced earlier are sid , name, job, salary and location. Out of these all are text except for salary which is a number.

 

The following shows the table field details.

 

![](images/00052.jpeg)

 

The table will be created after the save/go button is clicked. The result on the left hand side of the PHPMyAdmin screen will be similar to the one below.

 

![](images/00053.jpeg)

 

These steps are very similar to those done on actual web hosting but expect some minor differences in the way or look of the interfaces.

# Chapter 8. PHP for MySQL Database

 

In this chapter, the emphasis is to write a PHP code targeting a MySQL database and table. If this script is being run on an editor on a standalone computer or notebook, then the path to the database is the first thing to be found out. 

 

This information will be available in the FAQ’s part of the hosting service in case code is being written directly on the shared hosting location.

 

In the previous chapter, a staff table was shown. This table will be used in this chapter to demonstrate the select, insert, update and delete queries.

 

The first step in getting data from a table in the database or adding data to it is to connect to MySQL in the first place. Note: The examples that follow are for PHP version 5 series. For version 7 check end of chapter.

 

To this end the function mysql\_connect is used to connect to MySQL in PHP when the target database is MySQL. Anything that is opened has to be closed in programming so the mysql\_close() function plays this role.

 

 
| <html><body><?phpif($dx =mysql\_connect('localhost','root ',' ')){print"Connected to MySQL.";mysql\_close();} else {print"Could not connect to MySQL.";}?></body></html> |
| --- |

 

The connection mechanism is shown above in the PHP script. The line mysql\_connect('localhost',' root',' ')) will be slightly different on the webhost being used. The localhost is followed by a username and password. 

 

In the case of a developer software on a standalone machine the username is usually root but this needs to be verified in the help manual of PHP editor being used.

 

Now the second step after connecting to MySQL, is to connect to the selected database followed by the table to do some action. Let us start our example of the action by selecting the select or retrieval option.

 

 
| <html><body><?php$link\_id = mysql\_connect( 'localhost','root','') or die ("Could not connect: " . mysql\_error());mysql\_select\_db( "thottungal", $link\_id );$sql = "SELECT \* FROM staff";$result\_id = mysql\_query( $sql, $link\_id ) or die ( "Statement failed: " . mysql\_error() );$x=mysql\_num\_rows($result\_id);print "<b>Total number of entries retrieved: </b>$x";print "<table border=1 width=800>";while ( $row = mysql\_fetch\_array( $result\_id ) ) {print "<tr><td>".$row\['sid'\]."</td>"."<td>".$row\['name'\]."</td>"."<td>".$row\['job'\]."</td>"."<td>".$row\['salary'\]."</td>"."<td>".$row\['location'\]."</td></tr>";}mysql\_close( $link\_id );print "</table>";?></body></html> |
| --- |

 

We are using the staff table used in the previous chapter to retrieve all the rows in it. There are seven (7) rows in that table. The meaning of the lines of code above are as follows:

 

$link\_id = mysql\_connect( 'localhost','root','') or die ("Could not connect: " . mysql\_error());

 

Connect to My SQL. If not give an error and the program stops there.

 

mysql\_select\_db( "thottungal", $link\_id );

 

Having connected to MySQL look for the database.

 

$sql = "SELECT \* FROM staff";

Write the query that needs to be run in the database.

 

$result\_id = mysql\_query( $sql, $link\_id ) or die ( "Statement failed: " . mysql\_error() );

 

Run the query and save the result in a variable or give an error.

 

$x=mysql\_num\_rows($result\_id);

 

This line will give the number of rows of available for this query.

 

while ( $row = mysql\_fetch\_array( $result\_id ) ) {

print "<tr><td>".$row\['sid'\]."</td>"."<td>".$row\['name'\]."</td>"."<td>".$row\['job'\]."</td>"."<td>".$row\['salary'\]."</td>"."<td>".$row\['location'\]."</td></tr>";

}

 

The rows of the query will be printed through a loop. Here the while loop is used. Each column or field expected in the query is put within rows of a table. Here the quotations are very important. Usual errors are not enclosing the elements in the correct quotations.

 

mysql\_close( $link\_id );

# The database has to be closed and so is the table. The result of running this code is as follows:

 

![](images/00054.jpeg)

 

If all the fields are not needed, then just write the one that are to displayed and leave the rest alone.

 

If the query has a where condition - say for example to find all the employees and their information if their salary is greater than 3000 the code can be written as follows:

 

 
| <html><body><?php$link\_id = mysql\_connect( 'localhost','root','') or die ("Could not connect: " . mysql\_error());mysql\_select\_db( "thottungal", $link\_id );$sql = "SELECT \* FROM staff where salary >3000";$result\_id = mysql\_query( $sql, $link\_id ) or die ( "Statement failed: " . mysql\_error() );$x=mysql\_num\_rows($result\_id);print "<b>Total number of entries retrieved: </b>$x";print "<table border=1 width=800>";while ( $row = mysql\_fetch\_array( $result\_id ) ) {print "<tr><td>".$row\['sid'\]."</td>"."<td>".$row\['name'\]."</td>"."<td>".$row\['job'\]."</td>"."<td>".$row\['salary'\]."</td>"."<td>".$row\['location'\]."</td></tr>";}mysql\_close( $link\_id );print "</table>";?></body></html> |
| --- |

 

The result will be as follows:

 

![](images/00055.jpeg)

There is no change except in the $sql line.

 

Inserting data is an important part of a database table. If there is no data, then there is nothing to retrieve and the database will be practically useless.

 

To demonstrate the method to insert data into a table in MySQL using PHP let us create a PHP file as follows:

 

 
| <html><body><?phpif (isset($\_POST\['submit'\])){$link\_id = mysql\_connect( 'localhost','root','') or die ("Could not connect: " . mysql\_error());mysql\_select\_db( "thottungal", $link\_id );$sql = "insert into staff (sid,name,job,salary,location) values('{$\_POST\['sid'\]}','{$\_POST\['name'\]}','{$\_POST\['job'\]}','{$\_POST\['salary'\]}', '{$\_POST\['location'\]}')";mysql\_query( $sql, $link\_id ) or die ( "Statement failed: " . mysql\_error() );mysql\_close( $link\_id );}?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p>name:<input type=text= name="name" size ="50"><p>job:<input type=text= name="job" size ="30"><p>salary:<input type=text= name="salary" size ="10"><p>location:<input type=text= name="location" size ="30"><p><input type=submit name="submit" value="add to database"><p></form></body></html> |
| --- |

 

The PHP file has a form at the end of it that will allow one to enter values for each of the field in the table. The isset function is used to check if the submit button is hit and if so the values entered into the form will be inserted into the database. One can write a friendly message after the mysql\_query( $sql, $link\_id ) or die ( "Statement failed: " . mysql\_error() ); line.  

 

It is very important to watch out for quotation errors in the insert line. The result of entry of data can be observed by browsing the table using PHPMyadmin.

 

The following is an example of a PHPMyadmin browse search for the above code.

 

![](images/00056.jpeg)

 

To demonstrate the update method in PHP code for MySQL let us keep in mind that in the Staff table the sid is the prime key.

 

Thus the next code allows for all other fields to be updatable.  The code is as follows:

 

 
| <html><body><?phpif (isset($\_POST\['submit'\])){$link\_id = mysql\_connect( 'localhost','root','') or die ("Could not connect: " . mysql\_error());mysql\_select\_db( "thottungal", $link\_id );$sql = "update staff set name='{$\_POST\['name'\]}', job='{$\_POST\['job'\]}',salary='{$\_POST\['salary'\]}',location='{$\_POST\['location'\]}' where sid='{$\_POST\['sid'\]}'";$r =mysql\_query( $sql, $link\_id ) or die ( "Statement failed: " . mysql\_error() );if (mysql\_affected\_rows() ==1){print"Table is updated.";}mysql\_close( $link\_id ); }?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p>name:<input type=text= name="name" size ="50"><p>job:<input type=text= name="job" size ="30"><p>salary:<input type=text= name="salary" size ="10"><p>location:<input type=text= name="location" size ="30"><p><input type=submit name="submit" value="Update database"><p></form></body></html> |
| --- |

In the above code the form part is the same as in the case of the insert code. The change is in the query and the format used to set the update fields. The primary key is sid.

 

A new function mysql\_affected\_rows() is used here and this is used when update /delete is to be done in PHP. The result can be observed by browsing the table in PHPMyadmin as follows:

 

![](images/00057.jpeg)

# Last but not the least the code for deleting data from a database is as follows:

 

 
| <html><body><?phpif (isset($\_POST\['submit'\])){$link\_id = mysql\_connect( 'localhost','root','') or die ("Could not connect: " . mysql\_error());mysql\_select\_db( "thottungal", $link\_id );$sql = "delete from staff where sid='{$\_POST\['sid'\]}' limit 1";$r =mysql\_query( $sql, $link\_id ) or die ( "Statement failed: " . mysql\_error() );if (mysql\_affected\_rows() ==1){print"Row has been deleted.";}mysql\_close( $link\_id );}?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p><input type=submit name="submit" value="Update database"><p></form></body></html> |
| --- |

In the above code for deleting a row from the table the query ends with the words LIMIT 1. This makes sure only one row at most is removed.

 

Delete and update functions are to be used carefully in databases. Generally, this function is limited to certain roles. However, on internet websites users will need to update or delete their info.

 

The mysql\_affected\_rows() function is used with the delete code.  There is a lot of similarity between the code for update and delete.

 

The result of the deletion can be observed through PHPMyadmin as follows:

 

![](images/00058.jpeg)

 

# The row that was deleted in the above was the one that was entered in the insert code with sid=107.

 

The above code for delete can be modified to truncate the table leaving the structure but no data in the table. The code lines that will make this happen is as follows:

 

$link\_id = mysql\_connect( 'localhost','root','') or die ("Could not connect: " . mysql\_error());

mysql\_select\_db( "thottungal", $link\_id );

$sql = "truncate table staff";

 

One could modify the code lines above to drop the table also.

 

However, both truncate and drop are functions reserved for the administrator of the database and therefore in real situations unless specific permissions have been given the programmer might not be able to execute code to do these functions.

 

Version 7 PHP:

 

Version 7 of PHP is a major release in PHP and one of the areas that has been affected by new functions is in the way to deal with MySQL. The new functions are termed as mysqli where i stands for improvement. The good news is that for those who are familiar with the previous ways of connecting to MySQL, can easily migrate to the new functions because there is similarity in the way the connection will be made. 

 

mysqli\_connect() replaces mysql\_connect()

 

mysqli\_query() replaces mysql\_query()

 

mysqli\_fetch\_array() replaces mysql\_fetch\_array()

 

In short instead of mysql\_ the new functions start as mysqli\_. Let us look at an example of selecting data from the staff data using the new mysqli functions in PHP 7.

 

 
| <html><body><?php$link\_id = mysqli\_connect( 'localhost','root','','thottungal') or die ("Could not connect: " . mysqli\_connect\_error());$sql = "SELECT \* FROM staff";$result\_id = mysqli\_query( $link\_id, $sql ) or die ( "Statement failed: " . mysqli\_error($sql) );$x=mysqli\_num\_rows($result\_id);print "<b>Total number of entries retrieved: </b>$x";print "<table border=1 width=800>";while ( $row = mysqli\_fetch\_array( $result\_id ) ) {print "<tr><td>".$row\['sid'\]."</td>"."<td>".$row\['name'\]."</td>"."<td>".$row\['job'\]."</td>"."<td>".$row\['salary'\]."</td>"."<td>".$row\['location'\]."</td></tr>";}mysqli\_free\_result($result\_id);mysqli\_close( $link\_id );print "</table>";?></body></html> |
| --- |

 

The flow of logic is the same as in the previous version 5. $link\_id makes connection to the database. The difference here is that there are four elements to be entered within mysqli\_connect brackets. The last one is the name of the database. The remaining entries holds true for local install for development purposes and will be slightly different on the hosting site. This values need to be obtained from the technical support of shared hosting site if that is where the website is located.

 

After giving the query to $sql the number of rows obtained from the array created by mysqli\_fetch\_array is printed. The array is then printed out as shown in the code above. The program is closed by freeing the query from memory and then closing the connection. The function mysqli\_fetch\_array can handle arrays with string or number keywords.

 

Thus the version in PHP 5 and 7 are very much similar except in the areas mentioned in the two paragraphs above. Now let us try to insert a row into the database. The same code from version 5 will be modified below to fit version 7.

 

 
| <html><body><?phpif (isset($\_POST\['submit'\])){$link\_id = mysqli\_connect( 'localhost','root','','thottungal') or die ("Could not connect: " . mysqli\_connect\_error());$sql = "insert into staff (sid,name,job,salary,location) values('{$\_POST\['sid'\]}','{$\_POST\['name'\]}','{$\_POST\['job'\]}','{$\_POST\['salary'\]}', '{$\_POST\['location'\]}')";mysqli\_query($link\_id, $sql) or die ( "Statement failed: " . mysqli\_error($sql) );mysqli\_close( $link\_id );}?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p>name:<input type=text= name="name" size ="50"><p>job:<input type=text= name="job" size ="30"><p>salary:<input type=text= name="salary" size ="10"><p>location:<input type=text= name="location" size ="30"><p><input type=submit name="submit" value="add to database"><p></form></body></html> |
| --- |

Like in the previous version we connect to the database and execute the query and close the link. The single PHP file has a form to display and using isset() function after verifying the hitting of the submit button the insertion will take place. Let us look at the code for update.

 

 
| <html><body><?phpif (isset($\_POST\['submit'\])){$link\_id = mysqli\_connect( 'localhost','root','','thottungal') or die ("Could not connect: " . mysql\_error());$sql = "update staff set name='{$\_POST\['name'\]}', job='{$\_POST\['job'\]}',salary='{$\_POST\['salary'\]}',location='{$\_POST\['location'\]}' where sid='{$\_POST\['sid'\]}'";$r =mysqli\_query( $link\_id, $sql ) or die ( "Statement failed: " . mysqli\_error($sql) );if ($r){print"Table is updated.";}mysqli\_close( $link\_id );}?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p>name:<input type=text= name="name" size ="50"><p>job:<input type=text= name="job" size ="30"><p>salary:<input type=text= name="salary" size ="10"><p>location:<input type=text= name="location" size ="30"><p><input type=submit name="submit" value="Update database"><p></form></body></html> |
| --- |

 

The difference here compared to the same code when used with PHP version 5 is that the mysql\_affected\_rows has been replaced by an if statement in addition to using an i after the mysql\_functions.

 

To delete a row, replace the query in $sql by "delete from staff where sid='{$\_POST\['sid'\]}' limit 1" and remove the input text boxes for everything except the sid which is the primary key. 

 

The message under the if condition should be if ($r) {  print"Row deleted"}

# Chapter 9. PHP for an Oracle Database

 

# In the previous chapter the database discussed was MySQL. In this chapter let us take a look at the Oracle database with respect to PHP.  The Oracle database being discussed here is the express version 11.2. Appendix II shows how to install it if it is not on the client or standalone machine being used.

 

To use PHP with Oracle some configuration changes will be needed with the PHP installation. The code for this book was developed using the WAMP editor EasyPHP and this has several versions. It is not required to have the latest but the minimum version of this editor that will run the code in this book is that runs PHP 5 and above. The configuration change required to connect to Oracle using editor or a similar one is shown in Appendix III and IV.

 

It is very important to write down the default values of the Oracle installation. In the example(s) of this chapter the database installed by default is called orcl. The hr user and tables associated with that user is going to be used. 

Let us create a table called employee in the oracle database under the hr user with password hr. To do this use the SQL plus interface from the apps menu in windows under Oracle. The interface will look like this. If the hr account is locked , login as the sysdba and use the following - alter user hr account unlock; and then connect to hr.

![](images/00059.jpeg)

To create the employee table, use the following command:

create table employee (sid varchar2(10), name varchar2(50), manager varchar2(10) constraint sid\_pk primary key = (sid)); 

This will create the employee table with sid as the primary key. For the purpose of this book this simple table will be sufficient. My book on SQL might be helpful if SQL associated with Oracle is new to you.

If the changes to PHP.ini (configuration file) as discussed in Appendix III and IV has been done and saved, then it is time to get to the PHP connecters for Oracle. PHP program is being connected to the Oracle database using the PHP OCI8 extension. 

This extension at the time of writing this book can be used to Oracle 12,11, 10 and 9 databases. PHP by itself is independent of the Oracle database.

To connect to the database the OCI8 PHP class library provides the following functions oci\_connect(), oci\_pconnect() and oci\_new\_connect(). If a non persistent connection is required then use oci\_connect(). This is also cached. This improves efficiency of connection.

The cache used by oci\_connect is removed after the script has been run or when the connection resource has been closed.

The oci\_new\_connect is not cached while the oci\_pconnect() is cached and can be used across requests. An oci\_close() function is required with any of the three functions mentioned thus far.

After creating the employee table above using the create statement. The values have to be inserted.

The easiest way is using the insert statement as follows:

insert into employee values('101','Albert','103');

and similarly the other three rows of data as shown in the picture in the previous page.

After Oracle has been installed find the tnsnames.ora file which is usually in the network/admin/ folder. This file will give the sid value of the database. The default is orcl as mentioned earlier in this chapter. The usual port is 1521 and host will be local The host if it is the installation of Oracle 11.2 express on a standalone computer or notebook. 

The oci\_connect() function has three parts- username, password and connection\_string.

The username since we are connecting to a table under hr user is hr and password is hr and connection string is orcl- the sid name or name of database.

Make sure the sid name is exactly like it is stated in the tnsmames.ora file.

The oci\_parse () is used to parse a query.

The oci\_execute() is used to execute a statement.

oci\_fetch\_array() is used to fetch the next row from a query in array format. 

Lastly oci\_close() will close the connection to the database.

It might be noticed all these steps are similar to the way PHP connects to MySQL database. Now let us look at the following code.

 

 
| <?php$db = oci\_connect('hr', 'hr', 'orcl');if (!$db) {trigger\_error('Unable to connect to database', e\_user\_error);}$sql = 'select \* from employee';$stmt = oci\_parse($db, $sql);oci\_execute($stmt);$count = 0;print"<table border=1>";while (($row = oci\_fetch\_array($stmt,OCI\_BOTH)) != false) {print "<tr><td>".$row\['0'\]."</td>"."<td>".$row\['1'\]."</td>"."<td>".$row\['2'\]."</td></tr>";$count++;}print"</table>";print $count . ' record(s) found.';oci\_free\_statement($stmt); |
| --- |

 

 

 
| oci\_close($db);?></body></html> |
| --- |

 

The output will be as follows:

 

![](images/00060.jpeg)

The oci\_free statement () function is used mainly with the select query as a large amount of data will be involved and it is best to clear the memory after the execution of such a query.

In the above code, the oci\_fetch\_array has two parameters- the statement being parsed and the type of array keys. OCI\_BOTH stands for both string and numerical keys for an array. If the key is a string, then OCI\_ASSOC can be used instead. The row\[0\] indicates the first column of the oracle table in the array.  

If the column heading of each oracle table needs to be used, then keep in mind that names can be case sensitive. The default is that the column headings are in capital letters. Thus the above code can be modified as follows if column headings instead of numbers are required as array keys.

 
| while (($row = oci\_fetch\_array($stmt,OCI\_BOTH)) != false) {print '<tr><td>'.$row\["SID"\].'</td>'.'<td>'.$row\["NAME"\].'</td>'.'<td>'.$row\["MANAGER"\].'</td></tr>'; |
| --- |

 

The rest of the code is the same. There is a term called htmlentities in PHP. Its purpose is to convert all applicable characters into HTML entities. Its takes two parameters.  One of them is the string or input and the other parameter has to be selected from the ones below:

ENT\_COMPAT - to convert double quotes and leave single quotes alone.

ENT\_QOUTES - to convert both double and single quotes.

ENT\_NOQOUTES - to convert both double and single quotes unconverted.

ENT\_IGNORE - to discard invalid code unit sequences instead of returning an empty string. This should be used carefully due to security issues.

ENT\_SUBSTITUTE - to replace invalid code unit sequences with a unicode replacement character U + FFFD (UTF-8) or &#FFFD instead of returning an empty string.

ENT\_DISALLOWED - to replace invalid code points for the given document type with a replacement character U + FFFD (UTF-8) or &#FFFD instead of leaving them as is. Usefull in XML documents with embedded external contents.

Let us modify the above code to use html entities to print out the result of the employee table.

 
| <?php$db = oci\_connect('hr', 'hr', 'orcl');if (!$db) {trigger\_error('Unable to connect to database', e\_user\_error);}$sql = 'select \* from employee';$stmt = oci\_parse($db, $sql);oci\_execute($stmt);$count = 0;print"<table border=1>";while (($row = oci\_fetch\_array($stmt,OCI\_ASSOC+OCI\_RETURN\_NULLS)) != false) {echo "<tr>";foreach ($row as $item) { |
| --- |

 

 
| echo "<td>" . ($item !== null ? htmlentities($item, ENT\_QUOTES) : "&nbsp;") . "</td>\\n";    }print "</tr>";$count++;}print"</table>";print $count . ' record(s) found.';oci\_free\_statement($stmt);oci\_close($db);?></body></html> |
| --- |

 

The output will be the same as the previous code.  The difference here is there is no need to mention the key values either in numeric or non numeric manner.

 

Let us now look at a code to insert data into the Oracle database.

 

 
| <?php$db = oci\_connect('hr', 'hr', 'orcl');if (!$db) {trigger\_error('Unable to connect to database', e\_user\_error);}$sql = "insert into employee (sid,name,manager) values ('104','Adam','102')";$stmt = oci\_parse($db, $sql);oci\_execute($stmt, OCI\_NO\_AUTO\_COMMIT);oci\_commit($db);oci\_close($db);?></body></html> |
| --- |

 

The execute statement is followed by a commit to confirm the insertion into the database table.

The oci\_execute() function takes two parameters. The first is the parse statement as seen above and the second one is a method. The following are the methods available in oci\_execute():

OCI\_COMMIT\_ON\_SUCCESS - this will automatically commit all outstanding changes for this connection when the statement has succeeded. This is the default.

OCI\_DEFAULT - this is an old method which might be available in the version of OCI8 being used but usage of this is not advised since version 5.3.2 of PHP.

OCI\_NO\_AUTO\_COMMIT - like the one used in the example above does not commit changes. Thus if commit is needed then oci\_commit() has to be used similar to the example above. If this is not used any changes requested by the execute statement will be roll backed after the program is exited.

The insert done in the above example could be done by another method. This method involves using the OCI8 function called oci\_bind\_by\_name().

The oci\_bind\_by\_name() binds a PHP variable to an Oracle place holder. This binding improves database performance and is also a way to avoid SQL injection security issues. SQL injection is a type of computer attack in which malicious code is embedded in a poorly-designed application and then passed to the backend database. Bind variables are not treated as part of the SQL statement and hence it decreases the SQL injection issues. The code is as follows:

 

 
| ?php$db = oci\_connect('hr', 'hr', 'orcl');if (!$db) {trigger\_error('Unable to connect to database', e\_user\_error);}$sql = "insert into employee (sid,name,manager) values (:sid\_bv,:name\_bv,:manager\_bv)";$stmt = oci\_parse($db, $sql);$sid='104';$name ='Adam';$manager ='102';oci\_bind\_by\_name($stmt, ":sid\_bv", $sid);oci\_bind\_by\_name($stmt, ":name\_bv", $name);oci\_bind\_by\_name($stmt, ":manager\_bv",$manager);oci\_execute($stmt,OCI\_NO\_AUTO\_COMMIT); |
| --- |

 

 
| oci\_commit($db);oci\_close($db);?></body></html> |
| --- |

 

The code above creates three bind variables denoted by the \_bv ending and values to the insert statement is send via reference in the bind statement associated with $sql.

 

The code for updating a row in an oracle database table is as follows:

 

 
| <?php$db = oci\_connect('hr', 'hr', 'orcl');if (!$db) {trigger\_error('Unable to connect to database', e\_user\_error);}$sql = "update employee set manager='102' where sid='103'";$stmt = oci\_parse($db, $sql);oci\_execute($stmt, OCI\_NO\_AUTO\_COMMIT);oci\_commit($db);oci\_close($db);?> |
| --- |

 

The code for deleting rows or dropping a table can be obtained from the above provided permission to do these are given by the administrator.

 
| <?php$db = oci\_connect('hr', 'hr', 'orcl');if (!$db) {trigger\_error('Unable to connect to database', e\_user\_error);}$sql = "delete employee where sid='103'";$stmt = oci\_parse($db, $sql);oci\_execute($stmt, OCI\_NO\_AUTO\_COMMIT);oci\_commit($db);oci\_close($db);?> |
| --- |

 

# Chapter 10. Regular Expressions

 

Regular expressions are found in all programming languages to take into consideration the format of some inputs. For example, the postal code or zip code in many countries are not in the same format as in the United States.

 

PHP supports two types of regular expressions - POSIX extended and PCRE which is Pearl compatible. Note: The information below is applicable PHP version 5 only. Even in version 5 some versions will not accept the functions below. Functions in PHP 7 are shown at the end of this chapter.

 

POSIX has six functions in PHP and they are:

 

ereg() - Match a pattern and is case sensisitive.

 

eregi() - Match a pattern and is not case sensitive.

 

ereg\_replace() - Matches and replaces a pattern and is case sensitive.

 

eregi\_replace() - Matches and replaces a pattern and is not case sensitive.

 

split() - Splits a string using a pattern and is case sensitive.

 

spliti() - Splits a string using a pattern and is not case sensitive.

 

Metacharacters help to create patterns to test the input string against.

 

.    is a period meaning any single character?

 

^   is a caret which means beginning of a string.

 

$   means end of a string.

 

|   means alternatives (or).

 

() means group.

 

Quantifiers:

 

?  - zero or one occurences.

 

\* - zero or more occurences.

\+ - One or more occurences.

 

{x} - Exactly x occurences.

 

{x , y} - Between x and y occurences (both are inclusive)

 

{x, } - At least  x occurences.

 

Character classes:

 

\[a-z\] - any lowercase letter.

 

\[a-z A-Z\] - any letter.

 

\[0-9\] - any number.

 

\[\\f\\r\\t\\n\\v\] - any white space.

 

\[aeiou\] - any vowel.

 

\[\[:alnum:\]\] - any letter or number.

 

\[\[:alpha:\]\] - any letter (same as \[a-zA-Z\])

 

\[\[:blank:\]\] - any tabs or spaces.

 

\[\[:digit:\]\] - any number.

 

\[\[:lower:\]\] - any lowercase letter.

 

\[\[:upper:\]\] - any uppercase letter.

 

\[\[:punct:\]\] - any punctuation character.

 

\[\[:space:\]\] - any white space.

 

A literal is a value that is written exactly as it is interpreted. For example, the letter "b" matches the letter b.

 

Now let us write a program that will match the input against a five-digit postal code. The postal code consists of only numbers.

 

 
| <html><body><?phpif (isset($\_POST\['submit'\])){$pattern = $\_POST\['pattern'\];print $pattern;$zipcode = $\_POST\['zipcode'\];print $zipcode;if (eregi($pattern,$zipcode)){print"The zipcode is a five-digit number";} else { print"The zipcode is not a five-digit number";}}?><form action="expression.php" method="post">pattern:<input type=text= name="pattern" size ="20"><p>zipcode:<input type=text= name="zipcode" size ="20"><p><input type=submit name="submit" value="Check zipcode"><p></form></body></html>  |
| --- |

 

Now if the pattern is entered as ^(\[0-9\]{5}) which stands for the five digit zip code then enter a number it will be give a positive answer if the numbers match or if it does not then a negative number will be given.

 

Modify the code and see if the pattern is ^ http://www. and enter an URL to compare the pattern against. Note that the error messages and input boxes will have to modified to pass on the correct information.

 

PHP 7:

 

In the new version of PHP 

 

eregi() and ereg() function (s) replaced by preg\_match(). 

 

ereg\_replace() replaced by preg\_replace() 

 

split() replaced by preg\_split()

 

Let us look at some examples.

 

 
| <?php// The "i" after the pattern delimiter indicates a case-insensitive searchif (preg\_match("/php is easy./i", "PHP is easy.")) {    echo "A match was found.";} else {    echo "A match was not found.";}?> |
| --- |

 

 
| <?php/\* The \\b in the pattern indicates a word boundary, so only the distinct \* word "fun" is matched, and not a word partial like "have". \*/if (preg\_match("/\\bhave\\b/i", "We are having fun with PHP.")) {    echo "A match was found.";} else {    echo "A match was not found.";} |
| --- |

 

 
| <?php// get host name from URLpreg\_match('@^(?:http://)?(\[^/\]+)@i',    "http://www.xyz.com/index.html", $matches);$host = $matches\[1\];print $host;?> |
| --- |

 

This will print www.xyz.com.

# Appendix I. Workshop

 

The end of any book in programming is only as good as the understanding derived from it. The following questions are examples of knowledge that should have been obtained from this book or from similar ones.

 

1.  Name any two functions to print a message in PHP?

 

Answer: echo(), print();

 

2\. How can an external file be included in a PHP program?

 

Answer: The function include() or require() can be used to include an external file. The difference is in the way include() function can give error messages while continuing to run the code but require() will terminate the program upon encountering any errors.

 

3\. What is the difference between GET and POST methods of transferring data?

 

Answer: GET is used to transfer small amounts of data and this data will be visible during transfer. POST does not display the values being send to the PHP program.

 

4\. How are arrays declared in PHP?

 

Answer: $fruit = array('apple', 'grape', 'lemon');

 

5\. Which function will give the number of elements of an array?

 

Answer: count(). As in count($array);

 

6\. What is the difference between a session and a cookie?

 

Answer: Sessions are stored in the server and cookies are stored in the client machines. Cookies have expiration time. Sessions are closed when the browser is closed. Users do not have access to data stored in the session.

 

7\. How are cookies created and read?

 

Answer: A cookie is created by using the setcookie() function and retrieved using the $\_COOKIE\[‘cookie name’\] function. Within the setcookie() function the name of the cookie, value and duration should be included.

 

8\. Name different ways to write a loop in PHP.

 

Answer: While, For and do..while.

 

9\. What is the first step in trying to connect to MySQL database using PHP?

 

Answer: Connection to MySQL. Then the database.

 

10\. What is the function of explode()?

 

Answer: Explode splits a string into an array by string.

 

11\. What is the role of trim()?

 

Answer: Removes whitespaces from both ends of a string.

 

12\. How can a user be redirected to another webpage?

 

Answer: Use the header function.

 

13\. How to find the length of a string?

 

Answer: Use the strlen() function.

 

14\. An array with a string key is called \_\_\_\_\_\_\_\_\_\_\_.

 

Answer: Associative array.

 

15\. Which function can be used to check if a form has been submitted in a PHP program?

 

Answer: isset() used with an if statement.

 

16\. How to send mail in PHP?

 

Answer: Use the mail() function - mail($to,$subject,$message,$headers);

 

17\. Name any one encryption function that can be used in PHP.

 

Answer: MD5.

 

18\. What is meant by the term pear?

 

Answer: PEAR is a framework and distribution system for reusable PHP components.The project seeks to provide a structured library of code, maintain a system for distributing code and for managing code packages, and promote a standard coding style.PEAR is broken into three classes: PEAR Core Components, PEAR Packages, and PECL Packages.

 

19\. What is the difference between PHP and Javascript?

 

Answer: PHP is server based while Javascript is client based. 

 

20\. Which extension needs to be activated to use PHP with Oracle?

 

Answer: oci8 extension in the PHP configuration file needs to be uncommented.

 

# Practical Workshop

#  

# 1\. Create a table named staff under the user HR in an Oracle database. It should have six columns - id, name, job, manager, salary and location. All the variables are text or varchar2 except for salary which is a number. The primary key is id. 

#  

# Using PHP insert any six rows of values to this table.

#  

# 2\. Using PHP display all rows whose salary is greater than 1000.

#  

# 3. Write a program that will read an array of numbers and puts them in an ascending order.

#  

# 4\. Develop a PHP page that will save the page preferences of the user and allow him to use the page for about fifteen minutes.

 

5\. Develop a PHP webpage that allows one to enter a postal code, telephone number and country code in three letters based on the American, Canadian, European and any Asian format. The program must be able to give appropriate messages to guide the user.

  

Appendix II.  Installing Oracle Database

 

Check all your applications and see if Oracle is installed. On a windows machine we look as usual from the start button onto the applications or programs. Expand any oracle installation and find the SQL plus option. 

 

If Oracle is not one of your applications, then go to www.oracle.com and download section and based on your Windows or Linux details download the appropriate version for your computer. At the time of writing this book the only express version was 11G version 2. 

 

If one has any older version such Oracle 10 Express or Oracle 9i the codes in this book will also work. Installing the newer version is not required for the content of this book.

 

Please note that internet connection will be required to complete the registration and installation of the Oracle download. 

 

After installation and registration, the internet connection will not be required for operating the database. At the time of writing this book the oracle website looked like this.

 

![oracle.jpg](images/00061.jpeg)

 

Follow the downloads to database and then to oracle database. The following screen will come up.

 

![oracle2.jpg](images/00062.jpeg)

 

Notice that there are two versions for windows. Choose the one that is relevant to your machine. Make sure both files are downloaded.

 

Click on see all for more details. Oracle requires down loaders of their products to register. This is a free profile registration.

 

The next screen if one clicks see all will look like this. One needs to accept the license before downloading the appropriate software. Once the files are downloaded make sure there is internet connection on the computer before preparing to install the software.

 

![oracle3.jpg](images/00063.jpeg)

 

Installation of the windows based express edition of Oracle release 11.2 looks similar to the following screen shots. Make sure to write down the details of each screen.

 

![inst.jpg](images/00064.jpeg)

 

 

![inst2.jpg](images/00065.jpeg)

 

![inst3.jpg](images/00066.jpeg)

 

![inst4.jpg](images/00067.jpeg)

 

![inst5.jpg](images/00068.jpeg)

 

Make sure to note down the password and name of database created. This should be kept somewhere safe.

 

![inst6.jpg](images/00069.jpeg)

 

![inst7.jpg](images/00070.jpeg)

# Appendix III.  PHP with Oracle

 

To make changes to the EasyPHP WAMP click on the E icon on the desktop and choose configuration and PHP. This is for version 12 -14 using PHP 5 to 5.6.

 

![](images/00071.jpeg)

 

 

This will open the PHP configuartion file. Go to the line 

 

![](images/00072.jpeg)

 

which says extension=php\_oci8\_11g.dll and uncomment it. That is remove the ";" in front of it. Note the previous line should be left as is. This is because we are activating the extension of oci8 for 11g express version. Save the file with file save and then restart the machine or EasyPHP editor and that is it. If PHP has been installed separately then the PHP.ini configuration file and to the same above after a backup of any original file is made. 

 

Confirm with any administrator if the computer is not a standalone before making changes to any configuration files. Check Appendix IV for PHP 7.

  

Appendix IV.  Easy PHP interface

 

In this section we look at the different features or interfaces of the editor used to write programs in this book. The editor is Easy PHP and it can be downloaded from http://www.easyphp.org.

 

![](images/00073.jpeg)

 

The interface can be obtained after installing the latest version of EasyPHP editor. Upto version 17 there is no need for an internet connection to complete the installation. Once the icon shortcut appears on the desktop right click and choose open. As the "E" icon appears on the navigation bar at the bottom of the screen right click and choose open dashboard. This will lead to the interface above.

 

To start using the editor click on start HTTP server and if database is required then click on start Database Server. Note that the default version of PHP in version 17 is 5.6 and so if that is not what is needed choose change settings under the HTTP server. This is the third button after the red one. Choose version 7 and click ok. 

 

The portable directory is where the scripts are and it is from here the PHP scripts have to be run. The files are located in the eds-www directory under c drive or the drive chosen under EasyPHP. Use a notepad to write the PHP programs and keep it in this directory. It will appear under portable directory.

 

The MySQL administration allows one to bring up the PHPMyadmin to create databases and or tables. The entire administration of the MySQL database is done from here.

 

There is no direct access to other databases such as Oracle from this interface. Perhaps in later versions of the editor there might be. To activate the OCI8 feature for connection to Oracle it is important to find the PHP.ini file. There will two of them in this version of the editor as there are two versions of PHP associated with it. Find the PHP.ini file for the version you want and to do this go the installation folder of EasyPHP. On the computer used for this book it was located at: 

 

C:\\Program Files (x86)\\EasyPHP-Devserver-17\\eds-binaries\\php

 

for the version 7 and version 5. Choose the folder for the version of PHP you want and then find the PHP.ini file and uncomment (remove ;) the line dealing with OCI8 dll. If there are two lines, then uncomment the one associated with Oracle express version if that is the version of the database installed on the computer being used.

 

The default version of the PHP on this editor (version 7) is PHP 5.6. There is an online quick editor that can be used to paste code and test.

 

![](images/00074.jpeg)

 

This is pretty hand for those who are new to PHP or for those who do not like to create files in notepad etc.

 

Just keep in mind so far this online editor is for version 5.6 and one can be sure in newer versions of this editor in the future one cans see more up to date online editors.

# Appendix V.  References

 

I compiled this book for a laboratory class associated with an undergraduate course in web development. 

 

The following sources were referenced:

 

Programming PHP, 3rd Edition, Creating Dynamic Web Pages ,By [Rasmus Lerdorf](http://www.oreillynet.com/pub/au/85), [Kevin Tatroe](http://www.oreillynet.com/pub/au/810), [Peter MacIntyre](http://www.oreillynet.com/pub/au/2342), [O'Reilly Media](https://www.safaribooksonline.com/library/publisher/oreilly-media-inc/?utm_medium=referral&utm_campaign=publisher&utm_source=oreilly&utm_content=catalog&utm_content=catalog),February 2013.

 

Beginning PHP and MySQL, From Novice to Professional, Gilmore, W Jason, Apress, 2010

 

Oracle with PHP: php.net/manual/en/function.oci-connect.php

 

 

About the Author: 

 

The author is Oracle Certified and has been an IT and Management Consultant for the last seventeen years in public and private sectors. The author by education is an electrical and computer engineer with a masters degree in Engineering Systems and Management. 

 

The webpage for this and other books by the author is: http://beam.to/fjtbooks