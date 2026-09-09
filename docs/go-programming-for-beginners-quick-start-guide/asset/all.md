![](image_rsrc2TZ.jpg)

   

Go Programming For Beginners Quick Start Guide Ray Yao 

Copyright © 2015 by Ray Yao All Rights Reserved Neither part of this book nor whole of this book may be reproduced or transmitted in any form or by any means electronic, photographic or mechanical, including photocopying, recording, or by any information storage or retrieval system, without prior written permission from the author. All rights reserved! Ray Yao 

Ray Yao’s eBooks & Books on Amazon Advanced C++ Programming by Ray Yao Advanced Java Programming by Ray Yao AngularJs Programming by Ray Yao C# Programming by Ray Yao C# Interview & Certification Exam C++ Programming by Ray Yao C++ Interview & Certification Exam Django Programming by Ray Yao Go Programming by Ray Yao Html Css Programming by Ray Yao Html Css Interview & Certification Exam Java Programming by Ray Yao Java Interview & Certification Exam JavaScript Programming by Ray Yao JavaScript 50 Useful Programs JavaScript Interview & Certification Exam JQuery Programming by Ray Yao JQuery Interview & Certification Exam Kotlin Programming by Ray Yao Linux Command Line Linux Interview & Certification Exam MySql Programming by Ray Yao Node.Js Programming by Ray Yao Php Interview & Certification Exam Php MySql Programming by Ray Yao PowerShell Programming by Ray Yao Python Programming by Ray Yao Python Interview & Certification Exam R Programming by Ray Yao Ruby Programming by Ray Yao Rust Programming by Ray Yao Scala Programming by Ray Yao Shell Scripting Programming by Ray Yao Visual Basic Programming by Ray Yao Visual Basic Interview & Certification Exam Xml Json Programming by Ray Yao 

Preface “Go Programming” covers all essential Go language knowledge. You can learn complete primary skills of Go programming fast and easily.  
The book includes more than 60 practical examples for beginners and includes tests & answers for the college exam, the engineer certification exam, and the job interview exam.  
Note: This book is only for Go beginners, it is not suitable for experienced Go programmers. Source Code for Download This book provides source code for download; you can download the source code for better study, or copy the source code to your favorite editor to test the programs. Source Code Download Link: [https://forms . aweber . com/form/34/1805492434 . htm](https://forms.aweber.com/form/34/1805492434.htm) 

Table of Content [Hour 1](#part0006.xhtml) [What is Go?](#part0007.xhtml) [Install Go](#part0008.xhtml) [Environment Variables](#part0009.xhtml) [First Program of Go](#part0010.xhtml) [Comment](#part0011.xhtml) [Identifier](#part0012.xhtml) [Summary](#part0013.xhtml) [Hour 2](#part0014.xhtml) [Line Separator](#part0015.xhtml) [About “{”](#part0016.xhtml) [Keywords](#part0017.xhtml) [Data Type](#part0018.xhtml) [Variables](#part0019.xhtml) [Multiply Variables’ Declaration](#part0020.xhtml) [:= assignment operator](#part0021.xhtml) [Summary](#part0022.xhtml) [Hour 3](#part0023.xhtml) [Constants](#part0024.xhtml) [iota](#part0025.xhtml) [Arithmetic Operators](#part0026.xhtml) [Relational Operators](#part0027.xhtml) [Logical Operators](#part0028.xhtml) [Assignment Operators](#part0029.xhtml) [Operators Precedence](#part0030.xhtml) [Summary](#part0031.xhtml) [Hour 4](#part0032.xhtml) [If Statement](#part0033.xhtml) [if…else statement](#part0034.xhtml) [Switch Statement](#part0035.xhtml) [Select Statement](#part0036.xhtml) [For Loop](#part0037.xhtml) [Summary](#part0038.xhtml) [Hour 5](#part0039.xhtml) [Break](#part0040.xhtml) [Continue](#part0040.xhtml#a2SB) [Goto](#part0041.xhtml) [Function](#part0042.xhtml) [Working Scope](#part0043.xhtml) [Summary](#part0044.xhtml) [Hour 6](#part0045.xhtml) [Array](#part0046.xhtml) [Pointers](#part0047.xhtml) [Nil Pointer](#part0048.xhtml) [Summary](#part0049.xhtml) [Hour 7](#part0050.xhtml) [Structures](#part0051.xhtml) [Slice](#part0052.xhtml) [append() & copy()](#part0053.xhtml) [Summary](#part0054.xhtml) [Hour 8](#part0055.xhtml) [GOROUTINE](#part0056.xhtml) [Range](#part0057.xhtml) [Map](#part0058.xhtml) [Type Conversion](#part0059.xhtml) [Recursion](#part0060.xhtml) [Summary](#part0061.xhtml) [Appendix 1](#part0062.xhtml) [Concurrency](#part0063.xhtml) [Appendix 2](#part0064.xhtml) [Tests](#part0065.xhtml) [Answers](#part0066.xhtml) [Source Code Download](#part0068.xhtml) 

Hour 1 

What is Go? Go is an open source programming language released by Google in 2009. Go is a new language, a concurrent and fast compiled language with garbage collection. It has a great characteristic: it can compile a large Go program in a few seconds on a computer. Go provides a model for software construction that makes dependency analysis easier. Go is a statically typed language, and its type definition has no hierarchy, so users don't have to spend time defining relationships between types, which make users feel that it is lighter than a typical object-oriented language. Go can provide a way to construct system software on a multicore machine. The Go language programming is optimized for multiprocessor system applications that can be faster than C or C++ code and more securely support parallel processes. The feature of the Go language: 

1.  Simple, fast and safe
2.  Parallel, interesting, open source
3.  Memory management, array security, fast compilation.

Install Go This book uses Windows OS as examples to install Go. Download Link: [https://golan g . org/dl/](https://golang.org/dl/) 1. Click the link, go to the download web page. ![](image_rsrc2U0.jpg)2. Click the “go1.11.2 windows-amd64.msi ”, download the Go Installer to the local computer. 3. Click the Go Installer, begin to install…… ![](image_rsrc2U1.jpg)4. Click the “Next”……. By default. Msi files will be installed in the c:\\Go directory. …….. …….. 5. When the installation is complete, please click the “Finish”. ![](image_rsrc2U2.jpg)

Environment Variables After installing Go, You need to add the c:\\Go\\bin to the PATH of environment variables. Please configure the environment variables. Go to “Control Panel” > “System” > “Advanced System Settings” > “Advanced” > “Environment Variables” > “Path” > “Edit…” > “New”. Please add “C:\\Go\\bin ” to the end of the Path. ![](image_rsrc2U3.jpg)Note: The setting interface is different in different Windows OS. Please restart the computer so that the setting will take effect. 

First Program of Go Please create a working folder “myGo ” under C:\\, open the NotePad editor, and write the following code into the editor. Example 1.1 

| package main import "fmt" func main() { fmt. Println("Hello, World! ") }  |
| --- |

Save the file as “hello. go” in the C:\\myGo. Open the Command Line with “cmd”, enter the following commands: ![](image_rsrc2U4.jpg)Output: Hello World! Explanation: “package main” defines the name of the package as main. Each Go application must include a package called main. The  imported package “fmt” contains I/O functions. “func main()” is the first function to execute in the Go application. fmt. Println("Hello, World! ") outputs the text “Hello, World! ”. C:\\Windows\\system32>cd\\   goes back to C: root directory. C:\\cd  myGo    enters the “myGo” folder. “go run ” is a command to execute the Go program. 

Comment 

| //  |
| --- |
| /\* ……. \*/  |

“// ” is the symbol of single-line comment. “/\* ” and “\*/ ” are the symbols of multi-line comment. Comments will not be compiled. The Go compiler will ignore all comments. Example 1.2 

| package main  // package declaration import "fmt" func main() {     // define a main function fmt. Println("Hello, World! ") } /\* The output of the above code is: Hello, World! \*/  |
| --- |

Please use “go run ” command to run this program, and check the result. 

Identifier Identifiers are used to name variables, functions, expressions, and so on. An identifier consists of one or more letters (A~Z and a~z), numbers (0~9) and an underscore, but the first character must be a letter or underscore. The first character of identifier cannot be a number. For example: The following identifiers are valid: myVariable \_Variable variable100 The following identifiers are invalid: continue       // “continue” is a keyword of Go language 100Variable        //  begin with a number 

Summary “package main” defines the name of the package as main. Each Go application must include a package called main. The  imported package “fmt” contains I/O functions. “func main()” is the first function to execute in the Go application. fmt. Println("Hello, World! ") outputs the text “Hello, World! ”. “// ” is the symbol of single-line comment. “/\* ” and “\*/ ” are the symbols of multi-line comment. Comments will not be compiled. The Go compiler will ignore all comments. Identifiers are used to name variables, functions, expressions, and so on. An identifier consists of one or more letters (A~Z and a~z), numbers (0~9) and an underscore, but the first character must be a letter or underscore. The first character of identifier cannot be a number. 

Hour 2 

Line Separator In a Go language, each statement does not need a semicolon to end the line. For example: 

| fmt. Println("Hi, My friend! ") fmt. Println("Hi, Guy! ")  |
| --- |

There are two lines in the above code, one line represents the end of a statement, each statement don’t need a semicolon to end the line. 

About “{” “{“ cannot be placed on a single line, so the following code produces an error at run time. For example: 

| func main() {     / error fmt. Println("Hello, World! ") }  |
| --- |

The following code is correct: 

| func main() {     / { is placed in here, correct! fmt. Println("Hello, World! ") }  |
| --- |

Keywords There are 25 keywords in Go language. 

| break  || default  |
| --- | --- |
| case  || defer  |
| chan  || else  |
| const  || fallthrough  |
| continue  || for  |

Keywords cannot work as a name of variable, constant and  function, etc. 

Data Type In Go language, when we define a variable or function, we need to use a data type. The use of data types is conducive to Go programming. Chiefly, there are four kinds of data type in Go language, they are very commonly used in Go coding. 

1.  Boolean types

Boolean type consists of two predefined constants: For example: (1) true (2) false 

2.  Numeric types

The number types are integer int, floating-point float32, float64, and complex number. For example: 100,  200. 88, 168888. 168 

3.  String types

String types are a sequence joined together by a fixed length of characters. A string is concatenated by a single byte. The bytes of the Go language string identify Unicode text using utf-8 encoding. For example: “jQuery in 8 Hours” is a string. 

4.  Derived types

Derived types mean (1) Channel types,(2) Map types, (3) Interface types, (4) Slice types, (5) Function types, (6) Union types, (7) Structure types, (8) Array types, (9) Pointer types. For example: Var arr \[10\] int     / \* arr is an array of length 10 \* / 

Variables Variable names of Go language consist of letters, numbers and underscores, where the first character cannot be a number. There are three ways to declare a variable. (1) The first syntax to declare a variable is: 

| var  variable\_name  type variable\_name = value  |
| --- |

For example: var a int a = 100 (2) The second syntax to declare a variable is: 

| var variable\_name = value  |
| --- |

For example: var b = “ruby in 8 hours” (3) The third syntax to declare a variable is: 

| variable\_name : = value  |
| --- |

For example: c : = 100 Example 2.1 package main func main(){ var a = "C# in 8 Hours" var b string = "is" c: ="a good book! " var e bool = true println(a, b, c, e) } Output: C# in 8 Hours is a good book!   True Explanation: “var a = "C# in 8 Hours", var b string = "is a good book! ", var c bool = true” declare two string variables, one Boolean variable. 

Multiply Variables’ Declaration There are three ways to declare the multi-variables: (1) 

| var vname1, vname2, vname3  type vname1, vname2, vname3 = v1, v2, v3  |
| --- |

For example: var a, b, c int a, b, c  = 100, 200, 300 (2) 

| var vname1, vname2, vname3 = v1, v2, v3  |
| --- |

For example: var a, b, c = 100, 200, 300 (3) 

| vname1, vname2, vname3 : = v1, v2, v3  |
| --- |

For example: a, b, c : = 100, 200, 300 

:= assignment operator 

| variable := value  |
| --- |

:= assignment operator is used to assign a value to a variable. Note: the variable should not be declared previously, which would result in a compilation error. Namely, when : = is used, the variable should be declared at first time. Example 2.2 package main func main(){ var a, b, c int a, b, c  = 100, 200, 300 var d, e, f = 400, 500, 600 s1, s2, s3 := "R in 8 Hours", "is", "good book. " println(a, b, c) println(d, e, f) println(s1, s2, s3) } Output: 100  200  300 400  500  600 R in 8 Hours is a good book. Explanation: s1, s2, s3 := "R in 8 Hours", "is", "good book. " assign variables s1, s2, s3 respectively three string values. 

Summary In a Go language, each statement does not need a semicolon to end the line. “{“ cannot be placed on a single line, so the following code produces an error at run time. Keywords cannot work as a name of variable, constant and function, etc. Variable names of Go language consist of letters, numbers and underscores, where the first character cannot be a number. There are three ways to declare the multi-variables: 1. var vname1, vname2, vname3  type vname1, vname2, vname3 = v1, v2, v3 2. var vname1, vname2, vname3 = v1, v2, v3 3. vname1, vname2, vname3 : = v1, v2, v3 := assignment operator is used to assign a value to a variable. 

Hour 3 

Constants A constant is an identifier whose value is not changed while the program is running. The syntax to define a constant is: 

| const  contant\_name  \[type\] = value  |
| --- |

Or 

| const  contant\_name = value  |
| --- |

Example 3.1 package main func main() { const x, y, z int = 10, 20, 30   // define three constants const s = "jQuery in 8 Hours! " const b bool = true println(x, y, z) println(s) println(b)       } Output: 10  20  30 jQuery in 8 Hours! true Explanation: “const” is used to define a constant. Example 3.2 package main   // Define constants as enumerations func main() { const (   // enumeration color1 = "Blue" color2 = "Pink" color3 = "Gray" ) println(color1, color2, color3)     } Output: Blue   Pink   Gray Explanation: The constants color1, color2, color3 is defined in an enum mode. 

iota “iota” is a special constants. The value of the first iota is equal to 0, and its value is automatically incremented by 1 whenever iota is used in a new row. Example 3.3 package main func main() { const ( x = iota  // the first iota value is 0 y = iota z = iota ) println(x) println(y)    println(z) } Output: 0 1 2 Explanation: The first iota value is 0, the second iota value is 1, the third iota value is 2. 

Arithmetic Operators 

| Operator  |
| --- |
| \+  |
| \-  |
| \*  |
| /  |
| %  |
| ++  |
| \- -  |

For example: Given:       a = 100      b = 2 Calculation: a + b returns 102 a – b returns 98 a \* b returns 200 a / b returns 50 a % b returns 0 a ++ returns 101 a - - returns 99 

Relational Operators 

| Operators  |
| --- |
| \>  |
| <  |
| \>=  |
| <=  |
| \==  |
| ! =  |

For example: Given:    a =  100      b = 2 Calculation: a > b returns true b <  returns false a >= b returns true a <= b returns false a == b returns false a ! = b returns true 

Logical Operators 

| Operators  |
| --- |
| &&  |
| ||  |
| !  |

For example: Given:    a =  true      b = false Calculation: a && b returns false a || b returns true ! a returns false Explanation: 

 
| true && true; returns true;  || true && false; returns false;  || false &&false; returns false;  |
| --- | --- | --- |
| true II true; returns true;  || true II false; returns true;  || false II false; return false;  |
| ! false; returns true;  || ! true; returns false;  ||  |

Assignment Operators 

| Operators  || Examples:  |
| --- | --- |
| +=  || x+=y  |
| \- =  || x\- =y  |
| \* =  || x\* =y  |
| / =  || x/ =y  |
| %=  || x%=y  |

For exampl e ： Given:     x=200;      y=100; Explanation: x+=y;   // x=x+y;  outputs 300 x/ =y;   // x=x / y;  outputs 2 x\- =y;    //  x=x \- y;  outputs 100 x%=y;    // x=x%y;   outputs  0 

Operators Precedence The following table lists the operator precedence: (From top to bottom means priority from high to low). 

| Priority  |
| --- |
| 7  |
| 6  |
| 5  |
| 4  |
| 3  |
| 2  |
| 1  |

Summary A constant is an identifier whose value is not changed while the program is running. The syntax to define a constant is: const  contant\_name  \[type\] = value const  contant\_name = value “iota” is a special constants. The value of the first iota is equal to 0, and its value is automatically incremented by 1 whenever iota is used in a new row. There are following operators: arithmetic operators, relational operators, logical operators, assignment operators. 

Hour 4 

If Statement 

| if   test-expression  {   // if true do this;    }  |
| --- |

“if statement” executes codes inside { … } only if a specified condition is true, does not execute any codes inside {…} if the condition is false. Example 4.1 package main import "fmt" func main() { var num int = 100 if num > 50 { fmt. Printf("num is greater than 50" ) } } Output: num is greater than 50 Explanation: Because the value of num is greater than 50, the code inside the { } has been executed. 

if…else statement 

| if test\_expression{ // if true do this } else { // if false do this }  |
| --- |

“if... else statement” runs some code if a condition is true and runs another code if the condition is false. Example 4.2 package main func main() { var num int = 100; if num > 200 { println("num is greater than 200" ); } else { println("num is less than 200" ); } } Output: num is less than 200 Explanation: Because the value of num is less than 200, the else{ } code has been executed. 

Switch Statement 

| switch (variable ) { case 1: if equals this case, do this case 2: if equals this case, do this case 3: if equals this case, do this default : if not equals any case, run default code }  |
| --- |

The value of the variable will compare each case first, if equals one of the “case” value; it will execute that “case” code. Example4.3 package main func main() { var number int=20 switch ( number ) {  // number  value compares each case case 10 : println ( "Running case 10" )  case 20 : println ( "Running case 20" )  case 30 : println ( "Running case 30" )  default : println ( "Running default code" )    } } Output: Running case 20 Explanation: The number value is 20; it will match case 20, so it will run the code in case 20. 

Select Statement Select Statement is a bit like Switch Statement. Switch Statement executes case code sequentially. Select Statement executes case code randomly.  
(1) 

| make(chan int, number)  |
| --- |

“ make(chan int, number ) ” creates a channel with a buffer. “chan” means a channel. For example: make(chan int, 2)  creates a channel with 2 buffers make(chan int, 10) creates a channel with 10 buffer s . (2) 

| chan <\- data data <\- 　chan  |
| --- |

“chan <\- data” sends data to a channel. “data <\- 　chan” receives data from a channel. (3) 

| select { case receive or send data : statement(s);      case receive or send data : statement(s); default :  // optional statement(s); }  |
| --- |

If more than one case can be run, Select will randomly and fairly pick one to execute and the others will not. If no case can be run, Select will execute default clause. Example 4.4 package main import "fmt" func main() { c1:=make (chan int,1024)    // create a channel c2:=make (chan int,1024) c3:=make (chan int,1024) c1 <\- 100    // send data to a channel c2 <\- 200 c3 <\- 300   select {      // randomly execute one case . case <\- c1:     // receive data from a channel fmt. Println("Receive data from c1") case <\- c2: fmt. Println("Receive data from c2") case <\- c2: fmt. Println(Rreceive data from c3") default: fmt. Println("Not receive data yet") } } Output: Receive data from c2 Explanation: The select statement executes one of the case codes randomly. 

For Loop For Loop is a control structure that can execute a specified number of loops. (1) 

| for init; condiction; in/decrease { }  |
| --- |

init:   assign a first value to a variable. condition:    a test expression in/decrease:    increasement or decreasement Example 4.5 package main func main() { for a := 0; a <= 5; a++ { print(a) } } Output: 0 1 2 3 4 5 Explanation: a: =0 assigns 0 to a.   a<=5 is a test expression.   a++ is an increasement. (2) 

| for test\_expression { }  |
| --- |

test\_ expression checks if the condition is true or false. Example 4.6 package main func main() { var a int =0 var b int = 5 for a < b { a++ print(a) } } Output: 1 2 3 4 5 Explanation: for a < b checks if a is greater than b. 

Summary “if statement” executes codes inside { … } only if a specified condition is true, does not execute any codes inside {…} if the condition is false. In “switch statement”, the value of the variable will compare each case first, if equals one of the “case” value; it will execute that “case” code. Select Statement is a bit like Switch Statement. Switch Statement executes case code sequentially. Select Statement executes case code randomly. For Loop is a control structure that can execute a specified number of loops. 

Hour 5 

Break 

| break  |
| --- |

The break statement is used to terminate the loop. Break statement also is used to terminate the case in switch statement. Example 5.1 package main func main() { var num int = 20 for num < 30 { print(num," "); num++; if num > 25 { break;     // terminate the for loop } } } Output: 20 21 22 23 24 25 Explanation: if num > 25 is a test expression, if true, the break statement will terminate the loop. Continue 

| continue  |
| --- |

The continue statement skips the current loop to execute the next one. Example 5.2 package main func main() { var num int = 20 for num < 30 { if num == 25 { num = num + 1; continue;      // skip the current for loop } print(num, " ") num++;     } } Output: 20 21 22 23 24 26 27 28 29 Explanation: if num == 25 is a test expression, if true, the continue statement will skip the current for loop, and execute the next one. Note: there is no 25 in the result. 

Goto 

| goto label; ... label: statement;  |
| --- |

The goto statement can go to the specified code and execute them unconditionally. Example 5.3 package main func main() { var num int = 10 if num > 10{ goto code01 } if num == 10{ goto code02 } code01: print("num > 10") code02: print("num == 10") } Output: num == 10 Explanation: goto code01 means to execute the statement with label code01. goto code02 means to execute the statement with label code02. 

Function A function is a block of code that is reused to perform the same task. (1) The syntax to define a function is as follows: 

| func function\_name ( parameter type) type { …… return … }  |
| --- |

func:  define a function return:   pass the result to the caller. (2) The syntax to call a function is as follows: 

| variable = function\_name ( parameter type )  |
| --- |

Example 5.4 package main func main() {   var a int = 10 var b int = 20 var result int result = add(a, b)     // call the function print( "The sum is ", result ) } func add(num1, num2 int) int {  // define a function return num1 + num2     // pass the result to the caller } Output: The sum is 30 Explanation: add(a, b) calls the function add(a, b), and pass the parameter values of a and b to num1 and num2. func add(num1, num2 int) int defines a function add(…), num1 and num2 receive the value from a and b. return num1 + num2 passes the result value to the caller add(…). Example 5.5 package main import "fmt" func swap (a, b string) (string, string) { // define a function return b, a    // returns two values to the caller . } func main() { x, y : = swap("in 8 Hours", "JavaScript")   //call the function fmt. Println(x, y) } Output: JavaScript in 8 Hours Explanation: func swap(a, b string) (string, string) {…} defines a function. swap("in 8 Hours", "JavaScript") call the function swap(…), and pass the two parameters to the function swap(…){…}. 

Working Scope The working scope in any coding is a range where a variable can be accessed, and outside that working scope the variable cannot be accessed . 

| Variables defined within a function are called local variables . Variables defined outside a function are called global variables .  |
| --- |

Example 5.6 package main func main() { var a, b, c int     // defines local variables a = 100 b = 200 c = a + b print(a, b, c) } Output: 100 200 300 Explanation: var a, b, c int define three local variables inside a function. Example 5.7 package main var v int = 100     // define a global variable func main(){ print ("The value of the global variable is ",  v) } Output: The value of the global variable is 100. Explanation: var v int = 100 defines a global variable. 

Summary The break statement is used to terminate the loop. Break statement also is used to terminate the case in switch statement. The continue statement skips the current loop to execute the next one. The goto statement can go to the specified code and execute them unconditionally. (1) The syntax to define a function is as follows: func function\_name ( parameter type) type { …… return … } (2) The syntax to call a function is as follows: variable = function\_name ( parameter type ) Variables defined within a function are called local variables. Variables defined outside a function are called global variables. 

Hour 6 

Array An array is a collection of variables of the same type and name. Array element: each variable in an array. Array index:  also called as key, the numbers on each element. Note: the array index or array key starts from zero. There are several kinds of way to define an array: (1) 

| var  array\_name\[ length\] type     // define an array array\_name\[key\] = value  // assign value to the element  |
| --- |

Example 6.1 package main func main(){ var arr \[3\]int      // define an array with three elements arr\[0\]=100     // assign a value to the array element arr\[1\]=101 arr\[2\]=102 print(arr\[0\], " ", arr\[1\], " ", arr\[2\]) } Output: 100  101  102 Explanation: var arr \[3\]int defines an array with three elements. “arr” is the array name. 3 is array length. The array type is int. arr\[0\]=100 assigns a value to the array element. “arr” is the array name, \[0\] is an index or key. (2) 

| var array\_name \[ \] type = make( \[ \] type, length )   |
| --- |

make( \[ \] type, length) defines an array. Example 6.2 package main func main(){ var arr \[ \]int = make(\[ \]int, 3)   // define an array arr\[0\]=100   // assign a value to the array element arr\[1\]=101 arr\[2\]=102 print(arr\[0\], " ", arr\[1\], " ", arr\[2\]) } Output: 100  101  102 Explanation: var arr \[ \]int = make(\[ \]int, 3) defines an array with three elements. (3) 

| var array\_name = \[length\] type {value1,value2, ... }  |
| --- |

\[length\] type {value1,value2, ... } defines an array with values. Example 6.3 package main func main(){ var arr = \[3\] int {100,101, 102} // define an array with values print(arr\[0\], " ", arr\[1\], " ", arr\[2\]) } Output: 100  101 102 Explanation: var arr = \[3\] int {100,101, 102} defines an array with three values 100, 101, and 102. (4) 

| var array\_name = \[... \] type {value1,value2, … }  |
| --- |

\[... \] type {value1,value2… } defines an array with values. Example 6.4 package main func main(){ var arr = \[...\] int {100,101, 102}   // defines an array print(arr\[0\], " ", arr\[1\], " ", arr\[2\]) } Output: 100  101  102 Explanation: var arr = \[… \] int {100,101, 102} defines an array with three values 100, 101, and 102. 

Pointers A pointer represents the value of a memory address. (1) 

| &variable    // get the memory address of a variable  |
| --- |

Example 6.5 package main import "fmt" func main() { var num int = 10   fmt. Printf("The address of the variable: %x\\n", &num   ) } Output: The address of the variable: C000044058 Explanation: &num returns the address of the variable num. (2) 

| var variable\_name \* type     // declare a pointer \*variable\_name   // get the variable value in the address  |
| --- |

For example: var ipoint \*int        // declare an int pointer var fpoint \*float32    // declare a float32 pointer \*ipoint    // gets the ipoint value in the memory address . \*fpoint    // gets the fpoint value in the memory address . Example 6.6 package main import "fmt" func main() { var num int= 100   var pt \*int        // declare a pointer pt pt = &num    // &num get address and assign to pt fmt. Printf("The address of num: %x\\n", &num  ) fmt. Printf("The address in pt: %x\\n", pt ) fmt. Printf("The value of the \*pt: %d\\n", \*pt ) } Output: The address of num: C000044058 The address in pt: C000044058 The value of the \*pt: 100  Explanation: &num gets the memory address from num. pt = &num assigns the memory address to pt \*pt returns the pt value in the memory address. Example 6.7 package main import "fmt" func main() { var a string="Hello" var b \*string var c string b=&a     //&a gets the memory address c=\*b      //\*b gets the value in memory address fmt. Println(a) fmt. Println(b) fmt. Println(c) } Output: Hello 0xc0000381c8 Hello Explanation: &varilabe returns a memory address. \*variable returns a value in the memory address. 

Nil Pointer When a pointer is defined and not assigned to any variable address, its value is nil. Example 6.8 package main import "fmt" func main() { var  npt \*int fmt. Printf("The address stored in npt: %x\\n", npt  ) } Output: The address stored in npt: 0 Explanation: “npt” is a pointer, which has not yet been assigned any address, so the value of npt is 0. 

Summary An array is a collection of variables of the same type and name. Array element: each variable in an array. Array index:  also called as key, the numbers on each element. Note: the array index or array key starts from zero. A pointer represents the value of a memory address. &variable    // get the memory address of a variable var variable\_name \* type     // declare a pointer \*variable\_name   // get the variable value in the address When a pointer is defined and not assigned to any variable address, its value is nil. 

Hour 7 

Structures A structure is a collection of data with the same or different types of data. (1) Define Structure Type. 

| type structure\_name struct { member1  type; member2  type; ... member3  type; }  |
| --- |

(2) Access Structure Members 

| structure\_name{member1: value1, member2: value2, … }  |
| --- |

Example 7.1 package main import "fmt" type Flower struct {  // define a structure type color string   // structure member size string number int } func main() { fmt. Println(Flower{color:"Red", size:"Large", number:10 }) } Output: Red   Large  10 Explanation: “type Flower struct” defines a structure type (3) Declare Structure Variables 

| var variable structure\_name  |
| --- |

(4) Assign Values to Structure Members 

| variable . member = value  |
| --- |

Example 7.2 package main type Flower struct {  // define a structure type color string   // structure member size string number int } func main() { var Rose Flower   // declare a structure variable Rose Rose.color = "Red"    // assign value to structure member Rose.size = "Large" Rose.number = 10 println( "Rose color : ", Rose. color); println( "Rose size : ", Rose. size); println( "Rose number : ", Rose. number); } Output: Rose color:   Red Rose size: Large Rose number: 10 Explanation: “var Rose Flower” declares a structure variable Rose. Rose. color = "Red" assigns value to structure member Rose. color. 

Slice Slice is a special array, but its length is changeable. (1) The first syntax to create a Slice is as follows: 

| slice\_name : = \[ \] type {val1, val2, … }  |
| --- |

Example 7.3 package main import "fmt" func main(){ s := \[ \]int{1,2,3,4,5}     // create a slice fmt. Println(s) } Output: 1 2 3 4 5 Explanation: “s : = \[ \]int{1,2,3,4,5}” creates a Slice with five values. (2) The second syntax to create a Slice is as follows: 

| slice\_name: = make (\[ \] type, len, cap)  |
| --- |

leg means the length of the slice. cap means the capacity to contain slice elements Example 7.4 package main import "fmt" func main() { s := make(\[ \]int, 5, 8) fmt. Printf("len=%d cap=%d slice=%v\\n",len(s),cap(s),s) } Output: len=5   cap=8   slice=\[00000\]   Explanation: len(s) gets the length of the slice. cap(s) gets the capacity to contain all elements. Because Slice elements have not been assigned any values yet, the five values of this Slice are zero. (3) Get some value from Slice elements: 

| slice\_name \[key1, key2\]  |
| --- |

Get the value from key1 to key2-1. Example 7.5 package main import "fmt" func main() { var s = \[9\]int{0, 1, 2, 3, 4, 5, 6, 7, 8} mySlice:= s\[2:6\]   // get the value from s\[2\] to s\[5\] fmt. Println(mySlice) } Output: 2  3  4  5 Explanation: “s\[2: 6\]” gets the value from s\[2\] to s\[5\] (4) Assign value to Slice elements. 

| slice\_name \[key\] = value  |
| --- |

Example 7.6 package main import "fmt" func main() { var s = \[9\]int{0, 1, 2, 3, 4, 5, 6, 7, 8} s\[3\] = 10       // assign a new value to s\[3\] s\[6\] = 100     // assign a new value to s\[6\] fmt. Println(s) } Output: \[0  1  2  10  4  5  100 7  8\] Explanation: s\[3\] = 10      // assign a new value to s\[3\] s\[6\] = 100    // assign a new value to s\[6\] 

append() & copy() 

| append(slice\_name, values)   // append values to a Slice copy(new\_slice, old\_slice)   // copy old Slice to new Slice  |
| --- |

Example 7.7 package main import "fmt" func main() { mySlice : = make(\[\]int, 0, 0) showSlice(mySlice) mySlice = append(mySlice, 10,20,30)  // append showSlice(mySlice) newSlice : = make(\[\]int, len(mySlice), (cap(mySlice))\*2) copy(newSlice,mySlice)    // copy showSlice(newSlice)   } func showSlice(x \[\]int){ fmt. Printf("len=%d cap=%d slice=%v\\n",len(x),cap(x),x) } Output: len=0  cap=0  slice=\[ \] len=3  cap=4  slice=\[10  20  30 \] len=3  cap=8  slice=\[ 10  20  30\] Explanation: append(mySlice, 10,20,30) appends three values to mySlice. cap(mySlice))\*2  makes the capacity double. copy(newSlice,mySlice) copys the contents of mySlice  to newSlice. 

Summary A structure is a collection of data with the same or different types of data. (1) Define Structure Type. type structure\_name struct { member1  type; member2  type; ... member3  type; } (2) Access Structure Members structure\_name{member1: value1, member2: value2, …} (3) Declare Structure Variables var variable structure\_name (4) Assign Values to Structure Members variable . member = value Slice is a special array, but its length is changeable. append(slice\_name, values)   // append values to a Slice copy(new\_slice, old\_slice)   // copy old Slice to new Slice 

Hour 8 

GOROUTINE “goroutine” is used to run multiple tasks simultaneously, which means that goroutine function can execute multiple threads at the same time by using go keyword. The following example is to define a goroutine function, and run the goroutine function. 

| go func(arguments) {     // define a goroutine function } (arguments )      // run the goroutine function  |
| --- |

Example 8.1 package main import "fmt" func fn(s string) {   // define a function fn for i := 0; i < 5; i++ { fmt. Println(s) } } func main() { fn("Thread B")    // call the function fn go func(msg string) {    // define a goroutine function fmt. Println(msg) } ("Press Enter to Stop! ")    // run the goroutine function fmt. Scanln()      // accept user input from keyboard fmt. Println("Complete! ") } Output: Thread B Thread B Thread B Thread B Thread B Press Enter to Stop! Explanation: go func(msg string) {…} defines a goroutine function. ("Press Enter to Stop! ")  runs the goroutine function, and pass the parameter to the gorountine function. 

Range Range is a built-in function of the Go language, it is used to iterate over arrays, slices, strings and maps. \* Iterating over array, slice, string returns index and value. \* Iterating over map returns keys and value. \* Iterating over channel return values. (1) Iterating Over Array/slice 

| for key, value : = range array/slice { }  |
| --- |

Example 8.2 package main import "fmt" func main(){ for key, value : = range\[ \]int{10, 11, 12, 13} { fmt. Printf("key:%d  value:%d\\n", key, value) } } Output: key: 0    value: 10 key: 1    value: 11 key: 2    value: 12 key: 3    value: 13 Explanation: range\[ \]int{10, 11, 12, 13} iterates over an array or slice, and returns the keys and values. (2) Iterating Over String 

| for key, value : = range str { }  |
| --- |

Example 8.3 package main import "fmt" func main(){ var str = "hello" for key, value : = range str { fmt. Printf("key:%d value:0x%x\\n", key, value) } } Output: key : 0     value : 0x68 key : 1     value : 0x65 key : 2     value : 0x6c key : 3     value : 0x6c key : 4     value : 0x6f Explanation: “range str { }” iterate over a string,  returns its keys and values. (3) Iterating Over Channel 

| for value : = range channel  |
| --- |

Example 8.4 package main import "fmt" func main(){ c : = make(chan int) go func() {  // define a goroutine function c <\- 　1    // send datas to channels c <\- 　2 c <\- 　3 close(c)   // close channels } ( )    // call the goroutine function for v := range c {   // iterate over the channels fmt. Println("Send data to channel: ",v) } } Output: Send data to channel: 1 Send data to channel: 2 Send data to channel: 3 Explanation: “range c” iterates over the channels. go func(){  defines a goroutine function. } ( ) calls the goroutine function. 

Map Map is an unordered collection of key-value pairs. Map is used to quickly retrieve data by key, which is similar to an index and points to the value of the data. Two syntaxes to define a map is as follows: (1) 

| m1 : = map\[key\_type\]value\_type{ }  |
| --- |

“m1” is a map variable. (2) 

| m2 : = make(map\[key\_type\] value\_type)  |
| --- |

“m2” is a map variable. Example 8.5 package main import "fmt" func main() { m1 := map\[int\]int{}      // define a map m1 m2 := make(map\[int\]int)    // define a map m2 m1\[1\] = 10 m2\[2\] = 20 for key, value : = range m1 { fmt. Println("Key: ", key, "Value: ", value) } for key, value : = range m2 { fmt. Println("Key: ", key, "Value: ", value) } } Output: Key: 1    Value: 10 Key: 2    Value: 20 Explanation: “m1 : = map\[int\]int{}”  defines a map m1 “m2 : = make(map\[int\]int)” defines a map m2 

Type Conversion Type conversion means the one data type of a variable being converted into another data type. 

| data\_type (variables)  |
| --- |

Example 8.6 package main import "fmt" func main() { var num1 int = 100 var num2 int = 3 var result float32 result = float32(num1)/float32(num2)    // conversion fmt. Printf("The result is %f\\n", result) } Output: The result is 33. 333332 Explanation: float32(num1)/float32(num2) converts the data type from int into float32. 

Recursion Recursion means that the function calls itself. 

| func recursion() { recursion()  // call itself } func main() { recursion() }  |
| --- |

Example 8.7 package main import "fmt" func myRecur(n int) int {   if n == 0 { return 1 } return n \* myRecur(n-1)      // call itself } func main() { fmt. Print("Factorial of 10 is ")  fmt. Print(myRecur(10)) } Output: Factorial of 10 is 3628800 Explanation: myRecur(n-1)  calls itself.   The recursion doesn't stop until myRecur(0) occurs. 

Summary “goroutine” is used to run multiple tasks simultaneously, which means that goroutine function can execute multiple threads at the same time by using go keyword. Range is a built-in function of the Go language, it is used to iterate over arrays, slices, strings and maps. Map is an unordered collection of key-value pairs. Map is used to quickly retrieve data by key, which is similar to an index and points to the value of the data. Type conversion means the one data type of a variable being converted into another data type. data\_type (variables) Recursion means that the function calls itself. func recursion() { recursion()  // call itself } func main() { recursion() } 

Appendix 1 

Concurrency Go language supports concurrency, we can use “go” keyword to call a function, start a new runtime thread goroutine. The syntax to call a function with go keyword is as follows: 

| go function\_name (arguments)  |
| --- |

Example: package main import ( "fmt" "time" ) func fn(s string) {   // define a function fn for i : = 0; i < 5; i++ { time. Sleep(200 \* time. Millisecond)    // delay running fmt. Println(s) } } func main() { go fn("Thread A")      // call the function fn fn("Thread B")    // call the function fn go func(msg string) {    // define a goroutine function fmt. Println(msg) }("Press Enter to Stop! ")    // run the goroutine function fmt. Scanln()       // accept user input from keyboard fmt. Println("Complete! ") } Output: Thread B Thread A Thread B Thread A Thread B Thread A Thread B Thread A Thread B Press Enter to Stop! Thread A Complete! Explanation: go fn("Thread A") calls the function fn with “go” keyword, start a new thread goroutine. 

Appendix 2 

Tests Please choose the correct answer. (01) package main import " fill in "   // import a built-in function func main() { fmt. Println("Hello, World! ") } A. iostream     B. math     C. i/o     D. fmt (02) fill in a int    // declare a variable a = 100 A. variable     B. variab     C. var     D. va (03) package main func main() { const ( x = fill in    // a special constant y = fill in z = fill in ) print(x, y, z) } Output:    0  1  2 A. const     B. iota     C. constant     D. iote (04) package main func main() { var number int=20 fill in ( number ) {  // let number compares each case case 10 : println ( "Running case 10" )  case 20 : println ( "Running case 20" )  case 30 : println ( "Running case 30" )  default : println ( "Running default code" )    } } A.   If      B. While      C. Do      D. Switch (05) package main func main() { var num int = 10 if num > 10{ fill in code01     // run the specified code next } if num == 10{ fill in code02     // run the specified code next } code01: print("num > 10") code02: print("num == 10") } A. goto     B. go     C. to     D. return (06) package main func main(){ var arr \[ \]int = fill in (\[ \]int, 3)   // define an array arr\[0\]=100   // assign a value to the array element arr\[1\]=101 arr\[2\]=102 print(arr\[0\], " ", arr\[1\], " ", arr\[2\]) } A. array     B. define     C. make     d. arr (07) package main import "fmt" type Flower fill in {  // define a structure type color string   // structure member size string number int } func main() { fmt. Println(Flower{color:"Red", size:"Large", number:10 }) } A. structure     B. struct     C. string     D. type (08) package main import "fmt" func fn(s string) {   // define a function fn for i := 0; i < 5; i++ { fmt. Println(s) } } func main() { fn("Thread B")    // call the function fn fill in func(msg string) {    // define a goroutine function fmt. Println(msg) } ("Press Enter to Stop! ")    // run the goroutine function fmt. Scanln()      // accept user input from keyboard fmt. Println("Complete! ") } A. goto     B. go     C. to     D. goroutine (09) package main func main(){ var a = "C# in 8 Hours" var b string = "is" c: ="a good book! " var e fill in = true println(a, b, c, e) } A. string     B. boolean     C. bool     D. char (10) Given:       a = 100      b = 2 Calculation: a + b returns 102 a – b returns 98 a \* b returns 200 a / b returns 50 a % b returns fill in A. 0     B. 1.        C. 2        D. 3 (11) package main import "fmt" func main() { c1:=make (chan int,1024)    // create a channel c2:=make (chan int,1024) c3:=make (chan int,1024) c1 <\- 100    // send data to a channel c2 <\- 200 c3 <\- 300   fill in {      // randomly execute one case . case <\- c1:     // receive data from a channel fmt. Println("Receive data from c1") case <\- c2: fmt. Println("Receive data from c2") case <\- c2: fmt. Println(Rreceive data from c3") default: fmt. Println("Not receive data yet") } } A.    switch     B. select     C. while     D. if (12) package main import "fmt" fill in swap (a, b string) (string, string) { // define a function return b, a    // returns two values to the caller . } func main() { x, y : = swap("in 8 Hours", "JavaScript")   //call the function fmt. Println(x, y) } A. function     B. def     C. void     D. func (13) package main import "fmt" func main() { var num int= 100   var pt \*int        // declare a pointer pt pt = fill in    // &num get address and assign to pt fmt. Printf("The address of num: %x\\n", &num  ) fmt. Printf("The address in pt: %x\\n", pt ) fmt. Printf("The value of the \*pt: %d\\n", \*pt ) } A. \*num     B. $num     C. &num     D. #num (14) package main import "fmt" func main(){ s := fill in int{1,2,3,4,5}     // create a slice fmt. Println(s) } A.   \[ \]      B. \[0\]     C\[1\]     D. \[2\] (15) package main import "fmt" func main(){ c : = make(chan int) go func() {  // define a goroutine function c <\- 　1    // send datas to channels c <\- 　2 c <\- 　3 close(c)   // close channels } ( )    // call the goroutine function for v := fill in c {   // iterate over the channels fmt. Println("Send data to channel: ",v) } } A. iterate     B. chan     C. in     D.   range (16) package main func main(){ var a = "C# in 8 Hours" var b string = "is" c fill in "a good book! "  // assign value to c var e bool = true println(a, b, c, e) } A. <\-   　 B. : =      C. =      D. <= (17) 

 
| true && true; returns true;  || true && false; returns false;  || false &&false; returns false;  |
| --- | --- | --- |
| true II true; returns true;  || true II false; returns fill in ;  || false II false; return fill in ;  |
| ! false; returns true;  || ! true; returns false;  ||  |

A. true       true B. false      false C. true       false D. false      true (18) package main func main() { var a int =0 var b int = 5 fill in a < b {      // loop statement a++ print(a) } } Output: 1 2 3 4 5 A. while      B. if      C. do      D. for (19) package main import "fmt" func swap (a, b string) (string, string) { // define a function fill in b, a    // pass two values to the caller . } func main() { x, y : = swap("in 8 Hours", "JavaScript")   //call the function fmt. Println(x, y) } A. pass     B. return     C. send     D. goto (20) package main import "fmt" func main() { var  npt \*int fmt. Printf( npt  ) } //  What is the output? A. 0      B. 1      C. 2      D. 3 (21)  
package main import "fmt" func main() { var s = \[9\]int{0, 1, 2, 3, 4, 5, 6, 7, 8} mySlice:= s\[ fill in \]   // get four values fmt. Println(mySlice) } Output: 2  3  4  5 A.   2: 6       B. 1: 5       C. 3: 7       D. 3: 6 (22) package main import "fmt" func main() { m1 := fill in \[int\]int{}      // define a map m1 m2 := fill in (map\[int\]int)    // define a map m2 m1\[1\] = 10 m2\[2\] = 20 for key, value : = range m1 { fmt. Println("Key: ", key, "Value: ", value) } for key, value : = range m2 { fmt. Println("Key: ", key, "Value: ", value) } } A.    make      make B.    make      map C.    map        make D.    map        map (23) package main import "fmt" func myRecur(n int) int {   if n == 0 { return 1 } return n \* fill in      // recursion } func main() { fmt. Print("Factorial of 10 is ")  fmt. Print(myRecur(10)) } A.   myRecur(0) B.   myRecur(n-1)   C.   recursion(0) D.   recursion(n-1) (24) package main import ( "fmt" "time" ) func fn(s string) {   // define a function fn for i : = 0; i < 5; i++ { time. Sleep(200 \* time. Millisecond)    // delay running fmt. Println(s) } } func main() { fill in fn("Thread A")      // call the function fn fn("Thread B")    // call the function fn } A.   goroutine     B. goto     C. to     D. go 

Answers 

| 01.   D  |
| --- |
| 02.   C  |
| 03.   B  |
| 04.   D  |
| 05.   A  |
| 06.   C  |
| 07.   B  |
| 08.   B  |
| 09.   C  |
| 10.   A  |
| 11.   B  |
| 12.   D  |

Note: This book is only for beginners, it is not suitable for experienced programmers . Source Code Download Link: [https://forms . aweber . com/form/34/1805492434 . htm](https://forms.aweber.com/form/34/1805492434.htm) 

Source Code Download Ray Yao’s eBooks & Books on Amazon Advanced C++ Programming by Ray Yao Advanced Java Programming by Ray Yao AngularJs Programming by Ray Yao C# Programming by Ray Yao C# Interview & Certification Exam C++ Programming by Ray Yao C++ Interview & Certification Exam Django Programming by Ray Yao Go Programming by Ray Yao Html Css Programming by Ray Yao Html Css Interview & Certification Exam Java Programming by Ray Yao Java Interview & Certification Exam JavaScript Programming by Ray Yao JavaScript 50 Useful Programs JavaScript Interview & Certification Exam JQuery Programming by Ray Yao JQuery Interview & Certification Exam Kotlin Programming by Ray Yao Linux Command Line Linux Interview & Certification Exam MySql Programming by Ray Yao Node.Js Programming by Ray Yao Php Interview & Certification Exam Php MySql Programming by Ray Yao PowerShell Programming by Ray Yao Python Programming by Ray Yao Python Interview & Certification Exam R Programming by Ray Yao Ruby Programming by Ray Yao Rust Programming by Ray Yao Scala Programming by Ray Yao Shell Scripting Programming by Ray Yao Visual Basic Programming by Ray Yao Visual Basic Interview & Certification Exam Xml Json Programming by Ray Yao Source Code Download Link: [https://forms . aweber . com/form/34/1805492434 . htm](https://forms.aweber.com/form/34/1805492434.htm)