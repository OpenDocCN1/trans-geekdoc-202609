# THE COLDFUSION BLOCK

The ColdFusion block, predictably, is a lot simpler.

```
```
<p><a href="profiles_detail.cfm?countryID=<cfoutput>#rs_countryNames.countryID#</cfoutput>"><cfoutput query="rs_countryNames">#rs_countryNames.countryName#</cfoutput></a></p>
```
```

The first thing you should notice, assuming you read the deconstruction of the ASP script, is that there is no apparent loop structure. As a matter of fact, a loop is in play; but ColdFusion hides it behind the simple tag syntax. Anytime you use <cfoutput> and list a query as an attribute within that tag, ColdFusion automatically loops. The condition that breaks the loop—when ColdFusion reaches the end of the recordset—is implied.

The specific problem is that looping occurs only within the <cfoutput> tags, and there is no <br /> or <p> tags inside that block to create line breaks. A secondary problem is that Dreamweaver has generated two <cfoutput> blocks, where only one is needed.

You'll fix both problems momentarily.

# THE PHP BLOCK

The PHP block more closely resembles the ASP block:

```
```
<?php do { ?>
<p><a href="profiles_detail.php?countryID=<?php echo $row_rs_countryNames
=>['countryID']; ?>"><?php echo $row_rs_countryNames['countryName']; ?><?php
while ($row_rs_countryNames = mysql_fetch_assoc($rs_countryNames)); ?>
```
```

The looping structure in PHP is performed by a do..while structure. The do portion appears in the first line of the code block, and the while portion appears in the final line. In between, of course, is the line that creates the country name listing and the hyperlink with the proper countryID passed as a URL parameter.

To determine how many loops are necessary, this code block references the recordset itself, using mysql_fetch_assoc(). When you query a database using mysql_query() in conjunction with a SELECT statement, the returned data is not immediately available to PHP. To get to the data, you have to "fetch" it, using one of PHP's various functions for that purpose, including mysql_fetch_assoc(). This function returns one record (or row) of data at a time, which in the preceding code block is assigned to the $row_rs_countryNames variable. Thus, to return all of the rows, you need to loop through the recordset. Every time through the loop, the value of $row_rs_countryNames changes and it outputs accordingly into HTML.

> **NOTE** _The first time through the loop, the default value for $row_rs_countryNames is used; this value is set near the top of the document in the main query block itself, in line 6 on my page._