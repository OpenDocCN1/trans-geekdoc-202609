# How to declare variables and constants

A *variable* stores a value that can change as the program executes. In PHP, variables are easy to spot because they all begin with the dollar sign ($). When you write the code for PHP applications, you frequently declare variables and assign values to them as shown in figure 2-4.

To *declare* a variable, code the dollar sign ($) followed by the *variable name*. Then, to assign a value to the variable, code the *assignment operator* (=) followed by an expression that returns the value for the variable.

In the first set of examples, the first five statements assign *literal values* (or *literals*) to variables. A literal is a value that is expressed as itself, such as 25 or ‘hello’. Here, the first statement assigns a *numeric literal* of 10 to $count. This is stored as an integer.

The second statement assigns a numeric literal of 9.50 to a variable named $price. Since this number contains a decimal point followed by one or more digits, PHP stores this number as the double type.

The third statement assigns a *string literal* of ‘Bob’ to a variable named $first_name. Similarly, the fourth statement assigns a string literal of “Bob” to a variable named $first_name. This shows that you can use either single or double quotation marks to identify a string literal.

The fifth statement assigns a *Boolean literal* of false to a variable named $is_valid. Since Boolean literals aren’t case sensitive, this statement works the same with a Boolean literal of False or FALSE.

The next four statements show that you can assign the value that’s stored in one variable to another variable. In the sixth statement, for instance, the value that’s stored in the $count variable is copied into the $product_count variable.

When you work with variables, you need to remember that they’re case-sensitive. As a result, $Count isn’t the same as $count. Also, when you create variable names, you must follow the rules shown in this figure.

Besides the rules, your variables should have meaningful names so it’s easy to tell what a variable refers to and easy to remember how to spell the name. To create names like that, you should avoid abbreviations unless they are widely understood. If, for example, you abbreviate the name for monthly investment as $mon_inv, instead of $monthly_investment, it’s hard to tell what the variable name refers to and hard to remember how to spell it.

To create a variable name that has more than one word in it, many PHP programmers use underscore characters to separate the words in the name. For example, $is_valid and $list_price use this convention. The alternative is to use a convention called *camel casing*. With this convention, the first letter of each word is uppercase except for the first word. For example, $isValid and $listPrice use camel casing. Although you can use either convention, you should pick a convention and use it consistently.

In contrast to variables, the value of a *constant* can’t be changed once it’s set. To define a constant, you can use the notation in the last set of examples. Using a constant makes sure that the value won’t be changed accidentally, and it clearly indicates that the value is not supposed to change.