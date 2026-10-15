
$dbRead = new Zend\_Db\_Adapter\_Mysqli($read);

**5.** Because a `Zend_Db` object doesn’t connect to the database until it’s needed, it’s a good idea to make a test connection to ensure your code is OK. Add these conditional statements at the end of library.php:

if ($dbWrite->getConnection()) {  

  echo 'Write OK<br />';  

}  

if ($dbRead->getConnection()) {  

  echo 'Read OK';  

}

When you type the `->` after the object, code hints should show you the methods it can use. The `getConnection()` method has a self-explanatory name. If each connection is OK, the conditional statements display confirmation. If there’s a problem, you’ll see a fatal error similar to this:

![Image](graphics/fig07_13.jpg)

Don’t panic. The important information is in the second line, which says access was denied for `cs5write` and that a password was used. This normally means the password was wrong.

Another possible cause is choosing the wrong adapter class. It’s easy to mix up `Zend_Db_Adapter_Pdo_Mssql` with `Zend_Db_Adapter_Pdo_Mysql`. The former is for Microsoft SQL Server. If you make this mistake, the error message is likely to tell you that the `mssql` driver is not installed. If it is installed, you might be trying to connect to the wrong database server.

Check your code, paying particular attention to spelling and case sensitivity.

**6.** After verifying that your connections are working, delete the code you added in step 5. It’s not needed any more.

Leave library.php open to continue working with it in the next section.

### ![Image](graphics/note.jpg)**NOTE:**

For details of the `Zend_Db` adapter classes for other databases, see [http://framework.zend.com/manual/en/zend.db.adapter.html](http://framework.zend.com/manual/en/zend.db.adapter.html).

#### **Handling exceptions with try and catch**

ZF is an object-oriented framework. If an error occurs in any part of the script, it *throws an exception*. Unlike an ordinary PHP error, which displays the error message at the point in the script where it occurs, an exception can be handled in a different part of the script. If you look closely at the first line of the fearsome error message in the preceding screen shot, you’ll see it refers to an “uncaught exception.” When you throw something, it needs to be caught.

To prevent this sort of unsightly error message, you should always wrap object-oriented code in `try` and `catch` blocks like this:

try {  

  // main script  

} catch (Exception $e) {  

  echo $e->getMessage();  

}

The main script goes between the curly braces of the `try` block, where PHP tries to run the code. If all is well, the code is executed normally, and the `catch` block is ignored. If an exception is thrown, the script inside the `try` block is abandoned, and the `catch` block runs instead.

Objects can define many different types of exceptions, so you can have different `catch` blocks to handle each type separately. The `Exception` in the parentheses after `catch` indicates it’s a generic `catch` block to handle all exceptions. The exception is assigned to the variable `$e` so you can access any messages it contains. At the moment, the `catch` block just uses `echo` and the `getMessage()` method to display the error message. When the script is ready to be deployed in a real site, you replace the code in the `catch` block with a more elegant way of handling the problem, such as displaying an error page.

You need to wrap most of the code in library.php in a `try` block, and add a `catch` block at the bottom of the page.

**1.** Position the insertion point at the end of the following line, and press Enter/Return to insert a blank line:

require\_once('Zend/Loader/Autoloader.php');

**2.** On the new line, type **try**, followed by an opening curly brace.

**3.** Select all the code on the following line to the bottom of the page, and click the Indent Code icon ![Image](graphics/indent_code.jpg)in the Coding toolbar to indent the code in the `try` block.

**4.** Add a new line at the bottom of the page, and insert the closing brace of the `try` block, together with a `catch` block like this:

} catch (Exception $e) {  

  echo $e->getMessage();  

}

**5.** Save library.php. You can compare your code with lesson07/completed/library.php.

#### **Using Zend\_Validate to check user input**

The standard way of validating user input on the server is to create a series of conditional statements to test if a value meets certain criteria. For example, if you want to check whether a password contains between 8 and 15 characters, you can use the PHP function `strlen()`, which returns the length of a string, like this:

if (strlen($\_POST\['password'\]) >= 8 && strlen($\_POST\['password'\]) <= 15) {  

  // it's valid  

}

This works, but it doesn’t check what characters are used in the password. Pressing the spacebar eight times passes this test. So, you need to add other conditional statements to make sure all criteria are met.

`Zend_Validate` works in a similar way but provides a set of commonly used validators. Each subclass has an easily recognizable name that makes your validation script much easier to read, and you don’t need to become an expert in PHP functions to ensure that user input matches your requirements. **[Table 7.1](#ch07.html#ch07tab01)** lists the most commonly used subclasses. Each one is prefixed by `Zend_Validate_`, so `Alnum` becomes `Zend_Validate_Alnum`.

For example, to check that a string is 8–15 characters, use `Zend_Validate_StringLength` like this:

$val = new Zend\_Validate\_StringLength(8,15);

This instantiates a `Zend_Validate_StringLength` object, setting its minimum and maximum values to 8 and 15 respectively, and assigns it to `$val`.

To check whether `$_POST[‘password’]` contains between 8 and 15 characters, pass it as an argument to the `isValid()` method like this:

$val->isValid($\_POST\['password'\])

If `$_POST[‘password’]` contains 8–15 characters, this returns `TRUE`. Otherwise, it returns `FALSE`.

Normally, if a validation test fails, you want to generate an error message. Do this by using a conditional statement with the logical Not operator (see “Using the logical Not operator” in [Lesson 3](#ch03.html#ch03)) like this:

$val = new Zend\_Validate\_StringLength(8,15);  

if (**!**$val->isValid($\_POST\['password'\])) {  

  $errors\['password'\] = 'Password should be 8-15 characters';  

}

Adding the logical Not operator looks for a value that is *not* valid, so the error message is assigned to `$errors[‘password’]` only if `$_POST[‘password’]` is *not* 8–15 characters.

This validation test is fine as far as it goes, but it has the same problem as the earlier example: It checks only the number of characters. Pressing the spacebar 8–15 times still passes validation. You need to combine validators. One way is to use a series of conditional statements, but ZF offers another solution—chaining validators.

**Table 7.1 Commonly Used Validation Classes**

![Image](graphics/t0229-01.jpg)

![Image](graphics/t0229-02.jpg)

#### **Chaining validators to set multiple criteria**

To test for more than one criterion, create a generic `Zend_Validate` object, and use its `addValidator()` method to add each new test. You can instantiate each validator separately, and then pass it as an argument to `addValidator()` like this:

$val = new Zend\_Validate();  

$val1 = new Zend\_Validate\_StringLength(8, 15);  

$val2 = new Zend\_Validate\_Alnum();  

$val->addValidator($val1);  

$val->addValidator($val2);

However, it’s simpler to instantiate each validator directly as the argument to `addValidator()` like this:

$val = new Zend\_Validate();  

$val->addValidator(new Zend\_Validate\_StringLength(8, 15));  

$val->addValidator(new Zend\_Validate\_Alnum());

You can even chain the `addValidator()` methods one after the other like this:

$val = new Zend\_Validate();  

$val->addValidator(new Zend\_Validate\_StringLength(8, 15))  
