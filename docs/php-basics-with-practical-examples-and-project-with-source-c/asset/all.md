![](image_rsrcDS.jpg)

   

Practical Hand On Experience With Php & Mysql  
Hi Friends! This book is all about PHP and Mysql.It covers almost all the core topics in PHP.Each and every topic is explained with practical examples so that you can clearly understand the topic and you can practice the same on your own.  
The last chapter in this book covers a small project with full source code. It covers the main topics and give you an understanding of how to build a dynamic website from scratch using PHP and Mysql. © 2021 by Dipti Sahay All Rights Reserved http://readerscollection.in Content : 1.Introduction to PHP  
2.Type of applications that can be developed using Php. 3.How to install PHP locally  
4.Run your first program with Php  
5.Variable and Constants explained with examples  
6.Php datatypes  
7.Php operators. 8.Php operators usage explained with examples  
9.Php Strings and Arrays with examples 10.If and Else block and it's use with practical example  
11.Different types of loops in PHP.  
12.Php superglobals  
13.Create Php Forms  
14.Php Form Validation:Server side Validation 15.Introduction to Mysql  
16.How to connect to your database from your application 17.How to create database and tables  
18.Session management in php 19.A practical project where you will get to know how to create  
i)Database and table creation iii)A frontend where user can register and login and access the restricted page in the website  
CHAPTER 1: Introduction To Php:: Php is a server side scripting language and is generally used to develop dynamic  webpages. It is an opensource scripting language.It is free,widely used and easily available for  
download. It is the best ever tool for developing webapplications or dynamic websites.  
PHP was originally created by Rasmus lerdorf in 1994.  
Previously PHP stood for personal Home page but now PHP stands for PHP:Hypertext Preprocessor. Php scipts are executed on server.It is compatible with all servers like Apache,IIS,etc. A Php file contains HTML  
code,CSS code and Php  
script.The file is saved with .php extension.It is executed on server and the response generated is pure HTML which is displayed in the browser.  
So before we start learning Php we must know what Php can do . Php can be used to create  
dynamic page content.  
It can be used to create forms and collect data from end users. It can create session and can maintain session for any user while he is navigating through multiple pages in any website. Php can be used to manipulate data in database by performing crud operations like  
create,read,update and delete operations.  
Php can be used to create sessions and track user activity. To learn or work with Php you should have basic knowledge on HTML,CSS and javascript. HTML is hypertext markup language and CSS is cascading style sheet.HTML describes structure of webpage.HTML contains number of elements. These elements hold text and images for the webpage.It actually tells the browser how to display the data for a webpage. CSS is used to give a styling to those elements i.e the look and the feel of the webpage.  
HTML and CSS topics are not covered here however while using HTML tags and CSS code in this book I will briefly describe what is the main purpose of using them. CHAPTER 2  
Types of Application developed using Php:: Php can used to develop any dynamic webpage.Well what do we mean by dynamic  website? Dynamic website means that the content of the website is not static i.e html pages are not storing content for the website.Data or content is coming from database and it is changing with user action.  
So now what type of applications and websites we can develop using php.  
We can develop informative websites,blogs,B2B applications, B2C applications,ecommerce applications,forums,erp and many more. CHAPTER 3  
How to install Php locally:: Installing Php locally means installing it in your local PC.This is important step while learning Php so that you can run and test your php code locally on your PC. We are going to install xampp server (which contains  
Apache,Mysql and Php).Apache is a webserver which is required to run php scripts.  
Follow the below steps to install xampp in your PC. Step 1:Go to  
https://www.apachefriends.org/do wnload.html  
Download the latest xampp for your windows. Step 2:Save and Run the .exe file Step 3:A setup wizard dialog will get open on your screen for you.Follow the instructions and install your xampp in desired folder.  
Your installation part is now done! CHAPTER 4  
Run your first program with Php:: If you have done the xampp installation in C folder.Then navigate to C folder and manually start the server by clicking on xampp\_start icon which is  
already there inside xampp folder.See the screenshot below: ![](image_rsrcDT.jpg)To write the php scripts we need an editor.A number of free editor tools like Notepad editor ++, Sublime,Netbeans are available . You can use any of them.  
I will be using Netbeans for writing the php scripts.  
Navigate manually to C:\\xampp\\htdocs folder. This is a folder where you can store your project folder and files within it. I am creating a folder here and naming it as Practicalphp.I will be using this folder to store all the php scripts required for practical examples and test them as we proceed gradually. Php code starts with open tag and ends with close tags.Well what are open and close tags in php? <?php is the open tag and ?> is the close tag.Php script goes between these two tags.You can find the code below: <?php  
//php code goes here ?> Below we are going to print text on webpage with php.For this create a file in  
C:\\xampp\\htdocs\\PracticalPhp folder and save it as index.php. Paste the below code to display “Hello ! I am here” on a page. <!DOCTYPE html>  
<html lang="en">  
<head> <meta charset="utf-8">  
<title>MyFirstExample</title> </head>  
<body>  
<?php echo "Hello ! I am here" ;?>  
</body> </html> Now if you have already started your xampp server in your PC then open any browser and type localhost/PracticalPhp/ and click enter.You will see “Hello ! I am here “ on your screen.See the screenshot below: ![](image_rsrcDU.jpg)Illustration 1: Example To Print Hello !I am here A normal php file contains some HTML code and some Php scripting code and the file is saved with .php extension. The php code is written within php open tag and php close tags.Each statement of Php code ends with semicolon. Here in the above code “  
MyFirstExample” text is used as title within the HTML title tag which will get displayed on the top of the page.In Php there is a built-in function “echo” which can be used to output the text “Hello ! I am here”on a web page. CHAPTER 5  
Variable declaration and it's usage with examples:: A variable is a container which store values in it.It can store a string of text,numbers etc.We donot have to declare the  
datatype(ie String,Integer) of the variable.  
It automatically converts the variable to it's correct data type depending on it's value. The assignment operator is used to assign value to a variable.Once a variable is declared it can be used throughout the code. Php variables follow some naming conventions i.e follow some rules for defining a  
variable.A php variable starts with dollar sign $ ,followed with a name.A variable name cannot start with number.It can have alphanumeric characters and as well as underscore.A varaiable name cannot have spaces.They are case sensitive. Find below examples to define a variable: $var=”This is a string variable”; Since the above $var variable stores text.It is a variable with datatype as String . $var=10;  
Since the above $var variable stores number.It is a variable with Integer data type. $var=array(“a”,”b”,”c”); Since the $var stores array data so it is an array variable. $var=2.5;  
Since the $var variable stores a floating point number so it's a float variable. Php Constants:: An identifier which holds a value and that value remain the same throughout the script.The value cannot be changed throughout he script.It starts with a letter or underscore.It is global throughout the script.  
To create a constant in your script you can use define() function. <?php  
define(“STORE”,”Estore Diversity”); echo STORE;  
?>  
In the above example I have define a constant named  
STORE.It holds the value Estore Diversity.  
Now whenever I will use and print the STORE constant in my script it will display the value as Estore Diversity.  
So the main purpose to define constant is that when we want to define some identifiers that will hold some value that are not going to change throughout the code and are available globally to the script. CHAPTER 6  
Php Datatypes:: Datatype tells the type of data.A value which is stored in a variable can be of any  
datatype.There are number of datatypes: • String  
• Integer  
• Boolean  
• Array  
• Object  
• NULL  
• Float Any sequence of characters included between single or double quote is a String.For eaxmple:  
<?php $var=”Hello World”; echo $var;  
?> The above $var is a string variable as it holds sequence of characters between double quotes. A variable holding digits which is a non-decimal number is an Integer.Integer can be positive or negative but it should be whole numbers.  
For example: <?php  
$a= 10; echo $a; ?> In the above example variable $a holds a number 10 which donot have any decimal  point and thus it is an Integer. A variable which holds boolean value ie true or false is a boolean variable.  
Boolean values are used in conditional blocks. For example if some variable value is equal to true or false then the following condition will be executed.If and Else condtion have been explained in next section. A floating point number is a number which has decimal point. For example:  
<?php  
$b=2.45;  
?> Arrays are the datatype which stores multiple values of same type in one variable. We can define array by using array() function.This has been explained in  
detail in Array section. Objects are the datatype which stores data and also the  
information on how to process the data.An object must be explicitly declared. First we define a class  
with Class keyword.  
It holds some properties and  
methods.Then we create an instance ie the object of the class to use the methods and  
properties.  
<?php class A{  
public $var=”hello”;  
public function demo() {  
echo $this->var;  
}  
} $object= new A();  
echo $object->demo(); ?>  
Here we have declared a class A .It holds $var property and a method demo. Property is the variable and method is the function in the class. ![](image_rsrcDV.jpg)Illustration 2: Class Datatype demo() method is accessing the variable $var and value “hello” will get printed.  
$object is the object created for class A.Check the output of the code below: NULL is a special data type which holds no value.It has only NULL as value.  
A variable can be set with NULL value. <?php  
$x=NULL;  
var\_dump($x); ?>  
![](image_rsrcDW.jpg)Illustration 3: NULL Datatype  
CHAPTER 7  
 PHP Operators:: Operators are used to perform different operations on variable and values.  
Suppose we want two variables and we want to know the  
summation of that.Then we will perform and addition of that two variables using Arithmetic Operators.  
We can divide the operations into different groups: • Arithmetic Operators  
• Assignment operators  
• Comparison Operators  
• Increment/Decrement Operators  
• Logical Operators  
• String Operators  
• Array operators  
• Conditional assignment operators Arithmetic Operators: Addition: + is the addition operator.This is used when we want sum of two variables. For example: <?php $x= 10; $y=20; echo $x+$y; ?>  
![](image_rsrcDX.jpg)Illustration 4: Addition Operator Subtraction:- is the subtraction operator.This is used when we want to subtract one variable from other variable. <?php $x=50; $y=25; echo $x-$y; ?> Here by using subtraction operator $y variable is deducted from $x variable.Check the output below: ![](image_rsrcDY.jpg)Illustration 5: Subtraction Operator Multiplication: \* is the  
multiplication operator.This is used when we want a product of two variables. <?php  
$x=10;  
$y=20;  
echo $x\*$y;  
?> Here in above example we have two variable $x and $y.We are mutiplying it to get the product of two variables.Check the output below: ![](image_rsrcDZ.jpg)Illustration 6: Mutiplication operator Division: / is the divison operator which is used when we want to divide one variable by another variable. For example: <?php  
$x=100;  
$y=10;  
echo $x/$y; ?> Here we have one variable $x which is getting divided by $y and return a value. Check the output below:  
![](image_rsrcE0.jpg)Modulus:% is the modulus operator which returns the remainder when one variable is divided by another variable. For example: <?php  
$x=100;  
$y=40;  
echo $x%$y; ?> In the above example we have taken a variable $x and it is getting divided by $y. The result will be the remainder we are getting by dividing the two variables.Check out the output below: ![](image_rsrcE1.jpg)Illustration 7: Modulus Operator Exponentiation: \*\* is the  
 exponentiation operator.It is used when we want to print any variable with some power. For example: <?php  
$x=2;  
$y=3;  
echo $x\*\*$y; ?>  
In the above example we are finding 2 to power of 3.Check the outut below: ![](image_rsrcE2.jpg)Illustration 8: Exponentiation Operator  
Assignment Operators: With assignment operators we can set values in a variable.Basic assignment operator in PHP is “=” .  
For example: $x +=$y; is same $x= $x+ $y; $x -=$y; is same as $x=$x-$y; $x\*=$y; is same as $x=$x\*$y; $x /=$y; is same as $x=$x/$y; $x %=$y is same as $x=$x%$y; Comparison operators: \== is Equal operator . For  
example  
$x==$y Here this will return true if $x value is equal to $y value . === is the identical operator.For example : $x===$y returns true if and only if the values and type of both variables re same. != is the not equal to operator.For example:  
$x!=$y returns true if value of both variables are different.  
 <> is the not equal to operator.For example:  
$x!=$y returns true if value of both variables are different. !== Not identical operator. For example  
$x !== $y returns true if either the value is not same or the type is not same \> is the Greater operator.For example :  
$x > $y is true when $x value is greater than $y < is the Less than operator.For example :  
$x<$y is true when $x value is less than $y. \>= is Greater than or equal to operator.For example:  
$x>= $y is true when $x value is greater than or equal to $y <= is Less than or equal to operator .For example :  
$x<=$y is true when $x value is less than or equal to $y < = > is the spaceship  
operator.For example:  
$x < = > $y returns an integer less than ,equal to or greater than zero if value of $x is less  
than,equal to or greater thn $y. Increment and Decrement operators: $x++ will return $x and then increment it's value by one. ++$x will increment value of $x by oe and then return $x  
$x-- will return $x and then decrease it's value by one  
\--$x will decrement the value by one and then return $x Logical operators: And operator :$x and $y gives a result true if both $x and $y are true.  
&& operator:$x and $y gives a result true if both $x and $y are true.  
OR operator :$x and $y gives a result true if either $x and $y are true.  
|| operator :$x and $y gives a result true if either $x and $y are true.  
! Not operator: !$x gives a result true if $x is not true. CHAPTER 8  
Php String operators: There are two operators under Php String operators.One is the concatenation and other one is concatenation assignment operator. Concatenation : $x . $y concatenates $x and $y Concatenation Assignment operator :$x .=$y .This appends $y to $x. CHAPTER 9  
 Strings In PHP:  
A string is a sequence of characters.  
How can we define a string variable?  
Lets check out an example below:  
$x=”hello world”; Here in above example we have created a variable $x and assign some value to it.The value assigned to it is a sequence of characters.thus in this way a string variable is created. In Php there are various PHP string functions which can be used in application.Some of them have been discussed below: Suppose we want to check the length of a string variable.We can use strlen() for that.  
<?php echo strlen(“hi”)  
?> This will give the following output: 2 since there are only two characters. There are numbers of other php string functions .like  
strstr,strlen,strpos etc. PHP Arrays:  
Arrays is used to store multiple values in a single variable.  
To define array we use \[\] brackets.  
Lets define an array say fruits;  
$fruits=array(); The above $fruits is an empty array.Now we assign some values to it. $fruits=\['guava','apple','orange','pi neaplle','mango'\]; Now if we print the array\[1\] it will give the result as apple because in this array we have apple in index 1. Well there are three types of arrays:  
Numeric Arrays,Associative Arrays and Multidimensional arrays. Numeric Arrays are those where the index is numeric.  
Associative arrays are those where the index is not numeric. Multidimensional Arrays are those which contain more than 1 array. CHAPTER 10  
If and Else block with examples:: If and Else are conditional blocks that perform different actions based on some  condition. For example: We want to print hello when the variable value is 10.For this we are going to apply If and else block. Example:  
<?php  
$var=10; if($var==10) {  
echo “hello”; }  
else  
{  
echo “bye”; }  
?>  
In this above example first we have defined a variable and have assigned it a value of 10.  
In the next statement we are applying if condition ie if the value of variable is 10 then it will print hello otherwise it will execute the else block ie it will print bye.  
Here the variable value is  
satisfying the if condition ie the variable value is 10 so here hello will get displayed on the screen. See the output below: ![](image_rsrcE3.jpg)Illustration 9: If .. Else block  
CHAPTER 11  
Loops in PHP:: When we want to run a piece of code again and again when certain conditions are met then we use loops. There are different types of loops: while  
do .. while  
for  
foreach :loop While loop gets executed till the condition is true Syntax for while loop: while(till condition is true) {  
code to be executed  
} Example:  
Let say we have a variable $var=1; while ($var <=6) {  
echo $var; $var++; }  
OUTPUT: 123456 The variable here gets increased by 1 and is displayed on screen till it's value is less than or equal to 6. do....while loop always executes the block of code first time and then repeat the loop if condition is true. Syntax for do...while: do  
{  
code to be executed }while(condition is true) Example:  
$var=1; do  
{  
echo $var;  
$var++;  
}while($var<=6); Output: 123456 for Loop iterates through a block of code till the specified number of times and till the condition is true. Syntax  
for(initialization; condition; increment)  
{ code to be executed  
}  
Example:  
for($x=1 ;$x<=5 ;$x ++) {  
echo $x;  
} Output: 12345 Foreach loop :Loops through a block code for each element in an array Syntax:  
foreach($array as $key=>$value)  
{  
echo $key;  
echo '<br>';  
echo $value;  
}  
Suppose we have an array  
variable $arr. $arr=\['a'=>'yellow','b'=>'red','c'=> 'white'\];  
foreach($arr as $key=>$value) { echo $key; echo '<br>'; echo $value; } OUTPUT: a  
yellow b  
red  
c  
white PHP Superglobals:: The predefined variables which are global in scope ie they can be accessed from anywhere in the script.Nothing special has to be done to call these superglobal variables.Some of them are mentioned below: $\_GLOBALS $\_SERVER $\_POST  
 $\_GET  
$\_REQUEST $\_FILES  
$\_ENV  
$\_COOKIE $\_SESSION $\_SERVER returns information related to your headers and path $\_POST is used to retrieve value of data posted from any form, $\_GET is used to retrieve any value of any get variable,  
$\_REQUEST is used to retrieve both the post and get data.  
$\_ENV is the environment variable. PHP FORMS: Now a days we all are familiar with the websites on internet. Whether we have a restaurant site or event booking or any  
blog.Every website has a form for their every functionality.  
Say we visit a restaurant website and now we want to book a table for dinner.  
So how do the restaurant manager will come to know about the booking.  
Well he will ask his developer to create a page which will usually collect some information from guests . The developer will design the webpage and create a form where he will add some basic fields to collect information from guest. He will collect the Name,Mobile No. and other information. And then insert it in database.In this way Manager will come to know about the booking. So here we are going to learn how to create PHP forms.  
The PHP form start with <form> tag and ends with </form> The basic fields which we can include in the form is text  
field,password field,textarea,date calendar,radio buttons and  
checkboxes. Every form has a method type ie post or get.These methods specify how your data is being  
transferred from form to your server.  
Get is the default method.If Get method is used then data will get appended in the url whereas if the method is post it will be more secure and the data will not get exposed in the url. Every form has an action attribute ie the form on subit will redirect to that specific action for getting the processing of the form. Syntax::  
<form action=”action.php” method=”post”>  
<field1...>  
<field2...>  
</form> Example:Form for resrving a table for guests <form method type=”post” action=”process.php” >  
Name:<input type=”text”  
name=”name”>  
Mobile:<input type=”number” name=”mobile”>  
Email:<input type=”text”  
name=”email”>  
<input type=”submit”  
name=”submit” value=”submit”> </form> CHAPTER 14 Server Side Validation:: When we submit a form the form should be validated.This means we should apply a rule to check that the mandatory fields are not empty and the value entered is in correct type. For the above form we will add an action in process.php  
if(isset($\_POST\['submit'\])) {  
if($\_POST\['name'\]!='' &&  
$\_POST\['number'\]!='' && $\_POST\['email'\])  
{  
code to be executed }  
else  
{  
redirect to previous page } } The code above checks if the fields contain some value or not.If the value is not set for any field then the guest gets  
redirected to the form page. CHAPTER 15  
Intoduction to Mysql: Mysql is an opensource relational database system.Mysql is the mostly used database  with PHP. It is developed,distributed and supported by Oracle Corporation. In Mysql there are tables.  
Each table contain some rows and columns.It works for both small and large applications.It is fast , reliable and very easy to use database system.It compiles on number of platform. CHAPTER 16  
Connection of Mysql in PHP::  
We can use Mysqli to connect to PHP.  
Syntax:: <?php  
$host='localhost'; $username='root'; $password=''; //For creating a newconnection $conn= new mysqli($host, $username,$password); if($conn->connect\_error) {  
die(' Connection Failed : '.  
$conn->connect\_error);  
} echo 'Connected Successfully'; ?>  
Output::  
Connected Successfully In the above we are creating an instance of mysqli class  
providing necessary details.If the connection is created then  
connection will be successful otherwise it will print some error stating that connection is not created. CHAPTER 17  
Create database and tables:  
To create database you can write the following sql command:  
CREATE DATABASE dbname;  
You can also create database by navigating to phpmyadmin PhpMyAdmin is a free and open source administration tool for MySQL and MariaDB.As a portable web application written primarily in PHP,it has become one of the most popular MySQL administartor tools. Check the screensot below:  
![](image_rsrcE4.jpg)Illustration 10: phpMyAdmin Interface  
Mysql is the relational database which is used to store data.  
Connect to Mysql database from your php code: To connect with database from php code we need to write code to connect with database. <?php $servername = "hostname or ip address";  
$username = "mysql username"; $password = "mysql password"; /\*Create a connection with below code\*/  
$connection =  
mysqli\_connect($servername, $username, $password);  
/\*Add code to check connection\*/ if (!$connection){  
die("Connection failed: " .  
mysqli\_connect\_error());  
}  
echo "Connected successfully";  
?> How to create database: You can create database in two ways.The first way is to go to phpmyadmin and click on  
“Databases” tab.On clicking it an option will appear where you can enter your desired database name and click on :Create” button. Second option is to go to  
phpmyadmin and click on Sql tab.  
Paste the query: CREATE  
DATABASE \`database\_name\`; and then click on Go button.The above query will be executed and the database will be created. Now we need to create table in our database: I have created a database name \`myproject\`.Now I will be creating tables under this  
database.I am going to create table category under database myproject.When you have  
created database you can see that will appear in the left side of your phpmyadmin interface.  
From here you will click on the database myproject.  
In this way it gets selected. Now you can see an option to Create table.Enter the name of table in the text box which is there on the screen and number of columns ie the fields you want for your table. ![](image_rsrcE5.jpg)Now I have entered the name as category and 4 in column fields and click on GO button.Table category will be created and will ask you to enter the name of the columns and the datatype you want for your column names in table. ![](image_rsrcE6.jpg)Now click on GO button and table will be created. You can also run the below query under sql tab in phpmyadmin and execute the query to create table. CREATE TABLE  
\`myproject\`.\`category\` (  
\`id\` INT NOT NULL  
AUTO\_INCREMENT ,  
\`name\` VARCHAR(64) NOT NULL ,  
\`status\` CHAR(1) NOT NULL , \`sort\_order\` TINYINT(1) NOT NULL ,  
PRIMARY KEY (\`id\`)) ENGINE = InnoDB; CHAPTER 18 Session in PHP:  
Well what are sessions and why are they used ? Sessions are stored in server in form of variables.They are generally used to store webpage visitor preferences and identify him across multiple webpages. Session expires when we close the webpage or log out of the application. How to create session in PHP? We use $\_SESSION superglobal variable to create session.  
For creating session we need to first start session and the store the varibale in session. Find the code below:  
session\_start();  
$\_SESSION\['username'\]='your\_u sername'; How to check if the session is set or not? To check the session variable is set or not you can use isset variable and use that session variable.  
if(isset($\_SESSION\['username'\])) {  
/\*your piece of code\*/  
} How to end a session? When we donot require session we can unset the session variable and destroy it. session\_start();  
unset($\_SESSION\['username'\]); session\_destoy(); Where do we use session? Session is used to store the login details of any user so he can access the other webpages and we can track the user.When a user usually logs out his session gets expired and he leave the  
application. CHAPTER 19 Now we are going to create a small PHP project where we will be creating database and table . Then we we will be creating a small project where user will register and can login and  
navigate to the restricted page in the website. CREATE DATABASE:  
Run this below query to create database:  
Create DATABASE \`user\_registration\`; Select the database and copy the below code.Execute the query after pasting it under sql tab to create table \`users\`: CREATE TABLE  
\`user\_registration\`.\`users\` ( \`id\` INT NOT NULL  
AUTO\_INCREMENT , \`name\` VARCHAR (255) NOT NULL , \`type\` ENUM('user','admin') NOT NULL , \`username\`  
VARCHAR (64) NOT NULL , \`password\` VARCHAR (255) NOT NULL , \`status\` CHAR (1) NOT NULL DEFAULT 'A' , PRIMARY KEY (\`id\`)) ENGINE = InnoDB; Now we create a project folder name user\_registration.  
Under this folder we are going to save php files,css,js and images. We will be having below file structure for our project ![](image_rsrcE7.jpg)I have created a folder named as ReadersCollection.  
Inside that I have created my project folder named as  
user\_registration.  
This folder holds index.php which is the main registration page.Other pages are login page,restricted page and a  
process.php page.process page is the one where we will be writing all our logic part for the code.I have created a connection.php page which holds code for connecting to the database. Screenshot for the main registration page: ![](image_rsrcE8.jpg)This folder contains a css and js folder.The css folder contains bootstrap.css file and js folder olds bootstrap.js file.I have not included here.You can go to  
 bootstrap website and download the respective files and include in your project. Code for connection.php <?php  
session\_start();  
$servername = "localhost"; $username = "root";  
$password = ""; $dbname='user\_registration'; /\*Create a connection with below code\*/  
$connection =  
mysqli\_connect($servername, $username, $password,$dbname); /\*Add code to check connection\*/ if (!$connection){  
die("Connection failed: " . mysqli\_connect\_error());  
}  
//echo "Connected successfully"; ?>  
This page will be included in the top of every php page. REGISTRATION FUNCTIONALITY: The register form holds three input name,username and password.Username should be unique and password should be stored in encrypted form.The code for register or index page can be found below: Code for index.php <!DOCTYPE html>  
<?php  
include "connection.php"; ?>  
<html> <head>  
<title></title>  
<meta charset="UTF-8"> <meta name="viewport" content="width=device-width, initial-scale=1.0"> <link rel="stylesheet" href="css/bootstrap.css">  
<script  
src="js/bootstrap.js"></script> </head>  
<body>  
<div class="container textcenter">  
<nav class="navbar navbar-expand-lg navbar-light bg-light">  
<ul class="navbar-nav mr-auto">  
 <?php  
if(isset($\_SESSION\['username'\])) { ?>  
<li class="nav-item active"><a href="restricted.php"> Restricted Page | </a></li>  
<?php } ?>  
<?php if(!  
isset($\_SESSION\['username'\])) { ?>  
<li class="nav-item active"><a href="login.php"> Login |</a></li> <?php } if(isset($\_SESSION\['username'\])) { ?> <li class="nav-item active"><a href="process.php? action=logout"> Logout</a></li> <?php }?>  
</ul>  
</nav>  
<?php if(! isset($\_SESSION\['username'\])) { ?>  
<div class="row"> <div class="col-md-12"> <div  
class="row"><strong>Register  
here</strong></div>  
</div>  
</div>  
<form name="frm"  
method="post"  
action="process.php?  
action=register">  
<div class="row"> <div class="col-md-12"> <div class="col-md6">Name:</div>  
<div class="col-md6"><input type="text"  
name="name" value=""></div> </div>  
<div class="col-md12">  
<div class="col-md6">UserName:</div>  
<div class="col-md6"><input type="text"  
name="username"  
value=""></div>  
</div>  
<div class="col-md-12"> <div class="col-md6">Password:</div>  
<div class="col-md6"><input type="password"  
name="password"  
value=""></div>  
 </div> </div>  
<div class="row"><input type="submit" name="submit" value="SUBMIT"></div> </form>  
<?php } else {  
echo 'You are logged in.';  
}?> </div> </body> </html> Here we have created a form and have three inputs ie name,  
username and password. When visitor enter the above details and click on SUBMIT button his information gets inserted in table and he gets register in the system.  
He is then redirected to the restricted area. Code of process.php for  
action="process.php?  
action=register" to allow user to register in the system if(isset($\_REQUEST\['action'\]) &&  
($\_REQUEST\['action'\]=='register ')){ $name=$\_POST\['name'\]; $username=$\_POST\['username'\]; $password=md5($\_POST\['passw ord'\]); if( isset($name) &&  
isset($username) &&  
isset($password) ){ $username\_check=mysqli\_query( $connection,"SELECT \* from \`users\` where  
\`username\`=$username"); if(mysqli\_num\_rows($username\_ check)==0){  
$username\_db=$username;  
} else{ $username\_db=rand(0,9).'\_'. $username;  
}  
$sql="insert into \`users\`(\`name\`,\`username\`,\`pass word\`)values('".$name."','". $username\_db."','".  
$password."')"; mysqli\_query($connection, $sql)or die('error');  
$\_SESSION\['username'\]=$userna me\_db;  
$\_SESSION\['name'\]=$name; header("location:restricted.php"); }  
else{  
header("location:index.php? msg=Please enter fields"); }  
} Explanation: First the line  
if(isset($\_REQUEST\['action'\]) &&  
($\_REQUEST\['action'\]=='regis ter')){ checks if the action value is register then it will proceed further and if the value is not register then it will exit from the condition. $username\_check checks that whether this username already exists in the database or not. If it exists we are appending the username with some random numbers using rand() function so that it will remain unique. The next code inserts an entry and sets the variable name and username in session using $\_SESSION superglobal variable. Then user is redirected to restricted page .  
LOGIN FUNCTIONALITY: For login functionality we will be creating login.php page.Here we will be taking two inputs  
username and password and a submit button. After user enter the data the code checks the username and  
password matches then the user is succefully logged in and his login details like name and username is set in session.The user is then redirected to restricted page. Screenshot for login.php: ![](image_rsrcE9.jpg)Code for login.php page: <!DOCTYPE html>  
<?php  
include "connection.php";  
?>  
<html> <head>  
<title></title>  
<meta charset="UTF-8"> <meta name="viewport" content="width=device-width, initial-scale=1.0"> <link rel="stylesheet" href="css/bootstrap.css">  
<script  
src="js/bootstrap.js"></script> </head>  
<body> <div class="container textcenter"> <nav class="navbar navbar-expand-lg navbar-light bg-light"> <ul class="navbar-nav mr-auto"> <?php  
if(isset($\_SESSION\['username'\])) { ?> <li class="nav-item active"><a href="restricted.php"> Restricted Page | </a></li> <?php } ?>  
<?php if(!  
isset($\_SESSION\['username'\])) { ?> <li class="nav-item active"><a href="index.php"> Register |</a></li> <li class="nav-item active"><a href="login.php"> Login |</a></li> <?php }  
if(isset($\_SESSION\['username'\])) { ?> <li class="nav-item active"><a href="process.php? action=logout"> Logout</a></li> <?php }?>  
</ul>  
</nav>  
<div class="row"><?php if(isset($\_GET\['msg'\])){echo $\_GET\['msg'\];}?></div>  
<?php if(! isset($\_SESSION\['username'\])) { ?>  
<div class="row">  
<div class="col-md-12"> <div  
class="row"><strong>Login  
here</strong></div>  
</div>  
</div>  
<form name="frm"  
method="post"  
action="process.php?  
action=login">  
<div class="row"> <div class="col-md12">  
<div class="col-md6">UserName:</div>  
<div class="col-md6"><input type="text"  
name="username"  
value=""></div>  
</div>  
<div class="col-md-12"> <div class="col-md6">Password:</div>  
<div class="col-md6"><input type="password" name="password"  
 value=""></div>  
</div> </div>  
<div class="row"><input type="submit" name="submit" value="SUBMIT"></div>  
</form>  
<?php } else {  
echo 'You are logged in.';  
}?> </div> </body> </html> Code for action="process.php? action=login" in process.php below: if(isset($\_REQUEST\['action'\]) &&  
($\_REQUEST\['action'\]=='login')) { $username=$\_POST\['username'\]; $password=$\_POST\['password'\]; $new\_password=md5($password ); $sel\_query="SELECT \* from \`users\` WHERE \`username\`='". $username."' and \`password\`='". $new\_password."'"; $sql=mysqli\_query($connection, $sel\_query);  
if(mysqli\_num\_rows($sql)>0){  
$row=mysqli\_fetch\_array($sql);  
$\_SESSION\['username'\]=$row\['u sername'\];  
$\_SESSION\['name'\]=$row\['name '\];  
header("location:restricted.php");  
}  
else{  
header("location:index.php? msg=Incorrect username or password");  
}  
} Here the code checks for the username and password.As we are encrypting the password using md5 hash so when user enters his password we convert it into encrypted form using md5 hash and then data is verified with the database values and then if a match is found then user is redirected to restricted page. If a match is not found then the user is redirected to main page ie. the index.php page with a  
message in the msg variable ie Incorrect username and  
password. RESTRICTED PAGE FUNCTIONALITY: Code in “Restricted page” ie restricted.php page checks  
whether the session variable is set or not.If session variable $\_SESSION\['username'\] is already set then “Welcome to restricted access” message is displayed on page. Code for resticted page:  
<?php  
include "connection.php";  
if(!  
isset($\_SESSION\['username'\])){ header("location:index.php"); }  
?>  
<!DOCTYPE html>  
<html> <head>  
<title></title>  
<meta charset="UTF-8"> <meta name="viewport" content="width=device-width, initial-scale=1.0"> <link rel="stylesheet" href="css/bootstrap.css">  
<script  
src="js/bootstrap.js"></script> </head>  
<body> <div class="container textcenter"> <nav class="navbar navbar-expand-lg navbar-light bg-light"> <ul class="navbar-nav mr-auto"> <?php  
if(isset($\_SESSION\['username'\])) { ?> <li class="nav-item active"><a href="restricted.php"> Restricted Page | </a></li> <?php } ?>  
<?php if(!  
isset($\_SESSION\['username'\])) { ?> <li class="nav-item active"><a href="index.php"> Register |</a></li> <li class="nav-item active"><a href="login.php"> Login |</a></li> <?php }  
 if(isset($\_SESSION\['username'\])) { ?> <li class="nav-item active"><a href="process.php? action=logout"> Logout</a></li> <?php }?>  
</ul>  
</nav> <?php  
if(isset($\_SESSION\['username'\])) { ?> <div class="row">  
<div class="col-md-12"> <div  
class="row"><strong>Welcome to restricted  
access</strong></div> </div>  
</div>  
<?php } ?> </body> </html>  
LOGOUT FUNCTIONALITY: When user no longer wants to stay in your website he may opt to exit from the application.In this case he will click on logout button.Clicking on this his session will get expired and he will be redirected to index.php with a message ie “Logged Out Successfully”. Code for logout action which is in the top section of every page. if(isset($\_REQUEST\['action'\]) &&  
($\_REQUEST\['action'\]=='logout' )){ unset($\_SESSION\['name'\]); unset($\_SESSION\['username'\]); session\_destroy();  
header("location:index.php? msg=Logged out successfully"); }