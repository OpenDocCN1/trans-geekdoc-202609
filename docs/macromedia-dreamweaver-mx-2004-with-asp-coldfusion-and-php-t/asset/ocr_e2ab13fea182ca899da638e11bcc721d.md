3) Use the Bindings panel to create a new recordset, using the following settings:
Name: rs_countries
Connection: conn_newland
Table: tbl_country
Columns: Selected, countryName
Filter: None
Sort: countryName, Ascending

If you press the Test button, you’ll see that this recordset produces a list of all the countries in tbl_country in alphabetical order. You’ll use this to build the drop-down menu in the form.

![](bbox=[0.29, 0.295, 0.81, 0.575])

4) Click to select the menu, and in the Property inspector, name it tourCountry.
Click the Dynamic button to open the Dynamic List/Menu dialog. Select rs_countries from the Options from recordset menu. Leave the Values and Labels at the default, countryName, and click OK.

You’ve done this before, so the consequence of these steps should not be a mystery. When the page is displayed in a browser, the country names will populate the menu in alphabetical order. When the user clicks Submit, tours_detail.asp will load (that was specified in the form’s action attribute), and the name-value pair tourCountry=Argentina (or whichever country the user selected) will be sent as a form variable.