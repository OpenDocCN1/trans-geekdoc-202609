# The PHP file

Figure 2-13 presents the PHP file for this application. It starts with the code in a PHP tag. This code is divided into three parts as shown by the comments.

The first part gets the data from the form by using the filter_input function to access the POST request. This code stores that data in three variables named $product_description, $list_price, and $discount_percent.

The second part calculates the discount and the discounted price. First, it multiplies the list price by the discount percent and then by .01 (to convert the percent to two decimal places). Then, it subtracts the discount from the list price to get the discount price.

The third part applies formatting to the $list_price, $discount_percent, $discount, and $discount_price variables, and it stores the formatted results in variables that have the same names appended by _f. For instance, the first statement in this group uses the built-in number_format function to format the list price with two decimal places. In addition, the formatted result is concatenated with a $ sign. As a result, an entry of 1250 will be formatted as:

```
$1,250.00
```

Here, the $ sign is added by the concatenation, while the comma, decimal point, and two zeros are added by the number_format function.

In contrast, the discount percent that the user enters isn’t formatted. However, a % sign is appended to it by using the concatenation operator. As a result, an entry of 12.5 is formatted as:

```
12.5%
```

When all four of the variables are formatted, they are ready to be displayed on the web page. Then, the block of PHP code ends and the HTML for the page begins. This HTML consists of a series of <label> and <span> tags that use echo statements to display the data. These statements display the three user entries followed by the results of the calculations.

Of these echo statements, the first three use the htmlspecialchars function to escape the output, which helps to prevent XSS attacks. Here, it isn’t necessary to escape the data for the last two echo statements because this data is calculated by the application. As a result, it isn’t possible for an attacker to inject JavaScript into these variables. However, if you aren’t sure which variables might be vulnerable to an XSS attack, you can use the htmlspecialchars function on all of them.

***

If you’re new to programming, this is a good time to take a break and do exercise 2-1. That will give you a better understanding of how this application works and how the code in the application works.