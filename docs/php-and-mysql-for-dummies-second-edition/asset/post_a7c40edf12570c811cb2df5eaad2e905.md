
Table 6-5 Multiple Comparisons

| Condition | Is True If |
|---|---|
| $customer == "Smith" or $customer == "Jones" | The customer is named either Smith or Jones. |
| $customer == "Smith" and $custState == "OR" | The customer is named Smith, and the customer lives in Oregon. |
| $customer == "Smith" or $custState == "OR" | The customer is named Smith, or the customer lives in Oregon or both. |
| $customer == "Smith" xor $custState == "OR" | The customer is named Smith, or the customer lives in Oregon — but not both. |
| $customer != "Smith" and $custAge < 13 | The customer is named anything except Smith and is under 13 years of age. |

You can string together as many comparisons as necessary. The comparisons that use and are tested first, the comparisons that use xor are tested next, and the comparisons that use or are tested last. For instance, the following is a condition that includes three comparisons:

```
$age == 200 or $age == 300 and $name == "Goliath"
```

If the customer's name is Goliath and he is 300 years old, this statement is true. The statement is also true if the customer is 200 years old, regardless of what his name is. This condition is not true if the customer is 300 years old, but his name is not Goliath. You get these results because the program checks the condition as follows:

- 1. **The and is compared.** The program checks $age to see whether it equals 300, and it checks $name to see whether it equals Goliath. If both match, the condition is true, and the program does not need to check or. If only one or neither of the variables equal the designated value, the testing continues.
- 2. **The or is compared.** The program checks $age to see whether it equals 200. If it does, the condition is true. If it does not, the condition is false.

You can change the order in which comparisons are made by using parentheses. The word inside the parentheses is evaluated first. For instance, you can rewrite the previous statement with parentheses as follows:

```
( $age == 200 or $age == 300 ) and $name == "Goliath"
```

The parentheses change the order in which the conditions are checked. Now the or is checked first. This condition is true if the customer’s name is Goliath and he is either 200 or 300 years old. You get these results because the program checks the condition as follows:

- 1. **The or is compared.** The program checks `$age` to see whether it equals either 200 or 300. If it does, this part of the condition is true. However, the comparison on the other side of the `and` must also be true, so the testing continues.
- 2. **The and is compared.** The program checks `$name` to see whether it equals Goliath. If it does, the condition is true. If it does not, the condition is false.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_163_0.png)

Use parentheses liberally, even when you believe that you know the order of the comparisons. Unnecessary parentheses can’t hurt, but comparisons that have unexpected results can.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_163_1.png)

If you are familiar with other languages, such as C, you may have used || (for or) and && (for and) in place of the words. The || and && work in PHP as well. The statement `$a < $b && $c > $b` is just as valid as the statement `$a < $b and $c > $b`. The || is checked before the word or, and the && is checked before the word and.

## Adding Comments to Your Program

*Comments* are notes that are embedded in the program itself. Adding comments in your programs that describe their purpose and what they do is essential. It’s important for the lottery factor, that is, if you win the lottery and run off to a life of luxury on the French Riviera, someone else will have to finish the application. The new person needs to know what your program is supposed to do and how it does it. Actually, comments benefit you as well. You might need to revise the program next year when the details are long buried in your mind under more recent projects.

Use comments liberally. PHP ignores comments; comments are for humans. You can embed comments in your program anywhere as long as you tell PHP that they are comments. The format for comments is

```
/* comment text
more comment text */
```

Your comments can be as long or as short as you need. When PHP sees code that indicates the start of a comment (/*), it ignores everything until it sees the code that indicates the end of a comment (*/).

The following is one possible format for comments at the beginning of each program:

```
/*  name:          catalog.php
    description:  Program that displays descriptions of
                  products. The descriptions are stored
                  in a database. The product descriptions
                  are selected from the database based on
                  the category the user entered into a form.
    written by:   Lola Designer
    created:      2/1/02
    modified:     3/15/02
*/
```

You should use comments throughout the program to describe what the program does. Comments are particularly important when the program statements are complicated. Use comments such as the following frequently:

```
/* Get the information from the database */
/* Check whether the customer is over 18 years old */
/* Add shipping charges to the order total */
```

PHP also has a short comment format. You can specify that a single line is a comment by using the pound sign (#) or two forward slashes (//) in the following manner:

```
# This is comment line 1
// This is comment line 2
```

You can also use # or // in the middle of a line to signal the beginning of a comment. PHP will ignore everything from the # or // to the end of the line. This is useful for commenting a particular statement, as in the following example:

```
$average = $orderTotal/$nItems  // compute average price
```

Sometimes you really want to emphasize a comment. The following format makes a comment very noticeable:

```
###################################
## Double-Check This Section   ##
###################################
```

PHP comments are not included in the HTML code that is sent to the user's browser. The user does not see these comments.

Use comments as often as necessary in the script to make it clear. However, using too many comments is a mistake. Don't comment every line or everything that you do in the script. If your script is too full of comments, the really important comments can get lost in the maze. Only use comments to label sections and to explain code that is unusual or complicated — not code that is obvious.

- **Setting up statements that execute only when certain conditions are met:** Programs frequently need to do this. For instance, you may want to display a toy catalog to a child and an electronics catalog to an adult. This type of statement is a *conditional statement*. The PHP conditional statements are the `if` statement and the `case` statement.
- **Setting up a block of statements that is repeated:** You frequently need to repeat statements. For instance, you may want to create a list of all your customers. To do that, you might use two statements: one that gets the customer row from the database and a second one that stores the customer name in a list. You would need to repeat these two statements for every row in the customer database. The feature that enables you to do this is a *loop*. Three types of loops are `for` loops, `while` loops, and `do...while` loops.
- **Writing blocks of statements that can be reused many times:** Many tasks are performed in more than one part of the application. For instance, you might want to retrieve product information from the database and display it numerous times in an application. Getting and displaying the information might require several statements. Writing a block of statements that displays the product information and using this block repeatedly is much more efficient than writing the statements over again every time that you need to display the product information. PHP allows you to reuse statement blocks by creating a *function*.

In this chapter, you find out how to use the building blocks of PHP programs. I describe the most frequently used simple statements and the most useful complex statements and variables. You find out how to construct the building blocks and what they are used for. Then in Chapter 8, you find out how to use these building blocks to move data in and out of a database.

## Useful Simple Statements

A simple statement is a single instruction followed by a semicolon (;). Here are some useful simple statements used in PHP programs:

- `echo` statement: Produces output that browsers handle as HTML
- Assignment statement: Assigns values to variables
- Increment statement: Increases or decreases numbers in variables
- `exit` statement: Stops the execution of your program
- Function call: Uses stored blocks of statements at any location in a program

I discuss these simple statements and when to use them in the following sections.
