```
mode: 'scatter', //line display type
name: 'trained set', //line label
line: {
color: 'green', //details of the plot
width: 2,
};
```

// Plot the predicted point on the same graph.

```
var trace2 = {
x: [pred], //the time for which the prediction was required.
y: [pred], //thepredicted value for that given time.

mode: 'markers',
name: 'predicted',
line: {
color: 'red',
size: 8
};
```

// Obtain the y values of the curve of best fit.

```
var coeffs=[];
```

// Extract the coeffs of the equation of the curve of best fit.

```
coeffs = regression.coefficients;
var liney = [];
var ycof = coeffs[0];
```

// Generate the y values from the coeffs and xx arrays:

```
for( var i=0; i<xx.length; i++){
	for( var j = 1; j<coeffs.length; j++){
	ycof = (xx[i]**)*coeffs[j] + ycof;
	}
	liney.push(parseFloat([ycof]));
	ycof = coeffs[0];
}
```

// Plot the curve of best fit on the same graph.