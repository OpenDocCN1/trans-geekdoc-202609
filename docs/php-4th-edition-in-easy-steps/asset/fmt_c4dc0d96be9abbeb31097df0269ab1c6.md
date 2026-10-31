
`<?php echo ‘First statement’ ; echo ‘Second statement’ ?>`

![image](images/hot.jpg)

It does no harm to terminate the last statement of a PHP block if you wish to do so.

## Comment rules

It is often worthwhile adding comments to your PHP script code so it can be more easily understood by others, or by yourself when revisiting your code later. All whitespace and comments are completely ignored by the PHP parser so you can add as many comments as you like, without any adverse effect on performance.

Single-line comments may begin with a `#` hash character, or alternatively they may begin with a `//` double-slash sequence.

Multi-line (block) comments must be enclosed within `/*` and `*/` character sequences, as used in the C programming language:

```
<?php
echo ‘First statement’ ; // A single-line comment.
/* This is a multi-line comment  
containing two lines of comment. */
echo ‘Second statement’ ;
echo ‘Final statement’ ; # Another single-line comment.
?>
```

![image](images/hot.jpg)

The `//` single-line comment style is also used in C++ programming and the `#` single-line comment style is also used in Unix/Linux BASH shell scripting.

## Improving performance

![image](images/pg20_1.jpg)

It is useful to understand that the PHP engine performs a sequence of operations in order to execute your PHP code:

- **Lexing** – analyzes the code and generates a series of “tokens”. For example, the tag `<?php` generates the token `T_OPEN_TAG`, the keyword `echo` generates the token `T_ECHO` and the string `"Hello World!"` generates `T_CONSTANT_ENCAPSED_STRING`.
- **Parsing** – arranges the tokens into an “Abstract Syntax Tree” (AST). This represents what operations should be performed. For example, the AST to print the result of adding two numbers might look something like this:

```
operation => ECHO,
operand => expression (
operation => ADD,
operand1 => 4,
operand2 => 8
)
```
- **Compiling** – translates the Abstract Syntax Tree into instructional operation code (“OPcode”). This is an Intermediate Representation (IR) in machine language.
- **Executing** – runs the OPcode on the “Zend Virtual Machine” (VM). This interprets the OPcode to produce output.

Performing all these steps each time to execute a PHP script is not very efficient, so PHP includes an extension named “OPcache” that can be enabled to improve performance. OPcache stores OPcodes in memory so that lexing, parsing and compiling will only be performed when the PHP script is first executed. Subsequently, the low-level Intermediate Representation stored in memory can be executed on the Zend VM immediately.

![image](images/pg20_2.jpg)

To enable OPcache you will need to edit PHP’s initialization file. The PHP installation folder, such as `C:\\PHP`, contains files named `php.ini-development` and `php.ini-production`, which are initialization template files. When starting, PHP tries to find and load an initialization file named `php.ini`. A copy of either of the template files can be used for this purpose but the template named `php.ini-production` is recommended as the default settings in that file are optimized for performance and security. The OPcache extension is a file named `php_opcache.dll` located in an “ext” folder within the PHP installation folder.

![image](images/1b.jpg) Navigate to your PHP installation folder then save a copy of the `php.ini-production` file precisely as “php.ini”

![image](images/common1b.jpg)

php.ini

![image](images/2b.jpg) Next, open the `php.ini` file in a text editor such as Windows’ Notepad app

![image](images/3b.jpg) Now, at the end of the `php.ini` file, add a line to specify the location of OPcache

`zend_extension=C:\\PHP\\ext\\php_opcache.dll`

![image](images/4b.jpg) Then, add a line to enable the OPcache extension

`opcache.enable=1`

![image](images/5b.jpg) Save the file then restart the web server and examine the `phpinfo.php` output to confirm OPcache is now Enabled

![image](images/pg21_1.jpg)

![image](images/6b.jpg) Scroll down the Zend OPcache section to see that “Cache hits” and “Cache misses” are both initially zero

![image](images/pg21_2.jpg)

![image](images/7b.jpg) Load the `hello.php` file and re-examine the `phpinfo.php` output repeatedly to see that “Cache misses” first increases to 1 then “Cache hits” increments on successive occasions

## Enabling JIT compilation

The OPcache extension, described hereon pages 20-21, allows PHP to avoid repeated lexing, parsing, and compiling, but a further performance improvement can be made using “Just In Time” (JIT) compilation.

![image](images/pg22_1.jpg)

PHP’s JIT compilation feature generates low-level CPU instructions in Assembly language code that can be executed by many different CPU types. It transforms the OPcode into architecture-specific machine code that can be executed directly by the system’s CPU.

When PHP code is first run, the OPcode being executed by the Zend VM is examined by PHP to decide what would benefit from JIT compilation. Subsequent execution is performed directly by the system’s CPU – bypassing the Zend VM.

![image](images/pg22_2.jpg)

The OPcache extension must first be enabled to use JIT compilation, and you must specify in the PHP initialization file `php.ini` how much memory to allocate for compiled code.

![image](images/hot.jpg)

Just In Time compilation is a great new feature introduced in PHP 8.

![image](images/1b.jpg) Open the `php.ini` file in a text editor such as Windows’ Notepad app

![image](images/common1b.jpg)

php.ini

![image](images/2b.jpg) Now, at the end of the `php.ini` file, add a line to specify memory allocation of 100 megabytes for compiled code

`opcache.jit_buffer_size=100M`

![image](images/3b.jpg) Save the file then restart the web server and examine the `phpinfo.php` output to confirm JIT compilation is On

![image](images/pg23_1.jpg)

![image](images/commonb.jpg)

bench.php

It is anticipated that performance will become more important in the future for CPU-intensive tasks such as Artificial Intelligence (AI). To compare the performance improvements provided by OPcache and JIT compilation, a benchmark PHP script might contain a variety of CPU-intensive tasks. Not listed here but included in the source code archive for this book is a PHP benchmark script that produced the results below when executed with various PHP configurations:

![image](images/pg23_2.jpg)

## Summary

- PHP is a scripting language that is especially suited for web development as it can be embedded in HTML.
- PHP code is executed server-side on The Cloud, unlike JavaScript code that is executed client-side in the browser.
- A web server will first call upon the PHP engine to process PHP code before sending the response to the web browser.
- A local development environment can be created by installing a web server and the PHP engine on your own computer.
- The `http://localhost` URL is an alias for the numerical IP address of `http://127.0.0.1`.
- Access to the Abyss Web Server Console requires your user name and password, and is found at `http://localhost:9999`.
- The Web Server must be configured to recognize scripts so it will direct them to the PHP engine, by setting Interface, Interpreter, and Associated Extension parameters.
- The PHP code instruction `phpinfo()` can be used to serve up a web page containing your PHP version information.
- The PHP `echo` instruction literally writes the text content contained within following quote marks.
- All embedded PHP code must be enclosed within `<?php` and `?>` tags so it can be recognized by the PHP engine.
- Each statement within the PHP language must be terminated by a `;` semicolon character.
- Single-line comments may begin with a `#` hash character or with a `//` double-slash sequence.
