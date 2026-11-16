
this setting, because ColdFusion supports only ColdFusion Markup Language (CFML), so there is no possibility for confusion.

The second attribute, CODEPAGE, specifies the page's language. 1252 refers to English.

- 3) ASP only: Position the insertion point in line 2 and press Enter/Return twice to add some more space. Beginning in line 3, type the following code:

```
<%
Dim numAdult, numChild, basePrice, tourPrice
%>
```

As you know from before, <% is used to mark up ASP code that the server needs to process. The extra space just above the closing %> is to leave room for additional script, which you'll add in a moment.

The second line may look a bit odd. In ASP, whenever you want to create a new variable, you must declare it. You declare new variables using Dim. Thus, the second line announces to the server that you are creating three new variables. These variables have not yet been assigned any values—you'll give them values momentarily.

> NOTE Some languages do not require you to declare variables before you set their values. Neither ColdFusion nor PHP require you to first declare variables, so these don't have equivalents for the Dim line.

By the end of this step, ASP users' code window should appear as in the following screenshot. ColdFusion and PHP users, just to reiterate, haven't done anything in this task yet, but that's about to change.

![](img/43fd0127a958864ab2d93e28efe683e7_214_0.png)

- 4) All users: Set three variables, numAdult, numChild, and basePrice, to the values entered in the numAdults, numChildren, and tourName form fields.

In ASP, insert the following code beginning in the empty line after the Dim line:

```
numAdult = Request.Form("numAdults")
numChild = Request.Form("numChildren")
basePrice = Request.Form("tourName")
```

In ColdFusion, enter the following code at the top of the document, before the opening <!DOCTYPE> tag:

```
<cfset numAdult = form.numAdults>
<cfset numChild = form.numChildren>
<cfset basePrice = form.tourName>
```

In PHP, enter the following code at the top of the document, before the opening <!DOCTYPE> line:

```
$numAdult = $_POST['numAdults'];
$numChild = $_POST['numChildren'];
$basePrice = $_POST['tourName'];
```

You've seen Request.Form("fieldname"). form.fieldname, and $_POST['fieldname'] in earlier lessons. This time, rather than simply printing them on the page, as you did before, you are storing those values inside new variables. The reason for this is that what needs to be printed on the page is the output of the calculation. By storing these values in descriptively named variables, the calculation is easier to code (and read).

ColdFusion users might wonder why the form variables aren't surrounded by pound signs (##) as they were in previous lessons. Pound signs are used only when ColdFusion is outputting a dynamic value to an external source, such as HTML. Without them, ColdFusion would print the variable name, rather than its value. But the pound signs are unnecessary here, because the action here is internal to ColdFusion—it is not outputting values anywhere.

- 5) Set a fourth variable, tourPrice, to equal the output of the calculation itself.

In ASP: insert the following code in the line below the basePrice line:

```
tourPrice = (numAdult * basePrice) + (numChild * basePrice)
```

In ColdFusion, insert the following code in the line below the basePrice line:

```
<cfset tourPrice = (numAdult * basePrice) + (numChild * basePrice)>
```

In PHP, insert the following code in the line below the basePrice line:

```
$tourPrice = ($numAdult * $basePrice) + ($numChild * $basePrice);
```

Assuming you survived seventh-grade math, you probably know what this line is doing. It is setting the value of tourPrice to equal the output of a simple calculation. The parentheses are used, as in arithmetic, to ensure that the calculations take place in the proper order.

When this line of code is resolved on the server, tourPrice has the final calculated dollar amount as its value. With that in place, all we need to do is output it into the HTML code where the XXX placeholder is, and the user will see the information that they need.

```
<%@LANGUAGE="VBScript" CODEPAGE="1252" %>
<%
Dim numAdult, numChild, basePrice, tourPrice
numAdult = Request.Form("numAdults")
numChild = Request.Form("numChildren")
basePrice = Request.Form("basePrice")
tourPrice = (numAdult * basePrice) + (numChild * basePrice)
%>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-t
<html xmlns="http://www.w3.org/1999/xhtml">
```

## 6) Still in code view, scroll down to the XXX placeholder (around line 34 in ASP, around line 30 in ColdFusion, and around line 33 in PHP). Delete XXX and in its place enter the following code to output the value of the tourPrice variable.

In ASP:

<% Response.Write(tourPrice) %>

In ColdFusion:

<cfoutput>#tourPrice#</cfoutput>

In PHP:

<?php echo $tourPrice; ?>

Outputting a variable value is familiar to you by now. The main difference between this instance of outputting a variable and what you did in Lesson 5 is that you don't need to specify an HTTP-compatible scope—URL/querystring, form, cookie, etc. The scope of this variable is the page itself as it is processed in ASP, ColdFusion, or PHP, and the variable will be resolved and removed before the code is ever sent over HTTP to the browser.

```
25 </tr>
26 </table>
27 <td><img src="images/nav_bar.gif" name="navbar" width="450" height="20" border="0" usemap="#navbarMap">
28 <td><img name="copyright_bar" src="images/copyright_bar.gif" width="272" height="20" border="0" alt="">
29 </tr>
30 </table>
31 <td colspan="2">
32 <h1><br />
33 <p name="top" id="top"><strong>Tour Price Calculator</strong></p>
34 <p>The estimated cost of your tour is <strong><%= Response.Write(tourPrice) %></strong>.</p>
35 <p>Prices include hotel, accommodation, and travel expenses during the tour. They do not include airf
36 <p><a href="tourprice_processor.asp">Calculate</a> another tour.</p>
37 <p><a href="contact.asp">Contact</a> one of our qualified agents. </p>
38 </div>
39 </td>
40 </table>
```

- 7) Save and upload both tourprice.asp and tourprice_processor.asp. Select tourprice.asp in the Site panel, and press F12 to test it.

You should always test a page's functionality as soon as you can. These two pages are ready for testing. You'll add quite a few enhancements to this application, but its core functionality works—or should.

Try several different variations. Enter numeric values in each field, choose a tour, and press Submit. You should see the output page with the calculated amount in bold. Notice that the dollar amount appears, but nothing indicates that it's a dollar amount. Both ASP, ColdFusion, and recent versions of PHP have built-in functions that enable you to output numbers in proper currency format, as you'll see in a moment.

![](img/43fd0127a958864ab2d93e28efe683e7_217_0.png)

Once you have verified that it works in the best-case scenario, when you've properly entered numbers, try to break the application by entering bad data in the form. Leave one or both fields blank, or enter a letter, such as D.

![](img/43fd0127a958864ab2d93e28efe683e7_217_1.png)

The page either returns an error message or tries to complete the calculation, anyway, returning a meaningless number. The reason is that your script multiplies and adds the contents of the form fields. If these fields have no content or contain non-numeric characters, it can't perform calculations. This application would benefit from a form validation enhancement that would ensure that users actually entered numbers in both fields, before it attempts to calculate a price.

## 8) Return to tourprice_processor.asp in Dreamweaver, and insert the function that converts the output number to the U.S. dollar currency format.

In ASP:

```
<% Response.Write(FormatCurrency(tourPrice)) %>
```

In ColdFusion:

```
<cfoutput>#DollarFormat(tourPrice)#</cfoutput>
```

In PHP:

```
<?php echo number_format($tourPrice, 2, '.', ','); ?>
```

**NOTE** PHP versions 4.3 and higher have a function, money_format(), but this is not available in earlier versions of PHP, including the one that ships on Macintosh OS X. The only disadvantages to using number_format() in this context is that it won't output the dollar sign ($). You can add this manually, by entering $ between the <strong> (or, if you didn't change it, <span class="author"> tag and the opening <?php echo... tag.

Functions are predefined actions that tell the interpreter how to do something. Computer languages generally have dozens of functions, if not more, built in for common tasks. Converting numeric figures to currency format is a common task, and so many languages have a function that performs this task.

Functions take the following format: FunctionName(Parameter). In some cases, there is no parameter, but the parentheses remain, as in the case of ColdFusion's Now() function, which returns the current time on the server. In the case of ASP's FormatCurrency() and ColdFusion's DollarFormat(), the lone parameter is the number that you want to format. Because the number is held in the tourPrice variable, you place that variable in the parameter.

PHP's number_format() function takes four parameters. They are, in order, the number to be formatted ($tourPrice), the number of decimal spaces to allow (2), the punctuation element used to indicate the decimal place (.), and the punctuation element used to separate thousands (,). Because the period and comma characters in
