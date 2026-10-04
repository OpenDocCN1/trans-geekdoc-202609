238 T. P. Fowdur, L. Babooram, M.U-D-Ibn Nazir Rosun and M. Indoonduon

```
+ " groups.");
return;
}
```

```
// Transform the data to a suitable Matrix for ML.js functions.
//Next, the variable X converts the images found in 'data' as an array,
//into a matrix before being input into the kmeans() function, from the ml.js library.
```

```
var X = array2mat(data);
```

```
// Cluster the data into K groups with the KMeans method.
```

```
clusters = kmeans(X, K);
```

```
// From this point, the variable 'clusters' stores the different clustered images in the
//form of an object, which is further processed to be displayed on the webpage.
//When a different value is selected on the drop down, the cluster image function //
is automatically invoked,and the different clusters are computed and displayed.
```

```
// Prepare the columns [63].
var cols = newArray(K);
for (var j = 0; j < K; j++)
cols[j] = 10;
```

```
// Display the clustering result.
for (var i = 0; i < X.length; i++) {
```

```
// Each image of index i...
var img = document.getElementById("img" + i);
```

```
// is labeled by a group index between 0 and K-1
var groupLabel = clusters.labels[i];
```

```
// We can position the image in the corresponding group column [63].
img.style.position = "absolute";
img.style.left = (10 + groupLabel * 130) + "px";
img.style.top = cols[groupLabel] + "px";
img.classList.add("hover");
cols[groupLabel] += 30 + img.height;// and color the image border with
the average image color in the group [63].
```