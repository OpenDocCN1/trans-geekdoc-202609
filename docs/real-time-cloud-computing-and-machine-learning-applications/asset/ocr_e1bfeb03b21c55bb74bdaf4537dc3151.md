# Server and Servlet Architectures for a Cloud-Based Real-Time .

```
chart.setTitle("Unavailable for PC");
break;
case "Wi-Fi Strength":
plot.RangeAxis().setLabel("Wi-Fi Strength (dB)");
chart.setTitle("Unavailable for PC");
break;
// Pushing data to cloud if radio is active
if (cloudSwitch.isSelected()) {
// Iterating an index to act as key in database
readings.put("Key", idx);
idx = idx + 1;
try {
 client = ClientBuilder.url(new URL("https://8118bf82-4f01-4173-be30-76ffb8e7d-bluemix.cloud.com/"))
.username("apikey-5c23ef26874d4f6cab6a91ca350c71a5");
.password("a82ecf648efeded2f97774e07402f866bdcf9a6");
.build();
} catch (IOException e) {
System.out.println(e.toString());
System.out.println("catch");
}
db = client.database("laptopcloudparameters", false);
db.save(readings.toMap());
System.out.println("Data inserted in cloud database...");
}
// Pushing data to localhost if radio is active
if (localHostSwitch.isSelected()) {
localDBPC.insertPC(totownload, totalupload, packetsreceived,
packetsent);
System.out.println("Pushing PC record to localhost");
count = count + 1;
}
} catch (IOException ex) {
System.out.println(ex);
}
}
```