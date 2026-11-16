4) **In code view, find the calculation script. Delete the line that sets the value of the basePrice variable to the form variable tourName.**

The line in ASP that you are deleting is basePrice=Request.Form("tourName"), and it should be around line 34 (plus or minus) in code view.

The line in ColdFusion that you are deleting is <cfset basePrice = form.tourName>, and it should be around line 14 (plus or minus) in code view.

The line in PHP that you are deleting is $basePrice = $_POST['tourName'];, and it should be around line 12 in code view.

This line is no longer necessary, because you are not obtaining the base price from the form anymore, but rather from the database. In addition, there are two prices that you now need to use: the one for children and the one for adults.

```
25   IF Not IsNumeric(Request.Form("numAdults")) Or Not IsNumeric(Request.Form("numChildren")) Then
26      Response.Redirect("tourprice.asp?error=notnumeric")
27   End If
28  >
29  <%
30   <%
31   Dim numAdult, numChild, basePrice, tourPrice
32   numAdult = Request.Form("numAdults")
33   numChild = Request.Form("numChildren")
34   basePrice = Request.Form("tourName")
35   tourPrice = (numAdult * basePrice) + (numChild * basePrice)
36   %>
37
38   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-t
39   <html xmlns="http://www.w3.org/1999/xhtml">
40   <head>
```

# 5) **Add two new lines of code that set the value of two new variables: basePriceAdult and basePriceChild.**

```
In ASP:

basePriceAdult=rs_tourprices_filtered.Fields.Item("basePriceAdult").Value
basePriceChild=rs_tourprices_filtered.Fields.Item("basePriceChild").Value
```

```
In ColdFusion:

<cfset basePriceAdult = rs_tourprices_filtered.basePriceAdult>
<cfset basePriceChild = rs_tourprices_filtered.basePriceChild>
```

```
In PHP:

$basePriceAdult = $row_rs_tourprices_filtered['basePriceAdult'];
$basePriceChild = $row_rs_tourprices_filtered['basePriceChild'];
```