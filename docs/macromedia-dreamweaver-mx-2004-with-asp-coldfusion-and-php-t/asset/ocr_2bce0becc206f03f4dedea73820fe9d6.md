+   6) Change only the WHERE clause in the statement so that it reads as follows:

In ASP:

```
WHERE tbl_country.countryName='' & Request.Form("tourCountry") & ''
```

In ColdFusion:

```
WHERE tbl_country.countryName='#form.tourCountry#'
```

In PHP:

```
WHERE tbl_country.countryName='' . $_POST['tourCountry'] . ''
```

As before, make sure there is a space between the closing single quote (') and the next clause, which begins with ORDER BY.

For the most part, this version of the query should make sense to you. You are matching the country name specified in the form with any tour that is associated with the same country name (though once again, you must go through the relationship between tbl_tours and tbl_country to access this name).

The only mysterious thing here may be the single quote (') that surrounds the dynamic content in all three server models. This is a SQL issue. Any time you are specifying a text string (as opposed to an expression or a number), it must be put in single quotes. Otherwise, the database attempts to interpret the text as if it’s a function or some other special database command. By putting it in single quotes, you are telling the database not to interpret or evaluate it, but to match it with text stored in the database.

![](bbox=[0.29, 0.58, 0.94, 0.645])

+   7) Save and upload the file. Select tours.asp in the Site panel, and press F12 to test it. Select a country from the menu, and press Submit.