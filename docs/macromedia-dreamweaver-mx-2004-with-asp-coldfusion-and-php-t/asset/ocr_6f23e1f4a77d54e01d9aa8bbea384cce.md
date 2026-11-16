# # PREPARING THE INPUT PAGE

Currently, the Country Profiles page (profiles.asp) contains a listing in static HTML of many of the countries to which Newland offers tours. The countries themselves will be listed on the second page, which you have yet to add. That means that just about all of the content on this page (excluding the banner) is obsolete, so you need to delete it.

Once you have removed all of the old content, you’ll need to add a list of links that will let users choose a country profile. Since this list will be dynamically generated, you’ll first need to create a recordset that contains the data required to create the links, which includes the countryName and countryID fields. In this task, then, you will clear out the old content and add the recordset needed to create the list of dynamic URLs.

+   1) Open profiles.asp in design view.

I find it much easier to delete page content while in design view, rather than hunting around for it in code view.

+   2) Drag to select everything on the page starting from the horizontal rule just above Namibia all the way down to the bottom of the table.

The yellow icon (representing the image map) at the bottom outside of the table should not be selected.

![](bbox=[0.273, 0.54, 0.942, 0.862])