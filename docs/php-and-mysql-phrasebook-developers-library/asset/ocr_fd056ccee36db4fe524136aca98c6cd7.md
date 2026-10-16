The second parameter to fgetcsv() is the maximum length of a line in the CSV file. This is optional in PHP 5. So you need to check the length of the longest line in the CSV file; otherwise, data will get truncated.

The code at the beginning of this phrase reads in a CSV file and outputs it as an HTML table. This is done using the following code within a loop:

```
$line = fgetcsv($handle, 4096);
echo '<tr><td>';
echo implode('</td><td>', $line);
echo '</td></tr>';
```

This creates a row in an HTML table:
<tr><td>...</td></tr>.

Figure 7.3 shows both the original spreadsheet file (in OpenOffice.org) and the result in the browser.

![](bbox=[0.07, 0.8, 0.9, 0.95])

Figure 7.3 The CSV spreadsheet in OpenOffice.org and the result in the browser (fgetcsv.php; excerpt)