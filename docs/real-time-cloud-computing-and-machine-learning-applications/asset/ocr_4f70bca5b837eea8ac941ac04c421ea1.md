208 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoondonon

3. Double click on the index.html file under the public folder and add the following codes:

# Listing 3.59. Defining the character set and style

```
<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
<meta charset="utf-8">
<!-- Define the parameters for the text, background, table and buttons -->
<style>
body {
  background-color: #0f1724;
  color: #00a8ff;
  font-family: 'Abel';
  font-size: 50 px;
}
.btn-primary {
  color: #fff;
  background-color: #1d2025;
  border-color: #fffece5;
  margin-bottom: 20px;
  margin-top: 20px;
  font-size: 30px;
}
tbody {
  font-size: 40px ;
}
</style>
```

# Listing 3.60. Create a Table row for the main application heading

```
</head>
<body>
<!-- Create a table with a single row and a main heading describing the purpose of the application -->
<div class="table-responsive">
<table class="table">
<tbody>
<div id="Dataset" class="container">
<table width="100%%">
<tr>
<td></td>
```