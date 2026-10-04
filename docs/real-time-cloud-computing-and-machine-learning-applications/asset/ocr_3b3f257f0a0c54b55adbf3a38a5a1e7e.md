# 234 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoondumon

```
color: #fff;
background-color: #1d2025;
border-color: #11ece5;
margin-bottom: 40px;
margin-top: 20px;
font-size: 18px;
}
</style>
```

<!-- Call the kmeans_image.js file which defines the Kmeans algorithm -->

```
<script src="kmeans_image.js"></script>
```

```
</head>
```

```
<body>
```

<h1 style="text-align:center; margin:10px; font-size:20px;">K-MEANS - CLUSTERING</h1>

Upon clicking the 'Browse' button, a document browser opens and allows to select images at a time. When the 'Open' button is clicked on the document browser, loadImages() function is invoked and the selected images are displayed on the HTML page.

```
<div class="col-md-2"> <br>
Add images...<input id="imagefile" type="file" onchange="loadImages();" style="margin-bottom: 10px;font-family: 'Abel'; multiple">\</div><br>
```

<!-- Cluster images is added which calls the clustering function of the kmeans_image.js file. The purpose of the clustering function is to apply the kmeans algorithm to group similar images together into the number of groups specified by the user as per [63] -->

```
<div class="col-md-1"> <br>
<button onclick="clusterimages()" style="font-weight:lighter; color:black;">Cluster images</button>
in  <select id="selectK" onchange="clusterimages();" style="font-weight:bold;">"
```

```
<option value="2">2</option>
<option value="3">3</option>
```