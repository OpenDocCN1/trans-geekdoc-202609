600 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nasir Rosun and M. Indoondonon

```
// X-axis labels colour changed to black
XAxis.setText(Color.BLACK);
// prevents the last and first values from clipping off the chart
XAxis.setAvoidFirstLastClipping(true);

YAxis leftAxis = mChart.getAxisAxisLeft();
leftAxis.setDrawGridLines(false);
leftAxis.setTextColor(Color.BLACK);

```

# 6.3.9. The Create Method

This method is used to create a new LineDataSet to assign to the LineData Object. A LineDataSet is an object used to represent one group of values that belongs together inside the chart. The chart is designed to logically separated groups for every line inside the chart. The code for the method is given below in Listing 6.4, together with each line explained.

Listing 6.4. createSet method

```
private LineDataSet createSet() {
// Creates a new LineDataSet Object from MPAndroidChart Library with the label //being
t selected variable of the spinner
LineDataSet set = new LineDataSet(null, spinner.getSelectedItem().toString());
// sets the y-axis the data should be plotted against
set.setAxisDependency(YAxis.AxisDependency.LEFT);
// set min width of the line to 11 dp
set.LineWidth(11);
// set the colour of the line to black
set.setColor(Color.BLACK);
// disables highlights
set.setHighlightEnabled(false);
// disable drawing values
// disable circle indicator
set.setDrawCircles(false);
// drawing mode to cubic bezier for line smoothing
set.setMode(LineDataSet.Mode.CUBIC_BEZIER);
// set the intensity of smoothness
set.setCubicIntensity(0.2f);
// returns the newly created set
return set;
}
```