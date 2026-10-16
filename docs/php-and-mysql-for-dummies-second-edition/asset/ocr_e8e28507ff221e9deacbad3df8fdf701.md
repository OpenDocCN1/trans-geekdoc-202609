# Listing 8-9 (continued)

```
    echo " selected";
}
    echo "> $monthName[$n]\n";
}
    echo "</select>";

/* build selection list for the day */
$todayDay= date("d",$today);   //get the day from $today
echo "<select name='dateDay'>\n";
for ($n=1;$n<=31;$n++)
{
    echo " <option value=$n";
    if ($todayDay == $n )
    {
        echo " selected";
    }
    echo "> $n\n";
}
echo "</select>\n";

/* build selection list for the year */
$startYr = date("Y", $today); //get the year from $today
echo "<select name='dateYr'>\n";
for ($n=$startYr;$n<=$startYr+3;$n++)
{
    echo " <option value=$n";
    if ($startYr == $n )
    {
        echo " selected";
    }
    echo "> $n\n";
}
    echo "</select>\n";
    echo "</form>\n";
?>
</body></html>
```

The Web page produced by the program in Listing 8-9 is shown in Figure 8-10. The date appears above the form so that you can see that the select list shows the correct date. The selection list for the month shows all 12 months when it drops down. The selection list for the day shows 31 days when it drops down. The selection list for year shows four years.

The program in Listing 8-9 produces the Web page in Figure 8-10 by following these steps:

+   1. **Creates an array containing the names of the months.** The keys for the array are the numbers. The first month, January, starts with the key 1 so that the keys of the array match the numbers of the months.