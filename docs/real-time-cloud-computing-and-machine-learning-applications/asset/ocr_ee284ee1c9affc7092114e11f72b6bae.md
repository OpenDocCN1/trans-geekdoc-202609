# 434 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoondonon

```
JSONObject readings = (new JSONObject(str));

System.out.println("Fetching from PC...");
// Extracting values from their headers
time = readings.getString("Timestamp");
totaldownload = readings.getDouble("DownloadSpeed");
totalupload = readings.getDouble("UploadSpeed");
packetsreceived = readings.getDouble("PacketsReceived");
packetssent = readings.getDouble("PacketsSent");

System.out.println("Index:" + idx);
System.out.println("Time:" + time);
System.out.println("Total Download Speed:" + totaldownload);
System.out.println("Total Upload Speed:" + totalupload);
System.out.println("Packets Received:" + packetsreceived);
System.out.println("Packets Sent:" + packetssent);

XYPlot plot = (XYPlot) chart.getPlot();
switch(parameterSelection.getSelectedItem().toString()) {
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
    series.add(count, packetssent);
    break;
}
// Following parameters are not recorded on PC
// Message displayed to user about unavailability of parameter
case "LTE Download Speed":
  plot.getRangeAxis().setLabel("LTE Download Speed");
  chart.setTitle("Unavailable for PC");
  break;
case "LTE Upload Speed":
  plot.getRangeAxis().setLabel("LTE Upload Speed");
```