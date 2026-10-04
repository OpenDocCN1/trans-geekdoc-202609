```
var data = Papa.parse(csvData, {header: true});

var numberfrows = data.data.length;
//Obtain the number of entries in the file.
// Define the array variables for holding the data:
var sepL = [];
var sepW = [];
var petL = [];
var petW = [];
var p=[];

for(var i = 0; i < numberfrows-1 ; i++){
  // Put the values of each entry in their corresponding array by
  // specifying the name of the column in the file
sepL[i] = data.data[i].Sepal_Length;
seW[i] = data.data[i].Sepal_Width;
petL[i] = data.data[i].Petal_Length;
petW[i] = data.data[i].Petal_Width;
p[i] = data.data[i].Species;
n}
```

```
// Push all the values to the dataset array.
daset.push([sepL[i],sepW[i],petL[i],petW[i]]);
// Push the values of the Species column to the prediction array.
prediction.push(p[i]);
var graph=numberfrows;
for(var i = 0; i < (graph-1)/3 ; i++) {
  // Convert the values to floating point and push them to their
  // corresponding array variables.
I_sepal_length_S_push.push(parseFloat(data.data[i].Sepal_Length));
I_sepal_length_Ve_push.push(parseFloat(data.data[i+50].Sepal_Length));
I_petal_width_S_push.push(parseFloat(data.data[i].Petal_Width));
I_petal_width_Ve_push.push(parseFloat(data.data[i+50].Petal_Width));
I_sepal_width_S.push(parseFloat(data.data[i].Sepal_Width));
I_sepal_width_Ve_push.push(parseFloat(data.data[i+50].Sepal_Width));
```

```
I_sepal_length_Vi.push(parseFloat(data.data[i+100].Sepal_Length));
I_sepal_length_Ve.push(parseFloat(data.data[i+100].Sepal_Length));
I_petal_width_Vi.push(parseFloat(data.data[i+100].Petal_Width));
I_sepal_width_Vi.push(parseFloat(data.data[i+100].Sepal_Width));
```