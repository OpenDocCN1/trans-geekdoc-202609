# 560 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoondonon

```
<td width="180px" align="right">
<!-- Button to download by date---->
<button type="button" style="width: 250px" class="btn btn-primary"
onclick="downloadbyDate()">Download</button>
</td>
</tr>
<table>
<hr />
<td>
</tr>
</table>
<table>
</div>
<td>
</tr>
<tbody>
<table>
</div>
<!-- Adding script tags for JQuery and JQuery and CanvasJS, as libraries-->
<script src="https://canvasjs.com/assets/script/jquery-1.11.1.min.js"></script>
<script src="https://canvasjs.com/assets/script/jquery.canvasjs.min.js"></script>
<body>
</html>
```

# 5.3.7.3. Adding JavaScript Methods for index1.js

As mentioned previously, JavaScript caters for the display of values fetched from the servlet, as well as the latter to perform analytics. JavaScript codes are included in the "index1.js" file. Table 5.20 shows the methods defined:

# Table 5.20. Description of JavaScript methods for index1.js

| Methods | Description |
|---|---|
| classification(n) | Queries the servlet or localhost when the "Classify" button is pressed to return analytical values for KNN and MLP classification. |
| regression() | Queries the servlet or localhost when the "Predict" button is pressed to return analytical values for MLP and MLP regression. |
| window.onload | Is called as soon as the whole page loads, which denotes the start of the line graph that fetches the last set of values stored in the Cloudant or MySQL database, every five seconds. |
| refreshGraph() | Called when the parameter selection for the line graph is altered, such that the selected parameter is displayed on the graph. |
| downloadLast(N) | Queries the servlet or localhost when the "Download" button is clicked after entering a number of samples to be downloaded, to return a JSONObject containing a String parameter used to parse the .csv file. |
| downloadByDate() | Queries the servlet or localhost when the "Download" button is clicked after entering a specific date for samples to be downloaded. A .csv file with the returned encapsulated String parameter in the JSONObject.|