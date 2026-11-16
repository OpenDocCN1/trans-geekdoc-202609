
> NOTE Although WHERE EXISTS and subqueries in general are a part of the ANSI standard for SQL, they are not supported in MySQL. If you enter this code in MySQL, you will get an error. Because of this, PHP users can't complete this step and will have to deal with this problem another way. The best solution in this case would be to have separate development and production databases and only upload data from development to production when it is ready. Of course, this project is entirely fictional anyway, so don't worry about it for the rest of this book—just don't follow the Taiwan link on tours.php.

Click the Test button to see the results. You should now see 15, rather than 16 countries listed. Taiwan is no longer in the group. If a tour to Taiwan is added to tbl_tours, then Taiwan will be listed in the menu once again, because it would meet the EXIST criterion.

| Record | countryname |
| :--- | :--- |
| 1 | Argentina |
| 2 | Canada |
| 3 | Egypt |
| 4 | France |
| 5 | India |
| 6 | Israel |
| 7 | Italy |
| 8 | Japan |
| 9 | Mexico |
| 10 | Morocco |
| 11 | Namibia |
| 12 | Peru |
| 13 | Thailand |
| 14 | United Kingdom |
| 15 | United States |

- 9) Save and close tours.asp.

## SWITCHING SQL STATEMENTS ACCORDING TO ENVIRONMENTAL VARIABLES

You know from testing that each of the interfaces works—as long as two of the SQL statements are commented out. That setup is just fine for testing, when you can open the document and apply the correct commenting based on your needs, but obviously it needs help before it can go into production. You need an automated way of switching the query based on the type of search. Your first task is to identify how tours_detail.asp will know which search type the user has chosen. Then, based on that, you need to swap in the proper SQL statement. An if...else construct is perfect for swapping the correct SQL statement in, but how does it know which search type the user submitted?

Back in a previous lesson, you implemented server-side form validation. The way it worked was that it checked to see whether a form variable called numadults or numchildren existed and was numeric. If it didn’t exist, or it wasn’t numeric, the user was redirected back to the form on the tour price page to fix the problem. I remind you of this because it provides a strategy for determining which search type the user selected: Check for the presence or absence of certain variables, as follows:

- If no form or URL variables are present, then the user clicked the View All Tours link.
- If a URL variable is present, then the user clicked one of the Region links.
- If a form variable is present, then the user selected a country from the form menu.

With this information, you can construct the logic for the script you need to write. The following pseudocode spells out the logic. Statements in parentheses are the conclusions you can draw from certain information; however, these won’t be explicitly written into the final script.

```
If no form variable exists //either the user clicked View All Tours or clicked a
=>region link
If no URL variables exist //the user clicked the View All Tours link
Run the first query
Else a URL variable does exist //the user clicked a region link
Run the second query
Else a form variable does exist //the user selected a country from the form menu
Run the third query
```

Looking at this pseudocode, you’ll notice that it will require a pair of if...else structures, one nested inside the other. That’s because one of the conditions—the absence of a form variable—can be true for two different reasons: because the user clicked the View All link and there are no URL variables, or because the user clicked a region link and there is a URL variable.

- 1) Open tours_detail.asp in code view. Find the three lines of SQL code, and remove the comments from all of them. Add a few line breaks above and below them, to isolate them in your code.

In this step, you are preparing to wrap the if...else script around these lines of SQL. You don't want to disturb the neighboring code. Once ASP or ColdFusion determines which SQL query to execute, it will be as if the other two never existed.

```
Set rs_tourDetail = Server.CreateObject("ADODB.Recordset")

rs_tourDetail.ActiveConnection = MM_conn_newland_STRING

rs_tourDetail.Source = "SELECT * FROM tbl_tours INNER JOIN tbl_country ON tbl_country.countryID=tbl_tou...

rs_tourDetail.Source = "SELECT * FROM tbl_tours INNER JOIN tbl_country ON tbl_country.countryID=tbl_tou...

rs_tourDetail.Source = "SELECT * FROM tbl_tours INNER JOIN tbl_country ON tbl_country.countryID=tbl_tou...

rs_tourDetail.CursorType = 0
rs_tourDetail.CursorLocation = 2
rs_tourDetail.LockType = 1
rs_tourDetail.Open()
```

- 2) Just above the top line of SQL, write the line of code that tests for the existence of the form variable.

In ASP:
```
If IsEmpty(Request.Form("tourCountry")) Then
```

In ColdFusion:
```
<cfif Not IsDefined("form.tourCountry")>
```

In PHP:
```
if (!isset($_POST['tourCountry'])) {
```

Like all if statements, this can evaluate to true or false. If it's true (that is, the form variable does not exist), then the script still has to determine whether a URL variable exists. It's false, then we know that the user has selected a country from the form, and we can execute the third query.

- 3) Indent all three SQL statements at once, using the Tab key. Create a new line above the third SQL statement, and enter the script that will execute that line of code.

### In ASP:

```
Else
```

### In ColdFusion:

```
<cfelse>
```

### In PHP:

```
} else {
```

When an if statement evaluates to false, the interpreter looks for any else if or else statements. If it sees them, it executes them. By adding this code here, you ensure that if the form variable is present, then the SQL statement that filters with that variable is run.

- 4) After the third line of SQL, close the if...else block.

### In ASP:

```
End If
```

### In ColdFusion:

```
</cfif>
```

### In PHP:

```
}
```

```
9   If IsEmpty(Request.Form("tourCountry")) Then
10      rsTourDetail.Source = "SELECT * FROM tbl_tours INNER JOIN tbl_country ON tbl_country.countryID=tb
11      rsTourDetail.Source = "SELECT * FROM tbl_tours INNER JOIN tbl_country ON tbl_country.countryID=tb
12  Else
13      rsTourDetail.Source = "SELECT * FROM tbl_tours INNER JOIN tbl_country ON tbl_country.countryID=tb
14  End If
```

You are halfway there. In fact, if you uploaded this page now and accessed it by selecting a country and clicking Submit in the form on tours.asp, it would work as expected. But if you tried to access the page any other way, you would get an error, because it would try to execute both of the other two queries at the same time.

- 5) Indent the top two lines of SQL one more time. Above the first line of SQL, enter an if statement that checks for the presence of the URL variable.

In ASP:
```
If IsEmpty(Request.QueryString("regionID")) Then
```

In ColdFusion:
```
<cfif Not IsDefined("url.regionid")>
```

In PHP:
```
if (isset($_GET['regionID'])) {
```

If this, too, evaluates to true, then neither the form nor URL variable is present, and the broadest SQL query—the first one—should run. That query is directly below this line, so if it is indeed true, then that query will run.
If it is false, then the URL variable is present, and the second SQL query should run.

- 6) In the line between the top two queries, enter the code necessary to activate the second query.

In ASP:
```
Else
```

In ColdFusion:
```
<cfelse>
```

In PHP:
```
} else {
```

Again, the only way this code can be executed is if the form variable is not present, but the URL variable is.

- 7) In the line after the second SQL statement, enter a new line to close the nested if block.

In ASP:
```
End If
```

In ColdFusion:
```
</cfif>
```

In PHP:
```
}
```

These lines complete the nested if block, the lesson, and the tour search and display application.

```
9    If IsEmpty(Request.Form("tourCountry")) Then
10    If IsEmpty(Request.QueryString("regionID")) Then
11    rs_tourDetail.Source = "SELECT * FROM tbl_tours INNER JOIN tbl_country ON tbl_country.countryID
12 Else
13    rs_tourDetail.Source = "SELECT * FROM tbl_tours INNER JOIN tbl_country ON tbl_country.countryID
14 End If
15
16 Else
17    rs_tourDetail.Source = "SELECT * FROM tbl_tours INNER JOIN tbl_country ON tbl_country.countryID=tbl
18 End If
19
```

- 8) Save and upload this file. Test tours.asp in your browser, going back and forth trying every kind of search available.

The application should be bulletproof at this point. You should see all (and only) the tours that meet your search criteria. The Recordset Navigation Bar should show or hide, based on the number of records returned from your search. If you click a tour's country, you should see its profile. If you click a tour's Tour Price Calculator link, you should go to that application, and the tour should be preselected in the menu. In short, your users should now have a pretty slick interface through which to learn more about Newland Tours offerings.
