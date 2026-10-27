The previous example shows a simple demonstration of inheritance in PHP. Notice that each child's class inherits variables and methods from the parent "Person." In the code above, it's simple to see that the child class is a sub-class of its superclass. In this example, if a method or variable of the parent is changed, it will affect all classes derived from it.

# Importance of inheritance class

+   1. The program becomes more readable and easier to understand.
+   2. Code re-usability – inheritance enables the reuse of code.
+   3. It simplifies the system because there will be fewer classes that you need to implement and maintain.
+   4. The application becomes more flexible because it's easier to extend the functionality of existing classes.
+   5. It allows calling of parent class function from a child class function within a program.
+   6. Inheritance makes it easy for you to add comments to your code; just add the include <?php ... ?> and the above code will be added as a comment at the top of the "Child" class.
+   7. The implementation inheritance makes it easy to improve classes and re-use them.
+   8. Improves the code quality because each class contains only the specific information necessary to do its job.

# PHP Final Keyword

The word 'final' often signifies the last in a series of steps. In programming, 'final' means that no more changes can be made to that function's code after it has been called. It is also used when asking a question of the user and expecting an answer from only one particular argument, not from many different arguments. This tutorial will help you understand what the final keyword is and how it interacts with other PHP keywords like if statements, for loops, etc.

The final keyword works as a modifier in PHP, and it tells the interpreter that whatever follows the word 'final' cannot be overridden or extended in any way. Many programmers use the final keyword to describe a condition that is required for the following code to work correctly or execute on a particular condition. For example, the final keyword can be used if you need to find whether a string contains only lowercase letters or not. You could use a regular expression but doing so would end up in error because regular expressions are case insensitive. So, if you are using a final keyword, you will either have to make sure that no other code may modify the string or else make sure that the string is not modified in any way while using regular expressions.