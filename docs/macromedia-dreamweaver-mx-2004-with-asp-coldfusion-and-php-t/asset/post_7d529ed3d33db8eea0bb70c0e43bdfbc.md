
**TIP** Remember, in ASP, the & character is used to concatenate, or connect, text strings. The . character in PHP has the same purpose. Concatenation is necessary in both cases, because you are mixing literal strings (the majority of the SQL statements) that ASP or PHP should pass on without evaluating, and special ASP or PHP code that ASP/PHP should evaluate, such as ASP's `Request.QueryString()` and PHP's `$_GET()`. Strings are in quotes, while expressions are not. Combining the two requires you to concatenate—hence the use of & and . in these code blocks. ColdFusion doesn't have this problem, because it uses hash signs (#...#) to mark up expressions that ColdFusion should evaluate.

So what does this addition to the query do? It creates another criterion, which further limits the original search. The original search retrieves all of the information needed to build all of the tour descriptions. This query does that, too, except it limits the set to those tours whose countries share the same regionID as the one passed as a URL parameter.

Let's look at an example. Each tour has a field specifying its country. This country listing is, as you'll recall, a foreign key, which points to tbl_country. So both tours that take place in France have the countryID for France as one of their records. This shared field links the tours table to the country table, in this case, linking all tours in France to the record for the country France in tbl_country.

One of the fields that each country has is a foreign key for the region table. Thus, the record for France has a 3 in its region field, because 3 is the regionID for Europe, which contains France. Europe also contains the United Kingdom and Italy, so each of these countries' region fields also contains a 3. Japan's region value is 4, which is the regionID for East Asia. Therefore, all of the tours that list Japan as their country are related to a regionID of 4, and not of 1 or 3. Because Thailand is also in East Asia and has a regionID of 4, all of its tours are related to regionID 4.

To summarize, then, each regionID has a one-to-many relationship with countries. That is, each region may have several countries that belong to it. Likewise, each country has a one-to-many relationship with tours, which means that a single country can have multiple tours. However, no country can belong to multiple regions, and no tour can go to multiple countries. Therefore, you can write a query that retrieves tours where the tour's country belongs to a given region, and only those tours will be retrieved, and all others will be excluded.

That's what you've specified with this `WHERE` clause in the SQL statement. Test the file to make sure it works as expected.

- 4) Save, upload, and close tours_detail.asp. Select tours.asp in the Site panel, and press F12 to test that file.

You cannot test tours_detail.asp directly, because you would get an error. The SQL query that you just wrote needs the regionID URL variable to execute. If you test the page directly, that variable won’t be available, which will break the SQL query and return an error.

- 5) Click any of the regions in the menu on the page.

After you click, you should see only tours from that region displayed on the page, so that part of the functionality works.

![](img/43fd0127a958864ab2d93e28efe683e7_370_0.png)

But there’s some bad news as well: The Recordset Navigation Bar table is still visible. All of its cells are empty, because no region (at the moment) has more than five tours, so the page is always the first and last page. Remember, the Repeat Region server behavior on this page that displays the tours is limited to showing five records per page. It would be good to hide the Recordset Navigation Bar, when the page is the first and last page, that is, when five or fewer records are showing. But if that number ever exceeds five (say, for example, Newland adds tours to Germany, Norway, and Spain next year), the Recordset Navigation Bar needs to be made visible again.

## SUPPRESSING THE NAVIGATION BAR

As always, before you start coding, you should spell out exactly what it is you are trying to accomplish. You want to show the Recordset Navigation Bar, which is stored in a table, if the number of tours displayed on the page is greater than five (that is, six or more). Remember the page is set to show only five records at a time. However, if there are five or fewer, then the Recordset Navigation Bar can’t be activated, and so you don’t want it to appear.

As usual, the ASP, ColdFusion, and PHP code are different, but they all use the same concept.

- 1) Still in tours_detail.asp, using split view and the tag selector, select the table containing the Recordset Navigation Bar.

You have selected the entire table in both design and code views. You’ll need to work in code view in the next step, but you have to isolate the table, because you’ll need to add code above and below it to cause it to show conditionally. Here is a case where split view simplifies finding an element buried in code.

Or as an option, you can add a few extra lines of white space above and below the table to help set it off.

![](img/43fd0127a958864ab2d93e28efe683e7_371_0.png)

- 2) In code view, just before the table begins, enter the opening half of the script that controls the visibility of the table based on the number of records.

In ASP:

```
<% If (MM_acTotal = false Or Not IsEmpty(Request.QueryString("offset"))) Then %>
```

In ColdFusion:

```
<cfif rs_tourDetail.recordcount gt 5>
```

In PHP:

```
<?php if ($totalPages_rs_tourDetail != 0) { ?>
```

When you create a recordset, not only is the data in the recordset itself stored in memory on the server, so too is some basic information about that data. One piece of information available to ASP, ColdFusion and PHP is the record count, or number of records retrieved by the query. In ASP and ColdFusion, the variable that holds the total number of records is RecordCount, accessed as follows: rs_myQuery.recordcount. PHP's equivalent is mysql_num_rows(), accessed as follows: mysql_num_rows($rs_myQuery). (In both examples, rs_myQuery is the fictional name of a recordset you hypothetically created.)

Any time you are dealing with looping through records or paging through records, the RecordCount variable (ASP and ColdFusion) or mysql_num_rows() (PHP) function can be a great help. In the immediate situation, there is a catch: Scripts generated by server behaviors that you've already applied are using these variables. If you use them again, your scripts may collide in unexpected ways. Thus, you worked around these problems in the ASP and PHP scripts by working with variables created by the server behaviors.

Now let's look at the scripts themselves. In the ColdFusion version of the script, by far the most straightforward one, you are telling the server that if the record count is greater than five (the number of records you can show onscreen at any given time), then execute whatever comes after this line. What comes after it is the table that contains the Recordset Navigation Bar. If the number of recordsets is less than five (so that the if statement evaluates to false, then the script jumps ahead to the closing of the if structure (you haven't created the closing just yet) and continues. In other words, if the number of records is less than five, the table that contains the Recordset Navigation Bar does not appear. This flexible structure is convenient, because no matter what happens in the database—if new tours are added or removed—the Recordset Navigation Bar will be available if and only if it is needed.

The ASP version is written to make use of a pair of variables generated by the Recordset Navigation Bar object you inserted in the previous lesson. Understanding exactly how this line works presupposes some understanding of the VB code output by the Recordset Navigation Bar, and the nearly 300 lines of code that make up that script gets somewhat beyond the scope of what you are learning in this book. The condensed version is that the script detects when too many records were returned to fit on a page. If that’s true, then the table holding the recordset navigation bar is displayed; otherwise, it is hidden.

```
'Repeat__NumRows=__Repeat__Params__1
num_row_Total = num_row_Total+1
rs_tourDetail.MoveNext()
Wend
%>
<% If (MM_acTotal = false Or Not IsEmpty(Request.QueryString("offset"))) Then %>
<table width="50%" borders="1" align="center" cellpadding="3" cellspacing="0">
<tr>
<td width="23%" align="center">
<% If MM_offset <> 0 Then %>
<a href="<%MM_moveFirst%>">First</a>
<% End If %>
```

The PHP version of the script is a little more complex. An existing server behavior has created the $totalPages_rs_tourDetail variable, which the script uses to keep track of the total number of pages of records, a figure that is derived from the total number of records and the number of records displayed per page. This variable is also initialized to 0, which means (odd as it may seem) that if there is one page of records, its value is 0, and if there are three pages of records, then its value is 2. Thus, you know that if this value is not 0 (the operator != means “is not equal to”), then there are two or more pages, and the recordset navigation bar is needed. Conversely, if the value is 0, then the whole if block is skipped, and the recordset navigation bar is never displayed.
