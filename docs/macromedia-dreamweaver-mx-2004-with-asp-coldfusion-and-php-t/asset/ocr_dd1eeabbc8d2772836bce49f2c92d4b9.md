4) Select XX Country Name from the title, and replace it with countryName from the Bindings panel. Dreamweaver replaces the placeholder text you typed with its own pseudocode to indicate the source of the dynamic text.

![](bbox=[0.27, 0.17, 0.93, 0.45])

5) Select Tour Name XX, and replace it with tourName from the Bindings panel. Choose View > Live Data to verify that one country and tour are displaying correctly. Toggle off Live Data once you have verified that it’s working.

I often toggle Live Data on and off during development just to make sure there are no surprises. You should see Argentina: Highlights of Argentina in the title. The interesting thing to point out is that not only is the title derived from two different fields in a recordset, but the different fields are also derived from two different database tables. The country name comes from tbl_country, and the tour name comes from tbl_tours. The fact that the country (Argentina) is correctly correlated with the tour (Highlights of Argentina) is further confirmation that the join in your query worked.