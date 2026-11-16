These lines complete the nested if block, the lesson, and the tour search and display application.

```
9    If IsEmpty(Request.Form("tourCountry")) Then
10    If IsEmpty(Request.QueryString("regionID")) Then
11    rs_tourDetail.Source = "SELECT * FROM th_tours INNER JOIN thl_country ON thl_country.countryID
12 Else
13    rs_tourDetail.Source = "SELECT * FROM th_tours INNER JOIN thl_country ON thl_country.countryID
14 End If
15
16 Else
17    rs_tourDetail.Source = "SELECT * FROM th_tours INNER JOIN thl_country ON thl_country.countryID=thl
18 End If
19
```

+   8) Save and upload this file. Test tours.asp in your browser, going back and forth trying every kind of search available.

The application should be bulletproof at this point. You should see all (and only) the tours that meet your search criteria. The Recordset Navigation Bar should show or hide, based on the number of records returned from your search. If you click a tour's country, you should see its profile. If you click a tour's Tour Price Calculator link, you should go to that application, and the tour should be preselected in the menu. In short, your users should now have a pretty slick interface through which to learn more about Newland Tours offerings.