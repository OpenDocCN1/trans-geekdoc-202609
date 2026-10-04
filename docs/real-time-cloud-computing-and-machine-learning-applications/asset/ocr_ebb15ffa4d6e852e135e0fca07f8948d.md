# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 293

the netparams object holds "WiFi Download Speed" as a String, the downloadSpeed object, representing the double value of the Wi-Fi download speed in Kbps, is passed as an argument through the addEntry() method, implemented in Listing 4.29.

# Listing 4.29. Switch-case for updating UI

```
// Updating the live monitor graph
switch (netparams) {
  case "WiFi Download Speed":
    addEntry(downloadSpeed);
    break;
  case "WiFi Upload Speed":
    addEntry(uploadSpeed);
    break;
  case "LTE Download Speed":
    addEntry(mobiledownloadSpeed);
    break;
  case "LTE Upload Speed":
    addEntry(mobileuploadSpeed);
    break;
  case "Packets Received":
    addEntry(RXPackets);
    break;
  case "Packets Sent":
    addEntry(TXPackets);
    break;
  case "Wifi Signal Strength":
    addEntry((double) (WIFI_RSSI));
    break;
}
```

# 4.3.8.4. Pushing Values to the Local Server

The values retrieved from the Android phone need to be pushed to a running server on NetBeans IDE, which will in turn perform functions, the first one being the parameter retrieval process and the second being filling up of a cloud database for analytics. This section, therefore, involves the codes related to the Android application sending the parameters to the local server.

Apart from fetching network parameters every second, the application needs to have an ongoing piece of code that carries out the sending process at the same time the parameters are obtained. The best choice in this scenario is another thread, which is placed inside the Runnable thread in Listing 4.30. The steps are described below.

+   1. In this thread, a connection is made to the running server using the Socket class which aims towards providing a pathway for communication between