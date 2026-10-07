Handler creates a variable p of Person and assigns "John Smith" to its Name field. We then use template.ParseFiles, passing in the name of the template file and assigning the results to variable t.

Having parsed the template file, we next need to perform the merge, which we do by calling Execute, which passes the http.ResponseWriter and the data item we want to merge with the template as parameters.

When we launch the application in a browser, we get Figure 15.

![](bbox=[0.125, 0.246, 0.875, 0.483])

Figure 15: The Output of Our Simple Template

# Reworking the data access application using a template

Let's put our newfound knowledge of Go templates to work. First, we need to understand one of the many capabilities of a template—the ability to iterate over a set of results, then apply the appropriate formatting to each of them.

In order to achieve this, we must use the {{range}} {{end}} construct. We'll use the following template to build out our table. Everything between {{range}} and {{end}} will be repeated for every member of the object we pass into it.

Code Listing 12: The Template for "Cities" Database Application

```
<html>
<head>
<title>City Search</title>
</head>
<body>
<h1>Search Results</h1>
<table border='1'>
<tr>
<th>City</th>
```