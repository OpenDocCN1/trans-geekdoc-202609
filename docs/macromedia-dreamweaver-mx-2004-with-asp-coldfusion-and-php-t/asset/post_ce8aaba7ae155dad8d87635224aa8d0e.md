
Understanding these lines is easier if you recall the basic syntax of an INSERT statement in SQL:

```
INSERT INTO tbl_table
(field1, field2, field3)
VALUES
('value1', 'value2', 'value3')
```

The ASP, ColdFusion, and PHP code blocks are constructing SQL statements that use this syntax. But again, since they are replacing variables with actual values, you need to let each server know to evaluate these expressions before it inserts them into the database. As a consequence, you'll see quite a few pound signs in the ColdFusion version, and a lot of concatenation in the ASP and PHP versions.

> **TIP** ASP and PHP users should use code coloring to their advantage. The coloring typically changes the moment you enter an error, making it easy to spot problems before you test the page. ASP: In all cases, Request.Form should be purple, while the form field name should always be green. The ampersands (&) used to concatenate should always be blue. PHP: In all cases, string literals (including all commas and single quotes) are red, $_POST is always light blue, while periods and square brackets are always dark blue.

> **NOTE** ASP and PHP use both double quotes ("") and single quotes (''), which can be confusing. Content enclosed in double quotes is a part of ASP/PHP, specifically, string literals that ASP/PHP should pass without evaluating. Content enclosed in single quotes belongs to SQL, and represents the values being inserted into the database.

- 4) Insert the code that redirects the user to the master page once the insert is completed.

In ASP, before the closing %>:

```
Response.Redirect("admin_cp_master.asp")
```

In ColdFusion:

```
<cflocation url="admin_cp_master.cfm">
```

In PHP, before the closing ?>:

```
header("Location: admin_cp_master.php");
```

Because ASP, ColdFusion, and PHP will display an error message if they experience problems, the redirect line will only be executed if the insertion is successful.

Test the page to make sure it works (you can just make up the details about your country). Once you insert your data, you'll be sent to an as-yet incomplete admin_cp_master.asp. But there's an easy way to see whether the insertion was successful: Go to the country profiles. Updating the country profiles is the whole point of this application. You should find your newly inserted country there. Don't worry about nonsense data—you'll be building a delete application later in the lesson, and you'll need a bogus country or two to test it, so just leave your creation in the database for now.

![](img/43fd0127a958864ab2d93e28efe683e7_478_0.png)

> **NOTE** As you test the functionality of these pages, do not enter any apostrophes in any of your descriptions. If you do, you'll see an error message. This issue is addressed later in the lesson.

> **NOTE** Unless you upload an image to the images folder with the same name as the one you enter in the form, the image link will be broken.

## CREATING THE MASTER PAGE

A master-detail page pairing is necessary for the update and deletion functionality,
because you have to allow the users to select which country they want to update or
delete. In this task, you'll create a simple master-detail page consisting of a table with
each country's name. a link to modify the country, and a link to delete the country
in a row. As before, each of these links will pass a URL parameter identifying the
country that the user has selected.

- 1) Open admin_cp_master.asp, and switch to code view.
  As before, you'll create the recordset before laying out the page, and since you'll
  handwrite the code necessary to create the recordset, you need to be in code view.

- 2) Between the Restrict Access server behavior code and the beginning of the
  document itself (just before the <!DOCTYPE> tag), enter the code necessary to
  create a recordset ("rs_countries") that retrieves the country name and ID of
  every record in tbl_country.
  In ASP:

```
<%
Dim dbConn
Dim rs_countries
set dbConn = Server.CreateObject("adodb.connection")
dbConn.open("newland")
Set rs_countries = dbConn.Execute("SELECT countryID, countryName FROM tbl_country ORDER BY countryName ASC")
%>
```

In ColdFusion:

```
<cfquery name="rs_countries" datasource="newland">
SELECT countryID, countryName FROM tbl_country ORDER BY countryName ASC
</cfquery>
```

In PHP:

```
<?php
// Set up connection to MySQL
$host = "localhost";
$user = "[enter your username]";
$pwd = "[enter your password]";
$dbConn = mysql_connect($host,$user,$pwd);
// Connect to newland_tours database
$database = "newland_tours";
mysql_select_db($database);
$query_rs_countries = "SELECT countryID, countryName FROM tbl_country ORDER BY
countryName ASC";
$rs_countries = mysql_query($query_rs_countries);
$row_rs_countries = mysql_fetch_assoc($rs_countries);
?>
```

```
19 Response.Redirect(MM_urlFailedURL)
20 End If
21 %>
22 <%
23 <%
24 Dim dbConn
25 Dim rs_countries
26 Set dbConn = Server.CreateObject("adodb.connection")
27 dbConn.open("newland")
28 Set rs_countries = dbConn.Execute("SELECT countryID, countryName FROM tbl_country ORDER BY countryName ASC")
29 %>
30 <%
31 <!DOCTYPE HTML PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-t...
32 <html xmlns="http://www.w3.org/1999/xhtml">
33 <head>
```

Aside from the details of the SQL statement, this code is identical to that used earlier in this lesson, so you should understand it. The query itself is also easy to read: It retrieves the country name and unique ID, ordered by country name.

- **3) ASP and PHP users only: Add the code to close and destroy the recordset at the end of the document.**

In ASP:

```
<%
rs_countries.Close()
Set rs_countries = Nothing
%>
```

In PHP:

```
<?php
mysql_free_result($rs_countries);
?>
```

Again, this code prevents the recordset from wasting memory on the server.

```
70 </body>
71 </html>
72 <%
73 rs_countries.Close()
74 Set rs_countries = Nothing
76 %>
```

- 4) Switch to design view, and type the following two lines of text:

Select a country to modify or delete.

Caution: Deleting is instant and permanent.

Again, providing directions for the user is critical to the success of your applications.

![](img/43fd0127a958864ab2d93e28efe683e7_481_0.png)

## Select a Country Profile to Modify or Delete

Select a country to modify or delete.

Caution: Deleting is instant and permanent.

- 5) Return to code view, and below the paragraph you just created, add the code to create a new table with one row and three columns.

```
<table width="98%" border="1" cellspacing="0" cellpadding="3">
<tr>
<td>XX</td>
<td>XX</td>
<td>XX</td>
</tr>
</table>
```

This creates the basic framework for the table. When you are done with it, its contents will be dynamically generated, with each record being mapped to a single row. Since you can't know the number of rows in advance, you'll have to loop through the recordset, creating a new row for each record.

- 6) Enter the appropriate code needed to create a looping structure that encloses the <tr> tag. The code should wrap outside the opening and closing <tr> tags.

In ASP:

```
<%
   Do Until rs_countries.EOF
   %>
   <tr>
   <td>XX</td>
   <td>XX</td>
   <td>XX</td>
   </tr>
   <%
   rs_countries.MoveNext()
   Loop
   %>
```

### In ColdFusion:

```
<cfoutput query="rs_countries">
<tr>
<td>XX</td>
<td>XX</td>
<td>XX</td>
</tr>
</cfoutput>
```

### In PHP:

```
<?php
 do {
 ?>
 <tr>
 <td>XX</td>
 <td>XX</td>
 <td>XX</td>
 </tr>
 <?php
 }
 while ($row_rs_countries = mysql_fetch_assoc($rs_countries));
 ?>
```

In this step, you are in effect creating a repeat region—you just aren’t using the Dreamweaver behavior. And in spite of their cosmetic differences, all three server models use remarkably similar logic. Each has a block of code before and after the section to be looped over (the <tr> section). Each specifies a query and creates a loop that breaks only when the recordset runs out of records: ASP’s EOF accomplishes this explicitly; the recordset loop is implied in ColdFusion; when you specify the query attribute in a <cfoutput> tag; and PHP tests using mysql_fetch_assoc().

Next, you need to build the contents of the table cells, which will contain a mix of HTML and ASP, ColdFusion, or PHP code.

![](img/43fd0127a958864ab2d93e28efe683e7_482_0.png)
