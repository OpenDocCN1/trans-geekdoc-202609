4) Click the Advanced button to open the advanced version of the Recordset dialog. As you can see, this version of the dialog contains the SQL that you specified in the simple version of the dialog. You'll write the remaining code here in the SQL window.

TIP You can return to the simple version of the dialog by clicking the Simple button.

![](bbox=[0.07, 0.19, 0.68, 0.51])

5) Change the SQL statement in the window so that it reads as follows:

```
SELECT *
FROM tbl_tours INNER JOIN tbl_country
ON tbl_country.countryID=tbl_tours.country
ORDER BY tbl_country.countryName
```

The syntax for joins is hard to read for many people. However, this query does the exact same things as the following (easier to read) query:

```
SELECT *
FROM tbl_tours, tbl_country
WHERE tbl_country.countryID=tbl_tours.country
ORDER BY tbl_country.countryName
```

That is, it selects all records and fields from both tables. When it merges the two tables, it does so by matching the value in the country field of tbl_tours with the countryID field, which is the primary key of the tbl_country table. This ensures that the correct country's data is joined to each tour. In other words, the country Argentina (and all of its data as entered in tbl_country) is associated with Highlights of Argentina.