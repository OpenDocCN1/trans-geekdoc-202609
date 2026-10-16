```
<td>{$petInfo[$i]['petDescription']}</td>\n    <td align='right'>$$f_price</td>\n    </tr>\n";\n    echo "<tr><td colspan='4'><hr></td></tr>\n";\n}\n echo "</table>\n";\n?>\n</body></html>\n\n<?php\nfunction getPetsOfType($petType)\n{\n    $db = mysql_select_db("PetCatalog")\n        or die ("Couldn't select database");\n    $query = "SELECT * FROM Pet WHERE petType='$petType'";\n    $result = mysql_query($query)\n        or die ("Couldn't execute query.");\n\n    $j = 1;\n    while ($row=mysql_fetch_array($result,MYSQL_ASSOC))\n    {\n        foreach ($row as $colname => $value)\n        {\n            $array[$j][$colname] = $value;\n        }\n        $j++;\n    }\n    return $array;\n}\n?>
```

The program in Listing 8-4 proceeds as follows:

+   1. It connects to the MySQL server in the main program.
+   2. It calls the function getPetsOfType. It passes "horse" as a character string and also sets up $petInfo to receive the data returned by the function.
+   3. The function selects the database PetCatalog.
+   4. The function sends a query to get all the rows with horse in the petType column. The data is stored in a table in a temporary location. The variable $result identifies the location of the temporary table.
+   5. It sets up a counter. $j is a counter that is incremented in each loop. It starts at 1 before the loop.
+   6. It starts a while loop. The function attempts to get a row from the temporary data table and is successful. If there were no rows to get in the temporary location, the while loop would end.