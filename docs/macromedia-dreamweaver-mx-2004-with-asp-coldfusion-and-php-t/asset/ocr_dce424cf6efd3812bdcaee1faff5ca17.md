# 8) PHP users: revise the line you just found so that it reads as follows:

```
<?php echo number_format($row_rs_countries['population'],0,'.',''); ?>
```

The function number_format() takes four parameters, each one separated by a comma. The first is the number to format; here we specify the population number as retrieved from the database. The second is the number of decimal places; we specify 0. The third is the character used for the decimal; this is academic, since we won't have any decimals, but we specified a period. Note that the period is enclosed in single quotes, so PHP knows it is a text string, and not something it should try to parse. Finally, the fourth parameter is the character used to separate thousands; here we specified a comma, again, in quotes to indicate that it is a string.

![](bbox=[0.273, 0.313, 0.923, 0.683])

# 9) Save, upload, and test the file.

Both the image and the formatted number now show onscreen.