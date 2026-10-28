
## How to use the try-catch statement

When an Exception object is thrown, your application needs to catch it and handle it. Otherwise, your application ends with a runtime error.

To catch exceptions, you use a *try-catch statement* as shown in figure 15-10. First, you code a *try block* around the statement or statements that may throw an exception. Then, you code a *catch block* that contains the statements that are executed if an exception is thrown by any statement in the try block. This is known as *exception handling*.

The first example shows how to use a try-catch statement to catch the exception thrown by the calculate_future_value function. Here, the first statement in the try block calls the calculate_future_value function. Since this function call contains an invalid third argument, it throws an exception. As a result, when the exception is thrown, control jumps over the rest of the statements in the try block and goes to the catch block. Within the catch block, the Exception object is stored in a variable named $e. Here, the first and only statement uses the getMessage method of the Exception object to display the error message in the browser.

In some cases, you may want to use a catch block to re-throw an exception as illustrated by the second example. Then, the catch block can execute some code before it re-throws the exception to the code that called it. This gives the catch block an opportunity to perform any cleaning up it may need to do before the exception is re-thrown.

In addition, there are times when you may want to code multiple catch blocks as illustrated by the third example. This allows you to handle multiple types of exceptions with a single try-catch statement. To understand how this works, you need to know that the Exception class represents the most general type of exception and its subclasses represent more specific types of errors. For example, the PDOException class is a subclass of the Exception class that represents a specific type of exception.

If you have multiple catch blocks, the first catch block that matches the class of the exception catches and handles the exception. Since all exceptions are subclasses of the Exception class, you can use the Exception class to catch all exceptions. As a result, if you want to catch more specific types of exceptions, you need to code the most specific exception classes first and end with the Exception class. In general, it's considered a good practice to end with a catch block for the Exception class since it catches any exceptions that don't match the preceding catch blocks. This is analogous to the default case in a switch statement.

Most of the time, you only need to use the Exception class and other built-in exceptions such as the PDOException class. However, if necessary, you can create your own custom exception classes that inherit the Exception class. To do that, you can use the skills for working with inheritance described in chapter 14.

**The syntax for a try-catch statement**

```php
try { statements }
catch (ExceptionClass $exceptionName) { statements }
[ catch (ExceptionClass $exceptionName) { statements } ]
```

**A try-catch statement that catches an Exception object**

```php
try {
    $fv = calculate_future_value(10000, 0.06, 0);    // Throws error
    echo 'Future value was calculated successfully.';
} catch (Exception $e) {
    echo 'Error: ' . $e->getMessage();
}
```

**A try-catch statement that re-throws an Exception object**

```php
try {
    $fv = calculate_future_value($investment, $annual_rate, $years);
} catch (Exception $e) {
    // if needed, do something before re-throwing the exception
    throw $e;
}
```

**A try-catch statement that catches two types of exceptions**

```php
try {
    $db = new PDO($dsn, 'mmuser', 'pa55word', $options);
    // other statements
} catch (PDOException $e) {
    echo 'PDOException: ' . $e->getMessage();
} catch (Exception $e) {
    echo 'Exception: ' . $e->getMessage();
}
```

**Description**

- You can use a *try-catch statement* to catch any exceptions that are thrown.
- In a try-catch statement, you code a *try* block that contains the statements that may throw exceptions. Then, you code at least one *catch* block that contains the statements to execute when an exception is thrown in the try block.
- At the beginning of the catch block, you code the name of the class that defines the exception followed by a variable that allows you to access the exception object.
- If necessary, you can code a throw statement inside a catch block to *re-throw* the exception.
- The Exception class represents the most general type of exception and its subclasses represent more specific types of errors. For example, the PDOException class is a subclass of the Exception class that represents a specific type of exception.
- If you code multiple catch blocks, you should code the most specific Exception classes first and end with the Exception class.
- You can create a custom Exception object by inheriting the Exception class.

**Figure 15-10 How to use the try-catch statement**

## The Registration application

To show you how to validate data in a real-world application, figure 15-11 presents a simple Registration application. This application validates the data that the user enters into the four fields of the form before processing that data.

Although the validation requirements for this form are limited, this application uses a highly structured, object-oriented approach to data validation that you can use to validate the data in any form. After you review this code, you'll be introduced to a longer version of this application that validates the data in several different types of fields. The code for that application is available in one of the downloadable applications for this chapter so you can re-use it in your own applications.

### The user interface

Part 1 of figure 15-11 shows the user interface for the Registration application. Here, the user has submitted invalid data, and the form has been redisplayed with error messages next to the invalid data. Once the user submits valid data, the application can process the data and display the next page.

### The file structure

Part 1 also shows the file structure for the Registration application. This application uses the Model-View-Controller pattern. To clearly show that pattern, this application stores its classes in the model directory, it stores most of its HTML in the view directory, and it stores the controller in the index.php file of the root directory.

The next four figures present the four highlighted files. The rest of the files aren't explained in this chapter because you shouldn't have any trouble understanding them by now. If you want to view them, they are available in the download for the book.

### The model

Part 2 displays the code for the fields.php file in the model directory. This file contains the code for the Field and Fields classes. These are two of the three classes that are the basis for this object-oriented approach to data validation. In part 3, you'll see the code for the Validate class that uses the objects that are created from the Field and Fields classes.

The Field class stores basic information about the validity of a field in the form. It tracks the HTML name of the field, a message about the field, and a Boolean flag to indicate if the message is an error message.

The constructor method takes the field name and an optional initial message as its parameters. These are stored in the private properties of the object.

The Field class provides several methods. To start, the getName, getMessage, and hasError methods get the values of the private properties. Since these methods don't have corresponding set methods, they are read-only methods.

The setErrorMessage and clearErrorMessage methods set and clear an error message. To start, these methods set or clear the message for the field. Then, they set the $hasError property to indicate whether the field has an error.

The getHTML method formats the message for display in an HTML page. First, it uses the htmlspecialchars function to convert special characters such as ampersands to their HTML entity equivalent. Then, it returns the message wrapped in a `<span>` tag. If the field is an error, this code adds a class attribute with a value of "error" so the CSS for the application can format the `<span>` tag appropriately.

The Fields class stores Field objects in a private associative array. Since the constructor method doesn't need to do anything, it's omitted.

The addField method takes a field name and optional message as its parameters. Then, it creates a Field object and stores it in the array using the field name as the key. Conversely, the getField method takes a field name and returns the appropriate Field object from the array.

The hasErrors method returns TRUE if any of the individual fields has an error. It uses a foreach loop to check the hasError method of each field object and returns TRUE if it finds one field that has an error. If none of the fields have an error, this method returns FALSE.
