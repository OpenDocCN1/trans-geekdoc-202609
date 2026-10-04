
```html
<input type="number" id="sepalWidth" class="form-control"
align="center"><br>
</div>
<!-- Create a label for the Petal Length used in flower classification -->
<div class="col-md-1" align="center"><br>
<label for="x">Petal_Length:</label>
<input type="number" id="petalLength" class="form-control"
align="center"><br>
</div>
<!-- Create a label for the Petal Width used in flower classification -->
<div class="col-md-1" align="center"><br>
<label for="x">Petal_Width:</label>
<input type="number" id="petalWidth" class="form-control"
align="center"><br>
</div>
<!-- Create a button to call the KNN_CLASSIFY method defined in the
KNN.js script -->
<div class="col-md-1" align="center"><br>
<button type="button" id="prediction" class="btn-warning
onclick='KNN_CLASSIFY()'>CLASSIFY</button>
</div>
<div class="col-md-1" align="center"><br>
</div>
<div class="col-md-1" align="center"><br>
<!-- Create a label to output the flower classification result -->

<div class="col-md-2" align="center"><br>
<label for="x">The flower is classified as:</label>
<input type="text" id="KNN_predictedValue" name="x" class="form-control"
align="center"><br>
</div>
<div class="col-md-1" align="center"><br>
</div>
</div><br>
<!-- Create a space for displaying the chart -->
<div id="chart1"></div>
<br><br><br>
</div>
</body>
</html>
```

# Machine Learning Algorithms

5. It is important to format the dataset to be used in the analysis. A snapshot of the original iris.csv dataset obtained from:

https://forge.scilab.org/index.php?p/rdataset/source/tree/master/csv/datasets/iris.csv is given in Table 3.21 as follows:

## Table 3.21. Snapshot of the Iris data set

| Sepal.Length | Sepal.Width | Petal.Length | Petal.Width | Species |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 5.1 | 3.5 | 1.4 | 0.2 setosa |
| 2 | 4.9 | 3 | 1.4 | 0.2 setosa |
| 3 | 4.7 | 3.2 | 1.3 | 0.2 setosa |
| 4 | 4.6 | 3.1 | 1.5 | 0.2 setosa |
| 5 | 5 | 3.6 | 1.4 | 0.2 setosa |
| 6 | 5.4 | 3.9 | 1.7 | 0.4 setosa |
| 7 | 4.6 | 3.4 | 1.4 | 0.3 setosa |
| 8 | 5 | 3 | 1.5 | 0.2 setosa |
| 9 | 4.4 | 2.9 | 1.4 | 0.1 setosa |
| 10 | 4.9 | 3.7 | 1.5 | 0.2 setosa |
| 11 | 5.4 | 3.4 | 1.6 | 0.2 setosa |
| 12 | 4.8 | 3 | 1.4 | 0.1 setosa |
| 13 | 4.3 | 3 | 1.1 | 0.2 setosa |
| 14 | 5.8 | 4 | 1.2 | 0.4 setosa |
| 15 | 5.7 | 4.4 | 1.5 | 0.4 setosa |
| 16 | 5.4 | 3.9 | 1.3 | 0.4 setosa |
| 17 | 5.1 | 3.5 | 1.4 | 0.3 setosa |
| 18 | 5.7 | 3.8 | 1.7 | 0.3 setosa |
| 19 | 5.1 | 3.8 | 1.5 | 0.2 setosa |

Source: https://forge.scilab.org/index.php?p/rdataset/source/tree/master/csv/datasets/iris.csv. However, in order to be able to access its fields using the KNN.js (described in the next step), the first column of the csv must be deleted and the columns re-labelled as follows:

```
Sepal.Length -> Sepal_Length
Petal.Length -> Petal_Length
Sepal.Width -> Sepal_Width
Petal.Width -> Petal_Width
```

This is required to make the names valid in the javascript. A snapshot of the updated csv is given in Table 3.22.

## Table 3.22. Formatted dataset

| Sepal_Length | Sepal_Width | Petal_Length | Petal_Width | Species |
| :--- | :--- | :--- | :--- | :--- |
| 5.1 | 3.5 | 1.4 | 0.2 | setosa |
| 4.9 | 3 | 1.4 | 0.2 | setosa |
| 4.7 | 3.2 | 1.3 | 0.2 | setosa |
| 4.6 | 3.1 | 1.5 | 0.2 | setosa |
| 5 | 3.6 | 1.4 | 0.2 | setosa |
| 5.4 | 3.9 | 1.7 | 0.4 | setosa |
| 4.6 | 3.4 | 1.4 | 0.3 | setosa |
| 5 | 3.4 | 1.5 | 0.2 | setosa |
| 4.4 | 2.9 | 1.4 | 0.1 | setosa |
| 4.9 | 3.7 | 1.5 | 0.2 | setosa |
| 5.4 | 3.4 | 1.6 | 0.2 | setosa |
| 4.8 | 3 | 1.4 | 0.1 | setosa |
| 4.3 | 3 | 1.1 | 0.2 | setosa |
| 5.8 | 4 | 1.2 | 0.4 | setosa |
| 5.7 | 4.4 | 1.5 | 0.4 | setosa |
| 5.4 | 3.9 | 1.3 | 0.4 | setosa |
| 5.1 | 3.5 | 1.4 | 0.3 | setosa |
| 5.7 | 3.8 | 1.7 | 0.3 | setosa |
| 5.1 | 3.8 | 1.5 | 0.3 | setosa |

Moreover, the data must be read and converted from csv to json format using the PapParse.js script which is used in the KNN.js file described next.

- 6. Right click on the knn folder and create a new javascript file named KNN.js as shown in Figure 3.42.

![](img/2b52fde0e70e8c2f05a10309cf8982_227_0.png)

Figure 3.42. Creating the KNN.js file.

- 7. Double click on the KNN.js file and add the codes given in Listing 3.64. Some of the concepts used in this program have been adapted from [61].

## Listing 3.64. The KNN.js file for KNN based flower classification

```javascript
// Declare the variables that will have the features of the flower types.
// Variables to hold the features of the setosa flower type:
var l_sepal_length_S = [];
var l_petal_length_S = [];
var l_petal_width_S = [];
var l_sepal_width_S = [];

// Variables to hold the features of the versicolor flower type:
var l_sepal_length_Ve = [];
var l_petal_length_Ve = [];
var l_petal_width_Ve = [];
var l_sepal_width_Ve = [];

// Variables to hold the features of the virginica flower type:
var l_sepal_length_Vi = [];
var l_petal_length_Vi = [];
var l_petal_width_Vi = [];
var l_sepal_width_Vi = [];

// Variable to hold all features of the values from the dataset
var dataset = [];
// Variable to hold the values of all the flower types
var prediction = [];

// Add an event listener on the 'txtFileUpload' element defined in listing x..., so that
// the path to the target file can be obtained when the button is clicked
document.getElementById('txtFileUpload').addEventListener('change', upload, false);

// Create a function to create a reader object that will allow the data to be
// read from the file.

function upload(evt) {
  var data = null;
  var file = evt.target.files[0];
  var reader = new FileReader();
  reader.readAsText(file);
// (The OCR text seems to cut off or repeat here, I will provide the cleaned version of the provided logic)
```
*(Note: The provided OCR text contained significant repetitions and fragmented code in the final pages of the source text. I have cleaned the structural flow based on the visible content.)*
