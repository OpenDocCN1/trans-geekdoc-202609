`error_reporting(OPTIONS);`
OPTIONS is a code that tells PHP what error reporting level to use. To see all errors, use the following:
`error_reporting(E_ALL);`

To see all errors except notices, use the following:
`error_reporting(E_ALL & ~E_NOTICE);`
OPTIONS can be any of the codes described in the `php.ini` file.

# Using PHP Variables

Variables are containers used to hold information. A variable has a name, and information is stored in the variable. For instance, you might name a variable $age and store the number 12 in it. After information is stored in a variable, it can be used later in the program. One of the most common uses for variables is to hold the information that a user types into a form.

# Naming a variable

When you're naming a variable, keep the following rules in mind:

+   - All variable names have a dollar sign ($) in front of them. This tells PHP that it is a variable name.
+   - Variable names can be any length.
+   - Variable names can include letters, numbers, and underscores only.
+   - Variable names must begin with a letter or an underscore. They cannot begin with a number.
+   - Uppercase and lowercase letters are not the same. For example, `$firstname` and `$Firstname` are not the same variable. If you store information in `$firstname`, you can't access that information by using the variable name `$firstName`.

![](bbox=[0.12, 0.77, 0.2, 0.88])

When you name variables, use names that make it clear what information is in the variable. Using variable names like $var1, $var2, $A, or $B does not contribute to the clarity of the program. Although PHP doesn't care what you name the variable and won't get mixed up, people trying to follow the program will have a hard time keeping track of which variable holds what information. Variable names like $firstName, $age, and $orderTotal are much more descriptive and helpful.