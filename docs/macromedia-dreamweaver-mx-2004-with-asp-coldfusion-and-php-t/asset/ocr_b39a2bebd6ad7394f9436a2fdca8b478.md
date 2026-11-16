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

+   5) Set a fourth variable, tourPrice, to equal the output of the calculation itself.

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