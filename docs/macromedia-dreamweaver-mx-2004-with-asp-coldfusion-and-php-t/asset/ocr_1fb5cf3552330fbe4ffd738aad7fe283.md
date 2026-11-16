4) Position the cursor in between the commas, where you would enter someone's name. Open the Bindings panel (Window > Bindings).

The Bindings panel is used to specify all of the data that is available to the page. Data is typically stored in a name-value format. In this particular case, the name is firstName. The value doesn’t yet exist—it won’t exist until someone fills out the form. Remember also that this value comes to the page from a form on the test_form.asp page. Other possible sources besides forms (and you’ll get quite familiar with these later) include the URL, a recordset (data retrieved from a database), a cookie, and more. But this time, it’s from a form.

![](bbox=[0.26, 0.27, 0.45, 0.47])

5) Click the + button to add a new binding. From the menu, choose Request Variable (ASP) or Form Variable (ColdFusion and PHP). In the resulting dialog, for ASP, select Request.Form in the Type Menu and type firstName in the Name field, or for ColdFusion or PHP type firstName in the Name field. Click OK.

The first screenshot shows the Request Variable dialog, which ASP users see, while the second one shows the Form Variable dialog, which ColdFusion and PHP users see.

![](bbox=[0.26, 0.66, 0.92, 0.76])

The Bindings panel is updated to show the firstName variable. The screenshot shows what the Bindings panel looks like in ASP. It looks slightly different in GoldFusion and PHP (the word Request is replaced with Form, and the word Form.firstName is replaced with firstName).