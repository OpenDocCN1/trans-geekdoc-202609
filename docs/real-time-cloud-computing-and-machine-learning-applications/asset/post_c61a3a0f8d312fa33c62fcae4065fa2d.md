
# 220 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonondon

```javascript
// Plot the features of the vesticolor flower.

var trace2 = {
x: l_sepal_length_Ve,
y: l_petal_length_Ve,
z: l_petal_width_Ve,
q: l_sepal_width_Ve,
mode: 'markers',

marker: {
size: 12,
line: {
width: 0.5,
opacity: 0.8
}
type: 'scatter3d'
};

// Plot the features of the virginica flower.

var trace3 = {
x: l_sepal_length_Vi,
y: l_petal_length_Vi,
z: l_petal_width_Vi,
q: 'markers',
name: 'virginica',

marker: {
size: 12,
line: {
color: 'green',
width: 0.5,
opacity: 0.8
}
type: 'scatter3d'
};

var data = [trace1,trace2, trace3];
var layout = {
title: 'Line and Scatter Styling'
};
Plotly.newPlot('chart1', data, layout);
}
```

When the KNN-Flower-Classification link is clicked from the main application page, the window shown in Figure 3.43 is displayed.

![](img/2b52fde0e707e8c2f05a10309c3f8982_232_0.png)

Figure 3.43. KNN Classification page.

To test the application, a dataset file needs to be selected first, followed by user inputs for the different Sepal and Petal characteristics and then the CLASSIFY button is pressed. A typical output is as shown in Figure 3.44.

![](img/2b52fde0e707e8c2f05a10309c3f8982_232_1.png)

Figure 3.44. KNN Classification output page.

# 222 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonundon

The corresponding graph is shown in Figure 3.45.

Line and Scatter Styling

![](img/2b52fde0e707e8c2f05a10309c3f8982_233_0.png)

Figure 3.45. Graphical representation of the KNN classification.

# 3.7.3. Incorporating the Regression Algorithm Link

To develop the Polynomial regression part, the following steps should be performed:

- 1. Right click on the public folder and create another folder called 'Regression' as shown in Figure 3.46:

![](img/2b52fde0e707e8c2f05a10309c3f8982_233_1.png)

Figure 3.46. Creating the folder for the Polynomial Regression part.

- 2. Right click on the Regression folder and create an HTML file called Polynomial_Regression.html as shown in Figure 3.47.

# Machine Learning Algorithms

![](img/2b52fde0e707e8c2f05a10309c3f8982_234_0.png)

Figure 3.47. Creating the Polynomial_Regression.html file.

- 3. Copy and paste the ml.min.js, papaparse.min.js and plotly-latest.min.js files into the Regression folder as shown in Figure 3.48. These files are available from the links given in Table 3.20. Another relevant class for implementing the polynomial regression function is available from [62].

![](img/2b52fde0e707e8c2f05a10309c3f8982_234_1.png)

Figure 3.48. Adding the external libraries to the Regression folder.

- 4. Double click on the Polynomial_Regression.html file and add the following codes given in Listing 3.65 to it.

Listing 3.65. The Polynomial_Regression.html file for Prediction

```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
<meta charset="utf-8">

<!-- Import the necessary Javascript files. These files must be stored in the Regression folder after being downloaded from their respective links. -->
<script src="ml.min.js"></script>
<script src="papaparse.min.js"></script>
<script src="plotly-latest.min.js"></script>

<!-- Define the style for the background and buttons -->
<style>
 body {
    background-color: #0f1724;
    color: #00a8ff;
    font-family: 'Abel';
    font-size: 18px;
}

.btn-primary {
    color: #fff;
    background-color: #1d0025;
    border-color: #1ece5;
    margin-bottom: 40px;
    margin-top: 20px;
    font-size: 18px;
}
</style>
</head>
<body>
<h1 style="text-align:center; margin:10px;font-size:20px;">POLYNOMIAL REGRESSION</h1>

<!-- Create a space for browsing the dataset file to be used in the analysis -->
<div class="btn-success">
 <input type="file" name="file" class="inputfile" id="txtFileUpload2" accept=".csv" />
</div>

<!-- Call the Polynomial_Regression.js file which defines the Regression algorithm -->
<script src="Polynomial_Regression.js"></script>

<!-- In this example the dataset consists of temperature values recorded over a given interval. The regression analysis will be used to predict the temperature after N minutes. Hence a text-field is created for the user to enter the number of minutes, for which the prediction will be required -->
<div class="row" id="thirdrow">

<div class="col-md-2">
    <label for="x">Enter prediction interval in minutes:</label>
    <input type="number" id="PL_simplePred" class="form-control">
</div>

<!-- Create a text field to add the degree of the polynomial -->
<div class="col-md-2">
    <label for="x">Enter polynomial degree:</label>
    <input type="text" id="PL_degree" class="form-control">
</div>

<!-- Create a button to call the PR_predict() method defined in Polynomial_Regression.js script -->
<div class="col-md-1">
    <button type="button" id="prediction" class="btn-primary" onclick="PR_predict()">Predict</button>
</div>
<div class="col-md-1">
</div>

<div class="col-md-1">
</div>

<!-- Create a label to output the prediction result -->
<div class="col-md-3">
    <label for="x">The predicted temperature is:</label>
    <input type="text" id="PL_predictedValue" class="form-control">
</div>

<!-- Create a space for displaying the equation of the curve of best fit as well as plotting the curve of best fit and the data -->
<label for="input-group-text">Curve of best-fit</label>
<div>
<input type="text" id="curvebf" size="80" name="input-group-text" class="form-control">
</div>

<div id="chart1"></div>
</body>
</html>
```

5. Right click on the Regression folder and create a new javascript file named Polynomial_Regression.js as shown in Figure 3.49.

![](img/2b52fde0e707e8c2f05a10309c3f8982_237_0.png)

Figure 3.49. Creating the Polynomial_Regression.js file.

6. Double click on the Polynomial_Regression.js file and add the codes given in Listing 3.66.

# Listing 3.6. Javascript codes for the polynomial regression application

```javascript
// Array variables for holding the data from the dataset.
var xx = [];
var yy = [];
// Add an event listener on the 'txtFileUpload' element defined in listing 3.5, so
// that the path to the targeted file can be obtained when the upload button is
// clicked.

document.getElementById('txtFileUpload2').addEventListener('change', upload,
false);

// Write a function to create a reader that will load the data to be
// read from the file.

function upload(evt) {

var file = evt.target.files[0];
var reader = new FileReader();
reader.readAsText(file);

// When the file is loaded, create a data object to read the file using the
// parse function of the Papa.js script.

reader.onload = function(event) {
var csvData = event.target.result;
var data = Papa.parse(csvData, {header: true});

// Obtain the number of entries in the file.
var numberofrows = data.data.length;

// Push the data in float format to the arrays yy and xx.
// The Temperature column is pushed in the array yy and xx is used to
// hold the index.

for(var i = 0; i < numberofrows-1 ; i++){

    yy.push(parseFloat(data.data[i].Temp));
    xx.push(i);
}

reader.onerror = function() {
    alert('Unable to read ' + file.fileName);
}
}

// This is the main function for performing the polynomial regression.
function PR_pred(){
// Obtain the user input for the time in minutes after the prediction is
// required.
var pred=document.getElementById('PL_simplePred').value;
// Obtain the user input for the degree of the polynomial.
var degree=document.getElementById('PL_degree').value;
// Obtain a regression object using the PolynomialRegression function of the
// ML script. The function takes as inputs the arrays xx
```
