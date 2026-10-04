436 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoonundan

# 5.1.8.4. Stopping the Server

To stop the thread, the latter is paired up with the interrupt() method, illustrated in Listing 5.8, while disabling access to the “Stop Server” button just after. The program needs to be restarted if another thread is to be created since the port used to create the server will still be in use.

# 5.8. Implementing the stop button

```
private void stopMonitorActionPerformed(java.awt.ActionEvent event) {
  try {
    localserverthread.stop();
    stopServer.setEnabled(false);
    cloudSwitch.setEnabled(false);
    System.out.println("Server stopped... Restart program");
    serverStatus.setText("Server Status: Restart program");
  } catch (Exception e) {
    serverStatus.setText("Server Status: Launch Server first");
  }
}
```

# 5.1.8.5. Uploading Android Values to the Cloud

Android network monitoring includes download and upload parameters from both the Wi-Fi and mobile data services. In turn, if the phone is being used to register mobile data values, the Wi-Fi service of the phone needs to be turned off. As a result, to make a connection to the local server, the IP address of the local gateway cannot be simply used to route traffic from the Android phone to the local server

| Mapping Name | WAN Name | Internal Host | External Host | Enable |
|---|---|---|---|--|
| Android_Pa... | | 192.168.100.84 | | Enable |
| Type: | User-defined Application | | | |
| Application: | Select... | | | |
| Enable Port Mapping: | | | | |
| Mapping Name: | Android_Parameters | | | |
| WAN Name: | | | | |
| Internal Host: | 192.168.100.84 | | | |
| External Source IP Address: | | | | |
| Protocol: | | Internal port number: | 2001 | 2001 |
| External port number: | 2001 | 2001 | External source port number: | 2001 | 2001 |
| Delete | | | | |

Figure 5.13. Configuring port mapping on the router.