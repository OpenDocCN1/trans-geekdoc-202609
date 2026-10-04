
# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 599

```java
//Sets up the spinner with an Array adapter
// Create an ArrayAdapter using the string array and a default spinner layout
ArrayAdapter<CharSequence> adapter = ArrayAdapter.fromResource(this, R.array.variables, android.R.layout.simple_spinner_item);
// Select the layout to use when the list of choices adapter
adapter.setDropDownView(android.R.layout.simple_spinner_dropdown_);
// Apply the adapter to the spinner
spinner.setAdapter(adapter);
// sets the OnSelectedItemListener
spinner.setOnSelectedItemListener(this);

// Sets up the graph/
// enables all touch-interactions with the chart.
mChart.setTouchEnabled(true);
// Enables dragging (panning) for the chart.
mChart.setDragEnabled(true);
// Enables scaling for the chart on both axes.
mChart.setScaleEnabled(true);
// Enables pinch-zooming
mChart.setPinchZoom(true);
// Enables drawing the chart borders
mChart.setDrawBorders(true);
// Sets the background colour to white
mChart.setBackground.Color(Color.WHITE);
// Background grid rectangle while the chart drawing-area is to drawn
mChart.setDrawGridBackground(false);
// Enables the right axis to be drawn
mChart.getAxisRight().setEnabled(false);
// Disable the default description text
mChart.setDescription().setEnabled(false);

// Create a LineData Object from MPAndroidChart Library that encapsulates all // data for
a linechart
LineData data = new LineData();
data.setValueColor(Color.BLACK);
mChart.setData(data);
// Retrieve an instance of the default legend and text color to black
// the shape draw to black
Legend legend = mChart.getLegend();
legend.setForm(Legend.LegendForm.LINE);
legend.setTextColor(Color.BLACK);
// Gets the default X-axis
XAxis xAxis = mChart.getXAxis();
//enables the axis to be shown
xAxis.setEnabled(true);
//the line grid are disabled
xAxis.setDrawGridLines(false);
```

600 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nasir Rosun and M. Indoondonon

```java
// X-axis labels colour changed to black
xAxis.setText(Color.BLACK);
// prevents the last and first values from clipping off the chart
xAxis.setAvoidFirstLastClipping(true);

YAxis leftAxis = mChart.getAxisAxisLeft();
leftAxis.setDrawGridLines(false);
leftAxis.setTextColor(Color.BLACK);
```

## 6.3.9. The Create Method

This method is used to create a new LineDataSet to assign to the LineData Object. A LineDataSet is an object used to represent one group of values that belongs together inside the chart. The chart is designed to logically separated groups for every line inside the chart. The code for the method is given below in Listing 6.4, together with each line explained.

### Listing 6.4. createSet method

```java
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

## 6.3.10. The Addentry () Method

This method is used to update the values on the graph. First, the default LineData of the graph is fetched. Then, if a statement is used to check whether a LineDataSet has been added to the LineData object. If not, the createSet() method is called and the new LineDataSet is added to the LineData object to represent one line on the graph. After performing this check, the new value is added using the default addEntry (Entry e, int dataIndex) of the LineData object. The dataset index is set to zero once one LineDataSet has been added. The chart is notified of the update so it may refresh the graph and the view is moved to the new entry. The codes for the method are given in Listing 6

### Listing 6.5. addEntry method

```java
private void addEntry(double point) {
//Gets the current LineData assigned to the chart
LineData data = mChart.getData();
if (data == null) {
  //gets the current LineData from the LineData using ILineDataSet Object from MPAndroidChart Library
ILineDataSet set = data.getDataByIndex(0);
  //if no set has been created, returns null
  if (set == null) {
    //a new LineDataSet is created and added
    set = createSet();
    data.addDataSet(set);
  }
  //new entry is added to the first dataset
  data.addEntry(new Entry(set.entryCount(), (float) point), 0);
  data.notifyDataChanged();
  //Notify the change of data on the chart
mChart.notifyDataSetChanged();
  //Set a fixed number of visible entries
mChart.setVisibleRangeMaximum(120);
  //Set the focus on the last entry
mChart.moveToX(data.entryCount());
}
}
```

## 6.3.11. Clearing Graph on Item Selected

When the user changes the variable being displayed on the graph, the graph needs to be cleared of previous values. Since the MainActivity implements 602 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoondonman AdapterView.OnItemSelectedListener class, the abstract callback method onItemSelected() can be overridden. The graph is cleared using the clearViews () function of the LineChart Object as shown in the codes in Listing 6.6.

### Listing 6.6. onItemSelected method

```java
@Override
public void onItemSelected(AdapterView<?> parent, View view, int position, long id) {
if (monitoring) mChart.clearValues();
}
```

## 6.3.12. Querying Weather API & Sending Data to Local Server or Cloudant Database

To query the weather API, a connection to the internet is needed and in android, networking operations cannot be performed on the main thread since it will throw a NetworkOnMainThreadException. All Networking operations must be done on a background thread and then the result is relayed back to the UI. In android, this is handled by the AsyncTask class. This class has three generic types:

- Params - Parameters set to the task execution.
- Progress - Progress units published during the background computation.
- Results - The type of the result of the background computation.

To use this class, the QueryAPI is subclassed by extending the AsyncTask class with the necessary generic types: Void for Params, Void for Progress, and String for Results. The QueryAPI subclass will override two methods namely:

- doInBackground() - background operations are to be carried out here.
- onPostExecute() - invoked on the UI thread after the background computation finishes. The result from the background operation is passed as the input parameter to this method.

## 6.3.13. QueryAPI Class

This class is used to query the weather API periodically every N minute from the OpenWeather API accessible from the following link, https://openweathermap.org/. It is responsible for querying the API, retrieving the results, displaying the information on the graph, and sending the data obtained to either a local server or to the cloud database.

# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 603

## 6.3.14. The OpenWeather API

The OpenWeather API allows users to send requests to the OpenWeather servers. It is an online service that provides global weather data, including current weather data, forecasts, nowcasts, and historical data, utilizing meteorological broadcast services and raw data from airport weather stations, radar stations, and other weather stations [22]. The API has several packages which allow users to scale their applications if needed. The free tier has a limit of 60 calls/min with a maximum of 1 million calls per month. To obtain the current weather condition for a specific location, the URL for the API call need to be properly formulated by specifying the city name, response type, units of measurement & API key as shown in Figure 6.14.

```
api.openweathermap.org/data/2.5/weather? //endpoint
q={city name} //city name here
&appid={API key} //API Key
&mode={mode} //response type here - json/xml
&units={units} //measurement units - imperial/metric

https://openweathermap.org/data/2.5/weather?
p=20louis
&appid=d9ef3c5a1fc7aad855a430f86eabe867
&mode=json
units=metric
```

Figure 6.14. The URL Request Format.

## 6.3.15. The doBackground () method

This method is used to connect to the API endpoint to fetch the current weather conditions. The endpoint is stored in the String variable URL and the data is fetched using the Jsoup class. The Jsoup java library provides an API for working with real-time HTML. It is convenient for connecting to URLs, extracting and manipulating data from the HTML DOM. A connection to URL is opened by using the connect (String URL) method of the static Jsoup class and then the get () method fetches and parses the HTML data into a Document object. The Document object is converted to a String using the text () method. The resulting String is returned and passed to the onPostExecute () method. The codes are shown in Listing 6.7.
