
#### 2.8 Constants

---

### 2.1 Basics

---

A PHP script is executed on the server, and the plain HTML result is sent back to the browser. The script can be placed anywhere in the document.

**Syntax:**

```php
<?php
// PHP code goes here
?>
```

*   A PHP script starts with `<?php` and ends with `?>`.
*   PHP statements end with a semicolon (`;`).
*   In PHP, NO keywords (e.g. `if`, `else`, `while`, `echo`, etc.), classes, functions, and user-defined functions are case-sensitive. However, all variable names are case-sensitive! But, PHP is case sensitive in printing too.
*   The default file extension for PHP files is `.php`.
*   A PHP file normally contains HTML tags, and some PHP scripting code.

**How to differentiate PHP code?**

The PHP parsing engine needs a way to differentiate PHP code from the other elements in the page. The mechanism for doing so is known as 'escaping to PHP'. There are 4 ways to do:

**Canonical PHP tags** - `<?php...?>`

If you use this style, you can be positive that your tags will always be correctly interpreted.

**Short-open (SGML-style) tags** - `<?...?>`

Short tags are the shortest option to enable PHP to recognize the tags.

*   Choose the `--enable-short-tags` configuration option when you're building PHP.
*   Set the `short_open_tag` setting in your `php.ini` file to on.
*   This option must be disabled to parse XML with PHP because the same syntax is used for XML tags.

**ASP-style tags** - `<%...%>`

ASP-style tags mimic the tags used by Active Server Pages to describe code blocks. ASP-style tags look like this.

To use ASP-style tags, you will need to set the configuration option in your `php.ini` file.

**HTML script tags**

HTML script tags look like this:

```html
<script language = "PHP">...</script>
```

**Note:** We will stick to canonical PHP tags throughout the course.

**Comments:**

A comment is the portion of a program that exists only for the human readers.

A comment in PHP code is a line that is not executed as a part of the program. There are two commenting formats in PHP:

**Single-line comments**: `//`

**Multi-lines comments**: `/* */`

**Why do we use comments?**

It may be helpful in providing short explanation of a code block. Let others understand your code. Sometimes, they can remind you of what you had been thinking when you wrote the code.

**Whitespace in PHP:**

PHP is whitespace insensitive.

Whitespace includes spaces, tabs, and carriage returns (end-of-line characters).

PHP almost never matters how many whitespace characters you have in a row. One whitespace character is the same as many such characters.

---

**Statements in PHP:**

A statement in PHP is any expression that is followed by a semicolon (`;`).

A sequence of valid PHP statements that are enclosed by the PHP tags is a valid PHP program.

**Echo and Print Statements:**

There are two basic ways to get output: `echo` and `print`.

`echo` and `print` are both used to output data to the screen. `echo` is marginally faster than `print`.

![2-1-echo-print](Images/image00148.jpeg)

**echo Statement:**

The `echo` statement can be used with or without parentheses.

**Syntax:**

```
echo or echo()
```

**Practice:**

Open a new file in the editor and save it as `section2.php`.

```php
<?php

//normal echo statement
echo "Hello!";

//echo statement with html tags inside
echo "<h2>Hello</h2>";

//multiple parameters
echo "This ", "is ", "an ", "example ";

?>
```

**Execute:**

Execute the script in the browser:

![2-1-1](Images/image00149.jpeg)

**print Statement**

The `print` statement can be used with or without parentheses.

**Syntax:**

```
print or print()
```

**Practice:**

```php
<?php
print "Normal statement";
print "<h4>HTML tag usage</h4>";
//try multiple parameters
print "Trying ","parameters";
?>
```

**Execute:**

You will receive an error as below because `print` accepts single parameter.

![2-1-2](Images/image00150.jpeg)

Now comment or remove the last statement. Let me comment as for now!

```php
<?php
print "Normal statement";
print "<h4>HTML tag usage</h4>";
//try multiple parameters
//print "Trying ","parameters";
?>
```

Now look at the output:

![2-1-3](Images/image00151.jpeg)

Can you notice? `echo`'s last statement and `print`'s first statement are together instead of printing on next line. The reason is there is no mention of new line in between those 2 statements.

We will now insert a `<br>` tag in the first `print` statement:

```php
<?php
print "<br>Normal statement";
print "<h4>HTML tag usage</h4>";
//try multiple parameters
//print "Trying ","parameters";
?>
```

You can find the difference in the output as below:

![2-1-4](Images/image00152.jpeg)

Use whitespaces in between words and check how much space is printed on the screen.

**Example:**

```php
<?php
echo "checking...              ... for spaces";
?>
```

You will have only single space printed!

![2-1-5](Images/image00153.jpeg)

Hope you are now clear what `echo` and `print` statements do! They just print to the screen!

**Note-1:**

To demonstrate `echo`, `print`, whitespace we used `<?php ?>` tags multiple times. That is not the need actually!

Let me make the code as below:

```php
<?php

//normal echo statement
echo "Hello!";

//echo statement with html tags inside
echo "<h2>Hello</h2>";

//multiple parameters
echo "This ", "is ", "an ", "example ";

print "<br>Normal statement";
print "<h4>HTML tag usage</h4>";
//try multiple parameters
//print "Trying ","parameters";

echo "checking...              ... for spaces";

?>
```

From the next section, I will be demonstrating the scripts alone. Make sure you add the opening and closing tags of php.

If you don't add? Let us try that too!

Remove `<?php` and `?>` from the above coding snippet. Here is the output:

![2-1-6](Images/image00154.jpeg)

Only the HTML tags will be printed! So do not forget to add PHP tags to every PHP file!

**Note-2:**

Shall we check the page source to know what happens to the server-script?

Consider this code snippet:

```php
<?php
//normal echo statement
echo "Hello!";

//echo statement with html tags inside
echo "<h2>Hello</h2>";

//multiple parameters
echo "This ", "is ", "an ", "example ";

print "<br>Normal statement";
print "<h4>HTML tag usage</h4>";
//try multiple parameters
//print "Trying ","parameters";

echo "checking...              ... for spaces";
?>
```

Execute the script!

Right-Click on browser and choose View Page Source! (Or just `Ctrl + U`)

You can find the HTML tags coded clearly! In case of PHP, the output is alone shown but not the script!

![2-1-7](Images/image00155.jpeg)

This is how server-side renders the HTML part to the browser! That is, browser cannot view the server-side scripting code!

Try executing few more codes to understand how HTML is rendered.

---

### 2.2 Variables

---

A variable is used to store information in PHP programs.

**How to use variables?**

*   Variables are assigned using the `=` operator, with the variable on the left-hand side and the expression to be evaluated on the right.
*   The value of a variable is the value of its most recent assignment.

**Features of PHP variables:**

*   Variables can be declared / assigned anywhere in the script.
*   Variables can, (but do not need to) be declared before assignment.
*   A variable does not know in advance whether it will be used to store a number or a string of characters.
*   Variables used before they are assigned have default values.
*   PHP automatically associates a data type to the variable, depending on its value.
*   PHP does a good job of automatically converting types from one to another when necessary.

**Rules to name a variable**

*   A variable starts with the `$` sign, followed by the name of the variable.
*   A variable name must start with a letter or the underscore character.
*   A variable name cannot start with a number.
*   A variable name can only contain alpha-numeric characters and underscores (`a-z`, `A-Z`, `0-9`, and `_`).
