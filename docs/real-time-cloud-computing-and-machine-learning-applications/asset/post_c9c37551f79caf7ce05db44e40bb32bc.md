
```javascript
canvas.height);
else
    context.drawImage(img, 0, 0, img.height, img.width, 0, 0, canvas.width,
    canvas.height);
```

```javascript
// Get the image data (i.e., the RGB components of each of the 16 pixels)
var rgb = context.getImageData(0, 0, canvas.width, canvas.height);
```

```javascript
// Store it in the data array;
data.push(rgb.data);
```

```javascript
// Display the image thumbnail.
img.id = "img" + (data.length - 1);
img.style.width = "100px";
images.appendChild(img);
};
```

```javascript
img.style.imageOrientation = "from-image";
img.style.border = "10px solid white";
img.src = url;
```

```javascript
fileReader.readAsArrayBuffer(file.files[i]);
}
}
```

// Once the images are loaded, the user may select the value of K, i.e., the number
// of clusters in the drop down, and click the 'Cluster Images' button which invokes
// the clusterimages() method [63].

```javascript
function clusterimages() {

// Recover the desired number of groups.
// The script first retrieves the value of K from the drop down and stores it in the
// variable 'K' = [46].

```javascript
var K = parseInt(selectK.value);
```

// If the user has selected less images than 'K', the function returns, alerting the
// user that more than 'K+1' images need to be selected for the algorithm to work.

```javascript
if (data.length < K) {
alert("You need to upload at least " + (K + 1) + " images to cluster them in " + K
+ " groups.");
return;
}
```

```javascript
// Transform the data to a suitable Matrix for ML.js functions.
// Next, the variable X converts the images found in 'data' as an array,
// into a matrix before being input into the kmeans() function, from the ml.js library.
```

```javascript
var X = array2mat(data);
```

```javascript
// Cluster the data into K groups with the KMeans method.
```

```javascript
clusters = kmeans(X, K);
```

```javascript
// From this point, the variable 'clusters' stores the different clustered images in the
// form of an object, which is further processed to be displayed on the webpage.
// When a different value is selected on the drop down, the cluster image function //
// is automatically invoked, and the different clusters are computed and displayed.
```

```javascript
// Prepare the columns [63].
var cols = newArray(K);
for (var j = 0; j < K; j++)
cols[j] = 10;
```

```javascript
// Display the clustering result.
for (var i = 0; i < X.length; i++) {

```

```javascript
// Each image of index i...
var img = document.getElementById("img" + i);
```

```javascript
// is labeled by a group index between 0 and K-1
var groupLabel = clusters.labels[i];
```

```javascript
// We can position the image in the corresponding group column [63].
img.style.position = "absolute";
img.style.left = (10 + groupLabel * 130) + "px";
img.style.top = cols[groupLabel] + "px";
img.classList.add("hover");
cols[groupLabel] += 30 + img.height;// and color the image border with
// the average image color in the group [63].
```

# Machine Learning Algorithms

```javascript
var color = floor(classes.centers.row(groupLabel));
img.style.borderTopColor = "rgba(color[0] + ", + color[1] + ", + color[2] + 
" + 0.5 + ")";
img.style.borderRightColor = "rgba(color[4] + ", + color[5] + ", + color[6] + 
" + 0.5 + ")";
img.style.borderBottomColor="rgba(color[8] + ", + color[9] + ", + color[10] + 
" + 0.8 + ")";
img.style.borderLeftColor = "rgba(color[12] + ", + color[13] + ", + color[14] + 
" + 0.8 + ")";

}
// Define the reset() function [63]:
function reset() {
  data = new Array();
  images.innerHTML = "";
}
```

7. To test the application, four images from the Google V6 data set (https://storage.googleapis.com/images/web/visualizer/index.html?set=train&type=e-segmentation&r=false&c=%2m%2F015p6) as shown in Figure 3.56 have been used:

![](img/2b52fde0e707e8c2f05a10309c3f8982_250_png)

Figure 3.56. Test Images.

8. When the KMeans-Clustering.html link is clicked, the following page shown in Figure 3.57 is displayed.

9. To test the application, the Browse button is clicked and the four images in the dataset are added as shown in Figure 3.58.

10. When the Cluster Images button is clicked, the images are clustered based on the KMeans algorithm and the output shown in Figure 3.59 is obtained.

It is be noted that the whole project can be hosted on the Firebase platform by following the procedure described in Section 6. A snapshot of the application hosted on https://experiments.web.app/ is shown in Figure 3.60. 

![](img/2b52fde0e707e8c2f05a10309c3f8982_252_png)

Figure 3.60. The Firebase hosted machine learning application.

# REFERENCES

- [1] Campato, O., Artificial intelligence, machine learning and deep learning. New Delhi: Mercury Learning and Information LLC, 2020.
- [2] Rahman, W., machine learning. New Delhi: SAGE Publications India Ltd. 2020, pp. 11.
- [3] Goertzel, B., and Pennachin, Artificial intelligence. 1st ed. Berlin: Springer, 2007.
- [4] Yampolskiy, R., Artificial intelligence. CRC Press, 2017.
- [5] Shalev-Shwartz, S., and Ben-David, S., Understanding machine learning. Cambridge: Cambridge University Press, 2014.
- [6] Alpaydin, E., Introduction to machine learning. Cambridge, Mass: MIT Press, 2004.
- [7] Goodfellow, I., Bengio, Y., and Courville, A., Deep learning: MIT Press, 2016, pp. 1-2.
- [8] What Is Deep Learning? | It Works, Techniques & Applications, Mathworks, 2021. [Online]. Available: https://www.mathworks.com/discovery/deep-learning.html [Accessed 13 April 2021]
- [9] Skoda, P., and Adam, F., Knowledge Discovery in Big Data from Astronomy and Earth Observation. St. Louis: Elsevier, 2020, pp. 251.
- [10] Sutton, R., Bach, F., and Barto, A., Reinforcement Learning. Massachusetts MIT Press, 2018, pp. 1.
- [11] Zhang, C., and Ma, Y., Ensemble Machine Learning, 1st ed. Boston, MA: Springer US, 2012.
- [12] Albabate, A., and Minkowski, A., Semi-Supervised and Unsupervised Learning. London: ISTE, 2010.
- [13] Jeremy Jordan, Grouping data points with k-means clustering, 2021. [Online] Available: https://www.jeremyordan.com/grouping-data-points-with-k-means-clustering [Accessed 7 March 2021]
- [14] K-means, Mathworks, 2021. [Online]. Available: https://www.mathworks.com/help/stats/kmeans.html [Accessed 16 March 2021]
- [15] Gan, G., Ma, C., and Wu, J., Clustering: Theory, Algorithms, And Applications, 2nd ed. Philadelphia, PA: SIAM, Society for Industry and Applied Mathematics, 2007, pp. 103.
- [16] Agglomerative hierarchical cluster tree - MATLAB linkage, Mathworks, 2021. [Online]. Available: https://www.mathworks.com/help/stats/linkage.html [Accessed 7 February 2021]
- [17] Construct agglomerative clusters from linkages - MATLAB cluster, Mathworks, 2021. [Online]. Available: https://www.mathworks.com/help/stats/cluster.html [Accessed 11 February 2021]
- [18] Mohammed, M., Bashier, E., and Khan, M., Machine learning, 1st ed.
- [19] Construct clusters by Gaussian mixture distribution - Mathworks, 2021. [Online]. Available: https://www.mathworks.com/help/stats/gmistribution.html
- [20] Fischer, A., and Igel, A., Pattern Recognition, Image Analysis, Computer Vision, Berlin:, 2012.
- [21] Hinton, G., A Practical Guide to Training Boltzmann Machines, University of Toronto, Department of Computer Science, 2010.
- [22] Restricted Boltzmann Machine, Mathworks, 2021. [Online]. Available: https://www.mathworks.com/fileexchange/7121-restricted-machine
- [23] Cord, M., and Cunningham, P., Machine learning techniques, Berlin: 2008.
- [24] Mohammed, M., Bashier, E., and Khan, M., Machine learning: Algorithms and Applications, 1st ed. CRC Press, 2016.
- [25] Montgomery, D., Peck, E., and Vine, G., Introduction to Linear Regression Analysis, Wiley, 2012.
- [26] Fit linear regression model - MATLAB fitlm, Mathworks, 2021. [Online]. Available: https://www.mathworks.com/help/stats/fitlm.html
- [27] Predict responses of linear regression model - MATLAB predict, Mathworks, 2021. [Online]. Available: https://www.mathworks.com/help/stats/linearmodel.predict.html
- [28] Introduction to multiple regression, Chalmers Universities of Technologies, 2010. [Online]. Available: http://math.chalmers.se/Stat/Grundat/GB/MSG500/A10lecture5.pdf
- [29] Fitting of a Polynomial using Least Squares Method, Neutrium, 2021. [Online]. Available: https://neutrium.net/mathematics/least-squares-fitting-of-a-polynomial
- [30] Predict labels using k-nearest neighbor classification - MATLAB predict, Mathworks, 2021. [Online]. Available: https://www.mathworks.com/help/stats/classificationknn.predict.html
- [31] Bhattacharjee, S., Hybrid computational intelligence, 1st ed. Academic Press, 2020.
- [32] Train multiclass naive Bayes model - MATLAB fitcnb, Mathworks, 2021. [Online]. Available: https://www.mathworks.com/help/stats/fitcnb.html
- [33] Classify observations using naive Bayes classifier - MATLAB predict, Mathworks, 2021. [Online]. Available: https://www.mathworks.com/help/stats/compactclassificationnaivebayes.predict.html
- [34] Duda, R., Hart, P., and Stork, D., Pattern classification. 2nd ed. New York: Wiley, 2001, pp. 183.
