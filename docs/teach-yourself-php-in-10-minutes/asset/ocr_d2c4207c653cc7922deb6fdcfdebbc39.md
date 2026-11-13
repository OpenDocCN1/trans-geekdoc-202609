The width specifier indicates how many characters the formatted value should occupy in the displayed string and appears between the percent sign and the type specifier. For instance, the following example ensures that the name displayed takes up exactly 10 characters:

```
$name1 = "Tom";
$name2 = "Dick";
$name3 = "Harry";
echo "<PRE>";
printf("%10s \n", $name1);
printf("%10s \n", $name2);
printf("%10s \n", $name3);
echo "</PRE>";
```

**Padding** These examples use <PRE> tags to make sure that multiple spaces used for padding are displayed onscreen. Usually a web browser will treat multiple adjacent whitespace characters as a single space.

String padding is not used very often in creating dynamic web pages. However, it is useful when you're producing plain-text output, such as generated email text, in PHP.

If you run this example through a web browser, you will see that each name displayed is indented from the left of the screen by the correct number of characters to make each name right-aligned with the others.

The default behavior is to right-align to the given width. However, you can reverse this by using the minus symbol as an alignment specifier. To left-align the strings in the previous example, you would use the format specifier %–10s . Although visibly this would not appear any different from simply using %s , the strings would be padded on the right with spaces to a length of 10 characters.

You can change the padding character from a space to any other character by placing that character before the width value, prefixed with a single quotation mark. The following example ensures that a five-digit order number is always displayed padded with zeros if necessary:

```
$order = 201;
printf("Order number: %'05d", $order);
```

The output produced is as follows:

```
Order number: 00201
```