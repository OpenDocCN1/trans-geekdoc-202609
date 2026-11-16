Again, this frees up memory on the server, once your page no longer needs the recordset.

# 5) In code view, find the countryName form element. Give it a value attribute, as follows:

```
value="XX"
```

This is standard HTML, so it is the same for ASP, ColdFusion, and PHP. If you were to test the page now, the letters XX would appear in the Country Name field.

> TIP If you do test this page during the lesson, remember that it is expecting a querystringURL parameter. If one is not supplied (and one never is when you press F12), you will see an error. To solve this problem, at the end of the URL in the Address/Location bar in your browser, type the following: ?countryID=3 and press Enter/Return. Doing so provides the necessary information for the query to run and the error is removed.

# 6) Replace the XX placeholder with the dynamic value, as follows:

In ASP:

```
<%=rs_countryDetail("countryName")%>
```

In ColdFusion:

```
<cfoutput>#rs_countryDetail.countryName#</cfoutput>
```

In PHP:

```
<?php echo $row_rs_countryDetail['countryName']; ?>
```

This way, when the page loads, the proper country name appears by default in the field. If users modify it, then the country's name will be updated in the database. If the user leaves it alone, then strictly speaking, the form value will still replace the value in the database, but since they are the same, nothing will change.

![](bbox=[0.07, 0.675, 0.735, 0.72])

# 7) Using the correct ASP, ColdFusion, or PHP syntax, repeat steps 5 and 6 for each of the remaining text field elements, using the following information (provided in pseudocode):

Population: rs_countryDetail.population

Country Currency: rs_countryDetail.country_currency

Image URL: rs_countryDetail.imageURL,