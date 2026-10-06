
## Chapter 20: Writing High-Quality Code

- Where to use spaces in function calls: This book tends to use spaces around function arguments, but no space between the function name and the opening parenthesis:

```
include("animal_functions.php");
```

- How to format flow structures: This book uses spaces around and the parentheses of conditions:

```
if ($queryType == "animal") {
```

- How to name identifiers: A common naming technique is to use underscores to separate words within an identifier (variable_name or CONSTANT_NAME); this is sometimes referred to as "C-style" because of this convention used in C programming. Another common technique is to capitalize each word (including, optionally, the first) within an identifier (VariableName and variableName); these conventions are often known as upper camel case and lower camel case; respect this book:

- Upper case for class names (MyClass)
- Lower case for function, method, and variable names (myMethod() and $variable)
- Uppercase with underscores for constant names (MY_CONSTANT)
- Lowercase for predefined literal values (true, false, null)

You can invent your coding standards (writing them out formally if it helps) or adopt an existing standard. Common standards include:

- The PEAR coding standards: http://pear.php.net/manual/en/standards.php
- The Java code conventions: http://java.sun.com/docs/codeconv/
- The GNU coding standards: http://www.gnu.org/prep/standards/

It doesn't matter whether you use an off-the-shelf standard or create your own. The important point is, once you've adopted a standard, you should apply it consistently to all your PHP code.

## Documenting Your Code

Writing good documentation for your code requires discipline, but it is an important aspect of building high-quality applications. Though undocumented code makes perfect sense at the time you write it, code has a habit of becoming unintelligible when you return to it six months later. What's more, if other developers ever need to work on your undocumented code, they are going to have a hard time figuring out what it's supposed to do.

## Part III: Using PHP in Practice

The main way to document PHP code is to add comments to the code. By now you probably know that you can create two types of comments in PHP:

- Single-line comments: These start with either two slashes (/) or a hash symbol (#).
- Multi-line comments: These begin with /* and end with */

## Writing Good Comments

Writing comments is simple enough, but how do you write good comments? First of all, a comment needs to explain what a piece of code does (or is intended to). However, don't state the obvious. The following is an example of bad commenting:

```
for ($i=0; $i < count($users); $i++) { // Loop from 0 to count($users) -
$users[$i]->insert(); // Call the insert() method for the user
}
```

All these comments do is reiterate what is obvious from reading the code itself; they don't add extra meaning to the code. The following comment would be much more useful:

```
// Insert all the users into the database
for ($i=0; $i < count($users); $i++) {
$users[$i]->insert();
}
```

This gives the reader a higher-level picture of what the code is trying to do.

Another way to improve your comments is to format for readability. Add a blank line before the start of a comment (and possibly after the comment); add a space after the // when using inline comments; and line up inline comments across lines. Consider the following badly formatted comments:

```
//Retrieve all users
$users = User::getAll();
/*
Add the users to the database.
Each user's modification time is updated
before the user is added.
*/
for ($i=0; $i < count($users); $i++) {
$users[$i]->updateModDate(); //Set the modification time
$users[$i]->insert(); //Insert the user
}
```

You can see that it is quite hard to work out which parts of the script are comments, and which parts are code. Here's an improved version:

```
// Retrieve all users
$users = User::getAll();

/*
 Add all the users to the database.
Each user's modification time is updated
before the user is added.
*/
for ( $i=0; $i < count($ users ); $i++ ) {
$users[$i]->updateModification(); // Set the modification time
$users[$i]->insert();
}
```

By adding horizontal and vertical space between the comments, and aligning the two inline comments, the code becomes more readable.

Another good commenting strategy is to write your comments at the same time as you write your code, rather than after the fact. In fact, it is easier to write comments at this stage, while the code is still fresh in your mind. Also, because your comments describe the code's intention, commenting encourages you to think about how and why you're writing that block of code. In fact, for an extra level of discipline, try writing your comments before you write your code!

By adding lots of helpful comments to make your code more readable, you can improve things by using meaningful variable, function, and method names. The following code is clear enough that it doesn't need any commenting:

```
$jim = new User();
$jim->setFirstName("Jim");
$jim->setLastName("Smith");
$jim->addToDatabase();
```

## Using phpDocumentor to Generate External Documentation

Though in-code comments are are, it can be easier for a developer to get a higher-level overview of an application if the documentation is separate from the code files.

phpDocumentor is a PEAR package that updates the generation of external documentation files. It reads in your PHP script files, and uses the comments in your code to generate the documentation. By formatting your comments in a special way you can give phpDocumentor extra information about your code, as the scope and data type of each variable, and the relationship between variables, functions, and classes.

You install phpDocument like any other PEAR package (Chapter 15 for more details on installing PEAR packages):

```
$ php install --aldeps phpDocument
downloading phpDocument-1.4.2.tgz
Starting to download PhpDocument-1.4.2.tgz (2,421,028 bytes)
-------------------------------------------------------
... done: 2,421,028 bytes
downloading XML_Beautifier-1.2.0.tgz
Starting to download XML_Beautifier-1.2.0.tgz (12,948 bytes)
-------------------------------------------------------
... done: 12,948 bytes
downloading XML_Parser-1.3.2.tgz
Starting to download XML_Parser-1.3.2.tgz (16,260 bytes)
-------------------------------------------------------
... done: 16,260 bytes
downloading XML_Util-1.2.1.tgz
Starting to download XML_Util-1.2.1.tgz (17,729 bytes)
-------------------------------------------------------
... done: 17,729 bytes
install ok: channel://pear.php.net/phpDocument-1.4.2
install ok: channel://pear.php.net/XML_Parser-1.3.2
install ok: channel://pear.php.net/XML_Util-1.2.1
install ok: channel://pear.php.net/XML_Beautifier-1.2.0
$
```

You run phpDocument from the command-line by using the phpdoc command, as follows:

```
$ phpdoc -o html:earthli -f /home/joe/htdocs/myscript.php -t /home/docs
```

This command tells phpDocument what to:

- Output the generation in HTML
- Use the "frames" converter
- Use the "earthli" template
- Read the comments in the PHP script file /home/joe/htdocs/myscript.php
- Save the generated documentation in /home/docs

phpdoc supports a wide range of different options. For example you can use -d to specify a directory to read, rather than a single file. You can also output the documentation in PDF or XML format. For a complete list of options visit http://manual.phpdoc.org/HTMLSmartConverter/PHP/phpDocument/tutorial_phpDocument.howto.pkg#command-line.

If you prefer, you can use a Web interface for phpDocument, rather than the command-line interface. For more details on installing and using the Web interface, see http://manual.phpdoc.org/HTMLSmartConverter/PHP/phpDocument/tutorial_phpDocument.howto.pkg.html.
