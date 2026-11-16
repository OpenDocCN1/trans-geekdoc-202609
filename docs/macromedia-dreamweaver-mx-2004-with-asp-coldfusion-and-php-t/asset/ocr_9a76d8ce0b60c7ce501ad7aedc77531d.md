```
<?php
$host = "localhost";
$user = "root";
$pwd = "priscilla";
$dbConn = mysqli_connect($host,$user,$pwd);

// $dbconn = "newland_tours";
$valSelect_db = mysqli_select_db($dbconn,
"newland_tours");
$query_rs_regions = "SELECT * FROM tbl_region ORDER BY regionName*";
$rs_regions = mysqli_query($dbconn,$rs_regions);
$row_rs_regions = mysqli_fetch_assoc($rs_regions);
$query_rs_countryDetail = "SELECT * FROM tbl_country INNER JOIN tbl_region ON tbl_region.regionID=tbl_country";
$rs_countryDetail = mysqli_query($query_rs_countryDetail);
$row_rs_countryDetail = mysqli_fetch_assoc($rs_countryDetail);
?>

```

Once again, most of this code should look familiar to you. It's worth deconstructing the SQL statement, though. Remember, tbl_country contains most of the information that Newfoundland tracks about a country. The exception is the region name, which is stored in a different table, and linked through a relationship to tbl_country. The SQL statement therefore uses JOIN to retrieve this additional information. Also of note, this SQL statement does not retrieve all of the country profiles—only the profile that the user selected on the master page, that's ID was sent as a querystring/URL variable.

> ASP user should also Dim the new variable, rs_countryDetail, near the top of the script where the other Dim statements appear. The code should still work without it, but it's good practice to declare all variables.

You now have all of the information about the selected country that Newfoundland keeps. You'll use this information to populate the form on the page with live data from the database. When users submit the form, a script will replace existing database data with the information in the form. Now that this data is available, you need to bind it as the default value of each respective form element.

+   4) ASP and PHP Users: Scroll down to the bottom of the page, and add the code necessary to close and destroy the recordset.

In ASP:

```
<%
rs_countryDetail.Close()
Set rs_countryDetail = Nothing
%>
```

In PHP:

```
<?php
mysql_free_result($rs_countryDetail);
?>
```