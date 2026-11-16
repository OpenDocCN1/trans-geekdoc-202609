
The update form is complete, and the worst is over.

![](img/43fd0127a958864ab2d93e28efe683e7_494_0.png)

## ADDING THE UPDATE FUNCTIONALITY

After the preceding task, the last two tasks will be anticlimactic. In this task, you'll create the update processor page.

- 1) Open admin_cp_update_processor.asp in code view. Delete any code you see.

Once again, you'll be starting from a blank slate when producing this script-only page.

- 2) Write the code that creates the database connection.

In ASP:

```
<%
Dim dbConn
set dbConn = server.CreateObject("adodb.connection")
dbConn.open("newland")
%>
```

In ColdFusion:

```
<cfquery name="update_cp" datasource="newland">
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
?>
```

Now that you've got your connection, you can add the SQL.

## 3) Enter the code necessary to update the database in the blank line you left in the preceding step.

In ASP (all on one line):

```
dbConn.Execute("UPDATE tbl_country SET region='" & Request.Form("region") & '", countryName='" & Request.Form("countryName") & '", population='" & Request.Form("population") & '", country_currency='" & Request.Form("country_currency") & '", description='" & Request.Form("description") & '", imageURL='" & Request.Form("imageURL") & '", imageALT='" & Request.Form("imageALT") & '" WHERE countryID=" & Request.QueryString("countryID"))
```

In ColdFusion (you can use multiple lines):

```
UPDATE tbl_country
SET region='#form.region#',
countryName='#form.countryName#',
population='#form.population#',
country_currency='#form.country_currency#',
description='#form.description#',
imageURL='#form.imageURL#',
imageALT='#form.imageALT#'
WHERE countryID=#URL.countryID#
```

In PHP:

```
//Update database
$query_updateCountry = "UPDATE tbl_country SET region='.".$_POST['region']."',countryName='.".$_POST['countryName']."', population='.".$_POST['population'].',"', country_currency='.".$_POST['country_currency'].', description='.".$_POST['description'].' , imageURL='.".$_POST['imageURL'].', imageALT='.".$_POST['imageALT']."' WHERE countryID=".$_GET['countryID'];
$updateCountry = mysql_query($query_updateCountry);
```

Again, use code coloring to your advantage, especially ASP and PHP users. Also, make sure you don't inadvertently add a comma at the end of the element just before the WHERE clause.

```
<%
Dim dbConn
set dbConn = server.CreateObject("adodb.connection")
dbConn.open("newland")
dbConn.Execute("UPDATE tbl_country SET region='" & Request.Form("region") & "", countryName='" & Request.Form
%>
```

## 4) Insert the line of code needed to redirect the user back to the master page.

In ASP, in the line above the closing %> tag:

```
Response.Redirect("admin_cp_master.asp")
```

In ColdFusion, in the line after the closing </cfquery> tag:

```
<cflocation url="admin_cp_master.cfm">
```

In PHP, just before the closing ?> tag:

```
header("Location: admin_cp_master.php");
```

This returns the user to the master page, so she or he can conveniently verify that the modifications took place.

```
<%
Dim dbConn
set dbConn = server.CreateObject("adodb.connection")
dbConn.open("newland")
dbConn.Execute("UPDATE tbl_country SET region='" & Request.Form("region") & "", countryName='" & Request.Form
Response.Redirect("admin_cp_master.asp")
%>
```

## 5) Save and upload the file. Test the master page (F12), click a country, modify it, and click Submit. Return to that country's update page to change the value back.

The update functionality is complete and functional—at least for some of the countries. If you are using ASP, and you test using Argentina, 'Thailand, India, or a few others, you will see an error. The cause of the problem is that the text in the description or imageALT text areas contains an apostrophe character, which SQL misinterprets. (PHP and ColdFusion automatically escape this character, so ColdFusion and PHP users won't see this error.)

The solution to this problem is to remove all apostrophes from the text—which is not a reasonable business practice. Or is it?

In the next couple of steps, you will add some code that replaces the apostrophes with their HTML character entity equivalent (&#39;) automatically, just before the text is updated in the database. SQL will ignore the character entity (which is what we want), and when it is sent back to an HTML page, the browser correctly converts the character entity into an apostrophe. Neither the end user nor the user who maintains the Newland Tours site content will ever know that this happening behind the scenes. The only trace of this change, other than the ASP code you are about to write, is that &#39; will appear in the database in place of all apostrophes.

- 6) ASP Users Only: Return to admin_cp_update_processor.asp.

The find and replace script you'll add will appear on the processor page, just before the update is performed.

- 7) ASP Users Only: Add the following script after the opening <% and before Dim dbConn near the top of the page:

Dim description_fixed, imageALT_fixed
description_fixed = Replace(Request.Form("description"), "", "" ,"&#39;")
imageALT_fixed = Replace(Request.Form("imageALT"), "", "" ,"&#39;")

![](img/43fd0127a958864ab2d93e28efe683e7_497_0.png)

ASP has a built-in Replace() function, which takes (a) the text to be searched, (b) the string to search for, and (c) the string to replace it with as the first three parameters.

If you were to test the file now, you'd still get an error. That's because even though you've created a variable that holds the value of the two text fields, you don't insert the contents of that variable. You need to modify the SQL code.

- 8) ASP Users Only: Replace the two variables in the SQL statement, so that the UPDATE statement uses the fixed versions.

Replace description="" & Request.Form("description") & "", with description="" & description_fixed & "", and imageALT="" & Request.Form("imageALT") & "" with imageALT="" & imageALT_fixed & "".

As you complete this step, notice that the description portion is followed by a comma, while the imageALT portion (the last in the series) is not.

Request("country_currency") & "", descriptions="" & Request.Form("description_fixed") & "", imageURL="" & Request.Form("imageURL"

## 9) ASP Users Only: Save, upload, and test the page.

This time around, even countries that have descriptions and alt descriptions with apostrophes can be updated.

Now that you know how to fix the apostrophe problem, you can fix the insert country profile pages.

## 10) ASP Users Only: Return to admin_cp_insert_processor.asp and apply the fix here.

The changes in code that are necessary are virtually identical to those you input into admin_cp_update_processor.asp—the only difference is that the SQL statement looks slightly different, though what you have to replace is unchanged.

## ADDING THE DELETE FUNCTIONALITY

Writing the script for the delete processor page is even easier than writing the script for the update processor. Remember, users will access this page from the master page, which you have already built, so all that remains is to add the script that deletes the record from the database.

## 1) Open admin_cp_delete_processor.asp in code view, and remove any code.

Once again, this page will contain only a short script and a redirect elsewhere, so it needs no HTML code at all.

## 2) Add the code that creates the connection.

In ASP:

```
<%
Dim dbConn
set dbConn = server.CreateObject("adodb.connection")
dbConn.open("newland")
%>
```

In ColdFusion:

```
<cfquery name="delete_country" datasource="newland">
</cfquery>
```

In PHP:

```
<?php
// Set up connection to MySQL
$host = "localhost";
$User = "[enter your username]";
$pwd = "[enter your password]";
$dbConn = mysql_connect($host,$User,$pwd);
// Connect to newland_tours database
$database = "newland_tours";
mysql_select_db($database);
?>
```

Now you can insert the code that executes a SQL statement.

- 3) Add the code that deletes the record specified in the URL parameter, in the space you left in the preceding step.

In ASP (all in one line):
dbConn.Execute("DELETE FROM tbl_country WHERE countryID=" & Request.QueryString("countryID"))

In ColdFusion (may be on multiple lines):
DELETE FROM tbl_country
WHERE countryID=#URL.countryID#

In PHP:
$query_deleteCountry = "DELETE FROM tbl_country WHERE countryID=".$_GET['countryID'];
$deleteCountry = mysql_query($query_deleteCountry);

With SQL's DELETE statement, you don't have to specify each field singly, because it deletes from all fields, making it much more convenient to write. It also makes it easy to inadvertently wipe out your entire table, if you forget to specify the WHERE clause!

- 4) Add the redirection back to the master page, in the appropriate location.

In ASP, in the line above the closing %> tag:
Response.Redirect("admin_cp_master.asp")

In ColdFusion, in the line after the closing </cfquery> tag:
<cflocation url="admin_cp_master.cfm">

In PHP, before the closing ?> tag:
header("Location: admin_cp_master.php");
