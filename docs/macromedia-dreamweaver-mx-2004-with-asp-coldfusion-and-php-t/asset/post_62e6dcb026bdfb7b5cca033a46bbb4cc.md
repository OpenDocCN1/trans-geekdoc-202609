

The Repeat Region behavior will add the necessary code to ensure that multiple records, rather than just the first one, will be displayed.

![](img/43fd0127a958864ab2d93e28efe683e7_297_0.png)

- 7) In the Repeat Region dialog, leave the Recordset field alone, and select All records from the Show radio group.

The Recordset option enables you to specify which recordset you want to repeat; however, there is only one on this page, so you don't have to enter any information in the field.

The Show options—Show [   ] Records at a time and Show All records enable you to create recordset paging. Some recordsets will output so many rows of data that the page becomes unmanageable, so results are broken into groups of 10 or 25 results at a time. Most search engines use this strategy. Because you only have 16 country names in your recordset, which is not too unwieldy, you can go ahead and show all of the records at once.

![](img/43fd0127a958864ab2d93e28efe683e7_297_1.png)

- 8) Save, upload, and test the file.

You should now see all 16 countries listed, and if you roll over (don't click!) each of the links, you should see a different countryID parameter for each.

The only problem is the formatting. All of the countries are listed side-by-side on a single, hard-to-read line (ASP and ColdFusion), or they are spaced too far apart (PHP).

![](img/43fd0127a958864ab2d93e28efe683e7_298_0.png)

![](img/43fd0127a958864ab2d93e28efe683e7_298_1.png)

What's happening is that ASP, ColdFusion, and PHP are using a loop structure. In programming, loops are structures that execute over and over again until something breaks them out of the loop. Loops are flow control structures, just like if...else structures. The difference is that if...else structures execute once based on one or more conditions, while loops execute repeatedly until a given condition is met.

You created the loop by making the dynamic text a repeated region. A repeated region is an output block of text that is inside of a loop, causing the same region to be output multiple times. The region in this case is the country name and its link. The condition that must be met before the loop is broken and the remainder of the page is processed is that all of the records in the recordset are displayed.

- 9) Return to Dreamweaver, and switch to code view, finding the dynamic code just below the body text paragraph that begins “The following list shows…”.

To understand why the display problem is happening, you need to look at the loop structure directly and identify why the output is not displaying correctly. As usual, I strongly encourage you to understand what’s going on in all three code blocks, and not just in the server model you are using.

## THE ASP BLOCK

In ASP, the code Dreamweaver wrote for us to handle this functionality is as follows:

```
<%
    While ((Repeat1__numRows <> 0) AND (NOT rs_countryNames.EOF))
    %>
    <a href="profiles_detail.asp?countryid=<%= (rs_countryNames.fields.item("countryid").value) %>"><%= (rs_countryNames.Fields.Item("countryName").Value) %></a>
    <%
    Repeat1__index=Repeat1__index+1
    Repeat1__numRows=Repeat1__numRows-1
    rs_countryNames.MoveNext()
    Wend
    %>
```

This is an eyeful for nonprogrammers, but it’s important to at least get the gist of what’s going on. Notice that there are two ASP blocks (each with opening and closing <% %> tags). The top one contains a while statement: while is used to begin loops, and its parameter (the code in parentheses) is the condition that causes the loop to stop. In VBScript, EOF refers to end of file, so the condition says to break the loop when there are no more records to process. The bottom ASP block contains the code that actually advances through the loop one record at a time and eventually ends the loop (Wend).

Nested in between these two loop code blocks is the code that’s looped; it is the link itself. Notice that after the closing </a> tag in this code, there is no <br /> tag, which would add a line break after each URL. You’ll need to manually add that code at the end of that line of text to get the page to display properly. (You’ll do so momentarily.)

## THE COLDFUSION BLOCK

The ColdFusion block, predictably, is a lot simpler.

```
<p><a href="profiles_detail.cfm?countryID=<cfoutput>#rs_countryNames.countryID#</cfoutput>"><cfoutput query="rs_countryNames">#rs_countryNames.countryName#</cfoutput></a></p>
```

The first thing you should notice, assuming you read the deconstruction of the ASP script, is that there is no apparent loop structure. As a matter of fact, a loop is in play; but ColdFusion hides it behind the simple tag syntax. Anytime you use <cfoutput> and list a query as an attribute within that tag, ColdFusion automatically loops. The condition that breaks the loop—when ColdFusion reaches the end of the recordset—is implied.

The specific problem is that looping occurs only within the <cfoutput> tags, and there is no <br /> or <p> tags inside that block to create line breaks. A secondary problem is that Dreamweaver has generated two <cfoutput> blocks, where only one is needed.

You'll fix both problems momentarily.

## THE PHP BLOCK

The PHP block more closely resembles the ASP block:

```
<?php do { ?>
<p><a href="profiles_detail.php?countryID=<?php echo $row_rs_countryNames['countryID']; ?>"><?php echo $row_rs_countryNames['countryName']; ?></a>
<?php } while ($row_rs_countryNames = mysql_fetch_assoc($rs_countryNames)); ?>
```

The looping structure in PHP is performed by a do..while structure. The do portion appears in the first line of the code block, and the while portion appears in the final line. In between, of course, is the line that creates the country name listing and the hyperlink with the proper countryID passed as a URL parameter.

To determine how many loops are necessary, this code block references the recordset itself, using mysql_fetch_assoc(). When you query a database using mysql_query() in conjunction with a SELECT statement, the returned data is not immediately available to PHP. To get to the data, you have to "fetch" it, using one of PHP's various functions for that purpose, including mysql_fetch_assoc(). This function returns one record (or row) of data at a time, which in the preceding code block is assigned to the $row_rs_countryNames variable. Thus, to return all of the rows, you need to loop through the recordset. Every time through the loop, the value of $row_rs_countryNames changes and it outputs accordingly into HTML.

> **NOTE** _The first time through the loop, the default value for $row_rs_countryNames is used; this value is set near the top of the document in the main query block itself, in line 6 on my page._

Now that you understand how the code works, you probably can already see what the problem is: each time the code loops, it prints a block of text wrapped by an `<p></p>` tag pairing. And `<p>` tags are block-level HTML elements that output with extra space. In other words, you need to replace the `<p>` tags with a `<br />` tag. You'll add it momentarily.

Thus all three server models (ASP, ColdFusion, and PHP) are not quite looping what we want, and that is why the display on the page is not right. In all cases, all we need to do is modify the code being looped over, so that there are no paragraph tags inside the loop, and so that there is a line break after each link. This obviously is an easy solution—but it is only easy if you look at the code and take a moment to understand what's going on.

The solution varies somewhat by server model.

- 10) All server models: Find the closing `</a>` tag inside the loop, and immediately after it, insert a `<br />` tag.

This line break fixes the display problem from before for ASP and PHP. ColdFusion users need to complete one more step.

![](img/43fd0127a958864ab2d93e28efe683e7_301_0.png)

- 11) PHP users only: Move the opening `<p>` tag so that it is before the opening `<?php do` line; likewise, move the closing `</p>` tag so that it is outside the closing `<?php } while` line (but before the closing `</td>`.

This takes care of the nesting problem. Now, effectively all elements output by the loop are in a single paragraph, separated with line breaks (`<br />`).

The final PHP block should look as follows:

```
<p><?php do { ?>
<a href="profiles_detail.php?countryID=<?php echo $row_rs_countryNames['countryID']; ?>"><?php echo $row_rs_countryNames['countryName']; ?></a><br />
<?php } while ($row_rs_countryNames = mysql_fetch_assoc($rs_countryNames));
?></p></td>
```

![](img/43fd0127a958864ab2d93e28efe683e7_301_1.png)
