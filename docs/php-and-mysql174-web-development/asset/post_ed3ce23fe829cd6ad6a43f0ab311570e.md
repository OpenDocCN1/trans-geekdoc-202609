
## 1 PHP Crash Course

This chapter gives you a quick overview of PHP syntax and language constructs. If you are already a PHP programmer, it might fill some gaps in your knowledge. If you have a background using C, Perl, Python, or another programming language, it will help you get up to speed quickly.

In this book, you'll learn how to use PHP by working through lots of real-world examples taken from our experiences building real websites. Often, programming textbooks teach basic syntax with very simple examples. We have chosen not to do that. We recognize that what you do is get something up and running, and understand how the language is used, instead of plowing through another syntax and function reference that's no better than the online manual.

Try them in or download them from the website, change them, break them, and learn how to fix them again.

This chapter begins with the example of an online product order form to show how variables, operators, and expressions are used in PHP. It also covers variable types and operator precedence. You will learn how to form variables and manipulate them by working out the total and cost on a customer order.

You will then define the order form example using a PHP script to validate the input data. You will examine the concept of Boolean values and look at examples using if, else, the ?: operator, and the switch statement. Finally, you'll explore looping by writing some PHP to generate repetitive tables.

Key topics you will learn in this chapter include:

- Embedding PHP in HTML
- Adding dynamic content
- Accessing form variables
- Understanding identifiers

## Chapter 1. PHP Crash Course

- Creating user-declared variables
- Examining variable types
- Assigning values to variables
- Declaring and using constants
- Understanding variable scope
- Understanding operators and precedence
- Evaluating expressions
- Using variable functions
- Making decisions with `if`, `else`, and `switch`
- Taking advantage of iteration using `while`, `do`, and `for` loops

## Before You Begin: Accessing PHP

To work the examples in this chapter and the rest of the book, you need access to a web server with PHP installed. To gain the most from the examples and case studies, you should run them and try changing them. To do this, you need a testbed where you can experiment.

If PHP is not installed on your machine, you need to begin by installing it or having your system administrator install it for you. You can find instructions for doing so in Appendix A, “Installing Apache, PHP, and MySQL.”

## Creating a Sample Application: Bob’s Auto Parts

One of the most common applications of any server-side scripting language is HTML forms. You'll start learning PHP by implementing an order form for Bob’s Auto Parts, a fictional parts company. You can find all the code for the examples used in this chapter in the directory called `chapter01` on the CD-ROM.

## Creating the Order Form

Bob’s HTML programmer has set up an order form for the parts that Bob sells. This relatively simple order form, shown in Figure 1.1, is similar to many you have probably seen while surfing. Bob would like to be able to know what his customers ordered, work out the total prices of their orders, and determine how much sales tax is payable by the orders.

## Creating a Sample Application: Bob's Auto Parts 13

![](img/654520c37415debd4290b9b4aa2c03f2_44_0.png)

Figure 1.1 Bob's initial order form records only products and quantities

Part of the HTML for this form is shown in Listing 1.1.

## Listing 1.1 order.form.html— HTML for Bob's Basic Order Form

```html
<form action="processorder.php" method="post">
<table style="border: 0px;">
<tr style="background: #cccccc; text-align: center;"><td>Item</td>
<td style="width: 15px; text-align: center;"><td>Quantity</td>
</tr>
<tr>
<td>Tires</td>
<td><input type="text" name="tireqty" size="3" maxlength="3" /></td>
</tr>
<tr>
<td>Oil</td>
<td><input type="text" name="oilqty" size="3" maxLength="3" /></td>
</tr>
<tr>
<td>Spark Plugs</td>
<td><input type="text" name="sparkqty" size="3" maxlength="3" /></td>
</tr>
```

```html
<td colspan="2" style="text-align: center;"><input type="submit" value="Submit Order" /></td>
</tr>
</table>
</form>
```

Notice that the form action is set to the name of the PHP script that will process the customer's order (You will write this script next). In general, the value of the action attribute is the URL that will be loaded when clicks the Submit button. The data the user filled in the form will be sent to this URL via the HTTP method specified in the method attribute, either get (appended to the end of the URL) or post (sent as a separate message).

Also note the names of the form fields: tireqty, oilqty, and sparkqty. You'll use these names again in the PHP script. Because the names will be used, it's important to give your form fields meaningful names that you can easily.

## Processing the Form

Notice that the form action is set to the name of the PHP script that will process the customer's order (You will write this script next). In general, the value of the action attribute is the URL that will be loaded when clicks the Submit button. The data the user filled in the form will be sent to this URL via the HTTP method specified in the method attribute, either get (appended to the end of the URL) or post (sent as a separate message).

Also note the names of the form fields: tireqty, oilqty, and sparkqty. You'll use these names again in the PHP script. Because the names will be used, it's important to give your form fields meaningful names that you can easily.

## Embedding PHP in HTML

The variables, operators, and expressions are used in PHP. It also covers variable types and operator precedence. You will learn how to form variables and manipulate them by working out the total and cost on a customer order.

You will then define the order form example using a PHP script to validate the input data. You will examine the concept of Boolean values and look at examples using if, else, the ?: operator, and the switch statement. Finally, you'll explore looping by writing some PHP to generate repetitive tables.

Key topics you will learn in this chapter include:

- Embedding PHP in HTML
- Adding dynamic content
- Accessing form variables
- Understanding identifiers

## Chapter 1. PHP Crash Course

- Creating user-declared variables
- Examining variable types
- Assigning values to variables
- Declaring and using constants
- Understanding variable scope
- Understanding operators and precedence
- Evaluating expressions
- Using variable functions
- Making decisions with `if`, `else`, and `switch`
- Taking advantage of iteration using `while`, `do`, and `for` loops

## Before You Begin: Accessing PHP

To work the examples in this chapter and the rest of the book, you need access to a web server with PHP installed. To gain the most from the examples and case studies, you should run them and try changing them. To do this, you need a testbed where you can experiment.

If PHP is not installed on your machine, you need to begin by installing it or having your system administrator install it for you. You can find instructions for doing so in Appendix A, “Installing Apache, PHP, and MySQL.”

## Creating a Sample Application: Bob’s Auto Parts

One of the most common applications of any server-side scripting language is HTML forms. You'll start learning PHP by implementing an order form for Bob’s Auto Parts, a fictional parts company. You can find all the code for the examples used in this chapter in the directory called `chapter01` on the CD-ROM.

## Creating the Order Form

Bob’s HTML programmer has set up an order form for the parts that Bob sells. This relatively simple order form, shown in Figure 1.1, is similar to many you have probably seen while surfing. Bob would like to be able to know what his customers ordered, work out the total prices of their orders, and determine how much sales tax is payable by the orders.

## Creating a Sample Application: Bob's Auto Parts 13

![](img/654520c37415debd4290b9b4aa2c03f2_44_0.png)

Figure 1.1 Bob's initial order form records only products and quantities

Part of the HTML for this form is shown in Listing 1.1.

## Listing 1.1 order.form.html— HTML for Bob's Basic Order Form

```html
<form action="processorder.php" method="post">
<table style="border: 0px;">
<tr style="background: #cccccc; text-align: center;"><td>Item</td>
<td style="width: 15px; text-align: center;"><td>Quantity</td>
</tr>
<tr>
<td>Tires</td>
<td><input type="text" name="tireqty" size="3" maxlength="3" /></td>
</tr>
<tr>
<td>Oil</td>
<td><input type="text" name="oilqty" size="3" maxLength="3" /></td>
</tr>
<tr>
<td>Spark Plugs</td>
<td><input type="text" name="sparkqty" size="3" maxlength="3" /></td>
</tr>
```

```html
<td colspan="2" style="text-align: center;"><input type="submit" value="Submit Order" /></td>
</tr>
</table>
</form>
```

Notice that the form action is set to the name of the PHP script that will process the customer's order (You will write this script next). In general, the value of the action attribute is the URL that will be loaded when clicks the Submit button. The data the user filled in the form will be sent to this URL via the HTTP method specified in the method attribute, either get (appended to the end of the URL) or post (sent as a separate message).

Also note the names of the form fields: tireqty, oilqty, and sparkqty. You'll use these names again in the PHP script. Because the names will be used, it's important to give your form fields meaningful names that you can easily.

## Processing the Form

Notice that the form action is set to the name of the PHP script that will process the customer's order (You will write this script next). In general, the value of the action attribute is the URL that will be loaded when clicks the Submit button. The data the user filled in the form will be sent to this URL via the HTTP method specified in the method attribute, either get (appended to the end of the URL) or post (sent as a separate message).

Also note the names of the form fields: tireqty, oilqty, and sparkqty. You'll use these names again in the PHP script. Because the names will be used, it's important to give your form fields meaningful names that you can easily.

## Embedding PHP in HTML

The variables, operators, and expressions are used in PHP. It also covers variable types and operator precedence. You will learn how to form variables and manipulate them by working out the total and cost on a customer order.

You will then define the order form example using a PHP script to validate the input data. You will examine the concept of Boolean values and look at examples using if, else, the ?: operator, and the switch statement. Finally, you'll explore looping by writing some PHP to generate repetitive tables.

Key topics you will learn in this chapter include:

- Embedding PHP in HTML
- Adding dynamic content
- Accessing form variables
- Understanding identifiers

## PHP Tags

The PHP code in the preceding example began with <?php and ended with ?>. This is similar to all HTML tags because they begin with a less than (<) symbol and end with a greater than (>) symbol. These symbols <?php and ?> are called PHP tags. They tell the server server where the code starts and finishes. Any text between tags is interpreted as PHP. Any text outside these tags is treated as normal HTML.

There are two styles of PHP tags; each of the following codes is equivalent:

- XML style
  <?php echo '<order processed.</p>'; ?>
- Short style
  <?php echo '<order processed.</p>'; ?>

This is the tag that we use in this; it is the preferred PHP tag. The server administrator cannot turn it off, so you can guarantee it will be available on all servers, which is especially important if you are writing applications that may be used on different installations. This tag style can be used with Extensible Markup Language (XML) documents. In general, we recommend you use this tag.

This tag is the simplest and follows the style of Standard Generalized Markup Language (SGML) processing instruction. To use this type of tag—you must enable the short_open_tag setting in your config file or compile PHP with short tags enabled. You can find more information on how to use this tag in Appendix A. This type of tag is not recommended for code that you plan to distribute. It will not work in many environments as it is no longer enabled.

## PHP Statements

You tell the interpreter what to do by including PHP statements between your opening and closing tags. The preceding example used only one type of statement:

```php
echo '<order processed.</p>';
```

As you have possibly guessed, using the echo construct has a very simple result: It prints (or echoes) the string passed to the browser. In Figure 1.2, you can see the result that the text Order processed appears in the browser.

Notice that there is a semicolon at the end of the echo statement. Semicolons separate statements in English. If you have programmed in C or Java, you will be familiar with using the semicolon in this way.

Leaving the semicolon is a common syntax error that is easily made. However, it's equally easy to find and correct.
