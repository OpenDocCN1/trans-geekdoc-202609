   

 

 

PHP MYSQL

In 8 Hours

By Ray Yao

For Beginners

Learn PHP Fast!

 

  

Copyright © 2015 by Ray Yao

All Rights Reserved

 

Neither part of this e-book nor whole of this e-book may be reproduced or transmitted in any form or by any means electronic, photographic or mechanical, including photocopying, recording, or by any information storage or retrieval system, without prior written permission from the author.

Ray Yao

  

About the Author

Ray Yao:

Certified PHP engineer by Zend, USA

Certified JAVA programmer by Sun, USA

Certified SCWCD developer by Oracle, USA

Certified A+ professional by CompTIA, USA

Certified ASP. NET expert by Microsoft, USA

Certified MCP professional by Microsoft, USA

Certified TECHNOLOGY specialist by Microsoft, USA

Certified NETWORK+ professional by CompTIA, USA

 

Ray Yao’s books:

[Linux Command Line](http://www.amazon.com/Linux-Command-Line-Beginners-Guide-ebook/dp/B00OP0TZDY/ref=sr_1_20?ie=UTF8&qid=1420734172&sr=8-20&keywords=linux)

[JAVA 100 Tests for interview](http://www.amazon.com/JAVA-Tests-Answers-Explanations-Beginners-ebook/dp/B00T343AQU/ref=sr_1_77?ie=UTF8&qid=1422932089&sr=8-77&keywords=java)

[PHP 100 Tests for Interview](http://www.amazon.com/PHP-Tests-Beginner-Answers-Explanations-ebook/dp/B00U4Z5BHS/ref=sr_1_117?s=digital-text&ie=UTF8&qid=1425242078&sr=1-117&keywords=php)

[JAVA in 8 Hours](http://www.amazon.com/Java-Hours-Essential-Knowledge-Beginners-ebook/dp/B00UI9266Y/ref=sr_1_205?s=digital-text&ie=UTF8&qid=1426071988&sr=1-205&keywords=java)

[PHP in 8 Hours](http://www.amazon.com/PHP-MySQL-Minutes-Coding-Beginners-ebook/dp/B00U02VLB0/ref=sr_1_23?ie=UTF8&qid=1424960929&sr=8-23&keywords=PHP) 

[JavaScript in 8 Hours](http://www.amazon.com/JAVASCRIPT-Beginners-JavaScript-Simple-programming-ebook/dp/B00WH0ESWC/ref=sr_1_30?s=digital-text&ie=UTF8&qid=1429761426&sr=1-30&keywords=javascript)

[C++ in 8 Hours](http://www.amazon.com/Hours-Beginners-Simple-programming-coding-ebook/dp/B00XT1HRA8/ref=sr_1_16?ie=UTF8&qid=1432212644&sr=8-16&keywords=C%2B%2B)

[Ray Yao's books](http://www.amazon.com/Ray-Yao/e/B00RG5FG6K/ref=ntt_dp_epwbk_0)

  

Preface

“PHP & MYSQL in 8 Hours” is a useful book for beginners. You can learn complete primary knowledge of PHP & MYSQL fast and easily. The straightforward definitions, the plain and simple examples, the elaborate explanations and the neat and beautiful layout feature this helpful and educative book. You will be impressed by the new distinctive composing style. Reading this book is a great enjoyment! You can master all essential PHP & MySQL skill in 8 hours. Start Coding Today!

 (The appendix of this book includes

(1)    6 Security Tips

(2)   MySQL Command Charts

(3)   100 Tests for Interview, Answers and Explanations)

 

  

Table of Contents

[Hour 1](#part0000_split_005.html#_Toc423202265)  [Start PHP](#part0000_split_006.html#_Toc423202266)

[What is PHP?](#part0000_split_007.html#_Toc423202267)

[PHP Reserved Words](#part0000_split_010.html#_Toc423202268)

[Comments](#part0000_split_013.html#_Toc423202269)

[Variables](#part0000_split_016.html#_Toc423202270)

[Data Types](#part0000_split_019.html#_Toc423202271)

[Escaping Characters](#part0000_split_022.html#_Toc423202272)

[Functions](#part0000_split_025.html#_Toc423202273)

[Function with Arguments](#part0000_split_028.html#_Toc423202274)

[Variable Scope](#part0000_split_031.html#_Toc423202275)

[Multiple Arguments](#part0000_split_034.html#_Toc423202276)

[Hour 2](#part0000_split_037.html#_Toc423202277)  [PHP Basic](#part0000_split_038.html#_Toc423202278)

[Arithmetical Operators](#part0000_split_039.html#_Toc423202279)

[Logical Operators](#part0000_split_042.html#_Toc423202280)

[Assignment Operators](#part0000_split_045.html#_Toc423202281)

[Comparison Operators](#part0000_split_048.html#_Toc423202282)

[Conditional Operator](#part0000_split_051.html#_Toc423202283)

[If Statement](#part0000_split_054.html#_Toc423202284)

[If-else Statement](#part0000_split_057.html#_Toc423202285)

[Switch Statement](#part0000_split_060.html#_Toc423202286)

[For Loop](#part0000_split_063.html#_Toc423202287)

[While Loop](#part0000_split_066.html#_Toc423202288)

[Do-While Loop](#part0000_split_069.html#_Toc423202289)

[Break Statement](#part0000_split_072.html#_Toc423202290)

[Continue Statement](#part0000_split_075.html#_Toc423202291)

[Hour 3](#part0000_split_078.html#_Toc423202292)  [Use Array](#part0000_split_079.html#_Toc423202293)

[Create an Array](#part0000_split_080.html#_Toc423202294)

[Show array element values](#part0000_split_083.html#_Toc423202295)

[Get the Size of Array](#part0000_split_086.html#_Toc423202296)

[Add Array Elements](#part0000_split_089.html#_Toc423202297)

[Remove Array Elements](#part0000_split_092.html#_Toc423202298)

[Merge Array](#part0000_split_095.html#_Toc423202299)

[Extract Array](#part0000_split_098.html#_Toc423202300)

[Sort Array](#part0000_split_101.html#_Toc423202301)

[Array keys & Values](#part0000_split_104.html#_Toc423202302)

[Iterate Array](#part0000_split_107.html#_Toc423202303)

[Hour 4](#part0000_split_110.html#_Toc423202304)  [Form Basic](#part0000_split_111.html#_Toc423202305)

[Create a Form](#part0000_split_112.html#_Toc423202306)

[Text Inputs](#part0000_split_115.html#_Toc423202307)

[Password inputs](#part0000_split_118.html#_Toc423202308)

[Submit Inputs](#part0000_split_121.html#_Toc423202309)

[Reset Inputs](#part0000_split_124.html#_Toc423202310)

[Textarea Inputs](#part0000_split_127.html#_Toc423202311)

[Radio Inputs](#part0000_split_130.html#_Toc423202312)

[Checkbox Inputs](#part0000_split_133.html#_Toc423202313)

[Form Works with PHP](#part0000_split_136.html#_Toc423202314)

[Form Works with PHP](#part0000_split_138.html#_Toc423202315)

[Hour 5](#part0000_split_141.html#_Toc423202316)  [Dynamic Data](#part0000_split_142.html#_Toc423202317)

[Date & Time](#part0000_split_143.html#_Toc423202318)

[String Process](#part0000_split_146.html#_Toc423202319)

[Redirection of Browser](#part0000_split_149.html#_Toc423202320)

[Information of Visitor](#part0000_split_152.html#_Toc423202321)

[Cookie](#part0000_split_155.html#_Toc423202322)

[Session](#part0000_split_158.html#_Toc423202323)

[Open a File](#part0000_split_161.html#_Toc423202324)

[Read a File](#part0000_split_164.html#_Toc423202325)

[Write a File](#part0000_split_167.html#_Toc423202326)

[Close a File](#part0000_split_170.html#_Toc423202327)

[Hour 6](#part0000_split_173.html#_Toc423202328)  [MySql Basic](#part0000_split_174.html#_Toc423202329)

[Select a Database](#part0000_split_175.html#_Toc423202330)

[Create a Database](#part0000_split_178.html#_Toc423202331)

[Create & show a table](#part0000_split_181.html#_Toc423202332)

[MySQL Data Type](#part0000_split_184.html#_Toc423202333)

[Column Name Modifiers](#part0000_split_187.html#_Toc423202334)

[Insert Data to Table](#part0000_split_190.html#_Toc423202335)

[Alter a table](#part0000_split_193.html#_Toc423202336)

[Update Specific Data](#part0000_split_196.html#_Toc423202337)

[Delete Data](#part0000_split_199.html#_Toc423202338)

[Select Queries](#part0000_split_202.html#_Toc423202339)

[Hour 7](#part0000_split_205.html#_Toc423202340)  [MySql & PHP](#part0000_split_206.html#_Toc423202341)

[Connect MySql Server](#part0000_split_207.html#_Toc423202342)

[Select Database](#part0000_split_210.html#_Toc423202343)

[Insert Table Data](#part0000_split_213.html#_Toc423202344)

[Alter Table Data Type](#part0000_split_216.html#_Toc423202345)

[Retrieve Table Data](#part0000_split_219.html#_Toc423202346)

[mysqli\_fetch\_row( )](#part0000_split_222.html#_Toc423202347)

[mysqli\_fetch\_assoc( )](#part0000_split_225.html#_Toc423202348)

[mysqli\_fetch\_array( )](#part0000_split_228.html#_Toc423202349)

[mysqli\_num\_rows( )](#part0000_split_231.html#_Toc423202350)

[mysqli\_close( )](#part0000_split_234.html#_Toc423202351)

[Hour 8](#part0000_split_237.html#_Toc423202352)  [Class & Object](#part0000_split_238.html#_Toc423202353)

[Class Definition](#part0000_split_239.html#_Toc423202354)

[$this-> variable](#part0000_split_242.html#_Toc423202355)

[Object Declaration](#part0000_split_245.html#_Toc423202356)

[Constructor (1)](#part0000_split_248.html#_Toc423202357)

[Constructor (2)](#part0000_split_251.html#_Toc423202358)

[Destructor](#part0000_split_254.html#_Toc423202359)

[Extend Class](#part0000_split_257.html#_Toc423202360)

[The Use of Inheritance](#part0000_split_260.html#_Toc423202361)

[Class:: method ( )](#part0000_split_263.html#_Toc423202362)

 

[Appendix 1](#part0000_split_266.html#_Toc423202363)  [Security Tips](#part0000_split_267.html#_Toc423202364)

[Filter Malicious Password](#part0000_split_269.html#_Toc423202366)

[Filter Malicious Characters](#part0000_split_272.html#_Toc423202367)

[Filter Malicious Input](#part0000_split_275.html#_Toc423202368)

[Limit Specified Input](#part0000_split_278.html#_Toc423202369)

[Escape Output](#part0000_split_281.html#_Toc423202370)

[Protect Database](#part0000_split_284.html#_Toc423202371)

[Appendix 2 MySQL Command Charts](#part0000_split_287.html#_Toc423202372)

[(1)             Database Commands](#part0000_split_288.html#_Toc423202373)

[(2)             Table Commands](#part0000_split_288.html#_Toc423202374)

[(3)             Field Modifiers](#part0000_split_289.html#_Toc423202375)

[(4)             Operation Commands](#part0000_split_289.html#_Toc423202376)

[(5)             mysql\_xxx\_xxx (  )](#part0000_split_290.html#_Toc423202377)

[Appendix 3](#part0000_split_291.html#_Toc423202378)  [100 Tests for Interview, Answers & Explanations](#part0000_split_292.html#_Toc423202379)

[100 Tests for Interview, Answers & Explanations](#part0000_split_293.html#_Toc423202380)

 

[Conclusion](#part0000_split_419.html#_Toc423202390)

#  

#  

#  

#  

# Hour 1

 

# Start PHP

  

What is PHP?

PHP is a server-side language for web development, meaning “Personal Homepage Program”.

The syntax of PHP looks like this:

 
| <?php      // some PHP codes in here       ?> |
| --- |

##  

## Example:

<?php 

echo (“Hello World!”);

?>

 ( Output: Hello World! )

##  

## Explanation:

PHP code tag begins with <?php and ends with ?>, its syntax looks like this:

<?php      some PHP codes in here       ?>

“echo” is command of PHP, meaning “output” or “display”.

echo (“Hello World”); will output Hello World.

 

  

PHP Reserved Words

Some words are only used by PHP language itself. They may not be used when choosing identifier names for variable, function, and labels. The following words are part of PHP reserved words

 
| and || array( ) || break |
| --- | --- | --- |
| case || const || continue |
| default || do || echo( ) |
| else || else if || empty( ) |
| eval( ) || exception || exit( ) |
| extends || false || for |
| function || foreach || global |
| if || include( ) || include\_once( ) |
| isset( ) || list( ) || new |
| null || or || print( ) |
| require( ) || require\_once( ) || return( ) |
| static || switch || true |
| unset( ) || xor || while |

## Example:

const     // const is a reserved word.

continue   // continue is a reserved word.

## Explanation:

PHP reserved words may be not used as variable name, function name, and label name.

  

Comments

// is used in single-line comments.

/\*……\*/ are used in multi-line comments.

# is used in single-line comments sometimes.

##  

## Example:

<?php

echo (“OK”);  // output OK.

echo (“Hello”);   /\* echo (“Hello”); is a PHP statement, echo is a reserved word, it displays a word “OK”. PHP is very easy to learn. \*/

?>

( Output: OK )

 

## Explanation:

// output OK; is a single-line comment.

/\* echo (“OK”); is a PHP statement, echo is a keyword, it display a word OK. PHP is very easy to learn.\*/ is a multi-line comment.

  

Variables

Variable is a symbolic name associated with a value. Variable name starts with $ symbol.

## Example:

<?php

$var;

$abcde;

$my\_variable;

?>

## Explanation:

$var, $abcde and $my\_variable are all variables. 

They can store some value. e.g.

$var=100; 

$abcde=”Hello World”; 

$my\_variable=true;

Notice that variable naming cannot start with number, cannot have space. e.g. “$23var”, “$abc de” are invalid variable name. 

But “$var23”, “$abcde” are valid variable name.

  

Data Types

String – characters within double or single quotation.

Integer – numbers without decimal point.

Boolean – a value with true or false.

Float – numbers with decimal point.

## Example:

$str=’I am a string’;

$int=168;

$float=12.88;

$bool=true;

## Explanation:

$str=’I am a string’;  // $str data type is String.

$int=168;  // $int data type is Integer.

$float=12.88;  // $float data type is Float.

$bool=true;  // $bool data type is Boolean.

Note: Double quotes or single quotes are always used in string. e.g. “abcde”, ‘learning’.

  

Escaping Characters

The “ \\ ” backslash character can be used to escape characters.

\\n outputs content to the next new line.

\\r makes a return

\\t makes a tab

\\’ outputs a single quotation mark. 

\\” outputs a double quotation mark.

## Example:

<?php

echo “PHP say \\”Hello World\\” ”;  

?>

(Output: “Hello World”)

## Explanation:

\\” outputs a double quotation mark. Note that “Hello World” has a double quotation with it. Another sample: 

 \\t makes a tab

echo “Hello \\t\\t\\t World”;   // Note here has three taps

( Output:  Hello     World )

  

Functions

A function is a code block that can repeat to run many times. To define a function, use “function function-name ( ) { }”. 

 
| function function-name ( ) {……} |
| --- |

To call a function, use “function-name ( );”

 
| function-name ( ); |
| --- |

## Example:

<?php

function test( ){    

echo (“show a sample”);

} 

test ( );   

?>

(Output: show a sample)

## Explanation:

function test( ) { } is a declaration of PHP test( ) function.

test( ); is a command to call a function named test( ){ }.

When running the function test ( ), it will output “show a sample”.

  

Function with Arguments

A function can have one or more arguments inside the bracket. Arguments are used to pass data to function.

 
| function function-name ( $argument ){……}  |
| --- |

## Example:

<?php

function test( $arg ){

echo (“$arg”);

}

test(“display a sample”);

?>

(Output:  display a sample)

##  

## Explanation:

$arg is an argument of function test($arg ){ }. When test(“display a sample”) call the function test($arg){…}, it will pass the “display a sample” to $arg. After $arg has received the data, it will pass the data inside the function. echo ($arg) will use the data, and then outputs “display a sample”.

  

Variable Scope

Global variable is declared outside the function, it can be used in everywhere; local variable is declared inside the function, it is only used inside current function.

## Example:

<?php   

$num=200;  // This $num is global variable.

function test( ){

$num=100;  // This $num is local variable.

}

echo $num;

?>

(Output:  200)

## Explanation:

echo $num outputs 200, which means $num store a value of global variable.

If you want to declare a global variable inside a function, you should use a keyword “global” preceding the variable name. e.g. function test( ) { global $num; ……} 

  

Multiple Arguments

A function may have several arguments; these arguments will pass data simultaneously for the function.

 
| function function-name ( $arg1, $arg2, $arg3){……} |
| --- |

 

## Example:

<?php

function test ($a, $b, $c){

$sum=$a+$b+$c;

echo $sum;

}

 test(3, 6, 9);

?>

(Output:  18)

##  

## Explanation:

When test(3, 6, 9) call the function test ($a, $b, $c){…}, arguments 3,6,9 will pass to the $a, $b, $c, the $sum will be assigned the value of 18. The output is 18. 

#  

#  

#  

#  

#  

# Hour 2

 

# PHP Basic

  

Arithmetical Operators

 
| Operators || Running |
| --- | --- |
| + || add |
| \- || subtract |
| \* || multiply |
| / || divide |
| % || get modulus |
| ++ || increase 1 |
| \- - || decrease 1 |
| . || connect two strings |

## Example:

$add=100+200;   echo $add;    

$div=800/2;   echo $div;  

$mod=10%3;   echo $mod;   

$inc=10;   echo ++$inc;   

$str=”abc”.”de”;  echo $str;

## Explanation:

$add=100+200;   echo $add; will output  300 

$div=800/2;   echo $div; will output  400;

$mod=10%3;   echo $mod; will output  1;

$inc=10;   echo ++$inc; will output  11;

$str=”abc”.”de”;  echo $str; will output abcde.

  

Logical Operators

 

 
| Operators || Equivalent   |
| --- | --- |
| && || and |
| || || or |
| ! || not |

After using logical operators, the result will be true or false.

## Example:

$x=true; $y=false;

$a=$x && $y;   echo $a;   // output: false

$b=$x || $y;   echo $b;   // output: true

$c=! $x;   echo $c;   // output:  false

## Explanation:

 
|  true && true; returns true;  ||  true && false; returns false;  ||  false &&false; returns false;  |
| --- | --- | --- |
| true II true; returns true; || true II false; returns true; || false II false;return false; |
|  ! false;returns true;  || ! true;returns false; ||   |

 

  

Assignment Operators

 
| Operators || Examples: || Equivalent: |
| --- | --- | --- |
| += || $x+=$y || $x=$x+$y |
| \-\= || $x\-\=$y || $x=$x\-$y |
| \*\= || $x\*\=$y || $x=$x\*$y |
| /\= || $x/\=$y || $x=$x/$y |
| %= || $x%=$y || $x=$x%$y |
| .\= || $x.\=$y || $x=$x.$y |

## Example: 

$x=200;   $y=100; 

$x+=$y;  echo $x;

$x/=$y;   echo $x;

$x\-=$y;   echo $x;

 

$m=”abc”; $n=”de”; 

$m.=$n   echo $m;

## Explanation:

$x+=$y;   // $x=$x+$y;  echo $x; outputs 300

$x/\=$y;    // $x=$x/$y;  echo $x; outputs 2

$x\-\=$y;    //  $x=$x\-$y;  echo $x; outputs 100

$m.\=$n;    // $m=$m.$n;   echo $m; outputs  abcde

  

Comparison Operators

 

 
| Operators || Running |
| --- | --- |
| \> || greater than |
| < || less than |
| \>= || greater than or equal  |
| <= || less than or equal  |
| \== || equal  |
| !\= || not equal  |

After using comparison operators, the result will be true or false.

##  

## Example:

$a=100; $b=200;

$result = ($a\>$b); echo $result;

$result = ($a\==$b); echo $result;

$result = ($a!=$b); echo $result;

##  

## Explanation:

$result = ($a>$b); // test 100>200; outputs false.

$result = ($a==$b); // test 100==200; outputs false.

$result = ($a!\=$b); // test 100!\=200; outputs true.

  

Conditional Operator

 

The syntax of conditional operator looks like this:

 
|  (test-expression) ? (if-true-do-this) : (if-false-do-this);  |
| --- |

( test-expression) looks like $a<$b, $x!=$y, $m==$n. etc.

##  

## Example:

<?php

$a=100; $b=200;

$result=($a<$b) ? ”apple” : ”boy”;

echo $result;

?>

( Output: apple )

## Explanation:

The output is “apple”.

The conditional operator use ($a<$b) to test the $a and $b, because $a is less than $b, it is true. Therefore, the output is “apple”.

  

If Statement

 

 
| if ( test-expression ) {   // if true do this;   } |
| --- |

“if statement” executes codes inside { … } only if a specified condition is true, does not execute any codes inside {…} if the condition is false.

##  

## Example:

$a=200; 

$b=100;

if (a>b){

echo ”a is greater than b.”;

}

(Output:   a is greater than b.)

 

## Explanation:

( a>b ) is a test expression, namely (200>100), if returns true, it will execute the codes inside the { }, if returns false, it will not execute the codes  inside the { }.

  

If-else Statement

 

 
| if ( test-expression) {   // if true do this;   } else  {  // if false do this;   } |
| --- |

“if...else statement” runs some code if a condition is true and another code if the condition is false

## Example:

$a=100; $b=200;

if (a>b){

echo ”a is greater than b.”

}

else {

echo “a is less than b”;

}

(Output:  a is less than b.)

## Explanation:

( a>b ) is a test expression, namely (100>200), if returns true, it will output  ”a is greater than b.” if returns false, it will output “a is less than b”.

  

Switch Statement

 
| switch ( $variable ) { case 1: if equals this case, do this;  break;  case 2: if equals this case, do this;  break;  case 3: if equals this case, do this;  break;  default : if not equals any case, run default code;  break; } |
| --- |

The value of $variable will compare each case first, if equals one of the “case” value; it will execute that “case” code. “break;” terminates the code running.

## Example:

$number=20;

switch ( $number ) {

case 10 : echo “Running case 10”;  break;

case 20 : echo “Running case 20”;  break;

case 30 : echo “Running case 30”;  break;

default :  echo “Running default code”;  break;  }

(Output:  Running case 20)

## Explanation: 

The $number value is 20, it will match case 20, so it will run the code in case 20.

  

For Loop

 

 
| for( init, test-expression, increment) { // some code; } |
| --- |

“for loop” runs a block of code by specified number of times.

##  

## Example:

<?php 

    for ($x = 0; $x <= 5; $x++) {

    echo "$x ";

} 

?>

(Output: 012345 )

##  

## Explanation:

$x = 0 is initializer,

$x <= 5 is test-expression, the code will run at most 5 times.

$x++ means that x will increase 1each loop.

After 5 times loop, the code will output 012345.

  

While Loop

 

 
| while ( test-expression ) {  // some php code in here;  } |
| --- |

“while loop” loops through a block of code if the specified condition is true.

##  

## Sample:

$counter=0;

while ($counter < 8){

echo “&”;

$counter++;

}

( Output:  &&&&&&&& )

##  

## Explanation:

“$counter< 8” is a test expression, if the condition is true, the code will loop less than 8 times, until the $counter is 8, then the condition is false, the code will stop running.

  

Do-While Loop

 

 
| do{ // some php code in here } while ( test-expression); |
| --- |

“do...while” loops through a block of code once, and then repeats the loop if the specified condition is true.

##  

## Example:

$counter=0;

do {

echo “@”;

$counter++;

} while ($counter<8);

( Output: @@@@@@@@ )

##  

## Explanation:

“$counter< 8” is a test expression, if the condition is true, the code will loop less than 8 times, until the $counter is 8, then the condition is false, the code will stop running.

  

Break Statement

 

 
| Break; |
| --- |

“break” keyword is used to stop the running of a loop according to the condition.

 

## Example:

$num=0;

while ($num<10){

if ($num==5)  break;

$num++;

}

echo ( $num );

( Output:  5)

 

## Explanation:

“if ($num==5)  break;” is a break statement. If $num is 5, the program will run the “break” command, the break statement will exit the loop, then run “echo ( $num )”.

  

Continue Statement

 

 
| continue; |
| --- |

“continue” keyword is used to stop the current iteration, ignoring the following codes, and then continue the next loop.

## Example:

$num=0;

while ($num<10){

$num++;

if ($num==5)  continue;

echo ( $num );

}

 ( Output: 1234678910)

## Explanation:

Note that the output has no 5.

“if ($num==5)  continue;” includes “continue” command. When the $num is 5, the program will run “continue”, skipping the next command “echo ( $num )”, and then continue the next loop.

#  

#  

#  

#  

#  

# Hour 3

 

# Use Array

 

  

Create an Array

 

An array is a particular variable, which can contain one or more value at a time. array( ) is used to create an array. 

The syntax to create an array:

 
| $array-name = array (“value0”, “value1”, “value2”); |
| --- |

Other syntax to create an array:

 
| $array-name = array ( );$array-name\[index0\] = “value1”;$array-name\[index1\] = “value1”;$array-name\[index2\] = “value2”; |
| --- |

## Example:

$color = array ( );

$color \[0\] = red;

$color \[1\] = blue;

$color \[2\] = green;

## Explanation:

Above code creates an array, array name is $color, it has three elements: $color \[0\], $color \[1\], $color \[2\]. Its indexes are 0, 1, and 2. Its values are red, blue, and green.

  

Show array element values

 

To show array element values, use syntax as following:

 
| echo (   $array-name\[index\]    ); |
| --- |

 

## Example:

<?php

$color = array(“yellow”, “purple”, “orange”);

echo ( $color\[1\] );

?>

( Output:  purple )

##  

## Explanation:

From above, you can know:

The value of $color\[0\] is yellow.

The value of $color\[1\] is purple.

The value of $color\[2\] is orange.

Note that the indexes begin counting from zero.

  

Get the Size of Array

 

Two functions can get the size of an array.

 
| count( $array); |
| --- |
| sizeof($array); |

 

## Example:

<?php

$color = array(“yellow”, “purple”, “orange”);

$size=count($color);   // Or sizeof($color);

echo ( $size );  

?>

(Output:  3)

##  

## Explanation:

count($color) or sizeof($color) can return the size of array $color, and assigns the size of array to $size. 

array(“yellow”, “purple”, “orange”) has three elements, so its size is 3.

  

Add Array Elements

 

 
| array\_unshift( array, value1,  value2…);  |
| --- |
| array\_push( array, value1,  value2… );  |

array\_unshift( array, value1,  value2) adds value1, value2  at beginning of array.

array\_push( array, value1,  value2… ) adds value1, value2  at end of array.

## Example:

$myarray=array(“A”, “B”, ”C”);

array\_unshift($myarray, “D”, “E”);

array\_push($myarray, “F”, “G”);

echo ( $myarray );

( Output:   DEABCFG)

 

## Explanation:

array\_unshift($myarray, “D”, “E”) adds the element D, E at the beginning of  the element A, B, C in $myarray.

array\_push($myarray, “F”, “G”) adds the element F, G at the end of element A, B, C in $myarray.

  

Remove Array Elements

 

 
| array\_shift( array ); |
| --- |
| array\_pop( array); |

array\_shift( array ) removes element at beginning of the array.

array\_pop( array ) removes element at end of  the array.

## Example:

$myarray=array(“A”, “B”, “C”, “D”, “E” ):

$beginning=array\_shift($myarray);

$ending=array\_pop($myarray):

echo ( $beginning );  // shows the first removed element.

echo ( $ending );   // shows the last removed element.

( Output:  AE )

## Explanation:

array\_shift($myarray) removes and returns the first element in the $myarray, returns A.

array\_pop($myarray) removes and returns the last element in the $myarray, returns E.

 

  

Merge Array

 

 
| array\_merge( array1, array2 ); |
| --- |

array\_merge( array1, array2 ) can merge array1 and array2, and create a new array.

##  

## Example:

$array1=array (“A”, “B”, “C”);

$array2=array (“D”, “E”, “F”);

$array=array\_merge( $array1, $arra2 );

echo ( $array );

( Output:  ABCDEF )

##  

## Explanation:

array\_merge( $array1, $arra2 ) can merge two arrays to a new array $array, which holds the six elements from two arrays, returns ABCDEF.

 

  

Extract Array

 

 
| array\_slice( array, start, length ); |
| --- |

array\_slice( array, start, length ) can extract some elements from an array, at the start position and by specified length, and create a new array.

## Example:

$array=array(“A”,”B”,”C”,”D”,“E”,”F”);

$arr=array\_slice( array, 2, 3 );

echo $arr;

( Output: CDE )

 

## Explanation:

array\_slice( array, 2, 3 ) extracts 3 elements at the position 2 from $array.

Note that the beginning of position starts with 0.

  

Sort Array

 

 
| sort( array ); |
| --- |

sort(array) can sort the array in order by value.

##  

## Example:

$color=array(“yellow”, “red”, “blue”, “white”);

sort ( $color );

……

( Output:  blue  red  white  yellow )

 

## Explanation:

sort ( $color ) rearranges the order of $color array elements by value. After sorting, the array elements list in order as “blue red white yellow”.

  

Array keys & Values

 

Array elements are consisted of keys and value pair.

 
| array( key1=>value1, key2=>value2, kay3=>value3…); |
| --- |

“=>” is used to connect key and value. ( key and index is the same meaning.)

##  

## Example: 

<?php

$book=array( “1st”=>”JSP”, “2nd”=>”ASP”, “3th”=>”PHP”);

echo $book\[ “3th” \];

?>

( Output:  PHP)

 

## Explanation:

A string can act as an index of array.

“echo $book\[3th\]” shows the element value “PHP”, its index is “3th”.

  

Iterate Array

 

 
| foreach(array as $key=>$value){ } |
| --- |

For every loop iteration, the key of the current array element is assigned to $key, the value is assigned to $value, until iterates the last array element.

## Example:

$book=array( “1st”=>”JSP”, “2nd”=>”ASP”, “3th”=>”PHP”);

foreach ($book as $key=>$value){

echo “The $key book is about $value.\\n ”;

}

( Output:  The 1st book is about JSP.

                The 2nd book is about ASP.

                The 3th book is about PHP.)

## Explanation:

“foreach ($book as $key=>$value)” assigns $book’s key to $key, assign $book’s value to $value on each loop iteration. On the first loop iteration, “1st” is assigned to $key, “JSP” is assigned to $value, and so on…

#  

#  

#  

#  

#  

# Hour 4

 

# Form Basic

 

  

Create a Form

Html form submits data to server.

 
| <form  action=”url”  method=”get/post”>        …… </form> |
| --- |

The “action” attribute specifies the url of the PHP file that processes data from form.

The “method” attribute specifies the way to pass data to PHP file. Its value may be “get” or “post”.

## Example:

<form  action= “myfile.php”  method=”get” >

……

<form>

## Explanation:

action= “myfile.php”  specifies a PHP file myfile.php that processes the data from this form. 

method=”get” specifies the pass-data method is “get”, which is an open way to pass data.

method=”post” specifies the pass-data method is “post”, which is a hidden way to pass data.

  

Text Inputs

 

 
|  <input type=”text”  name=”xxx”>  |
| --- |

“type” attribute specifies the input type, which may be “text”, “password”, “radio”, “checkbox”, “hidden”……etc.

“text” type is used to input basic data

“name” attribute specifies the inputted contents that will be passed to the php file for processing.

## Example:

<form action=”myfile.php”  method=”get”>

<input type=”text”  name=”information”>

</form>

 (Display:   

 
|   |
| --- |

 )   

## Explanation:

input type=”text” specifies input type is “text”, 

name=”information” specifies the inputted contents that will be passed to the php file for processing.

  

Password inputs

 

 
| input type=”password” name=”yyy” |
| --- |

“type” attribute specifies the input type, which may be “text”, “password”, “radio”, “checkbox”, “hidden”……etc.

“password” type is used to input password.

“name” attribute specifies the inputted password that will be passed to the php file for processing.

## Example: 

<form action=”myfile.php”  method=”post”>

<input type=”password”  name=”secret”>

</form>

(Display:   

 
|   |
| --- |

 )   

 

## Explanation:

input type=”password” specifies input type is “password”, name=”secret” specifies the inputted password that will be passed to the php file for processing.

  

Submit Inputs

 
| <input type=”submit”  value=”xxx”> |
| --- |

 “submit” type is used to submit all data in the form to server.

“value” attribute specifies the characters will be displayed on a button.

## Example:

<form action=”myfile.php”  method=”post”>

<input type=”text”  name=”information”>

<input type=”submit”  value=”Send”>

</form>

(Display:

 
|  <form>………… 

 
| Send |
| --- |

</form>  |
| --- |

)

## Explanation:

input type=”submit” will submit all data in the form to server.

value=”Send” means the word “Send” shown on button.

  

Reset Inputs

 
| <input type=”reset”  value=”xxx”> |
| --- |

 “reset” type is used to clear all data in the form.

“value” attribute specifies the characters will be displayed on a button.

## Example:

<form action=”myfile.php”  method=”post”>

<input type=”text”  name=”information”>

<input type=”reset”  value=”Clear”>

</form>

(Display:

 
|  <form>………… 

 
| Clear |
| --- |

</form>  |
| --- |

 )

## Explanation:

input type=”reset” will clear all data in the form.

value=”Clear” means the word “Clear” shown on button.

  

Textarea Inputs

 
| <textarea  name=”xxx”  rows=”num”  cols=”num”> |
| --- |

“textarea” type is used to input data in a text area.

“rows” specifics the number of row.

“cols” specifics the number of column.

## Example:

<form action=”myfile.php”  method=”post”>

<textarea  name=”knowledge”  rows=”5”  cols=”10”>

 </form>

(  Display:

 
|   |
| --- |

)

## Explanation:

name=”knowledge” specifies the inputted contents that will be passed to the php file for processing.

“rows” specifies the number of row as 5.

“cols” specifies the number of column as 10.

  

Radio Inputs

 

 
| <input type=”radio”  name=”data” value=”myvalue”> |
| --- |

type=”radio” is used to input data by single choice.

name=”data” specifies the inputted contents that will be passed to the php file for processing.

value=”myvalue” specifies one of the optional contents.

## Example:

<input type=”radio”  name=”color” value=”red”>

<input type=”radio”  name=”color” value=”blue”>

<input type=”radio”  name=”color” value=”pink”>

( Display:

○　red                ○　blue             ○　pink

 )

## Explanation:

type=”radio allows you select one of the circles you like. 

name=”color” specifies the selected contents that will be passed to the php file for processing.

value=”red” specifies one of the contents that is red.

  

Checkbox Inputs

 

 
| <input type=”checkbox”  name=”data” value=”myvalue”> |
| --- |

type=”checkbox” is used to input data by multiple choice.

name=”data” specifies the inputted contents that will be passed to the php file for processing.

value=”myvalue” specifies one of the optional contents.

## Example:

<input type=”checkbox”  name=”color” value=”red”>

<input type=”checkbox”  name=”color” value=”blue”>

<input type=”checkbox”  name=”color” value=”pink”>

( Display:

□　red                □　blue             □　pink

 )

## Explanation:

type=”checkbox allows you check the box you like. 

name=”color” specifies the selected contents that will be passed to the php file for processing.

value=”red” specifies one of the contents that is red.

  

Form Works with PHP

 

 
| $data=$\_GET\[ data \]; |
| --- |

In PHP file, $data=$\_GET\[ data \]: get data from HTML form and assign to $data. (Note that form method =”get”).

.Example:

<form action=”myfile.php”  method=”get”>

<input type=”text”  name=”information”>

</form>   

( Input “Hello” in the form.)

 

<?php  // This is myfile.php

$information = $\_GET\[ information \];

echo $information;

?>

( Output:  Hello! )  

## Explanation:

In myfile.php, $\_GET\[ information \] gets the data “information” from html form, and assign to $information.

  

Form Works with PHP

 
| $data=$\_POST\[ data \]; |
| --- |

In PHP file, $data=$\_POST\[ data \]: get data from HTML form and assign to $data. (Note that form method =”post”).

## Example:

<form action=”myfile.php”  method=”post”>

<textarea name=”knowledge”  rows=”10”  cols=”5”>

 </form>

( Input “Hello World! Welcome to PHP!”.)

 

<?php  // This is myfile.php

$knowledge = $\_POST \[knowledge\];

echo $knowledge;

?>

( Output:  Hello World! Welcome to PHP! )  

## Explanation:

In myfile.php, $\_POST \[knowledge\] gets the data “Hello World! Welcome to PHP!” from html form, and assign to $knowledge.

#  

#  

#  

#  

#  

# Hour 5

 

# Dynamic Data

 

  

Date & Time

 
| date(“M  d  Y”); date( “h : i : s”); date(“D  H  A”); |
| --- |

date(“M  d  Y”) displays month, date, year.

date( “h : i : s”) displays hour, minutes, second.

date(“D  H  A”) displays Day, Hour, AM/PM

## Example:

$date = date(“M  d  Y”);

$hour = date( “h : i : s”);

$week = date(“D  H  A”);

echo $date;

echo $hour;

echo $week;

( Output:  Feb  10  2015  11:20:30  Mon  11  AM  )

##   Explanation:

 
| M: Jan-Dec || d: 01-31   || Y: YYYY |
| --- | --- | --- |
| h: 01-12 || i: 00-59 || s:  00-59 |
| D:  Mon-Sun || H:  00-23 || A:  AM or PM |

  

String Process

 

 
| strlen( ); strtoupper( ); strtolower( ); |
| --- |

strlen( ) returns a length of a string.

strtoupper( ) returns an uppercase of a string.

strtolower( ) returns a lowercase of a string.

##  

## Example:

$string=”Hello World!”;

echo strlen( $string );

echo strtoupper($string);

echo strtolower($string);

( Output:  12   HELLO WORLD!  hello world!  )

## Explanation: 

strlen( $string ) returns 12.

strtoupper($string) returns HELLO WORLD!

strtolower($string) returns hello world!  

  

Redirection of Browser

 

 
| header( “Location : $url”); |
| --- |

header( “Location : $url”) can redirect the browser  to another location.

“$url” specifies the location where to go.

##  

## Example:

<?php

$url=”http://www.myexample.com”;

header( “Location : $url”);

exit( );

?>

##  

## Explanation:

header( “Location : $url”) redirects the browser to www.myexample.com.

exit( ) can stop parsing of the code on current page.

  

Information of Visitor

 

 
| $\_SERVER\[“HTTP\_USER\_AGENT”\]; $\_SERVER\[“REMOTE\_ADDR”\]; |
| --- |

$\_SERVER \[“HTTP\_USER\_AGENT”\] can identify the browser of visitors

$\_SERVER \[“REMOTE\_ADDR”\] can record the IP address of visitors.

## Example:

$browser = $\_SERVER\[“HTTP\_USER\_AGENT”\]; 

$address = $\_SERVER\[“REMOTE\_ADDR”\];

echo $browser;

echo $address;

 ( Output:  Mozilla/x.x (compatible; MSIE 8.0)…  80.xxx.xxx.105)

## Explanation:

$\_SERVER\[“HTTP\_USER\_AGENT”\] returns the browser information of visitor.

$\_SERVER\[“REMOTE\_ADDR”\] returns the IP address of visitor.

  

Cookie

 

 
| setcookie ( “name”,  “value” ); // set cookie name and value. $\_COOKIE\[“name”\];  // get cookie value by cookie name. |
| --- |

A cookie is usually used to identify a user. It is a way to store information across multiple pages. 

## Example:

<?php   // in a.php

setcookie(“color”, “blue”);  

header(“location: b.php”);  exit( );

?>

<?php   // in b.php

$mycolor = $\_COOKIE\[‘color’\];   echo  $mycolor;

?>

(  Output:  blue )

## Explanation:

In a.php, setcookie(“color”, “blue”) sets a cookie name as color and value as blue.

In b.php, $\_COOKIE\[“color”\] gets a value blue by color.

  

Session

 
| session\_start( );  // Begin to use session $\_SESSION\[“name”\]=value;  // set session name & value. $\_SESSION\[“name”\];  // get session value by name. |
| --- |

A session is usually used to identify a user. It is a way to store information across multiple pages.

## Example:

<?php  session\_start( );    // in a.php

$\_SESSION \[“color”\] = green;

header(“location: b.php”);  exit( );

?>

<?php  session\_start( );    // in b.php

$carcolor = $\_SESSION \[“color”\];

?>

( Output:  green )

## Explanation:

In a.php, “$\_SESSION\[“color”\] = green” set a session name as color and value as green.

In b.php, $\_SESSION \[“color”\] gets a value green by color.

  

Open a File

 

 
| fopen ($filename, mode); |
| --- |

fopen ($filename, mode) opens a file or URL.

 
| Mode || Operation |
| --- | --- |
| r || open file for reading only, read from beginning. |
| w || open file for writing only, clear original content. |
| a || open file for writing only, append new content. |
| x || create a new file for writing only. |

Important Notice: If above modes with “+” sign, means opening the file for reading and writing. e.g. r+, w+, a+, x+

## Example:

$filename = “myfile.txt”;

fopen( $filename, r );

fopen( $filename, w );

## Explanation:

“fopen( $filename, r )” opens myfile.txt for reading only, and reads from the beginning.

“fopen( $filename, w )” opens myfile.txt for writing only, and clear the original contents.

  

Read a File

 

 
| fread( $openfile, length ); |
| --- |

“$openfile” specifies the opened file to read.

“length” Specifies the maximum number of bytes to read.

##  

## Example:

$filename = “myfile.txt”;

$openfile = fopen( $filename, r );

$content = fread( $openfile, 20 );

##  

## Explanation:

“fread( $openfile, 20 )” reads 20 bytes from myfile.txt, and read from beginning.

$content = fread( ) assigns the reading contents to $content.

  

Write a File

 

 
| fwrite( $openfile, “string”); |
| --- |

“$openfile” specifies the opened file to write.

“string” specifies the string to write.

 

## Example:

$filename = “myfile.txt”;

$openfile = fopen( $filename, w );

$content = fwrite( $openfile, “Hello World!” );

##  

## Explanation:

“fwrite( $openfile, “Hello World!” )” clears the original content first, and writes “Hello World!” at the beginning of specified file.

  

Close a File

 

 
| fclose ($openfile); |
| --- |

“$openfile” specifies the file that has been opened.

It is good practice to close the opened file after using that. You can release the memory, other processes may be able to use that file.

##  

## Example:

$filename = “myfile.txt”;

$openfile = fopen( $filename, r );

……

fclose( $openfile) ;

 

## Explanation:

After using the file myfile.txt, fclose( $openfile ) closes the opened file.

#  

#  

#  

#  

#  

# Hour 6

 

# MySql Basic

 

  
Select a Database

 

 
| use database-name; |
| --- |

Once you get connection with MySQL server, it is required to select a particular database to work with.

“use database-name” can select a database.

##  

## Example:

mysql>use mydatabase;

Database changed

 

## Explanation:

“mysql>” is a prompt of MySQL.

“use mydatabase” selects a database named “mydatabase”.

“Database changed” is a responded text from MySQL.

  
Create a Database

 
| create database database-name; |
| --- |

“create database database-name” can create a database.

“database-name” specifies a database name.

##  

## Example:

mysql> create database newdatabase;

Query OK,……

 

## Explanation:

“create database newdatabase” creates a database named “newdatabase”.

“Query OK,……” is a responded text from MySQL.

  

Create & show a table

 

 
| create table table-name(column type, column type,…); show tables; |
| --- |

“create table table-name” can create a table.

“column type, column type,…” specifies the column name and its data type.

“show tables” can show all tables.

##  

## Example:

mysql> create table colortable(id int, color varchar(20));

mysql> show tables;

 

## Explanation:

“create table colortable” creates a table named colortable.

“id int” specifies a column named “id”, data type as ”int”.

“color varchar(20)” specifies a column named “color”, data type as “varchar(20)”.

“show tables” can display all tables in database.

  

MySQL Data Type

 

 
| Type || Explanation |
| --- | --- |
| int || An integer  |
| decimal || A floating point number |
| date || A date in YYYY-MM-DD format |
| time || A time in HH:MM:SS format |
| year || A year in YYYY format |
| char( ) || A string of defined fixed length |
| varchar( ) || A string of defined changeable length |
| text || A string from 0 to 65535 characters |

##  

## Example:

mysql> create table colortable( id int, color varchar(20) );

 

## Explanation:

“id int”: the data type of “id” is “int”, which is an integer.

“color varchar(20)”: the data type of “color” is “varchar(20)”, which is a string of defined changeable length.

 

  

Column Name Modifiers

 

 
| Modifiers || Explanation |
| --- | --- |
| auto\_increment || automatically increase a value |
| not null || must contain data |
| unique || must be only one of its kind |
| primary key(arg) || specifies its argument as primary key |

 

## Example:

mysql> create table colortable( id int auto\_increment, 

color varchar(20) not null );

 

## Explanation:

“id int auto\_increment”: The value id can automatically increase than previous value.

“color varchar(20) not null”: The data in “color” column must be included.

  

Insert Data to Table

 

 
| insert into table-name ( column1, column 2, column3 ) values (value1, value2, value3); |
| --- |

 “column1, column 2, column3” will be respectively inserted data by “value1, value2, value3”

##  

## Example:

mysql>insert into colortable(color1, color2, color3) values(“red”, “blue”, “green”);

( Output: colortable )

 
| id || color1 || color2 || color3 |
| --- | --- | --- | --- |
| 1 || red || blue || green |

 

 

## Explanation:

The specified columns “color1, color 2, color3” will be respectively inserted data by “red, blue, green”.

  

Alter a table

 

 
| alter table table-name add column-name type; |
| --- |

New column can be added to a table by using the “alter” command.

 

## Example: 

mysql>alter table colortable add color4 varchar(20);

( Output: colortable)

 
| id || color1 || color2 || color3 || color4 |
| --- | --- | --- | --- | --- |
| 1 || red || blue || green || null |

 

## Explanation:

“add color4 varchar(20)” adds a new column named color4.

From above table, you can see the new column name is color4.

  

Update Specific Data

 

 
| update table-name set column-name=value where id=int; |
| --- |

A value can be changed in a column by its id.

 

## Example:

mysql> update colortable set color1=”yellow” where id=1;

 

( Output: colortable)

 
| id || color1 || color2 || color3 || color4 |
| --- | --- | --- | --- | --- |
| 1 || yellow || blue || green || null |

 

## Explanation:

“set color1=”yellow” where id=1” can update the value red to yellow in the row where id is 1.

  

Delete Data

 

 
| delete from table-name where id=int; |
| --- |

Some row can be deleted by using “delete” command.

##  

## Example:

mysql> delete from colortable where id=1;

( Output: colortable)

 
| id || color1 || color2 || color3 || color4 |
| --- | --- | --- | --- | --- |
|   ||   ||   ||   ||   |

 

## Explanation:

“delete from colortable where id=1” deletes all data in the row where id equals 1.

From above table, you can see there are not any data in the row where id equals 1.

  

Select Queries

 

 
| select \* from table-name; select column-name from table-name; |
| --- |

“select \* from table-name” can select all column.

“\*” represents all column.

“select column-name from table-name” can select a column.

 

## Example:

mysql> select color2 from colortable;

( Output: colortable)

 
| color2 |
| --- |
| blue |

 

## Explanation:

“select color2 from colortable” selects color2 from colortable.

 

#  

#  

#  

#  

#  

# Hour 7

 

# MySql & PHP

 

  

Connect MySql Server

 
| mysqli\_connect( “host”, “username”, “password” ); |
| --- |

“mysqli\_connect( ) lets PHP connect MySql server.

“host”: specifies a host name.

“username”: specifies a MySql user name.

“password”: specifies a MySql password.

 

## Example:

$con= mysqli\_connect( “host”, “user”, “psword” );

if( $con ) {

echo  “ Connect successfully! ”;

}

( Output:  Connect successfully! )

##  

## Explanation:

“$con=mysqli\_connect( “host”, “user”, “psword” )” try to make PHP connect MySql server. If successful, it returns true, if failed, it returns false. The result assigns to $con.

“if ( $con )” can test $con true or false.

  

Select Database

 

 
| MySqli\_select\_db( $con, “database-name” ); |
| --- |

The mysqli\_select\_db( ) is used to select a database for the connection.

“$con” is the connection of MySql server. (See previous page).

 “database-name” specifies the name of database.

## Example:

$select=mysqli\_select\_db( $con, “mydatabase” );

if( $select ) {

echo  “ Select db successfully! ”;

}

( Output:  Select db successfully! )

## Explanation:

“$select=mysqli\_select\_db( $con, “mydatabase” )” try to make PHP select MySql database. If succeed it returns true. If fail it returns false. The result assigns to $select.

“if ( $select )” can test $select true or false.

  

Insert Table Data

 

 
| $sql=”insert into table-name (columns) value (\\”values\\”)”; $query=mysqli\_query( $sql, $con); |
| --- |

$sql=”insert into table-name (columns) value (\\”values\\”)” is used to insert table data.

$query=mysqli\_query( $sql, $con) executes the query.

 “$con” is the connection of MySql server. (See previous page).

## Example:

$sql=”insert into table-name (color4) value (\\”$red\\”)”;

$query=mysqli\_query( $sql, $con);

if( $query ) {

echo  “ Insert data successfully! ”;

}

( Output: Insert data successfully! )

## Explanation:

insert into table-name (color4) value (\\”$red\\”) inserts $red to color4, mysqli\_query( $sql, $con) performs the query.

  

Alter Table Data Type

 

 
| $sql=”alter table table-name modify column data type”; $query=mysqli\_query( $sql, $con); |
| --- |

$sql=”alter table table-name modify column data type” is used to change data type of the column name.

$query=mysqli\_query( $sql, $con) executes the query.

“$con” is the connection of MySql server. (See previous page).

## Example:

$sql=”alter table colortable modify color4 char(30)”;

$query=mysqli\_query( $sql, $con);

if( $query ) {

echo  “ Alter data type successfully! ”;

}

( Output: Alter data type successfully! )

## Explanation:

“alter table colortable modify color4 char(30)” alters color4 data type to char(30), mysqli\_query( $sql, $con) performs the query.

  

Retrieve Table Data

 

 
| $sql=”select column from table-name”; $query=mysqli\_query( $sql, $con); |
| --- |

$sql=”select column from table-name” is used to retrieve table data by the column name from a table.

$query=mysqli\_query( $sql, $con) executes the query.

“$con” is the connection of MySql server. (See previous page).

## Example:

$sql=”select color1 from colortable”;

$query=mysqli\_query( $sql, $con);

if( $query ) {

echo  “ Retrieve data successfully! ”;

}

( Output: Retrieve data successfully! )

## Explanation:

“select color1 from colortable” retrieves table data by the color1 from colortable. mysqli\_query( $sql, $con) performs the query.

  

mysqli\_fetch\_row( )

 
| mysqli\_fetch\_row( ); |
| --- |

“mysqli\_fetch\_row( )” returns an indexed array of the row. Its key is always a number type.  e.g. \[ number \] => value.

## Example:  

test\_table

 
| Name || State || City |
| --- | --- | --- |
| Don || Ma || Stone |
| Kan || Nh || Water |

$sql=select \* from test\_table;  // \* represents all columns

$query=myslqi\_query( $sql);

$array=mysqli\_fetch\_row ($query);

print\_r($array);  // print\_r( ) is used to print array.

( Output:  \[0\]=>Don   

                \[1\]=>Ma  

                \[2\]=>Stone )

## Explanation:

mysqli\_fetch\_row( ) returns an array of the row, its key are always number type.

print\_r( ) is used to print array.

  

mysqli\_fetch\_assoc( )

 
| mysqli\_fetch\_assoc( ); |
| --- |

“mysqli\_fetch\_assoc( )” returns an assoc array of the row. Its key is always a string type.  e.g. \[ string \]=> value.

## Example:

test\_table

 
| Name || State || City |
| --- | --- | --- |
| Don || Ma || Stone |
| Kan || Nh || Water |

$sql=select \* from test\_table;  // \* represents all columns

$query=myslqi\_query( $sql);

$array=mysqli\_fetch\_assoc ($query);

print\_r($array);  // print\_r( ) is used to print array.

( Output:  \[Name\]=>Don

                \[State\]=>Ma

                \[City\]=>Stone)

## Explanation:

mysqli\_fetch\_assoc( ) returns an array of the row, its key are always string type.

print\_r( ) is used to print array.

  

mysqli\_fetch\_array( )

 
| mysqli\_fetch\_array( ); |
| --- |

“mysqli\_fetch\_array( )” returns both indexed and associative array of the row. Their keys are both number type and string type.  e.g. \[number\]=>value    \[ string \]=>value.

## Example:

test\_table

 
| Name || State || City |
| --- | --- | --- |
| Don || Ma || Stone |
| Kan || Nh || Water |

$sql=select \* from test\_table;  // \* represents all columns

$query=myslqi\_query( $sql);

$array=mysqli\_fetch\_array($query);

print\_r($array);  // print\_r( ) is used to print array.

( Output: 

\[0\] => Don            \[1\] => State          \[2\] => City

\[Name\] => Don    \[State\] => Ma       \[City\] => Stone )

## Explanation:

mysqli\_fetch\_array( ) returns an array of the row, their key are always both number type and string type.

  

mysqli\_num\_rows( )

 

 
| mysqli\_num\_rows( $query ); |
| --- |

mysqli\_num\_rows( $query) returns the total number of rows from $query, which is generated by mysqli\_query( ).

##  

## Example:

test\_table

 
| Name || State || City |
| --- | --- | --- |
| Don || Ma || Stone |
| Kan || Nh || Water |

$sql=select \* from test\_table;  // \* represents all columns

$query=myslqi\_query( $sql);

$row\_number=mysqli\_num\_rows( $query );

echo  $row\_number;  

( Outputs:  2 )

##  

## Explanation:

$row\_number=mysqli\_num\_rows( $query ) returns the total number of row from $query, which is 2.

  

mysqli\_close( )

 

 
| mysqli\_close( ); |
| --- |

Close a previously opened database connection to MySql server.

##  

## Example:

<?php

$con= mysqli\_connect( “host”, “user”, “psword” );

// ....some PHP code...

mysqli\_close($con);

?>

##  

## Explanation:

mysqli\_close($con) closes $con connection to the MySql server.

 

 

#  

#  

#  

#  

# Hour 8

 

# Class & Object

  

Class Definition

A class is a template for object, and creates an object.

 
| class  class-name{var $variable;function function-name ( ){ }} |
| --- |

“class class-name {……}” is used to define a class.

“var” defines a variable in class. Variable is also known as “property”. 

“function” defines a function in class. Function is also known as “method”.

## Example:

class color {

var c1; var c2;

function brightness ( ) {…}

}

## Explanation:

“class color” defines a class named “color”. “var” defines two variables named “c1” and “c2”. “function” defines a function named “brightness”.

  

$this-> variable

 

 
| $this-> variable; |
| --- |

“$this-> variable;” is used to access the variable in current class.

## Example:

class color {

var c1;

function brightness ( ) {  

$this->c1\=”red”; 

echo $this->c1;

}

}

( Output:  red )

##  

## Explanation:

“$this->c1” access the variable “c1” in current class.

“$this->c1=’red’;” assigns the value “red” to “c1”. 

  

Object Declaration

Object is an instance of a class.

 
| $object = new class-name;$object->variable;$object->function-name( ); |
| --- |

“$object = new class-name;” creates a new object named “$object”.

“$object->variable;” means that $object references a variable.

“$object-> function-name ( );” means that $object calls a function.

## Example:

$obj = new color;

$obj->c2;

$obj->brightness ( );

( Output:  red )

## Explanation:

“$obj = new color;” creates an object named” $obj”.

“ $obj->c2” means $obj references variable “c2”.

 “$obj->brightness ( );” means that “$obj” calls the function brightness( ){…}, outputs the result “red”.

  

Constructor (1)

When a function name is the same as a class name, the function is known as constructor.

Constructor is used to initialize class’s variable when create a new object.

## Example:

class color{

var c1;

var c2;

function color( $arg ) {  // This is a constructor

$this->c1= $arg;  

}  

}

$obj= new color( yellow );

## Explanation:

“function color( $arg ) {  $this-c1= $arg;  }” is a constructor.

When create an object $obj, color(yellow) calls the constructor, and passes the argument “yellow” to constructor by $arg, than $arg assigns the value to “c1”.

  

Constructor (2)

You can use \_construct( ) to work as constructor.

 
| \_construct( ); |
| --- |

Constructor is used to initialize class’s variable when create a new object.

## Example:

class color{

var c1;

function \_construct ( $arg ) {  // This is a constructor

$this-c1= $arg;  

}  

}

$obj= new color( yellow );

## Explanation:

“function \_construct ( $arg ) {  $this-c1= $arg;  }” is a constructor.

When creating an object $obj, color(yellow) calls the constructor, and passes the argument “yellow” to constructor by $arg, than $arg assigns the value to “c1”.

  

Destructor

\_destruct( ) can work as destructor to destroy an object.

 
| \_destructor( ); |
| --- |

When ending a class instance, \_destructor can be used.

## Example:

class color{

var c1;

……

function \_destructor {  // This is a destructor

echo “Using destructor…”;

}  

}

(  Output:  Using destructor…)

 

## Explanation:

“function \_destructor” is a destructor, which ends a class instance.

  

Extend Class

When a sub class extends a parent class, sub class obtains the variable and function from parent class.

 
| class sub-class extends parent-class {……} |
| --- |

##  

## Example:

class animal{

// parent class definition

}

class dog extends animal{

// sub class definition

}

class monkey extends animal{

// sub class definition.

}

## Explanation:

class dog and class monkey are two sub class, they extend their parent class “animal”, including its variable and function. 

  

The Use of Inheritance

The object of sub class can use the variable and function of parent class.

## Example:

class animal{

var $head;

function tail( ) {…}

}

class dog extends animal{

// sub class definition

}

$d = new dog( );

$d->$head = “big”;

$d->tail( );

## Explanation:

$d is an object of sub class.

“$d->$head” references a variable of parent class.

“$d->tail( );” calls a function of parent class.

  

Class:: method ( ) 

Class can use:: to references a variable or calls a function.

 
| class-name :: variable;class-name :: function( ); |
| --- |

## Example:

class animal{

var head;

function tail( ) {…}

}

class dog extends animal{

animal :: head;

animal :: tail( );

}

## Explanation:

“animal :: head;” means in sub class “dog”, a class named “animal” references a variable “head” in parent class.

“animal::tail( );” means in sub class ”dog”, a class named “animal” calls a function ”tail( )” in parent class.

#  

#  

#  

# Appendix 1

 

 

# Security Tips

  

Why Security Code?

It is very important to ensure the safety of PHP web site on Internet. There are various dangerous attacks from anonymous hackers. These risks list as following:

 
| Name || Malicious Behaviors |
| --- | --- |
| Cross-Site Scripting || Steal user information |
| Spoofed Forms || Remove client-side data |
| SQL Injection || Ruin database data  |
| Remote Code Injection || Controlled by attacker |
| Command Injection || Execute bad commands |
| Session Fixation || Set another person's SID |
| Session Hijack || Hijack user session key |
| …… || …… |

Attacker inputs malicious codes in HTML form.

<input type=”password” name= “password”>

<input type= “text” name= “characters” /> 

<textarea name = “words” rows= size1 cols= size2>

  

Filter Malicious Password

 

 
| ctype\_alnum( $\_POST\[ “password ” \]) |
| --- |

“ctype\_alnum ( )” only accepts a to z characters and 0 to 9 numbers, and returns true. Don’t allow <?, <%, <!, #, $, %, ^, &, \* and any other symbols.

## Example:

To filter malicious password, the PHP codes look like this:

$clean = array( );         // defines an array 

if ( ctype\_alnum ( $\_POST\[“password”\]))

{

$clean \[“password”\] = $\_POST\[“password”\]

}

## Explanation:

“$clean = array( );” defines an array named “$clean”.

“ctype\_alnum ( $\_POST\[“password”\])” only allows a to z and 0 to 9, and return true.

“$clean \[“password”\]” stores the characters or numbers, without other symbols such as @, #, $, %, &, <?, <%, <! …….

  

Filter Malicious Characters

 
| ctype\_alpha( $\_POST\[ “characters” \]) |
| --- |

“ctype\_alpha( )” only accepts a to z characters, and returns true. Don’t allow 0 to 9 numbers and <?, <%, <!, #, $, %, ^, &, and any other symbols.

## Example:

To filter malicious characters, the PHP codes look like this:

$clean = array( );         // defines an array 

if ( ctype\_alpha ( $\_POST\[“characters”\]))

{

$clean \[“characters”\] = $\_POST\[“characters”\]

}

## Explanation:

“$clean = array( );” defines an array named “$clean”.

“ctype\_alpha ( $\_POST\[“characters”\])” only allows a to z characters, and return true.

“$clean \[“characters”\]” stores characters only, without any numbers and other symbols such as @, #, $, %, &, <?, <%, <! …….

  

Filter Malicious Input

 
| str\_replace("ch1", "ch2 ", $\_POST \[“text”\] ) |
| --- |

“str\_replace( )” can replace character1 by charcter2 in what user have inputted.

“$\_POST\[text\]” is the text inputted by user.

##  

## Example:

$clean = array( );    // define an array

$clean\[“text”\]=str\_replace("malicious", "  ", $\_POST\[text\]);   

$clean\[“text”\]= str\_replace("@", "(at)", $\_POST\[text\]);

$clean\[“text”\]= str\_replace("%", "percent", $\_POST\[text\]);

## Explanation:

“str\_replace("script", "  ", $\_POST\[text\]” replaces “malicious” by an empty string.

“$str\_replace("@", "(at)", $\_POST\[text\]);” replaces @ by “(at)”.

“str\_replace("%", "percent", $\_POST\[text\]);” replaces % by “percent”.

$clean\[“text”\] stores the text you need.

  

Limit Specified Input

 
| in\_array( $\_POST \[“words”\], myarray ) |
| --- |

“in\_array ( )” can limit the inputted words from users. Allow specified characters or numbers that can be inputted, and returns true.

## Example:

$clean = array( );    // define an array

$myarray = array( “Rose”, “Andy”, “Judy”, “Tomy” );

if ( in\_array( $\_POST\[“words”\], $myarray ) )

{ 

$clean\[“words”\] = $\_POST\[“words”\];

}

## Explanation:

“$myarray = array( “Rose”, “Andy”, “Judy”, “Tomy” );” specifies  the inputted words that are one of the “Rose”, “Andy”, “Judy”, “Tomy” only.

“in\_array( $\_POST\[“words”\],  $myarray)” checks the inputted words if accord with the specified characters or numbers in $myarray. 

“$clean\[“words”\]” stores the specified words only.

  

Escape Output

Escape output means encoding the output so that the original meaning is preserved, which can prevents the user from potentially damaging commands.

 
| htmlentities( );htmlspecialchars( ); |
| --- |

 “htmlentities( );” and “htmlspecialchars( )” can convert characters to HTML entities in source code.

## Example:

## $str = "< © Ray >";

## echo htmlentities ( $str ); 

(   Output in source code:   &lt;&copy;Ray;&gt;     )

## Explanation

“htmlentities($str)” converts the "< © Ray \>" to html entities.

“&lt;” are html entities, meaning “<”.

“&copy” are html entities, meaning “©”.

“&gt” are html entities, meaning “>”.

htmlspecialchars( ) is almost the same as htmlentities( ).

To check the source code in IE browser: view-> source

  

Protect Database

 
| mysql\_real\_escape\_string( ) |
| --- |

“mysql\_real\_escape\_string( )” can eliminate the risk of SQL injection attacks. 

Before using MySQL query, do two things:

(1) Always use clean parameters.

(2) Always use “mysql\_real\_escape\_string(  )” to escape the output for Database, prevent SQL injection attacks.

## Example:

$mysql = array( );       //  define an array

$mysql \[ ‘product’ \] =

   mysql\_real\_escape\_string( $clean\[‘product’\] );

$sql = “SELECT \*

            FROM   catalog     // catalog is a table

            WHERE   product = ‘{ $mysql \[ ‘product’ \] }’”;

## Explanation:

 “$clean\[‘product’\]” is a clean parameter.

“$mysql \[ ‘product’ \]” has been escaped, which can be used to MySQL query. 

#  

# Appendix 2

 

MYSQL Commands

Charts

  

(1)          Database Commands

 
| MySQL Commands || Descriptions |
| --- | --- |
| CREATE DATABASE database-name || create database |
| USE database-name || use a database |
| SHOW database-name || show a database |
| DROP database-name || remove a database |

 

 

(2)         Table Commands

 
| MySQL Commands || Descriptions |
| --- | --- |
| CREATE TABLE  table-name || create table |
| SHOW TABLE || show all tables |
| DESCRIBE || show fields property |
| SHOW COLUMNS FROM table-name || show a field property |
| SHOW INDEX FROM table-name || list index field property |
| ALTER TABLE table-name || change data of a field |
| DROP TABLE table-name || remove a table |
| OPTIMIZE table-name || optimize a table |

 

  

(3)         Field Modifiers

 
| Modifier || Descriptions |
| --- | --- |
| AUTO\_INCREMENT || automatically generate a serial number |
| NUT NULL || cannot be empty value |
| NULL || can be empty value |
| UNIQUE || cannot not duplicate any entry |
| PRIMARY KEY || specify as a primary key  |
| DEFAULT || specify a default value for a field |
| INDEX || specify an index field for table |

 

(4)        Operation Commands

 
| Modifier || USE |
| --- | --- |
| SELECT field FROM table WHERE condition || query data |
| INSERT INTO table ( field ) VALUES (value) || insert data |
| DELETE FROM table WHERE condition || delete data |
| UPDATE table SET field = value WHERE condition || update data |
| PEPLACE INTO table (field ) VALUES (value) || replace data |

 

  

(5)         mysql\_xxx\_xxx (  )

 
| Commands || Description |
| --- | --- |
| mysql\_affected\_row ( ) || Returns the number of row affected by query |
| mysql\_close ( ) || Closes the connection with MySQL server |
| mysql\_connect ( ) || Creates an initial connection with MySQL server |
| mysql\_create\_db ( ) || Creates a database on the MySQL server |
| mysql\_data\_seek ( ) || Adjusts the result pointer to a random row in the results |
| mysql\_db\_query ( ) || This function was deprecated in PHP 5.3.0 |
| mysql\_error ( ) || Returns a string with the error description |
| mysql\_fetch\_array ( ) || Returns an array of strings associated with fetched row |
| mysql\_fetch\_assoc ( ) || Returns an associative array of strings of fetched row |
| mysql\_fetch\_row ( ) || Returns an indexed array of strings of the fetched row |
| mysql\_free\_result ( ) || Clears the system memory associated with the result  |
| mysql\_get\_server\_info ( ) || Returns a string with the MySQL server version |
| mysql\_num\_rows ( ) || Returns the number of rows in the result set |
| mysql\_query( ) || Submits a query to the database on the server |
| mysql\_real\_escape\_string ( ) || Escapes special characters in a string for MySQL |
| mysql\_result ( ) || Returns a string of one cell from a MySQL result set |
| mysql\_select\_db ( ) || Selects the database to use by database name |

#  

#  

#  

# Appendix 3

 

 

# 100 Tests for Interview, Answers & Explanations

 

  

Chapter 1 PHP Basic

#  

1\. Which following tags is not for PHP?

1.  <?php……?>
2.  <?......?>
3.  <script Language=”php”>……</script>
4.  <php…...>

 

(The answer & explanation is in the next page.)

  

1.  Answer: D

Explanation:

A is PHP standard tag.

B is PHP short tag.

C is PHP script tag.

D is not a PHP tag.

Note: short tag and script tag are considered deprecated and strongly not recommended.

 

 

 

2.  Which following type is not for PHP comment?

1.  //  for PHP single line comment
2.  #  for PHP single line comment
3.  (         ) for PHP multi-line comment
4.  /\*      \*/  for PHP multi-line comment

  

2\. Answer:  C

Explanation:

(      ) is not for PHP comments

 

 

3.  Which following express is not correct?

1.  a += b means  a = (a + b)
2.  a \*= b means  a = (a \* b)
3.  a != b means  a = (a ! b) 
4.  a %= b means  a = (a % b)

 

  

3\. Answer:  C

Explanation: 

 != means “not equal to”. 

About ”!b”, if the variable “b” had a value of true, then “!b” would have a value of false.

 

 

4\. Which following variable name is invalid? 

1.  $var
2.  $\_var
3.  $10var
4.  &$var

 

  

4.  Answer: C

Explanation:

PHP variable cannot start with numbers.

PHP variables always start with a dollar sign, character and underscore.

&$var is a reference to the $var variable.

Variable naming rule:

It can start with a dollar sign $.

It can start with character or underscore character.

It must not start with a number.

 

 

 

5.  Which following operator description is not correct?

1.  \+ is used in addition
2.  – is used in subtraction
3.  \* is used in multiplication
4.  % is used in division

 

  

5.  Answer:  D

Explanation:  

% is used in modulus.  /  is used in division.

 

 

6.  Which following statement is not correct?

$num=1:

echo $num++; // line 1, output 1, $num now equals to 2.

echo ++$num; // line 2, output 3, $num now equals to 3.

echo $num- -; // line 3, output 3, $num now equals to 2.

echo - -$num; // line 4, output 2, $num now equals to 1.

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

6\. Answer:  D

Explanation:

It should be: echo - -$num; // line 4, output 1, $num now equals to 1.

$num++      returns current value, and then plus 1.

++$num      current value plus 1, then returns new value.

$num- -       returns current value, and then minus 1. 

\- -$num       current value minus 1, then returns new value.

 

 

7.   Which following statement is not correct?

$x=0; echo ~$x;       // line 1 outputs -1.

$x=0; echo ~$x;       // line 2 outputs 1.

$x=1; echo $x<<1;   // line 3 outputs 2.

$x=8; echo $x>>1;   // line 4 outputs 4.

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

7.  Answer:  B

Explanation:

“~” is a bitwise operator “binary not”, which negates all the bits of an integer number.

<< Bitwise left shift.  $x<<n means:   x multiples 2n

\>> Bitwise right shift.  $x>>n means:   x divides 2n

 

 

8.  Which following declaration of variable is correct?

1.  string $str=”PHP”;
2.  int $num=100;
3.  boolean $boo=true;
4.  $var=3E-10;

 

  

8\. Answer:  D

Explanation:

Data type is not used to declare a variable.

 

 

9.  When the value of Boolean variable is False, which following number can be a substitute? 

1.  \-1
2.  0
3.  1
4.  Not all above.

  

9\. Answer: B

Explanation:

Boolean value is 1, meaning true.

Boolean value is 0, meaning false.

 

 

10.  If you don’t want the client browser to show the error information of PHP running, which following configuration should be set as “off” in php.ini?

1.  show\_errors
2.  log\_errors
3.  display\_errors
4.  view\_errors

  

10.  Answer:  C

Explanation:

For security reasons, you should set display \_errors as “off” in php.ini. 

B is used to record the errors to the log file.

A and D are not the configuration of php.ini.

 

 

11.  What is the output in the following code?

<?php

$var=”I like PHP!”;

$new\_var=&$var;

$new\_var=”PHP is very good!”;

echo $var;

?>

1.  I like PHP!
2.  PHP is very good!
3.  I like PHP! PHP is very good!
4.  PHP is very good! I like PHP!

  

11.  Answer:  B

Explanation:

“&” is used to references a variable.

By reference, the left-hand operand becomes “connected ” with the right-hand one, “&” can reversely assign the value. 

For example:

$a=100;

$b=&$a;

$b=200;

echo $a;          // outputs 200

 

 

12.  Which following statement is not correct?

1.  \\n can be used to move to a new line.
2.  \\t can be used to tab across a text area.
3.  \\” can be used to show ” symbol.
4.  \\$ can be used to show a variable value.

  

12.  Answer:  D

Explanation:

\\$ can be used to show $ symbol.

 

 

13.  What is the output in the following code?

<?php

$num=10;

function test( ) { echo $num; }

test( );

?>

1.  10
2.  0
3.  no output
4.  running failure

 

  

13.  C

Explanation:

Local variable $num inside the function test ( ) has not assigned any new value.

It should be changed the local variable as “global $num;”. For example:

<?php

$num=10;  

function test( ) { global echo $num; }  

test( );

?>

The output is 10.

 

 

14.  Which following line is not correct?

<?php

function test( ) {

static $var=sqrt(121);   // line 1

$str=”OK”;                   // line 2

static $int=10;               // line 3

echo $int;                      // line 4

}

?>

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

14.  Answer:  A

Explanation:

“static” cannot define an expression. For example:

static  $int=100+200;  // error

“static” only defines a variable.

 

 

15.  What is the output in the following code?

$str=”test”;

$num=int($str);

echo ++$num;

1.  test
2.  0
3.  1
4.  no output

 

  

15.  Answer:  C

Explanation:

Because the string “test” is first converted to the integer number 0, and then increase 1.

 

 

16.  Which following statement is not correct?

1.  Because the echo( ) is so frequently used, the PHP parser allows it parentheses to be omitted.
2.  PHP variable names are case-sensitive. Therefore, $var and $VAR are treated as different variable.
3.  When assigning numeric values to a variable, they should not be enclosed in quotes. Otherwise, they will be treated as string values.
4.  Using the .\= operator with numbers will plus them. Therefore, 9.\=6 means 15.

  

16.  Answers:  D

Explanation:

Using the .\= operator with numbers will concatenate them. Therefore, 9.\=6 means 96 instead of 15.

 

 

17.  What is the output of the following code?

define (‘NUM’, ‘100’); 

$number=NUM;

echo  gettype ($number);

1.  number
2.  string
3.  boolean
4.  integer

  

17\. Answer:  B

Explanation:

The constant NUM and ‘100’ are strings (notice the single quotes), which is assigned to the $number. Therefore, $number is a string.

 

 

18.  What is the output in the following code?

$num=100;

(boolean) $num;

echo $num;

1.  1
2.  0
3.  true
4.  100

  

18.  Answer:  D

Explanation:

The cast to Boolean creates a converted same value stored in $num. In fact, it does not change the value stored there.

 

 

19.  What is the output in the following code?

$str1=”apple”;

$str2=”Apple”;

echo (int)($str1>$str2);

1.  true
2.  false
3.  1
4.  0

  

19.  Answer:  C

Explanation:

Because the ASCII value of the character “a” (97) is higher than that of the character “A” (65). Therefore, “apple”  is greater than “Apple”. 1 represents true.

 

 

20.  Which operator precedence is higher?

1.  ||
2.  &&
3.  ! 
4.  ++

  

20.  Answer:  D

Explanation:

The operator precedence of “++” is higher than other three operators.

The order of operator precedence is: ++>!>&&>||.

 

 

21.  What is the output in the following code?

<?php

$arr=array(5=>”100”, “101”, “102”, “103”, 10>=”105”);

echo $arr\[9\];

?>

1.  “9”
2.  “104”
3.  “0”
4.  null

  

21\. Answer:  C

Explanation:

When a string array element has not been assigned any value yet, the default value is zero string. 

The value of $arr\[5\] is “100”.

The value of $arr\[6\] is “101”.

The value of $arr\[7\] is “102”.

The value of $arr\[8\] is “103”

The value of $arr\[9\] is “0”.

The value of $arr\[10\] is “105”.

 

 

22.  What is the output in the following code?

$arr=array(“A”, “B”, “C”,);

array\_unshift($arr, “D”, “E”,);

array\_push($arr, “F”, “G”);

foreach ($arr as $value)

{ 

each $value;

}

1.  FGABCDE
2.  DEABCFG
3.  DEABC
4.  ABCFG

 

  

22\. Answer: B

Explanation: 

Additional elements can be added at the beginning of an array by array\_unshift( ), and elements can added at the end of an array by array\_push( ).

 

 

23.  What is the output in the following code?

$arr=array(“A”,”B”,”C”);

$first=array\_shift($arr);

$last=array\_pop($arr);

echo ($first+$last);

1.  A
2.  B
3.  C
4.  AC

  

23.  Answer:  D

Explanation:

The first element in an array can be removed by the array\_shift( ), and the last element can be removed by the array\_pop( ).

 

 

24.  Which following statement can get the size of an array size?

1.  count($array)
2.  size($array)
3.  length($array)
4.  $array.length

  

24.  Answer:  A

Explanation:

count( ) can be used to determine the total number of elements in an array.

Notice that sizeof( ) is an alias of the count( ).

 

 

25.  What will the $arr array contents be after running following code?

<?php

$arr=array(1,2,3);

foreach($arr as $k=>$v)

{ 

$v+=1;

 }

?>

1.  array(1,2.3)
2.  array(2,3,4)
3.  array(3,4,5)
4.  array(4,5,6)

  

25.  Answer:  A

Explanation:

The foreach construct operates on a copy of $arr, therefore, no changes are mad to its original values.

 

 

26.  What will the $arr array contents be after running following code?

<?php

$arr=array(1,2,3);

foreach($arr as $k=>&$v)

{ 

$v+=1;

 }

?>

1.  array(1,2.3)
2.  array(2,3,4)
3.  array(3,4,5)
4.  array(4,5,6)

  

26.  Answer:  B

Explanation: 

“&” assignment operator works by reference. 

Modifying the contents of the array directly by assigning the value of each element to the iterated variable should be by reference rather than by value. 

 

 

27\. Which following statement is not correct?

$arr1=array(2,4,6,8);

$arr2=array(1,3,6,7);

$arr3=array\_merge($arr1,$arr2);

$arr4=array\_unique($arr1,$arr2);

$arr5=array\_intersect($arr1,$arr2);

$arr6=array\_flip($arr5);

1.  The element of $arr3 is: 2,4,6,8,1,3,6,7
2.  The element of $arr4 is: 1,2,3,4,6,7,8
3.  The element of $arr5 is: 6
4.  The element of $arr6 is: 1

  

27.  Answer:  D

Explanation:

The element of $arr6 should be 0.

array\_flip( ) will exchange key and value, key will become value, value will become key. For example:

$arr5\[0\]=6;

$arr6=array\_flip($arr5);  

After running array\_flip( ), you will get a result $arr5\[6\]=0;

Therefore, the element of $arr6 should be 0.

 

 

28\. Which following statement is not correct? 

1.  assort( ) is used to sort an associative array by value.
2.  rsort( ) is used to sort array in reverse order by value.
3.  ksort ( ) is used to sort an array by key. 
4.  usort ( ) is used to sort an array using a user-defined comparison function by key.

  

28.  Answer:  D

Explanation:

usort ( ) is used to sort an array using a user-defined comparison function by values, instead of by key.

 

 

29.  Which following statement is not correct?

1.  echo( ) doesn’t return value.
2.  print ( ) returns value.
3.  echo( ) can be used  as part of an expression.
4.  print( ) can be used as part of an expression.

 

  

29.  Answer:  C

Explanation:

echo( ) cannot be used  as part of an expression.

 

 

30.  Which following line is not correct?

define(‘EMAIL’, ‘xxx@xxx.net’); // line 1

define(‘1CONSTON’, ‘value’); // line 2

define(‘BOOL’, false); // line3

echo BOOL; //line 4

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

30.  Answer:  B

Explanation:

Constant names usually use upper-case names, which follow the same variable naming requirements except $.

Constant naming rule:

It can start with a letter.

It can start with an underscore character.

It must not start with a number.

 

  

Chapter 2 Statements

 

1.  Which statement can best represent the following “if” conditionals?

if(100==$var)

{echo ’Yes’;}

else

{echo ‘No’;}

1.  A while statement
2.  A for loop statement
3.  A switch statement without a default case
4.  (test-expression)?(if-true-do-this):(if-false-do-this))

  

1\. Answer: D

Explanation:

The code above would be equivalent to the following:

echo 100==$var ? “Yes” : “No”;

 

 

2.  Which statement can best represent the following “if” conditionals?

$num=1;

if ($num==0) { //if true do this.}

elseif ($num==1) { //if true do this.}

else { // will only be executed if not other conditions are met}

1.  A while statement
2.  A for loop statement
3.  A switch statement with a default case
4.  (test-expression)?(if-true-do-this):(if-false-do-this))

  

2\. Answer:  C

Explanation:

The code above would be equivalent to the following:

$num=1;

switch($num) {

case 0: // compare to 0; break;

case 1: // compare to 1; break;

default: // executed if no other condition are met; break;

}

 

 

3.  What is the difference between include ( ) and require ( ) when the specified file missing?

1.  Include ( ) generates an error and the script stop running, require ( ) generates a warning and the script continue running.
2.  Include ( ) generates a warning and the script stop running, require ( ) generates an error and the script continue running.
3.  Include ( ) generates a warning and the script continue running, require ( ) generates an error and the script stop running.
4.  There are no any different between include ( ) and require ( ). 

  

3\. Answer:  C

Explanation:

When a necessary file missing: 

Include ( ) generates a warning and the script continue running, require ( ) generates an error and the script stop running.

 

 

4.  What is the best way to iterate through an array $arr and modify its element?

<?php

$arr = array (“A”, “B”, ”C”, “D”, “E”);

?>

1.  by a foreach loop
2.  by for loop
3.  by a while loop
4.  by a do-while loop

  
4\. Answer:  B

Explanation:

for loop is suitable to iterate through an array and modify its element.

foreach is not suitable to modify the element of an array.

while loop and do-while loop are not suitable to iterate through an array.

 

 

5.  What is the output in the following code?

$num=0; $result=” ”;

while ($num<5) {

$num++;

if ($num==3) continue;

$result .\= ”$num”;

} echo { $result };

1.  3
2.  1 2 3
3.  1 2 4
4.  1 2 4 5

  

5.  Answer:  D

Explanation:

When $num equals to 5, the while loop will stop, and output the result.

When the test condition is true, the “continue” statement immediately stops the current iteration of the loop, and then goes on next iteration until the loop ends. 

 

 

6.  Which following line is not correct?

function &test( )  // line1

{

return “Here is a string”; // line 2

}

test( ); // line 3

echo “End”; // line 4

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

6.  Answer:  B

Explanation:

Notice that function declaration uses a “&” symbol in line 1.

Functions can be declared so that they return by reference; you must return a variable, instead of returning a string or an expression by reference.

Line 2 returns a string, therefore, it is wrong.

 

 

7.  What is the output in the following code?

function test( ){

if (func\_num\_args( ) >0){

$argument=func\_get\_arg(1);

echo “Red  $argument”; }

}

test (“Blue Car”);

1.  Red Car
2.  Blue Car
3.  Red Blue Car
4.  No output

  

7.  Answer:  A

Explanation:

func\_num\_args( ) will return the total number of arguments passed to the function.

func\_get\_arg(number) will return an specified item from the argument list;

func\_get\_arg(0)  // returns the first argument .

func\_get\_arg(1)  // returns the second argument.

 

 

8.  Which following statement is not correct?

1.  trim( ) removes whitespace from the beginning and end of a string.
2.  ltrim( ) removes whitespace from the beginning of a string.
3.  rtrim( ) removes whitespace from the end of a string.
4.  mtrim( ) removes whitespace from the middle of a string.

  

8\. Answer:  D

Explanation:  

PHP has no mtrim( ) function.

 

 

9.  What is the output in the following code?

<?php

$str = ‘javascript’;

echo $str {6};

?>

1.  c
2.  r
3.  i
4.  script

  

9.  Answer:  B

Explanation:

Note that offset counting begins at 0, not 1.

$string{number} specifies the offset of the character to be retrieved within curly braces, after the variable name.

 

 

10.  Which following statement is not correct?

1.  explode( ) splits a string into array elements.
2.  implode( ) joins array elements into a string.
3.  shuffle( ) randomly rearranges the sequence of elements in an array.
4.  range ( ) returns a range of an array index.

  

10.  Answer:  D

Explanation:

range( ) generates a new array containing the range of  its values, not index. For example:

$array=range(1, 100);  /\* Generates a new array containing all the values from 1 to 100. \*/ 

 

 

  

Chapter 3 Array

 

1\. Given:

$array = array (5 =>100);

$array\[ \] = ‘ok’;

What is the key of $array array?

1.  0
2.  ok
3.  6
4.  not sure

  

1.  Answer:  C

Explanation:

The $array now have a key of 6.

When a new element is added to an array without a key, it will be plus one to the greatest numeric key already in existence in the original array.

 

 

2.  Which following function is best way to print arrays?

1.  echo ( )
2.  print ( )
3.  printf ( )
4.  var\_dump ( ) or print\_r( )

 

  

2.  Answer:  D

Explanation:

var\_dump ( ) or print\_r( ) is suitable to output arrays.

print( ) is used in expression, with return type.

echo( ) is not used in expression, without return type.

printf ( ) is used in generating formatted output.

 

 

3.  Which following statement cannot create a new array?

1.  $arr=array (1,2,3);
2.  $arr=array {‘a’=>1, ‘b’=>2, ‘c’=>3};
3.  $arr=array (1=>”1st”,”2nd”,”3rd”);
4.  $arr=array ( );

  

3.  Answer:  B

Explanation:

$arr=array {‘a’=>1, ‘b’=>2, ‘c’=>3} cannot create an array because of { }, you should use ( ) instead of { }.

 

 

4.  Which following line returns true?

$arr1=array (10, 20, 30);

$arr2=array (2=>30, 1=>20, 0=>10);

$arr3=array (‘a’=>10, ‘b’=>20, ‘c’=>30);

var\_dump ($arr1==$arr2); // line1

var\_dump ($arr1===$arr2); // line2

var\_dump ($arr1==$arr3); // line3

var\_dump ($arr1===$arr4); // line4

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

4.  Answer:  A

Explanation:

\== returns true if two arrays contain the same key/value pairs.

\=== returns true if two arrays contain the same key/value pairs, and the same order, same data type.

 

 

5.  Which following line returns true?

$arr= array(‘a’=>10, ‘b’=20);

echo isset($arr\[‘c’\]); // line 1

echo array\_key\_exists(‘0’, $arr);  // line 2

echo in\_array(30, $arr);  // line 3

echo is\_array($arr); // line 4

1.  line 1
2.  line 2
3.  line 3
4.  line 4

 

  

5\. Answer:  D

Explanation:

is\_array( ) checks whether a variable is an array.

isset( ) checks whether an element with the given key exists.

array\_key\_exists( ) checks whether a key exists in an array.

in\_array( ) checks whether a value exists in an array.

 

 

6.  What is the output in the following code?

<?php

echo strtr("Hilla Warld","ia","eo");

?> 

1.  ia
2.  eo 
3.  Hilla Warld
4.  Hello World

  

6.  Answer:  D

Explanation:

The strtr() function replaces certain characters in a string.

In here, “i” is replaced as “e”, “a” is replaced as “o”.

 

 

7.  What is the output in the following code?

$str1= “123456789”;

$str2 = “56”;

echo strstr(str1, $str2);

1.  1234
2.  123456
3.  56789
4.  56

  

7.  Answer:  C

Explanation:

The strstr() function searches for the first occurrence of a string inside another string.

In here, find the first occurrence of "56" inside "123456789" and return the rest of the string.

 

 

8.  What is the output in the following code?

$str1= “123456789”;

$str2 = “56”;

echo strpos (str1, str2);

1.  3
2.  4
3.  5
4.  6

  

8.  Answer:  B

Explanation:

The strpos() function searches the position of the first occurrence of a string inside another string.

In here, finds the position of the first occurrence of "56" inside the string.

 

 

9.  What is the output in the following code?

function test(&$str2){

$str2 .\= ‘World’;

}

$str1 = ‘Hello ’;

test ($str1);

echo $str1;

test()

1.  Hello
2.  World
3.  Hello World
4.  No output

  

9.  Answer:  C

Explanation:

Note that there is a “&” symbol in the argument of the function.

If you want the argument sent by reference, you can use “&”.

“&” can reversely assign the value. e.g. str1=str2.

 

 

10.  Which following output format is not correct?

Assume the date and time now: November 18 2015 18:30:50.

$now1=date(“M  j, Y”);  

$now2=date(“m.d.y”);   

$now3=date(“g:i a”);     

$now4=date(“H:i:s”);     

1.  echo $now1; // output:  Nov 18, 2015
2.  echo $now2;  // output: 11.18.15
3.  echo $now3;  // output:  6: 30 pm
4.  echo $now4;  // output:  06:30:50

  

10.  Answer:  D

Explanation:

It should output 18:30:50.

Because “H” in date(“H:I:s”) means hour in 24-hour format (00-23).

 

 

  

Chapter 4  Dynamic Data

 

1.  Which following statement is not correct?

1.  strcmp( ) compares two strings with case-sensitive.
2.  strcasecmp( ) compares two strings with case-insensitive.
3.  str\_compare ( ) compares two strings from a specified start position.
4.  substr\_compare ( ) compares two strings from a specified start position.

  

1.  Answer:  C

Explanation:

PHP has no str\_compare( ).

Note that substr\_compare( ) is binary-safe and optionally case-sensitive.

 

 

2.  What is the output in the following code?

<?php

echo str\_replace ("morning", "evening", "Good morning!");

?>

1.  morning
2.  evening
3.  Good morning!
4.  Good evening!

 

  

2.  Answer:  D

Explanation:

str\_replace (find, replace, string) replaces some characters with some other characters in a string.

str\_replace ("morning", "evening", "Good morning!") replaces the characters "morning" in the string "Good morning!" with "evening"

 

 

3.  What is the output in the following code?

<?php

echo substr\_replace("Good", "Morning!",0);

?>

1.  Good
2.  Morning!
3.  0
4.  Not sure

  

3.  Answer:  B

Explanation: 

substr\_replace(string, replacement, start) replaces a part of a string with another string. Argument “start” specifies where to start replacing in the string.

echo substr\_replace("Good", "Morning!",0) replace "Good" with "Morning!". “0” will start replacing at the first character in the string. 

 

 

4.  What is the output in the following code?

<?php

echo substr("Good Morning!",5);

?>

1.  Good
2.  Morning!
3.  Good
4.  Not sure

  

4.  Answer:  B

Explanation:

The substr(string, start, length) function returns a part of a string. Argument “start” specifies where to start in the string.

In here, substr("Good Morning!",5) returns "Morning!" from the string. “5” specifies where to start in the string.

 

 

5.  Which specifier is not used in the printf( )?

1.  %s outputs a string.
2.  %f  outputs a floating- point number.
3.  %d outputs a decimal number.
4.  %h outputs a hexadecimal number.

  

5.  Answer:  D

Explanation:

You should use % x or %X instead of %h.

%x outputs a number as hexadecimal with lowercase letters.

%X outputs a number as hexadecimal with uppercase letters.

 

 

6.  Which following output is not correct?

1.  printf(“%05d”, 68); // output: 68000
2.  printf(“%\*5.2f, 12.345”);  // output: \*\*\*12.35
3.  printf(“%o”, 100);  // output: 144
4.  printf(“%x”, 100);  // output: 64

  

6.  Answer:  A

Explanation:

It should be 00068. 

If the output occupies fewer characters than the total, zeroes will fill the difference.

 

 

7.  Which following statement is not correct about Regular Expressions?

1.  ^ matches the start of the string.
2.  $ matches the end of the string.
3.  \\w matches the whitespace character.
4.  \\d matches the any digit.

  

7.   Answer:  C

Explanation:

\\w matches any word character.

\\s matches any whitespace character.

 

 

8.  Which following statement is not correct about Regular Expression?

1.  \* means that the character can appear zero or more times.
2.  \+ means that the character can appear one or more times.
3.  ? means that the character can appear zero or one times.
4.  {x,y} means that the character can appear x times or y times.

  

8.  Answer:  D

Explanation:

{x,y} means that the character can appear at least x times, an no more than y times.

 

 

9.  Which following line is not correct?

<form action=”myfile.php” method=”post”> // line 1

<input type=”text” name=”username”>  // line 2

</form>

<?php  // myfile.php

$username=$\_GET\[‘username’\];  // line 3

echo $username;  // line 4

?>

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

9.  Answer:  C

Explanation:

It should be $username=$\_POST\[‘username’\];  

Because submission method is “post” in line 1, instead of “get”.

If the submission method is unknown, the values can be referenced from the special $\_REQUEST\[ \] array.

 

 

10.  Given:

<form method=”post” action=”?”>

If you want current file as an action file, which following environment variable should use?

1.  $\_ENV
2.  $\_SERVER\[‘PHP\_SELF’\]
3.  $HTTP\_SERVER\_VARS\['HTTP\_HOST’\]
4.  $\_FILES

  

10.  Answer:  B

Explanation:

Calling $\_SERVER\[‘PHP\_SELF’\] can reload the current page. 

You can set the action file like this:

$self=$\_SERVER\[‘PHP\_SELF’\];

<form method=”post” action=“<?php $self ?>”>

Then, the action file is the current file.

 

  

Chapter 5  File Process

 

1.  The fopen(fileName, operatingMode) requires two argument : the file name and an operating mode. Which following statement is not correct in the following operating mode?

1.                                                                                           r+ opens the file for reading and writing, puts the pointer at the beginning of the file.
2.                                                                                           w opens the file for writing only, puts the pointer at the beginning of the file, and truncates it to zero length.
3.                                                                                           a + opens the file for reading and writing, puts the pointer at the beginning of the file.
4.                                                                                           x+ creates a new file for reading and writing.

  

1.  Answer:  C

Explanation:

a + should puts the pointer at the end of the file, instead of the beginning of the file.

 

 

 

2.  Which following line is not correct?

$filename=”myFile.txt”;

$file=fopen($filename, “r”);  // line 1

$filesize=filesize($file);  // line 2

$test=fread($file, $filesize);  // line 3

fclose($file);  // line 4

1.                                                                                           line 1
2.                                                                                           line 2
3.                                                                                           line 3
4.                                                                                           line 4

  

2.  Answer:  B

Explanation:

It should be $filesize=filesize($filename);  

The argument of filesize($filename) should use the $filename variable.

fopen( ) opens file. fread( ) reads file. fclose( ) closes file.

 

 

3.  To record the IP address of visitors to the web page, use\_\_\_\_\_\_.

1.                                                                                           $\_SERVER\[‘HTTP\_REFERER’\]
2.                                                                                           $\_SERVER\[‘PHP\_SELF’\]
3.                                                                                           $\_SERVER\[‘HTTP\_USER\_AGENT’\]
4.                                                                                           $\_SERVER\[‘REMOTE\_ADDR’\]

  

3.  Answer:  D

Explanation:

$\_SERVER\[‘REMOTE\_ADDR’\] can record the visitor’s IP address.

$\_SERVER\['HTTP\_REFERER'\] returns the complete URL of the current page.

$\_SERVER\['PHP\_SELF'\] returns the filename of the currently executing script. 

$\_SERVER\[‘HTTP\_USER\_AGENT’\] can identify the user’s browser.

 

 

4\. Which following line is not correct?

<?php

echo “Hello World!”; // line 1

$location=”http://www.example.com”; // line 2

header('Location:$location');  // line 3

exit( );  // line 4

?>

1.                                                                                           line 1
2.                                                                                           line 2
3.                                                                                           line 3
4.                                                                                           line 4

  

4.  Answer:  A

Explanation:

Important notice: The header( ) function must appear at the very start of the page, before any content is sent to the browser. Namely the header() must be called before any actual output is sent. Otherwise, it will cause an error.

 

 

5.   Which of the following functions get the entire contents of a file in such a way that it may be used as part of an expression?

1.                                                                                           fopen( )
2.                                                                                           feadfile( )
3.                                                                                           fgets( )
4.                                                                                           file( )

  

5.  Answer:  D

Explanation:

file( ) function can get the entire contents of a file in such a way that it may be used as part of an expression.

fopen( ) opens a file.

fgets() function returns a line from an open file.

readfile( ) reads whole file to output buffer, but it cannot be used as part of an expression.

 

 

6.  Which following line is not correct?

Given: <input type=”file” name=”FileUpLoad” size=”50”>

<?php echo $\_FILES\[‘FileUpLoad’\]\[‘name’\];?>  // line1

<?php echo $\_FILES\[‘FileUpLoad’\]\[‘length’\];?>  // line 2

<?php echo $\_FILES\[‘FileUpLoad’\]\[‘type’\];?>  // line 3

<?php echo $\_FILES\[‘FileUpLoad’\]\[‘error’\];?>  // line 4

1.                                                                                           line 1
2.                                                                                           line 2
3.                                                                                           line 3
4.                                                                                           line 4

  

6.  Answer:  B

Explanation:

The argument should be “size” instead of “length”.

<?php echo $\_FILES\[‘FileUpLoad’\]\[‘size’\];?> is correct. It can get the size (in bytes) of the file.

 

 

7.  The setcookie( ) function sets one cookie at a time and need six arguments.:

setcookie(Name, Value, Expiry, Path, Domain, \_\_\_\_\_\_\_\_);

1.                                                                                           IP
2.                                                                                           URL
3.                                                                                           Security 
4.                                                                                           Browser

  

7.  Answer:  C

Explanation:

It should be:

 setcookie(Name, Value, Expiry, Path, Domain, Security);

If Security is set to 1, it means using HTTPS.

If Security is set to 0, it means using HTTP.

 

 

8.  Which following line is not correct?

<html>

<body>

<?php

session\_start( );  // line 1

$\_SESSION\["favcolor"\] = "green";  // line 2

echo "Session variables are set.";  // line 3

echo $\_SESSION\['favcolor'\];?>  // line 4

?>

</body>

</html>

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

8.  Answer:  A

Explanation:

Note: The session\_start() function must be the most first line in your document. Place before any HTML tags.

 

 

9.  Which following line is not correct?

<?php 

session\_start ( );  // line 1

&\_SESSION\[“ok”\] = $\_GET\[“ok”\];  // line 2

$self=$\_SERVER\[‘PHP\_SELF’\];  // line 3

?>

<form action=”<?php ($self); ?>” method=”post”>

<input type=”text” name=”ok”>  // line 4

</form>

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

9.  Answer:  B

Explanation:

$\_GET\[“ok”\] is wrong.

It should be $\_POST\[“ok”\], because of method=”post” in form declaration.

 

 

10.  Which following statement is not correct about the difference between cookies and sessions?

1.  cookies store data on the client system, while sessions store data on the server.
2.  cookies cannot store critical data, while session can store critical data.
3.  cookies do not use much more server resource to store data, while sessions do.
4.  cookies do not require the allowance of the user’s browser to store data, while sessions do.

  

10.  Answer:  D

Explanation:

cookies require the allowance of the user’s browser to store data.

sessions do not require the allowance of the user’s browser to store data.

 

  

Chapter 6  Class & Object

 

 

1\. To define a class, use\_\_\_?

1.  define class class-name { }
2.  new class class-name { }
3.  create class class-name { }
4.  class class-name { }

 

 

  

1.  Answer: D

Explanation:

To declare a class, using class class-name { }. For example: 

class myClass {

// define properties 

// define methods

}

 

 

2.  To instantiate an object, use\_\_\_\_?

1.  myClass $myInstance = create myClass ( ); 
2.  $myInstance = create myClass ( );
3.  myClass $myInstance = new myClass( );
4.  $myInstance = new myClass ( );

  

2.  Answer:  D

Explanation:

To instantiate an object, use $myInstance = new myClass ( ); For example: 

class color {

$blue = new color( );

$red=new new color( );

}

 

 

3.  To call a method by an object, use\_\_\_?

1.  $obj=>myMethod( );
2.  $obj->myMethod( );
3.  $obj.myMethod( );
4.  $obj:myMethod( );

  

3.  Answer:  B

Explanation:

\-> symbol is used to call a method or reference a variable.

For example:

$obj-> myFunction( );

$obj->myVar=100;

 

 

4.  Which following line is not correct?

Class A {

     function display( ){

     echo “Shows A”;  // line 1

      }

}

Class B extends A{

      function display( ){  // line 2

      echo “Shows B”;  // line 3

      } 

A->display( );  // line 4

 

}

1.  line 1
2.  line 2
3.  line 3
4.  line 4

 

  

4.  Answer:  D

Explanation:

It should be:  A::display( );

When calling a same name method in parent class from a sub class, use :: symbol.

If using a class name calls a method, you can use:

 “class-name:: method( );”

The output of above code:  Shows B   Shows A

 

 

5.  Which following line is not correct?

Class myClass

{

$myVar=”123”  // line 1

function myFunction ( )  // line 2

{

$value=$this->myVar;  // line 3

 echo “$value”;  // line 4

 }

}

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

5.  Answer:  A

Explanation:

When defining a variable inside class, “var” should be used.

For example:

class color{ 

var $ed;

var $blue;

}

 

 

6.  Which following line is not correct?

class myClass{ 

var $myVar;  // line 1

function myClass ($temp)  // line 2

{

$obj->myVar = $temp;  // line 3

}

}

$obj = new myClass (“ok”);  // line 4

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

6\. Answer:  C

Explanation:

It should be:  $this->myVar = $temp;

When using var or method inside a class, “$this” should be used to reference a var or call a method.

 

 

7.  Which following code can be use to define a variable inside a class?

1.  variable
2.  define
3.  set
4.  var

  

7.  Answer:  D

Explanation: 

Inside a class, you should use “var” to define a variable.

For example: class myClass { var $myVariable;… }

 

 

8.  Which follow code can reference a variable or call a function inside a class?

1.  $reference->
2.  $this->
3.  $call->
4.  $object->

  

8.  Answer:  B

Explanation:

“$this” should be used to reference a variable or call a method inside a class.  For Example:

class myClass{ var $name=”abc”;}   $this->abc;

 

 

9.  Which following keyword can be used to inherit a parent class?

1.  succeeds
2.  follows
3.  expands
4.  extends

 

  

9.  Answer:  D

Explanation:

It should use “extends”. When a defined class extends another class, it needs “extends”, to follow a parent class.

For example:

class sub-class extends parent-class { … }

 

 

10.  When calling a same name function in parent class from a sub class, which following keyword can be used?

1.  super::
2.  superior::
3.  parent::
4.  senior::

 

 

  

10.  Answer: C

Explanation:

“parent” can express parent class.

If using a class name calls a method, you can use:

 “class-name:: method( );”

 

For example:

class A{

function test( ){ 

echo “ok”;

}

}

class B extends A{ 

function test( ){ 

parent::test( );//call a same name function in parent class.

}

}

  

Chapter 7  MySQL

 

 

1\. Which following command can create a new database?

1.  create database database-name;
2.  create database-name;
3.  new database database-name;
4.  new database-name;

 

  

1.  Answer:  A

Explanation:

To create a new database, use command “create database database-name;”   For example:

mysql> create database myDatabase;

 

 

2.  Which following command can select a database to work with?

1.  select database-name;
2.  open database-name;
3.  use database-name;
4.  run database-name;

  

2.  Answer: C

Explanation:

 To select a database to work with, use command “use database-name”.  For example:

mysql>use myDatabase;

 

 

3.  Which following command can create a database table?

1.  create table-name;
2.  create table table-name;
3.  new table-name;
4.  new table table-name;

 

  

3.  Answer:  B

Explanation:

To create a database table, use command “create table table-name;” For example:

mysql>create table myTable;

 

 

4.  Which following statement is not correct about MySql data types?

1.  int: An integer from -2147483648 to 2147483647
2.  date: A date with format of YYYY-MM-DD 
3.  text: A string with length from 1 to 65535 characters.
4.  char( ): A string of defined variable length up to 255 characters long.

  

4\. Answer: D

Explanation: 

char( ) means a string with defined fixed length from 1 to 255 character long. For example: char(90) pads a smaller string to make it 90 characters long.

varchar( ) means a string of defined variable length from 1 to 255 characters long with padding.

 

 

5.  Which follow word is not a MySql table modifier?

1.  null
2.  unique
3.  auto\_increment
4.  primary key( )

 

  

5.  Answer:  A

Explanation: 

“null” is not a MySql table modifier. It should be “not null”. For example:

mysql> create table myTable( 

id int auto\_crement, 

data1 char (30) not null, 

data2 varchar(30) not null, 

primary key(id) 

);

 

 

6.  Which following command is correct when inserting table data?

1.  insert database-name(columns) values(values);
2.  insert into database-name(columns) values(values);
3.  insert table-name(columns) values(values);
4.  insert into table-name(columns) values(values);

 

  

6.  Answer:  D

Explanation:

“insert into table-name(columns) values(values)” is used to insert table data. For example:

mysql>insert into colortable (color, color1, color2, color3) values(“white”, “red”, “blue”, “green”);

 

 

7.  Which following command is not correct when altering a table?

1.  alter table table-name add column-name data-type;
2.  alter table table-name add primary key(column-name);
3.  alter table table-name change old-table, new-table;
4.  alter table table-name drop column column-name;

  

7.  Answer:  C

Explanation:

“alter table table-name change old-table, new-table;” is not correct.

It should be:

 “alter table table-name change old-column-name new-column-name data-type;” 

For example:

alter table colortable change color1 color2 varchar(30);

The above command changes the column name color1 to color2.

 

 

8.  Which following command is correct when updating specific data?

1.  update table-name set column-name=value;
2.  update table-name get column-name=value;
3.  update table-name net column-name=value;
4.  update table-name let column-name=value;

  

8.  Answer:  A

Explanation:

“update table-name set column-name=value” is used to update specific data.

For example:

mysql>update colortable set color1=yellow, color2=purple;

 

 

9.  Which following command is not correct when deleting data, table?

1.  delete from table-name;
2.  delete from table-name where id=10;
3.  delete table table-name;
4.  drop table table-name;

  

9.  Answer:  C

Explanation:

“delete table table-name” is wrong syntax. It should be “drop table table-name”, which can delete a table.

For example:

mysql>drop table table-name;

 

 

10.  Which following command is not correct when querying data?

1.  select \* from table-name;
2.  select \* from table-name where column=value;
3.  select column-name from table-name;
4.  select column-name from table-name when column=value;

  

10.  Answer:  D

Explanation:

“select column-name from table-name when column=value;” is not correct.

It should be:

select \* from table-name where column=value, which can query a specific data.

For example:

mysql>select \* from colortable where id = 10;

The above queries a value with id is 10 in the table colortable

 

  

Chapter 8  MySQL & PHP

 

 

1.  To connect a MySql database, use\_\_\_?

1.  mysqli\_connect (host, username, password, dbname);
2.  mysqli\_connect (dbname, username, password, host);
3.  mysqli\_connect (host, password, username, dbname);
4.  mysqli\_connect (username, password, host, dbname);

  

1.  Answer:  A

Explanation:

To connect to a MySql database, use a command as following:

mysqli\_connect (host, username, password, dbname);

host means host name, 

dbname means database name.

 

 

2.  Which following line is not correct in the code?

$connect=mysqli\_connect ("host", "username", "password", "dbname");  // line 1

if ( $connect ) {  // line 2

die("Connection error: ");  //line 3

exit;  // line 4

 

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

2.  Answer: B

Explanation:

It should be:   if ( ! $connect ).  

“! $connect” means that connection failed.

“$connect" means that connection succeeded.

 

 

3.  Which following line is not correct in the code?

$con=mysqli\_connect ("host", "user", "psword", db");  

$query=”select id, color from colortable”; // line 1

$result=mysqli\_query( );  // line 2

while ($row=mysqli\_fectch\_array($result)) {

echo (“ID:”. $row\[id\] );  // line 3

echo (“COLOR:”. $row\[“color”\]);  // line 4

}

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

3.  Answer:  B

Explanation:

It should be:  $result=mysqli\_query($cont, $query);  

mysqli\_query($con, $query ) has two required arguments.

$con specifies the MySql connection.

$query specifies the query string.

 

 

4.  In MySql command, each line should have a symbol to end the command, it is \_\_\_\_?

1.  ,
2.  .
3.  ;
4.  !

 

  

4.  Answer: C

Explanation:

Symbol ; is used to end a command line.

For example:

$str=”select \* from mytable”;

 

 

5.  Which following command can remove a database?

1.  remove
2.  delete
3.  erase
4.  drop

  

5.  Answer:  D

Explanation:

Command “drop” can remove an existing database.

For example:

mysql> drop database databaseName;

 

 

6.  Which following statement is not correct about MySql data types?

1.  TINYINT: 1bytes
2.  SMALLINT: 2 bytes
3.  MEDIUMINT: 3 bytes
4.  INTEGER: 4 bytes

  

6\. Answer:  D

Explanation:

MySql only has INT data type, without INTEGER data type.

For example: 

mysql>create table mytable(id int auto\_increment,

                                             color varchar(20) not null,

                                              ……);

 

 

7.  If you want to insert “02/18/2015 12:26:38” into a database, which following data type should be used?

1.  DATE
2.  TIME
3.  DATETIME
4.  TIMESTAMP

 

  

7.  Answer:  C

Explanation:

The format of DATETIME is “mm/dd/yyyy  hh/mm/ss”.

The format of DATE is “mm/dd/yyyy”.

The format of TIME is “hh/mm/ss”.

The format of TIMESTAMP is “YYYYMMDDhhmmss”.

 

 

8.  When you set VARCHAR(8), MySql will automatically allocate \_\_\_ length to store the data.

1.  1+8 bytes
2.  2+8 bytes
3.  3+8 bytes
4.  4+8 bytes

  

8.  Answer:  A

Explanation: 

VARCHAR(8) actually allocates dynamically up to 1+8 bytes to store the data. 

8 bytes is used to store original data and, 1 additional byte is used to store the changeable length of the data. For example:

If you have the string 'hello' to store, that will take 6 bytes, not 5 bytes.

 

 

9.  Which following statement is not correct about marching character?

1.  “%” wildcard represents zero to more characters in search pattern.
2.  “\_” wildcard represents a single character in a search pattern.
3.  “like” is MySql keyword for marching character.
4.  “unlike” is MySql keyword for marching character.

  

9.  Answer: D

Explanation:

It should be “not like” instead of “unlike”. For example:

SELECT user\_name, country FROM writer   

WHERE user\_name NOT LIKE 'W%';

The above statement excludes those rows from the table writer, having the 1st character of user\_name ‘W’.

 

 

10.  To return both associative and indexed array of the row, use\_\_\_ command.

1.  mysql\_fetch\_assoc( );
2.  mysql\_fetch\_row( );
3.  mysql\_fetch\_array( );
4.  mysql\_fetch\_numeric( );

 

  

10.  Answer: A

Explanation:

To return both associative and indexed array of the row, use mysql\_fetch\_assoc( ) command.

To return associative array of the row, use mysql\_fetch\_assoc( ) command.

To return indexed array of the row, use mysql\_fetch\_array( ) command.

mysql\_fetch\_numeric( ) is not a MySql command.

 

  

Chapter 9  Advance PHP

 

 

1.  Which following method can be used as constructor?

1.  \_call( )
2.  \_set\_state( )
3.  \_construct( )
4.  \_autoload( )

 

  

1.  Answer:  C

Explanation:

\_constrctor( ) can be used to constructor.

\_call( ) is run when calling a non-existent method.

\_set\_state( ) is called by var\_export( ) for re-initialization.

\_autoload( ) can load the class definitions on demand.

 

 

2.  Which following method can be used as destructor?

1.  \_get( )
2.  \_set( )
3.  \_toString( )
4.  \_destruct( )

  

2.  Answer:  D

Explanation:

\_destruct( ) can be use to destructor.

\_get( ) is called when accessing an undefined object property.

\_set( ) is called when assigning an undefined object property.

\_toString( ) is called when directly using echo( ) or print( ) an object.

 

 

3.  Which following method can copy an object?

1.  \_isset( )
2.  \_unset( )
3.  \_invoke( )
4.  \_clone( )

  

3.  Answer:  D

Explanation:

\_clone( ) can be used to copy an object.

\_isset( ) is called when using isset() or empty() on inaccessible properties.

\_unset( ) is called when using unset() on inaccessible properties.

\_invoke( ) is called when a script tries to call an object as a function.

 

 

4.  Which following keyword can be used to connect an interface?

1.  extends
2.  implements
3.  interfaces
4.  combines

  

4.  Answer:  B

Explanation:

“implements” can connect an interface. For example:

interface colors{

function show( );

}

class green implements color{  // using implement 

function show( ){

echo “Shows green”;

}

}

 

 

5.  In PHP, we can use \_\_\_\_ to declare an abstract class.

1.  abstract
2.  theoretical
3.  conceptual
4.  intangible

  

5.  Answer:  A

Explanation:

“abstract” can be used to declare a abstract class. e.g.

abstract class color{  // using abstract

abstract function show( );

}

class blue extends color{

function show( ){

echo “Show blue”;

}

}

 

 

6.  Classes and methods can be declares as \_\_\_\_ to prevent further inheritance.

1.  private
2.  protected
3.  final
4.  public

  

6.  Answer:  C

Explanation:

“final” can prevent further inheritance from other class.

final class test{   // declare final

function abc( ){…}

}

 

 

7.  To determine whether a PHP variable is an instantiated object of a certain class, use\_\_\_\_?

1.  \_class( )
2.  \_object( )
3.  \_variable( )
4.  instanceof

  

7.  Answer:  D

Explanation:

“instanceof “ can identify an object belong to which class. 

For example:

class MyClass{ }

$a = new MyClass;

var\_dump($a instanceof MyClass);

The output is:   bool(true)

 

 

8.  In PHP 5, all objects are passed by \_\_\_.

1.  value
2.  reference
3.  constant
4.  variable

  

8.  Answer:  B

Explanation:

All objects in PHP 5 are passed by reference. 

For example:

$myInstance=new myClass( );

$copyInstance=$myInstance;

Then, $myInstance and $copyInstance are the same object.

 

 

9.  To check the non-existing variable or method in an object, use\_\_\_and\_\_\_.

1.  \_isset( )  \_unset( )
2.  \_construct( )   \_destruct( )
3.  \_sleep( )    \_wakeup( )
4.  \_set( )   \_get( )

  

9.  Answer:  D

Explanation:

\_set ( ) and \_get ( ) can check non-existing variable or method in an object. For example:

class test{

function \_set($name, $val){

echo “Nothing”;

}

}

$obj=new test( );

$obj->myar=10;   /\* $myvar has not yet been defined, $obj references a non-existing variable.   \*/

 

 

10.  To prevent a method from being overridden, use\_\_\_\_ keyword that precedes the method name.

1.  public
2.  private
3.  protected
4.  final

  

10.  Answer:  D

Explanation:

“final” can prevent a method from being overridden. 

For example:

class A{

final function test( ){ }

}

class B extends A{

function test( ){ }   /\* test( ) in class B cannot override the             test( ) in class A. “/

}

 

 

 

  

Chapter 10 Errors

 

 

1\. Which following line is not correct in the code?

$a=100;

$b=200;

if ($a>$b {  // line 1

echo “$a is greater than $b.”;  // line 2

}

else {  // line 3

echo “$a is less than $b”;  // line 4

}

1.  line 1
2.  line 2
3.  line 3
4.  line 4

 

  

1.  Answer:  A

Explanation:

If( ) is missing a “)”.

It should be:  If ($a>$b)

 

 

2.  Which following line is not correct in the code?

$a=100, b=200; // line 1

if ($a>$b) {  

echo “$a is greater than $b.”;  // line 2

}

else {  // line 3

echo “$a is less than $b”;  // line 4

}

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

2.  Answer:  A

Explanation:

“b” is missing $ symbol.

It should be: $b=200; 

 

 

3.  Which following line is not correct in the code?

$a=10;  // line 1

do{

each “Check error!”;  // line 2

$a++;  // line 3

} while( );  // line 4

1.  line 1
2.  line 2
3.  line 3
4.  line 4

  

3.  Answer:  D

Explanation:

“while ( )” is missing a test expression. 

It should be:  while ( $a< 12 );

 

 

4.  Which following line is not correct in the code?

<?php // line 1

$str=”Check error!”; line 2

function test( ){  

echo $str;  // line 3

 }

text( );  // line 4

?>

1.  line 1
2.  line 2
3.  line 3
4.  line 4

 

 

4.  Answer:  D

Explanation:

text( ) calls a non-existing function.

It should be:  test( );

 

 

5\. Which following line is not correct in the code?

$a=100;

$b=200;

if ($a<$b) {  // line 1

echo “Write a positive review for this book!”;  // line 2

echo “Very Good!”;

}

else {  // line 3

echo “Write a non-positive review for this book.”  // line 4 

echo “No Good!”;

}

 

1.  line 1
2.  line 2
3.  line 3
4.  line 4

 

  

5.  Answer:  D

Explanation:

This command is missing “;”.  It should have a “;” at the end of the command. Therefore,

“Write a non-positive review for this book.” is wrong.

“Write a positive review for this book!” is correct. Thank you very much!

 

  

How time flies! It is time to say good-bye. 

To view Ray Yao’s books:

[Linux Command Line](http://www.amazon.com/Linux-Command-Line-Beginners-Guide-ebook/dp/B00OP0TZDY/ref=sr_1_20?ie=UTF8&qid=1420734172&sr=8-20&keywords=linux)

[JAVA 100 Tests for interview](http://www.amazon.com/JAVA-Tests-Answers-Explanations-Beginners-ebook/dp/B00T343AQU/ref=sr_1_77?ie=UTF8&qid=1422932089&sr=8-77&keywords=java)

[PHP 100 Tests for interview](http://www.amazon.com/PHP-Tests-Beginner-Answers-Explanations-ebook/dp/B00U4Z5BHS/ref=sr_1_117?s=digital-text&ie=UTF8&qid=1425242078&sr=1-117&keywords=php)

[JAVA in 8 Hours](http://www.amazon.com/Java-Hours-Essential-Knowledge-Beginners-ebook/dp/B00UI9266Y/ref=sr_1_205?s=digital-text&ie=UTF8&qid=1426071988&sr=1-205&keywords=java)

[PHP in 8 Hours](http://www.amazon.com/PHP-MySQL-Minutes-Coding-Beginners-ebook/dp/B00U02VLB0/ref=sr_1_23?ie=UTF8&qid=1424960929&sr=8-23&keywords=PHP) 

[JavaScript in 8 Hours](http://www.amazon.com/JAVASCRIPT-Beginners-JavaScript-Simple-programming-ebook/dp/B00WH0ESWC/ref=sr_1_30?s=digital-text&ie=UTF8&qid=1429761426&sr=1-30&keywords=javascript)

[C++ in 8 Hours](http://www.amazon.com/Hours-Beginners-Simple-programming-coding-ebook/dp/B00XT1HRA8/ref=sr_1_16?ie=UTF8&qid=1432212644&sr=8-16&keywords=C%2B%2B)

[Ray Yao's books](http://www.amazon.com/Ray-Yao/e/B00RG5FG6K/ref=ntt_dp_epwbk_0)

# Conclusion

My friend,

I will appreciate so much if you write a positive review for this book. Thank you very much for your support!

Sincerely

Best Regards

Ray

 

 

My friend, See you!