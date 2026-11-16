```
19 Response.Redirect(MM_ouathFailedURL)
20 End If
21 %></22 <%
23 <%
24 Dim dbConn
25 Dim rs_countries
26 Set dbConn = Server.CreateObject("adodb.connection")
27 dbConn.open("newland")
28 Set rs_countries = dbConn.Execute("SELECT countryID, countryName FROM tbl_country ORDER BY countryName A")
29 %></30 <%
31 <!DOCTYPE HTML PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-t...
32 <html xmlns="http://www.w3.org/1999/xhtml">
33 <head>
```

Aside from the details of the SQL statement, this code is identical to that used earlier in this lesson, so you should understand it. The query itself is also easy to read: It retrieves the country name and unique ID, ordered by country name.

+   **3) ASP and PHP users only: Add the code to close and destroy the recordset at the end of the document.**

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

+   **4) Switch to design view, and type the following two lines of text:**

Select a country to modify or delete.

Caution: Deleting is instant and permanent.