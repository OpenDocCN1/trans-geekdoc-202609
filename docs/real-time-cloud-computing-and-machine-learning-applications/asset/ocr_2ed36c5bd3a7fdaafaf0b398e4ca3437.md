# Server and Servlet Architectures for a Cloud-Based Real-Time ... 771

https://weatherforecaster.eu-gb.mybluemix.net/ and if the user has selected the local java server, the webpage will contact the servlet hosted on a machine given the IP_address on port 8080. The codes are given in List 73.32.

# Listing 73.32. formRequestURL () Method

```
function formRequestURL() {
// Get the IP of local server
var IP_add = document.getElementById("IP_address").value;
//get the data source Object using the getElementById
var e = document.getElementById("data_src");
//get the data source from the select option
var source = e.options[e.selectedIndex].value;
// Create query string
check whether to use cloud or local server link
if (source === "cloud") {
//remote servlet address
query = "https://weatherforecaster.eu-gb.mybluemix.net/";
} else {
//local address including IP
query = "http://" + IP_add + ":8080/Network_Forecast/";
}

var returned = {
URL: query,
data_src: source
return returned;
}
```

# 7.4.1.2. Updating Graph

The user is presented with a "Select" element from which it is possible to select which weather parameter to monitor. After selecting a new parameter, the "onchange" event is triggered which performs the "displayGraph()" function. "displayGraph()" performs the following:

+   - Gets the selected item from the "Select" Element
- Creates an array of "dataPoints" which will hold x & y values for the graph.
- Initialises the Chart Container using the "new CanvasJS.Chart()" constructor. The chart is initialized with the default options and rendered using the "chart.render()" function.