```
for ($intLetter=0;$intLetter<13;$intLetter++)
    echo "<td>$intLetter</td>";
    echo "</tr>";
    echo "<tr>";
    for ($intLetter=0;$intLetter<13;$intLetter++)
        echo "<td align='center'>" . $strName{$intLetter} . "</td>";
    echo "</tr>";
    echo "</table>";
?>
```

The above script uses two loops to output two rows of a table. The first outputs the character offset numbers from 0 to 12:

```
for ($intLetter=0;$intLetter<13;$intLetter++)
    echo "<td>$intLetter</td>";
```

The second outputs the string characters:

```
for ($intLetter=0;$intLetter<13;$intLetter++)
    echo "<td align='center'>" . $strName{$intLetter} . "</td>";
```

All the rest of the script contains mainly ‘echo’ statements which form the XHTML table. Consider the ‘echo’ statement:

```
echo "<td align='center'>" . $strName{$intLetter} . "</td>";
```

We had to use the dot operator to concatenate the output as string character references cannot be expanded automatically inside of a double-quoted string. The following would not work:

```
echo "<td align='center'> $strName{$intLetter} </td>";
```

The output from the above script is illustrated in Figure 11.2.

# Calculating the length of a string

In the above example, note that we included the length of the string as a constant value as part of the ‘for’ loop. This is no use if we have implemented a form to obtain a string from the user

FIGURE 11.2 String character output

![](bbox=[0.2, 0.8, 0.9, 0.92])