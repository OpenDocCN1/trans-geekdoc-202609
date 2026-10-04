# Server and Servlet Architectures for a Cloud-Based Real-Time . 431

```
System.out.println("Fetching Android...");
// Extracting values from their headers in the JSON Object using
t exact, specific tags previously entered from the Android phone
time = readings.getString("Timestamp");
totaldownload = readings.nextDouble("DownloadSpeed");
totalupload = readings.nextDouble("UploadSpeed");
mobileownload = readings.nextDouble("MobileDownloadSpeed");
mobileupload = readings.nextDouble("MobileUploadSpeed");
packetsreceived = readings.nextDouble("PacketsReceived");
packetsent = readings.nextDouble("PacketsSent");
wifi_strength = readings.nextDouble("WifiStrength");
```

```
// Printing the index and the variables on the console
System.out.println("Index: " + idx);
System.out.println("Time: " + time);
System.out.println("Total Download Speed: " + totaldownload);
System.out.println("Total Upload Speed: " + totalupload);
System.out.println("Mobile Download Speed: " + mobileownload);
System.out.println("Mobile Upload Speed: " + mobileupload);
System.out.println("Packets Received: " + packetsreceived);
System.out.println("Packets Sent: " + packetsent);
System.out.println("Wifi Strength: " + wifi_strength");
```

```
// Getting the plot, i.e, the live graph
XYPlot plot = (XYPlot) chart.getPlot();
```

```
// Printing onto the graph based on user selection
witch (parameterSelection.getSelectedItem().toString()) {
case "Download Speed":
plot.getRangeAxis().setLabel("Download Speed (kbps)");
chart.setTitle("Download Speed");
series.add(count, totaldownload);
break;
case "Upload Speed":
plot.getRangeAxis().setLabel("Upload Speed (kbps)");
chart.setTitle("Upload Speed");
series.add(count, totalupload);
break;
case "Packets Received":
plot.getRangeAxis().setLabel("Number of packets");
chart.setTitle("Packets Received");
series.add(count, packetsreceived);
break;
case "Packets Sent":
plot.getRangeAxis().setLabel("Number of packets");
chart.setTitle("Packets Sent");
series.add(count, packetsent);

```