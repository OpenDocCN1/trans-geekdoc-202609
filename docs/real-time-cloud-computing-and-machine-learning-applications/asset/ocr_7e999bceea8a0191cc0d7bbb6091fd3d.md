# 768 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonon

![](bbox=[0.148, 0.093, 0.851, 0.376])

Figure 7.37. Graph to show live data.

The code for the HTML page is given in Listing 73.31.

# Listing 73.1. HTML Page Codes

```
<!doctype HTML>
<HTML lang="en">
<head>
<meta charset="utf-8">
<title>Weather Prediction</title>
<link rel="stylesheet" href="stylesheet.css">
</head>
<body>
<!-- Creates a table to place the element in order -->
<table class="GeneratedTable">
<tbody>
<tr>
<td>
<h2>Data Source</h2>
<select name="data_src" src="data_src" style="margin-right: 10%">
<!-- These represents the options available to the user -->
<option value="cloud">Cloudant Server</option>
<option value="local">Local Server</option>
</select>
</select>
<td><br>
<h2>Local Server IP Address</h2>
<!-- Input for window size to be used in the algorithms. -->
<input type="text" value="192.168.100.3" name="IP_address" class="form-control" id="IP_address"><br> <br>
```